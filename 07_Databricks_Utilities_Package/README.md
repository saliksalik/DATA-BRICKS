# Lab 7: Databricks Utilities Package

This lab introduces Databricks Utilities (dbutils), a package offering various utilities for interacting with the Databricks environment.

## Overview of Databricks Utilities

Databricks offers the following utilities:
- **credentials** - Show user roles and assume roles within a notebook
- **data** - Calculate statistics on a DataFrame and provide summaries
- **fs** - Interact with Databricks File System (DBFS)
- **jobs** - Interact with Databricks workflow jobs
- **library** - Locally compile applications using dbutils
- **meta** - Hook into the compiler
- **notebook** - Run chains of notebooks
- **preview** - Hidden utilities under preview
- **secrets** - Access secure credentials from within a notebook
- **widgets** - Create notebook parameters

> Most commonly used: **fs**, **notebook**, and **widgets**

---

## 1) Create a New Notebook
- Open Azure Databricks workspace.
- Create a new notebook for this lesson.
- Rename the notebook appropriately.

![Create Notebook](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Create%20Notebook.png?raw=true)

---

## 2) List Available Utilities
- Run the following command to see all available utilities:

```python
dbutils.help()
```

- Output shows all utility modules with descriptions.

![List Utilities](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/List%20Utilities.png?raw=true)

---

## 3) Get Help for Specific Utility
- View documentation for the FS utility:

```python
dbutils.fs.help()
```

- Get help for a specific command (e.g., cp):

```python
dbutils.fs.help("cp")
```

![FS Help](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/FS%20Help.png?raw=true)

---

## 4) File System Utility (fs)

### Using Magic Command vs dbutils
- Magic command approach:

```
%fs ls
```

- Equivalent dbutils approach:

```python
dbutils.fs.ls("/")
```

Both produce the same results but displayed differently.

![FS Magic vs Dbutils](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/FS%20Magic%20vs%20Dbutils.png?raw=true)

### Benefit of dbutils over Magic Commands
- dbutils integrates with Python code for more flexibility:

```python
# Loop through directories using dbutils
for item in dbutils.fs.ls("/"):
    print(item.name)
```

- This cannot be done with `%fs` magic command.

![FS Loop Example](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/FS%20Loop%20Example.png?raw=true)

### Common FS Commands
| Command | Description |
|---------|-------------|
| `cp` | Copy files |
| `head` | View first bytes of file |
| `ls` | List directory contents |
| `mkdir` | Create directory |
| `mv` | Move files |
| `put` | Write data to file |
| `rm` | Remove files |
| `mount` | Mount cloud storage (S3, ADLS) |

---

## 5) Notebook Utility

### View Notebook Utility Help
```python
dbutils.notebook.help()
```

Two main methods:
- **exit** - Return an exit code from the notebook
- **run** - Call a notebook from another notebook

![Notebook Help](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Notebook%20Help.png?raw=true)

### Create a Child Notebook
- Create a new notebook named "child_notebook".
- Add a print statement:

```python
print("I am a child notebook")
```

- Add exit command with return code:

```python
dbutils.notebook.exit("Success")
```

- Run to verify it works.

![Child Notebook](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Child%20Notebook.png?raw=true)

### Call Child Notebook from Parent
- In the parent notebook, add:

```python
result = dbutils.notebook.run("/path/to/child_notebook", 60)
print(result)
```

- Arguments:
  - First: Full path to child notebook
  - Second: Timeout in seconds
  - Third (optional): Parameters to pass

![Run Child Notebook](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Run%20Child%20Notebook.png?raw=true)

### View Child Notebook Execution
- Output shows:
  - Link to child notebook job
  - Exit code returned from child
- Click the link to see child notebook execution details.

![Child Notebook Output](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Child%20Notebook%20Output.png?raw=true)

---

## 6) Widget Utility (Parameters)

### View Widget Utility Help
```python
dbutils.widgets.help()
```

Available methods:
| Method | Description |
|--------|-------------|
| `text` | Create text input |
| `combobox` | Create combo box |
| `dropdown` | Create dropdown list |
| `multiselect` | Create multi-select list |
| `get` | Retrieve input value |
| `removeAll` | Remove all widgets |

![Widget Help](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Widget%20Help.png?raw=true)

### Create a Text Widget
- In the child notebook, add at the top:

```python
dbutils.widgets.text("input_value", "", "Enter a value")
```

- Arguments:
  - First: Variable name
  - Second: Default value (empty string)
  - Third: Label text

- Run the cell - a text box appears at the top of the notebook.

![Text Widget](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Text%20Widget.png?raw=true)

### Retrieve Widget Value
```python
input_val = dbutils.widgets.get("input_value")
print(f"I am a child notebook and received: {input_val}")
```

- If text box is empty, no value is printed.
- Enter a value in the text box and run again to see it.

![Get Widget Value](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Get%20Widget%20Value.png?raw=true)

### Pass Parameters from Parent Notebook
- Update the parent notebook to pass parameters:

```python
result = dbutils.notebook.run(
    "/path/to/child_notebook",
    60,
    {"input_value": "Hello from Parent!"}
)
print(result)
```

- Parameters passed as key-value pairs dictionary.

![Pass Parameters](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Pass%20Parameters.png?raw=true)

### Verify Parameter Passing
- Run the parent notebook.
- Click the child notebook job link.
- Output shows the value passed from parent.

![Parameter Output](https://github.com/saliksalik/DATA-BRICKS/blob/main/07_Databricks_Utilities_Package/outputs/Parameter%20Output.png?raw=true)

---

## Summary

| Utility | Purpose |
|---------|---------|
| **fs** | Interact with DBFS, mount cloud storage, integrate file operations with Python code |
| **notebook** | Chain notebooks together, return exit codes for success/failure checking |
| **widgets** | Add parameters to notebooks, pass values from parent to child notebooks |

### Key Takeaways
- `dbutils.help()` shows all available utilities
- `dbutils.<utility>.help()` shows methods for specific utility
- FS utility provides more flexibility than `%fs` magic command
- Notebook utility enables modular, reusable Spark applications
- Widget utility allows parameterized code execution

---

> **Note:** Screenshots referenced above should be added to the `outputs` folder to display properly.
