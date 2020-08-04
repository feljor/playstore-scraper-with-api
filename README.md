# playstore-scraper-with-api
PlayStore Scraper with Restful API using Node.js

## Documentation
Available methods:
- [getApps](#getapps): Retrieves the full detail of an application.

### getApps
Retrieve a list of applications from one of the collections at Google Play. Options:

* `collection` (optional, defaults to `collection=topselling_free`): the Google Play collection that will be retrieved. Available options are { **topselling_free, topselling_paid, topgrossing, movers_shakers, topselling_free_games, topselling_paid_games, topselling_grossing_games, topselling_new_free, topselling_new_paid, topselling_new_free_games, topselling_new_paid_games** }.
* `category` (optional, defaults to no category): the app category to filter by. Available options are { **APPLICATION, ANDROID_WEAR, ART_AND_DESIGN, AUTO_AND_VEHICLES, BEAUTY, BOOKS_AND_REFERENCE, BUSINESS, COMICS, COMMUNICATION, DATING, EDUCATION, ENTERTAINMENT, EVENTS, FINANCE, FOOD_AND_DRINK, HEALTH_AND_FITNESS, HOUSE_AND_HOME, LIBRARIES_AND_DEMO, LIFESTYLE, MAPS_AND_NAVIGATION, MEDICAL, MUSIC_AND_AUDIO, NEWS_AND_MAGAZINES, PARENTING, PERSONALIZATION, PHOTOGRAPHY, PRODUCTIVITY, SHOPPING, SOCIAL, SPORTS, TOOLS, TRAVEL_AND_LOCAL, VIDEO_PLAYERS, WEATHER, GAME, GAME_ACTION, GAME_ADVENTURE, GAME_ARCADE, GAME_BOARD, GAME_CARD, GAME_CASINO, GAME_CASUAL, GAME_EDUCATIONAL, GAME_MUSIC, GAME_PUZZLE, GAME_RACING, GAME_ROLE_PLAYING, GAME_SIMULATION, GAME_SPORTS, GAME_STRATEGY, GAME_TRIVIA, GAME_WORD, FAMILY, FAMILY_ACTION, FAMILY_BRAINGAMES, FAMILY_CREATE, FAMILY_EDUCATION, FAMILY_MUSICVIDEO, FAMILY_PRETEND** }.
* `age` (optional, defaults to no age filter): the age range to filter the apps (only for FAMILY and its subcategories). Available options are `age.FIVE_UNDER`, `age.SIX_EIGHT`, `age.NINE_UP`.
* `num` (optional, defaults to 500): the amount of apps to retrieve.
* `lang` (optional, defaults to `'en'`): the two letter language code used to retrieve the applications.
* `country` (optional, defaults to `'us'`): the two letter country code used to retrieve the applications.
* `fullDetail` (optional, defaults to `false`): if `true`, an extra request will be made for every resulting app to fetch its full detail.

Get Apps without any parameters:

```http
GET /api/apps/
```
Response:

```"results": [
        {
            "title": "TikTok - Make Your Day",
            "appId": "com.zhiliaoapp.musically",
            "url": "http://mercipro-scraper.herokuapp.com/api/apps/com.zhiliaoapp.musically",
            "icon": "https://lh3.googleusercontent.com/z5nin1RdQ4UZhv6fa1FNG7VE33imGqPgC4kKZIUjgf_up7E-Pj3AaojlMPwNNXaeGA",
            "developer": {
                "devId": "TikTok Inc.",
                "url": "http://mercipro-scraper.herokuapp.com/api/developers/TikTok%20Inc."
            },
            "developerId": "TikTok+Inc.",
            "priceText": "FREE",
            "price": 0,
            "free": true,
            "summary": "Real People. Real Videos.",
            "scoreText": "4.1",
            "score": 4.0861216,
            "playstoreUrl": "https://play.google.com/store/apps/details?id=com.zhiliaoapp.musically",
            "permissions": "http://mercipro-scraper.herokuapp.com/api/apps/com.zhiliaoapp.musically/permissions",
            "similar": "http://mercipro-scraper.herokuapp.com/api/apps/com.zhiliaoapp.musically/similar",
            "reviews": "http://mercipro-scraper.herokuapp.com/api/apps/com.zhiliaoapp.musically/reviews"
        },
        {
            "title": "ZOOM Cloud Meetings",
            "appId": "us.zoom.videomeetings",
            "url": "http://mercipro-scraper.herokuapp.com/api/apps/us.zoom.videomeetings",
            "icon": "https://lh3.googleusercontent.com/1DqxbUca62LmV1ehZirHGWYBef9Jrtl3DhZ4m6YBnWCUX-XNr3lcnYKb31R-7ukpKAw",
            "developer": {
                "devId": "zoom.us",
                "url": "http://mercipro-scraper.herokuapp.com/api/developers/zoom.us"
            },
            "developerId": "zoom.us",
            "priceText": "FREE",
            "price": 0,
            "free": true,
            "summary": "Zoom is a free HD meeting app with video and screen sharing for up to 100 people",
            "scoreText": "3.8",
            "score": 3.757078,
            "playstoreUrl": "https://play.google.com/store/apps/details?id=us.zoom.videomeetings",
            "permissions": "http://mercipro-scraper.herokuapp.com/api/apps/us.zoom.videomeetings/permissions",
            "similar": "http://mercipro-scraper.herokuapp.com/api/apps/us.zoom.videomeetings/similar",
            "reviews": "http://mercipro-scraper.herokuapp.com/api/apps/us.zoom.videomeetings/reviews"
        }
     ]
```
Exemple: To get a list of top selling action games in CANADA with full detail here's how the request will be.

```http
GET /api/apps/?fullDetail=true&collection=topselling_paid&category=GAME_ACTION&country=ca
```


Get an app detail

```http
GET /api/apps/fr.hdss/
```


Get app required permissions with full descriptions

```http
GET /api/apps/fr.hdss/permissions/
```

Get similar apps

```http
GET /api/apps/fr.hdss/similar/
```

Get an app's reviews

```http
GET /api/apps/fr.hdss/reviews/
```

Search apps

```http
GET /api/apps/?q=hdss
```

Get search suggestions for a partial term

```http
GET /api/apps/?suggest=face
```

Get apps by developer

```http
GET /api/developers/MerciPro%20Inc./
```
