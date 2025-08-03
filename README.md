# Netinfo - Network Reporting Tool

`netinfo` is a simple Bash script designed to quickly generate a detailed report on a Linux system's network configuration. It gathers essential information for troubleshooting or simply checking your setup.

## Features

- **IP Addresses:** Displays IPv4 and IPv6 addresses for all network interfaces.
- **Routing Tables:** Presents both IPv4 and IPv6 routing tables.
- **DNS Servers:** Extracts configured DNS servers using `systemd-resolved`.
- **Firewall Status:** Detects and displays firewall rules, whether using **iptables** or **nftables**.
- **Exporting:** Allows you to export the report to a local text file or share it via a temporary link using `termbin.com`.

## Installation

To install the script and make it available as a system-wide command, follow these steps:

1.  Download the script and place it in the `/usr/local/bin/` directory:
    ```bash
    sudo mv netinfo.sh /usr/local/bin/netinfo
    ```
    *Note: The `.sh` extension is removed to allow for a cleaner command name.*

2.  Make the script executable:
    ```bash
    sudo chmod +x /usr/local/bin/netinfo
    ```

3.  (Optional) Change the owner to root to prevent unauthorized modifications:
    ```bash
    sudo chown root:root /usr/local/bin/netinfo
    ```

## Usage

Once installed, you can use the `netinfo` command directly from any directory.

-   **Standard Report:**
    ```bash
    netinfo
    ```

-   **Export to Text File:**
    ```bash
    netinfo txt
    ```
    Creates a file named `netinfo-[DATE]_[TIME].txt` in the current directory.

-   **Share via a Temporary Link:**
    ```bash
    netinfo nc
    ```
    This command uses `netcat` to send the report to `termbin.com`, which returns a shareable URL. This option requires the `netcat-openbsd` package.

## Dependencies

-   `iproute2` (usually pre-installed on most distributions)
-   `journalctl` (for DNS information)
-   `iptables` or `nftables` (depending on your system)
-   `netcat-openbsd`: This package is required only for the `netinfo nc` command. The script will attempt to install it automatically if you use this option.
