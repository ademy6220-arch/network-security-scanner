# Multi-Language Network & Security Scanner

A modular security toolkit combining **Rust**, **C# (.NET)**, and **Nmap** to perform fast network scans, backup discovery, proxy validation, and firewall detection with database logging.

---

## 🛠️ Features & Structure

### 1. 🦀 Rust Scanner (`/rust-scanner`)
* **Asynchronous IP & Port Scanner:** Built with `tokio` for high-performance concurrent port scanning.
* **Backup Finder:** Recursively scans a target directory for sensitive backup file extensions (`.bak`, `.zip`, `.sql`, etc.).
* **Proxy Validator:** Tests HTTP/SOCKS5 proxies to check if they are active and secure.

### 2. ⚡ C# Scanner (`/csharp-scanner`)
* **Firewall Detection:** Analyzes socket connection behavior (timeouts vs. active resets) to determine if a port is actively filtered by a firewall.
* **SQLite Database Integration:** Automatically saves every scan result with a timestamp in a local `scan_results.db` database.

### 3. 🔍 Nmap Scripts (`/nmap-scripts`)
* Pre-configured shell scripts to perform deep TCP-ACK and FIN scans to map out active firewall rules and bypass basic packet filters.

---

## 🚀 How to Run

### Rust Scanner
Ensure you have [Rust](https://rustup.rs/) installed.
```bash
cd rust-scanner
cargo run
C# ScannerEnsure you have the .NET SDK installed.Bashcd csharp-scanner
dotnet run
Nmap ScansRun the firewall mapping commands (requires Nmap installed):Bashchmod +x nmap-scripts/firewall_scans.sh
./nmap-scripts/firewall_scans.sh <target-ip>
📊 Database Schema (SQLite)The C# scanner automatically creates and writes to a database with the following structure:ColumnTypeDescriptionIdINTEGERPrimary Key (Auto-Increment)IPTEXTScanned Target IPPortINTEGERScanned PortStatusTEXTOpen / Closed / Filtered (Firewall)TimestampDATETIMETime of the scanDisclaimer: This tool is intended for educational and authorized security testing purposes only.
