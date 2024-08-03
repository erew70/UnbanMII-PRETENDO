# How this works

you are blacklisted much differently on pretendo, if you ever tried using a different lfcs_b that doesnt match your 3ds on pretendo, you notice you will get an error. So now you know that bans are handled MUCH differently

# Welcome to Q and A section!
Q. Why wont lfcs_b unbanning work?

A. your bssid, csnum, devname, fcdcert, macadr, uidhmac, and userid wont match the lfcs_b you provide, think of it as logging into your account with your password, except this info wont match when checked against your lfcs_b.

Q. How to unban?

A. Use proxyman or charles to rewrite everything it really isnt that hard

Q. Where to rip info needed for unbanning?

A. You can try ai generated info but i can gurantee you the strings are either too short, invalid, or banned. So its better off you rip info off another 3ds. To rip info you will just have to setup charles and make sure ssl proxying is enabled for *:443 and your good to go. To find these strings, go to 104.25.1.76/ac// or 104.25.2.76/ac// in chls structure and you will find them there :) (use chls rewrite for replacement)

If you get ssl proxying erros then you probably do not have pretendo installed so you probably dont know what your doing so how about you just leave it alone, alright? 

Q. Can i just swap files isnt there some other files to swap?

A. No and you might end up bricking if you repalce ctcert.bin or si_a so dont try that please! (screams stupidy 😵‍💫)

# what is blacklisted on their end
## Online Play: (Matchmaking)
### Form (Easier for your eyes):

* bssid

* csnum

* devname

* fcdcert

* macadr

* uidhmac

* userid

## Body (this is what your 3ds sends to pretendo)

POST REQUEST
```
action=TE9HSU4%2A&apinfo=INSERT_APINFO_HERE&bssid=INSERT_BSSID_HERE&csnum=INSERT_CSNUM_HERE&devname=INSERT_DEVNAME_HERE&devtime=INSERT_DEVTIME_HERE&fcdcert=INSERT_FCDCERT_HERE&fpdver=INSERT_FPDVER_HERE&gamecd=INSERT_GAMECD_HERE&gameid=INSERT_GAMEID_HERE&gamever=INSERT_GAMEVER_HERE&ingamesn=&lang=INSERT_LANGHERE_&macadr=INSERT_MACADR_HERE&makercd=INSERT_MAKERCD_HERE&mediatype=INSERT_MEDIATYPE_HERE&region=INSERT_REGION_HERE&sdkver=INSERT_SDKVER_HERE&servertype=INSERT_SERVERTYPE_HERE&titleid=INSERT_TITLEID_HERE&uidhmac=INSERT_UIDHMAC_HERE&unitcd=INSERT_UNITCD_HERE&userid=INSERT_USERID_HERE
```

## Other stuff such as pnid linking and miiverse:
### Form (easier for your eyes)

GET Request:
  * X-Nintendo-Device-Cert

  * X-Nintendo-Unique-ID

  * X-Nintendo-Client-ID

  * X-Nintendo-Device-ID

  * X-Nintendo-Serial-Number

  * X-Nintendo-Client-Secret

## Body (what is sent to pretendo)

Headers:

GET REQUEST

```

Host: account.pretendo.cc

X-Nintendo-Platform-ID: INSERT_PLATFORMID_HERE (Example: 0)

X-Nintendo-Device-Type: INSERT_DEVICETYPE_HERE (Example: 2)

X-Nintendo-Device-ID: INSERT_DEVICEID_HERE 

X-Nintendo-Serial-Number: INSERT_SERIALNUMBER_HERE

X-Nintendo-System-Version: INSERT_SYSVERSION_HERE (Example: 0320)

X-Nintendo-Region: INSERT_REGION_HERE (Example: 2)

X-Nintendo-Country: INSERT_COUNTRY_HERE (Example: US)

Accept-Language: en

X-Nintendo-Client-ID: INSERT_CLIENTID_HERE

X-Nintendo-Client-Secret: INSERT_CLIENTSECRET_HERE

Accept: */*" 

X-Nintendo-API-Version: INSERT_APIVER_HERE (Example: 0100) 

X-Nintendo-FPD-Version: INSERT_FPDVER_HERE (Example: 0000)

X-Nintendo-Environment: INSERT_ENV_HERE (Example: L1)

X-Nintendo-Title-ID: INSERT_TITLEID_HERE (Example: 000400100002C000)

X-Nintendo-Unique-ID: INSERT_UNIQUEID_HERE

X-Nintendo-Application-Version:INSERT_APPVERSION_HERE (Example: 0003)

X-Nintendo-Device-Model: INSERT_DEVICEMODEL_HERE (Example: RED)

X-Nintendo-Device-Cert: INSERT_DEVICECERT_HERE 
```
Example Url: https://104.25.1.76/v1/api/admin/mapped_ids?input_type=user_id&output_type=pid&input=INSERT_INPUT_HERE


