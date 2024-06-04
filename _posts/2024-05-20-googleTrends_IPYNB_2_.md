---

---

```python
with open('animeTitles.txt', 'r') as file:
    stringAnime = file.readlines()[0]
    print(stringAnime)
listAnime = stringAnime.strip('][').split(', ')
listAnime = [string.replace("'", "") for string in listAnime]
```

    ['Sousou no Frieren', 'Fullmetal Alchemist: Brotherhood', 'Steins;Gate', 'Gintama°', 'Shingeki no Kyojin Season 3 Part 2', 'Gintama: The Final', "Gintama'", 'Hunter x Hunter (2011)', 'Ginga Eiyuu Densetsu', "Gintama': Enchousen", 'Bleach: Sennen Kessen-hen', 'Kaguya-sama wa Kokurasetai: Ultra Romantic', 'Fruits Basket: The Final', 'Gintama.', 'Gintama', 'Clannad: After Story', 'Koe no Katachi', '3-gatsu no Lion 2nd Season', 'Code Geass: Hangyaku no Lelouch R2', 'Kusuriya no Hitorigoto', 'Gintama Movie 2: Kanketsu-hen - Yorozuya yo Eien Nare', 'Shingeki no Kyojin: The Final Season - Kanketsu-hen', 'Monster', 'Gintama.: Shirogane no Tamashii-hen - Kouhan-sen', 'Violet Evergarden Movie', 'Owarimonogatari 2nd Season', 'Boku no Kokoro no Yabai Yatsu 2nd Season', 'Kimi no Na wa.', 'Jujutsu Kaisen 2nd Season', 'Kingdom 3rd Season', 'Gintama.: Shirogane no Tamashii-hen', 'Vinland Saga Season 2', 'Shingeki no Kyojin: The Final Season', 'Mob Psycho 100 II', 'Bocchi the Rock!', 'Haikyuu!! Karasuno Koukou vs. Shiratorizawa Gakuen Koukou', 'Kaguya-sama wa Kokurasetai: First Kiss wa Owaranai', 'Kizumonogatari III: Reiketsu-hen', 'Sen to Chihiro no Kamikakushi', 'The First Slam Dunk', 'Hajime no Ippo', 'Monogatari Series: Second Season', 'Shingeki no Kyojin: The Final Season Part 2', 'Vinland Saga', 'Cowboy Bebop', 'Kimetsu no Yaiba: Yuukaku-hen', 'Kingdom 5th Season', 'Kingdom 4th Season', 'Shiguang Dailiren', 'Mushishi Zoku Shou 2nd Season', 'One Piece', 'Ashita no Joe 2', 'Shouwa Genroku Rakugo Shinjuu: Sukeroku Futatabi-hen', 'Mob Psycho 100 III', 'Rurouni Kenshin: Meiji Kenkaku Romantan - Tsuioku-hen', '86 Part 2', 'Code Geass: Hangyaku no Lelouch', 'Bleach: Sennen Kessen-hen - Ketsubetsu-tan', 'Great Teacher Onizuka', 'Mo Dao Zu Shi: Wanjie Pian', 'Mushishi Zoku Shou', 'Tian Guan Cifu Er', 'Violet Evergarden', 'Hajime no Ippo: New Challenger', 'Mushoku Tensei: Isekai Ittara Honki Dasu Part 2', 'Mononoke Hime', 'Mushishi', 'Odd Taxi', '"Oshi no Ko"', "Fate/stay night Movie: Heaven's Feel - III. Spring Song", 'Howl no Ugoku Shiro', 'Bungou Stray Dogs 5th Season', 'Made in Abyss', 'Natsume Yuujinchou Shi', 'Shigatsu wa Kimi no Uso', 'Kaguya-sama wa Kokurasetai? Tensai-tachi no Renai Zunousen', 'Made in Abyss: Retsujitsu no Ougonkyou', 'Shiguang Dailiren II', 'Tengen Toppa Gurren Lagann', 'Shingeki no Kyojin Season 3', 'Natsume Yuujinchou Roku', 'Ping Pong the Animation', 'Death Note', 'Haikyuu!! Second Season', 'Made in Abyss Movie 3: Fukaki Tamashii no Reimei', 'Jujutsu Kaisen', 'Suzumiya Haruhi no Shoushitsu', 'Cyberpunk: Edgerunners', 'Hajime no Ippo: Rising', 'Hibike! Euphonium 3', 'Kenpuu Denki Berserk', 'Mushishi Zoku Shou: Suzu no Shizuku', 'Seishun Buta Yarou wa Yumemiru Shoujo no Yume wo Minai', 'Shin Evangelion Movie:||', 'Tengen Toppa Gurren Lagann Movie 2: Lagann-hen', 'Kimetsu no Yaiba Movie: Mugen Ressha-hen', 'Kizumonogatari II: Nekketsu-hen', 'Natsume Yuujinchou Go', 'Natsume Yuujinchou San', 'Ookami Kodomo no Ame to Yuki']



