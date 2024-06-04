---

---

```python
import pandas as pd
from pytrends.request import TrendReq
import time
import random

# Initialize pytrends
pytrends = TrendReq(hl='en-US', tz=360)

# List of top 100 anime series
top_100_anime = [
    "Naruto", "Attack on Titan", "My Hero Academia", "One Piece", 
    "Demon Slayer", "Dragon Ball Z", "Death Note", "Fullmetal Alchemist",
    "Sword Art Online", "Tokyo Ghoul",  # Add the rest of the anime series
    # ...
]

# Function to get search volume for a keyword over the past day
def get_search_volume(anime):
    pytrends.build_payload([anime], cat=0, timeframe='now 1-d', geo='', gprop='')
    data = pytrends.interest_over_time()
    if not data.empty:
        return data[anime].values[-1]  # Return the most recent data point
    else:
        return 0

# Dictionary to store search volumes
search_volumes = {}

# Fetch search volumes
for anime in top_100_anime:
    try:
        volume = get_search_volume(anime)
        search_volumes[anime] = volume
        print(f"{anime}: {volume}")
        time.sleep(random.randint(5,20))  # Sleep to avoid rate limit issues
    except Exception as e:
        print(f"Error fetching data for {anime}: {e}")

# Convert to DataFrame for easy viewing
df = pd.DataFrame(list(search_volumes.items()), columns=['Anime', 'Search Volume'])
df.sort_values(by='Search Volume', ascending=False, inplace=True)

# Save to CSV
df.to_csv('anime_search_volumes.csv', index=False)
print("Data saved to anime_search_volumes.csv")

```

    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Naruto: 87
    Error fetching data for Naruto: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Attack on Titan: 75
    Error fetching data for Attack on Titan: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    My Hero Academia: 85
    Error fetching data for My Hero Academia: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    One Piece: 87
    Error fetching data for One Piece: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Demon Slayer: 74
    Error fetching data for Demon Slayer: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Dragon Ball Z: 57
    Error fetching data for Dragon Ball Z: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Death Note: 99
    Error fetching data for Death Note: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Fullmetal Alchemist: 71
    Error fetching data for Fullmetal Alchemist: name 'random' is not defined


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)


    Sword Art Online: 72
    Error fetching data for Sword Art Online: name 'random' is not defined
    Tokyo Ghoul: 87
    Error fetching data for Tokyo Ghoul: name 'random' is not defined
    Data saved to anime_search_volumes.csv


    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)



```python
import requests
from bs4 import BeautifulSoup

# Make a request to the website
r = requests.get("https://www.imdb.com/title/tt0081595/")  # Replace with your show's URL

# Create an instance of BeautifulSoup
soup = BeautifulSoup(r.text, 'html.parser')

# Find the release date and genre
release_date = soup.find('a', {'title': 'See more release dates'}).text.strip()
genre = [a.text for a in soup.find_all('a', {'href': '/search/title?genres='})]

print(f"Release Date: {release_date}")
print(f"Genre: {', '.join(genre)}")
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    /tmp/ipykernel_1266/3294292872.py in <module>
          9 
         10 # Find the release date and genre
    ---> 11 release_date = soup.find('a', {'title': 'See more release dates'}).text.strip()
         12 genre = [a.text for a in soup.find_all('a', {'href': '/search/title?genres='})]
         13 


    AttributeError: 'NoneType' object has no attribute 'text'



```python
def fetchAnimeTitles():
    animeTitles = []
    animeReleaseDates = []

    urls = ['https://myanimelist.net/topanime.php?limit=0', 'https://myanimelist.net/topanime.php?limit=50']
    for url in urls:
        response = requests.get(url)

        soup = BeautifulSoup(response.content, 'html.parser')

        blockquote_tags = soup.find_all('h3')

        animeTags = [tag.get_text() for tag in blockquote_tags]

        for i in animeTags:
            animeTitles.append(i)
            animeReleaseDates.append(getReleaseDate(i))

        animeTitles = [item for item in animeTitles if "More" not in item]

    with open('animeTitles.txt', 'a') as file:
        file.write(str(animeTitles))

    with open('animeReleaseDates.txt', 'a') as file:
        file.write(str(animeReleaseDates))