## Paths

### Matchmaking: (Online Play)

* https://104.25.2.76:443/ac//
* https://104.25.1.76:443/ac//

Structure:
```
104.25.2.76:443
  /ac/
      / <-- (this is actually part of the url endpoint its not a slash into a folder)
```

Structure:
```
104.25.1.76:443
  /ac/
      / <-- (this is actually part of the url endpoint its not a slash into a folder)
```
## Other stuff such as pnid linking and miiverse:
Structure:
```
  104.25.2.76:443/
  
    /v1/
  
      /api/
    
          /admin/ (Linking in general)
          
              mapped_ids?input_type=user_id&output_type=pid&input=INSERT_INPUT_HERE
        
          /oauth20/
        
               /access_token/ (Generated when trying to link pnid)
            
                   /generate
                
          /people/ (Your profile settings on your pnid)
            
                /@me/
                
                    /devices/
                    
                        /@current/
                        
                            /attributes
                
                       /profile

```

Structure:
```
  104.25.1.76:443/
  
    /v1/
  
      /api/
    
          /admin/ (Linking in general)
          
              mapped_ids?input_type=user_id&output_type=pid&input=INSERT_INPUT_HERE
        
          /oauth20/
        
               /access_token/ (Generated when trying to link pnid)
            
                   /generate
                
          /people/  (Your profile settings on your pnid)
            
                /@me/
                
                    /devices/
                    
                        /@current/
                        
                            /attributes
                
                       /profile

```

# MISC:
## Mii selection screen (PNID Linking)

NOTE: standard.tga is encrypted or something in some sorts so i cannot view it :(

Structure:
```
37.19.216.130:443
   /mii/
       /INSERT_RANDOM_10_DIGIT_NUMBER_HERE/
                                          /standard.tga

```



## Access token
Check headers for pnid linking its the same thing

# Error codes:
002-2999: An error has occured please try again later (Invalid Info) 

002-0101: High traffic volume error (Invalid Info)

002-0121: Banned (Valid info but blacklisted, i have tried generating one before and got this error before)

No error: Yay your donor info or generated info worked, you are now successfully unbanned

# Notes
If you dont care about pnid linking or miiverse and want to play online on your banned 3ds, ignore the X-Nintendo-Blah-Blah stuff as that is only needed for pnid linking and miiverse

And yes the best way to generate unique info like this is inputting strings like those into ai and asking it to generate simillar ones to that or using scripts like python. There is no way to automate testing if its banned or not so your just gonna have to keep sifting through invalid and banned info till you get a working one.
Also if your using a generated unique info that isnt banned i would like you to know that somewhere in the world, there is a person who has a 3ds and you just generated their info based off of yours. So if you get their info banned, then their 3ds will be banned also. Same goes if you rip info off of donor 3ds

on another note it is probably a good idea to replace all the info instead of just the cert adn uniqueid and stuff because it will see that two different models will be using the same info (this is the disadvantage of generating random strings because you wont know model, country, and other stuff)

The only question i have for pretendo is how do you know if these are valid? Regex? otherwise you guys clearly have a list of all valid info stored on your servers. Because if you dont have these stored on your server or using regex, then you should be able to replace the unique info with random bullshit and get unbanned. Clearly something else is going on because i have tested that and it does not work.



# So how do i unban myself now???
just rewrite everything using charles proxy and replace your values with the new ones. If your using pablos citra use proxifier to get it to use your proxy and turn off access control in charles, if you havent already you can now install pretendo with luma3ds patches and enable these modules:

View --> Debugging --> Toggle LLE Service modules

* Online play: FRD

* PNID Linking: FRD, SSL, NIM, ACT, BOSS, CECD, DLP (HTTP causes issues so dont enable it)

Or for citra if you have donor 3ds your better off just ripping your lfcs_b, si_a, and ctcert.bin from your donor and using that

## Pnid linking errors (this happens because nnid is already linked)

no worries just go to this path: INSERT_USER_FOLDER_HERE/nand/data/SYSID0/sysdata/00010038/

once your in that path rename 00000000 to 10000000


If you dont have a user folder in the same folder as your citra-qt.exe file, then your user folder should be here: C:\Users\YOUR_USER_HERE\AppData\Roaming\Citra
