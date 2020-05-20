
# JSON & APIs - Student Activity

<img src='https://raw.githubusercontent.com/jirvingphd/Data-Science-Lessons/master/Mod%202/JSON-XML-Recur/old_town.jpg' width=50%> 

# ⏰ Activity - Part 1 (JSON)

## JSON

### Reading JSON files

Import JSON library. Also, import Pandas.



```python

```

Load JSON from file. This file contains song data from Spotify on Old Town Road by Lil Nas X. 


```python
json_file='old_town_road.json'

```

Print out data.


```python

```

Check type of data, get keys.


```python

```


```python

```

Explore 'meta' by printing it out, checking its type and keys.


```python

```


```python

```

Now use the 'track' key to inspect details about the song.
- Print out the keys from `track`


```python

```

- What key is the song in?

| ID | Key   |
|------|------|
| 0 | C |
1 |	C♯ 
2  | D 
3  | D♯
4  | E 
5  | F 
6  | F♯
7  | G
8  | G♯
9  | A
10 | A♯	
11 | B 	


```python

```

How long is the song?


```python

```

Load the 'track' data into a DataFrame.


```python

```

### Using the 'old_town_road.json' file and what you have learned above, do the following:

#### Create a DataFrame of the different segments of Old Town Road


```python

```


```python

```

#### Find the longest segment and the loudest segment.


```python

```


```python

```

#### How many bars are in the song?


```python

```

#### What's the average length of a bar?


```python

```

#  ⏰ Activity - Part 2: APIs

## Connecting to and interacting with an API

<img src='https://raw.githubusercontent.com/jirvingphd/Data-Science-Lessons/master/Mod%202/APIs/genius.jpeg'>
<!-- https://raw.githubusercontent.com/jirvingphd/Data-Science-Lessons/master/Mod%202/APIs/api_client.png -->

## Genius API
- The world's biggest collection of song lyrics and musical knowledge

<center>In this pair programming activity, you will connect to the Genius API in order to obtain song lyric data.

### Create an account to gain access

Go to the developer page at https://genius.com/developers. You will have to create a Genius account if you don't already have one.

Then you will want to create a new API client.

<img src='https://raw.githubusercontent.com/jirvingphd/Data-Science-Lessons/master/Mod%202/APIs/api_client.png'>

You can choose any name for the app. For the website URL, you could just use your Github page.<br><br>
<b>Note</b>: The URL must be a full URL with 'http://' in the front.

<img src='https://raw.githubusercontent.com/jirvingphd/Data-Science-Lessons/master/Mod%202/APIs/api_client2.png'>


```python
# Note: I added a genius_api.json file with my login info inside of my user folder
# I used a text editor (SublimeText3)
import json
## Replace your User folder below:
api_info_file = "/Users/jamesirving/.secret/genius_api.json"
with open(api_info_file,'r') as f:
    contents = f.read()
    api_info = json.loads(contents)
    
print(api_info.keys())

        
api_id = api_info['client-id']
api_secret = api_info['client-secret']
api_oath_token = api_info['oath-token']
```

    dict_keys(['client-id', 'client-secret', 'oath-token'])


You should see something similar to the above. <br><br>
If you click on 'Generate Access Token' you will be provided with a string that you will need to copy to your clipboard. Genius uses OAuth2 for making API calls so you will need to be passing the token into your calls.<br><br>
With your token copied, you're now ready to start connecting to the API.

### Check out documentation

Take a couple minutes to browse through the documentation found at https://docs.genius.com/. <br> <br>
Take note of what kinds of information is available through this API and what header data is needed to make certain calls. <br><br>
Keep the documentation open in a separate tab as you'll want to come back to it for reference.

### Preparing for requests

In the cells below:<br>
- Import the <b>requests</b> library
- Create a <b>base_url</b> string containing the base URL for the API (https://api.genius.com)
- Create a <b>headers</b> dictionary containing the key, <i>Authorization</i> and the value <i>Bearer </i> + your client access token. (Note: There should be a space in between 'Bearer' and the token.)
- Replace "TOKEN" with the value the API documentation indicates


```python
import requests

#TOKEN below should be the string that the API docs tells you
#Clearly I'm not giving mine out here on the internet. That'd be dumb
base_url = "http://api.genius.com"
#Key line below here when, this is how to authorize your request when
#using the API
headers = {'Authorization': 'Bearer TOKEN'}
```

### Search for "Old Town Road" (the song from JSON file)

Now let's try looking up a specific song and see what kind of info we can get on it.

If you look at the <b>/songs/</b> endpoint in the documentation, you'll notice that you need the ID for the song. <br><br>
In order to get a song ID, we will first need to search for a song and then grab its ID. <br><br>
We can do this through the <b>/search</b> endpoint which allows us to enter search terms such as song title, artist, and album.<br><br>
Take a look at the documention for the search endpoint - https://docs.genius.com/#/search-h2. <br><br>
To make a call to this endpoint, we need to pass in some data: a key called <b>q</b> and our search terms.

In the cells below:<br>
- First decide on a song you want to look up
- Create a <b>params</b> dictionary containing the key, <b>q</b> and the value the search terms for your song.
- Create a search_url by appending the base_url with <b>/search</b>
- Make a request to the search_url, passing in the arguments params=params and headers=headers and get the response.
- Under the 'response' dictionary, iterate through the 'hits' sub-dictionary until you find the correct song you searched for.
- Once you find the correct song, grab and store its ID as song_id.

<b>Hint:</b> The 'hits' sub-dictionary has a dictionary object called 'result' which contains 'title' (the song title), another dictionary 'primary_artist' (which has a key called 'name' to get the artist's name), and an 'id' value.


```python
search_url = None
song_title = None
params = None

response = None

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```

### Lookup a song

Now that we have the ID for our song, we can use the '/songs/' endpoint to look it up.

In the cells below:<br>
- Create a songs_url consisting of the base_url + '/songs/' 
- Create a query using songs_url + the song_id.
- Make a request to the songs_url, passing in the argument headers=headers and get the response.
- Explore the 'response' dictionary. What info can we get on a song?
- Grab the URL for the lyrics page for the song and store it as lyrics_url.


```python
songs_url =  None
songs_query = None
songs_query
```


```python

```


```python

```


```python

```


```python

```


```python

```

As a preview of what's to come in the next section with web scraping, we can use the lyrics_url you just grabbed to print out the lyrics to the song. <br><br>
You don't have to worry too much about what the following cell contains or how it works. It basically is creating a request to the URL for the lyrics, scanning the page for where the lyrics are, and then grabbing the lyrics as text and returning them. <br><br>
This uses a library called BeautifulSoup. You may have to install it first by running 'pip install bs4' in your terminal. <br><br>
Go ahead and run the cells below. Just something cool to check out!


```python
from bs4 import BeautifulSoup

def scrape_song_url(url):
    page = requests.get(url)
    html = BeautifulSoup(page.text, 'html.parser')
    lyrics = html.find('div', class_='lyrics').get_text()
    return lyrics
```


```python
## save the scraped lyrics as a new variable, lyrics

```


```python

```

### Saving the data

- Save the `response` key from your Genius API response as a new variable called `output`
- Add an additional `lyrics` key with the lyrics scraped above
- Your final dictionary should have 2 keys: `song` and `lyrics`


```python
output= {}
```


```python

```


```python

```

### Save `output` to a new json file called "old_town_road_lyrics.json"


```python

```

### Finally, load back in the json file to confirm it saved correctly


```python

```


```python

```


```python

```


```python

```
