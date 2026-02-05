# Lab 6: Notebook Magic Commands

This lab introduces Databricks Notebook Magic Commands, allowing multi-language code execution and utilities.

## Step-by-Step Guide

### Step 1: Access Databricks Workspace and Open Notebook
- Navigate to the workspace home page.
- Open an existing notebook created in the previous lab.

### Step 2: Check Default Notebook Language
- See the default language (e.g., Python) at the top.
- Click to change if needed, but keep as Python.

### Step 3: Mix Languages with Magic Commands
- Use magic commands to run code in other languages within the same notebook.

### Step 4: Use %sql Magic Command
- Type %sql in a cell to switch to SQL mode.
- Write SQL expressions.

### Step 5: Run SQL Code
- Execute the cell to run SQL (e.g., simple SELECT).

### Step 6: Use %scala Magic Command
- Type %scala to run Scala code in a cell.

### Step 7: Use %python Magic Command (Optional)
- Type %python to explicitly run Python (not needed in Python notebooks).

### Step 8: Use %md for Markdown
- Type %md to create documentation cells with Markdown.

### Step 9: Write and Run Markdown
- Add notes, links, or formatting; run to render.

### Step 10: Use %fs for File System Commands
- Type %fs to run DBFS commands (e.g., ls for listing files).

### Step 11: Explore Pre-loaded Datasets
- List files in DBFS directories (e.g., airlines dataset).

### Step 12: Use %sh for Shell Commands
- Type %sh to run Linux shell commands (e.g., tail).

### Step 13: List All Magic Commands
- Use %lsmagic to see available commands.

### Step 14: Get Help on Magic Commands
- Append ? to a command (e.g., %pip?) for documentation.
- Use ?? for source code.

### Step 15: Run Entire Notebook
- Click "Run All" to execute all cells in sequence.