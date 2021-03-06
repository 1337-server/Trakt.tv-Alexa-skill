# Tracked Media - A Trakt.tv API powered Alexa skill
[![Build Status](https://travis-ci.com/1337-server/Tracked-media.svg?branch=master)](https://travis-ci.com/1337-server/Tracked-media)
[![codecov](https://codecov.io/gh/1337-server/Tracked-media/branch/master/graph/badge.svg?token=P3MW0Y5TNL)](https://codecov.io/gh/1337-server/Tracked-media)


A simple Alexa app/skill to connect to the Trakt.tv API via your own trakt.tv account.

This skill will let you 
 - Add/Remove movies from any of your Trakt lists.
 - Add/Remove shows from any of your Trakt lists.
 - Get and readout popular lists supported lists are
     - Box Office
     - Trending
     - Popular
     - Watched
     - Collected
     - Anticipated
 - Add all missing movies/shows from the supported lists
 - Change your default list (initally this is set to watchlist)
     - This lets you save time later by not have to mention the list you want to add too
 - Send notifications to Discord/Slack about the shows/movies added
 

## Installation

You will need to create a Trakt.tv app from [here](https://trakt.tv/oauth/applications) to get your Client ID & Client Secret.

You will need both when you create your own Alexa app [here](https://developer.amazon.com/alexa/console/ask)

You need to enable account linking in your Alexa app,
settings should look something like this

![sample linking info ](sample.png)

With that done, You can use the JSON editor and copy all of package.json into the JSON editor

After that you need to upload the lambda folder to either Alexa hosted or your own host.
You will need to edit config.py to your own liking but most importantly remember to set your Trakt.tv API key with

```client_id = "your-api-key-goes-here"```
Don't remove the quotes!


Save & build and then deploy, and you should be good to enable the app in your Alexa app.

>"SKILLS AND GAMES" -> "Your Skills" -> "Dev"

Enabling the app should take you to trakt.tv where you login and grants your own app access to your trakt.tv account.

## Usage
### Adding/removing movies or shows
```python
"Alexa tell %myinvocationname to add the movie iron man"

"Alexa tell %myinvocationname to add the movie iron man to my list 'test' "

"Alexa tell %myinvocationname to remove the movie iron man"

"Alexa tell %myinvocationname to add the show The walking dead"
```
### Changing your default list
```python
"Alexa tell %myinvocationname set my list to watch list"

"Alexa tell %myinvocationname set my list to 'example'"

```
### Finding what's on your calendar
```python
"Alexa ask %myinvocationname what is on Trakt today"

"Alexa ask %myinvocationname what movies are on tomorrow"

"Alexa ask %myinvocationname what shows are on trakt next week"

```

### Finding if a movie or show is on your list
```python
"Alexa ask %myinvocationname if the movie Avatar on a list"

"Alexa ask %myinvocationname if the show The walking dead on a list"

```


### Getting the popular list (this only works with movies)
```python
"Alexa ask %myinvocationname Check the list box office"

"Alexa ask %myinvocationname Check the list trending"

"Alexa ask %myinvocationname Check the list popular"

"Alexa ask %myinvocationname Check the list watched"

"Alexa ask %myinvocationname Check the list collected"

"Alexa ask %myinvocationname Check the list Anticipated"
```

### This app/skill uses the Trakt.tv API 

<img src="https://raw.githubusercontent.com/1337-server/Tracked-media/master_1/assets/images/trakt-wide-red-black.png" width="300" />

## License
[MIT](https://choosealicense.com/licenses/mit/)

## The reason for this skill
I needed a way to add movies/shows from alexa to radarr/sonarr but there was no app/skill or source code that didnt require opening your own server up to the internet.
This gets around that by only having other apps read from the trakt.tv lists and removes the need to open ports on your server.
