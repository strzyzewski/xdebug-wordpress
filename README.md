# Docker XDebug Installer for WordPress

This repository contains a script that makes it easy to install and configure XDebug on a WordPress Docker container.

## Prerequisites

- Docker installed and running
- A running Docker container which is based on or derived from the standard WordPress image (see https://hub.docker.com/_/wordpress)

## Usage

1. Make the script executable: `chmod +x xdebug-start`

2. Run the script and provide your WordPress container name as an argument: `./xdebug-start your_container_name`

3. The script will install Xdebug, configure it for debugging and development, set the client host, and set it to start with every request (no need for a trigger). The script sets port 9003 for XDebug. Feel free to change the port to anything you like, but don't forget to configure your debugger client accordingly. 

4. After the script is executed successfully, Xdebug will be installed and configured in your WordPress container. Now, you can use your favorite IDE (e.g. Visual Studio Code) to start debugging your PHP code. A sample configuration for VS Code is provided in the folder .vscode.

## Running on WSL (Windows Subsystem for Linux)

You might encounter connectivity issues between the container and your debugger. Windows Firewall tends to block relevant traffic for XDebug from WSL. 
Try running the following command in a **PowerShell** terminal with administrative privileges:

`New-NetFirewallRule -DisplayName "WSL" -Direction Inbound  -InterfaceAlias "vEthernet (WSL)"  -Action Allow`
