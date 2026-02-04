# Lab 3: Azure Databricks Platform Architecture

This lab explains the Azure Databricks architecture, including control plane, compute planes, and data integration.

![Control Plane](https://github.com/saliksalik/DATA-BRICKS/blob/main/03_Azure_Databricks_Platform_Architecture/outputs/control%20plane.png?raw=true)

## Azure Databricks Architecture Breakdown

### 1. Governance & Access Layer (Left Side)
This section defines how identities interact with the ecosystem.

- **Web Application User**: Accesses the UI via SSO (Single Sign-On) authentication through Microsoft Entra ID (formerly Azure AD).
- **REST API Client**: Used for automated workflows and CI/CD pipelines, authenticating via revocable tokens.

### 2. The Control Plane (Top Box)
Managed by Databricks within the Customer's Databricks Account. It serves as the "brain" of the operation.

- **Purpose**: Manages workspace notebooks, clusters, and jobs.
- **Databricks Web Application**: The primary GUI for users.
- **Notebooks**: The environment for collaborative coding and data exploration.
- **Jobs and Queries**: Orchestration for scheduled tasks and SQL workloads.
- **Cluster Management**: The backend service that handles the provisioning and scaling of compute resources.

### 3. The Compute Planes (Middle Section)
This is where the actual data processing occurs, split into two distinct types:

- **Serverless Compute Plane**: Contains compute resources for Serverless SQL Warehouses and Model Serving.
- **Classic Compute Plane (VNet)**: Resides within the Customer's Azure Subscription. It uses clusters and classic/pro SQL warehouses to process data.

### 4. Storage & Data Integration (Bottom Section)
The data persistence layer, largely residing in the customer's subscription.

- **Customer Data**: Stored in ADLS Gen2 or Blob Storage; accessed via direct connection or DBFS mount.
- **Workspace Root Storage**: A dedicated account for the Root DBFS (FileStore, libraries) and system data.
- **Note**: Workspaces created before March 6, 2023, use Blob Storage, while newer ones use ADLS Gen2.
- **External Data Sources**: Represents third-party or on-premises data connected to the Databricks environment.

### 5. Communication Flows (Arrows)
- **Command Flows (Orange/Red)**: "Launch clusters" and "Start jobs" signals sent from the Control Plane to the Classic Compute Plane.
- **Metadata/Telemetry Flows (Blue/Black)**:
  - Push/pull table metadata: Syncing the Hive metastore/catalog.
  - Push logging data: Moving Spark logs to the management layer for viewing.
  - Push/pull metadata: General workspace state synchronization.
  - Direct Uploads: Pathway for getting job results, cluster logs, and notebook revisions back to storage.

### 6. Security Note: Secure Cluster Connectivity
The diagram includes a specific technical footnote regarding connectivity:

- The red arrows (Launch/Start) represent logical requests.
- For workspaces with No Public IP (SCC), these requests utilize a tunnel initiated by the compute resources (clusters) within the VNet.
- This architecture ensures that compute resources in the classic plane do not require public IP addresses, enhancing the security posture.