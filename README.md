<p align="center">
  <img src="https://i.imgur.com/PJxYRgW.png" width="200" height="200" />
</p>

<p align="center">
  <img src="https://github.com/e-corp-sam-sepiol/Documentation/blob/master/images/vertcoin-branding.png" width="343" height="68" /> <img src="https://i.imgur.com/1RKi4wd.png" width="90">
</p>

## [Vertcoin.org](https://vertcoin.org/)
## [Vertcoin Node Scanner](https://scanner.vertcoin.org/nodes)
## [`lit` `lit-af` /mit-dci/lit](https://github.com/mit-dci/lit)

------------

# Vertnode 
## An automated solution for installing Vertcoin node(s) on Single Board Computers and `amd64` compatible hardware

**`NOTE:` The steps provided below produce a “headless” server... meaning we will not be using a GUI to configure Vertcoin or check to see how things are running. In fact, once the server is set up, you will only interact with it using command line calls over `SSH`. The idea is to have this full node be simple, low-power, with optimized memory usage and something that “just runs” in your basement, closet, etc.**

### Functioning Status
- [x] `Working` **Raspberry Pi 3 B+** | ARM Cortex-A53 1.4GHz | 1GB SRAM | 
- [x] `Working` **Raspberry Pi Zero (W)** | Single Core ARMv6 1 Ghz | 433MB RAM |
- [x] `Working` **Intel NUC** | Dual-Core 2.16 GHz Intel Celeron | 8GB DDR3 RAM |
- [x] `Working` **Rock64 Media Board** | Quad-Core ARM Cortex A53 64-Bit CPU | 4GB LPDDR3 RAM | 
- [x] `Working` **Orange Pi One** | H3 Quad-core Cortex-A7 1.2 GHz | 512MB RAM |
- [x] `Working` **`lit` & `lit-af`**

### **`Optional lit & lit-af Installation`**<img src="https://i.imgur.com/c6GEfJS.png" width="30" height="30" />
### **`Optional P2Pool Installation`**
### **`USB flash drive required: 8GB >`**
## [`lit` `lit-af` Vertnode Documentation](https://github.com/e-corp-sam-sepiol/vertnode/blob/master/docs/lit.md)


