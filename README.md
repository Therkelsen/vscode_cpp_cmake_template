# Project Setup
This works and is intended for Ubuntu 20.04. Don't @ me.

## Install Dependencies
Run the following command to install necessary packages:

```
sudo apt install gcc gdb make cmake clangd build-essential
```

## Clone the Repository
Clone the repository using your preferred method. Once cloned, open the repo in VS Code:

```
code .
```

Or, if you're using VS Code Insiders:

```
code-insiders .
```

## Install Extensions
Make sure to install the following VS Code extensions:

- "C/C++" by Microsoft
- "CMake Tools" by Microsoft
- "CMake" by twxs
- "clangd" by LLVM

## Add Keybind to Build and Run
To bind a key to build and run the project, do the following:

1. Press `Ctrl + Shift + P` and type `Keyboard Shortcuts JSON` to open the keybindings JSON file.
2. Add the following entry, modifying the keybind to your preference (example uses `F5`):

```
{
    "key": "F5",
    "command": "workbench.action.tasks.runTask",
    "args": "run"
}
```

3. Save the file.

## Disable C/C++ IntelliSense in Favor of clangd
Disable the default IntelliSense and use clangd instead:

1. Press `Ctrl + Shift + P` and type `User Settings JSON` to open the user settings JSON file.
2. Add the following entry:

```
"C_Cpp.intelliSenseEngine": "disabled"
```

3. Save the file
4. Verify that clangd works by hovering over the `v` vector in the `main.cpp` file. It should show some goodies.

## Configure CMake
To setup your project, from your workspace run the following command:

```
cmake -S . -B build
```

Then navigate to the `/build` directory and execute the following commands:

```
cmake ..
make
```

If prompted, reload the clang configuration. If not, do it manually:
Hit `Ctrl + Shift + P` and run the `clangd: Restart Language Server` command.

## Run
Now, from within your `main.cpp` file, hit the keybind you bound to run the code. The output should show up in the build-in terminal below.