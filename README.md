Livestreamer
============
Livestreamer is a CLI program that launches live streams from various streaming
services in a custom video player and also a Python library that allows you to
interact with the stream data in your own application.

Current release: **1.3.2** (2012-10-03)

Currently includes plugins for these sites:

* GOMTV.net
* Justin.tv/Twitch.tv
* Livestream.com
* Ongamenet.com
* Own3d.tv
* SVTPlay
* UStream
* YouTube


Dependencies
------------
Livestreamer and it's plugins currently depends on these software:

* Python version >= 2.6 or >= 3.0 (currently CPython and PyPy is known to work)
* python-setuptools or python-distribute

These will be installed automatically by the setup script if they are missing:
* python-requests (at least version 0.12.1)
* python-pbs
* python-argparse (only needed for Python version < 2.7)

For RTMP based plugins:
* librtmp/rtmpdump (git clone after 2011-07-31 is needed for Twitch/JustinTV plugin)


Installing (Linux, OS X etc)
---------------------------
**Release version**

Pip is a tool to install Python packages from a central repository.

    $ sudo pip install livestreamer


**Git version**

Clone or download an archive of the repository then run:

    $ sudo python setup.py install


Installing (Windows - Installer)
-----------------------------
1. Download installer from downloads and run it
2. Once installed, open  %APPDATA%\livestreamer\livestreamerrc in a text editor and make sure everything is correct
3. Use livestreamer from command prompt

*Note!* Installer has only been tested on Windows 7 (x64) as of now. Also, if you have previously installed manually you may need to remove livestreamer.exe from PYTHONPATH\Scripts.


Installing (Windows - Manual install)
---------------------------------
1. Install Python
2. Install Python setuptools
3. Get rtmpdump and unpack it somewhere (rtmpdump-20110925-git-6230845-win32.zip from the downloads section should work)
4. Add these paths to your Path environment variable (separate with a semicolon):
 * PYTHONPATH\
 * PYTHONPATH\Scripts\
 * RTMPDUMPPATH\ (or specify full path with --rtmpdump option)
 * PLAYERPATH\ (or specify full path with --player option)

5. **Release version** Open a command prompt and run:

        pip install livestreamer

   **Git version** Open a command prompt and change directory to livestreamer source, then run:

       python setup.py install

    This should install any missing Python dependencies automatically if they are missing.


Using
-----
    $ livestreamer --help

Plugin specific usage
---------------------
Most plugins are straight-forward to use, just pass the URL to the stream and it will work.
However, some plugins are using what could be called a "meta URL" to find the stream for you.


**gomtv**
Passing the URL *gomtv.net* will make the plugin figure out what match is currently playing automatically.

**ongamenet**
To use this plugin the URL *ongamenet.com* must be passed. 


Common issues
-------------
**livestreamer errors with "Unable to read from stream" or "Error while executing subprocess" on Twitch/JustinTV streams.**

When building rtmpdump from source it may link with a already existing (probably older) librtmp version instead of using it's
own version. On Debian/Ubuntu it is recommended to use the official packages of *librtmp0* and *rtmpdump* version
*2.4+20111222.git4e06e21* or newer. This version contains the necessary code to play Twitch/JustinTV streams and
avoids any conflicts. It should be available in the testing or unstable repositories if it's not available in stable yet.


**VLC on Windows fails to play with a error message.**

VLC version 2.0.1 and 2.0.2 contains a bug that prevents it from reading data from stdin.
This has been fixed in version 2.0.3.


Saving arguments AKA config file
--------------------------------
Livestreamer can read arguments from the file ~/.livestreamerrc (POSIX) or %APPDATA%\livestreamer\livestreamerrc (Windows).
A example file:

    player=mplayer
    gomtv-username=username
    gomtv-password=password


Using livestreamer as a library
-------------------------------

http://livestreamer.readthedocs.org/

