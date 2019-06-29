## Create video with multiples images

### USAGE:

```console
ffmpeg -framerate 1/2.5 -loop 1 -i go%d.png -i song.mp3 -shortest out.mp4
```

> -framerate = each image will be displayed by 2.5 secs

> %d = iterate over images
