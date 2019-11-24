Ansible Role: PowerShell Core
=========

Manages PowerShell Core on Windows or Linux. PowerShell is a task-based command-line shell and scripting language built on .NET. PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.

Requirements
------------
* Windows Server 2012
* Windows Server 2012 R2
* Windows Server 2016 
* Windows Server 2019
* Ubuntu 16.04
* Ubuntu 18.04
* CentOS 7
* RedHat Enterprise Linux 7

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    powershell_state: present

The state of PowerShell Core, present (default) will install the specified version, absent will remove it.

    powershell_version: latest

The version of PowerShell Core to install (example `6.2.3`), `latest` will find the newest release.

    powershell_debian_package_name: powershell

The package name for Debian based installations, `powershell-preview` will install a prerelease version.

    powershell_redhat_package_name: powershell

The package name for Debian based installations, `powershell-preview` will install a prerelease version.

    powershell_windows_enable_context_menu: false

This property controls the option for adding the Open PowerShell item to the context menu in Windows Explorer.

    powershell_windows_enable_psremoting: false

This property controls the option for enabling PowerShell remoting during installation.

    powershell_windows_enable_register_manifest: false

This property controls the option for registering the Windows Event Logging manifest.

Dependencies
------------

None

Example Playbook
----------------

    - hosts: win_servers
      vars:
        wac_state: present
      roles:
         - joezollo.powershell

License
-------

WIP

Author Information
------------------

This role was created by Joe Zollo (joe@zollo.net)