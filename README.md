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
Another way to transfer files between your Ubuntu and Kali Linux systems after establishing an SSH connection is by using the `rsync` command. `rsync` is a powerful and versatile file synchronization and transfer tool that works well over SSH. Here's how you can use it:

**On Ubuntu (source system):**

1. Open a terminal on your Ubuntu system.

2. Use the `rsync` command to transfer files from your local system to the Kali Linux system. Replace `local_file` with the path to the file you want to transfer, `username` with your Kali Linux username, and `kali_ip_address` with the IP address of your Kali Linux system. Also, specify the destination directory on the Kali Linux system:

   ```bash
   rsync -avz -e ssh local_file username@kali_ip_address:/path/to/destination/directory/
   ```

   For example:

   ```bash
   rsync -avz -e ssh file.txt Username@IP:/home/FolderName/
   ```

   - `-avz` stands for:
     - `a`: Archive mode (preserves file permissions, ownership, and timestamps).
     - `v`: Verbose mode (shows detailed progress).
     - `z`: Compresses data during transfer, which can be beneficial for large files.

3. You will be prompted to enter the password for your Kali Linux user account. After providing the correct password, `rsync` will transfer the file to the specified directory on the Kali Linux system.

**On Kali Linux (destination system):**

To transfer files from the Kali Linux system to your Ubuntu system using `rsync`, reverse the source and destination in the `rsync` command:

```bash
rsync -avz -e ssh username@kali_ip_address:/path/to/remote/file.txt /path/to/local/destination/
```

For example:

```bash
rsync -avz -e ssh username@IP:/home/FolderName/file.txt /path/to/local/destination/
```

`rsync` is a versatile tool and provides various options for transferring files efficiently and securely. It's particularly useful when you need to synchronize directories or transfer multiple files.
