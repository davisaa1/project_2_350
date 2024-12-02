# Apache Druid: Project 2 Overview

## Installation of Apache Druid on WSL

### Requirements for Installation
To install Apache Druid on Windows Subsystem for Linux (WSL), ensure the following prerequisites:
- **WSL installed and configured**: WSL2 is recommended for better performance.
- **Java Runtime Environment (JRE)**: Apache Druid requires Java 8 or Java 11. Install using:
  ```bash
  sudo apt update && sudo apt install openjdk-11-jdk
  ```
- **Curl or wget**: Required for downloading files.
- **Node.js**: Optional, for specific components or integrations.

### Installation Steps
1. **Download the Apache Druid distribution**:
   ```bash
   wget https://downloads.apache.org/druid/druid-<version>.tar.gz
   ```
2. **Extract the package**:
   ```bash
   tar -xvf druid-<version>.tar.gz
   ```
3. **Move to the extracted directory**:
   ```bash
   cd druid-<version>
   ```
4. **Start Druid services**:
   ```bash
   ./bin/start-micro-quickstart
   ```

## Main Purposes and Characteristics of Apache Druid
Apache Druid is a high-performance real-time analytics database designed for:
- **Interactive querying**: Optimized for slicing and dicing large datasets.
- **Real-time ingestion**: Supports streaming data input alongside batch loading.
- **Scalability**: Horizontally scalable architecture to handle high concurrency and large datasets.
- **Low-latency queries**: Uses a columnar storage format and indexing for faster data retrieval.

### Key Features
- **Time-based partitioning**: Ideal for time-series data.
- **Pluggable architecture**: Extensible with custom ingestion, query, and storage modules.
- **Built-in fault tolerance**: Uses a distributed system with high availability.

## Main Usage of Apache Druid
### Use Case: Analyzing Streaming Data
Below is an example of ingesting and querying data using Python:

1. **Install necessary libraries**:
   ```bash
   pip install pydruid pandas
   ```

2. **Ingest data into Druid**:
   Use the `data loader` interface in Druid or programmatically define ingestion specs.

3. **Query data**:
   ```python
   from pydruid.client import PyDruid
   from pydruid.utils.aggregators import count

   # Connect to Druid
   client = PyDruid('http://localhost:8888', 'druid/v2/sql')

   # Query data
   query = """
       SELECT timestamp, COUNT(*) as event_count
       FROM my_table
       WHERE timestamp >= CURRENT_TIMESTAMP - INTERVAL '7' DAY
       GROUP BY timestamp
       ORDER BY timestamp
   """
   result = client.sql(query)
   print(result)
   ```

### Visualization
Integrate with tools like Apache Superset or export data to visualization libraries in Python (e.g., Matplotlib).

## Shortcomings of the Current Version
- **Complex configuration**: Initial setup and configuration require significant manual effort.
- **Limited join support**: Druid's join operations are not as robust as traditional relational databases.
- **Cost of updates**: Real-time ingestion may require re-ingesting large portions of data for updates.
- **Resource-intensive**: Performance tuning may necessitate high hardware requirements.

## Plans for the Future
Apache Druid's roadmap includes:
- **Improved SQL capabilities**: Enhancements to query language support for complex joins and window functions.
- **Enhanced cloud-native features**: Improved integration with cloud storage and orchestration tools.
- **Streamlining ingestion pipelines**: Expanding support for newer streaming platforms and simplifying configurations.
- **Better multi-tenancy**: Introducing fine-grained access control and resource allocation mechanisms.

## Documentation Structure
- **README.md**: High-level overview guide.
- **InstallationAndRequirements.md**: Detailed installation instructions.
- **Usage.md**: Examples and best practices for querying and using Apache Druid.
- **Characteristics.md**: The key purposes and features of Apache Druid
- **SHORTCOMINGS.md**: Known issues and workarounds.
- **FUTURE_PLANS.md**: Summary of ongoing and future development goals.
