# MD

## Purpose ##
This is my testing project based on the existing scripts and efforts by projects [linux-minidisc](https://github.com/glaubitz/linux-minidisc), [NetMDPython](https://wiki.physik.fu-berlin.de/linux-minidisc/doku.php?id=netmdpython#getting_the_code), [QHiMDTransfer](https://wiki.physik.fu-berlin.de/linux-minidisc/doku.php?id=qhimdtransfer) and [Platinum-MD](https://github.com/gavinbenda/platinum-md.git) to extract digital contents from my portable MD player to my computer. 

This project is specifically practical to audiovisual archivists whose organizations hold collections in MiniDisc format. In the early 2000s, many cultural institutions utilized MiniDisc to record interviews, live performance and broadcasting records. However, with the obsolesence of MiniDisc format, it is important for archivists to retrieve the digital contents originally recorded on MiniDiscs and transfer them into local computer directory for further preservation treatments. 

**This file is intended to provide a follow-along instructions for archivists to retrieve digital contents from MiniDiscs.**

## About MD ##
In 1992, Sony launched a born-digital optical disc based media format called MiniDisc. Audio information is written onto discs via the magneto-optical mechanism. Sony invented the ATRAC (Adaptive Transform Acoustic Coding) algorithm to largely compress audio data being recorded. Therefore, the size of MiniDisc is significantly smaller than its counterpart compact disc (CD). With the magneto-optical mechanism, MiniDisc is rewritable and track-tracing enabled. Sony discontinued manufacturing MiniDisc recorder-player in 2013, making MiniDisc an obsolete media format. Over the years, there are two types of discs being invented: standard MD and Hi-MD. Based on different ATRAC data processing mechanisms, audio information could be recorded in standard mode (SD) and long-play mode (LP2 and LP4). NetMD was launched in the early 2000s, allowing users to directly transfer music tracks from personal computers to MD recorder-players via a USB port through a Sony proprietary software. With the invention of Hi-MD discs and Hi-MD recorder-player, the ATRAC algorithm is upgraded to a system called DWDD (Domain Wall Displacement Detection), which is a data compression mechanism applied on recording Hi-MDs. Hi-MD could carry audio information and non-audio digital files. 
MD players are backward compatible, which means a Hi-MD player is able to playback MiniDiscs with audio information recorded in different modes. But the recording capability of different generations of MD players varies. 

Traditionally, it is only through Sony's proprietary Windows-only software SonicStage that users could transfer contents between MiniDiscs (on NetMD above models) and local computers. With the open-source scripts, the content transfer process is made more flexible.


## Where to Go ##
* **For SD-MD**: To transfer contents from ***standard-MD formatted discs*** (including SP, LP2, LP4) to local computer, visit [here](Standard-MD.md)
* **For Hi-MD**: To transfer contents from ***Hi-MD formatted discs*** (including PCM, Hi-SP, Hi-LP) to local computer, visit [here](Hi-MD.md)
* **For more "authentic taste"?**: The above two methods tend to *automatically wrapped retrieved tracks in .wav*, except for the tracks recorded in SP mode. If you **DON'T** want that, but hope to ***extract audio tracks in its more original atrac-format***, you may try this under-experimenting approach [here](Experimenting_with_Platinum-MD.md).
* For transcoding ATRAC files to more accessible formats, visit [here](Transcoding.md)

#### *Don't know the format?* ####
* Hi-MD is indicated on the surface of a Hi-MD disc, while standard MD discs do not have the "Hi-MD" logo
* But even standard MDs can be formatted in Hi-MD format and record audio in Hi-MD modes with a Hi-MD recorder-player
* If you are not sure about the format, the way to find out is a little bit tricky. 
  * You can connect your MD to your computer and visit [web-minidisc](https://stefano.brilli.me/webminidisc/) on Google Chrome browser. If it successfully identify the player and show the stored contents, the tracks are recorded in standard mode.
  * If web-minidisc fails to identify your player or your disc, probably your disc is Hi-MD or formatted to Hi-MD mode.


## My Equipment ##
* iMac (macOS Catalina version 10.15.7) 
* *homebrew* and *ffmepg* installed
* Sony MZ-M200 Hi-MD recorder-player (an equivalent to MZ-RH1, the latest model of Sony portable MD recorder-player)
* USB 2.0 port to connect MD with Mac
* Several standard MD discs and Hi-MD discs with protected and unprotected audio information recorded in SD, LP2, LP4 and Hi-MD modes.

