# Visual Studio Code - Installation and Configuration
- [Home](../README.md)
- [VS Code](./vscode.md)

---
The following steps will install and configure VS Code with the primary intended purpose of working with PowerShell. 

---
1. Download and Install VS Code and Git for Windows  
    - winget install Microsoft.VisualStudioCode --override '/SILENT /mergetasks="!runcode,addcontextmenufiles,addcontextmenufolders"' 
    (How to use winget to install VSCode with custom options? · microsoft/winget-cli · Discussion #1798 · GitHub) 
    - `winget install --id Git.Git -e --source winget` 

2. Install extensions 
    - PowerShell 
    - PowerShell Snippets 
    - Sign in and update profile 
3. PowerShell Settings
    - Click the Settings Sproket in the lower left-hand corner and select "Settings" from the menu
    - Select "User" at the top and scroll down and expand "Extensions" in the left pane
    - Click on "PowerShell" under "Extensions" and then update the following settings as needed:
      - Code Folding – Enable 
      - Add Whitespace Around Pipe (|) – Enable 
      - Auto Correct Aliases – Enable 
      - Avoid Semicolons As Line Terminators - Enable 
      - Open Brace On Same Line – Disable 
      - Trim Whitespace Around Pipe – Enable 
      - Use Correct Casing – Enable 
4. Add Code Snippets 