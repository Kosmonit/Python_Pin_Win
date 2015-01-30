# Python_Pin_Win
Python bindings for Pin Tool on Windows under MS Visual Studio 2005 or higher.

Based on project: https://github.com/blankwall/Python_Pin

# Hotfix
I compiled the project Python_Pin on Windows under MS Visual Studio 2005 but I found errors at compile time.

Files pin.h and python.h should be different namespace.

I placed python.h in namespace SPPY:

`namespace SPPY` 

`{`

`#include <Python.h>`

`}`

This helped


# Using
To run python script strace.py with program program.exe use this command:

`pin.exe -t Python_Pin.dll -m strace.py -- program.exe`
