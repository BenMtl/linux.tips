# Concatenate two or more files
Create a list file with them, example content for `list.txt`
```sh
file file1.avi
file file2.avi
file file3.avi
...
```
Concatenate them in a single `output.avi` file
```
ffmpeg -f concat -i list.txt -c copy "output.avi"
```
that's it...

# Change video resolution
To change video resolution on a file just use these flags
```sh
# FullHD video resize (1920x1080) from 4K video but it works from lower resolutions too
# "-2" instead of "1080" just keep up current resolution (4:3 / 16:9 / 16:10 / ...) by using just one dimension
ffmpeg -i input.mkv -vf scale=1920:-2 output.mkv
```

# Convert 1080p -> 720p
Convert files in a directory from 1080p to 720p
```sh
#!/usr/bin/env bash
#
# Utility for converting src/* from 1080p to 720p
#
# ffmpeg -y -i input -c:v libx264 -b:v 2600k -pass 1 -an -f null /dev/null && \
# ffmpeg -i input -c:v libx264 -b:v 2600k -pass 2 -c:a aac -b:a 128k output.mp4
DIRSRC=/tmp/tmp/src/*
DIRDEST=/tmp/tmp/dst

for FILE in $DIRSRC; do
    FILEDST=`basename "$FILE"`
    ffmpeg -i "$FILE" -vf scale=-1:720 -c:v libx264 -crf 18 -preset veryslow -c:a copy "$DIRDEST/$FILEDST"
done
```

# Convert webm to mp3
```sh
# -vn      # disable video
# -ab xxx  # audio bitrate
# -ar xxx  # audio sampling rate (in Hz)
ffmpeg -i filename.webm -vn -ab 128K -ar 44100 filename.mp3
```

# Play files
```sh
# Play mp3 file, full text command line, no display needed
ffplay -nodisp filename.mp3
```
