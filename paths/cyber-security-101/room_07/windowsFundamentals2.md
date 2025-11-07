# Room: Windows Fundamentals 2

**Platform:** TryHackMe
**Category:** Learn
**Difficulty:** Easy
**Estimated time:** `30 min`
**Objective(s):** In part 2 of the Windows Fundamentals module, discover more about System Configuration, UAC Settings, Resource Monitoring, the Windows Registry and more..

---

## TL;DR

Windows offers a variety of built-in tools to monitor, configure, and troubleshoot the system — from **MSConfig** and **UAC** settings to **Resource Monitor**, **Computer Management**, **Command Prompt** and the **Registry**. Each tool gives me insight into system behavior, performance, and configuration, helping me keep Windows running smoothly and securely.

---

## 1) System Configuration

I explored the **System Configuration utility** (MSConfig), a neat tool for troubleshooting Windows startup issues. It has five tabs: General, Boot, Services, Startup, and Tools. The General tab controls what loads on startup, the Boot tab sets boot options, and Services lists background apps. The Startup tab is mostly empty in the VM, but Task Manager is recommended for managing startup programs. The Tools tab gives quick access to various system utilities, which can be launched directly from MSConfig. Overall, it’s a powerful diagnostic tool that’s fun to explore safely!

## 2) Change UAC Settings

In this stage, I explored the **UAC settings** available through the *System Configuration Tools* tab. I can adjust the UAC level using a slider or even turn it off entirely (though that’s not recommended). Moving the slider shows how the system’s behavior changes and reflects Microsoft’s recommendations for keeping the system secure.

## 3) Computer Management

The **Computer Management** (compmgmt) utility is a powerful hub with three main sections: *System Tools*, *Storage* and *Services & Applications*.
Under System Tools, I explored *Task Scheduler* for automating tasks, *Event Viewer* for auditing system events, *Shared Folders* to see network shares and active sessions, *Local Users* and *Groups* for account management, *Performance Monitor* (Perfmon) for tracking system resources, and *Device Manager* to view and configure hardware.
In *Storage*, I focused on *Disk Management*, which allows creating, resizing, and assigning drive letters for partitions—useful for advanced storage tasks on *Windows Server*.
Finally, under Services & Applications, I reviewed services and their properties, and explored **WMI Control** for managing Windows via scripting or PowerShell, noting that the old **WMIC** tool is now deprecated.
Overall, Computer Management provides a central place to monitor, configure, and troubleshoot almost every aspect of a Windows system.

## 4) System Configuration Panel

The **System Information** (msinfo32) tool provides a detailed overview of a Windows system, covering hardware, components, and software environment.
In System Summary, we can see general specs like processor model and system details. Hardware Resources shows:
- low-level system info
- Components lists installed devices such as display and input hardware
- Software Environment reveals OS-integrated and installed software, along with environment variables and network connections.

Environment variables store key system data, like the **Windows installation path** (WINDIR), which programs can reference to locate system files.
The tool also includes a search bar, letting me quickly find specific info, like IP addresses, across all components. Overall, msinfo32 is a handy utility for diagnosing and exploring detailed system information.

## 5) Ressource Monitor

**Resource Monitor** (resmon) is a powerful Windows tool for monitoring system performance in real time, showing detailed usage per process for **CPU**, **Memory**, **Disk** and **Network**.

Each of these four areas has its own tab with in-depth data, while the right-hand pane provides a live graphical view of activity. I can also see which processes are using specific files or modules, filter by process, and even manage services—start, stop, pause, or resume them.

It’s especially useful for troubleshooting, identifying deadlocks, or resolving file locking conflicts without abruptly closing applications and risking data loss. Overall, **resmon** gives me a clear picture of what’s happening under the hood of my system.

## 6) Command Prompt

The **Command Prompt** (cmd) is a classic Windows tool that lets me interact with the system via text commands instead of the GUI. Even though the GUI makes most tasks easy, cmd is still super useful for gathering system info and troubleshooting.

Basic commands like `hostname` and `whoami` tell me the computer name and the current logged-in user, while `ipconfig` shows network settings. I can use `/?` with most commands to view their help manual, and `cls` clears the screen.

Commands like `netstat` provide network connection details, and `net` manages network resources with sub-commands like *user*, *localgroup*, *share* and *session*. Experimenting with parameters reveals even more functionality.
Overall, cmd is a powerful, lightweight way to see what’s going on under the hood and perform tasks quickly, especially for troubleshooting or advanced users.

## 7) Registry Editor

The **Windows Registry** is basically the central brain of the system, storing all sorts of crucial info that Windows constantly checks while running. It keeps track of things like user profiles, installed applications, folder and icon settings, connected hardware, and even which ports are in use.

Editing the registry is powerful but risky — a wrong change can break the system, so it’s really only for advanced users. The most common way to view or edit it is through **Registry Editor** (regedit).

In short, the registry is the behind-the-scenes hub that keeps Windows running smoothly, and handling it carefully is key.

## 8) Conclusion

The second part of **Windows Fundamentals** was a deep dive into the nuts and bolts of the system. I explored how to troubleshoot startup issues with **MSConfig**, manage permissions with **UAC**, monitor performance with **Resource Monitor**, inspect system details with **msinfo32**, and interact directly with the system using *Command Prompt* and the *Registry Editor*.

These tools are essential for advanced users who want to understand what’s happening under the hood, tweak system settings safely, and troubleshoot issues effectively. Overall, this module gave me a stronger grasp of Windows internals, making me more confident in managing and analyzing the system.