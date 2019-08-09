# audible2oog
A Linux Toolkit based on Python2 at present to convert audible downloaded aax files to oog.

How to get your activation bytes

http://ffmpeg.org/ffmpeg-all.html#Audible-AAX
https://github.com/inAudible-NG/tables






```
#!/bin/sh
LANG="de_DE.UTF-8"

echo "Install missing dependencys ..."
sudo apt-get install ffmpeg python-pip chromium
sudo pip install requests
sudo pip install selenium

echo "Configure audible activator ..."
mkdir aax2mp3tools
cd aax2mp3tools
wget https://github.com/inAudible-NG/audible-activator/archive/master.zip
unzip master.zip
wget https://chromedriver.storage.googleapis.com/2.35/chromedriver_linux64.zip
unzip chromedriver_linux64.zip

echo "Räume auf ..."
rm master.zip
rm chromedriver_linux64.zip

echo "Starte nun den audible-Activator ..." 
cd audible-activator-master
echo "Bitte gib nun Dein audible-Username und das dazugehörige Passwort ein:"
./audible-activator.py -l de

echo "Bitte notiere Dir die 16 Stellen der ermittelten activation_bytes, beispielsweise 8a1ed00d"
exit
```