def getReleaseDate(animeTitle):
    search_url = f'https://myanimelist.net/anime.php?q={animeTitle}'
    response = requests.get(search_url)
    soup = BeautifulSoup(response.content, 'html.parser')
    anime_info = soup.find('div', class_='js-scrollfix-bottom-rel')
    release_date = anime_info.find('span', class_='information season').text.strip()
    return release_date

getReleaseDate("naruto")
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    /tmp/ipykernel_1266/4014572738.py in <module>
         34     return release_date
         35 
    ---> 36 getReleaseDate("naruto")
    

    /tmp/ipykernel_1266/4014572738.py in getReleaseDate(animeTitle)
         31     soup = BeautifulSoup(response.content, 'html.parser')
         32     anime_info = soup.find('div', class_='js-scrollfix-bottom-rel')
    ---> 33     release_date = anime_info.find('span', class_='information season').text.strip()
         34     return release_date
         35 


    AttributeError: 'NoneType' object has no attribute 'find'



```python
from bs4 import BeautifulSoup
import requests
import re

# URL of the Wikipedia page
url = 'https://en.wikipedia.org/wiki/One-Punch_Man'

# Send a GET request to the URL
response = requests.get(url)
html_content = response.text

# Parse the HTML content using BeautifulSoup
soup = BeautifulSoup(html_content, 'html.parser')
# Find the infobox and genre row containing the genre information
infobox = soup.find('table', {'class': 'infobox'})
genreRow = infobox.find('th', string='Genre')  
releaseDate = infobox.find('th', string='Original run')

# The genre information is typically in the next <td> tag
# Chatgpt code to remove the citation numbers within wikipedia page
genre = genreRow.find_next_sibling('td').get_text().strip()
cleanedGenre = re.sub(r'\[\d+\]', ', ', genre)
# Remove the trailing comma and space at the end
cleanedGenre = cleanedGenre.rstrip(', ')
# This code I made. It finds the release date within the infobox
releaseDate = releaseDate.find_next_sibling('td').get_text().strip()
releaseDate = releaseDate.split('–')[0].strip()
print(f"Genre: {cleanedGenre}")
print(f"Release Date: {releaseDate}")
```

    Genre: Action, Comedy, Superhero
    Release Date: 2009
    <class 'str'>



```python
from bs4 import BeautifulSoup
import requests
import re

for anime in animeTitles:
    title = anime.replace(' ', '_')
    # URL of the Wikipedia page
    url = f'https://en.wikipedia.org/wiki/{title}'

    # Send a GET request to the URL
    response = requests.get(url)
    html_content = response.text

    # Parse the HTML content using BeautifulSoup
    soup = BeautifulSoup(html_content, 'html.parser')
    # Find the infobox and genre row containing the genre information
    infobox = soup.find('table', {'class': 'infobox'})
    genreRow = infobox.find('th', string='Genre')  
    releaseDate = infobox.find('th', string='Original run')

    # The genre information is typically in the next <td> tag
    # Chatgpt code to remove the citation numbers within wikipedia page
    genre = genreRow.find_next_sibling('td').get_text().strip()
    cleanedGenre = re.sub(r'\[\d+\]', ', ', genre)
    # Remove the trailing comma and space at the end
    cleanedGenre = cleanedGenre.rstrip(', ')
    # This code I made. It finds the release date within the infobox
    releaseDate = releaseDate.find_next_sibling('td').get_text().strip()
    releaseDate = releaseDate.split('–')[0].strip()
    print(f"{anime}: {cleanedGenre}")
    print(f"{anime}: {releaseDate}")
```

    Naruto: Adventure, Fantasy comedy, Martial arts
    Naruto: September 21, 1999
    Attack on Titan: Action, Dark fantasy, Post-apocalyptic
    Attack on Titan: September 9, 2009
    One Piece: Adventure, Fantasy, Science fiction
    One Piece: July 22, 1997
    My Hero Academia: Adventure, Science fantasy, Superhero
    My Hero Academia: July 7, 2014
    Dragon Ball Z: Adventure, Fantasy, Martial arts
    Dragon Ball Z: April 26, 1989
    Fullmetal Alchemist: Brotherhood: Adventure, Dark fantasy, Steampunk
    Fullmetal Alchemist: Brotherhood: April 5, 2009
    Death Note: Mystery, Psychological thriller, , Supernatural thriller
    Death Note: December 1, 2003



    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    /tmp/ipykernel_138126/2778352980.py in <module>
         17     # Find the infobox and genre row containing the genre information
         18     infobox = soup.find('table', {'class': 'infobox'})
    ---> 19     genreRow = infobox.find('th', string='Genre')
         20     releaseDate = infobox.find('th', string='Original run')
         21 


    AttributeError: 'NoneType' object has no attribute 'find'



