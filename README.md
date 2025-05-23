# Jieli-Development-Board

For this project, we recommend compiling in the Windows environment using VSCode. The installation and setup process is as follows:

1. Set Up [the Development Environment on Windows](#12-windows)  
2. [Configure VSCode for Development](#23-compilation-using-vscode)

For more detailed development tools and manuals, please click the link below:
https://doc.zh-jieli.com/Tools/zh-cn/dev_tools/dev_env/index.html



## 1 Development Environment Setup

### 1.2 Windows

The SDK project is designed to work on **Windows systems** and uses **Code::Blocks** as the default development environment.

The setup process consists of three main steps:

1. **Download and install [the Windows version of Code::Blocks](https://pkgman.jieliapp.com/s/codeblocks)**

2. **Launch Code::Blocks once and then close it**
    This step ensures Code::Blocks generates the necessary configuration files.

3. **Download and install [the latest version of the JieLi Windows toolchain](https://pkgman.jieliapp.com/s/win-toolchain)**
    [Click here to download]

After completing the steps above, you're ready to open the Code::Blocks project and start building and developing.
 For more details, refer to the **[SDK Compilation and Download Guide](#2-sdk-compilation-and-download)**.

### 1.3 Linux


By default, the SDK project supports development and compilation in a Linux environment using a Makefile. Refer to the instructions for [compiling with make](#22-compilation-using-make).

- The post-processing script `download.sh` (modified based on the Windows version `download.bat`) can be used to generate `.fw` firmware files.

- Downloading the firmware to the device is not supported.

For toolchain and post-processing tool download links, refer to: **[Latest Tool Version](https://doc.zh-jieli.com/Tools/zh-cn/other_info/index.html)**.

## 2 SDK Compilation and Download

After installing the toolchain, you can start compiling the SDK.

By default, the SDK supports both compilation and downloading on Windows systems. On Linux systems, only compilation is supported.

The SDK is released with a `.cbp` Code::Blocks project file by default. In addition, a Makefile and VSCode configuration are also provided, allowing users to choose command-line compilation as needed.

### 2.1 Compilation Using Code::Blocks

#### 2.1.1. Steps to Compile the SDK Using Code::Blocks

Compiling the SDK with Code::Blocks involves two steps. The following example uses the AC695N SDK:

#### 2.1.1.1. Open the `.cbp` Project File in the SDK Directory

Double-click to open the corresponding `.cbp` project file.

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/double_click_open_cbp_file.jpg)

#### 2.1.1.2. Use the force download tool to connect the development board (prototype) to the PC.

Connect the USB female end of the force upgrade tool to the PC, and the USB male end to the prototype or development board.
 (**Note:** Make sure the connections are not reversed. Refer to the image below.)

The process is as follows:

1. Connect according to the instructions shown in the image.
2. The green and red LEDs on the force download tool will start flashing.
3. Press the button on the force download tool — the green LED will turn off, and the red LED will stay on.
4. Now, the program can be flashed onto the development board.

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/fu_image1.jpg)

**For detailed information**, refer to: [**Upgrade and Download Instructions**.](https://doc.zh-jieli.com/Tools/zh-cn/dev_tools/forced_upgrade/upgrade_and_download.html)

### 2.2 Compilation Using `make`

There is a `Makefile` located in the root directory of the SDK. Additionally, to support the use of `make` on Windows, the SDK includes a `tools` directory that contains the necessary compilation tools.

#### 2.2.1. Compilation Using `make` on Windows

Compilation on Windows consists of two steps. The following example uses the AC695N SDK for illustration:

1. Open the `make_prompt.bat` script located in the `tools` directory under the SDK folder, as shown in the image below.

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/open_tools_dir.jpg)

2. In the command prompt window that appears, type `make` and press Enter.

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/enter_make_prompt.jpg)

#### 2.2.2. Compilation Using `make` on Linux

To compile on Linux, follow the four steps below:

1. **Download [the toolchain for Linux](https://pkgman.jieliapp.com/s/linux-toolchain).**
2. **Extract the toolchain to the `/opt/jieli` directory**, ensuring that the path `/opt/jieli/common/bin/clang` exists (pay attention to the directory structure).
3. **Make sure the result of `ulimit -n` is sufficiently large** (recommended to be greater than 8096). Otherwise, the build process may fail due to too many open files. You can set a higher value using: `ulimit -n 8096` 
4. Navigate to the root directory of the SDK and run `make` to compile

#### 2.2.3. Troubleshooting Makefile Compilation Errors

Check the following if you encounter errors during compilation using the Makefile:

1. Make sure there are no spaces or Chinese characters in the SDK path.

2. Ensure the path to the SDK is not too deep, as excessive path depth may cause issues.

3. Verify that the tools folder in the SDK root directory matches the one provided in [the conversion tools package](https://pkgman.jieliapp.com/s/cbp2make). Check for any missing files.

4. Try compiling the corresponding Code::Blocks project to confirm whether the toolchain environment is working properly.

5. If you are not using the provided make_prompt.bat script for compilation, ensure that the %PATH% environment variable is correctly configured, i.e., the toolchain can be found through this environment variable.

 ### 2.3. Compilation Using VSCode

Compilation in VSCode is done by invoking the `make` command.
 On Linux, you need to follow the steps in **"Compiling with make"** to complete the initial configuration.

#### 2.3.1. VSCode Setup Steps

The following example uses the AC695N SDK for illustration:

##### 2.3.1.1. Install the required extensions: **Task Explorer** and **C/C++**.

As shown in the figure below:

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/vscode_install_task_explorer.jpg)

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/vscode_install_c_cpp_ext.jpg)

##### 2.3.1.2. Open the SDK directory using VSCode.

As shown in the figure below:

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/open_vscode.jpg)

Alternatively, you can directly open VSCode, then select **“Open Folder”** from the menu bar and choose the SDK directory to open it, as shown in the image below.

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/build_with_vscode_open_folder.jpg)



##### 2.3.1.3. Select the corresponding task to compile.

As shown in the figure below:

Click **TASK EXPLORER > SDK > vscode** to view the available tasks:

- **all**: Build the entire project
- **clean**: Clean the build output files

![img](https://doc.zh-jieli.com/Tools/zh-cn/_images/vscode_build.jpg)





