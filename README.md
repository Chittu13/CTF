# CTF

1. [Steganography](#stenography)
2. [Web](#web)
3. [Cryptography](#crypto)
4. [Forensics](#forensics)
5. [Reverse Engineering](#rev)

## Steganography <a name="stenography"></a>

- steghide extract -sf image.jpg -p <password>
- stegcracker imag.png /user/share/wordlists/rockyou.txt
- file image.png
- strings image.png 
- exiftool image.png 
  - eog image.png
- xxd image.png     ----> (if you see IEND chunk in exiftool use this command. )
- Download the stegsolve.jar in any GitHub
  - run java -jar stegsolve.jar ----> ( make sure that you give the permission. )
- If the image is QR code image
  - then go to --> [ZXing Decoder](https://zxing.org/w/decode.jspx)
- sudo apt install ruby
  - sudo gem install zsteg
  - zsteg image.png ----> ( only for png image )
- binwalk -e image.png
  - binwalk --dd = ".*" image.png
- outguess -r image.png flag.txt # for the LSB




## Web <a name="web"></a>
Web <a name="web"></a>
<!-- Add web-related content here -->
## Cryptography <a name="crypto"></a>
<!-- Add cryptography-related content here -->
## Forensics <a name="forensics"></a>
<!-- Add forensics-related content here -->
## Reverse Engineering <a name="rev"></a>
<!-- Add reverse engineering-related content here -->
