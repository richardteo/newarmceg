# Code Components


## Changing sheet name

```sheet = client.open('Seletar SFT Records').worksheet('SHEETNAME')```

The line of code above will direct data to the specific sheet

------------

## For Adding new location or activity
```
  activity_dict = {'1': "Run", '2': "Gym", '3': "Sports and Games", '4':'Statics'}
  route_dict = {'1': "Stadium", '2': "1km", '3': "2km", '4': "3.2km", '5': "MEC"}
  location_dict = {'1': "Stadium", '2': "Parade Square", '3': "Buaya Square", '4': "Training Sheds", '5': "MEC"}
```
  The above data types is called a dictionary. If there are additional location or activity to be added this will be the place to add. 
```
  ROUTECONFIRMATION: [MessageHandler(Filters.regex('^[1-5]$'), route_confirmation)]
  LOCATIONCONF: [MessageHandler(Filters.regex('^[1-5]$'), location)]
  CONFIRMATION: [MessageHandler(Filters.regex('^[1-5]$'), confirmation)]
```
  And increase the number in [1-5] in Filters.regex('^[1-5]$') component accordingly based on the dictionary

```
  def route_confirmation(update: Update, _: CallbackContext):
    if update.message.text == '1':
        userID = str(update.message.chat_id)
        userID_database[userID].append(activity_dict[update.message.text])
        reply_keyboard = [['1','2','3','4','5']]
        update.message.reply_text(
            'Which route will you be running today? \n'
            'Please choose an option \n\n'
            '1: Stadium \n'
            '2: 1km \n'
            '3: 2km \n'
            '4: 3.2km \n'
            '5: MEC \n'
            'Send /cancel to stop talking to me.',
            reply_markup=ReplyKeyboardMarkup(reply_keyboard),
        )
        return CONFIRMATION

    elif update.message.text == '4':
        userID = str(update.message.chat_id)
        userID_database[userID].append(activity_dict[update.message.text])
        reply_keyboard = [['1','2','3','4','5']]
        update.message.reply_text(
            'Where will you be doing your statics at?'
            'Please choose an option \n\n'
            '1: Stadium \n'
            '2: Parade Square \n'
            '3: Buaya Square \n'
            '4: Training Sheds \n'
            '5: MEC \n'                       
            'Send /cancel to stop talking to me.',
            reply_markup=ReplyKeyboardMarkup(reply_keyboard),
        )
        return LOCATIONCONF
```
  Also modify the codes according. In reply_keyboard(Add in the addtional number) and update.message.reply_text(Add in the actual name of the location).

---------

## Password management

```if update.message.text == 'PASSWORD'```
The code above is where the password is stored

---------

## Modifying bot's reply

```update.message.reply_text("something inside")```

Anything with the code, the bot will reply with whatever is inside the brackets
