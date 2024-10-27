# CTF 2.0
- [Hints](/CTF/Important.md)
- [Steganography](#stenography)
  - [Steganography audio](#stenographyaudio)
- [Web](#web)
- [Cryptography](#crypto)
- [Forensics](#forensics)
- [Reverse Engineering](#rev)
- [OSINT](#osint)
- [PWD](#pwd)

## Steganography <a name="stenography"></a>

- ```file image.png```
- - ```strings image.png```
- ```steghide --extract -sf image.jpg -p <password>```
- ```stegcracker imag.png /usr/share/wordlists/rockyou.txt```
- ```pngcheck image.png```
  - If you are getting error then use below command
  - __`foremost image.png` ---> to recover the original image__
- ```sudo apt install libimage-exiftool-perl -y```
  - ```exiftool image.png```
  - ```eog image.png```
- ```xxd image.png```
  - if you see IEND chunk in exiftool use this command.
- ```find | xargs cat | grep "find"``` //if you have lot of text file then you this
  - ```grep -rni "flag{.*}"```
- Download the stegsolve.jar in any GitHub
  - ```java -jar stegsolve.jar```
  - make sure that you give the permission. 
- [ZXing Decoder](https://zxing.org/w/decode.jspx)
  - If the image is QR code image
- ```sudo apt install ruby```
  - ```sudo gem install zsteg```
  - ```zsteg image.png``` or ```zsteg  -a image.png```
  - only for png image.
- ```binwalk -e image.png```
  - ```binwalk --dd = ".*" image.png```
- ```outguess -r image.png flag.txt```
  - for the LSB.
- For the noice image
  - go to --> [online](https://piellardj.github.io/stereogram-solver)
- one more for the LSB.
  - go to ---> [jsteg](https://github.com/lukechampine/jsteg) (clone it!!)
  - open the file
  - run this command ```go run cmd/jsteg/main.go reveal ~/Desktop/image.jpg```
- [Unicode](https://330k.github.io/misc_tools/unicode_steganography.html) 
  - zero width space
- Use ```GIMP``` to work with QR dots
- ```otfinfo -i font.ttf``` for file.ttf
- ```zbarimg image.png``` to read the qr code
- redacted text (cover with block) in a given pdf
  - ```pdftotext file.pdf``` or ```pdftohtml  file.pdf```
- suspicious space and tabs in a given text file
  - __[python](https://github.com/Chittu13/All_in_one/blob/main/CTF/Codes/space.md)__ script to extract and convert from binary to ASCII and get  the flag.

## Steganography audio <a name="stenographyaudio"></a>
- [Morsecode](https://morsecode.world/international/decoder/audio-decoder-adaptive.html)
- [stegolsb](https://github.com/ragibson/Steganography.git)
  - If the audio is related to LSB
  - ```cd Steganography```
  - give the permission
  - ```python3 setup.py install```
  - ```stegolsb wavsteg -r -i file.wav -o flag.txt -n 2 -b 1000```




## Web <a name="web"></a>
- ```http://127.0.0.1:808/index.php?page=' and die(system("cat index.php")) or ' ```
  - if you want to read the index.php use this payload in the url "    ' and die(system("cat index.php")) or ' "
- ```curl -X POST --data hash=2196812e91c29df34f5e217cfd639881 "http://example.com:8080/admin.php"```
  - you use this if you found hash in the sorce page
- ```wget -m http://example.com:8080/```
  - here it will download the all the file in the website
  - ```grep -R "CTF{.*}"``` use this commond after download the all files
- ```gobuster dir -k -u http://127.0.0.1/ -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x txt,cnf,conf```
- ```gobuster dir -w /usr/share/wordlists/dirb/common.txt -x .html,.php -u http://192.168.51.11/```

## Cryptography <a name="crypto"></a>
1. This is [Hill Cipher](https://www.dcode.fr/hill-cipher), see how it works or use an online decoder
   - __[Reference](https://github.com/Chittu13/All_in_one/tree/main/CTF/cryptography/hill.md)__

2. Replace small letters with A, capital letters with B
    - ```BA BAAB AAABABAAAAABB AAA BBBBAA BBABAAA BA ABBABAAAB AABAAAA AB AAAAAA AABABB BBAABBABBAABA```
    - [bacon-cipher](https://www.dcode.fr/bacon-cipher)
## Forensics <a name="forensics"></a>
- [outer space audio](https://github.com/colaclanth/sstv.git)
  - ```sudo python3 setup.py install```
  - ```sstv -d file.wav -o result.png```
  - if the hit is related about SSTV(slow scan TV)
- ```strings flag.zip | grep -i cit | sort | uniq -u```
  - Given zip file was numerous directories with a flag.txt
- A simple script to converts the RGB values of each pixel into characters
  - [Script](https://github.com/Chittu13/All_in_one/tree/main/CTF/Codes)
## Reverse Engineering <a name="rev"></a>
- ```ltrace ./filename```
  - The file is executable_file so we use ./filename
- ```strace ./filename```
- [ghidra](https://github.com/NationalSecurityAgency/ghidra/releases)
  - Download the zip file from the above line```hidra_11.0.3_PUBLIC_20240410.zip```
- ```objbump -d executablefile``` it will show the assembly code of the file

## OSINT <a name="osint"></a>
- To find the user in the internet use this tool called [sherlock](https://github.com/Chittu13/All_in_one/blob/main/CTF/Tools/sherlock.md)

## PWD <a name="pwd"></a>


