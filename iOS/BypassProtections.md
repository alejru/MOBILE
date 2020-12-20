# Bypass Security Protections
### Bypass Jailbreak Detection
There are many alternatives in Cydia. Liberty works very well for me.
 
<img src="images/liberty.png" width="200" height="200">

### Bypass SSL Pining
Many times you won't be able to intercept HTTPS traffic, even after installing the Burp Suite CA certificate due to certificate pinning, where the app checks the server's certificate against a known copy of that certificate. It can be baypass by using: 
* SSL Kill Switch. Download the .deb file and install it using dpkg -i. 
* Firda - Objection. `ios sslpinning disable`
