# MD

## Purpose ##
This is my testing project based on the existing coding scripts established by [linux-minidisc](https://github.com/glaubitz/linux-minidisc) and [NetMDPython](https://wiki.physik.fu-berlin.de/linux-minidisc/doku.php?id=netmdpython#getting_the_code) to extract digital contents from my portable Hi-MD player to my computer. 

This project is specifically practical to audiovisual archivists whose organizations hold collections in MiniDisc format. In the early 2000s, many cultural institutions utilized MiniDisc to record interviews, live performance and broadcasting records. However, with the obsolesence of MiniDisc format, it is important for archivists to retrieve the digital contents originally recorded on MiniDiscs and transfer them into local computer directory for further preservation treatments. 

This file is designed for needed archivists to follow-along for retrieving contents from MiniDiscs.

## About MD ##
In 1992, Sony launched a born-digital optical disc based media format called MiniDisc. Audio information is written onto discs via the magneto-optical mechanism. Sony invented the ATRAC (Adaptive Transform Acoustic Coding) algorithm to largely compress audio data being recorded. Therefore, the size of MiniDisc is significantly smaller than its counterpart compact disc (CD). With the magneto-optical mechanism, MiniDisc is rewritable and track-tracing enabled. Sony discontinued manufacturing MiniDisc recorder-player in 2013, making MiniDisc an obsolete media format. Over the years, there are two types of discs being invented: standard MD and Hi-MD. Based on different ATRAC data processing mechanisms, audio information could be recorded in standard mode (SD) and long-play mode (LP2 and LP4). NetMD was launched in the early 2000s, allowing users to directly transfer music tracks from personal computers to MD recorder-players via a USB port through a Sony proprietary software. With the invention of Hi-MD discs and Hi-MD recorder-player, the ATRAC algorithm is upgraded to a system called DWDD (Domain Wall Displacement Detection), which is a data compression mechanism applied on recording Hi-MDs. Hi-MD could carry audio information and non-audio digital files. 
MD players are backward compatible, which means a Hi-MD player is able to playback MiniDiscs with audio information recorded in different modes. But the recording capability of different generations of MD players varies. 

Traditionally, it is only through Sony's proprietary Windows-only software SonicStage that users could transfer contents from MiniDiscs to their local computers. With the open-source scripts, the content transfer process is made more flexible.

## Good to Know Before Started ##
The current linux-minidisc and NetMDPython are designed for NetMD devices. For now, they can work with *unprotected* audio tracks recorded in *non-Hi-MD modes*. It is found that, analog-recorded tracks are usually unprotected. All tracks uploaded by SonicStage are protected (back then, general users used SonicStage to transfer music into their players and make their mixtapes). Surprisingly, tracks uploaded by MD Simple Burner are not. 
As this file is designed for audiovisual archivists, and considering that MiniDisc archival collections usually store analog-input audio information (e.g. interview), there is good chance that contents would be mostly unprotected.
Scripts with Hi-MD compatability are under development. More discussion could be found [here](https://github.com/gavinbenda/platinum-md/issues/40), [here](https://github.com/gavinbenda/platinum-md/issues/11), and [here](https://wiki.physik.fu-berlin.de/linux-minidisc/doku.php?id=start#source_code).

## My Equipment ##
* iMac (macOS Catalina version 10.15.7) 
* Sony MZ-M200 Hi-MD
* USB 2.0 port to connect MD with Mac
* Several MD discs with protected and unprotected audio information recorded in SD, LP2 and LP4 modes.

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
* The outcome will look like:

![list contents](https://github.com/jyw321/MD/blob/main/Screen%20Shot%202021-01-28%20at%2017.05.17.png =250x)

* If protected contents are included (e.g. those imported through SonicStage), the outcome will look like:

![list contents protected](https://github.com/jyw321/MD/blob/main/Screen%20Shot%202021-01-28%20at%2017.07.00.png)

* 

### How-to Upload Contents ###
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
