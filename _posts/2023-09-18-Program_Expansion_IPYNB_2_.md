---
comments: True
layout: post
title: City Download
description: A program I modified online to download uncropped images of cities.
type: hacks
courses: {'compsci': {'week': 4}}
---

```python
# This imports various libraries that will be used to download images
import geopandas as gpd
import us

import rasterio
import rasterio.mask
from xyzservices import TileProvider
from requests.exceptions import HTTPError

# Reads SHP file with data on cities
df = gpd.read_file("US_place_2020.shp")  
# Converts geometries to a new coordinate system
# https://geopandas.org/en/stable/docs/reference/api/geopandas.GeoSeries.to_crs.html
df=df.to_crs(epsg=3857)

import contextily as ctx
```


```python
# Get the most extreme points in each direction based on city boundaries
west, south, east, north = bbox = df.iloc[0].geometry.bounds
# Save shapes to array
shapes=[df.geometry.iloc[0]]
# Store image in img variable, get image from Google Satellite
# https://contextily.readthedocs.io/en/latest/reference.html
try:
	img, ext = ctx.bounds2raster(west,south,east,north,"output.tif",zoom='auto',source=TileProvider.from_qms("Google Satellite")) #try with auto zoom level
except HTTPError:
        img, ext = ctx.bounds2raster(west,south,east,north,"output.tif",zoom=15,source=TileProvider.from_qms("Google Satellite")) #if that doesn't work try with 15, if this fails the program will crash
with rasterio.open("output.tif") as src:
	# Masks image based on coordinates from shapes array
	out_image, out_transform = rasterio.mask.mask(src,shapes,crop=True)  #mask the input iamge to polygon bounds 
	out_meta=src.meta


out_meta.update({"driver": "GTiff","height": out_image.shape[1],"width": out_image.shape[2],"transform": out_transform}) #update the metadata of image

# Save image to TIF file
with rasterio.open("masked.tif", "w", **out_meta) as dest:
	dest.write(out_image)
```


```python
#get info for place, stored in dbf file that comes with shp file
name=df.iloc[0].NAME
geoid=df.iloc[0].GEOID
statefp = df.iloc[0].STATEFP
state=us.states.lookup(statefp).name

#save the image as a JPG to make it postable to twitter
from PIL import Image
im = Image.open("masked.tif")
# Creates new image with RBG color channels
# [int(round(.05*x+x)) for x in im.size] increases the size of the existing image by 5%, then rounds to nearest integer
# (255,255,255) sets the initial background color to white
bg=Image.new("RGB",tuple([int(round(.05*x+x)) for x in im.size]),(255,255,255)) 
# update size of new image
img_w, img_h = im.size
bg_w, bg_h = bg.size
bg_w, bg_h = bg.size
# Centers image, '//' divides to nearest integer
offset = ((bg_w - img_w) // 2, (bg_h - img_h) // 2)

# Saves image to image.jpg file
bg.paste(im,offset,im)
size=1980,1080
# Sets thumbnail of image
bg.thumbnail(size,Image.LANCZOS)
bg.save("image.jpg")

filename="image.jpg"
```


```python
import tweepy
from secrets import *
# Set twitter access tokens, confirms the account that the program will post on
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

api = tweepy.API(auth)

res = api.media_upload(filename)

media_id = res.media_id

# Post Image in post to twitter
api.create_media_metadata(media_id,f"An aerial image of {name}, {state} surrounded by white.")
api.update_status(status=f'GEOID {geoid} {name}, {state}',media_ids=[media_id])


#delete this row and save to shapefile
df=gpd.read_file("US_place_2020.shp")
df = df.iloc[1:]
df.to_file("US_place_2020.shp")
```

This code was very nice, and helped me a lot with downloading the files, as I could not have made this myself. However, it didn't do exactly what I wanted to do. 

- It posted the image to twitter, I needed it to save it to a folder with a specific name
- The code used a shapefile and other data files only obtainable from a website which you needed to enter a research purpose and other info I didn't have
- The program cropped the image to the exact boundaries of a city, I needed it to be a bounding box
- The program only saved one image, I cannot sit there and run the program several thousand times

The first of the issues was relatively simple to fix, I just removed the section of code that posts the image to twitter, and then saved the file to a folder instead of as image.jpg. Code is below


