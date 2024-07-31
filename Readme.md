# How this works

you are blacklisted much differently on pretendo, if you ever tried using a different lfcs_b that doesnt match your 3ds on pretendo, you notice you will get an error. 

# what is blacklisted on their end
# Online Play: (Matchmaking)
## Form (Easier for your eyes):

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
action=TE9HSU4%2A&apinfo=INSERTAPINFOHERE&bssid=INSERTBSSIDHERE&csnum=INSERTCSNUMHERE&devname=INSERTDEVNAMEHERE&devtime=INSERTDEVTIMEHERE&fcdcert=INSERTFCDCERTHERE&fpdver=INSERTFPDVERHERE&gamecd=INSERTGAMECDHERE&gameid=INSERTGAMEIDHERE&gamever=INSERTGAMEVERHERE&ingamesn=&lang=INSERTLANGHERE&macadr=INSERTMACADR&makercd=INSERTMAKERCDHERE&mediatype=INSERTMEDIATYPEHERE&region=INSERTREGIONHERE&sdkver=INSERTSDKVERHERE&servertype=INSERTSERVERTYPEHERE&titleid=INSERTTITLEIDHERE&uidhmac=INSERTUIDHMACHERE&unitcd=INSERTUNITCDHERE&userid=INSERTUSERIDHERE
```

# Other stuff such as pnid linking and miiverse:
## Form (easier for your eyes)

GET Request:
  * X-Nintendo-Device-Cert

  * X-Nintendo-Unique-ID

  * X-Nintendo-Client-ID

  * X-Nintendo-Device-ID

  * X-Nintendo-Serial-Number

  * X-Nintendo-Client-Secret

# Body (what is sent to pretendo)

Headers:

GET REQUEST

```

Host: account.pretendo.cc

X-Nintendo-Platform-ID: INSERTPLATFORMIDHERE (Example: 0)

X-Nintendo-Device-Type: INSERTDEVICETYPEHERE (Example: 2)

X-Nintendo-Device-ID: INSERTDEVICEIDHERE 

X-Nintendo-Serial-Number: INSERTSERIALNUMBERHERE

X-Nintendo-System-Version: INSERTSYSVERSIONHERE (Example: 0320)

X-Nintendo-Region: INSERTREGIONHERE (Example: 2)

X-Nintendo-Country: INSERTCOUNTRYHERE (Example: US)

Accept-Language: en

X-Nintendo-Client-ID: INSERTCLIENTIDHERE

X-Nintendo-Client-Secret: INSERTCLIENTSECRETHERE

Accept: */*" 

X-Nintendo-API-Version: INSERTAPIVERHERE (Example: 0100) 

X-Nintendo-FPD-Version: INSERT FPDVER HERE (Example: 0000)

X-Nintendo-Environment: INSERTENVHERE (Example: L1)

X-Nintendo-Title-ID: INSERTTITLEIDHERE (Example: 000400100002C000)

X-Nintendo-Unique-ID: INSERTUNIQUEIDHERE

X-Nintendo-Application-Version:INSERTAPPVERSIONHERE (Example: 0003)

X-Nintendo-Device-Model: INSERTDEVICEMODELHERE (Example: RED)

X-Nintendo-Device-Cert: INSERTDEVICECERTHERE 
```
Example Url: https://104.25.1.76/v1/api/admin/mapped_ids?input_type=user_id&output_type=pid&input=INSERTINPUTHERE


# Paths

## Matchmaking: (Online Play)

* https://104.25.2.76:443/ac//
* https://104.25.1.76:443/ac//

Structure:
```
104.25.2.76:443
  /ac/
      /
```

Structure:
```
104.25.1.76:443
  /ac/
      /
```
## Other stuff such as pnid linking and miiverse:
Structure:
```
  104.25.2.76:443/
  
    /v1/
  
      /api/
    
          /admin/ (Linking in general)
          
              mapped_ids?input_type=user_id&output_type=pid&input=INSERTINPUTHERE
        
          /oauth20/
        
               /access_token/ (Generated when trying to link pnid)
            
                   /generate
                
          /people/ (Selecting Mii from your 3ds or stored on the server)
            
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
          
              mapped_ids?input_type=user_id&output_type=pid&input=INSERTINPUTHERE
        
          /oauth20/
        
               /access_token/ (Generated when trying to link pnid)
            
                   /generate
                
          /people/ (Selecting Mii from your 3ds or stored on the server)
            
                /@me/
                
                    /devices/
                    
                        /@current/
                        
                            /attributes
                
                       /profile

```

# Error codes:
002-2999: An error has occured please try again later (Invalid Info) 

002-0101: High traffic volume error (Invalid Info)

002-0121: Banned (Valid info but blacklisted, i have tried generating one before and got this error before)

No error: Yay your donor info or generated info worked, you are now successfully unbanned

# Notes
If you dont care about pnid linking or miiverse and want to play online on your banned 3ds, ignore the X-Nintendo-Blah-Blah stuff as that is only needed for pnid linking and miiverse
The only question i have from pretendo is how do you know if these are valid? Regex? otherwise you guys clearly have a list of all valid info stored on your servers.

