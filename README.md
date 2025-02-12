<h2 align="center"> Memory Forensics Investigation with MemLabs </h2>

In this hands-on project, I will analyze memory dumps from **MemLabs**, a set of memory forensic challenges, to uncover malicious activities, extract indicators of compromise (IOCs), and solve scenario-based puzzles. This lab will demonstrate practical memory analysis skills using tools like Volatility, YARA, and Volatility3, while simulating a real-world incident response workflow.

The memory images used in this lab are sourced from [**MemLabs GitHub**](https://github.com/stuxnet999/MemLabs/blob/master/README.md), which provides realistic scenarios involving malware, data exfiltration, and anti-forensics techniques.


## **Overview**

* **Volatility3**: A memory forensics framework for analyzing processes, network artifacts, and kernel structures in memory dumps.

* **YARA**: A pattern-matching tool to detect malware signatures in memory.

* **Rekall**: An alternative memory analysis framework (optional).


## **Project Objectives**

* **Analyze memory dumps** to identify hidden processes, injected code, and malicious drivers.
* **Recover artifacts** such as exfiltrated files, command histories, and encryption keys.
* **Map findings** to attacker tactics using the MITRE ATT&CK framework.
* **Solve MemLabs challenges** by locating "flags" hidden in memory (e.g., `flag{...}`).


## **Prerequisites**
* **Basic knowledge of OS internals** (e.g., process trees, VAD entries).
* **Kali Linux or REMnux**: Preconfigured for forensics tools (Volatility, YARA, etc.).
* **Volatility3 installed**:
    
    ```bash
    git clone https://github.com/volatilityfoundation/volatility3.git
    pip install -r requirements.txt
    ```
    
- **MemLabs memory images**: Download from the [MemLabs repository](https://github.com/stuxnet999/MemLabs).

---