```python
    animeTitles = []

    urls = [
        "https://myanimelist.net/topanime.php?limit=0",
        "https://myanimelist.net/topanime.php?limit=50",
    ]
    for url in urls:
        response = requests.get(url)

        soup = BeautifulSoup(response.content, "html.parser")

        blockquote_tags = soup.find_all("h3")

        animeTags = [tag.get_text() for tag in blockquote_tags]

        for i in animeTags:
            animeTitles.append(i)
        animeTitles = [item for item in animeTitles if "More" not in item]
    print(animeTitles)
    with open("animeTitles.txt", "a") as file:
        file.write(str(animeTitles))
```

    ['Sousou no Frieren', 'Fullmetal Alchemist: Brotherhood', 'Steins;Gate', 'Gintama°', 'Shingeki no Kyojin Season 3 Part 2', 'Gintama: The Final', "Gintama'", 'Hunter x Hunter (2011)', 'Ginga Eiyuu Densetsu', "Gintama': Enchousen", 'Bleach: Sennen Kessen-hen', 'Kaguya-sama wa Kokurasetai: Ultra Romantic', 'Fruits Basket: The Final', 'Gintama.', 'Gintama', 'Clannad: After Story', 'Koe no Katachi', '3-gatsu no Lion 2nd Season', 'Code Geass: Hangyaku no Lelouch R2', 'Kusuriya no Hitorigoto', 'Gintama Movie 2: Kanketsu-hen - Yorozuya yo Eien Nare', 'Shingeki no Kyojin: The Final Season - Kanketsu-hen', 'Monster', 'Gintama.: Shirogane no Tamashii-hen - Kouhan-sen', 'Violet Evergarden Movie', 'Owarimonogatari 2nd Season', 'Boku no Kokoro no Yabai Yatsu 2nd Season', 'Kimi no Na wa.', 'Jujutsu Kaisen 2nd Season', 'Kingdom 3rd Season', 'Gintama.: Shirogane no Tamashii-hen', 'Vinland Saga Season 2', 'Shingeki no Kyojin: The Final Season', 'Mob Psycho 100 II', 'Bocchi the Rock!', 'Haikyuu!! Karasuno Koukou vs. Shiratorizawa Gakuen Koukou', 'Kaguya-sama wa Kokurasetai: First Kiss wa Owaranai', 'Kizumonogatari III: Reiketsu-hen', 'Sen to Chihiro no Kamikakushi', 'Hajime no Ippo', 'Shingeki no Kyojin: The Final Season Part 2', 'The First Slam Dunk', 'Monogatari Series: Second Season', 'Kimetsu no Yaiba: Yuukaku-hen', 'Kingdom 5th Season', 'Cowboy Bebop', 'Vinland Saga', 'Kingdom 4th Season', 'Shiguang Dailiren', 'Mushishi Zoku Shou 2nd Season', 'One Piece', 'Ashita no Joe 2', 'Shouwa Genroku Rakugo Shinjuu: Sukeroku Futatabi-hen', 'Mob Psycho 100 III', 'Rurouni Kenshin: Meiji Kenkaku Romantan - Tsuioku-hen', '86 Part 2', 'Code Geass: Hangyaku no Lelouch', 'Bleach: Sennen Kessen-hen - Ketsubetsu-tan', 'Great Teacher Onizuka', 'Mo Dao Zu Shi: Wanjie Pian', 'Mushishi Zoku Shou', 'Tian Guan Cifu Er', 'Violet Evergarden', 'Hajime no Ippo: New Challenger', 'Mushoku Tensei: Isekai Ittara Honki Dasu Part 2', 'Mononoke Hime', 'Mushishi', 'Odd Taxi', "Fate/stay night Movie: Heaven's Feel - III. Spring Song", 'Howl no Ugoku Shiro', '"Oshi no Ko"', 'Bungou Stray Dogs 5th Season', 'Made in Abyss', 'Natsume Yuujinchou Shi', 'Shigatsu wa Kimi no Uso', 'Kaguya-sama wa Kokurasetai? Tensai-tachi no Renai Zunousen', 'Made in Abyss: Retsujitsu no Ougonkyou', 'Tengen Toppa Gurren Lagann', 'Shingeki no Kyojin Season 3', 'Natsume Yuujinchou Roku', 'Ping Pong the Animation', 'Shiguang Dailiren II', 'Death Note', 'Haikyuu!! Second Season', 'Made in Abyss Movie 3: Fukaki Tamashii no Reimei', 'Jujutsu Kaisen', 'Suzumiya Haruhi no Shoushitsu', 'Cyberpunk: Edgerunners', 'Hajime no Ippo: Rising', 'Hibike! Euphonium 3', 'Kenpuu Denki Berserk', 'Mushishi Zoku Shou: Suzu no Shizuku', 'Seishun Buta Yarou wa Yumemiru Shoujo no Yume wo Minai', 'Shin Evangelion Movie:||', 'Tengen Toppa Gurren Lagann Movie 2: Lagann-hen', 'Kimetsu no Yaiba Movie: Mugen Ressha-hen', 'Kizumonogatari II: Nekketsu-hen', 'Natsume Yuujinchou Go', 'Natsume Yuujinchou San', 'Ookami Kodomo no Ame to Yuki']



