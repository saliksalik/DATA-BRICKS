# Lab 4: How to Create Spark Cluster

This lab guides you through creating an Azure Databricks cluster, including configuration options, cost considerations, and management.

## Step-by-Step Guide

### Step 1: Access Your Databricks Workspace
- Go to your Databricks workspace.


### Step 2: Navigate to the Compute Menu
- From the workspace, go to the **Compute** menu.
- Here you can create all-purpose clusters, job clusters, SQL warehouses, cluster pools, and security policies.

![Navigate to the Compute Menu](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Navigate%20to%20the%20Compute%20Menu.png?raw=true)

### Step 3: Click Create Cluster
- Hit the **Create Cluster** button to start creating an all-purpose cluster.

![Click Create Cluster](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Click%20Create%20Cluster.png?raw=true)

### Step 4: Name the Cluster
- Give a name to the cluster (e.g., "demo cluster").
- The default might be something like "Prashant Pandey's cluster" – change it as needed.

![Name the Cluster](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Name%20the%20Cluster.png?raw=true)

### Step 5: Choose Cluster Type
- Select **Multi-node** or **Single-node**.
  - Multi-node: Driver and executors run on separate machines.
  - Single-node: Driver and executors run on the same machine.

![Choose Cluster Type](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Choose%20Cluster%20Type.png?raw=true)

### Step 6: Select Access Mode
- Options: Single user, Shared, No isolation shared.
- Choose **Single user** for this lab.

![Select Access Mode](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Select%20Access%20Mode.png?raw=true)

### Step 7: Choose Databricks Runtime
- Go with the default runtime (latest with long-term support).
- Optionally, enable Photon acceleration for performance boost (extra cost) – remove it for learning purposes.

![Choose Databricks Runtime](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Choose%20Databricks%20Runtime.png?raw=true)

### Step 8: Select Worker Node Type
- Choose the VM size for workers.
- Minimum: 14 GB memory, 4 CPU cores.
- For learning, select the smallest size to keep costs low.
- Note: For multi-node, total cores = (workers + driver) * cores per node.

![Select Worker Node Type](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Select%20Worker%20Node%20Type.png?raw=true)

### Step 9: Configure Auto Scaling
- Enable Auto Scaling (default).
- Set minimum workers (e.g., 1) and maximum workers (e.g., 2).
- The cluster will scale up/down based on workload.

![Configure Auto Scaling](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Configure%20Auto%20Scaling.png?raw=true)

### Step 10: Set Auto Termination
- Enable auto termination (default).
- Set to 30 minutes (recommended for learning clusters to avoid costs).

![Set Auto Termination](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Set%20Auto%20Termination.png?raw=true)

### Step 11: Choose Driver VM
- Select the same size as workers (bare minimum for learning).

### Step 12: Add Tags (Optional)
- Add custom tags for metadata and reporting.

![Add Tags (Optional)](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Add%20Tags%20(Optional).png?raw=true)

### Step 13: Advanced Options (Optional)
- Configure Spark settings, environment variables, etc.
- Skip for now – Databricks sets good defaults.

![Advanced Options (Optional)](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Advanced%20Options%20(Optional).png?raw=true)

### Step 14: Review Estimated Cost
- Check the summary for estimated cost in DBU (Databricks Units).
- Typically 1-3 DBU per hour.
- DBU ≈ 1 USD; total cost includes DBU + Azure resources.

![Review Estimated Cost](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Review%20Estimated%20Cost.png?raw=true)

### Step 15: Account Limitations
- On Azure Free account: Max 4 CPU cores total.
- Can't create multi-node clusters (requires 12+ cores).
- Use single-node for free accounts.
- Upgrade to Pay-as-you-Go for multi-node.

### Step 16: Create the Cluster
- Click **Create Cluster**.
- Wait 5-7 minutes for launch.

![Create the Cluster](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Create%20the%20Cluster.png?raw=true)

### Step 17: Explore Cluster Tabs (Once Ready)
- **Notebooks**: Active notebooks attached to the cluster.
- **Libraries**: Install additional libraries.
- **Event Log**: Logs for start/stop events.
- **Spark UI**: Monitor jobs and performance.
- **Driver Logs**: stdout, stderr, log4j output.
- **Metrics**: Ganglia metrics UI.
- **Spark UI** (duplicate).

![Explore Cluster Tabs (Once Ready)](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Explore%20Cluster%20Tabs%20(Once%20Ready).png?raw=true)

### Step 18: Edit Cluster Configuration
- Use the **Edit** button to change settings (runtime, termination, node type).
- Some changes require restart.

### Step 19: Terminate the Cluster
- Click **Terminate** to stop the cluster.
- It won't delete resources immediately.

![Terminate the Cluster](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Terminate%20the%20Cluster.png?raw=true)

### Step 20: Permanently Delete the Cluster
- Go to **More** > Delete to remove permanently.
- This cleans up Azure resources (may take 10 minutes).

![Permanently Delete the Cluster](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Permanently%20Delete%20the%20Cluster.png?raw=true)

### Step 21: Verify in Azure Portal
- Check resources: VM, disks, NICs, public IP.
- Terminated clusters still show resources (small charges for disks/IP).
- Permanent deletion removes all.

![Verify in Azure Portal](https://github.com/saliksalik/DATA-BRICKS/blob/main/04_How_to_create_Spark_Cluster/outputs/Verify%20in%20Azure%20Portal.png?raw=true)

### Cost-Saving Tips
- Delete clusters after use to avoid charges.
- Use single-node for learning.
- Set short auto-termination.