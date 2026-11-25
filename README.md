# Awesome-Operating-System-Security-Kernel-Research

# Awesome Operating System Security & Kernel Research

> A curated list of top Operating System Security and Kernel Research platforms — both SaaS/Hosted commercial endpoint protection suites and open-source alternatives for kernel-level security, rootkit detection, and OS internals research.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [CrowdStrike Falcon](#crowdstrike-falcon)
  - [SentinelOne Singularity](#sentinelone-singularity)
  - [Microsoft Defender for Endpoint](#microsoft-defender-for-endpoint)
  - [Carbon Black Cloud](#carbon-black-cloud)
  - [Sophos Intercept X](#sophos-intercept-x)
  - [Trend Micro Apex One](#trend-micro-apex-one)
  - [Cybereason](#cybereason)
  - [Bitdefender GravityZone](#bitdefender-gravityzone)
  - [Palo Alto Cortex XDR](#palo-alto-cortex-xdr)
  - [Trellix Endpoint Security](#trellix-endpoint-security)
- [Open-Source Software](#-open-source-software)
  - [Warden](#warden)
  - [Wazuh](#wazuh)
  - [chkrootkit](#chkrootkit)
  - [HakiOS (hakios-xnu-kernel)](#hakios-hakios-xnu-kernel)
  - [RustEKC](#rustekc)
  - [Harness](#harness)
  - [RuntimeTrace](#runtimetrace)
  - [KSword](#ksword)
  - [Endpoint Security AI Agent](#endpoint-security-ai-agent)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted OS Security and Kernel-level endpoint protection platforms. These are not open-source but are included as reference points for feature comparison.

### CrowdStrike Falcon
**Type:** AI-native endpoint protection with kernel-level telemetry
CrowdStrike Falcon is a leading cloud-native endpoint protection platform with deep kernel-level visibility and threat intelligence. It provides EDR, XDR, and managed threat hunting capabilities, with a single lightweight agent.

### SentinelOne Singularity
**Type:** Autonomous endpoint protection with kernel-level behavioral AI
SentinelOne provides autonomous EDR/XDR with behavioral AI models that run at the endpoint level, including kernel-level monitoring. It is known for automated response and ransomware rollback capabilities.

### Microsoft Defender for Endpoint
**Type:** Integrated endpoint protection within Microsoft XDR
Defender for Endpoint provides EDR capabilities tightly integrated with the Microsoft security ecosystem, including kernel-level sensor telemetry and automated investigation.

### Carbon Black Cloud
**Type:** Behavioral EDR with kernel-level recording
Carbon Black Cloud provides continuous endpoint activity recording and behavioral analytics, with kernel-level visibility for threat hunting and compliance.

### Sophos Intercept X
**Type:** Deep learning endpoint protection with anti-ransomware
Intercept X combines signature-based and behavioral detection with deep learning models, including kernel-level ransomware protection via CryptoGuard.

### Trend Micro Apex One
**Type:** Enterprise endpoint security with XDR
Apex One provides endpoint protection with behavioral analysis, application control, and integration into Trend Micro's Vision One XDR platform.

### Cybereason
**Type:** AI-driven endpoint detection and response
Cybereason provides EDR with behavioral analytics and automated response, including kernel-level monitoring for ransomware and fileless attacks.

### Bitdefender GravityZone
**Type:** Layered endpoint protection with machine learning
GravityZone provides endpoint security with multiple layers including machine learning, behavioral monitoring, and kernel-level protection.

### Palo Alto Cortex XDR
**Type:** Integrated XDR with kernel-level endpoint protection
Cortex XDR combines endpoint protection with network and cloud telemetry, providing kernel-level visibility and automated response.

### Trellix Endpoint Security
**Type:** Enterprise endpoint protection with FireEye/McAfee heritage
Trellix Endpoint Security provides integrated endpoint protection with threat intelligence from FireEye/Mandiant lineage, including kernel-level behavioral monitoring.

---

## 🟩 Open-Source Software

Self-hosted, community-driven tools for OS security research, kernel-level protection, and rootkit detection.

### Warden
**Stack:** Rust / eBPF / Linux | **License:** Open Source (GitHub) 
Warden is a free, open-source **EDR for Linux workstations** written in Rust, with a security model hardened through adversarial testing . Key kernel-level and security research capabilities include:
- **eBPF modules** (`warden-exec`, `warden-network`) for kernel-level execution and network monitoring 
- **Fanotify-based ransomware detection** with per-PID, per-directory, and global counters to catch fork-per-file attacks 
- **YARA scanning** with file descriptor-based reads to avoid TOCTOU vulnerabilities 
- **Hardened through real testing**: package-manager spoofing detection (checks directory, not just name), quarantine bypass prevention via safe truncation, and UID checks for auto-quarantine privileges 
- **GTK4 GUI** with privileged actions gated behind `pkexec` authentication 

The project documents its security findings and fixes in `PROGRESS.md`, with reproducing tests for each vulnerability addressed .  
**Best for:** Linux security researchers and administrators wanting a hardened, open-source EDR with kernel-level telemetry and documented security research practices.

### Wazuh
**Stack:** C++ / OpenSearch | **License:** GPL-2.0 
Wazuh is a unified open-source XDR and SIEM platform with an endpoint security agent deployed to monitored systems and a management server that collects and analyzes data . Key capabilities for OS security research include:
- **File Integrity Monitoring (FIM)** with real-time alerts on file additions, modifications, and deletions 
- **Rootkit detection** and **malware detection** monitoring files, system logs, Windows Registry, and system calls 
- **Vulnerability Detection** correlating software inventory against CVE data 
- **Active response** for automated actions 
- **FreeBSD support** with extensive quarterly improvements including fixes for MYSQL option startup issues, asyncinotify support for the Wazuh API, and SQLite-based package information retrieval [citation:4]

The FreeBSD status report documents ongoing work to improve platform support, with a centralized GitHub repository for patches [citation:4].  
**Best for:** Organizations wanting a comprehensive open-source SIEM/XDR platform with kernel-level monitoring and rootkit detection capabilities across multiple platforms.

### chkrootkit
**Stack:** Shell script / C | **License:** Open Source 
chkrootkit is a long-standing tool to locally check for signs of a rootkit . It contains:
- **chkrootkit**: shell script that checks system binaries for rootkit modification 
- **ifpromisc**: checks if the network interface is in promiscuous mode 
- **chklastlog / chkwtmp / chkutmp**: checks for log deletions 
- **chkproc**: checks for signs of LKM (Loadable Kernel Module) trojans 
- **chkdirs**: checks for signs of LKM trojans 

It is packaged for Fedora (version 0.58) and available for multiple architectures [citation:8].  
**Best for:** System administrators wanting a proven, lightweight tool for detecting signs of rootkits on Linux systems.

### HakiOS (hakios-xnu-kernel)
**Stack:** C / XNU (Darwin kernel) | **License:** APSL 2.0 (XNU patch) / MIT (rest) 
HakiOS is an experimental project focused on bringing **Darwin (XNU kernel)** to Android hardware . Key research characteristics:
- **Runs Apple's open-source XNU kernel** (`xnu-8796.121.2`, iOS 16.5) on Android phones, with a boot loader, drivers, and configuration of its own 
- **Runs in QEMU** with nothing of Apple's and nothing of any phone's (`make qemu-open`) 
- **Research bench, not a ROM**: by default runs from RAM, and a reboot gives the phone back to Android 
- **Metal on Adreno**: `hakios-metal` implements Metal's command model on the Adreno GPU through the kernel's GPU driver, achieving 110-118 fps for page swipes on a POCO X5 Pro 5G [citation:5]
- **Builds on Linux with stock clang** (no macOS, no Xcode) and on macOS with Xcode 

**Important:** This is an independent research project, not affiliated with or endorsed by Apple. No Apple firmware is distributed—users supply their own .  
**Best for:** OS kernel researchers exploring cross-platform kernel porting, Darwin internals, and GPU driver implementation on non-native hardware.

### RustEKC
**Stack:** Rust / RISC-V64 / AArch64 | **License:** Open Source (Zenodo artifact) 
RustEKC is a **portable kernel compartment** (Embedded Kernel Compartment) implemented in Rust that eliminates the need for virtualization, extended ISAs, and secure hardware modules for kernel isolation . Key research characteristics:
- **Cross-platform prototype** with good portability and reusability 
- **Deployed OS kernels**: rCore, FreeRTOS, and TinyLinux as payloads 
- **QEMU platform** support for RISC-V64 and AArch64 
- **Artifact includes**: source code, payload sources, and pre-compiled binaries for direct testing 

The design aims to enhance operating system security by solving the kernel growth and complexity problem with a cross-platform isolation mechanism .  
**Best for:** OS security researchers exploring lightweight kernel isolation mechanisms without hardware virtualization support.

### Harness
**Stack:** Hypervisor-based (Raspberry Pi) | **License:** Research artifact (USENIX Security '25) 
Harness is a lightweight framework that **transparently protects vehicle control from an untrusted Android Automotive Operating System (AAOS)** . Key research characteristics:
- **Leverages hypervisor capabilities** to isolate security-critical components from AAOS 
- **Protects interactions** with the external environment 
- **Ensures vehicle control operations align with user intent** 
- **Artifacts include**: modified host and guest kernels, Harness kernel module, Lowvisor host kernel module, and AOSP patch 

Presented at USENIX Security '25, with attack simulation and benchmark evaluation code provided [citation:11].  
**Best for:** Automotive security researchers and OS kernel researchers exploring hypervisor-based isolation for safety-critical systems.

### RuntimeTrace
**Stack:** Python / eBPF / Linux | **License:** Open Source (PyPI) 
RuntimeTrace is a **runtime cross-layer consistency checker via eBPF** that detects discrepancies between kernel state and user-space expectations . Key research-relevant capabilities:
- **Detects deleted executables still running** (`deleted_exe_running`) 
- **Hidden module detection** via `/proc/modules` vs `/sys/module` comparison (with careful handling of built-in vs loaded modules) 
- **Pure comparison logic** tested with fake tampered and clean scenarios, plus a root-only eBPF collector test that attaches a real probe 
- **Lessons documented**: the first version flagged well over a hundred "hidden modules" on a clean system due to built-in modules appearing in `/sys/module`, fixed by checking for `coresize` file 

The tool emphasizes that "a tool that cries wolf on a clean system gets ignored" and documents its fixes before shipping [citation:3].  
**Best for:** Security researchers and system administrators wanting to detect kernel-level inconsistencies such as hidden modules and deleted executables.

### KSword
**Stack:** Windows kernel driver / Qt | **License:** Open Source (AtomGit mirror) 
KSword is a **Windows kernel-level anti-rootkit and system analysis project** built around a hypervisor (Intel VMX/EPT, experimental AMD SVM/NPT) . Key research capabilities:
- **Nested virtualization architecture** (Hyper-V → Windows → KSword → VMware → TinyCore chain documented) 
- **17 main docks** covering Process, Network, Memory, File, Driver, Kernel, HVM, Monitor, Hardware, Privileges, Windows, Registry, Handles, Startup, Services, and more 
- **Kernel-level analysis**: SSDT/SSSDT, inline/IAT/EAT hooks, CID cross-view, ALPC/IPC, callback inventory, and descriptor/IOCTL decoding 
- **Reversible R0 hiding** (gated), PPL/signature operations with risk prompts 
- **Kernel Knowledge**: 71 articles included 

Controlled Intel experiments include 4×2 page remap/restore trials and VMware guest nested-SVM probes (1/2/4/8-vCPU) .  
**Best for:** Windows kernel security researchers exploring rootkit detection, hypervisor-based monitoring, and deep system internals analysis.

### Endpoint Security AI Agent
**Stack:** Python / FastAPI / osquery / Docker | **License:** Open Source (GitHub) 
An open-source **AI EDR** that detects and stops ransomware, Cobalt Strike, and living-off-the-land attacks in real time . Key capabilities:
- **ML-powered ransomware detection**: encrypted extensions, high entropy, rapid file changes 
- **C2 beaconing detection**: interval, jitter, reputation analysis 
- **LOLBAS detection**: abuse of PowerShell, cmd, wmic, rundll32 
- **Autonomous response**: auto-kill, quarantine, host isolation 
- **ChatGPT-style AI analyst** for natural language security event queries 
- **Cross-platform**: Windows, macOS, Linux via Docker Compose 

It uses osquery for real-time telemetry and provides a Next.js dashboard with real-time WebSocket updates [citation:12].  
**Best for:** Security teams and researchers wanting an open-source AI-driven EDR with kernel-level telemetry and natural language analysis capabilities.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Kernel-Level | Focus | Self-Hosted | Best For |
|----------|---------|-------|--------------|-------|-------------|----------|
| **CrowdStrike** | Proprietary | Cloud | ✅ | Endpoint protection | ❌ | AI-native EDR/XDR |
| **SentinelOne** | Proprietary | Cloud | ✅ | Autonomous EDR | ❌ | Behavioral AI response |
| **Warden** | Open Source | Rust/eBPF | ✅ | Linux EDR | ✅ | Hardened OSS EDR |
| **Wazuh** | GPL-2.0 | C++/OpenSearch | ✅ | SIEM/XDR | ✅ | Full OSS security platform |
| **chkrootkit** | Open Source | Shell/C | (Checks) | Rootkit detection | ✅ | Lightweight rootkit scanner |
| **HakiOS** | APSL 2.0/MIT | C/XNU | ✅ | Darwin on Android | ✅ | Cross-platform kernel research |
| **RustEKC** | Open Source | Rust | ✅ | Kernel isolation | ✅ | Portable kernel compartment |
| **Harness** | Research | Hypervisor | ✅ | AAOS protection | ✅ | Automotive kernel isolation |
| **RuntimeTrace** | Open Source | Python/eBPF | ✅ | Consistency checking | ✅ | Kernel/user-space discrepancies |
| **KSword** | Open Source | Windows/Qt | ✅ | Anti-rootkit | ✅ | Windows kernel research |
| **Endpoint Security AI** | Open Source | Python/FastAPI | (osquery) | AI EDR | ✅ | AI-driven threat detection |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source OS security or kernel research tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the open-source ecosystem:** The open-source landscape for **OS security and kernel research** is **fragmented across distinct research and operational layers**. **Warden** provides the most hardened open-source Linux EDR, with documented adversarial testing and eBPF-based kernel monitoring . **Wazuh** remains the most comprehensive open-source SIEM/XDR platform with rootkit detection and cross-platform support . **HakiOS** represents ambitious kernel porting research, running Darwin on Android hardware . **RustEKC** and **Harness** explore kernel isolation mechanisms for security-critical systems . **KSword** provides deep Windows kernel anti-rootkit analysis . **RuntimeTrace** and **Endpoint Security AI Agent** address specific detection and analysis workflows. No single open-source project replicates the full enterprise breadth of CrowdStrike or SentinelOne, but these tools cover the core kernel-level research, rootkit detection, and EDR workflows for self-hosted and research deployments.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
