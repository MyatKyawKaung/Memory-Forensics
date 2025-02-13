Install stable version of volatility3

```
git clone https://github.com/volatilityfoundation/volatility3.git
```

![1](https://github.com/user-attachments/assets/d256bd34-6274-4f4c-9c59-0857d57e119b)

See available options:

```
python3 vol.py -h
```

For plugin specific options: run

```
vol.py <plugin> --help
```

![2](https://github.com/user-attachments/assets/5148a91e-5b4b-42ef-967d-7b2a160105f0)

Download and unzip the memory dump from MemLabs repository. Once its been extracted, we will start doing our investigation.

![3](https://github.com/user-attachments/assets/61d1a3d9-a0c6-481c-81f4-ded34c384402)

## **Memory Profile & OS Identification**

Use **windows.info** plugin **to** Identify OS version, architecture, and build without needing a "profile" (unlike Volatility 2). You can learn more about this on [“https://volatility3.readthedocs.io/en/v2.0.1/basics.html”](https://volatility3.readthedocs.io/en/latest/)

```
python3 vol.py -f <memory image> windows.info
```

![4](https://github.com/user-attachments/assets/ec27f5e4-d49c-49cf-bede-94de3dbc2409)
![5](https://github.com/user-attachments/assets/cb7c5735-fa63-4dda-af56-f73d2bf5bc15)


According to the volatility3 output, we will analyze the following fields to identify which machine is this memory dump is taken from. 

| Field Name | Value | Description |
| :---: | :---: | :---: |
| Kernel Base | 0xf8000261f000 | Memory address where the Windows kernel is loaded |
| layer_name | WindowsIntel32e | This means the memory image is from a 64-bit Intel system (Intel x86_64) |
| NTBuildLab | 7601.17514.amd64fre.win7sp1_rtm | This image is from Windows 7 SP1 (Service Pack 1), 64-bit, RTM (Release to Manufacturing) build 7601.17514 |
| KeNumberProcessors | 1 | The system has 1 CPU core |
| MachineType | 34404 (Decimal) | Machine Type field that identifies the target architecture |
| SystemTime | 2019-12-11 14:38:00 UTC | The date and time when the memory image was captured |
| NtSystemRoot | 	C:\Windows | The system's Windows installation path |
| NtProductType |	NtProductWinNt | Indicates this is a standard Windows NT-based system (workstation or server) |
| NtMajorVersion |	6 |  Windows major version |
| NtMinorVersion |	1 |  Windows minor version |

NtMajorVersion 6 and NtMinorVersion 1 confirm it’s Windows 7 or Server 2008 R2.

![6](https://github.com/user-attachments/assets/4cd96deb-c0c4-4ff7-9743-41fc0f047c43)

PE Machine  34404 → Portable Executable (PE) Machine Type field that identifies the target architecture.

![7](https://github.com/user-attachments/assets/b1f3af24-da1f-4c47-bf46-31457b18320c)
![8](https://github.com/user-attachments/assets/9ceafdab-419f-404f-9858-520dccf356b2)


**NTBuildLab** field and **7601.17514.amd64fre.win7sp1_rtm** value confirms the Windows 7 build.

![9](https://github.com/user-attachments/assets/12767657-fe23-475a-9acc-60820a64ca18)

Based on all the data, we can conclude this memory dump is taken from Windows 7 SP1 (64-bit) [Build 7601.17514] running on an x86-64 (AMD64) CPU with 1 core. It was captured on 11-December-2019, at 14:38 UTC

Reference: https://learn.microsoft.com/en-us/windows/win32/sysinfo/operating-system-version