```python
import requests
from bs4 import BeautifulSoup
import re
from datetime import datetime

# List of anime titles to process
animeTitles = ['Naruto', 'Attack on Titan', 'One Piece', 'Invalid Title Example']

# File to store titles that need manual entries
manual_entries_file = 'manualEntries.txt'

with open(manual_entries_file, 'w') as manual_file:
    for anime in animeTitles:
        try:
            title = anime.replace(' ', '_')
            # URL of the Wikipedia page
            url = f'https://en.wikipedia.org/wiki/{title}'

            # Send a GET request to the URL
            response = requests.get(url)
            
            # Check if the page exists
            if response.status_code == 404:
                raise ValueError("Wikipedia page does not exist")

            html_content = response.text

            # Parse the HTML content using BeautifulSoup
            soup = BeautifulSoup(html_content, 'html.parser')
            
            # Find the infobox
            infobox = soup.find('table', {'class': 'infobox'})

            # Handle cases where infobox is not found
            if infobox is None:
                raise ValueError("Infobox not found")

            # Find the genre row and release date row
            genreRow = infobox.find('th', string='Genre')
            releaseDateRow = infobox.find('th', string='Original run')

            # Handle cases where genre or release date rows are not found
            if genreRow is None or releaseDateRow is None:
                raise ValueError("Genre or release date row not found")

            # Get the genre information
            genre = genreRow.find_next_sibling('td').get_text().strip()
            cleanedGenre = re.sub(r'\[\d+\]', ', ', genre)
            # Remove the trailing comma and space at the end
            cleanedGenre = cleanedGenre.rstrip(', ')

            # Get the release date information
            releaseDate = releaseDateRow.find_next_sibling('td').get_text().strip()
            releaseDate = releaseDate.split('–')[0].strip()
            releaseDate = datetime.strptime(releaseDate, '%B %d, %Y')
            # Print the results
            print(f"{anime}: {cleanedGenre}")
            print(f"{anime}: {releaseDate}")

        except Exception as e:
            # Write the title to the manual entries file if there's an error
            manual_file.write(f"{anime}\n")
            print(f"Error processing {anime}: {e}")

```

    Naruto: Adventure, Fantasy comedy, Martial arts
    Naruto: 1999-09-21 00:00:00
    Attack on Titan: Action, Dark fantasy, Post-apocalyptic
    Attack on Titan: 2009-09-09 00:00:00
    One Piece: Adventure, Fantasy, Science fiction
    One Piece: 1997-07-22 00:00:00
    Error processing Invalid Title Example: Wikipedia page does not exist



