# COLLECTION-Cricket

This collection of repositories is used for building `Cricket`.
<!-- TOC depthFrom:2 updateOnSave:true -->

- [Installing Sources](#installing-sources)
- [Prerequisites for running or building](#prerequisites-for-running-or-building)
- [Interpret python source](#interpret-python-source)
- [Build procedure](#build-procedure)
- [Application Installer creation](#application-installer-creation)
- [Application release procedure](#application-release-procedure)

<!-- /TOC -->

## Installing Sources

<strong>From a tar file</strong>

Unpack the tar file in a convenient directory, using <code>tar -xzf <em><strong>tarfile.tgz</strong></em> -C <em><strong>destdir</strong></em></code>.

Then change directory to the <code><em><strong>destdir</strong></em></code>.

<strong>From github.mcci.com</strong>

Clone the release tag repository from MCCI's github server using the command:

```shell
git clone --recursive https://github.com/mcci-usb/COLLECTION-cricket-ui.git --branch <tag_name> --single-branch
```
For an example - Cloning for the release tag 'v1.0.0', replace the <tag_name> with v1.0.0 

Then change directories to the top level of the cloned repository.

## Prerequisites for running or building

<strong>On Windows:</strong>

Development environment

* OS - Windows 10 64 bit
* Python - 3.7.6
* wxpython - 4.0.7.post2
* pyserial - 3.4
* pyusb - 1.0.2
* libusb - 1.0.22b9
* libusb1 - 1.8
* pyinstaller - 3.6 

Download [python3.7.6](https://www.python.org/downloads/release/python-376/) and install

```shell
pip install wxpython==4.0.7.post2
pip install pyserial
pip install pyusb
pip install libusb
pip install libusb1
pip install pyinstaller
```

<strong>On Linux and Mac:</strong>

Development environment

* Linux OS - Ubuntu 20.04 64 bit
* Python - 3.8.2
* Mac OS - High Sierra 10.13.6 64 bit
* Python - 3.7.0
* wxpython - 4.0.7.post2
* pyserial - 3.4
* pyusb - 1.0.2
* libusb - 1.0.22b9
* libusb1 - 1.8
* pyinstaller - 3.6  
* hidapi - 0.10.1  - Only for Mac OS

```shell
sudo apt-get install python3
sudo apt-get install python3-pip
sudo pip3 install wxpython==4.0.7.post2
sudo pip3 install pyserial
sudo pip3 install pyusb
sudo pip3 install libusb
sudo pip3 install libusb1
sudo pip3 install pyinstaller
brew install hidapi - Only for Mac OS
```

Note:
* If the installation of wxpython is not success, perform `sudo apt-get install build-essential libgtk-3-dev`
* Some times the installation of wxpython takes longer time (>30 minutes).

## Interpret python source

This is to ensure that the source can be interpreted without any error

Move to the directory `destdir/cricket/src/`

<strong>On Windows:</strong>

```shell
python main.py
```

This show up application UI window on screen

<strong>On Linux and Mac:</strong>

```shell
python3 main.py
```

This show up application UI window on screen


## Build procedure

<strong>On Windows and Linux:</strong>

Placing of libusb-1.0.dll for exe creation

* Move to the Python installation directory
* Copy the libusb-1.0.dll from `Python/Python37-32/Lib/site-packages/libusb/_platform/_windows/x86/`
* Paste the dll to the directory `destdir/cricket/src/`
* Paste the dll to the OS directory `Windows/SysWOW64/`

Move to the directory `destdir/cricket/src/`

<strong>On Windows:</strong>

```shell
pyinstaller Cricket-Windows.spec
```

<strong>On Linux and On Raspberry Pi:</strong>

```shell
pyinstaller Cricket-Linux.spec
```

<strong>On Mac:</strong>

```shell
pyinstaller Cricket-Mac.spec
```
The executable 'Cricket' show up in `destdir/cricket/src/dist/`.

## Application Installer creation

<strong>On Windows:</strong>

Download [Inno Setup Compiler](https://jrsoftware.org/isdl.php#stable) and install

Run the Inno Setup Script file 'Cricket-Windows' which is in `destdir/installerScript/`.

The App Installer 'cricket-<ver tag>-windows-installer' show up in `destdir/AppInstaller/`.


<strong>On Linux:</strong>

Create Linux deb package using Debreate Debian package builder

Run the Package project file 'Cricket-Linux' which is in `destdir/installerScript/`.

The App Installer 'cricket-<ver tag>-linux-installer' show up in `destdir/AppInstaller/`.

<strong>On Raspberry Pi:</strong>

Create Raspberry Pi deb package using Debreate Debian package builder

Run the Package project file 'Cricket-Linux' which is in `destdir/installerScript/`.

The App Installer 'cricket-<ver tag>-linux-installer' show up in `destdir/AppInstaller/`.

<strong>On Mac:</strong>

Download [Packages](http://s.sudre.free.fr/Software/Packages/about.html) and install

To know about [Packages](https://www.techrepublic.com/article/how-to-repackage-os-x-apps-with-packages/) more

Run the Package project file 'Cricket-Mac' which is in `destdir/installerScript/`.

The App Installer 'cricket-<ver tag>-mac-installer' show up in `destdir/AppInstaller/`.


## Application release procedure

<strong>On Windows:</strong>

Create a release directory with release version `cricket-<ver tag>-windows-installer`

Move the App Installer 'cricket-<ver tag>-windows-installer' into the release directory and zip (compress) it, 
the name of zipped folder should be  `cricket-<ver tag>-windows-installer.zip`.

The Application Installer must be digitally signed before it can be deployed.

<strong>On Linux:</strong>

Create a release directory with release version `cricket-<ver tag>-linux-installer.deb`

Move the App Installer 'cricket-<ver tag>-windows-installer' into the release directory and zip (compress) it, 
the name of zipped folder should be  `cricket-<ver tag>-linux-installer.deb.zip`.

The Application Installer must be digitally signed before it can be deployed.

<strong>On Raspberry Pi:</strong>

Create a release directory with release version `cricket-<ver tag>-linux-installer.deb`

Move the App Installer 'cricket-<ver tag>-windows-installer' into the release directory and zip (compress) it, 
the name of zipped folder should be  `cricket-<ver tag>-arch64-linux-installer.deb.tar.gz`.

The Application Installer must be digitally signed before it can be deployed.

<strong>On Mac:</strong>

Create a release directory with release version `cricket-<ver tag>-mac-installer.pkg`.

Move the App Installer 'UI3141-3201-Installer' into the release directory and zip (compress) it, 
the name of zipped folder should be  `cricket-<ver tag>-mac-installer.pkg.zip`.

The Mac application and the Application Installer must be signed and notarized before it can be deployed.

