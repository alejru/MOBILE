# Side Channel Data Leakage
### Application Screenshot
iOS takes a screenshot of the application when it moves into the bakcground. 
An attacker having physical access to the system can easily access this screenshot and view sensitive information, for instance it is important to check the payment form where the details of a credit card are filled. </br>
Before returning from your applicationDidEnterBackground method, you should hide or obscure passwords and other sensitive personal information. 
Also, you could replace the screeen data with a splas screen moving it to the background, and restoring it on the foreground. 

### Pasteboard
* Cycript </br>
Install Cycript in the iDevice via Cydia
```
# cycript -p <PID>
# [UIPasteboard generalPasteboard].items
```
* Frida - Objection `ios pasteboard monitor`

### Device Logs
### Keyboard Cache
