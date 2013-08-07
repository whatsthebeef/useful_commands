### Generate keystore with certificate

Make sure the keytool is on the path and change location to the config of your app server (inside the domain with glassfish)

```shell

keytool -genkey -alias zode64 -keyalg RSA -keypass changeit -storepass changeit -keystore keystore.jks

What is your first and last name (CN) : [host/domain name]

keytool -export -alias zode64 -storepass changeit -file server.cer -keystore keystore.jks

keytool -import -v -trustcacerts -alias zode64 -file server.cer -keystore cacerts.jks -keypass changeit

```

For removing the keystore and certificates created above

```shell

keytool -delete -alias zode64 -keystore cacerts.jks

keytool -delete -alias zode64 -keystore keystore.jks

```
