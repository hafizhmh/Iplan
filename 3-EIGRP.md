# EIGRP

## _Fundamentals_

### Introduction

- EIGRP = Enhanced Interior Gateway Routing protocol
- Distance vector routing protocol
- IGRP derivative, support VLSM and higher speed interfaces.
- Feature: unequal-cost load balancing, up to 255 hops, rapid confergencs.
- Use Diffusing Update Algorithm (DUAL) to identify network paths for fast convergence.

### AS

- AS represents a common routing domain.
- Router in the same AS use same metric calculation formula.
- Router exchange routes only with members in the same AS.

### Terminology

- Successor route  
  Route with the lowest path metric
- Successor  
  First next-hop router for the successor route
- Feasible distance (FD)  
  Metric for the lowest-metric path
- Reported distance (RD)  
  Distance reported by a router to reach a prefix
- Feasible successor  
  A route that satisfies feasibility condition. Maintained as a backup route. Ensure the backup is loop-free.
- Feasibility condition  
  Received RD must be less than FD

### Topology table

EIGRP contains topology table, differ from true distance vector protocols.  
Entry:

- Network Prefix
- Neighbors that advertise the network
- FD, RD, and hop counts
- Value for metric calculation:
  - Load
  - Reliability
  - Total delay
  - Minimum bandwidth
- Feasible successor

### EIGRP Neigbors

- **NOT** relying on periodic advertisement
- Exchanging routing table when forming adjacency
- Advertise incemental updates only when topology changes occur.

### Inter-Router Communication

- Port: IP/88
- Multicast if possible, unicast whan necessary
- Multicast group address 224.0.0.10 /  MAC address 01:00:5e:00:00:0a
- Packet:
  | Type | Name | Function |
  | --- | --- | --- |
  | 1 | Hello | EIGRP neighbors discovery, health check |
  | 2 | Request | Get specific information from neighbor(s) |
  | 3 | Update | Send routing/reachability information to neighbors |
  | 4 | Query | Sent to search for another path during convergence |
  | 5 | Reply | Response for query |

### Neighbors Formation

- RIB is exchanged between neighbors.
- Formation is attempted after hearing a hello packet
- Parameters must match:
  - K
  - Primary subnet
  - AS number
  - Auth params
- Process:  
  | R1  | R2 |
  | ---: | :--- |
  | Hello -> ||
  || <- Hello |
  |Update, Init Set -> ||
  ||<- ACK|
  |Update, Routes -> ||
  ||<- ACK|
  |Update, End of Table -> ||
  ||<- ACK|

---

## _EIGRP Configuration Modes_

### Classic Mode

- Most of the configurations are in the EIGRP process (global)
- Some of the configurations are in the interface configuration
- Add complexity for deployment and troubleshooting
- Example of individually configured settings:
  - Hello interval
  - Split-horizon
  - Auth
  - Summary route advertisement
- Step:
  - Global config: `router eigrp <as-number>`
  - Interface confige: `network <ip-address> [mask]`

### Named mode

- All configurations in one location
- Supports current and future features
- Supports multiple address families
- Clear scope of commands
- Settings subsections:
  - Address family: relevant information to the global AS operations
    - K
    - Logging setting
    - Stub setting
  - Interface: relevant information to the interface
    - Hello advertisement interval
    - Split horizon
    - Auth
    - Summary route advertisements
    - Can be implemented to a specific interface of default interface. Specifif interface settings take priority.
  - Topology: relevant informations regarding EIGRP topology database and RIB presentation

## Router iD

- Dynamically set (default)
  - Highest IPv4 address of loopback interfaces
  - Highest IPv4 address of active up physical interfaces
- Manually set

## Passice interface

Interfaces that do not send or process hello packet, preventing forming adjacencies.

<!-- TODO:  EIGRP part 2-->
