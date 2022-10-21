# Aircrack-ng

## To crack WEP for a given essid name and store into a file
```shell
aircrack-ng -a 1 -e <essid> -l <output file> <.cap or .ivs file(s)>
```

## To crack WPA/WPA2 from airolib-ng database
```shell
aircrack-ng -e <essid> -r <database> <.cap or .ivs file(s)>
```

## To crack WPA/WPA2 from a wordlist
```shell
aircrack-ng -e <essid> -w <wordlist> <.cap or .ivs file(s)>
```

## To crack a given bssid
```shell
aircrack-ng -b <bssid> -l <output file> <.cap or .ivs file(s)>
```

## To crack a given bssid using FMS/Korek method
```shell
aircrack-ng -K -b <bssid> <.cap or .ivs file(s)>
```

## To crack a given essid (WEP) and display the ASCII of the key
```shell
aircrack-ng -e <essid> -s <.cap of .ivs file(s)>
```

## To crack a given essid (WEP) and create a EWSA Project
```shell
aircrack-ng -e <essid> -E <EWSA file> <.cap or .ivs file(s)>
```
