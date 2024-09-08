- __Flag formate is `shift{*}`__
- ip.dst == 172.20.2.136 && tcp.dstport == 8008
  <br>
  <br>
![image](https://github.com/Chittu13/CTF/blob/main/image/wireshark.gif)
```py
from scapy.all import *

flag = []

packets = rdpcap("space.pcapng")

for pkt in packets:
    if TCP in pkt and pkt[TCP].dport == 8008 and pkt[IP].dst == '172.20.2.136':
        # Get the TCP window size
        window_size = pkt[TCP].window
        character = chr(window_size)
        flag.append(character)
        print(f'Window size: {window_size} -> ASCII: {character}')

print(''.join(flag))
```

__Flag: `shctf{1_sh0uld_try_h1d1ng_1n_th3_ch3cksum_n3xt_t1me_0817}`__
