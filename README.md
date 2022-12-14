# Remembrance
[![Test Coverage](https://img.shields.io/badge/Test%20Coverage-100%25-success)](https://github.com/jacob-h-barrow/Penguin-Services)
[![Security](https://img.shields.io/badge/Secure-True-informational)](https://github.com/jacob-h-barrow/Penguin-Services)
[![Platform](https://img.shields.io/badge/Platform-Ubuntu%2020%2B-critical)](https://github.com/jacob-h-barrow/Penguin-Services)
[![Python Version](https://img.shields.io/badge/Python-3.8%2B-critical)](https://github.com/jacob-h-barrow/Penguin-Services)
[![MIT License](https://img.shields.io/badge/License-MIT-lightgrey)](https://github.com/jacob-h-barrow/Penguin-Services/blob/main/Penguin-Services.png)

![RemembranceBanner](https://user-images.githubusercontent.com/112576275/192099739-bdbe9b3c-4893-4168-a9a1-194fe387d2e0.png)

- Created By Jacob H Barrow
- 
## Description
Provides an interface to the following Linux files: /proc/net/tcp, /proc/net/tcp6, /proc/net/udp, /proc/net/udp6, /proc/net/packet.
There is an option to only parse certain files, with the option to sort on all the fields (lambda sorting).
This is the same file that populates the information in netstat!

Gist: Use the IpStat iterable in a simple for loop. More advanced options are available in other modules.
Gist: Use the ConnTrackHandler context manager to provide a handle over a netstat-like response.

Dataclass:
    - Connection
        - proto: str
        - connectionId: str
        - uid: str
        - localAddr: str
        - remoteAddr: str
        - state: str
        - pid: str
        - exeName: str

    - PacketSocket
        - proto: str
        - pid: str
        - exeName: str

This module allows the user to for loop all the current connections on your device.

## Usage
``` python
>>> from remembrance import IpStatHandler, ConnTrackHandler
>>>
>>> for conn in IpStat()
>>>     print(conn)
>>>
>>> with ConnTrackHandler() as handler:
>>>     print(handler)
>>>     for i in range(3):
>>>         handler.refreshIpStat()
>>>     print(handler.retrieveIpInfo("FOREIGN_IP"))
```

- `ConnTrackHandler()`: Netstat-like Context Manager, acts as netstat-like handler using the with statement.
- `ConnTrack.refreshIpStat()`: Retrieve all specified connections to the system.
- `ConnTrack.retrieveIpInfo(ip)`: Retrieve all of the history/connections associated with the ip address on this system.
- `ConnTrack.retrieveIpInfo_LastN(ip)`: Retrieve the last n ip connections associated with this ip on this system. 
- `IpStat()` - Provides an iterable to for loop over current device connections, essentially returning an iterable object over /proc/net/tcp, /proc/net/tcp6, /proc/net/udp, /proc/net/udp6, /proc/net/packet by default.

### Dumbledore's Army
