# Introduction #

This article helps you to get started with the `videocity` software. This is "work in progress" and we recommend that you use SVN to checkout the source code to get started. The `videocity` server side of the project has two other dependencies: p2p-sip and rtmplite. The server side runs in Python 2.5 and client is ActionScript 3.0. The client requires a browser with Flash Player 10.0.22 or higher installed. For getting started, we will use the same machine for both client and server.

# Install Python #

If you don't already have Python 2.5 installed, then please follow the instructions to download and install Python 2.5 from [http://www.python.org/download/releases/](http://www.python.org/download/releases/). The latest applicable version is 2.5.4 as of today.

On windows I assume that Python is installed in `C:/Python25` and on Unix and MacOS in `/usr/bin/python`

# Checkout p2p-sip, rtmplite, videocity #

We will checkout dependencies as well as videocity project software using SVN. Make sure SVN is installed on your computer. It is installed by default on most Unix machines. All the three projects are on googlecode.

### On Unix (Linux or MacOS) ###

First we create a {{{project}} directory in your home directory. Then checkout three projects from {{{googlecode}} in this project directory.

```
bash$ mkdir ~/project
bash$ cd ~/project
bash$ svn checkout http://p2p-sip.googlecode.com/svn/trunk/ p2p-sip
bash$ svn checkout http://rtmplite.googlecode.com/svn/trunk/ rtmplite
bash$ svn checkout http://videocity.googlecode.com/svn/trunk/ videocity
```

### On Windows XP or Vista ###

Please install an SVN client such as [TortoiseSVN](http://tortoisesvn.net/) for Windows. Once installed, create a project directory such as `c:\project`, and checkout these three projects in the directory `http://p2p-sip.googlecode.com/svn/trunk/`, `http://rtmplite.googlecode.com/svn/trunk/`, `http://videocity.googlecode.com/svn/trunk/`. If you are using TortoiseSVN, open windows explorer, and go to `c:\project` directory. Then right click and do "SVN Checkout". Specify the URL say `http://p2p-sip.googlecode.com/svn/trunk/` and checkout directory as `c:\project\p2p-sip`, and click on "OK". Then repeat the procedure for other two URLs specified above, with respective directory names.

# Run the server #

The main server application is in `videocity` project, named `videocity.py`. Go to the `videocity` sub-directory, set the `PYTHONPATH` environment variable to include dependencies, and run the main module `videocity.py`. If you get errors, please make sure that your dependencies are installed correctly and that your PYTHONPATH is set correctly.

### On Unix (Linux or MacOS) ###

```
bash$ cd videocity
bash$ export PYTHONPATH=../p2p-sip/src:../rtmplite:.
bash$ python python/videocity.py
```

### On Windows XP or Vista ###

```
C:\projects> cd videocity
C:\projects\videocity> set PYTHONPATH=..\p2p-sip\src;..\rtmplite;.
C:\projects\videocity> c:\Python25\python.exe python\videocity.py
```

# Do a quick smoke test #

Once your server is running, you can do a quick test by launching your web browser such as FireFox (Unix, MacOS or Windows), Safari (MacOS) or Internet Explorer (Windows) application. You will also need Flash Player 10.0.22 or higher installed in your browser. If applicable, please install the Flash Player from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) first.

Open your browser and point your browser to open URL `http://localhost:5080`. This will open the main page of the `videocity` application and has embedded Flash application for the client side of the software.

You can follow the help on that page to sign up, create your room and soft-cards, and enter your room. Alternatively, you can go to a pre-created room page at URL `http://localhost:5080/kundansingh_99@yahoo.com`. You can see the server logs on the server console to see the HTTP requests made by client.

Once your enter the room, you can see the play lists described in the room page. If you open another browser instance or tab, and enter the same room, these two instances of the users will be able to see each other and communicate with each other. For example, launch the text chat from the bottom bar to send text message to the other user. Move your mouse towards the left of the Flash application to see the other user in the room. Enable your camera so that your video is sent to the other user in the room. Upload photos from your computer and share in the room so that the other user sees those photos.

# Conclusion and next step #

Once you are comfortable running the software on your localhost, you can move to a network environment. Note that the soft-card created for URL `http://localhost:5080` cannot be used for network URL of the form `http://my.39peers.net:5080`. Thus, you will have to create new cards when using a remote network URL.

One intermediate step for moving from localhost to network is to update your DNS lookup to resolve "my.39peers.net" to your localhost. This way, your client and server assume network environment, whereas you can still run your client and server on the same localhost. On Unix and MacOS systems, you can edit the `/etc/hosts` file to add the following line.
```
127.0.0.1 my.39peers.net
```
Now you will be able to use the URL of the form `http://my.39peers.net:5080` to connect to your server running on localhost.