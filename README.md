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
### step 5 - discovering service Version vulnerabilities.
we selected one of the identified services and searched for thw version's vulnerabilities: MICROSOFT Windows RPC.
BELOW are the results and mitigation recommendations.
vulnerabilities of microsoft windows RPC , Explaining tge problems in one parts and the solution in another part
ChatGPT said:

Sure! Below is a clear explanation of vulnerabilities in Microsoft Windows RPC (Remote Procedure Call), divided into two parts:

🔐 Part 1: Vulnerabilities of Microsoft Windows RPC
1. Remote Code Execution (RCE)

One of the most severe types of vulnerabilities in Windows RPC is RCE, where attackers can run arbitrary code on a remote system. Notable examples:

CVE-2022-26809: A critical vulnerability in RPC Runtime (RPCSS service) that allowed unauthenticated remote code execution with high privileges.

CVE-2008-4250: Related to MS08-067, this vulnerability allowed remote code execution and was exploited by the Conficker worm.

2. Privilege Escalation

RPC services often run with SYSTEM-level privileges, and misconfigurations or flaws can be exploited to escalate privileges locally.

3. Information Disclosure

Improper handling of memory or access controls can lead to sensitive data being leaked through RPC services.

4. Denial of Service (DoS)

Some vulnerabilities allow attackers to crash the RPC service or cause it to hang, making systems unresponsive. This can be used to disrupt services on a network.

5. Authentication Bypass

In some cases, poor implementation of authentication in RPC endpoints can allow unauthorized users to access or execute RPC calls.

6. Firewall and Exposure Risks

RPC dynamically assigns ports, which makes it hard to securely manage through firewalls. Exposing these services to the internet without proper filtering can be dangerous.

🛡️ Part 2: Solutions and Mitigations
✅ 1. Apply Security Updates

Always install the latest Windows updates and patches from Microsoft, especially those related to RPC (e.g., MS08-067, CVE-2022-26809, etc.).

Enable automatic updates or use enterprise patch management tools.

✅ 2. Limit RPC Exposure

Restrict access to RPC services to trusted IP ranges only using Windows Firewall or external firewalls.

Avoid exposing RPC services to the public internet unless absolutely necessary.

✅ 3. Use Network Segmentation

Place sensitive systems behind segmented networks with restricted access.

Use VLANs or subnets to separate internal services from user-facing ones.

✅ 4. Enable Strong Authentication

Enforce NTLMv2 or Kerberos for RPC communication.

Disable anonymous access where not needed.

✅ 5. Monitor and Log RPC Activity

Use tools like Windows Event Viewer, Sysmon, or SIEMs to log and monitor RPC activity.

Look for suspicious RPC requests, especially from external or unauthorized sources.

✅ 6. Configure Firewalls to Control Dynamic RPC Ports

RPC uses dynamic ports by default (typically 49152–65535 on modern systems).

Restrict this range to a smaller set using the registry (HKLM\Software\Microsoft\Rpc\Internet) and configure firewalls accordingly.

✅ 7. Use Security Baselines

Apply Microsoft Security Baselines via Group Policy or Microsoft Endpoint Manager.

These harden the system configurations, including RPC settings.
