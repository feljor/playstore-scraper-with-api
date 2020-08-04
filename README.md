# playstore-scraper-with-api
PlayStore Scraper with Restful API using Node.js

Get the top free apps (default list)
```http
GET /api/apps/
```

Get the top free apps with full detail

```http
GET /api/apps/?fullDetail=true
```

Get the top selling action games in russia

```http
GET /api/apps/?collection=topselling_paid&category=GAME_ACTION&country=ru
```

Get an app detail

```http
GET /api/apps/fr.hdss/
```

Get an app detail in french

```http
GET /api/apps/fr.hdss/?lang=fr
```

Get app required permissions with full descriptions

```http
GET /api/apps/fr.hdss/permissions/
```

Get app required permissions (short list)

```http
GET /api/apps/fr.hdss/permissions/?short=true
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
