# Splunk SIEM Setup on Ubuntu Desktop

## Overview

This project provides a comprehensive guide to setting up Splunk on an Ubuntu Desktop for basic Security Information and Event Management (SIEM) purposes. The setup involves installing Splunk, configuring it to monitor logs, and verifying data ingestion. This guide also includes troubleshooting tips and common issues encountered during setup.

## Installation

### 1. **Download and Install Splunk**

1. **Download the Splunk `.deb` Package**
   - Visit the official Splunk website and download the `.deb` package for Linux.
   - Example file: `splunk-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb`.

2. **Install the Package**
   - Run the following command to install Splunk:
     ```bash
     sudo dpkg -i splunk-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb
     ```
   - If you encounter errors related to dependencies, use the following command to resolve them:
     ```bash
     sudo apt-get install -f
     ```

### 2. **Start and Enable Splunk**

1. **Start Splunk**
   - Use the command below to start Splunk:
     ```bash
     sudo /opt/splunk/bin/splunk start
     ```

2. **Enable Splunk to Start on Boot**
   - To ensure Splunk starts automatically with the system, run:
     ```bash
     sudo /opt/splunk/bin/splunk enable boot-start
     ```

## Configuration

### 1. **Add a Sample Log File**

1. **Create a Sample Log File**
   - Create a directory and a log file to be monitored by Splunk:
     ```bash
     mkdir -p /home/charlie/sample_logs
     echo "Sample log entry" > /home/charlie/sample_logs/app.log
     ```

2. **Add the Log File to Splunk**
   - Use the following command to monitor the log file:
     ```bash
     sudo /opt/splunk/bin/splunk add monitor /home/charlie/sample_logs/app.log -sourcetype log -index main
     ```

### 2. **Verify Data Ingestion**

1. **Access the Splunk Web Interface**
   - Open your browser and navigate to:
     ```plaintext
     http://localhost:8000
     ```
   - Log in with the default or configured credentials.

2. **Search for the Ingested Logs**
   - Use the Splunk search bar to query:
     ```spl
     index=main
     ```
   - Verify that the sample logs are displayed in the search results.

## Troubleshooting and Caveats

### **1. Disk Space Issues**

- **Problem:** Errors related to insufficient disk space may occur if the VM's disk is too small.
- **Solution:** Ensure your VM has adequate disk space. For Splunk, at least 20 GB is recommended, but this may vary based on log volume.

### **2. VM Tools and Clipboard Issues**

- **Problem:** Issues with copying and pasting commands between host and VM.
- **Solution:** Install VMware Tools or open-vm-tools to enable clipboard sharing. Make sure these tools are up-to-date and properly installed.

### **3. Splunk Command Errors**

- **Problem:** Errors like "command not found" or issues with running Splunk commands.
- **Solution:** Verify the Splunk installation path and ensure the commands are correctly formatted. If the command is not found, check if Splunk was installed in a different directory.

### **4. Log File Monitoring Errors**

- **Problem:** Splunk does not display the log entries.
- **Solution:** Double-check the file path and ensure the log file has appropriate permissions. Confirm that the `-index` and `-sourcetype` parameters are correctly specified.

### **5. Splunk Web Interface Access**

- **Problem:** Cannot access the Splunk web interface.
- **Solution:** Ensure Splunk is running and that the correct port (8000) is open and accessible. Verify network settings and firewall configurations.

## Conclusion

This guide outlines the process of setting up Splunk on an Ubuntu Desktop and includes troubleshooting tips for common issues encountered during setup. Following these steps provides foundational knowledge of Splunk for SIEM purposes.

## Additional Notes

- Regularly update Splunk to the latest version to benefit from security patches and new features.
- Review Splunk's official documentation for advanced configuration and optimization tips.

---

Feel free to fork or clone this repository for your own use or contribute improvements.
