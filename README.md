<p align="center">
  <a href="https://github.com/Samuel-Cavada" target="_blank">
    <img src="https://img.shields.io/badge/Back_to_Main_Page-000000?style=for-the-badge&logo=github&logoColor=white" alt="Back to Main Page"/>
  </a>
</p>

<h1 align="center">🔐 Microsoft Defender: Endpoint Activity Simulation & Log Hunting</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Cloud Platform" />
  <img src="https://img.shields.io/badge/OS-Windows%2010-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="OS" />
  <img src="https://img.shields.io/badge/Tool-PowerShell-00B388?style=for-the-badge&logo=powershell&logoColor=white" alt="Tool" />
  <img src="https://img.shields.io/badge/Focus-Endpoint%20Detection-orange?style=for-the-badge" alt="Focus Area" />
</p>

---

## 📌 Project Objective
> Simulate endpoint activity on a Windows VM using PowerShell commands, then analyze the resulting logs in Microsoft Defender. This project demonstrates how actions are captured and visualized through Defender’s advanced hunting capabilities.

---

## 🧰 Tools & Technologies
- **Platform:** Azure  
- **OS:** Windows 10  
- **Tools:** Microsoft Defender for Endpoint, PowerShell  
- **Languages/Scripts:** PowerShell, KQL (Kusto Query Language)  

---

## 🧠 Skills Gained / Focus Areas
- ✅ Created and executed PowerShell scripts on a cloud VM  
- ✅ Triggered Defender detections using EICAR and test commands  
- ✅ Queried logs from `DeviceFileEvents`, `DeviceProcessEvents`, and `DeviceNetworkEvents`  
- ✅ Practiced interpreting real-time endpoint activity via KQL  

---

## 🧪 Environment Setup
> Provisioned a Windows 10 Virtual Machine in Microsoft Azure. Onboarded the VM to Microsoft Defender for Endpoint via the Microsoft 365 Defender portal. VM was used to simulate benign and suspicious endpoint actions for detection testing.

![Environment Setup](assets/images/setup.jpg)

---

## 🛠️ Walkthrough

### ✅ Step 1: Create Virtual Machine
> Deployed a Windows 10 VM in Azure and confirmed it was reporting to Microsoft Defender for Endpoint.

![Step 1](assets/images/step1.jpg)

---

### ✅ Step 2: Simulate Endpoint Activity
> Ran a series of PowerShell commands to simulate user and malicious behavior.

```powershell
# Create and delete a file
New-Item hi.txt
Remove-Item hi.txt

# Test outbound network connectivity
Test-NetConnection -ComputerName 8.8.8.8 -Port 443
Test-NetConnection -ComputerName 8.8.8.8 -Port 69
Test-NetConnection 10.0.0.4

```

# Simulate malware detection using the EICAR test string
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' >> big-malware.exe


### ✅ Step 2: Simulate Endpoint Activity
> This step simulates real-world endpoint actions using PowerShell to generate detectable events in Microsoft Defender for Endpoint. The goal is to test file creation/deletion, network connectivity, and simulated malware activity.

#### 🔧 Commands Executed:

```powershell
# Create a file
New-Item hi.txt

# Delete the file
Remove-Item hi.txt

# Test external network connectivity on common ports
Test-NetConnection -ComputerName 8.8.8.8 -Port 443
Test-NetConnection -ComputerName 8.8.8.8 -Port 69

# Test internal IP connectivity (replace IP with a valid subnet address)
Test-NetConnection 10.0.0.4

# Simulate malware behavior using the EICAR test string
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' >> big-malware.exe
