# File Integrity Monitoring System Using Python

## 1. Project Overview

The **File Integrity Monitoring (FIM) System** is a Python-based security tool designed to monitor files and identify unauthorized or unexpected changes within a specified directory.

The system uses the SHA-256 cryptographic hashing algorithm to calculate file hashes and maintain a trusted baseline of file states. During subsequent scans, it compares the current file hashes against the stored baseline to identify modified, newly created, and deleted files.

The application also provides continuous monitoring through periodic directory scans and records detected events in a log file for future review.

## 2. Objectives

- Develop a Python-based file integrity monitoring solution.
- Calculate SHA-256 hashes to verify file integrity.
- Create and maintain a baseline of monitored files.
- Detect file modifications, new file creation, and file deletion.
- Provide manual and continuous monitoring options.
- Record detected security events in a log file.
- Provide a simple menu-driven interface for users.

## 3. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| hashlib | SHA-256 hash calculation |
| JSON | Baseline storage |
| pathlib | File and directory handling |
| logging | Security event logging |
| time | Periodic monitoring intervals |

**Operating System:** Windows

**External Dependencies:** No third-party Python packages are required. The project uses Python standard-library modules.

## 4. Project Features

### 4.1 SHA-256 File Hashing

The system calculates a SHA-256 hash for each monitored file. The hash represents the file's contents and is used to identify changes.

### 4.2 Baseline Creation

The application scans the selected directory and records the SHA-256 hash of each accessible file. The baseline is stored in JSON format.

File location:

`baseline/file_hashes.json`

### 4.3 File Modification Detection

The system compares the current hash of each existing file with its corresponding baseline hash. If the hashes differ, the file is reported as modified.

### 4.4 New File Detection

If a file exists in the monitored directory but is not present in the stored baseline, the application identifies it as a newly created file.

### 4.5 Deleted File Detection

If a file recorded in the baseline is missing from a completed directory scan, the application identifies it as deleted.

### 4.6 Continuous Monitoring

The application supports continuous monitoring by periodically scanning the monitored directory. The default scan interval is five seconds.

When a file change is observed, the system performs an integrity check against the stored baseline and displays the detected events.

### 4.7 Security Event Logging

Detected file integrity events are recorded in a log file with timestamps, severity levels, event types, and file paths.

Log location:

`logs/fim_alerts.log`

## 5. Project Structure

```text
File-Integrity-Monitoring-System/
│
├── main.py
├── file_hasher.py
├── baseline.py
├── monitor.py
├── alert_logger.py
│
├── baseline/
│   └── file_hashes.json
│
├── monitored_files/
│   └── test.txt
│
├── logs/
│   └── fim_alerts.log
│
├── screenshots/
│
├── README.md
└── requirements.txt
```

## 6. Module Description

| File | Description |
|---|---|
| `main.py` | Provides the menu-driven application and connects the project modules. |
| `file_hasher.py` | Calculates SHA-256 hashes for files. |
| `baseline.py` | Creates and stores the file integrity baseline. |
| `monitor.py` | Scans files and detects modifications, new files, and deletions. It also implements continuous monitoring. |
| `alert_logger.py` | Records detected integrity events in the log file. |

## 7. Installation and Execution

### Prerequisites

- Windows operating system.
- Python installed on the system.
- Visual Studio Code or another Python-compatible editor (optional).

### Step 1: Obtain the Project

Download or clone the project repository and open the project folder.

### Step 2: Open the Terminal

Open PowerShell or the integrated terminal in Visual Studio Code.

Navigate to the project directory:

```powershell
cd "File-Integrity-Monitoring-System"
```

### Step 3: Run the Application

Execute the following command:

```powershell
python main.py
```

## 8. Application Usage

The application provides the following menu options:

1. **Create File Integrity Baseline** – Scans the monitored directory and creates a baseline.
2. **Scan Files for Integrity Changes** – Performs a manual integrity scan.
3. **Start Continuous Monitoring** – Starts periodic monitoring with a default five-second interval.
4. **Update Baseline (Accept Current State)** – Replaces the existing baseline after user confirmation.
5. **Exit** – Closes the application.

### Monitoring Workflow

1. Create an initial baseline.
2. Start manual or continuous monitoring.
3. The system calculates the current file hashes.
4. Current file information is compared with the stored baseline.
5. Modified, new, and deleted files are identified.
6. Alerts are displayed in the terminal.
7. Detected events are recorded in the log file.

## 9. Testing and Results

The following test scenarios are used to verify the application's functionality.

| Test Case | Expected Result |
|---|---|
| Create initial baseline | File hashes are recorded in the JSON baseline. |
| Scan without changing files | No integrity changes detected. |
| Modify an existing file | Modified-file alert is displayed. |
| Create a new file | New-file alert is displayed. |
| Delete a baseline-recorded file | Deleted-file alert is displayed. |
| Start continuous monitoring | Changes are detected during periodic scans. |
| Check the alert log | Detected events are recorded with timestamps. |

## 10. Security Considerations and Limitations

- SHA-256 is used to identify changes in file contents.
- The baseline should be created from a trusted state.
- Updating the baseline accepts the current file state as the new reference.
- Continuous monitoring uses periodic scans rather than operating-system-level real-time file event notifications.
- Changes occurring and being reversed between scan intervals may not be detected.
- The baseline and log files should be protected against unauthorized modification or deletion.
- The system identifies integrity changes but does not determine whether a change was authorized or malicious.

## 11. Conclusion

The File Integrity Monitoring System demonstrates how Python can be used to implement a basic security monitoring solution for file integrity verification.

By using SHA-256 hashing, baseline comparison, change detection, continuous monitoring, and event logging, the application provides a practical way to identify changes within a monitored directory.

This project demonstrates the application of fundamental cybersecurity concepts, Python programming, file handling, cryptographic hashing, and security event monitoring.

## 12. Future Enhancements

- Integration with email or desktop notifications.
- Real-time file monitoring using operating-system event notifications.
- Monitoring multiple directories.
- Enhanced reporting and alert classification.
- Protection of baseline data through secure storage and access controls.
