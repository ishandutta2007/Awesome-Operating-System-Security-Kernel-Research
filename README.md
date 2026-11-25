# Awesome Operating System Security & Kernel Research

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

> A curated list of top Operating System Security and Kernel Research platforms — comparing enterprise SaaS endpoint detection & response (EDR/XDR) suites and open-source tools for kernel-level security, eBPF telemetry, rootkit detection, vulnerability fuzzer analysis, and low-level OS internals research.

🌟 **Star this repository if you find it helpful!** 🌟

---

## 📑 Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS & Commercial Platforms](#-saas--commercial-platforms)
- [Open-Source Software & Research Tools](#-open-source-software--research-tools)
  - [osquery](#osquery)
  - [bcc (BPF Compiler Collection)](#bcc-bpf-compiler-collection)
  - [Wazuh](#wazuh)
  - [Atomic Red Team](#atomic-red-team)
  - [bpftrace](#bpftrace)
  - [Falco](#falco)
  - [Syzkaller](#syzkaller)
  - [Capa](#capa)
  - [Tetragon](#tetragon)
  - [Tracee](#tracee)
  - [Volatility 3](#volatility-3)
  - [HakiOS (hakios-xnu-kernel)](#hakios-hakios-xnu-kernel)
  - [Rekall](#rekall)
  - [AIDE](#aide)
  - [osquery-extensions](#osquery-extensions)
  - [chkrootkit](#chkrootkit)
  - [Warden](#warden)
  - [Endpoint Security AI Agent](#endpoint-security-ai-agent)
  - [RuntimeTrace](#runtimetrace)
  - [KSword](#ksword)
  - [RustEKC](#rustekc)
  - [Harness](#harness)
- [📊 Comparison at a Glance](#-comparison-at-a-glance)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## Sector Overview & Market Dynamics

The global **Endpoint Security and OS Protection** market is valued at approximately **$18.5 Billion in 2024** and is projected to expand to nearly **$38.5 Billion by 2030**, exhibiting a robust Compound Annual Growth Rate (CAGR) of ~12.5%. 

The market dynamics exhibit a **moderately concentrated hybrid structure**: the upper echelon is dominated by mega-cap technology conglomerates (such as Microsoft and Broadcom) and specialized cybersecurity giants (such as Palo Alto Networks and CrowdStrike) that command the majority of large enterprise deployments, while a diverse and fragmented long-tail of specialized EDR providers, MDR vendors, and open-source low-level kernel telemetry frameworks serve niche and emerging operational use cases.

---

## 🟦 SaaS & Commercial Platforms

Enterprise-grade, cloud-hosted operating system security, EDR, and kernel-level endpoint protection suites. Sorted by company size (valuation / market capitalization) in descending order:

| Platform | Company Size (Market Cap / Revenue) | Pricing (Specific Starting Tier) | Free Tier / Evaluation Limits | Key Kernel & Security Focus |
| :--- | :--- | :--- | :--- | :--- |
| **Microsoft Defender for Endpoint** | **$3.55T Market Cap** (~$318B Revenue; >$20B Security ARR) | **$3.00/user/month** (Plan 1 standalone) / **$5.20/user/month** (Plan 2 with full EDR) | **30-day free trial** (up to 25 evaluation licenses via Microsoft 365 Admin Center) | Integrated Windows/Linux/macOS kernel sensors, behavioral EDR, Attack Surface Reduction (ASR) rules, and automated investigation playbooks. |
| **Carbon Black Cloud** | **$1.42T Market Cap** (Broadcom parent; ~$63.9B total Revenue) | **$30.00/endpoint/year** (starting baseline estimate for Endpoint Standard tier) | **14 to 30-day vendor-assisted evaluation/PoC** upon enterprise request (no automated instant self-serve tier) | Deep continuous event recording at the kernel level, streaming behavioral prevention, tamper-resistant system auditing, and live response CLI. |
| **Palo Alto Cortex XDR** | **$231B Market Cap** (~$12.4B TTM Revenue) | **$40.00/endpoint/year** (Cortex XDR Prevent list baseline) / **$70.00/endpoint/year** (Cortex XDR Pro) | **30-day vendor-managed Proof of Concept (PoC)** upon enterprise sales request | Cross-data detection, kernel driver hooking & anti-tamper controls, exploit prevention modules, and cloud analytics. |
| **CrowdStrike Falcon** | **$52B Market Cap** (~$4.8B TTM Revenue) | **$59.99/device/year** (or **$7.99/device/month**) for entry Falcon Go tier | **15-day free trial** (Falcon Go / Pro with full Next-Gen Antivirus, USB Device Control, and Express Support; no credit card required) | AI-native endpoint protection with kernel-level driver sensors (`CSAgent`), zero-reboot architecture, and continuous telemetry. |
| **SentinelOne Singularity** | **$7.9B Market Cap** (~$1.0B TTM Revenue) | **$69.99/endpoint/year** (Singularity Core list baseline) | **14 to 30-day structured partner-led evaluation/PoC** (up to 60 days via authorized MSP/VAR channels) | Autonomous behavioral AI models operating at the kernel/OS layer, automated rollback, and real-time active containment without cloud round-trip. |
| **Trend Micro Apex One** | **$6.2B Market Cap** (~$1.8B TTM Revenue) | **$32.50/endpoint/year** (Apex One as a Service base volume license; ~₹1,500/seat/yr) | **30-day free trial** (Apex One as a Service cloud tenant evaluation) | Advanced malware analysis, kernel-level behavioral monitoring, virtual patching, and integrated endpoint detection & response. |
| **Sophos Intercept X** | **$3.9B Valuation** (Thoma Bravo; ~$1.0B ARR) | **$28.00/user/year** (baseline Intercept X Advanced license via authorized resellers) | **30-day free trial** (full access to Sophos Central management console and endpoint agents; instant online sign-up) | Deep learning neural network detection, CryptoGuard kernel anti-ransomware rollback, and exploit mitigation. |
| **Trellix Endpoint Security** | **~$1.5B Revenue** (Symphony Technology Group; FireEye + McAfee) | **$26.00/endpoint/year** (Trellix ENS Essentials starting list tier) | **60-day free trial** (provisions 5 evaluation endpoint licenses via Trellix ePO-SaaS) | Deep kernel telemetry, unified endpoint prevention (ENS), behavioral dynamic application containment, and adaptive threat defense. |
| **Bitdefender GravityZone** | **~$800M Valuation** (~$350M Revenue) | **$38.50/device/year** (Business Security tier at 10-seat baseline; promo rates often start at **$26.95/device/year**) | **30-day free trial** (unrestricted access to GravityZone Cloud Console for up to 100 endpoints) | Multi-layered kernel protection, HyperDetect tunable machine learning, fileless attack defense, and risk analytics. |
| **Cybereason** | **~$400M Valuation** (~$180M Revenue; LevelBlue acquisition) | **$72.00/endpoint/year** ($6.00/endpoint/month base EDR tier estimate) | **14 to 30-day structured Proof of Concept (PoC)** upon enterprise request | Malicious Operation (MalOp) graph engine, kernel sensor monitoring, and automated response orchestration. |

---

## 🟩 Open-Source Software & Research Tools

Self-hosted, community-driven frameworks, kernel introspection libraries, eBPF tracing tools, and OS security analysis engines. Sorted by GitHub star count in descending order:

### osquery
[![Stars](https://img.shields.io/github/stars/osquery/osquery?style=social&color=white)](https://github.com/osquery/osquery/stargazers)
- **Repository:** [osquery/osquery](https://github.com/osquery/osquery)
- **Stack:** C++ / SQLite / Multi-Platform | **License:** Apache-2.0
- **Overview:** Exposes an operating system as a high-performance relational database. Allows security researchers and incident responders to write SQL-based queries to inspect low-level OS internals, running processes, open network sockets, kernel modules, file hashes, and hardware devices across Linux, macOS, and Windows.

### bcc (BPF Compiler Collection)
[![Stars](https://img.shields.io/github/stars/iovisor/bcc?style=social&color=white)](https://github.com/iovisor/bcc/stargazers)
- **Repository:** [iovisor/bcc](https://github.com/iovisor/bcc)
- **Stack:** C / C++ / Python / eBPF | **License:** Apache-2.0
- **Overview:** Toolkit for creating efficient kernel tracing and manipulation programs using extended Berkeley Packet Filters (eBPF). Widely regarded as the foundational framework for Linux kernel observation, performance analysis, security auditing, and system-call interdiction with negligible performance overhead.

### Wazuh
[![Stars](https://img.shields.io/github/stars/wazuh/wazuh?style=social&color=white)](https://github.com/wazuh/wazuh/stargazers)
- **Repository:** [wazuh/wazuh](https://github.com/wazuh/wazuh)
- **Stack:** C / C++ / OpenSearch / Python | **License:** GPL-2.0
- **Overview:** Free and open-source unified XDR and SIEM platform. Provides an endpoint security agent that continuously monitors OS system calls, Windows Registry changes, file integrity (FIM), and active processes, while checking for rootkits, vulnerabilities, and policy compliance.

### Atomic Red Team
[![Stars](https://img.shields.io/github/stars/redcanaryco/atomic-red-team?style=social&color=white)](https://github.com/redcanaryco/atomic-red-team/stargazers)
- **Repository:** [redcanaryco/atomic-red-team](https://github.com/redcanaryco/atomic-red-team)
- **Stack:** YAML / PowerShell / Bash / Python | **License:** MIT
- **Overview:** Library of simple, open-source, automated tests mapped directly to the MITRE ATT&CK framework. Essential for testing whether OS security telemetry, kernel hooks, and EDR agents accurately detect adversarial behaviors and privilege escalation attempts.

### bpftrace
[![Stars](https://img.shields.io/github/stars/iovisor/bpftrace?style=social&color=white)](https://github.com/iovisor/bpftrace/stargazers)
- **Repository:** [iovisor/bpftrace](https://github.com/iovisor/bpftrace)
- **Stack:** C++ / LLVM / eBPF | **License:** Apache-2.0
- **Overview:** High-level tracing language for Linux eBPF inspired by awk, C, and DTrace. Enables researchers to inspect kernel probe points (`kprobes`), user space probes (`uprobes`), and kernel tracepoints on the fly without modifying kernel code or recompiling drivers.

### Falco
[![Stars](https://img.shields.io/github/stars/falcosecurity/falco?style=social&color=white)](https://github.com/falcosecurity/falco/stargazers)
- **Repository:** [falcosecurity/falco](https://github.com/falcosecurity/falco)
- **Stack:** C++ / eBPF / Lua | **License:** Apache-2.0
- **Overview:** De facto standard cloud-native runtime security tool created by Sysdig (CNCF graduated). Employs eBPF kernel drivers to intercept Linux system calls in real-time, matching them against customizable security rule sets to detect abnormal kernel behavior, unauthorized container execution, and privilege escalation.

### Syzkaller
[![Stars](https://img.shields.io/github/stars/google/syzkaller?style=social&color=white)](https://github.com/google/syzkaller/stargazers)
- **Repository:** [google/syzkaller](https://github.com/google/syzkaller)
- **Stack:** Go / C++ | **License:** Apache-2.0
- **Overview:** Unsupervised, coverage-guided kernel fuzzer developed by Google. Used globally by OS security teams to discover memory safety vulnerabilities, zero-day crashes, and race conditions in the Linux kernel, FreeBSD, NetBSD, OpenBSD, Windows, and Fuchsia.

### Capa
[![Stars](https://img.shields.io/github/stars/mandiant/capa?style=social&color=white)](https://github.com/mandiant/capa/stargazers)
- **Repository:** [mandiant/capa](https://github.com/mandiant/capa)
- **Stack:** Python / Rust | **License:** Apache-2.0
- **Overview:** Open-source identification tool from Mandiant that detects capabilities in executable files. Automatically tells you what a binary can do (e.g., inject code into kernel space, install services, bypass UAC, or evade detection) by comparing program structure against curated community rules.

### Tetragon
[![Stars](https://img.shields.io/github/stars/cilium/tetragon?style=social&color=white)](https://github.com/cilium/tetragon/stargazers)
- **Repository:** [cilium/tetragon](https://github.com/cilium/tetragon)
- **Stack:** C / Go / eBPF | **License:** Apache-2.0
- **Overview:** eBPF-based real-time security observability and runtime enforcement tool from Cilium. Inspects system calls, namespace transitions, and socket operations directly within the Linux kernel to enforce deep security boundaries and immediately terminate rogue processes.

### Tracee
[![Stars](https://img.shields.io/github/stars/aquasecurity/tracee?style=social&color=white)](https://github.com/aquasecurity/tracee/stargazers)
- **Repository:** [aquasecurity/tracee](https://github.com/aquasecurity/tracee)
- **Stack:** Go / C / eBPF | **License:** Apache-2.0
- **Overview:** Lightweight OS and container runtime security engine powered by eBPF from Aqua Security. Captures low-level operating system events and executes behavioral signature detection engines to catch malicious system modifications, rootkits, and container breakouts.

### Volatility 3
[![Stars](https://img.shields.io/github/stars/volatilityfoundation/volatility3?style=social&color=white)](https://github.com/volatilityfoundation/volatility3/stargazers)
- **Repository:** [volatilityfoundation/volatility3](https://github.com/volatilityfoundation/volatility3)
- **Stack:** Python | **License:** VSL (Volatility Software License)
- **Overview:** The world's most widely used memory forensics framework for extracting digital artifacts from volatile memory (RAM) dumps. Indispensable for kernel security researchers analyzing DKOM (Direct Kernel Object Manipulation), hidden drivers, injected threads, and advanced memory-resident rootkits.

### HakiOS (hakios-xnu-kernel)
[![Stars](https://img.shields.io/github/stars/oosexgang/hakios-xnu-kernel?style=social&color=white)](https://github.com/oosexgang/hakios-xnu-kernel/stargazers)
- **Repository:** [oosexgang/hakios-xnu-kernel](https://github.com/oosexgang/hakios-xnu-kernel)
- **Stack:** C / XNU (Darwin kernel) | **License:** APSL-2.0 / MIT
- **Overview:** Experimental research operating system project bringing Apple's Darwin (XNU) kernel to Android smartphone hardware. Allows low-level kernel researchers to explore cross-platform porting, hardware abstraction layers, custom bootloaders, and native Metal command models on Adreno GPUs.

### Rekall
[![Stars](https://img.shields.io/github/stars/google/rekall?style=social&color=white)](https://github.com/google/rekall/stargazers)
- **Repository:** [google/rekall](https://github.com/google/rekall)
- **Stack:** Python / C | **License:** Apache-2.0
- **Overview:** Advanced memory analysis and kernel incident response platform originally developed by Google. Provides an interactive exploration environment for physical memory analysis, page table translation, kernel object carving, and Windows/Linux kernel symbol resolution.

### AIDE (Advanced Intrusion Detection Environment)
[![Stars](https://img.shields.io/github/stars/aide/aide?style=social&color=white)](https://github.com/aide/aide/stargazers)
- **Repository:** [aide/aide](https://github.com/aide/aide)
- **Stack:** C | **License:** GPL-2.0
- **Overview:** Proven open-source host-based file and directory integrity checker (FIM). Creates a cryptographic baseline database of OS binaries, file attributes, extended attributes, and SELinux contexts, alerting administrators when system files or kernel binaries are altered.

### osquery-extensions
[![Stars](https://img.shields.io/github/stars/trailofbits/osquery-extensions?style=social&color=white)](https://github.com/trailofbits/osquery-extensions/stargazers)
- **Repository:** [trailofbits/osquery-extensions](https://github.com/trailofbits/osquery-extensions)
- **Stack:** C++ / Go / Python | **License:** Apache-2.0
- **Overview:** Curated collection of high-impact osquery plugins and extensions developed by Trail of Bits. Extends osquery with specialized tables for system introspection, binary analysis, dynamic firewall state evaluation, and low-level forensics data collection.

### chkrootkit
[![Stars](https://img.shields.io/github/stars/Magentron/chkrootkit?style=social&color=white)](https://github.com/Magentron/chkrootkit/stargazers)
- **Repository:** [Magentron/chkrootkit](https://github.com/Magentron/chkrootkit) (Official Mirror)
- **Stack:** Shell script / C | **License:** Open Source (chkrootkit license)
- **Overview:** Classical, lightweight Unix/Linux security scanner that inspects local system binaries for signs of rootkit modifications, promisc network interfaces, deleted utmp/wtmp logs, and Loadable Kernel Module (LKM) trojans.

### Warden
[![Stars](https://img.shields.io/github/stars/Spellskite-coding/Warden?style=social&color=white)](https://github.com/Spellskite-coding/Warden/stargazers)
- **Repository:** [Spellskite-coding/Warden](https://github.com/Spellskite-coding/Warden)
- **Stack:** Rust / eBPF / GTK4 | **License:** Open Source
- **Overview:** Hardened, autonomous EDR built in Rust specifically for Linux workstations. Leverages fanotify and custom eBPF probes (`warden-exec`, `warden-network`) to monitor execution anomalies, stop ransomware across multiple directory forks, and prevent privilege escalation via PID file-descriptor interdiction.

### Endpoint Security AI Agent
[![Stars](https://img.shields.io/github/stars/MuthoniGathiithi/endpoint-security-ai-agent?style=social&color=white)](https://github.com/MuthoniGathiithi/endpoint-security-ai-agent/stargazers)
- **Repository:** [MuthoniGathiithi/endpoint-security-ai-agent](https://github.com/MuthoniGathiithi/endpoint-security-ai-agent)
- **Stack:** Python / FastAPI / osquery / Docker | **License:** MIT
- **Overview:** Autonomous AI-driven EDR prototype designed to stop ransomware, Living-off-the-Land (LOLBAS) attacks, and C2 beaconing. Integrates osquery kernel telemetry tables with an interactive LLM natural-language incident analyst interface.

### RuntimeTrace
[![Stars](https://img.shields.io/github/stars/JackSessions/runtime-trace?style=social&color=white)](https://github.com/JackSessions/runtime-trace/stargazers)
- **Repository:** [JackSessions/runtime-trace](https://github.com/JackSessions/runtime-trace)
- **Stack:** Python / eBPF / Linux | **License:** Open Source
- **Overview:** Runtime cross-layer consistency checker powered by eBPF. Pinpoints stealth discrepancies between kernel state and user-space visibility, such as deleted running executables (`deleted_exe_running`) and hidden loadable kernel modules (LKMs).

### KSword
- **Repository:** AtomGit / Internal Research Mirror
- **Stack:** C++ / Windows Kernel Driver / Qt | **License:** Open Source
- **Overview:** Windows kernel anti-rootkit and low-level system inspection utility built on nested hypervisor virtualization (Intel VMX/EPT). Provides deep introspection into SSDT/SSSDT tables, inline/IAT/EAT hooks, ALPC communication, and driver object callouts.

### RustEKC
- **Repository:** Zenodo Research Artifact (USENIX)
- **Stack:** Rust / RISC-V64 / AArch64 | **License:** Open Source Research Artifact
- **Overview:** Embedded Kernel Compartment (EKC) implemented in Rust providing lightweight kernel isolation without requiring hardware virtualization modules or extended instruction-set architectures.

### Harness
- **Repository:** USENIX Security '25 Artifact
- **Stack:** C / Hypervisor / AOSP | **License:** Research Artifact
- **Overview:** Lightweight automotive hypervisor isolation framework that protects vehicle control signals and safety-critical subsystems from an untrusted Android Automotive Operating System (AAOS).

---

## 📊 Comparison at a Glance

| Software | Classification | Primary Stack | Kernel-Level Telemetry | Primary Focus | Deployment Model | Best For |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CrowdStrike Falcon** | Commercial SaaS | C++ / Cloud AI | ✅ Kernel Driver Sensor | Autonomous EDR / XDR | Cloud SaaS Agent | Enterprise SOCs & Threat Hunting |
| **SentinelOne Singularity**| Commercial SaaS | C++ / Python / AI | ✅ Behavioral Driver | Autonomous Endpoint Protection | Cloud SaaS Agent | Zero-touch Automated Rollback |
| **Microsoft Defender** | Commercial SaaS | C++ / Cloud / M365 | ✅ Native OS Sensors | Enterprise EDR / XDR | Cloud / OS Built-in | Microsoft 365 & Hybrid Estates |
| **Palo Alto Cortex XDR**| Commercial SaaS | C++ / Cloud | ✅ Driver Interception | Multi-Data Source XDR | Cloud SaaS Agent | Cross-domain Network + EDR SecOps |
| **osquery** | Open Source | C++ / SQLite | ✅ (via OS Tables) | SQL-based OS Introspection | Self-Hosted / Fleet | Endpoint Audit & Fleet Observability |
| **bcc** | Open Source | C / Python / eBPF | ✅ Deep eBPF Tracing | Linux Tracing & Interdiction | Self-Hosted CLI / Tools | Linux Kernel Developers & Performance |
| **Wazuh** | Open Source | C / C++ / OpenSearch | ✅ Syscall / FIM Monitoring | Unified Open Source XDR/SIEM | Self-Hosted Distributed | On-premise SIEM & Compliance |
| **Atomic Red Team** | Open Source | PowerShell / YAML | ❌ (Tests OS Sensors) | Attack Simulation (ATT&CK) | Standalone Scripts | Detection Engineering & Validation |
| **bpftrace** | Open Source | C++ / LLVM / eBPF | ✅ Dynamic kprobe/uprobe | High-level Kernel Tracing | Self-Hosted CLI | Live Kernel Debugging & Research |
| **Falco** | Open Source | C++ / eBPF | ✅ Syscall Interception | Cloud-Native Runtime Security | Self-Hosted Daemon / K8s | Container & Kernel Runtime Defense |
| **Syzkaller** | Open Source | Go / C++ | ✅ Syscall Fuzzing | Unsupervised Kernel Fuzzing | Self-Hosted Cluster | OS Kernel Vulnerability Research |
| **Capa** | Open Source | Python / Rust | ❌ (Static / Dynamic) | Binary Capability Detection | Self-Hosted CLI | Reverse Engineering & Malware Analysis |
| **Tetragon** | Open Source | C / Go / eBPF | ✅ Real-time Enforcement | eBPF Security Observability | Self-Hosted Daemon / K8s | In-kernel Policy & Process Killing |
| **Tracee** | Open Source | Go / C / eBPF | ✅ eBPF Event Tracing | Runtime Security & Forensics | Self-Hosted Daemon / K8s | Container Security & Behavioral Analysis |
| **Volatility 3** | Open Source | Python | ✅ Volatile RAM Forensics | Memory Forensics & Rootkits | Self-Hosted CLI | Incident Response & DKOM Rootkits |
| **HakiOS** | Open Source | C / Darwin XNU | ✅ Apple XNU Kernel | Darwin Kernel on Android | Bare-metal Phone / QEMU | Kernel Porting & Driver Internals |
| **AIDE** | Open Source | C | ❌ (Filesystem FIM) | File Integrity Monitoring | Self-Hosted Cron / Daemon | OS Tampering & Binary Verification |
| **Warden** | Open Source | Rust / eBPF | ✅ fanotify & eBPF | Linux Workstation EDR | Self-Hosted Standalone | Hardened Linux Desktop Protection |
| **chkrootkit** | Open Source | Shell / C | ⚠️ (Process/LKM Checks) | Rootkit Scanning | Self-Hosted Script | Quick Legacy Linux Rootkit Audits |
| **RuntimeTrace** | Open Source | Python / eBPF | ✅ Consistency Checking | Kernel vs User-space Delta | Self-Hosted CLI | Detecting Hidden Modules & Fileless Apps |
| **KSword** | Open Source | C++ / Windows Driver | ✅ Hypervisor VMX/EPT | Windows Kernel Anti-Rootkit | Self-Hosted Desktop App | Deep Windows Kernel Analysis & Hooks |

---

## 🤝 Contributing

Contributions are warmly welcome! If you know of an outstanding open-source OS security framework, eBPF tool, or kernel research project that should be added to this list:

1. Fork this repository.
2. Create a new branch: `git checkout -b feature/new-kernel-tool`
3. Add your entry following the established format:
   - Include a star badge linking to the repository's stargazers: `[![Stars](https://img.shields.io/github/stars/org/repo?style=social&color=white)](https://github.com/org/repo/stargazers)`
   - Include repository link, primary stack, license, and a concise 2–3 sentence description.
   - Insert it in the sorted order based on stargazers count.
4. Submit a Pull Request with a clear description of why the tool is valuable for OS security and kernel researchers.

---

## 📄 License

This list and documentation are released under the [Creative Commons Zero 1.0 Universal](LICENSE) (CC0 1.0) Public Domain Dedication. All listed commercial products and open-source software packages remain the copyrighted intellectual property and trademarks of their respective creators and owners.

---

⭐ **Found this resource useful for your research? Please consider starring this repository!** ⭐
