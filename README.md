## Create video with multiples images

### USAGE:

```console
ffmpeg -framerate 1/2.5 -loop 1 -i go%d.png -i song.mp3 -shortest out.mp4
```

> -framerate = each image will be displayed by 2.5 secs

> %d = iterate over images

# FFmpeg Commands for All Needs: 2019 Guide

### Get File Information From a Video File
You can easily obtain a lot of information on a given video file with the following command-line instruction:

```console
ffmpeg -i video.avi
```

# Convert Images to a Video Sequence
This command will transform all the images from the current directory (named image1.jpg, image2.jpg, etc...) to a video file named video.mpg.

```console
ffmpeg -f image2 -i image%d.jpg video.mpg
```

# Convert a Video to X Images
This command will generate imagess named image1.jpg, image2.jpg, etc, from a given video file. The following image formats are available: PGM, PPM, PAM, PGMYUV, JPEG, GIF, PNG, TIFF, SGI.

```console
ffmpeg -i video.mpg image%d.jpg
```

# Crop a Video File
Cropping is a very common operation in video editing. FFmpeg provides a crop filter for this specific purpose:

```console
ffmpeg -i input.mp4 -filter:v "crop=out_w:out_h:x:y" output.mp4
```
The options are as follows:

- out_w is the width of the output rectangle
- out_h is the height of the output rectangle
- x and y specify the top left corner of the output rectangle
- output.mp4 is the output file

# Resize a Video
Using the -vf scale filter, it is possible to resize videos to a desired size:

```console
ffmpeg -i input.avi -vf scale=320:240 output.avi
```

The same works with images as well:
```console
ffmpeg -i input.jpg -vf scale=320:240 output_320x240.png
```

# Extract a Portion of a Video
Another very common operation on video files is to extract a specific portion of a given video. This can be done super easily:
```console
ffmpeg -ss 00:00:30 -i orginalfile.mpg -t 00:00:05 -vcodec copy -acodec copy newfile.mpg
```
In the example above, we are cutting out a part starting at 00:00:30 into the original file with a 5 seconds length. -ss indicates the starting time, and -t indicates the duration.

# Extract Sound From a Video, and Save It in Mp3 Format
Creating an audio file from a video is an easy task:
```console
ffmpeg -i source_video.avi -vn -ar 44100 -ac 2 -ab 192k -f mp3 sound.mp3
```

Explanations:

- Source video: source_video.avi
- Audio bitrate: 192kb/s
- output: mp3 format
- Generated sound : sound.mp3

# Convert a Wav File to Mp3
FFmpeg isn't only for videos, there's a lot you can do with audio files as well. This example will convert a .wav file to mp3 format.
```console
ffmpeg -i input_sound.avi -vn -ar 44100 -ac 2 -ab 192k -f mp3 output_sound.mp3
```

# Convert .avi Video to .mpg
Coverting video files from a format to another is extremely simple. Here, a .avi video is converted to .mpg:
```console
ffmpeg -i original_video.avi final_video.mpg
```

# Convert .mpg to .avi
And vice-versa. This command convert videos to a specified file format:
```console
ffmpeg -i original_video.mpg final_video.avi
```

# Convert .avi to .flv
.flv is a very popular format for web videos. This example converts a .avi file into .flv, while specifying various parameters as such as the display size.
```console
ffmpeg -i original_video.avi -ab 56 -ar 44100 -b 200 -r 15 -s 320x240 -f flv final_video.flv
```

# Mix a Video With a Sound File
If you have an audio and video file, you can mix them together:
```console
ffmpeg -i sound.wav -i original_video.avi final_video.mpg
```

# Add Text Subtitles to a Video
If you have subtitles for a movie or documentary, it is possible to use FFmpeg to insert them into your video file:
```console
ffmpeg -i input.mp4 -i subtitles.srt -c copy -c:s mov_text output.mp4
```

# Image Overlay on a Video
Let's finish this round-up with an advanced command. Here, we are applying an overlay image to an existing video:
```console
ffmpeg -i input.mp4 -i image.png -filter_complex "[0:v][1:v] overlay=25:25:enable='between(t,0,20)'" -pix_fmt yuv420p -c:a copy output.mp4
```
Some explanations:

- overlay=25:25: The image will be positioned 25px to the right and 25px down, originating from the top left corner (0:0).
- enable='between(t,0,20)': The overlay image will be shown from 00:00:00 to 00:00:20

> source: https://dzone.com/articles/ffmpeg-commands-for-all-needs-2019-guide?edition=515295&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-10
