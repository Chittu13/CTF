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
### Steganography audio <a name="stenographyaudio"></a>





## Web <a name="web"></a>

## Cryptography <a name="crypto"></a>

## Forensics <a name="forensics"></a>
- [outer space audio](https://github.com/colaclanth/sstv.git)
  - ```sudo python3 setup.py install```
  - ```sstv -d file.wav -o result.png```
  - if the hit is related about SSTV(slow scan TV)

## Reverse Engineering <a name="rev"></a>

