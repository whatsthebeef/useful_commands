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

### Generate mapping data with ogr2ogr

Download the cultural vectos from here http://www.naturalearthdata.com/downloads/110m-cultural-vectors/

```shell

ogr2ogr -f GeoJSON subunits.json ne_110m_admin_0_map_subunits.shp

To get iso2 as id and include names - 

topojson --id-property iso_a2 -p name=NAME -p name -o world.json subunits.json

To get all capital cities

ogr2ogr -f GeoJSON -where "FEATURECLA = 'Admin-0 capital'" places.json ne_110m_populated_places.shp

```

### Generate ubuntu usb boot stick

```shell

hdiutil convert ~/Downloads/ubuntu-12.04.3-desktop-amd64.iso -format UDRW -o ~/Downloads/ubuntu-12.img

diskutil list

diskutil unmountDisk /dev/disk1

sudo dd if=~/Downloads/ubuntu-12.img.dmg of=/dev/rdisk1 bs=1m

```

