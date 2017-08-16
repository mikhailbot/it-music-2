# IT Music v2

> Entrance music, for IT folks

### Build Setup

``` bash
# install dependencies
yarn # npm install

# serve with hot reload at localhost:9080
yarn run dev # npm run dev

# build electron application for production
yarn run build # npm run build

# lint all JS/Vue component files in `src/`
yarn run lint # npm run lint

```

### Overview
This is a very simple app--tap your card and get some entrance music as you enter the office!

There will be two primary modes:

1. Active listening mode--waiting for someone to tap their card
2. Self serve administration--allow users to add themselves to the app as well as change their song preference

#### Active Listening Mode
This mode will be relatively simple. It will listen for keyboard input (obtained from the card reader) and check if it exists for a given user. If it does we'll play their intro music, if not we'll do nothing. Taps while music is playing will be ignored as well.

#### Self Serve Administration
The heart of the app will live here. The goal is to allow people to add themselves as well as upload new song clips to be played when they tap their card. Self management is key here. The tapping of your card will act as a form of authentication to edit the settings for our particular users.

The primary administration screen will give users two options--upload a new song or add themselves as an user.

##### Adding Users and Songs
Users will have an account saved in a local db of some kind (linvodb3 mostly). It'll include their ID number obtained from tapping their card, as well as a reference to a music file to be played when they do.

They can attempt to add themselves by tapping their card, and selecting an existing song or upload a new song. Song lengths will be checked on upload and limited to 25 seconds. We'll then copy the song to a configuration spot for safe keeping and add it to the db.

If the user already exists they can tap their card and choose a different song or upload a new one. Songs will be shared amongst all users for simplicity sake.

The user edit screen will require the tapping of a card and that user screen will be presented. Access to the "URL bar" isn't possible so it should be safe to assume you can't edit someones song without their card.

#### User Accounts
```json
{
  "userId": 1234567890,
  "songId": 1
}

```

#### Songs
```json
{
  "songId": 1,
  "songPath": "/path/to/song.mp3"
}
```