```python
    bg.paste(im, offset, im)
    size = 1980, 1080
    bg.thumbnail(size, Image.LANCZOS)
## Using California Shapefile, save to a folder called cities
## Name image name of city, followed by an underscore and two-letter abbreviation for california
    bg.save("cities/" + name + "_CA.jpg")
## Log to terminal where program left off
    print('Index: ' + str(index) + ', City: ' + name + " saved.")
```

The next issue was less of a code issue, and more of an access issue. I managed to eventually find the census website with shapefiles and other related data for all states at the following link:
https://www.census.gov/cgi-bin/geo/shapefiles/index.php?year=2022&layergroup=Places

    The third issue took by far the longest to resolve, mainly because I overthought it and was looking in the wrong places. My first thought was the look at all the possible options for the rasterio.mask.mask function, which I found here: https://rasterio.readthedocs.io/en/latest/api/rasterio.mask.html
However, many of the descriptions were to a degree confusing, and after trying several of them, I realized all of them cropped the cities to the exact boundary anyways.

    The second idea I had was to save the img variable directly to an output.tif file. However, I quickly realized that the ctx.bounds2raster and rasterio.mask.mask
functions did not output the same type of image, and the program would give an error.

    Then, I looked through documentation for some of these libraries and found the ctx.bounds2img function, which I hoped would successfully download the image, but
again gave an error. Looking back, I realize now this is likely because of the code that was converting the tif file to a jpg, whereas this command may have already saved the image as a jpg file. But, I quickly realized that the original output.tif file had a perfectly cropped image, and I didn't need to do any more work to get that image to masked.tif, and simply replaced the masked.tif references in the rest of the program with output.tif and commented out the code cropping the image file to exact boundaries.

The last issue was easier to resolve, thankfully, and I simply added a for loop to repeat. The modified code is below:
The program was ran locally on my computer, so output is not shown, but the modified program is also an example of lists and iteration, and the citynames and data are stored in df, and they are iterated through in the for loop in the line 'for index, row in df.iterrows():' until every single file is downloaded.


```python
import geopandas as gpd
import us

import rasterio
import rasterio.mask
from xyzservices import TileProvider
from requests.exceptions import HTTPError
from PIL import Image
import contextily as ctx

# Read the GeoDataFrame
df = gpd.read_file("tl_2022_08_place.shp")
df = df.to_crs(epsg=3857)

start = -1

for index, row in df.iterrows():
    if index < start:
        continue

    west, south, east, north = row.geometry.bounds
    shapes = [row.geometry]
    try:
        img, ext = ctx.bounds2raster(west, south, east, north, "output.tif", zoom='auto', source=TileProvider.from_qms("Google Satellite")) #try with auto zoom level
    except HTTPError:
        img, ext = ctx.bounds2raster(west, south, east, north, "output.tif", zoom=15, source=TileProvider.from_qms("Google Satellite")) #if that doesn't work try with 15, if this fails the program will crash
    # with rasterio.open("output.tif") as src:
        # out_image, out_transform = rasterio.mask.mask(src, shapes, crop=True, filled=False)  #mask the input image to polygon bounds
        # out_meta = src.meta

    # out_meta.update({"driver": "GTiff", "height": img.shape[1], "width": img.shape[2], "transform": ext}) #update the metadata

    #with rasterio.open("masked.tif", "w") as dest:
    #    dest.write(img)


    # Get info for place
    name = row.NAME
    geoid = row.GEOID
    statefp = row.STATEFP
    state = us.states.lookup(statefp).name

    # Save the image as a JPG
    # im = Image.open("masked.tif")
    im = Image.open("output.tif")
    bg = Image.new("RGB", tuple([int(round(.05*x+x)) for x in im.size]), (255, 255, 255))
    img_w, img_h = im.size
    bg_w, bg_h = bg.size
    offset = ((bg_w - img_w) // 2, (bg_h - img_h) // 2)

    bg.paste(im, offset, im)
    size = 1980, 1080
    bg.thumbnail(size, Image.LANCZOS)
    bg.save("cities/" + name + "_CO.jpg")
    print('Index: ' + str(index) + ', City: ' + name + " saved.")

# Save the modified GeoDataFrame to a new shapefile
df.to_file("tl_2022_08_place.shp")

```
