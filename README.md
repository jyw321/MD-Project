# MD
This is my testing project based on the existing coding scripts established by [linux-minidisc](https://github.com/glaubitz/linux-minidisc) and [NetMDPython](https://wiki.physik.fu-berlin.de/linux-minidisc/doku.php?id=netmdpython#getting_the_code) to extract digital contents from my portable Hi-MD player to my computer.

In 1992, Sony launched a born-digital optical disc based media format called MiniDisc. Audio information is written onto discs via the magneto-optical mechanism. Sony invented the ATRAC (Adaptive Transform Acoustic Coding) algorithm to largely compress audio data being recorded. Therefore, the size of MiniDisc is significantly smaller than its counterpart compact disc (CD). With the magneto-optical mechanism, MiniDisc is rewritable and track-tracing enabled. Sony discontinued manufacturing MiniDisc recorder-player in 2013, making MiniDisc an obsolete media format. Over the years, there are two types of discs being invented: standard MD and Hi-MD. Based on different ATRAC data processing mechanisms, audio information could be recorded in standard mode (SD) and long-play mode (LP2 and LP4). NetMD was launched in the early 2000s, allowing users to directly transfer music tracks from personal computers to MD recorder-players via a USB port through a Sony proprietary software. With the invention of Hi-MD discs and Hi-MD recorder-player, the ATRAC algorithm is upgraded to a system called DWDD (Domain Wall Displacement Detection), which is a data compression mechanism applied on recording Hi-MDs. Hi-MD could carry audio information and non-audio digital files. 
MD players are backward compatible, which means a Hi-MD player is able to playback MiniDiscs with audio information recorded in different modes. But the recording capability of different generations of MD players varies. 

The current linux-minidisc and NetMDPython are designed for NetMD devices. For now, they can work with audio tracks recorded in non-Hi-MD modes. Codes of Hi-MD compatability are under development. More discussion could be found [here](https://github.com/gavinbenda/platinum-md/issues/40) and [here](https://github.com/gavinbenda/platinum-md/issues/11).

## My Equipment ##
#### iMac (macOS Catalina version 10.15.7) ####
#### Sony MZ-M200 Hi-MD ####
#### USB 2.0 port to connect MD with Mac ####
#### several MD discs with audio information recorded in SD, LP2 and LP4 modes. ####


## Workflow ##

* Download and install [Macports](http://www.macports.org).
