# secbyte-windows-internals-kernel-forensics-boot-sequence-ctf-labs
A practical collection of cybersecurity CTF labs covering Windows system internals, kernel architecture (ETW, Object Manager, Threads, Tokens, API syscalls, Working Sets), process forensics (Process Hollowing, Registry Hive analysis), Linux /proc internals, and OS boot sequence mechanics (UEFI, Bootmgr, Winlogon).
# Windows System Internals, Kernel Telemetry, Process Forensics & Boot Sequence CTF Labs

Welcome to the **Windows System Internals, Kernel Telemetry, Process Forensics & Boot Sequence CTF Lab Collection**. This repository serves as an organized, searchable catalog of practical cybersecurity labs hosted on Learn SecByte.

This collection focuses on deep Windows operating system architecture, kernel-level telemetry, low-level process execution mechanics, and boot-time forensic analysis—spanning **Windows Kernel Internals & Telemetry (ETW tracing, Object Manager, Thread scheduling, Security Tokens, Native API syscalls)**, **Windows Memory & Process Forensics (Process Hollowing, Working Set management, Registry hive forensics)**, and **OS Boot Mechanics & Process Control (UEFI/BIOS initialization, Winlogon, Linux `/proc` virtual file system)**.

---

## Lab Collection Index

### 1. Windows Kernel Architecture, Telemetry & Security Model
* **Windows System Internals: Ghosts in the Kernel**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-system-internals-ghosts-in-the-kernel](https://learn.secbyte.org/ctf/windows-system-internals-ghosts-in-the-kernel)  
  *Focus:* Analyzing Windows Executive services, Kernel-mode vs. User-mode transitions, kernel driver structures (`DRIVER_OBJECT`, `DEVICE_OBJECT`), and inspecting hidden kernel callbacks.

* **Windows Kernel Basics: Event Tracer Incident**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-kernel-basics-event-tracer-incident](https://learn.secbyte.org/ctf/windows-kernel-basics-event-tracer-incident)  
  *Focus:* Leveraging Event Tracing for Windows (ETW) telemetry, auditing ETW session providers (`Microsoft-Windows-Threat-Intelligence`), and detecting ETW patching/blindspot evasion attempts.

<Image src="image_agent_tag_5454463380955242298" alt="Windows Kernel architecture diagram detailing Executive Services, Object Manager, and User/Kernel mode boundaries" caption="Windows Kernel Architecture & Executive Subsystems Framework" />

---

* **Windows Security Model: Token Trail**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-security-model-token-trail](https://learn.secbyte.org/ctf/windows-security-model-token-trail)  
  *Focus:* Auditing Windows Access Tokens (`TOKEN_USER`, `TOKEN_PRIVILEGES`), detecting Token Impersonation and Theft (SeAssignPrimaryTokenPrivilege, SeImpersonatePrivilege), and tracing privilege elevation pathways.

* **Windows Object Manager: Invisible Paths**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-object-manager-invisible-paths](https://learn.secbyte.org/ctf/windows-object-manager-invisible-paths)  
  *Focus:* Inspecting the Windows Object Manager namespace using WinObj, analyzing symbolic links (`\RPC Control`), object directory security descriptors, and auditing handle tables.

* **Windows API Exploration: The Syscall Cipher**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-api-exploration-the-syscall-cipher](https://learn.secbyte.org/ctf/windows-api-exploration-the-syscall-cipher)  
  *Focus:* Tracing user-mode API calls (`kernel32.dll`, `ntdll.dll`) to Native API System Calls (`Nt`/`Zw` functions), inspecting direct/indirect syscall execution (Hell's Gate, Halo's Gate), and bypassing EDR user-mode hooks.

### 2. Windows Process, Memory & Registry Forensics
* **Windows Process Forensics: The Hollowed Service**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-process-forensics-the-hollowed-service](https://learn.secbyte.org/ctf/windows-process-forensics-the-hollowed-service)  
  *Focus:* Investigating Process Hollowing (`NtUnmapViewOfSection`, `VirtualAllocEx`, `WriteProcessMemory`), analyzing PEB (Process Environment Block) structures, and unearthing unbacked memory regions using Volatility and Process Hacker/System Informer.

* **Windows Threads: An Executor's Trace**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-threads-an-executors-trace](https://learn.secbyte.org/ctf/windows-threads-an-executors-trace)  
  *Focus:* Analyzing thread creation mechanics (`CreateRemoteThread`, `NtCreateThreadEx`), inspecting Thread Environment Blocks (TEB), tracking thread execution contexts, and identifying malicious thread injection.

* **Windows Memory Management: Working Set Incident**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-memory-management-working-set-incident](https://learn.secbyte.org/ctf/windows-memory-management-working-set-incident)  
  *Focus:* Inspecting physical memory page tables, analyzing Working Set lists (`SYSTEM_SERVICE_DESCRIPTOR_TABLE`), diagnosing page faults, and dumping process memory dumps (`RAM`).

* **Registry Forensics: Ghost Keys in the Hive**  
  *Lab Link:* [https://learn.secbyte.org/ctf/registry-forensics-ghost-keys-in-the-hive](https://learn.secbyte.org/ctf/registry-forensics-ghost-keys-in-the-hive)  
  *Focus:* Parsing Windows Registry transaction logs (`.LOG1`/`.LOG2`), recovering deleted registry keys from raw hives (`SYSTEM`, `SOFTWARE`, `NTUSER.DAT`), and detecting hidden persistence keys (Run keys, UserInit, Winlogon helpers).

### 3. OS Boot Mechanics & Low-Level Process Control
* **Windows Boot Process: From Firmware to Login**  
  *Lab Link:* [https://learn.secbyte.org/ctf/windows-boot-process-from-firmware-to-login](https://learn.secbyte.org/ctf/windows-boot-process-from-firmware-to-login)  
  *Focus:* Dissecting the complete Windows startup sequence—from UEFI/BIOS firmware, `bootmgr.efi`, `winload.efi`, kernel loading (`ntoskrnl.exe`), `HAL.dll`, `smss.exe`, `csrss.exe`, to `winlogon.exe`.

<Image src="image_agent_tag_5454463380955240927" alt="Windows Boot Process flow diagram illustrating stage progression from UEFI firmware to login" caption="Windows OS Boot Process & Component Startup Execution Pipeline" />

---

* **Boot Sequence Breakdown**  
  *Lab Link:* [https://learn.secbyte.org/ctf/boot-sequence-breakdown](https://learn.secbyte.org/ctf/boot-sequence-breakdown)  
  *Focus:* Comparing multi-OS boot loader implementations (GRUB, Systemd-boot, Windows Boot Manager), analyzing Master Boot Record (MBR) and GUID Partition Table (GPT) structures, and inspecting boot integrity controls (Secure Boot, TPM).

* **Linux Internals: Ghosts in /proc**  
  *Lab Link:* [https://learn.secbyte.org/ctf/linux-internals-ghosts-in-proc](https://learn.secbyte.org/ctf/linux-internals-ghosts-in-proc)  
  *Focus:* Inspecting the Linux pseudo-filesystem (`/proc`), dissecting `/proc/[pid]/mem`, `/proc/[pid]/exe`, `/proc/[pid]/fd`, and detecting unlinked running binaries and process hiding techniques.

---

## Learning Path

### Path A: Windows System Internals & Kernel Specialist
1. **Kernel Architecture & Telemetry:** Start with [Windows System Internals: Ghosts in the Kernel](https://learn.secbyte.org/ctf/windows-system-internals-ghosts-in-the-kernel) and [Windows Kernel Basics: Event Tracer Incident](https://learn.secbyte.org/ctf/windows-kernel-basics-event-tracer-incident).
2. **Tokens & Object Manager:** Master Windows security primitives via [Windows Security Model: Token Trail](https://learn.secbyte.org/ctf/windows-security-model-token-trail), [Windows Object Manager](https://learn.secbyte.org/ctf/windows-object-manager-invisible-paths), and [Windows API Exploration: The Syscall Cipher](https://learn.secbyte.org/ctf/windows-api-exploration-the-syscall-cipher).

### Path B: Windows Memory & Process Forensic Examiner
1. **Process Injection & Memory:** Investigate host execution in [Windows Process Forensics: The Hollowed Service](https://learn.secbyte.org/ctf/windows-process-forensics-the-hollowed-service), [Windows Threads](https://learn.secbyte.org/ctf/windows-threads-an-executors-trace), and [Windows Memory Management](https://learn.secbyte.org/ctf/windows-memory-management-working-set-incident).
2. **Registry Forensics:** Recover deleted registry keys in [Registry Forensics: Ghost Keys in the Hive](https://learn.secbyte.org/ctf/registry-forensics-ghost-keys-in-the-hive).

### Path C: OS Boot Mechanics & Process Control Specialist
1. **Boot Analysis:** Master system startup execution in [Windows Boot Process: From Firmware to Login](https://learn.secbyte.org/ctf/windows-boot-process-from-firmware-to-login) and [Boot Sequence Breakdown](https://learn.secbyte.org/ctf/boot-sequence-breakdown).
2. **Linux Process Virtual Filesystem:** Inspect process memory handles in [Linux Internals: Ghosts in /proc](https://learn.secbyte.org/ctf/linux-internals-ghosts-in-proc).

---

## How to Use the Labs

1. Select a practice scenario from the **Lab Collection Index**.
2. Click the direct link to launch the exercise environment on Learn SecByte.
3. Review scenario directives, ETW trace logs (`.etl`), crash memory dumps (`.dmp`), raw Registry hives, or kernel debug logs (`WinDbg`).
4. Analyze Process Hollowing in memory, trace Windows API system call stubs, audit ETW telemetry providers, parse deleted registry transactions, or inspect UEFI boot manager execution stubs to capture flags.

---

## Target Audience

* **Windows Forensic Investigators & Incident Responders:** Analyze physical memory dumps, reconstruct process hollowing injections, parse Registry hive transaction logs, and triage ETW event streams.
* **Reverse Engineers & Vulnerability Researchers:** Inspect native Windows API system calls (`ntdll.dll`), analyze thread execution contexts, debug kernel callbacks, and audit process privilege tokens.
* **Detection Engineers & Blue Teamers:** Develop ETW telemetry rules, detect process injection patterns, monitor Object Manager symbolic link manipulation, and track privilege escalation.
* **Cybersecurity Students:** Acquire practical expertise in Windows OS architecture, kernel internals, memory management, and system boot procedures.

---

## Disclaimer

All lab links provided in this repository direct to official training environments hosted on Learn SecByte. All materials and exercises are provided strictly for educational purposes, defensive skill building, and authorized security research. Unauthorized kernel modification, memory tampering, or probing against external systems is strictly prohibited.
