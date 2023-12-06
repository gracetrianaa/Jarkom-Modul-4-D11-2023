# Jarkom-Modul-4-D11-2023

| Nama                              | NRP        |
| --------------------------------- | ---------- |
| Gracetriana Survinta Septinaputri | 5025211199 |
| Muhammad Rifqi Fadhilah           | 5025211228 |

- [VLSM-GNS3](#vlsm-gns3)
  - [Rute](#rute)
  - [Pohon IP](#pohon-ip)
  - [Topologi](#topologi)
  - [Subnetting](#subnetting)
  - [Routing](#routing)
- [CIDR-CPT](#cidr-cpt)

## VLSM-GNS3

### Rute

![Alt text](images/vlsm_topologi_21.png)

| Nama Subnet | Rute                                            | Jumlah IP | Netmask |
| ----------- | ----------------------------------------------- | --------- | ------- |
| A1          | Heiter-Switch8-Sein-Switch8-RiegelCanyon        | 512       | /22     |
| A2          | Lawine-Switch7-BredtRegion-Switch7-Heiter       | 31        | /26     |
| A3          | Lawine-Linie                                    | 2         | /30     |
| A4          | Linie-Switch11-GranzChannel                     | 255       | /23     |
| A5          | Eisen-Linie                                     | 2         | /30     |
| A6          | Eisen-Switch1-Richter-Switch1-Revolte           | 3         | /29     |
| A7          | Eisen-Lugner                                    | 2         | /30     |
| A8          | Lugner-Switch10-TurkRegion                      | 1001      | /22     |
| A9          | Lugner-Switch9-GrobeForest                      | 251       | /24     |
| A10         | Eisen-Switch0-Stark                             | 2         | /30     |
| A11         | Aura-Eisen                                      | 2         | /30     |
| A12         | Aura-Frieren                                    | 2         | /30     |
| A13         | Frieren-Switch3-LakeKorridor                    | 25        | /27     |
| A14         | Frieren-Flamme                                  | 2         | /30     |
| A15         | Flamme-Himmel                                   | 2         | /30     |
| A16         | Himmel-Switch6-SchwerMountains                  | 6         | /29     |
| A17         | Flamme-Switch5-RohrRoad                         | 1001      | /22     |
| A18         | Flamme-Fern                                     | 2         | /30     |
| A19         | Fern-Switch4-LaubHills-Switch4-AppetitRegion    | 1023      | /21     |
| A20         | Aura-Denken                                     | 2         | /30     |
| A21         | Denken-Switch2-RoyalCapital-Switch2-WilleRegion | 127       | /24     |
| Total       |                                                 | 4255      | /19     |

### Pohon IP

![Alt text](<images/jarkom modul 4_vlsm tree.jpg>)

#### Pembagian IP berdasarkan Pohon IP

| Subnet | Network ID  | Netmask         | Broadcast    |
| ------ | ----------- | --------------- | ------------ |
| A1     | 10.27.16.0  | 255.255.252.0   | 10.27.19.255 |
| A2     | 10.27.0.128 | 255.255.255.192 | 10.27.0.191  |
| A3     | 10.27.0.36  | 255.255.255.252 | 10.27.0.39   |
| A4     | 10.27.6.0   | 255.255.254.0   | 10.27.7.255  |
| A5     | 10.27.0.32  | 255.255.255.252 | 10.27.0.35   |
| A6     | 10.27.0.48  | 255.255.255.248 | 10.27.0.55   |
| A7     | 10.27.0.28  | 255.255.255.252 | 10.27.0.31   |
| A8     | 10.27.12.0  | 255.255.252.0   | 10.27.15.255 |
| A9     | 10.27.4.0   | 255.255.255.0   | 10.27.4.255  |
| A10    | 10.27.0.24  | 255.255.255.252 | 10.27.0.27   |
| A11    | 10.27.0.20  | 255.255.255.252 | 10.27.0.23   |
| A12    | 10.27.0.16  | 255.255.255.252 | 10.27.0.19   |
| A13    | 10.27.0.64  | 255.255.255.224 | 10.27.0.95   |
| A14    | 10.27.0.12  | 255.255.255.252 | 10.27.0.15   |
| A15    | 10.27.0.8   | 255.255.255.252 | 10.27.0.11   |
| A16    | 10.27.0.40  | 255.255.255.248 | 10.27.0.47   |
| A17    | 10.27.8.0   | 255.255.252.0   | 10.27.11.255 |
| A18    | 10.27.0.4   | 255.255.255.252 | 10.27.0.7    |
| A19    | 10.27.24.0  | 255.255.248.0   | 10.27.31.255 |
| A20    | 10.27.0.0   | 255.255.255.252 | 10.27.0.3    |
| A21    | 10.27.2.0   | 255.255.255.0   | 10.27.2.255  |

### Topologi

![Alt text](<images/Screenshot topologi.png>)

### Subnetting

Melakukan konfigurasi interface pada `Edit Network Configuration` untuk mengatur IP tiap interfacenya.

- Aura

```
auto eth1
iface eth1 inet static
	address 10.27.0.1
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.27.0.17
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.27.0.21
	netmask 255.255.255.252
```

- Frieren

```
auto eth0
iface eth0 inet static
	address 10.27.0.18
	netmask 255.255.255.252
	gateway 10.27.0.17

auto eth1
iface eth1 inet static
	address 10.27.0.13
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.27.0.65
	netmask 255.255.255.224
```

- Flamme

```
auto eth0
iface eth0 inet static
	address 10.27.0.14
	netmask 255.255.255.252
	gateway 10.27.0.13

auto eth1
iface eth1 inet static
	address 10.27.0.5
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.27.0.9
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.27.8.1
	netmask 255.255.252.0
```

- Himmel

```
auto eth0
iface eth0 inet static
	address 10.27.0.10
	netmask 255.255.255.252
	gateway 10.27.0.9

auto eth1
iface eth1 inet static
	address 10.27.0.41
	netmask 255.255.255.248
```

- SchwerMountains

```
auto eth0
iface eth0 inet static
	address 10.27.0.42
	netmask 255.255.252.0
	gateway 10.27.0.41
```

- Fern

```
auto eth0
iface eth0 inet static
	address 10.27.0.6
	netmask 255.255.255.252
	gateway 10.27.0.5

auto eth1
iface eth1 inet static
	address 10.27.24.1
	netmask 255.255.248.0
```

- LaubHills

```
auto eth0
iface eth0 inet static
	address 10.27.24.2
	netmask 255.255.248.0
	gateway 10.27.24.1
```

- AppetitRegion

```
auto eth0
iface eth0 inet static
	address 10.27.24.3
	netmask 255.255.248.0
	gateway 10.27.24.1
```

- RohrRoad

```
auto eth0
iface eth0 inet static
	address 10.27.8.2
	netmask 255.255.252.0
	gateway 10.27.8.1
```

- LakeKorridor

```
auto eth0
iface eth0 inet static
	address 10.27.0.66
	netmask 255.255.255.224
	gateway 10.27.0.65
```

- Eisen

```
auto eth0
iface eth0 inet static
	address 10.27.0.22
	netmask 255.255.255.252
	gateway 10.27.0.21

auto eth1
iface eth1 inet static
	address 10.27.0.33
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.27.0.29
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 10.27.0.25
	netmask 255.255.255.252

auto eth4
iface eth4 inet static
	address 10.27.0.49
	netmask 255.255.255.248
```

- Linie

```
auto eth0
iface eth0 inet static
	address 10.27.0.34
	netmask 255.255.255.252
	gateway 10.27.0.33

auto eth1
iface eth1 inet static
	address 10.27.0.37
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.27.6.1
	netmask 255.255.254.0
```

- Lawine

```
auto eth0
iface eth0 inet static
	address 10.27.0.38
	netmask 255.255.255.252
	gateway 10.27.0.37

auto eth1
iface eth1 inet static
	address 10.27.0.129
	netmask 255.255.255.192
```

- Heiter

```
auto eth0
iface eth0 inet static
	address 10.27.0.131
	netmask 255.255.255.192
	gateway 10.27.0.129

auto eth1
iface eth1 inet static
	address 10.27.16.1
	netmask 255.255.252.0
```

- Sein

```
auto eth0
iface eth0 inet static
	address 10.27.16.2
	netmask 255.255.252.0
	gateway 10.27.16.1
```

- RiegelCanyon

```
auto eth0
iface eth0 inet static
	address 10.27.16.3
	netmask 255.255.252.0
	gateway 10.27.16.1
```

- BredtRegion

```
auto eth0
iface eth0 inet static
	address 10.27.0.130
	netmask 255.255.255.192
	gateway 10.27.0.129
```

- GranzChannel

```
auto eth0
iface eth0 inet static
	address 10.27.6.2
	netmask 255.255.254.0
	gateway 10.27.6.1
```

- Richter

```
auto eth0
iface eth0 inet static
	address 10.27.0.50
	netmask 255.255.255.248
	gateway 10.27.0.49
```

- Revolte

```
auto eth0
iface eth0 inet static
	address 10.27.0.51
	netmask 255.255.255.248
	gateway 10.27.0.49
```

- Lugner

```
auto eth0
iface eth0 inet static
	address 10.27.0.30
	netmask 255.255.255.252
	gateway 10.27.0.29

auto eth1
iface eth1 inet static
	address 10.27.12.1
	netmask 255.255.252.0

auto eth2
iface eth2 inet static
	address 10.27.4.1
	netmask 255.255.255.0
```

- TurkRegion

```
auto eth0
iface eth0 inet static
	address 10.27.12.2
	netmask 255.255.252.0
	gateway 10.27.12.1
```

- GrobeForest

```
auto eth0
iface eth0 inet static
	address 10.27.4.2
	netmask 255.255.255.0
	gateway 10.27.4.1
```

- Stark

```
auto eth0
iface eth0 inet static
	address 10.27.0.26
	netmask 255.255.255.252
	gateway 10.27.0.25
```

- Denken

```
auto eth0
iface eth0 inet static
	address 10.27.0.2
	netmask 255.255.255.252
	gateway 10.27.0.1

auto eth1
iface eth1 inet static
	address 10.27.2.1
	netmask 255.255.255.0
```

- RoyalCapital

```
auto eth0
iface eth0 inet static
	address 10.27.2.2
	netmask 255.255.255.0
	gateway 10.27.2.1
```

- WilleRegion

```
auto eth0
iface eth0 inet static
	address 10.27.2.3
	netmask 255.255.255.0
	gateway 10.27.2.1
```

### Routing

Mengatur konfigurasi untuk routing pada router tertentu dengan command

```
route add -net <NID subnet> netmask <netmask> gw <IP gateway>
```

Berikut adalah tabel routing tiap router yang terpakai

<table class="tg">
<thead>
  <tr>
    <th class="tg-a5cz"><span>Router</span></th>
    <th class="tg-a5cz"><span>Subnet</span></th>
    <th class="tg-a5cz"><span>Network</span></th>
    <th class="tg-a5cz"><span>Netmask</span></th>
    <th class="tg-a5cz"><span>Gateway</span></th>
    <th class="tg-a5cz"><span>Console</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-baqh" rowspan="18">Aura</td>
    <td class="tg-7zrl">A1</td>
    <td class="tg-7zrl">10.27.16.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.16.0 netmask 255.255.252.0 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A2</td>
    <td class="tg-7zrl">10.27.0.128</td>
    <td class="tg-7zrl">255.255.255.192</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.0.128 netmask 255.255.255.192 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A3</td>
    <td class="tg-7zrl">10.27.0.36</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.0.36 netmask 255.255.255.252 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A4</td>
    <td class="tg-7zrl">10.27.6.0</td>
    <td class="tg-7zrl">255.255.254.0</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.6.0 netmask 255.255.254.0 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A5</td>
    <td class="tg-7zrl">10.27.0.32</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.0.32 netmask 255.255.255.252 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A6</td>
    <td class="tg-7zrl">10.27.0.48</td>
    <td class="tg-7zrl">255.255.255.248</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.0.48 netmask 255.255.255.248 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A7</td>
    <td class="tg-7zrl">10.27.0.28</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.0.28 netmask 255.255.255.252 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A8</td>
    <td class="tg-7zrl">10.27.12.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.12.0 netmask 255.255.252.0 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A9</td>
    <td class="tg-7zrl">10.27.4.0</td>
    <td class="tg-7zrl">255.255.255.0</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.4.0 netmask 255.255.255.0 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A10</td>
    <td class="tg-7zrl">10.27.0.24</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.22</td>
    <td class="tg-7zrl">route add -net 10.27.0.24 netmask 255.255.255.252 gw 10.27.0.22</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A13</td>
    <td class="tg-7zrl">10.27.0.64</td>
    <td class="tg-7zrl">255.255.255.224</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.0.64 netmask 255.255.255.224 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A14</td>
    <td class="tg-7zrl">10.27.0.12</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.0.12 netmask 255.255.255.252 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A15</td>
    <td class="tg-7zrl">10.27.0.8</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.0.8 netmask 255.255.255.252 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A16</td>
    <td class="tg-7zrl">10.27.0.40</td>
    <td class="tg-7zrl">255.255.255.248</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.0.40 netmask 255.255.255.248 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A17</td>
    <td class="tg-7zrl">10.27.8.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.8.0 netmask 255.255.252.0 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A18</td>
    <td class="tg-7zrl">10.27.0.4</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.0.4 netmask 255.255.255.252 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A19</td>
    <td class="tg-7zrl">10.27.24.0</td>
    <td class="tg-7zrl">255.255.248.0</td>
    <td class="tg-7zrl">10.27.0.18</td>
    <td class="tg-7zrl">route add -net 10.27.24.0 netmask 255.255.248.0 gw 10.27.0.18</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A21</td>
    <td class="tg-7zrl">10.27.2.0</td>
    <td class="tg-7zrl">255.255.255.0</td>
    <td class="tg-7zrl">10.27.0.2</td>
    <td class="tg-7zrl">route add -net 10.27.2.0 netmask 255.255.255.0 gw 10.27.0.2</td>
  </tr>
  <tr>
    <td class="tg-baqh" rowspan="5">Frieren</td>
    <td class="tg-7zrl">A15</td>
    <td class="tg-7zrl">10.27.0.8</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.14</td>
    <td class="tg-7zrl">route add -net 10.27.0.8 netmask 255.255.255.252 gw 10.27.0.14</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A16</td>
    <td class="tg-7zrl">10.27.0.40</td>
    <td class="tg-7zrl">255.255.255.248</td>
    <td class="tg-7zrl">10.27.0.14</td>
    <td class="tg-7zrl">route add -net 10.27.0.40 netmask 255.255.255.248 gw 10.27.0.14</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A17</td>
    <td class="tg-7zrl">10.27.8.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.14</td>
    <td class="tg-7zrl">route add -net 10.27.8.0 netmask 255.255.252.0 gw 10.27.0.14</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A18</td>
    <td class="tg-7zrl">10.27.0.4</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.14</td>
    <td class="tg-7zrl">route add -net 10.27.0.4 netmask 255.255.255.252 gw 10.27.0.14</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A19</td>
    <td class="tg-7zrl">10.27.24.0</td>
    <td class="tg-7zrl">255.255.248.0</td>
    <td class="tg-7zrl">10.27.0.14</td>
    <td class="tg-7zrl">route add -net 10.27.24.0 netmask 255.255.248.0 gw 10.27.0.14</td>
  </tr>
  <tr>
    <td class="tg-baqh" rowspan="2">Flamme</td>
    <td class="tg-7zrl">A16</td>
    <td class="tg-7zrl">10.27.0.40</td>
    <td class="tg-7zrl">255.255.255.248</td>
    <td class="tg-7zrl">10.27.0.10</td>
    <td class="tg-7zrl">route add -net 10.27.0.40 netmask 255.255.255.248 gw 10.27.0.10</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A19</td>
    <td class="tg-7zrl">10.27.24.0</td>
    <td class="tg-7zrl">255.255.248.0</td>
    <td class="tg-7zrl">10.27.0.6</td>
    <td class="tg-7zrl">route add -net 10.27.24.0 netmask 255.255.248.0 gw 10.27.0.6</td>
  </tr>
  <tr>
    <td class="tg-baqh" rowspan="6">Eisen</td>
    <td class="tg-7zrl">A1</td>
    <td class="tg-7zrl">10.27.16.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.34</td>
    <td class="tg-7zrl">route add -net 10.27.16.0 netmask 255.255.252.0 gw 10.27.0.34</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A2</td>
    <td class="tg-7zrl">10.27.0.128</td>
    <td class="tg-7zrl">255.255.255.192</td>
    <td class="tg-7zrl">10.27.0.34</td>
    <td class="tg-7zrl">route add -net 10.27.0.128 netmask 255.255.255.192 gw 10.27.0.34</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A3</td>
    <td class="tg-7zrl">10.27.0.36</td>
    <td class="tg-7zrl">255.255.255.252</td>
    <td class="tg-7zrl">10.27.0.34</td>
    <td class="tg-7zrl">route add -net 10.27.0.36 netmask 255.255.255.252 gw 10.27.0.34</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A4</td>
    <td class="tg-7zrl">10.27.6.0</td>
    <td class="tg-7zrl">255.255.254.0</td>
    <td class="tg-7zrl">10.27.0.34</td>
    <td class="tg-7zrl">route add -net 10.27.6.0 netmask 255.255.254.0 gw 10.27.0.34</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A8</td>
    <td class="tg-7zrl">10.27.12.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.30</td>
    <td class="tg-7zrl">route add -net 10.27.12.0 netmask 255.255.252.0 gw 10.27.0.30</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A9</td>
    <td class="tg-7zrl">10.27.4.0</td>
    <td class="tg-7zrl">255.255.255.0</td>
    <td class="tg-7zrl">10.27.0.30</td>
    <td class="tg-7zrl">route add -net 10.27.4.0 netmask 255.255.255.0 gw 10.27.0.30</td>
  </tr>
  <tr>
    <td class="tg-baqh" rowspan="2">Linie</td>
    <td class="tg-7zrl">A1</td>
    <td class="tg-7zrl">10.27.16.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.38</td>
    <td class="tg-7zrl">route add -net 10.27.16.0 netmask 255.255.252.0 gw 10.27.0.38</td>
  </tr>
  <tr>
    <td class="tg-7zrl">A2</td>
    <td class="tg-7zrl">10.27.0.128</td>
    <td class="tg-7zrl">255.255.255.192</td>
    <td class="tg-7zrl">10.27.0.38</td>
    <td class="tg-7zrl">route add -net 10.27.0.128 netmask 255.255.252.192 gw 10.27.0.38</td>
  </tr>
  <tr>
    <td class="tg-nrix">Lawine</td>
    <td class="tg-7zrl">A1</td>
    <td class="tg-7zrl">10.27.16.0</td>
    <td class="tg-7zrl">255.255.252.0</td>
    <td class="tg-7zrl">10.27.0.131</td>
    <td class="tg-7zrl">route add -net 10.27.16.0 netmask 255.255.252.0 gw 10.27.0.131</td>
  </tr>
</tbody>
</table>

### Testing

Melakukan testing dengan `ping` dari `Stark` ke IP `ApetitRegion` dan `GrobeForest`

![Alt text](<images/Screenshot (185).png>)

## CIDR-CPT

### Penggabungan CIDR

![Screenshot 2023-12-06 211853](https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/401ad45e-719f-41b7-8f15-d3a8b94b0d0a)

<img width="579" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/5875b1ad-40c8-4081-bc6c-507de5c50dce">

<img width="563" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/6f721a2f-de9c-4e57-af7e-9c10c9c99a01">

<img width="559" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/63a4f8db-2dc5-43a6-9877-621e136c94c5">

<img width="557" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/e48aed84-94f7-497f-b39a-7bbd2b4a5fb1">

<img width="560" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/c90978cb-6d9f-47a8-b764-4c63fba30eea">

<img width="559" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/5f9a1e7d-1c6a-4073-b930-26fdc015c27a">

### Tree CIDR

![CIDR TREE](https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/ec6d4f2e-bea4-427e-9ac5-9c6b42257f75)

### Routing

contoh setup routing di aura 

<img width="521" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/3626291e-25d8-4549-a861-5d10bd92fd33">

### Testing

<img width="425" alt="image" src="https://github.com/gracetrianaa/Jarkom-Modul-4-D11-2023/assets/130858750/24dfa4fc-a9be-4654-9897-edb788624889">
