### Generate keystore with certificate

```shell

keytool -genkey -alias zode64 -keyalg RSA -keypass changeit -storepass changeit -keystore keystore.jks

name and surname (CN) : [host/domain name]

keytool -export -alias zode64 -storepass changeit -file server.cer -keystore keystore.jks

keytool -import -v -trustcacerts -alias zode64 -file server.cer -keystore cacerts.jks -keypass changeit

keytool -delete -alias zode64 -keystore cacerts.jks

keytool -delete -alias zode64 -keystore keystore.jks

```
