# phone-fileserver
Documenting ways to serve files from your phone.

* [BibleBox like interface with PHP](#phpserver)
* [Miniserver running on Termux](#miniserver)

## <a id="phpserver"></a>BibleBox like inerface 

BibleBox is a derivative of LibraryBox that is a derivative of PirateBox.

BibleBox devices are popular for sharing files over wifi. But there are times you don't have your BibleBox with you.

But my smart phone is quite capable of doing a similar job though with some shortcomings.

* It has a wifi hot spot capabilities
* It can run a web server. Though not at the default port 80 (unless your phone is rooted)
* It has a file system that can be served

The advantage of BibleBox is that you put your files in the folders provided and let people explore. 

I don't want to have to write a downloads page so something like what BibleBox implements is needed. BibleBox runs a PHP enabled server.

There is the PirateBox app but your phone needs to be rooted for that to work. 

Server for PHP is a free download for Android. The phone does not need to be rooted to run that.

The default files from BibleBox can be placed in the home folder. Though the server will serve up an index.php instead of an index.html if both exist. The server does not work like the BibleBox server so you have to add a file into every folder that you put files to share in.

### Install on phone
* Server for PHP
* QR code Generator

### Download
* PHP-fileserver.zip

## <a id="miniserver"></a>Miniserver - NodeJS - Termux

This is a bit techy to set up but it works well with just a home page and links to the download folders or just a link to the root of the downloads folder/s.

Youu can use it with or without a home page. If no index.html is present then it will just serve up a folder list. The directory listing is mobile friendly so easy to navigate on a phone.


### Install on Phone

* Termux

### In Termux console

```
apt update
apt install nodejs
npm install -g miniserver
termux-setup-storage
```
In a file manage on your phone make a folder in your internal storage called __miniserver__. If you have a home page called index.html put it here. If you don't then the server will serve up the folers and or files in that folder.

In Termux type the following:

```
cd storage/shared/miniserver
miniserver
```

The hard part is you have to know what the IP address is on the wifi network. To get the ip address in Termux type the following:

```
ifconfig wlan0
```

The third line will have: `inet addr:` the number after that is your ip address.

Once the server is running then you can connect to it on the phone at localhost:8080 or from another device on the same wireless network at the IP address followed by the :8080 port address.
