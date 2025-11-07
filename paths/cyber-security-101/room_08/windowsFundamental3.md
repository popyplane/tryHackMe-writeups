# Room: Windows Fundamentals 3

**Platform:** TryHackMe
**Category:** Learn
**Difficulty:** Easy
**Estimated time:** `30 min`
**Objective(s):** In part 3 of the Windows Fundamentals module, learn about the built-in Microsoft tools that help keep the device secure, such as Windows Updates, Windows Security, BitLocker, and more...

---

## TL:DR

Windows Fundamentals 3 covers the essential built-in tools to secure and maintain a Windows device. Key topics include:

- **Windows Update:** Ensures the system is patched with security and feature updates, protecting against vulnerabilities.
- **Windows Security:** Central hub for managing protection areas like antivirus, firewall, SmartScreen, and device security.
- **Virus & Threat Protection:** Offers real-time scanning, controlled folder access, and ransomware protection.
- **Firewall & Network Protection:** Monitors and controls network traffic through domain, private, and public profiles.
- **App & Browser Control:** SmartScreen and Exploit Protection safeguard against malicious apps, downloads, and exploits.
- **Device Security:** Core isolation and TPM protect system integrity and sensitive data at the hardware level.
- **BitLocker:** Encrypts drives to prevent unauthorized data access, especially effective with TPM-enabled devices.
- **Volume Shadow Copy Service (VSS):** Creates snapshots for backups and system restore, but requires offline backups to mitigate ransomware risks.

---

## 1) Windows Updates

**Windows Update** is Microsoft’s built-in service that delivers *security patches*, *feature improvements* and *bug fixes* for Windows and other Microsoft products like **Defender**.

Updates are typically released on the second Tuesday of every month, a day known as **Patch Tuesday**. However, critical updates can be pushed out immediately if a serious vulnerability needs to be fixed.

You can access Windows Update via:
- Settings > Windows Update
OR
- The **Run dialog** / **Command Prompt** using:
```bash
> control /name Microsoft.WindowsUpdate
```

In the TryHackMe virtual machine, the update settings are *managed*, meaning updates are controlled by an administrator or system policy, and the VM itself cannot connect to Microsoft’s servers to download new updates.

Historically, users would often delay updates due to required reboots or inconvenience. To fix this, Microsoft changed the approach starting with Windows 10, making updates mandatory — they can be postponed but not skipped indefinitely.

Keeping Windows updated is crucial for system security and stability, ensuring protection against vulnerabilities and maintaining performance.

## 2) Windows Security

**Windows Security** is the central hub for managing all tools that protect your device and data. It can be accessed directly from the **Settings** menu.

The main focus areas under Protection areas include:
- Virus & threat protection
- Firewall & network protection
- App & browser control
- Device security

Each area handles a specific aspect of your system’s defense.
Windows Security also uses status icons to indicate protection levels:
* Green: Your device is protected — no action needed.
* Yellow: A recommendation is available — review suggested actions.
* Red: Immediate attention required — a critical issue needs fixing.

> The interface may look different depending on your Windows version. For example, **Windows Server 2019** differs slightly from **Windows 10 Home/Pro** in layout and available features.

Overall, Windows Security provides a unified and visual way to monitor and manage your system’s protection.

## 3) Virus & threat protection

**Virus & Threat Protection** in Windows Security is the core feature that helps safeguard your system from malware, ransomware, and other malicious threats. It’s divided into three main parts:

#### Current Threats
This section shows your **device’s current security status** and allows you to perform different types of scans:
- **Quick Scan**: Checks the most common areas where threats are typically found.
- **Full Scan**: Scans the entire system, including all files and running programs — can take over an hour.
- **Custom Scan**: Lets you select specific files or folders to scan.

You can also review your Threat History:
- **Last Scan**: Shows when the last scan was performed.
- **Quarantined Threats**: Items isolated to prevent them from running.
- **Allowed Threats**: Items manually allowed to run — only do this if you’re absolutely sure they’re safe.

#### Virus & Threat Protection Settings
Under **Manage Settings**, you can enable or configure advanced protection features:
- Real-time protection: Actively detects and blocks malware from running.
- Cloud-delivered protection: Uses Microsoft’s cloud to stay updated with the latest threat intelligence.
- Automatic sample submission: Sends suspicious samples to Microsoft for analysis.
- Controlled folder access: Protects sensitive areas from unauthorized changes (key for ransomware defense).
- Exclusions: Lets you exclude files or folders from scans — only use with caution.
- Notifications: Sends security alerts and status updates.

#### Updates & Ransomware Protection
- **Virus definition updates**: You can manually check for and install the latest Defender updates.
- **Ransomware protection**: Relies on Controlled Folder Access and Real-time protection — both should be enabled for full protection.
> Tip: You can right-click any file or folder and select “Scan with Microsoft Defender” to perform an instant check.

> Note: In the TryHackMe VM, Real-time protection is disabled for performance reasons and because the VM is isolated. On personal devices, always keep it enabled and updated unless a trusted third-party antivirus is installed.

## 4) Firewall and Network Protection

A **firewall** acts as a security barrier between your computer and the outside world. As Microsoft explains, it controls what traffic is allowed to enter or leave your system through specific network ports — essentially working like a security guard that checks the “ID” of every connection attempting to pass through.

#### Firewall Profiles
**Windows Firewall** uses three different profiles depending on the type of network you’re connected to:
- **Domain**: Used in corporate environments where the computer can authenticate with a domain controller.
- **Private**: Intended for trusted home or office networks, where you have more control over security.
- **Public**: The default profile for untrusted networks, such as cafés, airports, or public Wi-Fi.

