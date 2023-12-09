# Optimize Ubuntu 22.04 for Speed

## Update and Upgrade

To ensure your Ubuntu 22.04 system is running with the latest software and security updates, it is crucial to regularly update and upgrade the installed packages. The `sudo apt update` command refreshes the package index, while `sudo apt upgrade` installs the latest versions of the installed packages. Keeping your system up-to-date not only provides access to new features but also addresses potential vulnerabilities, enhancing overall system stability and security.

```bash
sudo apt update
sudo apt upgrade
```

## Reduce Overheat

Overheating is a common concern, especially on laptops and devices with limited cooling capabilities. To mitigate this, installing TLP (Power Management) and CPUfreq (CPU frequency scaling) utilities can be beneficial. TLP optimizes power usage, extending battery life and reducing heat generation. The `cpufrequtils` package allows dynamic adjustment of CPU frequencies, managing power consumption based on system load. After installation, checking the status of TLP and CPUfrequtils services with `systemctl status` ensures that these utilities are actively managing power consumption.

```bash
sudo apt install tlp tlp-rdw
sudo apt install cpufrequtils
systemctl status tlp
systemctl status cpufrequtils
```

## Show System Information

Understanding how your system is utilizing resources is crucial for optimization. The `sudo tlp-stat -s` command provides detailed information about TLP settings, giving insights into power management configurations. Additionally, `cpufreq-info` displays information about the CPU frequency, which is valuable for assessing how the system dynamically adjusts CPU performance based on demand.

```bash
sudo tlp-stat -s
cpufreq-info
```

## Configure Pagination using Swap and Zram

Pagination strategies involving swap and Zram can significantly impact system performance, particularly in environments with limited RAM. If your system has 8GB of RAM, configuring a swap file and Zram can help manage memory efficiently.

### Swap File

Disabling existing swaps with `swapoff -a` allows for the creation of a new 8GB swap file using `fallocate`. The file permissions are then adjusted, and the file is formatted as swap before activation with `swapon`. Adding an entry to `/etc/fstab` ensures the swap persists across reboots.

```bash
sudo swapoff -a
sudo fallocate -l 8G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
# Only if needed, check /etc/fstab
# cat /etc/fstab
# sudo echo "/swapfile none swap sw 0 0" | sudo tee -a /etc/fstab
```

### Zram

Zram provides a compressed block device in RAM, acting as a swap space that can enhance performance. Installing `zram-tools` and configuring options in `/etc/default/zramswap` optimize Zram for your system. The recommended configuration includes the LZO compression algorithm (`ALGO=lzo`) and a compression ratio of 70% (`PERCENT=70`).

```bash
sudo apt install zram-tools
sudo vi /etc/default/zramswap
```

After configuration, verifying the status of the swap and Zram services with `systemctl status` and checking system information with commands like `zramctl`, `swapon -s`, and `free -h` ensures proper implementation and utilization.

```bash
systemctl status swapfile.swap
systemctl status zramswap
zramctl
swapon -s
free -h
```

## Delete Temporary Files in APT

Cleaning up temporary files generated during package installations is essential for maintaining a lean system. The `sudo apt autoclean && sudo apt clean && sudo apt autoremove` command sequence removes unnecessary package files, freeing up disk space. Regularly performing this maintenance task ensures a more efficient use of storage resources.

```bash
sudo apt autoclean && sudo apt clean && sudo apt autoremove
```

By following these steps, you can optimize your Ubuntu 22.04 system for speed, addressing performance considerations, power management, and resource utilization.

