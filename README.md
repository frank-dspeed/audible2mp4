# audible2mp4
A Script that uses Audible-NG Rainbowtables to get the Audible Activation bytes from a .aax file and also runs ffmpeg to produce a none protected .mp4 file. http://ffmpeg.org/ffmpeg-all.html#Audible-AAX

How to get your activation bytes
https://github.com/inAudible-NG/tables

## Script Method

```
#!/bin/bash
FILE="/path/to/File"
echo "Install missing dependencys ..."
sudo apt-get install ffmpeg
CHECKSUM=$(ffprobe $FILE &> /tmp/audible_checksum && cat /tmp/audible_checksum | grep checksum | rev | cut -d" " -f1 && rm /tmp/audible_checksum)
git clone https://github.com/frank-dspeed/tables
cd tables
AUDIBLE_ACTIVATION_BYTES=$(rcrack . -h $CHECKSUM | grep "hex:" | cut -d: -f1)

ffmpeg -activation_bytes $AUDIBLE_ACTIVATION_BYTES -i $FILE -vn -c:a copy output.mp4
```

## Manual Method

Install ffmpeg

```
sudo apt-get install ffmpeg
```

```
ffprobe your.aax
```

find the checksum 

```
git clone https://github.com/frank-dspeed/tables
cd tables
rcrack . -h <checksum>
```

find the hex: bytes in the result

```
ffmpeg -activation_bytes <activation bytes from hex:> -i your.aax -vn -c:a copy output.mp4
```
