# Network Device Scanner
<p align="center">
  <img src="Wallpaper.png" alt="description" style="width:40%; height:40%;">
</p>

A Python-based tool to scan and analyze devices on a local network using `nmap`. This script provides a menu-driven interface to perform standard, quick, detailed, or custom subnet scans, displaying device details such as IP addresses, MAC addresses, hostnames, vendors, operating systems, and open ports. Results are presented in a tabulated format and saved to a text file with a network topology map.

## Features

- **Multiple Scan Modes**:
  - **Standard Scan**: Balances speed and detail with OS and service detection.
  - **Quick Scan**: Fast ping scan to detect live hosts (no OS or port details).
  - **Detailed Scan**: Verbose scan with comprehensive OS and service information.
  - **Custom Subnet Scan**: Allows scanning a user-defined subnet (e.g., `/16`, `/24`, `/28`).
- **Output**:
  - Tabulated device list with IP, MAC, vendor, hostname, OS, and open ports.
  - ASCII-based network topology map centered around the gateway.
  - Results saved to a timestamped file (e.g., `network_scan_standard_2025-03-27_20-00-00.txt`).
- **Error Handling**: Saves errors to a file if the scan fails (e.g., missing permissions or dependencies).
- **UTF-8 Support**: Handles special characters in output files.

## Prerequisites

To run this script, you need the following installed on your system:

### Software
- **nmap**: A network scanning tool.
  - **Linux**: `sudo apt-get install nmap`
  - **macOS**: `brew install nmap`
  - **Windows**: Download and install from [nmap.org](https://nmap.org/download.html)
- **Python 3.x**: Ensure Python 3 is installed. Check with `python3 --version` or `python --version`.

### Python Packages (via `pip`)
"pip" is Python's package installer, used to install libraries required by this script. If you don’t have `pip`, install it via:
- **Linux/macOS**: `sudo apt-get install python3-pip` or `brew install python`
- **Windows**: Comes with Python installer (ensure "Add Python to PATH" is checked).

Install the required Python packages with:
```bash
pip install python-nmap tabulate
```
- **`python-nmap`**: A Python wrapper for `nmap` to perform network scans programmatically.
- **`tabulate`**: Formats scan results into readable tables.

### Permissions
- Run the script with **administrator/root privileges** for best results (e.g., `sudo` on Linux/macOS or as Administrator on Windows). This ensures access to raw sockets and accurate MAC address detection.

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/PyNetScan.git
   cd PyNetScan
   ```

2. Install dependencies:
   - Install `nmap` (see "Software" above).
   - Install Python packages:
     ```bash
     pip install -r requirements.txt
     ```
     If `requirements.txt` doesn’t exist, create it with:
     ```
     python-nmap
     tabulate
     ```
     Then run the command above.

3. Verify installations:
   - Check `nmap`: `nmap --version`
   - Check Python packages: `pip list | grep -E "python-nmap|tabulate"`

## Usage

1. Run the script:
   ```bash
   sudo python3 netscan.py
   ```
   - Use `sudo` on Linux/macOS or run as Administrator on Windows for full functionality.
   - Replace `python3` with `python` if that’s your system’s command for Python 3.

2. Menu Options:
   ```
   Network Device Scanner Menu
   ===========================
   1. Scan Network (Standard)
   2. Quick Scan
   3. Detailed Scan
   4. Custom Subnet Scan
   5. Help
   6. Exit
   ```
   - Enter a number (1-6) to select an option.
   - **Custom Subnet Scan**: Input a valid CIDR suffix (e.g., `/24`, `/16`, `/28`) when prompted.

3. Output:
   - The script displays scan progress and results in the terminal.
   - Results are saved to a file (e.g., `network_scan_standard_2025-03-27_20-00-00.txt`).
   - Errors, if any, are saved to a file (e.g., `network_scan_error_2025-03-27_20-00-00.txt`).

### Example
```bash
sudo python3 netscan.py
```
Select `1` for a standard scan. Output might look like:
```
Starting scan with machine IP: 192.168.1.100
Network range: 192.168.1.0/24
Scan in progress...
Scan completed!

Scan Time: 2025-03-27 20:00:00
Scanning network: 192.168.1.0/24
Your device IP: 192.168.1.100
==================================================
Network Devices Found:
+-----+---------------+-------------------+------------+---------+---------+-------------+-------------+
| seq | ip            | mac               | vendor     | name    | os      | os_version  | open_ports  |
+-----+---------------+-------------------+------------+---------+---------+-------------+-------------+
|   1 | 192.168.1.1   | 00:14:22:01:23:45 | Cisco Ltd  | router  | Unknown | Unknown     | 22, 80      |
|   2 | 192.168.1.100 | 00:16:17:02:34:56 | Dell Inc   | mypc    | Linux   | 5.x         | 22, 3389    |
+-----+---------------+-------------------+------------+---------+---------+-------------+-------------+

Network Topology Map:
┌──────────────┐
│  Gateway: 192.168.1.1  │
│   MAC: 00:14:22:01:23:45   │
└──────┬───────┘
       │
       ├── 1. 192.168.1.1 (00:14:22:01:23:45)
       │   ├── Vendor: Cisco Ltd
       │   ├── Hostname: router
       │   ├── OS: Unknown Unknown
       │   └── Open Ports: 22, 80
       │
       ├── 2. 192.168.1.100 (00:16:17:02:34:56)
       │   ├── Vendor: Dell Inc
       │   ├── Hostname: mypc
       │   ├── OS: Linux 5.x
       │   └── Open Ports: 22, 3389

Output saved to network_scan_standard_2025-03-27_20-00-00.txt
```

## Notes

- **MAC Address Detection**: May not work for devices behind routers, with firewalls, or without ARP responses.
- **Quick Scan**: Skips OS and port detection for speed.
- **File Encoding**: Uses UTF-8 to support special characters.
- **Troubleshooting**: If errors occur, check permissions, `nmap` installation, or network connectivity.

## Contributing

Feel free to submit issues or pull requests to improve this tool. Suggestions for additional scan types, better topology visualization, or enhanced error handling are welcome!

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### Explanation of "Pips" in the Context
In the README, I clarified that "pip" is Python's package installer, used to install `python-nmap` and `tabulate`. These are external libraries (not part of Python's standard library) required for the script to function:
- `python-nmap`: Interfaces with `nmap` to perform scans.
- `tabulate`: Formats the output into a neat table.

### Running the Code
The script (`netScan.py`) is ready to use as provided. Save it in a file named `netscan.py`, install the prerequisites as outlined in the README, and run it with:
```bash
sudo python3    
```
