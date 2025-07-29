# IDM Activation Script (IAS)

[![Version](https://img.shields.io/badge/version-1.5-blue.svg)](https://github.com/jcrvnx/idm-activation)
[![Windows](https://img.shields.io/badge/Windows-7%2B-green.svg)](https://github.com/jcrvnx/idm-activation)
[![License](https://img.shields.io/badge/License-Open%20Source-blue.svg)](https://github.com/jcrvnx/idm-activation)

> **A powerful and comprehensive tool for managing Internet Download Manager (IDM) activation and trial periods on Windows systems.**

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Command Line Options](#command-line-options)
- [How It Works](#how-it-works)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [Disclaimer](#disclaimer)
- [Credits](#credits)

## 🎯 Overview

**IDM Activation Script (IAS)** is an open-source Windows batch script designed to provide advanced management capabilities for Internet Download Manager (IDM). Originally created by [WindowsAddict](https://github.com/WindowsAddict), this fork is maintained by [Jcrist Vincent Orhen](https://github.com/jcrvnx) with ongoing improvements and updates.

The script offers multiple activation methods and comprehensive registry management to ensure optimal IDM functionality while respecting software licensing.

## ✨ Features

### 🔧 Core Functionality
- **Freeze Trial**: Extends the 30-day trial period indefinitely
- **Activation**: Provides full activation capabilities (with fallback recommendations)
- **Reset**: Complete cleanup of activation and trial data
- **Registry Management**: Advanced CLSID registry key manipulation
- **Backup System**: Automatic backup creation before modifications

### 🛡️ Advanced Capabilities
- **Multi-Architecture Support**: x86, x64, ARM32, and ARM64 compatibility
- **Cross-Platform Detection**: Automatic architecture detection and process elevation
- **Registry Synchronization**: Handles HKCU/HKU synchronization issues
- **Permission Management**: Advanced registry permission handling
- **Error Recovery**: Comprehensive error handling and recovery mechanisms

### 🔍 System Integration
- **WMI Integration**: Windows Management Instrumentation support
- **PowerShell Integration**: Advanced PowerShell scripting capabilities
- **Service Validation**: Null service verification for stability
- **Internet Connectivity**: Automatic connectivity testing
- **Update Checking**: Built-in version update detection

### 🎨 User Experience
- **Interactive Menu**: User-friendly console interface
- **Color Support**: Enhanced visual feedback with color coding
- **Progress Indicators**: Real-time operation status
- **Unattended Mode**: Command-line automation support
- **Terminal Compatibility**: Windows Terminal and legacy console support

## 💻 System Requirements

### Operating System
- **Windows 7** (Build 7600+) / **Windows Server 2008 R2**
- **Windows 8** / **Windows Server 2012**
- **Windows 8.1** / **Windows Server 2012 R2**
- **Windows 10** / **Windows Server 2016/2019**
- **Windows 11** / **Windows Server 2022**

### Architecture Support
- **x86 (32-bit)**
- **x64 (64-bit)**
- **ARM32**
- **ARM64**

### Prerequisites
- **Administrator Privileges**: Required for registry modifications
- **PowerShell**: Must be enabled and functional
- **WMI Service**: Windows Management Instrumentation
- **Null Service**: System service for script stability
- **Internet Connection**: For update checks and IDM connectivity

## 📦 Installation

### Method 1: Direct Download
1. Download the `IAS.cmd` file from this repository
2. Extract to a local folder (not from archive directly)
3. Right-click and "Run as administrator"

### Method 2: Git Clone
```bash
git clone https://github.com/jcrvnx/idm-activation.git
cd idm-activation
```

### Important Notes
- **Do not run directly from archive**: Extract files first
- **Run as Administrator**: Required for registry access
- **Disable antivirus temporarily**: May flag registry modifications
- **Backup system**: Recommended before first use

## 🚀 Usage

### Interactive Mode (Recommended)
1. Right-click `IAS.cmd` and select "Run as administrator"
2. Choose from the main menu:
   - **[1] Freeze Trial** - Recommended option
   - **[2] Activate** - Full activation (may show fake serial screen)
   - **[3] Reset** - Clean slate for activation/trial
   - **[4] Download IDM** - Direct download link
   - **[5] Help** - Documentation and support
   - **[0] Exit** - Close the application

### Command Line Mode
```cmd
# Freeze trial (recommended)
IAS.cmd /frz

# Activate IDM
IAS.cmd /act

# Reset activation and trial
IAS.cmd /res

# Unattended mode with elevation
IAS.cmd /frz -el
```

## ⚙️ Command Line Options

| Parameter | Description | Usage |
|-----------|-------------|-------|
| `/frz` | Freeze trial period | `IAS.cmd /frz` |
| `/act` | Activate IDM | `IAS.cmd /act` |
| `/res` | Reset activation/trial | `IAS.cmd /res` |
| `-el` | Force elevation | `IAS.cmd /frz -el` |
| `-qedit` | Disable QuickEdit | `IAS.cmd -qedit` |

### Unattended Mode
Modify the script variables for automatic execution:
```cmd
set _activate=1    # Auto-activate
set _freeze=1      # Auto-freeze trial
set _reset=1       # Auto-reset
```

## 🔬 How It Works

### Registry Management
The script performs sophisticated registry operations:

1. **CLSID Detection**: Scans for IDM-related CLSID registry keys
2. **Permission Handling**: Takes ownership and modifies permissions
3. **Key Manipulation**: Locks or deletes problematic registry entries
4. **Synchronization**: Handles HKCU/HKU registry synchronization

### Activation Process
1. **System Validation**: Checks OS, architecture, and services
2. **Backup Creation**: Creates timestamped registry backups
3. **Registry Cleanup**: Removes existing activation data
4. **Key Addition**: Adds required registry entries
5. **CLSID Management**: Processes CLSID registry keys
6. **Registration**: Applies fake registration data (if activating)
7. **Download Test**: Verifies IDM functionality

### Trial Freezing
1. **Registry Locking**: Secures trial-related registry keys
2. **Permission Denial**: Prevents IDM from modifying trial data
3. **Persistence**: Ensures trial status remains frozen

## 🔧 Troubleshooting

### Common Issues

#### "PowerShell is not working"
- **Solution**: Enable PowerShell execution policy
- **Command**: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

#### "WMI is not working"
- **Solution**: Restart Windows Management Instrumentation service
- **Command**: `net start winmgmt`

#### "Null service is not running"
- **Solution**: Restart Null service
- **Command**: `net start null`

#### "User Account SID not found"
- **Solution**: Run as the user who installed IDM
- **Alternative**: Reinstall IDM under current user

#### "Failed to write in registry"
- **Solution**: Ensure administrator privileges
- **Alternative**: Disable antivirus temporarily

### Error Recovery
- **Automatic Backups**: Check `%SystemRoot%\Temp\` for backup files
- **Registry Restore**: Use backup `.reg` files to restore if needed
- **IDM Reinstall**: Complete reinstallation may be required

### Advanced Troubleshooting
- **Check logs**: Review console output for specific error messages
- **Verify permissions**: Ensure full registry access
- **Test connectivity**: Verify internet access to IDM servers
- **Update script**: Download latest version for bug fixes

## 🤝 Contributing

We welcome contributions to improve IAS:

### How to Contribute
1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Development Guidelines
- **Test thoroughly** on multiple Windows versions
- **Maintain compatibility** with existing features
- **Document changes** clearly
- **Follow existing code style**

### Reporting Issues
- **Use GitHub Issues** for bug reports
- **Include system information** (OS, architecture, IDM version)
- **Provide error messages** and steps to reproduce
- **Check existing issues** before creating new ones

## ⚠️ Disclaimer

### Legal Notice
This software is provided for **educational and research purposes only**. Users are responsible for:

- **Compliance with local laws** regarding software licensing
- **Respect for software terms of service**
- **Proper use of the tool** within legal boundaries
- **Understanding the implications** of registry modifications

### Usage Responsibility
- **Backup your system** before using this tool
- **Use at your own risk** - registry modifications can affect system stability
- **Test in safe environment** before production use
- **Understand the consequences** of activation modifications

### No Warranty
This software is provided **"as is"** without warranty of any kind. The authors are not responsible for:

- **Data loss** or system damage
- **Software licensing violations**
- **System instability** or performance issues
- **Any consequences** of using this tool

## 👥 Credits

### Original Creator
- **[WindowsAddict](https://github.com/WindowsAddict)** - Original IAS creator

### Current Maintainer
- **[Jcrist Vincent Orhen](https://github.com/jcrvnx)** - Fork maintainer and active developer

### Contributors
- **Open Source Community** - Bug reports, feature requests, and improvements
- **Testing Community** - Multi-platform testing and validation

### Acknowledgments
- **Internet Download Manager** - The target software for this tool
- **Windows Community** - Ongoing support and feedback
- **Open Source Projects** - Inspiration and technical guidance

## 📄 License

This project is **open source** and available under appropriate open source licensing. Please respect the original creator's work and contribute positively to the community.

---

**⭐ Star this repository if you find it helpful!**

**🔗 Links:**
- [Original Repository](https://github.com/WindowsAddict/IDM-Activation-Script)
- [Documentation](https://massgrave.dev/idm-activation-script)
- [IDM Official Site](https://www.internetdownloadmanager.com/)

**📧 Support:**
- [GitHub Issues](https://github.com/jcrvnx/idm-activation/issues)
- [Documentation](https://massgrave.dev/idm-activation-script)

---

*Last updated: July 30 2025 | Version: 1.5* 
