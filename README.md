# NetProbe: Python Network Diagnostic Tool

A lightweight, automated script for server health checks. It analyzes TCP/IP connectivity, scans critical service ports, and generates structured reports for system administration.

**Key Feature:** Uses TCP handshakes for connectivity checks, allowing it to function in restricted environments (Google Colab, Docker containers) where standard ICMP `ping` is blocked.

## Features

* **Reliable Connectivity:** Falls back to TCP connections (Port 80/443) if OS-level ping is missing.
* **Concurrency:** Multi-threaded port scanning for high performance.
* **Reporting:** clean Pandas DataFrame output.
* **Alerting:** Built-in stub for SMTP email notifications on failure.

## Installation

1. Clone the repository:
```bash
git clone https://github.com/saltfry/NetProbe.git

```


2. Install the required package:
```bash
pip install pandas

```



## Configuration & Usage

Open the script and modify the `TARGETS` list and `PORTS_TO_SCAN` dictionary at the top of the file:

```python
TARGETS = ['google.com', '192.168.1.50']

PORTS_TO_SCAN = {
    22: 'SSH',
    80: 'HTTP',
    443: 'HTTPS'
}

```

Run the script in a Python environment or Jupyter Notebook:

```python
health_report = run_network_diagnostic(TARGETS)
print(health_report)

```

## Sample Output

| Target | Ping_Status | Port | Service | Port_Status |
| --- | --- | --- | --- | --- |
| google.com | Online | 443 | HTTPS | OPEN |
| 192.168.1.50 | Offline | N/A | N/A | Unreachable |

## License

MIT License
