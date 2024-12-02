# Installation of Apache Druid on WSL

## Requirements for Installation
To install Apache Druid on Windows Subsystem for Linux (WSL), ensure the following prerequisites:

### Prerequisites
1. **WSL Installed and Configured**
   - Install WSL2 for better performance. Run the following command to set it up if not already done:
     ```bash
     wsl --install
     ```

2. **Java Runtime Environment (JRE)**
   - Apache Druid requires Java 8 or Java 11. Install JRE using:
     ```bash
     sudo apt update && sudo apt install openjdk-11-jdk
     ```

3. **Curl or wget**
   - Either tool is needed to download the Druid installation package.
   - Install wget if not available:
     ```bash
     sudo apt install wget
     ```

4. **Node.js (Optional)**
   - Node.js may be required for advanced components. Install if necessary:
     ```bash
     sudo apt install nodejs
     ```

## Installation Steps
1. **Download the Apache Druid Distribution**
   - Use wget to download the latest version:
     ```bash
     wget https://downloads.apache.org/druid/druid-<version>.tar.gz
     ```

2. **Extract the Package**
   - Unpack the tarball:
     ```bash
     tar -xvf druid-<version>.tar.gz
     ```

3. **Move to the Extracted Directory**
   - Navigate into the extracted files:
     ```bash
     cd druid-<version>
     ```

4. **Start Druid Services**
   - Run the micro-quickstart script to start the services:
     ```bash
     ./bin/start-micro-quickstart
     ```

5. **Verify Installation**
   - Open a browser and navigate to [http://localhost:8888](http://localhost:8888) to access the Druid console.

