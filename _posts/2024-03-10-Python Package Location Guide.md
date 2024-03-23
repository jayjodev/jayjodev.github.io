---
title: Python Installation and Package Location Guide
author: Jay Jo
date: 2024-03-10 00:00:00 +09:00
categories: [tip]
tags: [tip]
---

Follow these steps to determine how Python is installed on your system and where the Python packages are installed:

## 1. Find the Python Installation Path

To find out where Python is installed, use the command:

```bash
which python3
```

This command will return the path to the Python executable that is being used by default.

## 2. Determine the Python Version

Check the Python version to ensure you're working with the correct Python installation:

```bash
python3 --version
```

## 3. Locate the Installed Packages

To find out where Python packages are installed, use the `site` module:

```bash
python3 -m site
```

This command will list several directories, including where the global site-packages are located.

## 4. Find the Location of a Specific Package

To find out where a specific package is installed, use `pip show`:

```bash
pip3 show [package-name]
```

Replace `[package-name]` with the name of the package you're interested in. This command provides detailed information about the package, including its location on your system.


```
jupyter lab
```