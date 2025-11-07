# Room: Windows Fundamentals 1

**Platform:** TryHackMe
**Category:** Learn
**Difficulty:** Easy
**Estimated time:** `30 min`
**Objective(s):** In part 1 of the Windows Fundamentals module, we'll start our journey learning about the Windows desktop, the NTFS file system, UAC, the Control Panel, and more..

---

## TL;DR

I learned the key components and security features of Windows, from the desktop to user management, UAC, and Task Manager, giving me a strong foundation for system use and administration.

---

## 1) Windows Editions

**Windows** has been the leading operating system since its first release in 1985, making it a frequent target for hackers and malware. Over the years, **Microsoft** has released many versions—some successful, like *Windows 7* and *10*, and others less so, like *Vista* and *8*. The transition from *Windows XP* caused major challenges for organizations adapting to new systems. Today, *Windows 11* stands as the main OS for desktops, available in Home and Pro editions, while *Windows Server 2025* is the latest for servers. With each version, **Microsoft** has focused on improving both usability and security.

## 2) The Desktop (GUI)

This stage introduced the **Windows Desktop environment**, explaining its main graphical components and customization options. After logging in, users are greeted with the desktop — a workspace containing shortcuts, folders, and files for quick access. The **Start Menu** provides navigation to programs, settings, and account actions, while the **Taskbar** manages open applications and pinned items for easy switching. The **Notification Area** displays system icons like time, network, and volume, which can be customized through Taskbar settings. Overall, this section gave a clear overview of how Windows organizes its user interface and how each element contributes to efficient navigation and personalization.

## 3) Introduction to Windows

Now we are given a machine to explore how to use **Windows**. We can access it via remote desktop with the credentials tryHackMe gives us.

## 4) The Filesystem

Next, this stage covers the Windows file system, focusing on **NTFS** (New Technology File System), which replaced older formats like *FAT16*, *FAT32*, and *HPFS*. **NTFS** introduced major improvements such as file journaling for recovery, support for files larger than 4GB, file and folder permissions, compression, and encryption. It allows fine-grained control over access through permissions like Full Control, Read, and Write, all configurable via file or folder properties. Another key **NTFS** feature is *Alternate Data Streams* (ADS), which let files store hidden data streams — sometimes used by malware, but also legitimately by Windows for metadata such as download origins. Overall, **NTFS** is a powerful and secure file system forming the foundation of modern Windows storage.

## 5) The Windows\System32 Folders

This stage introduced the **Windows folder (C:\Windows)** — the core directory that contains the **Windows operating system** files. While it’s usually located on the `C: drive`, it can technically reside on another drive or path. To reference it dynamically, Windows uses an environment variable, `%windir%`, which points to the system’s Windows directory.
Environment variables store important system information such as file paths, processor details, and temporary folder locations. Inside the Windows folder are many subfolders, the most critical being **System32**, which contains essential system files needed for Windows to function. Any accidental deletion or modification in System32 can make the operating system unusable, so it must be handled with great caution.

## 6) User Accounts, Profiles, and Permissions

This stage explored user accounts on Windows, which come in two main types: **Administrator** and **Standard User**. The Administrator has full control over the system — managing users, settings, and installations — while the Standard User is limited to modifying personal files and folders.
I learned how to view existing accounts via `Settings > Other users`, and how only Administrators can add or change account types. Each user has a personal profile stored under `C:\Users\[username]`, which is created automatically upon first login.
I also saw how to manage users and groups through *Local User* and *Group Management* (lusrmgr.msc). Here, accounts and groups are listed along with their permissions. Groups define what users can do on the system, and any user added to a group inherits that group’s permissions — a core principle of Windows account management

## 7) User Account Control (UAC)

In this stage, you learned about **UAC** — a key Windows security feature designed to protect systems from unauthorized changes and malware infections.
Most home users operate as local administrators, meaning they have full control over the system. However, running everyday tasks (like browsing or writing documents) with these elevated privileges is risky. Malware running under an admin account could easily modify system settings or files.
That’s where **UAC** comes in. Introduced in Windows Vista, **UAC** limits the use of administrative rights until they’re explicitly approved. Even when an admin logs in, their session runs with standard privileges by default. When a task needs higher-level access, a **UAC** prompt appears, asking for confirmation (and sometimes a password).
This extra step prevents unauthorized changes and helps block malware from gaining full control. You can recognize programs that will trigger **UAC** by the shield icon on their shortcuts. In short, **UAC** acts as a safeguard between the user and the system — ensuring that elevated actions only happen with clear user consent.

## 8) Settings and the Control Panel

In this stage, I explored the **two main hubs for system configuration** in Windows — the **Settings menu** and the **Control Panel**.
For years, the **Control Panel** was the heart of system management, used for tasks like adding printers or uninstalling programs. With **Windows 8**, Microsoft introduced the **Settings menu**, designed for a more modern and touch-friendly experience. Today, on Windows 10 and beyond, **Settings** has become the go-to place for most users to personalize and adjust their systems.
While both serve similar purposes, the **Control Panel** still handles more advanced and legacy configurations. Interestingly, some actions in Settings (like changing network adapter options) still redirect you to the Control Panel — proof that both tools are intertwined.
If you’re ever unsure which one to open, simply **search for what you need** in the Start Menu. Windows will automatically guide you to the right location, whether that’s a Settings page or a Control Panel window.

## 9) Task Manager

In this final stage, I explored the **Task Manager**, a tool that provides insight into the applications and processes currently running on the system. It also shows performance metrics like CPU and RAM usage, helping me understand how system resources are being utilized.
I accessed the Task Manager by right-clicking the taskbar, which initially opened it in *Simple View* with limited information. By selecting `More details`, I gained a full view of running processes, performance data, and additional system information.
This tool is essential for monitoring and managing system activity.

## 10) Conclusion

In this module, I gained a solid foundation in **Windows fundamentals**, exploring everything from the *desktop interface* and *file system* to *user accounts*, *UAC*, *system settings*, and *Task Manager*. I learned how **Windows** organizes its environment, manages permissions, and safeguards against unauthorized changes, giving me a better understanding of both usability and security aspects. Overall, this module gave me the practical knowledge to navigate, configure, and monitor a *Windows system* confidently, laying the groundwork for more advanced Windows administration and security tasks.