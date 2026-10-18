# cine library

Cine Diary
A minimal personal movie/series/anime diary.

Part 1: Run the site
Put index.html and README.md in one folder, for example Documents/cine-diary.
Open a terminal in that folder.
Windows: open the folder in File Explorer, click the address bar, type cmd and press Enter.
Mac: right-click the folder and choose “New Terminal at Folder”.
Run python3 -m http.server 8080. On Windows, use python -m http.server 8080 if python3 isn’t found. If you don’t have Python, install it from python.org, or run npx serve -l 8080 if you have Node.
Open http://localhost:8080 in your browser.
Leave the terminal window open while you use the site. Closing it stops the server, and you start it again the same way next time.

Always use the same port (8080). Your browser stores data per address, so a different port looks like an empty diary until Drive sync restores it.

Part 2: Get an OMDb key
Go to omdbapi.com/apikey.aspx.
Choose the FREE plan (1,000 requests a day), enter your email and a short reason, and submit.
Open the email from OMDb and click the activation link. The key doesn’t work until you do.
In Cine Diary, click Settings, paste the key into “OMDb API key” and click Save.
Click + Add, search any title and check that results appear. If you see “Invalid API key!”, the key isn’t activated yet.

At this point the site works fully and saves in your browser. Parts 3 and 4 add the Drive sync.

Part 3: Create the Google client ID
Go to console.cloud.google.com and sign in with the Google account whose Drive you want to use.
Click the project dropdown at the top, then New Project. Name it “Cine Diary” and click Create, then make sure it is selected.
Open the menu, then APIs & Services → Library. Search for Google Drive API, open it and click Enable.
Open APIs & Services → OAuth consent screen. Google may call this “Google Auth Platform” and show a Get started button.
App name: Cine Diary. Support email: your email.
Audience: External.
Contact email: your email. Accept the terms and click Create.
Under Audience (or Test users), click Add users and add your own Gmail address. Leave the app in Testing mode. You never need to publish it, but only listed test users can sign in.
Open Credentials (or Clients) and click Create credentials → OAuth client ID.
Application type: Web application. Name: Cine Diary.
Under Authorised JavaScript origins, click Add URI and enter exactly http://localhost:8080. Don’t add a trailing slash.
Leave “Authorised redirect URIs” empty.
Click Create.
Copy the Client ID. It looks like 123456-abcdef.apps.googleusercontent.com. You don’t need the client secret.

Part 4: Connect Drive
In Cine Diary, open Settings and paste the Client ID into “Google OAuth Client ID”.
Click Save & connect Drive.
A Google popup opens. If your browser blocks it, allow popups for localhost and try again.
Choose your account. You’ll see “Google hasn’t verified this app”. This is normal because it’s your own app. Click Advanced, then Go to Cine Diary (unsafe).
Tick the permission to see and manage the files the app creates, then click Continue. The app can’t see any of your other Drive files.
The pill in the header should change to “Syncing…” and then “Saved to Drive”.
Check by opening drive.google.com. A file called cine-diary.json should be in My Drive.

After that, every change you make saves to Drive a couple of seconds later.

