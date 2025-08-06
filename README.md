# Splunk-Enterprise-Home-Lab
This home lab will be a demonstration of my literacy and knkowledge of the Splunk SIEM tool.

Notes (will turn this into a displayable project):

3 Important parts of Splunk:
- Forwarder
  - Sender of data
  - Lives on the machine its collecting log data from
  - Feeds raw data to the index
- Indexer
  - Proccesses incoming data from the forwarder
  - Stores events
  - Holds raw data
- Search Head
  - Executes your search requests
  - Where your SPL is inputted
  - The interface for searching through indexes

Different Types of Splunk Deployments:
1. Standalone - Single instance usually just downloaded on a local machine. No need for forwarders since Splunk is installed on the machine itself.
2. Basic - This is a biasic deployment of Splunk. This is installed on a local machine but the forwarder is installed on a remote machine elsewhere. Any and all data in this instance will come from the remote machine and not the local machine.
3. Multi-Instanace - Most companies utilize Splunk in this capacity. Each piece of the environment is separated meaning the Search Head, Indexer, and Forwarder are all using their own resources.

Clustering - A component cluster is a group of 3+ of the same component.
- an SH cluster would require a 1:1 replica of the other SH in the cluster. A deployer is used to manage the SH cluster.
- A Indexer cluster increases data availability by data replication. Think of this as a "Raid 5" for index storag. If one goes down, the other indexers carries a copy of all data.
- A forwarder clusuter would consist of a machines that have forwarders on them. This would require a deployment server to manage multiple forwarders.

Data Pipeline
1. Input - Forwarders have the data (Data = Streams)
2. Parsing - Processing of data (Data = Events)
3. License Usage - License meter check
4. Indexing - Data is written to disk (Data = Compressed)

Input Phase
- Files/Directories
- Network Traffic
- Log Files
- HEC

Source
- Path of the data
- Method to collect data

Host
- Who sent the data

Source Type
- Data format


<h2>Splunk Navigation</h2>
<h2></h2>
