---
title: "Resolving the 'zsh: command not found: go' Error on macOS After Installing Go with Brew"

author: Jay Jo
date: 2024-03-31 00:00:00 +09:00
categories: [tip]
tags: [tip]
---

After installing Go with Homebrew on macOS, if you encounter the `zsh: command not found: go` error, it likely means that the Go binary is not in your system's PATH. Here's how to troubleshoot and fix this issue.

## 1. Verify Go Installation

First, ensure that Go is indeed installed through Homebrew:

\`\`\`sh
brew list go
\`\`\`

If Go is listed, it means the installation was successful.

## 2. Locate Go Binary

Find out where Homebrew has installed Go:

\`\`\`sh
brew --prefix go
\`\`\`

This command should return the directory where Go is installed, like `/usr/local/opt/go`.

## 3. Update PATH

You need to add Go's binary directory to your PATH. If Go is installed in `/usr/local/opt/go`, its binaries are likely in `/usr/local/opt/go/bin`. Add this to your PATH in your `.zshrc` file.

Open your `.zshrc` file:

\`\`\`sh
nano ~/.zshrc
\`\`\`

Add the following line to the file:

\`\`\`sh
export PATH="/usr/local/opt/go/bin:$PATH"
\`\`\`

Save and close the file.

## 4. Apply Changes

Apply the changes to your current terminal session:

\`\`\`sh
source ~/.zshrc
\`\`\`

## 5. Verify PATH Update

Check if the PATH update is successful:

\`\`\`sh
echo $PATH
\`\`\`

You should see `/usr/local/opt/go/bin` in the output.

## 6. Test Go Command

Finally, test if the `go` command is recognized:

\`\`\`sh
go version
\`\`\`

This command should output the installed version of Go, confirming that the issue is resolved.
