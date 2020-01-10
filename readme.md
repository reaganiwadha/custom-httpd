# Custom Apache HTTPD Server ![GCI Badge](https://img.shields.io/badge/Google%20Code%20In-JBoss%20Community-red?style=flatr&labelColor=fdb900&link=https://codein.withgoogle.com/organizations/jboss-community/)
![Screenshot of its working](https://github.com/reaganiwadha/custom-httpd/blob/master/screenshot.png?raw=true)

This guide will help you modify, compile and install a custom HTTPD server!

## Getting Apache HTTPD
### Downloading
To download the HTTPD Source code, you can go to the [Apache Site](http://httpd.apache.org/docs/current/install.html). Or you could just directly download the file into your downloads folder like so

(On the day of creating this guide, the latest version is 2.4.41)
```bash
wget https://www-us.apache.org/dist//httpd/httpd-2.4.41.tar.gz
```

### Extracting
Extract the gzip like so
```bash
gzip -d httpd-2.4.41.tar.gz
tar xvf httpd-2.4.41.tar
```
Now, you should see a directory containing all the files required to build httpd

## Adding a custom version name
To add a custom version name, you can navigate to ```include/ap_release.h``` where it contains the httpd versioning parameters and modify the AP_SERVER_BASEPRODUC.

```cpp
#define AP_SERVER_BASEPRODUC "Apache-GCI"
```

## Configuring Build
To configure the build, you can easily run the provided ```configure``` file
```bash
./configure
```

This will automatically configure to install to ```/usr/local/apache2```. If you wanted to install this somewhere else you can define the prefix parameter and the path where you want it to be installed.

```
./configure --prefix=/path/to/installation
```

## Compiling and Installing
To compile and install the custom Apache HTTPD server, run 
```
make
``` 
and then 
```
sudo make install
```

This will compile and install automatically to ```/usr/local/apache2```.

## Starting the server
To start the server, you can run
```
sudo /usr/local/apache2/bin/apachectl -k start
```
or
```
sudo /path/to/installation/bin/apachectl -k start
```

## Testing if it works
After starting the server, you can test it by going to ```localhost``` and it should return you the index.html

## Checking the log
The logs will also include your custom name, to check it you can go to ```logs/error_log``` in your installation.

```
[Fri Jan 10 18:46:21.954144 2020] [mpm_event:notice] [pid 25635:tid 139774419078080] AH00489: Apache-GCI/2.4.41 (Unix) configured -- resuming normal operations
[Fri Jan 10 18:46:21.954483 2020] [core:notice] [pid 25635:tid 139774419078080] AH00094: Command line: '/usr/local/apache2/bin/httpd'
```

## Replacing index.html
You can replace the ```index.html``` that is located in the ```htdocs``` of your installation to see if it works! 

Congratulations! You've build your own custom apache server!