```python
import requests
from bs4 import BeautifulSoup
import re
from datetime import datetime

def genreFetch(animeTitles):
    # File to store titles that need manual entries
    manual_entries_file = 'manualEntries.txt'

    # Dictionary to store the results
    anime_data = {}

    with open(manual_entries_file, 'w') as manual_file:
        for anime in animeTitles:
            try:
                title = anime.replace(' ', '_')
                # URL of the Wikipedia page
                url = f'https://en.wikipedia.org/wiki/{title}'

                # Send a GET request to the URL
                response = requests.get(url)
                
                # Check if the page exists
                if response.status_code == 404:
                    raise ValueError("Wikipedia page does not exist")

                html_content = response.text

                # Parse the HTML content using BeautifulSoup
                soup = BeautifulSoup(html_content, 'html.parser')
                
                # Find the infobox
                infobox = soup.find('table', {'class': 'infobox'})

                # Handle cases where infobox is not found
                if infobox is None:
                    raise ValueError("Infobox not found")

                # Find the genre row and release date row
                genreRow = infobox.find('th', string='Genre')
                releaseDateRow = infobox.find('th', string='Original run')

                # Handle cases where genre or release date rows are not found
                if genreRow is None or releaseDateRow is None:
                    raise ValueError("Genre or release date row not found")

                # Get the genre information
                genre = genreRow.find_next_sibling('td').get_text().strip()
                cleanedGenre = re.sub(r'\[\d+\]', ', ', genre)
                # Remove the trailing comma and space at the end
                cleanedGenre = cleanedGenre.rstrip(', ')

                # Get the release date information
                releaseDate = releaseDateRow.find_next_sibling('td').get_text().strip()
                releaseDate = releaseDate.split('–')[0].strip()
                releaseDate = datetime.strptime(releaseDate, '%B %d, %Y')

                # Store the results in the dictionary
                anime_data[anime] = {
                    'genre': cleanedGenre,
                    'release_date': releaseDate
                }

                # Print the results
                print(f"{anime}: Genre: {cleanedGenre}")
                print(f"{anime}: Release Date: {releaseDate}")

            except Exception as e:
                # Write the title to the manual entries file if there's an error
                manual_file.write(f"{anime}\n")
                print(f"Error processing {anime}: {e}")

    return anime_data

# Example usage:
animeTitles = ["Naruto", "Attack on Titan", "One Piece"]
anime_data = genreFetch(animeTitles)
print(anime_data)

```

    Naruto: Genre: Adventure, Fantasy comedy, Martial arts
    Naruto: Release Date: 1999-09-21 00:00:00
    Attack on Titan: Genre: Action, Dark fantasy, Post-apocalyptic
    Attack on Titan: Release Date: 2009-09-09 00:00:00
    One Piece: Genre: Adventure, Fantasy, Science fiction
    One Piece: Release Date: 1997-07-22 00:00:00
    {'Naruto': {'genre': 'Adventure, Fantasy comedy, Martial arts', 'release_date': datetime.datetime(1999, 9, 21, 0, 0)}, 'Attack on Titan': {'genre': 'Action, Dark fantasy, Post-apocalyptic', 'release_date': datetime.datetime(2009, 9, 9, 0, 0)}, 'One Piece': {'genre': 'Adventure, Fantasy, Science fiction', 'release_date': datetime.datetime(1997, 7, 22, 0, 0)}}



