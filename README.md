# NMAP-Scanning-project
this project is aimed at idenitfying devices in a network, uncovering open ports, and chech for vulnerabilities

### step 1
to scan our devices (host) for open ports, we need to identify its ip address
**procedure**
* start NMAP from the CMD terminal.
* type "ipconfig". this will display all ip addresses, select the interface you are using, in this case, the wireless interface.
  
<img width="614" height="464" alt="image" src="https://github.com/user-attachments/assets/1621190e-790b-4c37-b815-05c1aa59c106" />
 
### step 2
finding your network range
in order to find your network range, all the ip addresses currently connected in the same network (subnet). type nmap -sn 172.20.10.2. since the host ip is 172.20.10.2, then the network is 172.20.10.0/24 
<img width="629" height="141" alt="image" src="https://github.com/user-attachments/assets/1bbff57d-c180-480d-9b6a-751ed46fd46a" />
### step 3 - scan for open ports
this involve identifying open ports on the host machine that can lead to an attack or security breach.
**procudure**
* select any of the ip addresses in the network.
* use this nmap command to identify open ports (nmap < hostipaddress>).
  <img width="525" height="103" alt="image" src="https://github.com/user-attachments/assets/47286968-cdf0-49f8-a672-686d1aff3c3a" />
### step 4 - Identify services
this step involve identifying service on the machine (target).
To achieve this with nmap, we used the following command: nmap -sV <Targetipadress> 
<img width="786" height="232" alt="image" src="https://github.com/user-attachments/assets/afc788ea-ad41-4684-a4e3-919a5d3ff050" />
