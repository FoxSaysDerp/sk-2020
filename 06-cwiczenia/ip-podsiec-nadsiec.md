Podsieci i nadsieci IP
----------------------

adresacja
-----------------------------------------------------
| PC     |  interfejs   | adres  |
| --------- |:-------------| :---------------| 
| ``PC1``   | enp0s3 | 192.168.100.101/24 |
| ``PC-R-1``| enp0s3 |  192.168.200.97/29 |
| ``PC-R-1``| enp0s8 | 192.168.100.1/24 |
| ``PC-R-2``| enp0s3 | 192.168.200.98/29 |
| ``PC-R-2``| enp0s8  | 192.168.0.129/27 |
| ``PC-R-2``| enp0s9  | 192.168.0.193/27 |
| ``PC-R-2``| enp0s10 | 192.168.0.65/27 |
| ``PC2``   | enp0s3  | 192.168.0.130/27 |

routing
-------

| destination | trasa | interfejs  |
| --------- |:-------------| :---------------| 
| ``PC1``     |  | |
| ``default`` | ``ip route add default via 192.168.100.1/24 dev eth0`` | enp0s3 ``ip addr add 192.168.100.101/24 dev eth0`` |
| ``PC-R-1``  |  |        |
| ``default`` | ``ip route add default via 192.168.200.98/29 dev eth0``  | enp0s3 ``ip addr add 192.168.200.97/29 dev eth0`` |
| ``default`` | ``ip route add default via 192.168.100.101/24 dev eth0``  | enp0s8 ``ip addr add 192.168.100.1/24 dev eth1`` |
| mozna dzielic   |  |  |
| ``192.168.0.64/27``  | ``ip route add 192.168.0.64/27 via 192.168.200.98/29 dev eth1``  | enp0s8  |
| ``192.168.0.128/27`` | ``ip route add 192.168.0.128/27 via 192.168.200.98/29 dev eth1`` | enp0s8 |
| ``192.168.0.192/27`` | ``ip route add 192.168.0.192/27 via 192.168.200.98/29 dev eth1``  | enp0s8 |
| lub za 1 iteracją   |  |  |
| ``192.168.0.64/27`` ``192.168.0.128/27`` ``192.168.0.192/27``   | ``ip route add 192.168.0.0/24 via 192.168.200.98/29 dev eth1``  | enp0s8|
| ``PC-R-2``  |  |        |
| ``default`` | ``ip route add default via 192.168.200.97/29 dev eth0``  | enp0s3 ``ip addr add 192.168.200.98/29 dev eth0`` |
| ``192.168.100.0/24`` | ``ip route add 192.168.100.0/24 via 192.168.200.97/29 dev eth0``  | enp0s3 |
| ``defaut``  | ``ip route add default via 192.168.0.130/27 dev eth1``  | enp0s8 ``ip addr add 192.168.0.129/27 dev eth1`` |
| ``default`` | ``ip route add default via 192.168.0.194/27 dev eth2``  | enp0s9 ``ip addr add 192.168.0.193/27 dev eth2`` |
| ``default`` | ``ip route add default via 192.168.0.66/27 dev eth3``  | enp0s10 ``ip addr add 192.168.0.65/27 dev eth3`` |


Zadanie
------------

![zadanie 5](over_network.svg)

1. Wykorzystując program DIA lub draw IO ikony CISCO
  * Przygotuj diagram powyższej sieci uwzględniając urządzenia tj:
    * ROUTER
    * SWITCH
    * PC
  * Uzupełnij diagram o adresację sieci oraz poszczególnych urządzeń
  
2.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem
   * W pierwszej kolejności przygotuj ``PC1``, ``PC-R-1``, ``PC-R-2``, ``PC-2``
   * Do konfiguracji wykorzystaj dane z tabeli powyżej
   * Rozszerz istniejącą konfigurację dzieląc istnijącą sieć dla ``PC2`` na 3 podsieci zgodnie z diagramem
   * Przetestuj połączenie pomiędzy wszystkimi elementami sieci ``PC1->PC2`` ``PC1->PC4``
   * Zapewnij permanentną konfigurację, dodając odpowiednie wpisy w plikach konfiguracji


Zadanie do domu
---------------
1. Przygotuj schemat powyższej sieci z wykorzystaniem programu CISCO PACKET TRACER
2. Zaproponuj adresację dla poniższego schematu
   Centrum Informatyki dysponje adresem CIDR ``149.156.48.0/22`` część z tej przestrzeni zatrzymuje na potrzeby własnych potrzeb, pozostałą część oddaje innym jednostkom

  ![zadanie 6](campus-network.svg)
