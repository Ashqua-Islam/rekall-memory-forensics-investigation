# rekall-memory-forensics-investigation
# 🔍 Memory Forensics Investigation using Rekall

## 📌 Overview

This project presents a digital forensic investigation using the Rekall framework to analyze a memory dump and detect suspicious activities such as hidden processes, injected code, and possible malware behavior.

## 🎯 Scenario

A security breach was suspected at a company after unusual network activity was detected at 2:00 AM. No malware was found on disk, indicating a possible fileless attack.

## 🛠 Tools Used

* Rekall
* WinPmem
* Windows Memory Dump

## 🔎 Key Analysis Performed

### 1. Process Analysis

* Command: `pslist`
* Found suspicious process: **SEGameTool.exe**
* Possible use: loader or post-exploitation tool 

### 2. Memory Injection Detection

* Command: `malfind`
* Detected suspicious memory region in **msedgewebview2**
* Indicators:

  * EXECUTE_READWRITE permissions
  * Empty instructions (common in process hollowing) 

### 3. DLL Analysis

* Command: `dlllist`
* Suspicious DLL:

  * **DashboardWebView2Loader.dll**
* Possible DLL side-loading behavior 

### 4. Kernel Modules Analysis

* Command: `modules`
* Suspicious modules found outside standard directories
* Recommended verification of signatures 

### 5. Process Tree Analysis

* Command: `pstree`
* Findings:

  * uTorrent spawning multiple processes
  * Unusual behavior of msedgewebview2 instances
  * Suspicious process: browser_assist.exe 

### 6. Hidden Code Detection

* Command: `vadinfo`
* Found manually mapped code regions indicating possible malware execution 

### 7. Orphan Threads Analysis

* Command: `orphan_threads`
* Indicators:

  * RWX permissions
  * Private memory (not linked to disk)
* Suggests code injection or shellcode 

### 8. Kernel Hook Detection

* Command: `ssdt`
* Possible rootkit activity detected 

### 9. Handles Analysis

* Command: `handles`
* Suspicious access to system resources observed 

##  Conclusion

The investigation strongly indicates:

* Presence of injected or hollowed processes
* Suspicious process behavior
* Possible fileless malware activity

##  Full Report

Refer to `report.pdf` for complete analysis.


## 📚 Skills Demonstrated

* Memory Forensics
* Cybersecurity Investigation
* Incident Response
* Malware Analysis

