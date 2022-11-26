# Jarkom Modul 4 B02
```
Muhammad Daffa Aldriantama (5025201177)
Burhanudin Rifa (5025201191)
Maisan Auliya (5025201137)
```

## Pembagian Subnet
Hal pertama yang kami lakukan adalah dengan menentukan subnet yang ada pada topologi. Dikarenakan metode yang dipakai adalah VLSM. Kami melingkari tiap host yang terhubung pada interface router dan menghitung IP yang dibutuhkan. Berikut adalah gambaran pembagian subnetnya

## Jumlah IP
Setelah melakukan pembagian subnet kita melakukan penjumlahan pada IP, sehingga didapatkan hasil penjumlahan ip berikut :

## VSLM-Tree
Setelah mendapatkan penjumlahan IP kita membuat tree yang terdapat pada topologi. Pada subnet memiliki NID 10.4.0.0 dengan netmask /20 sehingga pembagian IP berdasarkan NID dan Netmask yang di dapat.
![Alt text](/imgs/VLSM_Tree.png)


Pada VLSM ini diturunkan sesuai dengan netmask atasnya sehingga ketika /20 akan diturunkan menjadi /21, lakukan secara berulang-ulang sampai node semua terpenuhi.

## Pembagian IP
Kemudian kita bagi dengan tetap menggunakan IP perfix 10.4 . hasil pembagian seperti berikut :

## Config VSLM
Menambah Ethernet / Port

Karena default hanya memiliki 2 port ethernet, maka kita bisa menambah port pada tab physical

## Config IP pada Node
Contoh pada The Minister, kita menambahkan IP dan Subnet Mask sesuai dengan pembagian yang telah dilakukan, dengan IP ditambah 1 dari subnetnya. dan jangan lupa untuk di on kan pada port nya.

Pada server & Client ditambahkan juga gateway yang mengarah ke router terdekat.

Lakukan berulang-ulang pada semua node.

## Routing
Pada routing berikut adalah config yang berada pada router. Untuk langkah nya bisa masuk kedalam router, lalu menekan menu static dan menambahkan data yang diinginkan.

## The Reference
- 10.4.0.4/30 via 10.4.0.10
- 10.4.0.64/26 via 10.4.0.10
- 10.4.8.0/22 via 10.4.0.10
- 10.4.0.0/30 via 10.4.0.10
- 10.4.2.0/24 via 10.4.0.10
- 10.4.0.24/30 via 10.4.0.26
- 10.4.6.0/23 via 10.4.0.26
- 10.4.0.16/30 via 10.4.0.18
- 10.4.0.128/30 via 10.4.0.18
- 10.4.0.20/30 via 10.4.0.18
- 10.4.1.128/25 via 10.4.0.18
- 10.4.1.0/25 via 10.4.0.18
- 10.4.0.12/30 via 10.4.0.18
- 10.4.4.0/23 via 10.4.0.18
- 10.4.3.0/24 via 10.4.0.18
- 10.4.0.28/30 via 10.4.0.18

Pada The Reference merupakan pusat Router jadi semua IP dari subnet diasiggn ke Router The Reference agar semua bisa terhubung.

## The Order

- 0.0.0.0/0 via 10.4.0.9
- 10.4.8.0/22 via 10.4.0.6
- 10.4.0.0/30 via 10.4.0.6
- 10.4.2.0/24 via 10.4.0.6 

## The Minister

- 0.0.0.0/0 via 10.4.0.5
- 10.4.2.0/24 via 10.4.0.2

## The Daundless
- 0.0.0.0/0 via 10.4.0.1

0.0.0.0 berarti mengambil semua pesan dan diarahkan ke next hop.

## The Magical
- 0.0.0.0/0 via 10.4.0.25

## The Instrument
- 0.0.0.0/0 via 10.4.0.17
- 10.4.0.20/30 via 10.4.0.22
- 10.4.1.128/25 via 10.4.0.22
- 10.4.1.0/25 via 10.4.0.22
- 10.4.0.12/30 via 10.4.0.14
- 10.4.3.0/24 via 10.4.0.14
- 10.4.4.0/23 via 10.4.0.14
- 10.4.0.28/30 via 10.4.0.14

## The Profound
- 0.0.0.0/0 via 10.4.0.21

## The Firefist
- 0.0.0.0/0 via 10.4.0.13
- 10.4.0.28/30 via 10.4.3.3

## The Queen
- 0.0.0.0/0 via 10.4.3.1

## Testing
Hasil dari message tiap node.

# CIDR - GNS3
Penggabungan Subnet

Kita melakukan penggabungan subnet-subnet paling bawah dalam topologi yaitu dimulai dari subnet yang paling jauh dengan cloud/nat hingga hanya memiliki 1 subnet (induk).

