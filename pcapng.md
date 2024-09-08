ip.dst == 172.20.2.136 && tcp.dstport == 8008
![image]()
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
