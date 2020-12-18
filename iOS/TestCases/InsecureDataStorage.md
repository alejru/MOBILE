# Insecure Data Storage
### Important Directories
Take your time to explore these directories very well
```
/var/containers/Bundle/Application/{UUID}
/var/mobile/Containers/Data/Application/{UUID}

```
### Identify Path of Application
```
root# ps aux | grep test
mobile     449   0.4  9.0   686832  46216   ??  Ss    5:03PM   0:05.52 /var/containers/Bundle/Application/57BE5393-74D6-478E-905E-8F131D526897/test.app/test
```
### UUID and UDID
UDID is used for the identification of an iOS Device and UUID for the identification of an iOS application.
`TIP: is case you have difficulties with the UUID iddentification, you could use FILZA to explore the file system and easily identify UUIDs`
### XML and Plist Files
Once the path of the application is identified, find the .plist files and check if there is sensitive information in there.

### SQLite Files
Unless you are using an encrypted variant of SQLite, the data stored in simple SQLite is not secure.
Identify the .sqlite file (or .db):
```
root# pwd
/var/mobile/Containers/Data/Application/63A17000-C8E0-48D3-B81B-F4B4D4866E7B/Documents
ARUTestiOS:/var/mobile/Containers/Data/Application/63A17000-C8E0-48D3-B81B-F4B4D4866E7B/Documents root# ls
credentials.sqlite

```
You could move the .sqlite file to your kali machine where you can open it with sqlite3:
```
[18:22:22] root@kali:~/pentest# scp root@192.168.12.118:/var/mobile/Containers/Data/Application/63A17000-C8E0-48D3-B81B-F4B4D4866E7B/Documents/credentials.sqlite credentials.sqlite
root@192.168.12.118's password: 
credentials.sqlite                                                                               100%   12KB 717.8KB/s   00:00    
[18:22:22] root@kali:~/pentest# ls
credentials.sqlite  
[18:23:32] root@kali:~/pentest# sqlite3 credentials.sqlite 
SQLite version 3.33.0 2020-08-14 13:23:32
Enter ".help" for usage hints.
sqlite> .tables
creds
sqlite> select * from creds;
1|test|12345
sqlite> 

```


### Keychain Data
### Core Data
### NSUserDefaults Class
NSUserDefaults is used for customization as per the user's preferences, and might contain sensitive information. This is stored in the devise as .plist file in the preferences directory, for instance: `/var/mobile/Containers/Data/Application/63A17000-C8E0-48D3-B81B-F4B4D4866E7B/Library/Preferences`. The Plist file should be converted to XML by using plutil.
```
# plutil -convert xml1 com.krvw.iGoat.plist 
Converted 1 files to XML format
# cat com.krvw.iGoat.plist 
....
	<key>password</key>
	<string>hotey</string>
	<key>username</key>
	<string>donkey</string>
</dict>
</plist>

```

### Temporaty Files (Data Cache)
### Log Files