Kondisi Awal

## Penggabungan Pertama (Subnet B)
  1. Subnet A2 dan A3 menghasilkan B1 dengan netmask /23 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /24 dari A3.
  2. Subnet A13 dan A14 menghasilkan B2 dengan netmask /23 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /24 dari A13.

## Penggabungan Kedua (Subnet C)
  1. Subnet A1 dan B1 menghasilkan C1 dengan netmask /21 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /22 dari A1.
  2. Subnet A12 dan B2 menghasilkan C2 dengan netmask /22 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /23 dari A12.
  3. Subnet A9 dan A10 menghasilkan C3 dengan netmask /24 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /25 dari A9.

## Penggabungan Ketiga (Subnet D)
  1. Subnet C1 dan A4 menghasilkan D1 dengan netmask /20 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /21 dari C1.
  2. Subnet A11 dan C2 menghasilkan D2 dengan netmask /21 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /22 dari C2.
  3. Subnet A8 dan C3 menghasilkan D3 dengan netmask /23 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /24 dari C3.

## Penggabungan Keempat (Subnet E)
  1. Subnet D1 dan A5 menghasilkan E1 dengan netmask /19 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /20 dari D1.
  2. Subnet D2 dan A15 menghasilkan E2 dengan netmask /20 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /21 dari D2.

## Penggabungan Kelima (Subnet F)
  1. Subnet D3 dan E2 menghasilkan F1 dengan netmask /19 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /20 dari E2.

## Penggabungan Keenam (Subnet G)
  1. Subnet E1 dan A6 menghasilkan G1 dengan netmask /18 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /19 dari E1.
  2. Subnet A7 dan F1 menghasilkan G2 dengan netmask /18 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /19 dari F1.
  3. Subnet A17 dan A18 menghasilkan G3 dengan netmask /22 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /23 dari A18.

## Penggabungan Ketujuh (Subnet H)
  1. Subnet A16 dan G3 menghasilkan H1 dengan netmask /21 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /22 dari G3.

## Penggabungan Kedelapan (Subnet I)
  1. Subnet G2 dan H1 menghasilkan I1 dengan netmask /17 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /18 dari G2.

## Penggabungan Kesembilan (Subnet J)
  1. Subnet G1 dan I1 menghasilkan J1 dengan netmask /16 yaitu satu tingkat dari netmask terbesar yang diambil yaitu /17 dari I1.

## CIDR-Tree

Setelah mendapatkan penggabungan subnet, kita membuat tree yang terdapat pada topologi. Pada paling atas (parent) memiliki subnet dengan NID 10.4.0.0 dengan netmask /16.

## Pembagian IP

Kemudian kita bagi dengan tetap menggunakan ip perfix 10.4. Hasil pembagian seperti berikut :

## Eth Configuration

Pada masing-masing node akan dilakukan network configuration, kita melakukan assignment dengan IP yang telah ditetapkan sesuai dengan subnet

## The Reference

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.4.68.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 10.4.66.1
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 10.4.32.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 10.4.160.1
netmask 255.255.255.252
```

## The Order

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.160.2
netmask 255.255.255.252
gateway 10.4.160.1

auto eth1
iface eth1 inet static
address 10.4.136.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 10.4.144.1
netmask 255.255.255.192
```

## Ashaf

```auto eth0
iface eth0 inet static
address 10.4.144.2
netmask 255.255.255.192
gateway 10.4.144.1 
```

## The Minister

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.136.2
netmask 255.255.255.252
gateway 10.4.136.1

auto eth1
iface eth1 inet static
address 10.4.133.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 10.4.128.1
netmask 255.255.252.0
```

## Guidessu

```auto eth0
iface eth0 inet static
address 10.4.128.2
netmask 255.255.252.0
gateway 10.4.128.1
```
## The Daundless

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.133.2
netmask 255.255.255.252
gateway 10.4.133.1

auto eth1
iface eth1 inet static
address 10.4.132.1
netmask 255.255.255.0
```

## Phanora

```auto eth0
iface eth0 inet static
address 10.4.132.2
netmask 255.255.255.0
gateway 10.4.132.1
```

## Johan

```auto eth0
iface eth0 inet static
address 10.4.132.3
netmask 255.255.255.0
gateway 10.4.132.1
```

## The Beast

```auto eth0
iface eth0 inet static
address 10.4.68.2
netmask 255.255.255.252
gateway 10.4.68.1
```

## The Magical

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.66.2
netmask 255.255.255.252
gateway 10.4.66.1

