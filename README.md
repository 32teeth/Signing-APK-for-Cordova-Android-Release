#create signed APK
---

```
(sudo) keytool -genkey -v -keystore [key name].keystore -alias [alias] -keyalg RSA -keysize 2048 -validity 10000
```
you will be prompted to provision additional details

* password
* full name
* organization unit (optional)
* organization
* city or locality
* state or province
* two letter country code

at the "is this correct line" enter

```
yes
```
you will be prompted for a key password hit return if the same as keystore


```
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore [key name].keystore [path to apk] [alias]
```

```
jarsigner -verify -verbose -certs [path to apk]
```

```
zipalign -v 4 [path to apk] [path to release apk]
```

now upload your signed apk to the google play store
