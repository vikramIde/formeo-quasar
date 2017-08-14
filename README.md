# Formapp

> A Ncp project
## Table of Contents

<!-- toc -->

- [System Setup](#system-setup)
- [Project Setup](#project-setup)

<!-- tocstop -->

## System Setup
```bash
# If you don't have Android Studio Setup
$ sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
# Download Android Studio from https://developer.android.com/studio/index.html
# Run studio.sh, and finish installing android.

# Finally
$ sudo npm install -g cordova
$ sudo npm install -g quasar-cli
```

## Project Setup

``` bash
# Clone this project.
$ git clone https://bitbucket.org/nanocorp/formapp  # I personally use SSH, but not everyone has it setup
$ cd formapp

# install dependencies
$ npm install

# build for production with minification
$ quasar build

# Prepare Cordova
$ quasar wrap cordova
$ cd cordova
$ cordova platform add android
$ cordova run
```

# Gallery 

## 1
![alt text](https://image.prntscr.com/image/lmQw4NqsTAegshlsGvSx7Q.png "List of templates in Admin pannel")

## 2

 ![alt text](https://image.prntscr.com/image/ouYWO0ZlTPie2ky6dvil7g.png "Formeo Form builder on web Admin Pannel")

## 3
	
 ![alt text](https://files.gitter.im/vikramIde/GqpP/WhatsApp-Image-2017-08-14-at-5.30.26-PM.jpeg "Formeo Form builder on web Admin Pannel")

## 4
  
   ![alt text](https://files.gitter.im/vikramIde/1djX/WhatsApp-Image-2017-08-14-at-5.30.26-PM-_1_.jpeg "Formeo Form builder on web Admin Pannel")

## 5
    
    ![alt text](https://files.gitter.im/vikramIde/sA9Y/WhatsApp-Image-2017-08-14-at-5.30.26-PM-_2_.jpeg "Formeo Form builder on web Admin Pannel")
## 6
    
    ![alt text](https://files.gitter.im/vikramIde/i60s/WhatsApp-Image-2017-08-14-at-5.30.26-PM-_3_.jpeg "Formeo Form builder on web Admin Pannel")











