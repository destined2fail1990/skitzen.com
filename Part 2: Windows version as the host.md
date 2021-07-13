# Part 2: Windows Version

I was able to get VMWare up with VNC Server by RealVNC through a free trial. I forgot that VMWare had VNC built in, although it offers no remote access or encryption, which shouldn't matter. However this way I can access them from anywhere.

So far it achieved what I wanted, I eliminated the CTRL + ALT requirement from VMWare and made it easy to switch between. 

# Firewall Setup
I wanted to touch on a little more how I have the firewall set up within my computer. Essentially I am using the virtual networking from VMWare and the Windows Advanced Firewall to ensure all traffic is blocked over the primary adapter, which for me right now is a wireless adapater. Wireless is solid enough now in the AC1000+ range and built into my new motherboard.

---------
                    VM-1
                  /
HOST - Firewall-VM 
      /           \ 
    /               VM-2
HOST
---------

Here is an example of what it looks like coming from the host adapater, which with automatic routing off, ends up with a routing table like:

# Host Routing Table:
===========================================================================
Interface List
  7...2c db 07 -- -- -- ......Intel(R) Dual Band Wireless-AC 3168
 12...2c db 07 -- -- -- ......Microsoft Wi-Fi Direct Virtual Adapter
 20...2e db 07 -- -- -- ......Microsoft Wi-Fi Direct Virtual Adapter #2
 21...00 50 56 -- -- -- ......VMware Virtual Ethernet Adapter for VMnet1
  4...00 50 56 -- -- -- ......VMware Virtual Ethernet Adapter for VMnet8
 17...00 50 56 -- -- -- ......VMware Virtual Ethernet Adapter for VMnet19
  1...........................Software Loopback Interface 1
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     192.168.50.1     192.168.50.3     35
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    331
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    331
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    331
      192.168.1.0    255.255.255.0         On-link       192.168.1.8    259
      192.168.1.8  255.255.255.255         On-link       192.168.1.8    259
    192.168.1.255  255.255.255.255         On-link       192.168.1.8    259
     192.168.50.0    255.255.255.0         On-link      192.168.50.3    291
     192.168.50.3  255.255.255.255         On-link      192.168.50.3    291
   192.168.50.255  255.255.255.255         On-link      192.168.50.3    291
    192.168.136.0    255.255.255.0         On-link     192.168.136.1    291
    192.168.136.1  255.255.255.255         On-link     192.168.136.1    291
  192.168.136.255  255.255.255.255         On-link     192.168.136.1    291
    192.168.164.0    255.255.255.0         On-link     192.168.164.1    291
    192.168.164.1  255.255.255.255         On-link     192.168.164.1    291
  192.168.164.255  255.255.255.255         On-link     192.168.164.1    291
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link     192.168.164.1    291
        224.0.0.0        240.0.0.0         On-link     192.168.136.1    291
        224.0.0.0        240.0.0.0         On-link       192.168.1.8    259
        224.0.0.0        240.0.0.0         On-link      192.168.50.3    291
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    331
  255.255.255.255  255.255.255.255         On-link     192.168.164.1    291
  255.255.255.255  255.255.255.255         On-link     192.168.136.1    291
  255.255.255.255  255.255.255.255         On-link       192.168.1.8    259
  255.255.255.255  255.255.255.255         On-link      192.168.50.3    291
===========================================================================
Persistent Routes:
  None

## VMNet Adapters
- VMNet1 is the default Host Only Adapter and isn't necessary due to the Firewall in place
- VMNet8 is the default NAT Adapter and isn't actively used either.
- VMNet19 is the adapater I am using as the 192.168.50.1/24 network, providing internet to the other devices. DHCP is served via an IPFire Firewall VM.

# VM-1 Routing Table:
===========================================================================
Interface List
  8...00 50 56 -- -- -- ......Intel(R) 82574L Gigabit Network Connection
  9...2c db 07 -- -- -- ......Bluetooth Device (Personal Area Network)
  1...........................Software Loopback Interface 1
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     192.168.50.1     192.168.50.2     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    331
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    331
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    331
     192.168.50.0    255.255.255.0         On-link      192.168.50.2    281
     192.168.50.2  255.255.255.255         On-link      192.168.50.2    281
   192.168.50.255  255.255.255.255         On-link      192.168.50.2    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    331
        224.0.0.0        240.0.0.0         On-link      192.168.50.2    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    331
  255.255.255.255  255.255.255.255         On-link      192.168.50.2    281
===========================================================================
Persistent Routes:
  None
