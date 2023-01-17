# Pre-requisite and deployment instructions
## Python (Minimum version 3.9.5)
  1. Download python from https://python.org
  2. To check if its installed correctly, open CMD, type python. The version number should show up.
  
## Python libraries 
  1. GSpread. In CMD, enter pip install gspread
  3. oauth2client. In CMD, enter pip install oauth2client
  5. python telegram bot. In CMD, enter pip install python-telegram-bot --upgrade
  4. pytz. In CMD, enter pip install pytz
    
## Integrated Development Environment(IDE) for editing python codes
  1. Personally, I just use notepad++. You can use visual studio, pycharm or IDLE. To each their own.
  
## Google Cloud for Google Sheet
  1. Create a Google Sheet
  2. Go to console.cloud.google.com
  3. Create new project and give it a relavant name.
  4. Go into the new project created.
  5. Go to API & Services.
  6. Go to library and search google drive and click enable.
  7. Click create credentials.
  8. Select Google Drive API in option "Which API are you using?". 
  9. Select Web Server in option "Where will you be calling the API from?".
  10. Select Application data in option "What data will you be accessing?".
  11. Select "No, I will not be using them." in the option "Are you planning to use this API with App engine or Compute engine?".
  12. Click "What credentials do I need?" button.
  13. Fill up the service account name. For the role select project > editor. MAKE SURE JSON IS SELECTED. Click continue. A credential file will be downloaded(Please keep the file save. Rename the file to creds.json).
  14. Go to API Library and enable Google Sheets API.
  15. Go to the JSON file(from step 13) that is downloaded, get the client_email value.
  16. Go to the Google sheet that has been created in step 1. Share the sheet to the client email that is from the JSON file.
  
## Git
  1. Download git from https://git-scm.com/
  2. To check if its installed correctly, open CMD, type git. git usage and help will show up.

## Creating Telegram Bot
  1. Search for @Botfather on telegram. /start, / newbot , give it a name and username.
  2. Select the bot and get the API Token. Save the API Token (It will be used in the python codes).
  
## Heroku[^1]
  1. Go to heroku and create an account(Account is free).
  2. Set primary development language as python.
  3. Install heroku CLI (https://devcenter.heroku.com/articles/heroku-cli).
  4. Open CMD, type heroku login. Press any key to open the browser to login or q to exit.
  5. Go back to the CMD and it will show that heroku is logged in.
  6. In the same CMD, change directory(CD) to the path that the bot will be created at.
  7. In the same CMD, type heroku create. A webapp name will be created.  
       Webapp & Webhook example  
       Webapp Name: aaaaa  
       Webhook URL: https://aaaaa.herokuapp.com/  
  8. In the same CMD, type heroku config:set TOKEN = XXXXXXXXX (replace XXXXXXXXX with telegram bot token)
  9. Deployment of codes after editing
       Step 1. go to folder location and type CMD in the URL path
       Step 2. heroku login
       Step 3. git init
       Step 4. git add .
       Step 5. git commit -m "Comments"
       Step 6. git push heroku master --force
  10. Go to heroku website(https://id.heroku.com/login), click on the Webapp name.
  11. Click configure add ons and add Heroku Scheduler.
  12. Add the following command into Heroku Scheduler.```$curl -n -X DELETE https://api.heroku.com/apps/WebAppName/dynos \n -H "Content Type: application/json \n -H "Accept: application/vnd.heroku+json; version=3" \n -H "Authorization: Bearer 06c5ffe1-8fae-4d95-9e25-9e9fbe294191"```  
  
## Uptimerobot (uptimerobot.com)
  1. Create an account. Log in after creating the account.
  2. Click add new monitor.
  3. Monitor type select HTTP(s), leave Friendly name empty
  4. For URL (or IP) field, enter https://WebAppName.herokuapp.com
  5. Leave the monitoring interval as it is.
  6. To ensure that the service is running, login to heroku CLI, after logging in, enter heroku logs -t

---------------------

[^1]: Heroku will not charge any fees as the bot will be running on a free dyno, but credit card is required for verification purposes. It is necessary to verify the account in order to keep the bot up 24/7, as using free add ons is required for the bot to work properly.