auto eth1
iface eth1 inet static
address 10.4.64.1
netmask 255.255.254.0
```

## Haines

```auto eth0
iface eth0 inet static
address 10.4.64.2
netmask 255.255.254.0
gateway 10.4.64.1
```

## Corvekt

```auto eth0
iface eth0 inet static
address 10.4.64.3
netmask 255.255.254.0
gateway 10.4.64.1
```

## The Instrument

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.32.2
netmask 255.255.255.252
gateway 10.4.32.1

auto eth1
iface eth1 inet static
address 10.4.17.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 10.4.4.1
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 10.4.8.1
netmask 255.255.255.128
```

## Matt Cugat

```auto eth0
iface eth0 inet static
address 10.4.8.2
netmask 255.255.255.128
gateway 10.4.8.1
```

## The Profound

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.17.2
netmask 255.255.255.252
gateway 10.4.17.1

auto eth1
iface eth1 inet static
address 10.4.16.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 10.4.16.129
netmask 255.255.255.128
```

## Spendrow

```auto eth0
iface eth0 inet static
address 10.4.16.2
netmask 255.255.255.128
gateway 10.4.16.1
```

## Helga

```auto eth0
iface eth0 inet static
address 10.4.16.130
netmask 255.255.255.128
gateway 10.4.16.129
```

## The Firefist

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.4.2
netmask 255.255.255.252
gateway 10.4.4.1

auto eth1
iface eth1 inet static
address 10.4.2.1
netmask 255.255.254.0

auto eth2
iface eth2 inet static
address 10.4.0.1
netmask 255.255.255.0
```

## Oakleave

```auto eth0
iface eth0 inet static
address 10.4.2.2
netmask 255.255.254.0
gateway 10.4.2.1
```

## Keith

```auto eth0
iface eth0 inet static
address 10.4.0.3
netmask 255.255.255.0
gateway 10.4.0.1
```

## The Queen

```auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.4.0.2
netmask 255.255.255.0
gateway 10.4.0.1

auto eth1
iface eth1 inet static
address 10.4.1.1
netmask 255.255.255.252
```

## The Witch

```auto eth0
iface eth0 inet static
address 10.4.1.2
netmask 255.255.255.252
gateway 10.4.1.1
```

## Routing
Setelah itu akan dilakukan routing pada GNS3 agar semua router, server, dan client akan saling terhubung.

## The Reference

``` route add -net 10.4.144.0 netmask 255.255.255.192 gw 10.4.160.2
route add -net 10.4.136.0 netmask 255.255.255.252 gw 10.4.160.2
route add -net 10.4.128.0 netmask 255.255.252.0 gw 10.4.160.2
route add -net 10.4.133.0 netmask 255.255.255.252 gw 10.4.160.2
route add -net 10.4.132.0 netmask 255.255.255.0 gw 10.4.160.2

route add -net 10.4.64.0 netmask 255.255.254.0 gw 10.4.66.2

route add -net 10.4.8.0 netmask 255.255.255.128 gw 10.4.32.2
route add -net 10.4.17.0 netmask 255.255.255.252 gw 10.4.32.2
route add -net 10.4.16.0 netmask 255.255.255.128 gw 10.4.32.2
route add -net 10.4.16.128 netmask 255.255.255.128 gw 10.4.32.2
route add -net 10.4.4.0 netmask 255.255.255.252 gw 10.4.32.2
route add -net 10.4.2.0 netmask 255.255.254.0 gw 10.4.32.2
route add -net 10.4.0.0 netmask 255.255.255.0 gw 10.4.32.2
route add -net 10.4.1.0 netmask 255.255.255.252 gw 10.4.32.2
```

## The Order

```route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.160.1

route add -net 10.4.128.0 netmask 255.255.252.0 gw 10.4.136.2
route add -net 10.4.133.0 netmask 255.255.255.252 gw 10.4.136.2
route add -net 10.4.132.0 netmask 255.255.255.0 gw 10.4.136.2
```

## The Minister

```route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.136.1

route add -net 10.4.132.0 netmask 255.255.255.0 gw 10.4.133.2
```
## The Daundless

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.133.1
```
## The Magical

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.66.1
```
## The Instrument

```route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.32.1

route add -net 10.4.16.0 netmask 255.255.255.128 gw 10.4.17.2
route add -net 10.4.16.128 netmask 255.255.255.128 gw 10.4.17.2

route add -net 10.4.2.0 netmask 255.255.254.0 gw 10.4.4.2
route add -net 10.4.0.0 netmask 255.255.255.0 gw 10.4.4.2
route add -net 10.4.1.0 netmask 255.255.255.252 gw 10.4.4.2
```

## The Profound

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.17.1
```

## The Firefist

```route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.4.1

route add -net 10.4.1.0 netmask 255.255.255.252 gw 10.4.0.2
```

## The Queen

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.4.0.1
```