### Supported
- [x] **Raspberry Pi | [Raspbian Stretch Lite](https://downloads.raspberrypi.org/raspbian_lite_latest/)**
- [x] **Raspberry Pi Zero / Wireless | [Raspbian Stretch Lite](https://downloads.raspberrypi.org/raspbian_lite_latest)** 
- [x] **Rock64 Media Board | [Debian Stretch Minimal](https://github.com/ayufan-rock64/linux-build/releases/download/0.6.15/stretch-minimal-rock64-0.6.15-175-arm64.img.xz)**
- [x] **Intel NUC | [Ubuntu Server 16.04](http://releases.ubuntu.com/16.04/ubuntu-16.04.4-server-amd64.iso)**
- [x] **Orange Pi One | [Armbian Stretch](https://dl.armbian.com/orangepione/Debian_stretch_next.7z) | [Getting Started](https://docs.armbian.com/User-Guide_Getting-Started/) |** `login` root `pass` 1234

**`RECOMMENDED:`** When you first boot your Raspberry Pi, Rock64 Media Board, Intel NUC, Orange Pi One or `amd64` compatible hardware running Debian / Ubuntu ensure that you insert a USB flash drive and...
```
sudo apt-get update ; sudo apt-get upgrade -y ; sudo apt-get install git -y ; sudo reboot
``` 
**and `ssh` back into your system before running the `install-vertnode.sh` script.**
```
git clone https://github.com/e-corp-sam-sepiol/vertnode.git
cd vertnode/
chmod +x install-vertnode.sh
./install-vertnode.sh 
```

---------------

### TO-DO Checklist
- [x] add support for Orange Pi One single board computer
- [ ] adjust swap file size based on RAM 
- [ ] address option of installing p2pool on raspberry pi zero (currently possible, not recommended)
- [ ] expand support for x86_64 Debian / Ubuntu virtual machine, add option for USB flash drive
- [x] fix `go` errors when fetching `go version`
- [ ] add `md5` hash checksum to `vertcoind` and `golang` downloads
- [x] force compiling from souce on raspberry pi zero
- [ ] add TOR network option
- [x] fix libdb_cxx.so missing directory error when running vertcoin after compiling from source

---------------

### FAQ

#### Why a Vertcoin Full node?
Vertcoin is a digital currency supported by a peer-to-peer network. In order to run efficiently and effectively, it needs peers run by different people... and the more the better.

#### Why a Raspberry Pi?
Raspberry Pi is an inexpensive computing hardware platform that generates little heat, draws little power, and can run silently 24 hours a day without having to think about it.

#### Why a Orange Pi One?
Orange Pi One is inexpensive computing hardware that generates little heat, draws little power, and can run silently 24 hours a day without having to think about it.

#### Why a Rock64 Media Board?
ROCK64 is a credit card size 4K60P HDR10 Media Board Computer powered by Rockchip RK3328 Quad-Core ARM Cortex A53 64-Bit Processor and support up to 4GB 1600MHz LPDDR3 memory. The Rock64 Media Board is an inexpensive computing hardware platform that generates little heat, draws little power, and can run silently 24 hours a day without having to think about it. The Rock64 Media Board costs a little bit more than the Raspberry Pi 3, but provides better hardware and significantly more memory. 

#### Why use an Intel NUC?
Intel NUC is the next significant step up in computing hardware in comparison to a Raspberry Pi and the Rock64 Media Board. The NUC generates little heat, draws little more power than the Raspberry Pi, with significantly better hardware and can run silently 24 hours a day without having to think about it. 

Intel’s Next Unit of Computing (NUC) models are well equipped for light- to medium-duty server use in a home. Much more robust than their ARM-based Raspberry Pi counterparts, Intel’s NUCs will consume more power but be able to handle more computationally intensive tasks. Some NUC models will have room for a 2.5-inch SSD for onboard storage.

#### What if I don't have an Intel NUC?
The Intel NUC was chosen because of it's entry level hardware, and the wide distribution of hardware with similar capability to the Intel NUC existing in the world today. If you do not have an Intel NUC don't worry, if your CPU supports `amd64` architecture, has 2GB or more of `RAM` and 16GB+ of hard drive space the steps performed below apply when using Ubuntu 16.04. The headless server edition is recommended, a GUI is not needed to run a Vertcoin Core full node. 

#### What is a Full Node?

Vertcoin’s peer-to-peer network is composed of network "nodes," run mostly by volunteers. Those running vertcoin nodes have a direct and authoritative view of the vertcoin blockchain, with a local copy of all the transactions, independently validated by their own system and can initiate transactions directly on the vertcoin network. 

By running a node, you don’t have to rely on any third party to validate a transaction. Moreover, **by running a vertcoin node you contribute to the vertcoin network by making it more robust**. A full-node client consumes substantial computer resources (e.g., more than `4 GB` of disk, `~1 GB` of `RAM` at most) but offers complete autonomy and independent transaction verification.

**Running a node, however, requires a permanently connected system with enough resources to process all vertcoin transactions.** Vertcoin nodes also transmit and receive vertcoin transactions and blocks, consuming internet bandwidth. If your internet connection is limited, has a low data cap, or is metered (charged by the gigabit), you should probably not run a vertcoin node on it, or run it in a way that limits its bandwidth usage.

Despite these resource requirements, hundreds of volunteers run vertcoin nodes. **Some are running on systems as simple as a [Raspberry Pi](https://www.canakit.com/raspberry-pi-3-model-b-plus.html) (a $35 USD computer the size of a pack of cards)**. Many volunteers also run vertcoin nodes on rented servers, usually some variant of Linux. A Virtual Private Server (VPS) or Cloud Computing Server instance can be used to run a vertcoin node. Such servers can be rented for $25 to $50 USD per month from a variety of providers.

#### Why run a headless node on a Single Board Computer?

1. You want to support vertcoin. Running a node makes the network more robust and able to serve more wallets, more users, and more transactions. 
2. You are building or using applications such as mining that must validate transactions according to vertcoin’s consensus rules.
3. You are developing vertcoin software and need to rely on a vertcoin node for programmable (API) access to the network and blockchain.

**The idea is to have this full node be simple, low-power, with optimized memory usage and something that “just runs” in your basement, closet, etc.**

---------------

### How to install Raspbian
**`Download Raspbian Stretch Lite`**
`https://www.raspberrypi.org/downloads/raspbian/`  

We will utilize the software 'Win32 Disk Imager' to format and install Raspbian on the MicroSD card. Please follow the [guide](https://www.raspberrypi.org/documentation/installation/installing-images/windows.md) below for details on installing the Rasbian image to the MicroSD card.

If you are using Linux please use [Etcher](https://etcher.io/)

![Write](https://i.imgur.com/fTyqpat.png)  
![Writing...](https://i.imgur.com/DrGi0mb.png)  
![Done](https://i.imgur.com/cfUjvKR.png)

Once Win32 Disk Imager is finished writing to the MicroSD card please access the 'boot' partition of the MicroSD card with Windows Explorer `Win+E`. Create a new empty text file named `ssh` like so...

![MicroSD card - ssh](https://i.imgur.com/m14rGdV.png)  
This enables `SSH` access on the Raspberry Pi's first boot sequence. 

### How to enable wireless connection on boot if hard wiring is not available

Create another new text file named `wpa_supplicant.conf` that will hold the network info...

Edit the file that you just created adjusting for the name of your country code, network name and network password.

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="NETWORK-NAME"
    psk="NETWORK-PASSWORD"
}
```
Please safely remove the USB Card Reader / MicroSD card as to ensure the data is not corrupted.

Insert the MicroSD card that was safely removed into the microSD slot the Raspberry Pi. Once the Pi has booted it will attempt to join the wireless network using the information provided in the `wpa_supplicant.conf` file.

------------

## Testing Errors

- [x] **Configuring firewall | Fixed with: `sudo reboot` then re-run `install_vertnode.sh`**

**`RECOMMENDED:` When you first boot your Raspberry Pi ensure that you `sudo apt-get update ; sudo apt-get upgrade -y ; sudo reboot` and `ssh` back into the Raspberry Pi before running the `install-vertnode.sh` script.**

**This error occurs when `sudo apt-get upgrade` installs a new kernel to the Raspberry Pi, it affects `iptables` which is a part of the kernel. Updating the kernel requires a reboot.**
```
ERROR: initcaps
[Errno 2] iptables v1.6.0: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

------------

### [Manual Installation Walkthrough: Raspberry Pi 3](https://github.com/vertcoin-project/VertDocs/blob/master/docs/FullNodes/raspberry-pi.md)
### [Manual Installation Walkthrough: Raspberry Pi Zero W](https://github.com/vertcoin-project/VertDocs/blob/master/docs/FullNodes/raspberry-pi-zero-w.md)
### [Manual Installation Walkthrough: Intel NUC](https://github.com/vertcoin-project/VertDocs/blob/master/docs/FullNodes/intel-nuc.md)

------------

### Shopping List
|                                                              Name                                                             |        Price        |                                         URL                                        |
|:-----------------------------------------------------------------------------------------------------------------------------:|:-------------------:|:----------------------------------------------------------------------------------:|
|                                                         Raspberry Pi                                                          | -------             | ----------------------------------                                                 |
| CanaKit Raspberry Pi 3 with 2.5A Micro USB Power Supply                                                                       | $42-$45 USD         | https://www.amazon.com/CanaKit-Raspberry-Micro-Supply-Listed/dp/B01C6FFNY4/        |
|                                                                                         C4 Labs Zebra Case - Raspberry Pi 3B+ | $14.95 USD          | https://www.amazon.com/C4-Labs-Zebra-Case-Raspberry/dp/B00M6G9YBM/                 |
| CanaKit Raspberry Pi Zero W (Wireless) Complete Starter Kit - 16 GB                                                           | $32.99 USD          | https://www.amazon.com/CanaKit-Raspberry-Wireless-Complete-Starter/dp/B072N3X39J/  |
|                                                                      Zebra Zero Heatsink Case Black Ice for Raspberry Pi Zero | $6.95 USD           | https://www.amazon.com/Zebra-Heatsink-Raspberry-Wireless-C4Labs/dp/B01HP636I4/     |
|                                                Pine64 Rock64 Media Board 1-4GB                                                | $24.95 - $44.95 USD | https://www.pine64.org/?product=rock64-media-board-computer                        |
|                                               Orange Pi One Project Board ARMv7                                               | $19.99 USD          | https://www.amazon.com/Orange-Pi-One-Project-Board/dp/B01CD48E94/                  |
| LoveRPi 8" MicroUSB to 4.0mm x 1.7mm Barrel Plug Adapter with Click Button Power Switch for Banana Pi M2 and Orange Pi Boards | $5.99 USD           | https://www.amazon.com/LoveRPi-MicroUSB-Barrel-Adapter-Button/dp/B01CMZVQQ2/       |
|                                                          LoveRPi 2.5A 4.0mm x 1.7mm Barrel Plug Power Supply Adapter Charger  | ~7.00 USD           | https://www.amazon.com/LoveRPi-Barrel-Supply-Adapter-Charger/dp/B01CMZ96EG/        |
|                                                 Sandisk Ultra 16GB Micro SDHC                                                 | $8.17 USD           | https://www.amazon.com/Sandisk-Ultra-Micro-UHS-I-Adapter/dp/B073K14CVB/            |
|                                           Kingston Digital DataTraveler 16GB USB 2.0                                          | $5.99 USD           | https://www.amazon.com/Kingston-Digital-DataTraveler-DTSE9H-16GBZ/dp/B006W8U2WU/   |
|                                                           Intel NUC                                                           | -------             | NOTE the memory type the Intel NUC takes, DDR3 or DDR4 and purchase accordingly    |
|                                                                                                            Intel NUC NUC5CPYH | $115.13 USD         | https://www.amazon.com/Intel-NUC5CPYH-Graphics-2-5-Inch-BOXNUC5CPYH/dp/B00XPVRR5M/ |
|                                                                                                         Intel NUC BOXNUC6CAYH | $127.02 USD         | https://www.amazon.com/dp/B01MSZTD8N/                                              |
|                                                                                                   Intel NUC 7 Pentium Mini PC |  $169.99 USD        | https://www.amazon.com/Intel-NUC7-Pentium-Mini-BOXNUC7PJYH1/dp/B07C9GF256/         |
|                                                                                                       Crucial 4GB Single DDR4 | $40.25 USD          | https://www.amazon.com/Crucial-PC4-19200-Unbuffered-SODIMM-260-Pin/dp/B019FRDKWI/  |
|                                                                                                       Crucial 4GB Single DDR3 | $37.48 USD          | https://www.amazon.com/dp/B009RBN6I6/                                              |
|                                                                                                        SanDisk SSD PLUS 120GB | $44.95 USD          | https://www.amazon.com/dp/B01F9G414U/                                              |

------------------------

![NodeMap](https://i.imgur.com/rzj5SU2.png)
## [Vertcoin Node Scanner](https://scanner.vertcoin.org/nodes)

<p align="center">
  <img src="https://i.imgur.com/TKEVSFv.png">
</p>

<p align="center">
  <img src="https://images-na.ssl-images-amazon.com/images/I/91AAiPdhwxL._SL1500_.jpg">
</p>

<p align="center">
  <img src="https://cdn.shopify.com/s/files/1/0569/7173/products/Rock64Wood_2_1024x1024.jpg?v=1510970757">
</p>

<p align="center">
  <img src="https://i.imgur.com/zgx4uiu.jpg">
</p>

<p align="center">
  <img src="https://images-na.ssl-images-amazon.com/images/I/61NNweC8vCL._SL1448_.jpg">
</p>

<p align="center">
  <img src="https://i.imgur.com/9T0gKr7.png">
</p>
