# All-in-One Setup  

**Blog:** [Hail Frida: The Universal SSL Pinning Bypass for Android](https://infosecwriteups.com/hail-frida-the-universal-ssl-pinning-bypass-for-android-e9e1d733d29)  

## Steps:  

1. Install Frida on PC and download the Android server.  
2. Push the server to `/data/local/tmp`:  
   ```bash
   adb push <path to frida-server> /data/local/tmp
   adb shell chmod 777 /data/local/tmp/frida-server
3. Push the proxy’s CA Certificate:
 ```bash
adb push <path to cacert.der> /data/local/tmp/cert-der.crt
```
4. Push fridascript.js into the device:
 ```bash
adb push fridascript.js /data/local/tmp
```
5. Run the Frida server in another command prompt:
```bash
adb shell /data/local/tmp/frida-server &
```
6. Open another terminal and check all running processes:
```bash
frida-ps -U
frida-ps -Uai
```
7. Hook the app:
```bash
frida -U -f com.app.test -l D:\Open_tools\platform-tools\fridascript.js --pause
```


## Other links
[SSL By Pass Patching](https://github.com/ilya-kozyr/android-ssl-pinning-bypass)