```python
from bs4 import BeautifulSoup
import requests
import pandas as pd
from pytrends.request import TrendReq
import time
import random

animeTitles = []
animeRelevancy = []

with open('animeTitles.txt', 'r') as file:
    stringAnime = file.readlines()[0]
listAnime = stringAnime.strip('][').split(', ')
listAnime = [string.replace("'", "") for string in listAnime]

def get_weekly_searches(keyword):
    pytrends = TrendReq(hl='en-US', tz=360)
    kw_list = [keyword]

    # Fetch interest over time for the past 7 days
    pytrends.build_payload(kw_list, cat=0, timeframe='now 1-d', geo='', gprop='')
    data = pytrends.interest_over_time()

    # Check if the data is not empty
    if not data.empty:
        data = data.reset_index()
        return data
    else:
        return None

def summarize_searches(data, keyword):
    if data is not None:
        total_searches = data[keyword].sum()
        return(total_searches)

for title in listAnime:
    data = get_weekly_searches(title)
    animeRelevancy.append(dict(name=str(title), searches=summarize_searches(data,title)))
    with open('animes.txt', 'a') as file:
        file.write(str(dict(name=str(title), searches=summarize_searches(data,title))))
    listAnime.remove(title)
    with open('animeTitles.txt', 'w') as file:
        file.write(str(listAnime))


```

    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)
    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)
    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)
    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)
    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)
    /home/trevor/.local/lib/python3.10/site-packages/pytrends/request.py:260: FutureWarning: Downcasting object dtype arrays on .fillna, .ffill, .bfill is deprecated and will change in a future version. Call result.infer_objects(copy=False) instead. To opt-in to the future behavior, set `pd.set_option('future.no_silent_downcasting', True)`
      df = df.fillna(False)



    ---------------------------------------------------------------------------

    TooManyRequestsError                      Traceback (most recent call last)

    /tmp/ipykernel_13183/3715162926.py in <module>
         35 
         36 for title in listAnime:
    ---> 37     data = get_weekly_searches(title)
         38     animeRelevancy.append(dict(name=str(title), searches=summarize_searches(data,title)))
         39     with open('animes.txt', 'a') as file:


    /tmp/ipykernel_13183/3715162926.py in get_weekly_searches(keyword)
         20     # Fetch interest over time for the past 7 days
         21     pytrends.build_payload(kw_list, cat=0, timeframe='now 1-d', geo='', gprop='')
    ---> 22     data = pytrends.interest_over_time()
         23 
         24     # Check if the data is not empty


    ~/.local/lib/python3.10/site-packages/pytrends/request.py in interest_over_time(self)
        230 
        231         # make the request and parse the returned json
    --> 232         req_json = self._get_data(
        233             url=TrendReq.INTEREST_OVER_TIME_URL,
        234             method=TrendReq.GET_METHOD,


    ~/.local/lib/python3.10/site-packages/pytrends/request.py in _get_data(self, url, method, trim_chars, **kwargs)
        157         else:
        158             if response.status_code == status_codes.codes.too_many_requests:
    --> 159                 raise exceptions.TooManyRequestsError.from_response(response)
        160             raise exceptions.ResponseError.from_response(response)
        161 


    TooManyRequestsError: The request failed: Google returned a response with code 429



```python
import re
import ast
with open('animes.txt', 'r') as file:
    stringAnime = file.readlines()[0]
stringAnime = re.sub(r'}{','},{', stringAnime)
stringAnime = "[" + stringAnime + "]"
animeList = ast.literal_eval(stringAnime)


data = [entry for entry in animeList if entry["searches"] is not None]

sorted_data = sorted(data, key=lambda x: x['searches'], reverse=True)

for entry in sorted_data:
    print(entry["name"],entry['searches'])

```

    Jujutsu Kaisen 13061
    One Piece 12373
    "Oshi no Ko" 12264
    Monster 11939
    Death Note 11194
    Vinland Saga 10996
    Hajime no Ippo 9097
    Gintama 8736
    Made in Abyss 8241
    "Gintama" 7741
    Cowboy Bebop 7706
    Violet Evergarden 6398
    Cyberpunk: Edgerunners 5339
    Bocchi the Rock! 4387
    Sousou no Frieren 3587
    Kusuriya no Hitorigoto 1889
    Fullmetal Alchemist: Brotherhood 1619
    Odd Taxi 446
    Mushishi 358
    Made in Abyss: Retsujitsu no Ougonkyou 270
    Mushishi Zoku Shou 2nd Season 258
    Haikyuu!! Karasuno Koukou vs. Shiratorizawa Gakuen Koukou 248
    Tengen Toppa Gurren Lagann 232
    "Gintama: Enchousen" 198
    Vinland Saga Season 2 198
    Kingdom 5th Season 192
    Violet Evergarden Movie 191
    Shigatsu wa Kimi no Uso 189
    Hunter x Hunter (2011) 187
    Kimetsu no Yaiba Movie: Mugen Ressha-hen 185
    Shiguang Dailiren 180
    Gintama.: Shirogane no Tamashii-hen - Kouhan-sen 173
    Great Teacher Onizuka 172
    Hajime no Ippo: Rising 171
    Mushoku Tensei: Isekai Ittara Honki Dasu Part 2 170
    Koe no Katachi 169
    Kaguya-sama wa Kokurasetai? Tensai-tachi no Renai Zunousen 166
    Fruits Basket: The Final 160
    Steins;Gate 100
    Gintama. 100
    Kimi no Na wa. 100
    Kingdom 3rd Season 100
    Gintama° 100
    Gintama Movie 2: Kanketsu-hen - Yorozuya yo Eien Nare 100
    Mob Psycho 100 III 100
    Mononoke Hime 100
    Ping Pong the Animation 100
    Shin Evangelion Movie:|| 100
    Clannad: After Story 100
    Mob Psycho 100 II 100
    Shingeki no Kyojin Season 3 100
    Kizumonogatari II: Nekketsu-hen 100



```python

```

    Error

