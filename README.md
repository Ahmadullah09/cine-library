# cine library
Cine Diary
A minimal personal movie/series/anime diary.
Run it from this folder: python3 -m http.server 8080
Open http://localhost:8080 (don't double-click the file — Google sign-in won't work from `file://`).
1. OMDb key
Get a free key at https://www.omdbapi.com/apikey.aspx (they email it to you), then paste it in Settings.
2. Google Drive sync (one-time setup)
Go to https://console.cloud.google.com and create a project.
APIs & Services → Library → enable Google Drive API.
OAuth consent screen → External, add yourself as a test user.
Credentials → Create credentials → OAuth client ID → Web application.
Under Authorised JavaScript origins, add `http://localhost:8080`.
Copy the Client ID into Settings → Google OAuth Client ID, then press Save & connect Drive.
Every change is saved to `cine-diary.json` in your Drive (a few seconds after you edit). The app only has access to files it created (`drive.file` scope). The pill in the header shows sync status; click it to sync manually or reconnect (Google tokens last about an hour).
Data is also cached in the browser, so the site still works offline and merges with Drive when it reconnects (newest edit per title wins).
Using it
+ Add → pick a category (Movies/TV Series/Anime Movies/Anime Series), search, add to Watchlist or Watched. OMDb has no "anime" type, so you choose the category yourself.
Mark as watched on any watchlist card.
Click a card for details, original ratings (IMDb, Rotten Tomatoes, Metacritic) and your own 0–10 ratings for plot, cast, world-building, soundtrack, cinematography and impact. The average is shown out of 10.
Settings also have JSON export/import for backups.
