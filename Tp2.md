# TP2 : Hey yo tell a neighbor tell a friend

### 1. Quelques pings

🌞 Prouvez que votre configuration est effective

``` powershell
wheelroot@Ubuntu01:~$ ip addr show enp0s8
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:ec:c9:5c brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.103/24 brd 192.168.56.255 scope global dynamic noprefixroute enp0s8
       valid_lft 363sec preferred_lft 363sec
    inet6 fe80::6220:c497:6a6f:c28e/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```

🌞 Tester que votre LAN + votre adressage IP est fonctionnel

``` powershell
wheelroot@Ubuntu01:~$ ping 192.168.56.103
PING 192.168.56.103 (192.168.56.103) 56(84) bytes of data.
64 bytes from 192.168.56.103: icmp_seq=1 ttl=64 time=0.134 ms
64 bytes from 192.168.56.103: icmp_seq=2 ttl=64 time=0.121 ms
64 bytes from 192.168.56.103: icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from 192.168.56.103: icmp_seq=4 ttl=64 time=0.583 ms
64 bytes from 192.168.56.103: icmp_seq=5 ttl=64 time=0.073 ms
64 bytes from 192.168.56.103: icmp_seq=6 ttl=64 time=0.118 ms
64 bytes from 192.168.56.103: icmp_seq=7 ttl=64 time=0.087 ms
64 bytes from 192.168.56.103: icmp_seq=8 ttl=64 time=0.306 ms
^C
--- 192.168.56.103 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7510ms
rtt min/avg/max/mdev = 0.051/0.184/0.583/0.167 ms
```

🌞 Capture de ping

[Ping](./ping.pcap)

### 1. Animal numérique

🌞 Sur le PC serveur

```powershell 
wheelroot@Ubuntu01:~$ nc -lvp 9999
Listening on 0.0.0.0 9999
Connection received on 192.168.56.1 50899
```

🌞 Sur le PC serveur toujours

```powershell
PS C:\Users\Ethan> netstat -i

Connexion actives

  Proto  Adresse locale          Adresse distante      État            Temps dans l’état (ms)
TCP    192.168.56.1:9999      192.168.56.103:52434   ESTABLISHED        489233
```

🌞 Sur le PC client

```powershell
PS C:\Users\Ethan\Desktop\netcat> ./nc64.exe 192.168.56.103 9999
```

🌞 Echangez-vous des messages

```powershell
wheelroot@Ubuntu01:~$ nc -lvp 9999
Listening on 0.0.0.0 9999
Connection received on 192.168.56.1 50899
uytresq
uytresq

------

PS C:\Users\Ethan\Desktop\netcat> ./nc64.exe 192.168.56.103 9999
uytresq
```

🌞 Utilisez une commande qui permet de voir la connexion en cours

```powershell
PS C:\Users\Ethan> netstat -i

Connexion actives

  Proto  Adresse locale          Adresse distante      État            Temps dans l’état (ms)
TCP    192.168.56.1:9999      192.168.56.103:52434   ESTABLISHED        489233
``` 

🌞 Faites une capture Wireshark complète d'un échange

[Échange](./netcat1.pcap)

🌞 Utilisez Wireshark pour capturer du trafic HTTP

[HTTP](./http.pcap)

🌞 Pour les 5 applications

[Service 1](./Service1.pcap)

```powershell
[RiotClientServices.exe]
  TCP    10.33.79.0:51750       104.16.55.40:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51756       104.16.55.40:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51806       104.18.41.183:443      ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51807       92.122.166.147:443     ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51808       172.65.252.238:5223    ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51809       104.18.40.25:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51812       172.64.146.73:443      ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51819       104.17.174.5:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51820       104.17.173.5:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51821       104.17.174.5:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51822       104.17.174.5:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51825       104.18.157.37:443      ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51842       34.120.195.249:443     ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51847       104.19.147.81:443      ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51850       92.122.166.236:443     ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51851       92.122.166.236:443     ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51852       92.122.166.236:443     ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51853       92.122.166.236:443     ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51854       104.18.40.25:443       ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51855       104.17.174.5:443       ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51856       104.17.173.5:443       ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51857       104.17.174.5:443       ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51859       104.17.173.5:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51860       172.64.149.48:443      ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51862       23.15.179.144:443      ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51870       104.16.56.40:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51871       104.18.41.183:443      ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51873       8.8.4.4:443            ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51875       162.159.61.3:443       ESTABLISHED
 [Riot Client.exe]
  TCP    10.33.79.0:51878       104.16.55.40:443       ESTABLISHED
 [RiotClientServices.exe]
  TCP    10.33.79.0:51891       13.249.9.113:443       ESTABLISHED
 [vgtray.exe]
  TCP    10.33.79.0:51918       172.65.225.25:443      ESTABLISHED
 [brave.exe]
  TCP    10.33.79.0:51919       172.65.225.25:443      CLOSE_WAIT
 [brave.exe]
  TCP    10.33.79.0:51920       162.159.137.232:443    TIME_WAIT
  TCP    10.33.79.0:51921       162.159.61.3:443       TIME_WAIT
  TCP    10.33.79.0:51922       162.159.61.3:443       TIME_WAIT
  TCP    127.0.0.1:6463         0.0.0.0:0              LISTENING
 [Discord.exe]
  TCP    127.0.0.1:51447        0.0.0.0:0              LISTENING
 [BurpSuiteCommunity.exe]
  TCP    127.0.0.1:51757        0.0.0.0:0              LISTENING
 [RiotClientServices.exe]
  TCP    127.0.0.1:51757        127.0.0.1:51838        ESTABLISHED
 [RiotClientServices.exe]
  TCP    127.0.0.1:51757        127.0.0.1:51846        ESTABLISHED
 [RiotClientServices.exe]
  TCP    127.0.0.1:51757        127.0.0.1:51848        ESTABLISHED
 [RiotClientServices.exe]
```

