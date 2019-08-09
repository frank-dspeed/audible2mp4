# audible2mp4
A Linux Toolkit based on Python2 at present to convert audible downloaded aax files to oog.

How to get your activation bytes

http://ffmpeg.org/ffmpeg-all.html#Audible-AAX
https://github.com/inAudible-NG/tables

git clone https://github.com/frank-dspeed/tables
cd tables
```
#!/bin/bash
FILE="/path/to/File"
echo "Install missing dependencys ..."
sudo apt-get install ffmpeg python-pip chromium
git clone https://github.com/frank-dspeed/tables
cd tables
ACTIVATION=rcrack . -h $(ffprobe $FILE &> /tmp/audible_checksum && cat /tmp/audible_checksum | grep checksum | rev | cut -d" " -f1 && rm /tmp/audible_checksum) | grep "hex:" | cut -d: -f1

ffmpeg -activation_bytes $ACTIVATION -i $FILE -vn -c:a copy output.mp4
```
