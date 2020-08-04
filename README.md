# playstore-scraper-with-api
PlayStore Scraper with Restful API using Node.js

## Documentation
Available methods:
- [getApps](#getapps): Retrieve a list of applications from one of the collections at Google Play.
- [getAppDetail](#getappdetail): Retrieves the full detail of an application.

### getApps
Retrieve a list of applications from one of the collections at Google Play. Options:

* `collection` (optional, defaults to `collection=topselling_free`): the Google Play collection that will be retrieved. Available options are { **topselling_free, topselling_paid, topgrossing, movers_shakers, topselling_free_games, topselling_paid_games, topselling_grossing_games, topselling_new_free, topselling_new_paid, topselling_new_free_games, topselling_new_paid_games** }.
* `category` (optional, defaults to no category): the app category to filter by. Available options are { **APPLICATION, ANDROID_WEAR, ART_AND_DESIGN, AUTO_AND_VEHICLES, BEAUTY, BOOKS_AND_REFERENCE, BUSINESS, COMICS, COMMUNICATION, DATING, EDUCATION, ENTERTAINMENT, EVENTS, FINANCE, FOOD_AND_DRINK, HEALTH_AND_FITNESS, HOUSE_AND_HOME, LIBRARIES_AND_DEMO, LIFESTYLE, MAPS_AND_NAVIGATION, MEDICAL, MUSIC_AND_AUDIO, NEWS_AND_MAGAZINES, PARENTING, PERSONALIZATION, PHOTOGRAPHY, PRODUCTIVITY, SHOPPING, SOCIAL, SPORTS, TOOLS, TRAVEL_AND_LOCAL, VIDEO_PLAYERS, WEATHER, GAME, GAME_ACTION, GAME_ADVENTURE, GAME_ARCADE, GAME_BOARD, GAME_CARD, GAME_CASINO, GAME_CASUAL, GAME_EDUCATIONAL, GAME_MUSIC, GAME_PUZZLE, GAME_RACING, GAME_ROLE_PLAYING, GAME_SIMULATION, GAME_SPORTS, GAME_STRATEGY, GAME_TRIVIA, GAME_WORD, FAMILY, FAMILY_ACTION, FAMILY_BRAINGAMES, FAMILY_CREATE, FAMILY_EDUCATION, FAMILY_MUSICVIDEO, FAMILY_PRETEND** }.
* `age` (optional, defaults to no age filter): the age range to filter the apps (only for FAMILY and its subcategories). Available options are `age.FIVE_UNDER`, `age.SIX_EIGHT`, `age.NINE_UP`.
* `num` (optional, defaults to 500): the amount of apps to retrieve.
* `lang` (optional, defaults to `'en'`): the two letter language code used to retrieve the applications.
* `country` (optional, defaults to `'us'`): the two letter country code used to retrieve the applications.
* `fullDetail` (optional, defaults to `false`): if `true`, an extra request will be made for every resulting app to fetch its full detail.

Request:

```http
GET /api/apps/
```
Response:

```
{
  "results": [
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
  }
```
Request with Params: Get top selling action games in Canada

```http
GET /api/apps/?fullDetail=true&collection=topselling_paid&category=GAME_ACTION&country=ca
```

### getAppDetail
Retrieves the full detail of an application. Options:

* `appId`: (as a path in url) the Google Play id of the application (the `?id=` parameter on the url).
* `lang` (optional, defaults to `'en'`): the two letter language code in which to fetch the app page.
* `country` (optional, defaults to `'us'`): the two letter country code used to retrieve the applications. Needed when the app is available only in some countries.

Request:

```http
GET /api/apps/fr.hdss/
```
Response:

```
{
    "title": "HDSS.TO - Anciens Films et Séries de 1900 - 2000",
    "description": "Nous avons conçu cette application avec un seul objectif dans la tête: \"Vous donner de quoi vous divertir avec des anciens Films et Séries TV de 1900 à 2000\". N'est-ce pas une meilleure idée ?\r\n\r\nAvec l'application HDSS.TO - Anciens Films et Séries TV en Français, oubliez tous vos moments de stress et concentrez-vous devant l'écran de votre smartphone Android pour Regarder les meilleurs Films qui ont diverti votre jeunesse.\r\n\r\nLE CONTENU DE L'APPLICATION\r\n==========================\r\n\r\nLa nostalgie est tout ce qui nous attire le plus. Pour cela, nous publions tous vos anciens films populaires dans cette application. Et comme nous nous soucions également du temps d'attente, nous avons optimisé le lecteur de l'application \"HDSS.TO - Anciens Films Complet\" pour une lecture plus rapide et avons ajouté 3 serveurs supplémentaires.\r\n\r\nLa source de nos films est souvent sur des serveurs sûrs et sécurisés comme par exemple YouTube, Viméo, Dailymotion, etc... \r\n\r\nAvec notre application, vous pouvez regarder des anciens films français gratuits sans violation des droits d'auteur. Lorsque vous ouvrez l'application, vous trouverez un guide. En lisant notre guide, vous apprendrez comment utiliser l'application. Une fois que vous utilisez notre guide, vous pouvez commencer à regarder des films en ligne gratuitement en français.\r\n\r\nLES FONCTIONNALITES\r\n====================\r\n\r\nGrâce à cette application vous bénéficierez des plusieurs avantages tels que:\r\n\r\n- La mise à jour régulière des vieux films gratuits à regarder.\r\n- Un moteur de recherche intégré pour trouver facilement les vieux films complets que vous cherchez.\r\n- Une suggestion des films qui pourront vous intéressé en plus de celui que vous regardez actuellement\r\n- Une possibilité de sauvegarder vos vieux films préférés ou de les mettre dans la liste des souhaits pour les regarder plus tard.\r\n- Capacité de gérer votre compte directement depuis l'application\r\n- Accéder à des films complets en Français par genre et par popularité\r\n- Et plus encore.\r\n\r\nVIE PRIVEE ET DONNEES PERSONNELLES\r\n==================================\r\n\r\nNous collectons certaines données à propos de vous d'une manière facultative afin de mieux vou sproposer nos services.\r\n\r\nPar exemple, il peut nous arriver pendant votre navigation de vous demander votre Email si vous décidez de créer un compte dans l'application.\r\n\r\nSi vous le souhaitez, après avoir créer votre profil dans l'application, vous pouvez également vous décider d'ajouter votre photo et toutes ses données sont stockées dans notre base des données sans aucun but nocif ou d'utilisation incorrect.\r\n\r\nPour votre vie privée, vous pouvez décider de supprimer otre compte de notre plateforme si vous ne voyez plus son utilité, mais rassurez-vous une fois encore qu'aucune de vos données n'est partagée à des tiers pour une raison quelconque.\r\n\r\nNOTRE SITE WEB\r\n==============\r\n\r\nCette application \"HDSS.TO - Anciens Films Gratuits\" est lié sur un site web avec les mêmes contenus. Si vous êtes connecté sur votre PC, vous pouvez trouver directement vos films préférés sur votre PC en accédant sur le lien suivant (https://lestreaming.fr).\r\n\r\nQue vous soyez en France, Belgique, Suisse ou tout autre pays francophone, vous pouvez regarder des films gratuitement en Streaming dans la version française ou avec des sous-titres français.",
    "descriptionHTML": "Nous avons conçu cette application avec un seul objectif dans la tête: &quot;Vous donner de quoi vous divertir avec des anciens Films et Séries TV de 1900 à 2000&quot;. N&#39;est-ce pas une meilleure idée ?<br><br>Avec l&#39;application HDSS.TO - Anciens Films et Séries TV en Français, oubliez tous vos moments de stress et concentrez-vous devant l&#39;écran de votre smartphone Android pour Regarder les meilleurs Films qui ont diverti votre jeunesse.<br><br>LE CONTENU DE L&#39;APPLICATION<br>==========================<br><br>La nostalgie est tout ce qui nous attire le plus. Pour cela, nous publions tous vos anciens films populaires dans cette application. Et comme nous nous soucions également du temps d&#39;attente, nous avons optimisé le lecteur de l&#39;application &quot;HDSS.TO - Anciens Films Complet&quot; pour une lecture plus rapide et avons ajouté 3 serveurs supplémentaires.<br><br>La source de nos films est souvent sur des serveurs sûrs et sécurisés comme par exemple YouTube, Viméo, Dailymotion, etc... <br><br>Avec notre application, vous pouvez regarder des anciens films français gratuits sans violation des droits d&#39;auteur. Lorsque vous ouvrez l&#39;application, vous trouverez un guide. En lisant notre guide, vous apprendrez comment utiliser l&#39;application. Une fois que vous utilisez notre guide, vous pouvez commencer à regarder des films en ligne gratuitement en français.<br><br>LES FONCTIONNALITES<br>====================<br><br>Grâce à cette application vous bénéficierez des plusieurs avantages tels que:<br><br>- La mise à jour régulière des vieux films gratuits à regarder.<br>- Un moteur de recherche intégré pour trouver facilement les vieux films complets que vous cherchez.<br>- Une suggestion des films qui pourront vous intéressé en plus de celui que vous regardez actuellement<br>- Une possibilité de sauvegarder vos vieux films préférés ou de les mettre dans la liste des souhaits pour les regarder plus tard.<br>- Capacité de gérer votre compte directement depuis l&#39;application<br>- Accéder à des films complets en Français par genre et par popularité<br>- Et plus encore.<br><br>VIE PRIVEE ET DONNEES PERSONNELLES<br>==================================<br><br>Nous collectons certaines données à propos de vous d&#39;une manière facultative afin de mieux vou sproposer nos services.<br><br>Par exemple, il peut nous arriver pendant votre navigation de vous demander votre Email si vous décidez de créer un compte dans l&#39;application.<br><br>Si vous le souhaitez, après avoir créer votre profil dans l&#39;application, vous pouvez également vous décider d&#39;ajouter votre photo et toutes ses données sont stockées dans notre base des données sans aucun but nocif ou d&#39;utilisation incorrect.<br><br>Pour votre vie privée, vous pouvez décider de supprimer otre compte de notre plateforme si vous ne voyez plus son utilité, mais rassurez-vous une fois encore qu&#39;aucune de vos données n&#39;est partagée à des tiers pour une raison quelconque.<br><br>NOTRE SITE WEB<br>==============<br><br>Cette application &quot;HDSS.TO - Anciens Films Gratuits&quot; est lié sur un site web avec les mêmes contenus. Si vous êtes connecté sur votre PC, vous pouvez trouver directement vos films préférés sur votre PC en accédant sur le lien suivant (https://lestreaming.fr).<br><br>Que vous soyez en France, Belgique, Suisse ou tout autre pays francophone, vous pouvez regarder des films gratuitement en Streaming dans la version française ou avec des sous-titres français.",
    "summary": "Here is the best app to watch old movies from the 20th century",
    "installs": "50,000+",
    "minInstalls": 50000,
    "maxInstalls": 62058,
    "score": 3.38,
    "scoreText": "3.4",
    "ratings": 399,
    "reviews": "http://mercipro-scraper.herokuapp.com/api/apps/fr.hdss/reviews",
    "histogram": {
        "1": 111,
        "2": 7,
        "3": 55,
        "4": 63,
        "5": 159
    },
    "price": 0,
    "free": true,
    "currency": "USD",
    "priceText": "Free",
    "offersIAP": false,
    "size": "18M",
    "androidVersion": "4.4",
    "androidVersionText": "4.4 and up",
    "developer": {
        "devId": "MerciPro Inc.",
        "url": "http://mercipro-scraper.herokuapp.com/api/developers/MerciPro%20Inc."
    },
    "developerId": "6529673015364471915",
    "developerEmail": "admin@lestreaming.fr",
    "developerAddress": "82 Ave Patrice Emery Lumumba, Bukavu, République démocratique du Congo",
    "privacyPolicy": "https://lestreaming.fr/page/confidentialite",
    "developerInternalID": "6529673015364471915",
    "genre": "Entertainment",
    "genreId": "ENTERTAINMENT",
    "icon": "https://lh3.googleusercontent.com/2f0W1Y3Z59_moDrQApnTiVwp2pmr37VCa2VNxfz9IheOvwCU6epqep2DdWPF36q2Dw",
    "headerImage": "https://lh3.googleusercontent.com/jJQuwmEBd6pbguPwkbqI-RjBzfkEt0AETKBolQglsgekwQtG82SUkN-v9obUQVxTsbw",
    "screenshots": [
        "https://lh3.googleusercontent.com/sc3t2RkK3XlshfkEzfAfu4cQw3wYOU80KmqInupYD3hK0FoWG3j8hp06A1R0O2wEjnEo",
        "https://lh3.googleusercontent.com/C2zQVPno3yMjIlfKTE_j6QOhU702bqNRljipIgANDiHTBVW9gz9kco4_4ag3Z1aj4zc",
        "https://lh3.googleusercontent.com/VFXjnj22muah2WOqVRZnR_KhP7aaWyLIwfhgybgIjI699J6fbJ4vqv5PrmyoK_XLlVS8",
        "https://lh3.googleusercontent.com/su5GzLNX6rZ5eqRgeAhDIy-mollGuGBZjtQfZvYJcf9q_byv6m7QxAF3VdZrHcurDoE9",
        "https://lh3.googleusercontent.com/o-TzwwnfNtE0r0606h7JcTyXnBv7efFM5fEx0rEUn79Y28hBsTzwROdtrF8g5XhxoLg",
        "https://lh3.googleusercontent.com/fM4N5xXtnvoeDZkLpjqWuQNDro1BNEunpdDQ5hrT_kp2Tk5yinM-q9WR2yR7eHqoQn4"
    ],
    "contentRating": "Everyone",
    "adSupported": true,
    "released": "Feb 25, 2020",
    "updated": 1593804944000,
    "version": "2.9",
    "recentChanges": "- Recherche avancée et Instantanée<br>- Correction de tous les bugs<br>- Ajout des serveurs supplémentaires<br>- Aucune inscription requise<br>- Aucune pubs à caractère adulte<br>- Aucune redirection pendant la lecture<br>- Suppression du formulaire de demande des films<br>- Autres améliorations",
    "comments": [
        "Very bad app doesn't work !!!",
        "I love this app😍😍😍",
        "You can't research the movie that you want",
        "bad app",
        "Nice"
    ],
    "editorsChoice": false,
    "appId": "fr.hdss",
    "url": "http://mercipro-scraper.herokuapp.com/api/apps/fr.hdss",
    "playstoreUrl": "https://play.google.com/store/apps/details?id=fr.hdss&hl=en&gl=us",
    "permissions": "http://mercipro-scraper.herokuapp.com/api/apps/fr.hdss/permissions",
    "similar": "http://mercipro-scraper.herokuapp.com/api/apps/fr.hdss/similar"
}
```

Get an app detail in swahili

```http
GET /api/apps/fr.hdss/?lang=sw
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