[Service 2](./Service2.pcap)

```powershell
  TCP    10.33.79.0:52080       104.115.89.237:443     ESTABLISHED
>  [WinStore.App.exe]
    TCP    10.33.79.0:52081       150.171.28.10:443      ESTABLISHED
>  [WinStore.App.exe]
    TCP    10.33.79.0:52084       104.115.89.237:443     ESTABLISHED
>  [WinStore.App.exe]
    TCP    10.33.79.0:52086       13.107.246.42:443      ESTABLISHED
>  [WinStore.App.exe]
```

[Service 3](./Service3.pcap)

```powershell
 TCP    10.33.79.0:52111       74.125.71.188:5228     ESTABLISHED
>  [chrome.exe]
    UDP    0.0.0.0:5353           *:*
>  [chrome.exe]
    UDP    0.0.0.0:5353           *:*
>  [chrome.exe]
    UDP    0.0.0.0:5353           *:*
>  [chrome.exe]
    UDP    0.0.0.0:5353           *:*
>  [chrome.exe]
    UDP    0.0.0.0:49275          142.250.179.78:443
>  [chrome.exe]
    UDP    0.0.0.0:49428          142.250.178.138:443
>  [chrome.exe]
    UDP    0.0.0.0:50803          64.233.166.84:443
>  [chrome.exe]
    UDP    0.0.0.0:51316          162.159.61.3:443
>  [chrome.exe]
    UDP    0.0.0.0:52172          74.125.206.94:443
>  [chrome.exe]
    UDP    0.0.0.0:54759          8.8.4.4:443
>  [chrome.exe]
    UDP    0.0.0.0:57548          172.217.20.202:443
>  [chrome.exe]
    UDP    0.0.0.0:60181          142.250.178.138:443
>  [chrome.exe]
    UDP    0.0.0.0:60686          142.250.201.174:443
>  [chrome.exe]
    UDP    0.0.0.0:60797          172.217.20.202:443
>  [chrome.exe]
    UDP    0.0.0.0:60893          216.58.213.74:443
>  [chrome.exe]
    UDP    0.0.0.0:61959          172.217.18.202:443
>  [chrome.exe]
    UDP    0.0.0.0:64629          172.64.41.3:443
>  [chrome.exe]
    UDP    0.0.0.0:65385          172.64.41.3:443
```

[Service 4](./Service4.pcap)

```powershell
PS C:\Users\Ethan> netstat -a -n -b | Select-string Teams -Context 1,0

    TCP    10.33.79.0:52155       20.50.73.10:443        ESTABLISHED
>  [ms-teams.exe]
    TCP    10.33.79.0:52177       52.168.117.169:443     ESTABLISHED
>  [ms-teams.exe]
    TCP    10.33.79.0:52178       13.69.239.74:443       ESTABLISHED
>  [ms-teams.exe]
    TCP    10.33.79.0:52180       52.123.135.185:443     ESTABLISHED
>  [ms-teams.exe]
    TCP    10.33.79.0:52182       52.123.129.14:443      ESTABLISHED
```

[Service 5](./Service5.pcap)

```powershell
PS C:\Users\Ethan> netstat -a -n -b | Select-string Discord -Context 1,0

    TCP    10.33.79.0:52210       162.159.137.232:443    ESTABLISHED
>  [Discord.exe]
    TCP    10.33.79.0:52211       162.159.136.234:443    ESTABLISHED
>  [Discord.exe]
    TCP    127.0.0.1:6463         0.0.0.0:0              LISTENING
>  [Discord.exe]
    UDP    0.0.0.0:52259          162.159.138.232:443
>  [Discord.exe]
    UDP    0.0.0.0:60402          162.159.128.233:443
>  [Discord.exe]
    UDP    0.0.0.0:63882          162.159.135.233:443
>  [Discord.exe]

```