---
title: natural-language-processing
author: Jay Jo
date: 2024-03-23 00:00:00 +09:00
categories: [Tip]
tags: [tip]
---

# Python Package Installation Guide

## Creating and Activating a Virtual Environment

1. **Create a Virtual Environment:**  
   Open your terminal and execute the following command to create a virtual environment. Replace `myenv` with your preferred environment name.

   ```bash
   python3 -m venv myenv
   ```

2. **Activate the Virtual Environment:**  
   Activate the created virtual environment using the command below. The activation command differs based on the operating system:

   - On macOS or Linux:
     ```bash
     source myenv/bin/activate
     ```
   - On Windows:
     ```cmd
     myenv\Scripts\activate
     ```

   Once activated, your terminal prompt will change to indicate that you are in a virtual environment.

## Installing PyTorch

With the virtual environment activated, you can install PyTorch using pip:

```bash
(myenv) ➜  ~ pip3 install torch
```

This command will download and install PyTorch and its dependencies into your virtual environment.

## Verifying the Installation

After the installation is complete, you can verify the installation of PyTorch by executing:

```bash
(myenv) python -c "import torch; print(torch.__version__)"
```

If the installation was successful, this command will print the installed version of PyTorch.
