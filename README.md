# C++ Development with MSYS2, MinGW, Clangd, and VSCodium on Windows

This guide helps you set up a lightweight and powerful C++ development environment using:

- [MSYS2](https://www.msys2.org/). MinGW-w64 GCC for compiling and debugging C++ code.
- Clangd for intelligent code completion, diagnostics, and navigation.
- [VSCodium](https://vscodium.com/).
- Extensions in VSCodium:
  - **C++ Runner** by `franneck94`
  - **C/C++ Debug (gdb)** by `KylinIdeTeam`
  - **Clangd** by `llvm-vs-code-extensions`
---
## Step 1: Install MSYS2

1. Download and install **.exe file** from [MSYS2's website](https://www.msys2.org/)
2. Open the **MSYS2 MSYS** terminal and run the initial update:

   ```bash
   pacman -Syu
    ```
> ⚠️ If the terminal shows **errors**, close the terminal, then reopen it and run **the same command** again.

3. After the initial update is complete, run the second update to finish syncing packages:
   ```bash
   pacman -Su
    ```
## Step 2: Install Required Packages

Open the **MSYS2 MinGW64** and run:
1. Command to install GCC compiler (g++):
   ```bash
   pacman -S mingw-w64-x86_64-gcc
    ```
2. Command to install GDB debugger:
   ```bash
   pacman -S mingw-w64-x86_64-gdb
    ```
3. Command to install Clangd and its related tools:
   ```bash
   pacman -S mingw-w64-x86_64-clang-tools-extra
    ```
## Step 3: Add to Environment PATH (Windows)

To make tools like `g++`, `gdb`, and `clangd` globally accessible in VSCodium terminals and editors:

1. Press **Win + S** or use the **Start Menu Search**, type **Environment Variables**, and open **Edit the system environment variables**.

2. In the **System Properties** window, click the **Environment Variables...** button.

3. In the new **Environment Variables** window that opens, look under the **System variables** section, scroll down and find **path**.

4. Select **path** and click the **Edit** button.

5. In the **Edit Environment Variable** window, click **New**.

6. Copy and paste the following path **(MinGW bin path)**:
   ```bash
   C:\msys64\mingw64\bin
    ```
7. Click **OK** to close all windows and apply changes.

8. After setting the path, open a new **Command Prompt**, **PowerShell**, or **VSCodium terminal** and run these codes to test them if they are accessible in VSCodium terminals and editors:
   ```bash
   g++ --version
   gdb --version
   clangd --version
    ```
## Step 4: Configure Clangd extension in VSCodium

1. Install the **Clangd** extension by `llvm-vs-code-extensions` in VSCodium.

2. Open your **settings.json**
or **Ctrl+Shift+P → “Preferences: Open User Settings (JSON)”**.

3. Add the following Clangd setting **(clangd.exe path in MinGW and MinGW C++ libraries)**:
    ```json
    {
        "clangd.arguments": [
        "-IC:/msys64/mingw64/include",
        ],
        "clangd.path": "C:/msys64/mingw64/bin/clangd.exe"
    }
    ```
## Step 5: Run and Debug with C++ Extensions in VSCodium

1. Install the **C++ Runner** extension by `franneck94` in VSCodium.

2. Install the **C/C++ Debug (gdb)** extension by `KylinIdeTeam` in VSCodium.

> 📝 These extensions handle their configurations for you — no additional configuration is needed.

3. To **run** your `.cpp` files:
  - Open and **choose** the folder that contains your `.cpp` files in VSCodium.
  - Click **Start Compilation**.
  - Then click **Run Executable**.

4. To **debug** your `.cpp` files:
  - Open and **choose** the folder that contains your `.cpp` files in VSCodium.
  - Click **Start Compilation**.
  - Then click **Start Debugging**.

## Step 6 (Optional): Updating All Packages

Open the **MSYS2 MSYS** terminal and run the next update:

   ```bash
   pacman -Syu
