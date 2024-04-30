---
title: Creating and Activating a Virtual Environment
author: Jay Jo
date: 2024-03-23 00:00:00 +09:00
categories: [tip]
tags: [tip]
---

1. **Create a Virtual Environment:**  
   Open your terminal and execute the following command to create a virtual environment. Replace `myenv` with your preferred environment name.

   ```bash
   python3 -m venv ~/myenv
   ```

2. **Activate the Virtual Environment:**  
   Activate the created virtual environment using the command below. The activation command differs based on the operating system:

   - On macOS or Linux:
     ```bash
     source ~/myenv/bin/activate
     ```

   Once activated, your terminal prompt will change to indicate that you are in a virtual environment.

   ```
   python3 -m venv ~/myenv
   source ~/myenv/bin/activate
   (myenv) ➜ pip3 install torch
   ```

3. **Deactivate the Virtual Environment:**  

   - On macOS or Linux:
     ```bash
     deactivate
     ```

## 4. Installing PyTorch

With the virtual environment activated, you can install PyTorch using pip:

```bash
(myenv) ➜  ~ pip3 install torch
```

This command will download and install PyTorch and its dependencies into your virtual environment.

## 5.  Verifying the Installation

After the installation is complete, you can verify the installation of PyTorch by executing:

```bash
(myenv) python -c "import torch; print(torch.__version__)"
```

If the installation was successful, this command will print the installed version of PyTorch.


## 6. Locate the Installed Packages

To find out where Python packages are installed, use the `site` module:

```bash
(myenv) ➜  python3 -m site
```

This command will list several directories, including where the global site-packages are located.

## 7. Find the Location of a Specific Package

To find out where a specific package is installed, use `pip show`:

```bash
(myenv) ➜ ~ pip3 show [package-name]

(myenv) ➜  ~ pip3 show torch
Name: torch
Version: 2.2.1
Summary: Tensors and Dynamic neural networks in Python with strong GPU acceleration
Home-page: https://pytorch.org/
Author: PyTorch Team
Author-email: packages@pytorch.org
License: BSD-3
Location: /Users/jayjo/myenv/lib/python3.12/site-packages
Requires: filelock, fsspec, jinja2, networkx, sympy, typing-extensions
Required-by: 

```

Replace `[package-name]` with the name of the package you're interested in. This command provides detailed information about the package, including its location on your system.
