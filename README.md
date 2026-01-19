# SOC Home Lab Report – Basic Nmap Scan

## 1. Objective

The objective of this lab was to simulate external network reconnaissance against a Windows system and analyze the resulting security events from a SOC (Security Operations Center) perspective.

---

## 2. Lab Environment

**Attacker Machine**

* OS: Kali Linux
* Role: External reconnaissance host
* Tools Used: Nmap

**Victim Machine**

* OS: Windows 10
* Role: Target system
* Services Exposed: RPC, NetBIOS, SMB

**Network Configuration**

* VirtualBox Host‑Only Adapter
* Isolated internal lab network

---

## 3. Reconnaissance Activity

An initial nmap scan was performed from Kali Linux to identify open ports and running services on the Windows host.

**Command Used**

```
nmap -sS -sV 192.168.56.105
```

**Scan Results**

* Port 135/tcp – Microsoft RPC
* Port 139/tcp – NetBIOS Session Service
* Port 445/tcp – Microsoft SMB
* OS identified as Microsoft Windows

This confirms that the target system exposes Windows file sharing and remote procedure call services, which are commonly targeted during the reconnaissance phase of an attack.

---

## 4. Windows Security Log Analysis

During the reconnaissance activity, Windows generated several security events associated with system‑level authentication and service access.

### Observations

* No successful or failed user logon events detected
* No attacker IP address recorded, as the scan did not perform authentication
---

## 5. SOC Interpretation

From a SOC analyst perspective:

* The activity represents **early‑stage reconnaissance**
* No indicators of compromise detected
* Would be classified as **low‑severity informational activity**

---

## 6. Conclusion

This lab demonstrated how external reconnaissance can be performed against a Windows system and how Windows records related security events. Understanding this behavior helps SOC analysts distinguish between benign system activity and malicious authentication attempts.

---

## 7. Skills Demonstrated

* Network reconnaissance using Nmap
* TCP SYN and service version scanning
* Windows Event Viewer analysis
* SOC‑style activity interpretation
* Incident documentation
