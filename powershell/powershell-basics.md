# Powershell Basics

## **Overview:** <a href="#overview" id="overview"></a>

**The following goes over Powershell and the basics**

### **What is PowerShell?** <a href="#what-is-powershell" id="what-is-powershell"></a>

PowerShell is a powerful task automation and configuration management framework from Microsoft. It includes a command-line shell and scripting language, designed to help professionals control and automate the administration of Windows and applications.

**Key Features:**

* **Cmdlets:** Lightweight commands within PowerShell.
* **Pipelines:** Pass outputs from one cmdlet as inputs to another.
* **Scripting Language:** Create scripts to automate tasks.
* **Automation:** Simplify complex and repetitive tasks.
* **Object-Oriented:** Operates with objects, not just text.

### **Basic Command Syntax and Structure** <a href="#basic-command-syntax-and-structure" id="basic-command-syntax-and-structure"></a>

PowerShell commands, or cmdlets, use a Verb-Noun naming convention:

```powershell
Verb-Noun -Parameter <Value>
```

**Examples:**

```powershell
Get-Process -Name "notepad"
```

**Common Verbs:**

* `Get`: Retrieve data
* `Set`: Change data
* `New`: Create a new resource
* `Remove`: Delete a resource
* `Start`: Begin an operation

#### **Practical Examples to Get Started** <a href="#practical-examples-to-get-started" id="practical-examples-to-get-started"></a>

**Exercise 1: Open PowerShell**

* **Windows:** Search for "PowerShell" in the Start menu and open it.
* **macOS/Linux:** Open your terminal and type `pwsh` to start PowerShell Core.

**Exercise 2: Run Basic Commands**

*   **List all running processes:**

    ```powershell
    Get-Process
    ```
*   **Get help for a cmdlet**

    ```powershell
    Get-Help Get-Process
    ```
*   **Retrieve the current date and time:**

    ```powershell
    Get-Date
    ```

**Exercise 3: Explore PowerShell Help**

*   **Update the help system:**

    ```powershell
    Update-Help
    ```
*   **Get detailed help for a cmdlet**

    ```powershell
    Get.-Help Get-Process -Detailed
    ```

**Exercise 4: Check Parameters of a Given Command**

```powershell
Get-Help Get-Process -Parameter *
```
