# HandsonProject: Azure Databricks

Project Description: Build a data project using Databricks in Azure platform and other Azure tools/services such as Delta Lake, Unity Catalog, Azure Data Factory

Technologies used:  
- Azure Data Lake Storage to keep the data-
- Azure Data Factory to orchestrate some of the workflow
- Databricks Job Clusters which are created as part of the Databricks jobs. Databricks Cluster pools, they are created to speed up the cluster creation times. And finally, create the All Purpose Cluster

Solution Architecture:
Azure Databricks has 2 main components: Control Plane - Databricks subscription (Databricks cluster manager, Databricks UX, DBFS, Clusters) and Data Plane - Customer Subscription (Virtual network, Network security group for the virtual network, Azure blob storage for default storage, Databricks workspace)
Create Databricks resource
![image](https://github.com/britneydang/HandsonProject_RacingData/assets/110323703/4891c10f-9314-43f8-9b29-3ba4940fb6f8)

Databricks Clusters
- Cluster: a collection of Virtual Machines. In a cluster, there is a driver node which orchestrates the tasks performed by one or more worker nodes. Clusters allow us to treat this group of computers, as a single compute engine via the Driver node. 2 types of cluster:
    - all purpose cluster: created manually; persistent; suitable for interactive and adhoc workload; shared among others; expensive to run
    - job cluster: created by job; terminated at the end of the job; suitable for automated workload (ETL pipeline, ML workflow) at a regular interval; isolated just for the job; cheaper to run; great for repeated production workload.
- Cluster Pool: give user the ability to set aside some ready-to-use compute capacity, so that when user create an All Purpose Cluster, it can be created quickly. Usually when creating a Cluster, it takes about 5 to 6 minutes to spin up a Cluster. In order to speed up, can have a pool of resources waiting for which is Cluster Pool.

- Multi node: 1 driver node and 1 or more worker nodes
- Single node: only 1 driver node which acts as both driver and worker (not suitable for ETL workloads)

- Create cluster: Databricks workspace -> Compute -> all-purpose compute -> create compute ->
![image](https://github.com/britneydang/HandsonProject_RacingData/assets/110323703/bbc9625e-c953-4a82-b482-9084945d73eb)
- Create Cluster Pool: Compute -> Pools -> Create Pool

![image](https://github.com/britneydang/HandsonProject_RacingData/assets/110323703/fe2eb189-096d-4de2-9a33-510705133e73)
- Create All-purpose compute: Compute -> all-purpose compute -> create compute -> select the previous created pool for note type -> to test how long it take to create a cluster with and without a cluster pool.
- Create Policy -> to set something at a certain value so user cannot select other option. Script is written in JSON format
![image](https://github.com/britneydang/HandsonProject_RacingData/assets/110323703/a9eb7f25-c0ec-4cdf-b097-7820a6a2541d)
![image](https://github.com/britneydang/HandsonProject_RacingData/assets/110323703/d9addc84-cae1-48f9-99e6-5b86fa0a6138)

Databricks Notebooks: a Notebook is a collection of cells that run commands on a Databricks Cluster

- Make sure that the cluster is still running -> workspace -> create folder -> create notebook inside that folder -> select language 'Python' and select cluster
- Magic command: %sql/%scala/%python (to switch lanaguage within a cell), %md (markdown), %fs (view all available files), %sh (all processes are running in this cluster)
Databricks Utilities:
- File System Utilities: access databricks file system from a notebook and can use various file system level operations.
- Secrets Utilities: get secret values from secrets, which are stored in secret scopes backed by Databricksor Azure Key Vault.
- Widget Utilities: to parameterized notebooks so that a calling notebook or another application, for example, a Data Factory Pipeline can pass a parameter value to the notebook at runtime.
- Notebook Workflow Utilities: invoke one notebook from another and chain them together.

Access Azure Data Lake from Databricks:

- 


