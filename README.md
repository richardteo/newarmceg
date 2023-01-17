# Seletar camp's SFT Bot

## This repository contains SFT bots for the below units.
1. ARMCEG
2. BETC
3. CEC
4. TPTHUBEAST
5. SSPSBN
6. NSMen

--------------



## Bot's flow chart

### Start process
```
/start > Sign in > Answer health check questionnaire > Enter name > Select activity > if activity == ('run') > Select route/location > Confirm details > store details in Google sheets
                                                                                    > else confirm details > store details in Google sheets
```

### End process
```
/end > Confirm exercise end
```

--------------


### Cancel process

If an option No is given, upon pressing it, it will cancel the whole process.
```
/cancel ``` command will cancel the whole process of the sign in.
