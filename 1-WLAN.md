# WLAN

## -Introduction-

### Tipe Wireless Network

- WPAN
- WLAN
- WMAN
- WWAN

### Wireless Technology

- Bluetooth: 100m
- WiMax: 50km
- Cellular broadband
  - GSM
  - CDMA
- Satellite

### 802

- 2.4GHz (UHF) only:
  - 802.11
  - 802.11b
  - 802.11g
- 5 GHz (SHF) only:
  - 802.11.a
  - 802.11ac
- Both:
  - 802.11n
  - 802.11ax
  
### Standard Organization

- ITU
- IEEE
- Wi-Fi Alliance

## -WLAN-

### WLAN Component

- Wireless NIC e.g. dongle
- Wireless Home Router

  Serve as:
  - AP, providing wires access
  - Switch, interconnecting wired devices
  - Router, providing a default gateway to other network
- Wireless AP

### AP Categories

- Autonomous:

  Standalone, configured through a CLI or GUI.
- Controller-based/Lightweight AP:

  Use Lightweight Access Point Protocol (LWAPP). Automatically controlled & managed by a WLAN Controller (WLC).

### Wireless Antenna

- Omnidirectional
- Directional
- MIMO

## -WLAN Operation-

### Wireless Topology Modes

- Adhoc: Client peer-to-peer
  ![Adhoc](img\topology-modes-adhoc.png)
- Infrastructure: Connect client to the network through AP
  ![Infrastructure](img\topology-modes-infrastructure.png)
- Tethering: Sharing network/cellular access as a personal hotspot
  ![Tethering](img\topology-modes-tethering.png)

### Topology blocks

- Basic Service Set (BSS): Single AP interconnecting all wireless clients.