Each profile can be customized individually, and offers two main options:
- Turn the firewall on or off
- Block all incoming connections for extra protection

> Important: You should always keep your Windows Defender Firewall enabled unless you’re absolutely certain of what you’re doing — disabling it can make your system vulnerable to attacks.

#### Allowing Apps Through the Firewall
From the **“Allow an app through firewall”** section, you can view and manage which applications have network access. Some apps may be allowed on Private, Public, or both types of networks. Clicking Details shows more information about each program’s permissions.

#### Advanced Settings
For more advanced control, you can open **Windows Defender Firewall** with Advanced Security by running the command `WF.msc`. This interface allows experienced users to configure custom inbound and outbound rules, port access, and specific network policies.

In short, the **Windows Firewall** is a fundamental line of defense that helps keep your device secure by monitoring, filtering, and managing network traffic across all your connections.

## 5) App and Browser Control

This section focuses on **Microsoft Defender SmartScreen**, a built-in Windows security feature designed to protect you from online threats such as phishing websites, malicious downloads, and unsafe applications.

Per Microsoft, *“Microsoft Defender SmartScreen protects against phishing or malware websites and applications, and the downloading of potentially malicious files.”* In short, it’s your digital bodyguard for safe browsing and downloading.

#### Check Apps and Files
**SmartScreen** scans unrecognized apps and files from the web before you open them, warning you if something seems suspicious. This helps prevent accidentally running *dangerous* or *fake* software.

#### Exploit Protection
**Exploit Protection** is another layer of defense built into Windows 10 and Windows Server 2019. It works behind the scenes to protect your device from **code exploits** — attacks that take advantage of system vulnerabilities to execute malicious actions.

> Warning: These are critical security features. Unless you are absolutely sure of what you’re doing, it’s best to keep the default SmartScreen and Exploit Protection settings enabled to ensure maximum protection.

In short, this section helps you **stay safe online and offline** by guarding against malicious files, shady apps, and system-level attacks — all without needing third-party tools.

## 6) Device Security

### Device Security

This section focuses on hardware-level protection that helps safeguard your system from deeper, more sophisticated attacks.

#### Core Isolation
**Core isolation** provides virtualization-based security features that help protect important system processes from being tampered with by malicious code.  

- **Memory Integrity:** Prevents attackers from injecting malicious code into high-security processes, ensuring your system’s core operations remain secure.

> **Warning:** It’s strongly recommended to leave these settings at their default values, unless you fully understand their impact on your system.

#### Security Processor (TPM)
Modern systems also include a **Security Processor**, better known as the **Trusted Platform Module (TPM)**.

Per Microsoft, *“Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that carries out cryptographic operations, featuring multiple physical security mechanisms to make it tamper-resistant.”*

In simpler terms, **TPM acts as a hardware vault** — it securely stores encryption keys, passwords, and certificates, ensuring that even if malware compromises your software, the sensitive data remains protected.

Overall, the **Device Security** section ensures your system’s foundation is protected at the hardware and virtualization level, forming one of the most important layers of Windows security.


## 7) BitLocker

**BitLocker** is a data protection feature in Windows designed to prevent unauthorized access to data on lost, stolen, or decommissioned devices.

Per Microsoft: *"BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers."*

#### Key Points

- On devices with a **Trusted Platform Module (TPM)** installed, BitLocker provides the highest level of protection.
- TPM works alongside BitLocker to:
  - Secure user data
  - Ensure the system has not been tampered with while offline
- Best protection is achieved with **TPM version 1.2 or later**.

> **Note:** The BitLocker feature is not included in the attached VM.

Refer to the official [Microsoft BitLocker documentation](https://learn.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview) for more details.

## 8) Volume Shadow Copy Service (VSS)

Per Microsoft, the **Volume Shadow Copy Service (VSS)** coordinates the creation of consistent shadow copies (snapshots) of data for backup purposes. These shadow copies are stored in the **System Volume Information** folder on each drive with protection enabled.

When **VSS/System Protection** is enabled, I can:

- Create a restore point
- Perform a system restore
- Configure restore settings
- Delete restore points

From a security perspective, malware often targets these shadow copies. Some ransomware will attempt to delete them, making recovery impossible without an offline or off-site backup.

For hands-on practice with VSS, the attached VM can be configured through **Advanced System Settings**, or I can explore Day 23 of *Advent of Cyber 2* for an interactive exercise.

---

## Conclusion

Windows provides a robust suite of security and protection tools built into the OS, from software-level defenses like antivirus, firewall, and SmartScreen, to hardware-based protections with Core Isolation and TPM. Features like BitLocker and VSS further ensure data security and recoverability. Staying updated, keeping real-time protection enabled, and using these tools as intended forms a multi-layered defense that helps maintain system integrity, prevent unauthorized access, and safeguard against malware and ransomware.

---

## Further reading material:

- [Antimalware Scan Interface](https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal)
- [Credential Guard](https://docs.microsoft.com/en-us/windows/security/identity-protection/credential-guard/credential-guard-manage)
- [Windows 10 Hello](https://support.microsoft.com/en-us/windows/learn-about-windows-hello-and-set-it-up-dae28983-8242-bb2a-d3d1-87c9d265a5f0#:~:text=Windows%2010,in%20with%20just%20your%20PIN.)
- [CSO Online - The best new Windows 10 security features](https://www.csoonline.com/article/3253899/the-best-new-windows-10-security-features.html)

> Note: Attackers use built-in Windows tools and utilities in an attempt to go undetected within the victim environment.  This tactic is known as Living Off The Land. Refer to the following resource here to learn more about this. 