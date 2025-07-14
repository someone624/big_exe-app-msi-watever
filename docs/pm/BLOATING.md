# Best way to bloat
There are lots of ways to make a Python file into some exe/app or other linux stuff. Some of those give results on bloating them using this, but some optimize unused modules/packages/libraries. This .md file will show which ones give the best results
## Most common ones
This .md file will cover those freezing things
### Usage
Just some example commands
#### PyInstaller
```bash
pyinstaller --onefile --windowed app.py
```
> --onefile will make a single file
> --windowed will remove the console
#### py2exe
This needs a setup.py then a command:
```python
# setup.py
from distutils.core import setup
import py2exe

setup(console=['app.py'])  # or windows=['app.py'] for GUI
```
```bash
python setup.py py2exe
```
> This is Windows ![Windows logo](../../assets/image/windows.png) only
#### cx_Freeze
This also needs a setup.py
```python
# setup.py
from cx_Freeze import setup, Executable

setup(
    name="AppName",
    version="0.1",
    description="My cool app",
    executables=[Executable("app.py")]
)
```
```bash
python setup.py build
```
#### Briefcase (BeeWare)
```bash
briefcase new
briefcase build
briefcase run
```
Or to package:
```
briefcase package
briefcase create
```
#### staticx
```bash
pyinstaller --onefile app.py
staticx dist/app dist/app_static
```
#### Nutika
```bash
nuitka --onefile --standalone app.py
```
> --onefile makes it a single file
> --standalone bundles dependencies
#### PyOxidizer
```bash
pyoxidizer init
pyoxidizer build
```
This makes a pyoxidizer.bzl config file.
Now just change it and you are ready:
```python
python_config = default_python_config()
packaging_policy = default_packaging_policy()
```
#### shiv
```bash
shiv -o app.pyz -e app:main .
```
> -o: output filename
> -e: entry point
> .  : current directory
#### zipapp
```bash
python -m zipapp myapp -m "app:main" -o app.pyz
```
> -m: module/function to run
> -o: output filename
## Which one bloats the most?
### :star::star::star::star:
These things in this section bloat the output the most since they include 100% of every module/package/library that is needed. So if you import 30 libraries that are unused, it's all going in there.
#### PyInstaller ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png)  ![Unsupported on ChromeOS, but can work](../../assets/image/chrome_os.png)
#### py2exe ![Supported on Windows](../../assets/image/windows.png)
#### py2app ![Supported on MacOS](../../assets/image/mac_os.png)
>On PyInstaller, ChromeOS ![ChromeOS](../../assets/image/chrome_os.png) is unsupported but there are ways.
---
### :star::star::star:
The things in this section bloat the output but optimize some unused code/modules/packages/libraries. So if you give it 30 libraries, it will optimize it a bit. These ones don't do that as much as some of those later down this list.
#### cx_Freeze ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png)  ![Unsupported on ChromeOS, but can work](../../assets/image/chrome_os.png)
#### Briefcase ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png) ![Supported on Android](../../assets/image/android.png) ![Supported on iOS](../../assets/image/ios.png)
>On cx_Freeze, ChromeOS ![ChromeOS](../../assets/image/chrome_os.png) is unsupported but there are ways.
---
### :star::star:
The things in this section are just a wrapper. Like they are a candy wrapper. If you give it 30 libraries, it is a wrapper. If you unwrap the wrapper and then eat the ~~libraries~~ candy, then you have 4 options for the wrapper:
- Throw it in the bin
-  Litter
-  Keep it in your pocket
- Eat the wrapper too
#### Staticx ![Supported on Linux](../../assets/image/linux.png) ![Supported on ChromeOS](../../assets/image/chrome_os.png) ![Unsupported on Windows, but can work](../../assets/image/windows.png)
> On Staticx, Windows ![Windows](../../assets/image/windows.png) is unsupported but there are ways.
---
### :star:
These ones in this section are made for tiny output. If you give it 30 unused libraries, say bye to those libraries. If you use 30 libraries, you can say goodbye to those libraries. If you give it 30 used libraries, you can still say goodbye to them. Say hi to your memory though since the size of these are -15 TB
<!-- yes, that is a minus sign, it is a negative number -->
#### Nutika ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png)  ![Unsupported on ChromeOS, but can work](../../assets/image/chrome_os.png)
#### PyOxidizer ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png)
#### shiv ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png)  ![Unsupported on ChromeOS, but can work](../../assets/image/chrome_os.png)
#### zipapp ![Supported on Windows](../../assets/image/windows.png) ![Supported on MacOS](../../assets/image/mac_os.png) ![Supported on Linux](../../assets/image/linux.png)  ![Unsupported on ChromeOS, but can work](../../assets/image/chrome_os.png)
> On Nutika, shiv, and zipapp, ChromeOS ![ChromeOS](../../assets/image/chrome_os.png) is unsupported but can work
# Tl;DR
So the best ones for bloating are
1. PyInstaller
2. py2exe
3. py2app
4. Briefcase
5. cx_Freeze
6. bbfreeze
7. pyarmor
8. Staticx
9. PyOxidizer
10. Nutika
11. shiv
12. zipapp 
> [!NOTE]
> Some don't actually freeze things/are outdated, its just me being an idiot.
## Tl;DR of TL;DR
| Thing | Bloat? |
| -------- | -------- |
| pyinstaller | :star: |
| py2exe | :star: |
| cx_freeze | :white_check_mark: |
| staticx | :neutral_face: |
| nutika | :warning: |
| pyoxidizer | :x:
