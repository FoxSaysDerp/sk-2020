## Ustawianie parametrów sieci

### Zadania

0. Z wykorzystaniem dowolnych systemów operacyjnych na których potrafisz uruchomić interpreter ``python`` oraz oprogramowania virtualbox odwzoruj poniższy schemat sieci:

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj i uruchom program ``server.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``
2. na 2 z komputerów zainstaluj i uruchom program ``client.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``
3. Manipulując konfiguracją sieci na poziomie virtualbox, uruchom serwer czatu, oraz udostępnij go na wybranym porcie oraz adresie tak aby istniała możliwość połączenia przez inne osoby w obrębie pracowni
4. Zainstaluj oprogramowanie serwera HTTP ``nginx`` lub innego, skonfiguruj plik index.html wg instrukcji, sprawdź dostępność strony z wykorzystaniem dowolnego klienta protokołu ``HTTP`` z różnych konfiguracji IP
5. Posługując się programami tj: ``netstat`` lub ``lsof`` sprawdź na jakich portach zostały uruchomione serwery czatu czy HTTP

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 10.0.15.4 | |
| MASKA  | /24 (255.255.255.0) | |
|   |  | |
| PC 2  |  | |
| IP - address  | 10.0.15.6 | |
| MASKA  | /24 (255.255.255.0 )| |

Weryfikacja połączenia

Polecenie - PC 1
```
ping 10.0.15.6
```

Efekt - PC 1
```
Nawiązano połączenie pomiędzy maszynami
```

Polecenie - PC 2
```
ping 10.0.15.4
```

Efekt - PC 2
```
Nawiązano połączenie pomiędzy maszynami
```


Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.10.10 | ip addr add 192.168.10.10/24 dev eth0 |
| MASKA  | 255.255.255.0 | |
|   |  | |
| PC 2  |  | |
| IP - address  | 192.168.10.11 | ip addr add 192.168.10.11/23 dev eth0 |
| MASKA  | 255.255.128.0 | |
| PC 2  |  | |
| IP - address  | 172.16.100.100 | ip addr add 172.16.100.100/16 dev eth0 |
| MASKA  | 255.255.0.0 | |

Weryfikacja połączenia

Polecenie - PC 1
```
ping 192.168.10.11
```

Efekt - PC 1
```
Nawiązano połączenie pomiędzy maszynami
```

Polecenie - PC 2
```
ping 192.168.10.10
```

Efekt - PC 2
```
Nawiązano połączenie pomiędzy maszynami
```

Polecenie - PC 2
```
ping 172.16.100.100
```

Efekt - PC 2
```
Brak połączenia pomiędzy maszynami
```

## Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.56.120 | ip addr add 192.168.8.120/24 dev eth0 |
| MASKA  |  | 255.255.255.0 |
|   |  | |
| PC 2  |  | |
| IP - address  | 192.168.56.240 | ip addr add 192.168.56.240/24 dev eth0 |
| MASKA  |  | 255.255.255.0 |

Weryfikacja połączenia

Polecenie - PC 1
```
ping 192.168.56.240
```

Efekt - PC 1
```
Nawiązano połączenie pomiędzy maszynami
```

Polecenie - PC 2
```
ping 192.168.56.120
```

Efekt - PC 2
```
Nawiązano połączenie pomiędzy maszynami
```

### Utrwalenie konfiguracji

Dlaczego? Jak? Co? :)
Konfiguracje muszą być utrwalane, aby po zatrzymaniu maszyn nie utracić połączenia. Służy do tego odpowiedni plik konfiguracyjny.

### Warto wiedzieć

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| Lokalizacja pliku z konfiguracją sieci| | |
| UP -> Wyłączenie interfejsu sieciowego| | |
| DOWN -> Włączenie interfejsu sieciowego| | |
| Sprawdzenie obecnych parametrów | | |
| lista wszystkich interfejsów | | |
| Które interfejsy jakie porty słuchają | | |

