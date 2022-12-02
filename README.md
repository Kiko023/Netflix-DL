1. Install python 3.10.7 (or any version from 3.8.x to 3.10.x), be sure to add python to PATH while installing it

https://www.python.org/ftp/python/3.10.7/python-3.10.7-amd64.exe

https://datatofish.com/add-python-to-windows-path/

2. Install Visual C++ Redistributable Packages for Visual Studio 2013

https://www.microsoft.com/en-eg/download/details.aspx?id=40784

3. Run install.requirements.bat

4. Go to the folder configs
and add your email and password in Netflix in config.py (open the file with Notepad++), search for

	"email": "enter your email address here", # Enter the email address of your Netflix account here
	"password": "enter your password here", # Enter the password of your Netflix account here
  
and replace "enter your email address here" with the email of your account in Netflix, 
and replace "enter your password here" with the password of your account in Netflix, and it will be like

	"email": "david2021236@protonmail.com", # Enter the email address of your Netflix account here
	"password": "25&ns&257", # Enter the password of your Netflix account here

5. Install this Chrome extension

https://chrome.google.com/webstore/detail/get-cookiestxt/bgaddhkoddajcdgocldbbfleckgcbcid

and go to netflix.com and download the cookies, rename the file to cookies.txt and put it in

configs\Cookies

For Firefox use this addon

https://addons.mozilla.org/en-US/firefox/addon/cookies-txt-one-click/

6. In the script's folder three batches

**A download.video.bat**

For downloading the video in AVC high profile with the audio and subtitles use

`python NFripper.py --high`

For downloading the video in Main profile with the audio and subtitles use

`python NFripper.py --main`

the script will download only the original audio with the highest bitrate and all the available subtitles, 
to download the audio in all the available languages use

`python NFripper.py --high --all-audios`

or

`python NFripper.py --main --all-audios`

To set the default audio language in config.py replace

`"AUDIO": "None",`

with the language you want, for example for the French language to be the default audio language use

`"AUDIO": "fra",`

To set the default subtitles language in config.py replace

`"SUB": "None",`

with the language you want, for example for the English language to be the default subtitles language use

`"SUB": "eng",`

If you want to downlod the video for a specific seasons or all the seasons use

`python NFripper.py 80014749 --high -s 1`

`python NFripper.py 80014749 --high -s 1,3,5`

`python NFripper.py 80014749 --high -s 1-5`

To download the video in 720p use

`python NFripper.py --high -q 720`

If you do not want to download the subtitles use

`python NFripper.py --high --ns`

When you run any of the three batches you will be asked for the URL of the TV Show or the movie in Netflix

for example use this link to download the video of Rick and Morty

https://www.netflix.com/title/80014749

or you could add the ID like this

`python NFripper.py 80014749 --high`

The downloads will be saved in the folder `"downloads\netflix"`

For adding more options use the instructions in NFripper.py, open the file with Notepad++.

**B. download.subtitles.bat**

For downloading only the subtitles

`python NFripper.py --nv --na --keep --slang eng`

change eng to the language you need to download the subtitles in.

To download the subtitles in multiple languages use

`python NFripper.py --nv --na --keep --slang eng fra rus pol`

If you want to downlod the subtitles for a specific episode or episodes use

`python NFripper.py --nv --na --keep --slang eng -s 1 -e 8`

`python NFripper.py --nv --na --keep --slang eng -s 1 -e 1-3`

`python NFripper.py --nv --na --keep --slang eng -s 1 -e 2,4,7`

You could download the subtitles of all the seasons by using

`python NFripper.py 70153404 --nv --na --keep -s 1-10 --slang eng`

remove --slang eng if you want to download the subtitles in all of the available languages in Netflix of your country.

To download the subtitles in all of the languages and all the forced subtitles use

`python NFripper.py --nv --na --keep --all-forced`

To download the forced subtitles in specific languages use

`python NFripper.py --nv --na --keep --flang jpn tha`

**C. download.audio.bat**

For downloading only the audio

`python NFripper.py --ns --nv --keep --alang eng`

change eng to the language you need to download the audio in

To download the audio in multiple languages use

`python NFripper.py --ns --nv --keep --alang eng fra rus pol`

To download the audio in 2 channels only use

`python NFripper.py --ns --nv --keep --only-2ch-audio`

To download the audio in AAC codec use

`python NFripper.py 80014749 --ns --nv --keep --alang eng -s 1 -e 1 --aformat-51ch aac`

*or*

`python NFripper.py 80014749 --ns --nv --keep --alang eng -s 1 -e 1 --aformat-2ch aac`

To download the audio in a specific bitrate use

`python NFripper.py 81185548 --audio-bitrate 384`

**If you got the error message "title is not available in your Netflix region" in configs\Cookies
delete cookies_nf.txt and add a new cookies.txt, or change the VPN if you are using a VPN, not every VPN will work with this script.**

**Don't put any files in the folder configs\Tokens, the script will generate netflix_token.json by itself.**

In case of getting any error messages with aria2c you could disable it by adding the command `--no-aria2c`

`python NFripper.py --no-aria2c --high`

**To download the Interactive TV shows and movies, in MSLClient.py which is in the folder helpers/Parsers/Netflix/ 
change it to "isBranching": True and after you download the video change it to "isBranching": False.**

https://help.netflix.com/en/node/62526