```python
import requests
from bs4 import BeautifulSoup
import re
from datetime import datetime

def genreFetch(animeTitles):
    # File to store titles that need manual entries
    manual_entries_file = 'manualEntries.txt'

    # Dictionary to store the results
    anime_data = {}

    with open(manual_entries_file, 'w') as manual_file:
        for anime in animeTitles:
            try:
                title = anime.replace(' ', '_')
                # URL of the Wikipedia page
                url = f'https://en.wikipedia.org/wiki/{title}'

                # Send a GET request to the URL
                response = requests.get(url)
                
                # Check if the page exists
                if response.status_code == 404:
                    raise ValueError("Wikipedia page does not exist")

                html_content = response.text

                # Parse the HTML content using BeautifulSoup
                soup = BeautifulSoup(html_content, 'html.parser')
                
                # Find the infobox
                infobox = soup.find('table', {'class': 'infobox'})

                # Handle cases where infobox is not found
                if infobox is None:
                    raise ValueError("Infobox not found")

                # Find the genre row and release date row
                genreRow = infobox.find('th', string='Genre')
                releaseDateRow = infobox.find('th', string='Original run')

                # Handle cases where genre or release date rows are not found
                if genreRow is None or releaseDateRow is None:
                    raise ValueError("Genre or release date row not found")

                # Get the genre information
                genre = genreRow.find_next_sibling('td').get_text().strip()
                cleanedGenre = re.sub(r'\[\d+\]', '', genre).strip()

                # Get the release date information
                releaseDate = releaseDateRow.find_next_sibling('td').get_text().strip()
                releaseDate = releaseDate.split('–')[0].strip()
                releaseDate = datetime.strptime(releaseDate, '%B %d, %Y')

                # Store the results in the dictionary
                anime_data[anime] = {
                    'genre': cleanedGenre,
                    'release_date': releaseDate
                }

                # Print the results
                print(f"{anime}: Genre: {cleanedGenre}")
                print(f"{anime}: Release Date: {releaseDate}")

            except Exception as e:
                # Write the title to the manual entries file if there's an error
                manual_file.write(f"{anime}\n")
                print(f"Error processing {anime}: {e}")

    return anime_data

# Example usage
animeList = [
    {"name": "Naruto", "searches": 1000},
    {"name": "Attack on Titan", "searches": 1500},
    {"name": "One Piece", "searches": None},
    {"name": "Demon Slayer", "searches": 2000}
]

# Filter entries where searches is not None
data = [entry for entry in animeList if entry["searches"] is not None]

# Fetch genres and release dates for the filtered anime names
stuff = genreFetch([entry["name"] for entry in data])

# Initialize lists to store genres and release dates
genres = []
release_dates = []

# Extract genres and release dates from the fetched data
for anime in stuff:
    genres.append(stuff[anime]['genre'])
    release_dates.append(stuff[anime]['release_date'])

print("Genres:", genres)
print("Release Dates:", release_dates)

```

    Naruto: Genre: AdventureFantasy comedyMartial arts
    Naruto: Release Date: 1999-09-21 00:00:00
    Attack on Titan: Genre: ActionDark fantasyPost-apocalyptic
    Attack on Titan: Release Date: 2009-09-09 00:00:00
    Error processing Demon Slayer: Infobox not found
    Genres: ['AdventureFantasy comedyMartial arts', 'ActionDark fantasyPost-apocalyptic']
    Release Dates: [datetime.datetime(1999, 9, 21, 0, 0), datetime.datetime(2009, 9, 9, 0, 0)]



```python
import random
from datetime import datetime, timedelta

def generate_random_date(start_year=1985, end_year=2015):
    start_date = datetime(start_year, 1, 1)
    end_date = datetime(end_year, 12, 31)
    
    time_between_dates = end_date - start_date
    days_between_dates = time_between_dates.days
    
    random_number_of_days = random.randrange(days_between_dates)
    random_date = start_date + timedelta(days=random_number_of_days)
    
    return random_date

generate_random_date()
```




    datetime.datetime(2004, 5, 14, 0, 0)


