## Transcoding ATRAC Files ##

Considering the highly proprietary and unpopular nature of audio files in different versions of ATRAC formats, it is recommended that archivists create audio files in more commonly seen formats for public access besides keeping the original ATRAC-codec files.
In this case, FFmpeg is a good choice. The latest FFmpeg version 4 is versatile enough to encode and decode files in ATRAC codec, including ATRAC1, ATRAC3 and ATRAC3 plus.

For transcoding files in `.aea` (ATRAC1 codec), `.oma`, `.at3` (ATRAC3 codec) wrapper, use FFmpeg to transcode into `.mp3`:
```
ffmpeg -i input_file -f mp3 output_file
```

For transcoding files in `.pcm` (Hi-MD lossless mode), the open-source free-to-download software [Audacity](https://www.audacityteam.org/download/) is a good bet. 
 * Follow instructions to download Audacity to your computer
 * Import the `.pcm` file as `Raw Data`
 * Configure the setting to PCM 16 bit, 44100HZ
 * Load the file and check if it is the correct audio file
 * Export the `.pcm` file into a desired format (e.g. .wav, .mp3)
