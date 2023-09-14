# SSH-connection-Between-2-VMs
To establish an SSH connection between an Ubuntu system and a Kali Linux system, you need to follow these steps. SSH (Secure Shell) is a secure protocol for remotely accessing and managing systems.

**1. Ensure SSH is Installed:**

First, ensure that SSH is installed on both your Ubuntu and Kali Linux systems. Typically, it is pre-installed, but if it's not, you can install it using the following commands:

For Ubuntu:

```bash
sudo apt update
sudo apt install openssh-server
```

For Kali Linux:

```bash
sudo apt update
sudo apt install openssh-server
```

**2. Start the SSH Service:**

The SSH service should start automatically after installation. However, you can manually start or restart it using the following commands:

On Ubuntu:

```bash
sudo systemctl start ssh
```

On Kali Linux:

```bash
sudo systemctl start ssh
```

**3. Find the IP Addresses:**

You'll need the IP address of both the Ubuntu and Kali Linux systems. You can find this information by running the following command on each system:

```bash
ip -a
```

Look for an IP address under the interface you are using (typically "eth0" for wired connections or "wlan0" for wireless connections).

**4. Connect from Ubuntu to Kali Linux:**

On your Ubuntu system, you can use the `ssh` command to connect to the Kali Linux system. Replace `username` with your Kali Linux username and `kali_ip_address` with the actual IP address of your Kali Linux system:

```bash
ssh username@kali_ip_address
```

For example:

```bash
ssh <username>@<IP>
```

**5. Authenticate:**

When you run the `ssh` command, you will be prompted to enter the password for the Kali Linux user account you specified. Enter the password, and if it's correct, you will be logged into the Kali Linux system via SSH.

**6. Secure Your Connection (Optional but Recommended):**

To enhance security, you can:

- Disable password authentication and use SSH keys for authentication. This involves generating an SSH key pair on your local machine and copying the public key to the `~/.ssh/authorized_keys` file on the remote server.

- Change the default SSH port (usually 22) to a non-standard port for added security.

- Configure firewall rules to allow SSH traffic only from trusted IP addresses.

Remember that SSH is a powerful tool, and securing it is crucial to prevent unauthorized access to your systems.

Please exercise caution and ensure you have proper authorization when connecting to remote systems, especially if you are working in a professional or corporate environment.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AFTER CONNECTING:
Create a dir in ubuntu and give following command as done un screenshot.....for transfering files rsync -rcavL <sorucefile> <username>@<IP>~/ pathtosavethefile
