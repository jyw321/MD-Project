# Standard MD #

This is a walk-through of transferring digital contents stored in standard-MD formatted MiniDisc to local computer. The workflow is based on the linux-minidisc rooted [NetMDPython scripts](https://wiki.physik.fu-berlin.de/linux-minidisc/doku.php?id=netmdpython). The workflow below concentrates on operation in Mac OS system.

## Good to Know Before Started ##
The current NetMDPython are designed for NetMD devices. For now, they can work with *unprotected* audio tracks recorded in *non-Hi-MD modes*. It is found that, analog-recorded tracks are usually unprotected. All tracks uploaded by SonicStage are protected (back then, general users used SonicStage to transfer music into their players and make their mixtapes). Surprisingly, tracks uploaded by MD Simple Burner are not. 
As this file is designed for audiovisual archivists, and considering that MiniDisc archival collections usually store analog-input audio information (e.g. interview), there is good chance that contents would be mostly unprotected.


## Workflow ##
### Set-up ###
* Download and install [Macports](http://www.macports.org).
* After installing macports, you'll need to modify your .bashrc in your home-directory by adding ”/opt/local/bin” to the PATH-environment. In the terminal (Applications→Utilities→Terminal), type: 
```bash
echo "PATH=$PATH:/opt/local/bin" >> ~/.bashrc
```
* Then install the ports *git-core* and *libusb* from Macports:
```bash
sudo port install libusb git-core py26-crypto sox
```
* Clone the codes with *git* into your local root directory. 
``` bash
git clone https://github.com/glaubitz/linux-minidisc/
```
* Insert MD disc into MD player (the player should be switched on automatically).
* Connect MD player with Mac via a USB port.
* In Terminal, type:
``` bash
cd linux-minidisc/netmd
```
(The Python *libnetmd* can be found in the *netmd* subdirectory in the "linux-minidisc" folder)

### How-to List Contents ###
* To list what you have in the MD disc, type:
``` bash
./lsmd.py
```
* The content list will contain total number of recorded tracks, track titles and time-stamps, protection status, and track recording modes.

* The outcome will look like:

![list contents](https://github.com/jyw321/MD/blob/main/Screen%20Shot%202021-01-28%20at%2017.05.17.png)

* If protected contents are included (e.g. those imported through SonicStage), the outcome will look like:

![list contents protected](https://github.com/jyw321/MD/blob/main/Screen%20Shot%202021-01-28%20at%2017.07.00.png)


### How-to Upload Contents from MD to Mac ###
* Using, Sony's MZ-RH1/M200, you can upload tracks from MD player to your computer.
* Before you can successfully upload tracks from MD player to computer, you need to install FFmpeg (an open-source media encoding and processing application), which will be used for regconizing and transcoding ATRAC information.
* To install FFmpeg, 
``` bash
sudo port install ffmpeg-devel
```
* To upload unprotected audio tracks from MD disc to computer by using Sony's MZ-RH1/M200:
``` bash
./upload.py
```
(protected tracks will be skipped automatically)

* Upon retrieving the tracks, they will be saved in a subfolder under the *netmd* directory. SD tracks are saved as .aea format and LP2/LP4 tracks into .wav. 
(MediaInfo or ExifTool are not able to identify the codec of the .aea format. But FFProbe could recognize the ATRAC1 codec of .aea files.)

* If the above command-lines fail to work out of blue, try unplug the MD player from the computer, unload the disc, terminate the Terminal, and re-connect everything again.
