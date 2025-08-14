# NMAP-Scanning-project
this project is aimed at idenitfying devices in a network, uncovering open ports, and chech for vulnerabilities

### step 1
to scan our devices (host) for open ports, we need to identify its ip address
**procedure**
* start NMAP from the CMD terminal.
* type "ipconfig". this will display all ip addresses, select the interface you are using, in this case, the wireless interface.
  
<img width="614" height="464" alt="image" src="https://github.com/user-attachments/assets/1621190e-790b-4c37-b815-05c1aa59c106" />
 
---
### step 2
finding your network range
in order to find your network range, all the ip addresses currently connected in the same network (subnet). type nmap -sn 172.20.10.2. since the host ip is 172.20.10.2, then the network is 172.20.10.0/24 
<img width="629" height="141" alt="image" src="https://github.com/user-attachments/assets/1bbff57d-c180-480d-9b6a-751ed46fd46a" />

---
### step 3 - scan for open ports
this involve identifying open ports on the host machine that can lead to an attack or security breach.
**procudure**
* select any of the ip addresses in the network.
* use this nmap command to identify open ports (nmap < hostipaddress>).
  <img width="525" height="103" alt="image" src="https://github.com/user-attachments/assets/47286968-cdf0-49f8-a672-686d1aff3c3a" />

---

### step 4 - Identify services
this step involve identifying service on the machine (target).
To achieve this with nmap, we used the following command: nmap -sV <Targetipadress> 
<img width="786" height="232" alt="image" src="https://github.com/user-attachments/assets/afc788ea-ad41-4684-a4e3-919a5d3ff050" />

### step 5 - discovering service Version vulnerabilities.
we selected one of the identified services and searched for thw version's vulnerabilities: MICROSOFT Windows RPC.
BELOW are the results and mitigation recommendations.

<img width="811" height="246" alt="image" src="https://github.com/user-attachments/assets/d9122780-fbec-478a-a6f7-1086401ed716" />

**Problem Summary:**
Microsoft Windows Remote Procedure Call (RPC) is a core system component used for inter-process communication across the network. However, it has been a frequent target for attackers due to:

1. Remote Code Execution (RCE) vulnerabilities, allowing attackers to run malicious code remotely (e.g., CVE-2022-26809).
2. Privilege escalation due to RPC services running with high privileges.
3. Denial of Service (DoS) attacks that crash or freeze systems.
4. Information disclosure through poor access control or memory handling.
5. Authentication bypass, leading to unauthorized access.
6. High exposure risk, as RPC often uses dynamic ports and is hard to secure via firewalls.
7. These vulnerabilities can lead to full system compromise, especially when RPC services are exposed to untrusted networks.

**Effective Solutions:**
1. Apply Security Patches Regularly
- Keep Windows systems up to date with the latest patches, especially those targeting RPC vulnerabilities.
2. Restrict RPC Access
- Limit RPC communication to trusted IP addresses only; block public internet access.
3. Use Firewalls and Port Restrictions
- Configure firewalls to control or limit RPC’s dynamic port range.
4. Enforce Strong Authentication
- Require NTLMv2 or Kerberos; disable anonymous RPC access.
5. Network Segmentation
- Isolate sensitive systems using subnets or VLANs to minimize lateral movement.
6. Monitor RPC Activity
- Use logging and threat detection tools to monitor and analyze suspicious RPC behavior.
7. Apply Security Baselines
- Use Microsoft-recommended security baselines to harden RPC-related settings.
