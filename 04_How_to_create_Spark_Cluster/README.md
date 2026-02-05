# Lab 4: How to Create Spark Cluster

This lab guides you through creating an Azure Databricks cluster, including configuration options, cost considerations, and management.

## Step-by-Step Guide

### Step 1: Access Your Databricks Workspace
- Go to your Databricks workspace.
- This is the starting point for most lectures.

### Step 2: Navigate to the Compute Menu
- From the workspace, go to the **Compute** menu.
- Here you can create all-purpose clusters, job clusters, SQL warehouses, cluster pools, and security policies.

### Step 3: Click Create Cluster
- Hit the **Create Cluster** button to start creating an all-purpose cluster.

### Step 4: Name the Cluster
- Give a name to the cluster (e.g., "demo cluster").
- The default might be something like "Prashant Pandey's cluster" – change it as needed.

### Step 5: Choose Cluster Type
- Select **Multi-node** or **Single-node**.
  - Multi-node: Driver and executors run on separate machines.
  - Single-node: Driver and executors run on the same machine.

### Step 6: Select Access Mode
- Options: Single user, Shared, No isolation shared.
- Choose **Single user** for this lab.

### Step 7: Choose Databricks Runtime
- Go with the default runtime (latest with long-term support).
- Optionally, enable Photon acceleration for performance boost (extra cost) – remove it for learning purposes.

### Step 8: Select Worker Node Type
- Choose the VM size for workers.
- Minimum: 14 GB memory, 4 CPU cores.
- For learning, select the smallest size to keep costs low.
- Note: For multi-node, total cores = (workers + driver) * cores per node.

### Step 9: Configure Auto Scaling
- Enable Auto Scaling (default).
- Set minimum workers (e.g., 1) and maximum workers (e.g., 2).
- The cluster will scale up/down based on workload.

### Step 10: Set Auto Termination
- Enable auto termination (default).
- Set to 30 minutes (recommended for learning clusters to avoid costs).

### Step 11: Choose Driver VM
- Select the same size as workers (bare minimum for learning).

### Step 12: Add Tags (Optional)
- Add custom tags for metadata and reporting.

### Step 13: Advanced Options (Optional)
- Configure Spark settings, environment variables, etc.
- Skip for now – Databricks sets good defaults.

### Step 14: Review Estimated Cost
- Check the summary for estimated cost in DBU (Databricks Units).
- Typically 1-3 DBU per hour.
- DBU ≈ 1 USD; total cost includes DBU + Azure resources.

### Step 15: Account Limitations
- On Azure Free account: Max 4 CPU cores total.
- Can't create multi-node clusters (requires 12+ cores).
- Use single-node for free accounts.
- Upgrade to Pay-as-you-Go for multi-node.

### Step 16: Create the Cluster
- Click **Create Cluster**.
- Wait 5-7 minutes for launch.

### Step 17: Explore Cluster Tabs (Once Ready)
- **Notebooks**: Active notebooks attached to the cluster.
- **Libraries**: Install additional libraries.
- **Event Log**: Logs for start/stop events.
- **Spark UI**: Monitor jobs and performance.
- **Driver Logs**: stdout, stderr, log4j output.
- **Metrics**: Ganglia metrics UI.
- **Spark UI** (duplicate).

### Step 18: Edit Cluster Configuration
- Use the **Edit** button to change settings (runtime, termination, node type).
- Some changes require restart.

### Step 19: Terminate the Cluster
- Click **Terminate** to stop the cluster.
- It won't delete resources immediately.

### Step 20: Permanently Delete the Cluster
- Go to **More** > Delete to remove permanently.
- This cleans up Azure resources (may take 10 minutes).

### Step 21: Verify in Azure Portal
- Check resources: VM, disks, NICs, public IP.
- Terminated clusters still show resources (small charges for disks/IP).
- Permanent deletion removes all.

### Cost-Saving Tips
- Delete clusters after use to avoid charges.
- Use single-node for learning.
- Set short auto-termination.