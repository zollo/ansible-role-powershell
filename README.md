Ansible Role: PowerShell
=========

Manages PowerShell on Windows or Linux. PowerShell is a task-based command-line shell and scripting language built on .NET. PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.

Requirements
------------

* Windows Server 2016
* Windows Server 2019
* Ubuntu 20.04/18.04
* CentOS 7/8

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    powershell_state: present

The state of PowerShell Core, present (default) will install the specified version, absent will remove it.

    powershell_version: latest

The specific version of PowerShell Core to install (example `6.2.3`), `latest` will find the newest release. Must match up with the value set in `powershell_version_major`.

    powershell_version_major: 6

The major version of PowerShell Core to install (currently, only `6` and `7` are valid values).

    powershell_modules: []

List containing PowerShell modules to install from the PowerShell Gallery.

    powershell_debian_package_name: powershell

The package name for Debian based installations, `powershell-preview` will install a prerelease version.

    powershell_debian_modules_scope: AllUsers

The installation scope of the modules defined in `powershell_modules`, specific to Debian based installations.

    powershell_redhat_package_name: powershell

The package name for Red Hat based installations, `powershell-preview` will install a prerelease version.

    powershell_redhat_modules_scope: AllUsers

The installation scope of the modules defined in `powershell_modules`, specific to RedHat based installations.

    powershell_redhat_update_ca_trust: false

Enables a potential workaround for issues related to Microsoft's SSL Certificate for packages.microsoft.com.

    powershell_windows_modules_scope: AllUsers

The installation scope of the modules defined in `powershell_modules`, specific to Windows based installations.

    powershell_windows_enable_context_menu: false

Controls the option for adding the Open PowerShell item to the context menu in Windows Explorer.

    powershell_windows_enable_psremoting: false

Controls the option for enabling PowerShell remoting during installation.

    powershell_windows_enable_register_manifest: false

Controls the option for registering the Windows Event Logging manifest.

    powershell_windows_artifact_arch: x64

The processor architecture for Windows based installations, valid values are `x64` (64-bit) or `x86` (32-bit).

Dependencies
------------

None

Example Playbook
----------------

    - name: Install PowerShell 6.2.3
      hosts: core_infra
      vars:
        powershell_version: '6.2.3'
      roles:
         - joezollo.powershell

License
-------

WIP

Author Information
------------------

This role was created by Joe Zollo (joe@zollo.net)