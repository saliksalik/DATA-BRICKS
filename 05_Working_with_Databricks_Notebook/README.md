# Lab 5: Working with Databricks Notebook

This lab introduces Databricks Notebooks, covering creation, configuration, code execution, and key features.

## Step-by-Step Guide

### Step 1: Access Databricks Workspace
- Navigate to your Azure Databricks workspace home page.

### Step 2: Go to Workspace Menu
- Click the Workspace menu in the sidebar.
- Expand the workspace folder to see shared and user folders.

### Step 3: Create a New Folder
- Right-click the workspace directory.
- Select "Create" > "Folder".
- Name your folder (e.g., "exercises").

### Step 4: Create a New Notebook
- Right-click the new folder.
- Select "Create" > "Notebook".
- Databricks creates a notebook with a default name.

### Step 5: Rename the Notebook
- Change the default name to something meaningful.
- Note the default language (Python) next to the name.

### Step 6: Change Notebook Language (Optional)
- Click the language dropdown.
- Options: Python, SQL, Scala, R.
- Keep as Python.

### Step 7: Attach Notebook to Cluster
- Click the "Connect" button at the top.
- If no cluster, select "Create new resource".

### Step 8: Create a New Cluster
- Choose "Personal Compute" policy.
- Name the cluster.
- Select VM: 14 GB, 4 cores.
- Choose latest runtime.
- Review cost summary (low DBU).
- Click "Create".

### Step 9: Write Code in a Cell
- Click in the first cell (shows line number).
- Write Python code (e.g., `msg = "Hello World"`).

### Step 10: Run the Cell
- Press Ctrl+Enter or click the Run button.
- Output appears below the cell.

### Step 11: Add Another Cell
- Click below the first cell to add a new one.
- Write code to print the variable (e.g., `print(msg)`).
- Run it.

### Step 12: Check Cluster Status
- See cluster name and status at the top.

### Step 13: Explore Cluster Options
- Click the cluster dropdown.
- Options: Detach, restart, Spark UI, driver logs.

### Step 14: Use File Menu
- Access: New, Clone, Rename, Move, Delete, Export (as .dbc, .py, .ipynb, .html).

### Step 15: Use Edit Menu
- Cut, copy, paste cells; find/replace; format code; set indentation.

### Step 16: Use View Menu
- Switch views: Standard, Results Only, Side-by-Side.

### Step 17: Use Run Menu
- Run all, run above/below, clear outputs/state.

### Step 18: Use Help Menu
- Keyboard shortcuts (edit vs. command mode).

### Step 19: Explore Right Sidebar
- Comments, Experiments, Revision History, Variable Explorer, Python Libraries.

### Step 20: Check Libraries
- View installed libs: Notebook, Cluster, Runtime levels.

### Step 21: Return to Workspace Home
- Click Databricks logo.
- See recent items for quick access.