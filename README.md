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

This code don't work on Windows:

//     FILE* tool = fopen(filename, "r");

//     if (tool == NULL) {

//         perror("fopen");

//         exit(1);

//     }

// 

// 	 SPPY::PyRun_SimpleFile(tool, filename);

//     fclose(tool);

And replece on this code:

	 SPPY::PyObject* PyFileObject = SPPY::PyFile_FromString((char *)filename, "r");

	 SPPY::PyRun_SimpleFile(SPPY::PyFile_AsFile(PyFileObject), filename);

# Using
To run python script strace.py with program program.exe use this command:

`pin.exe -t Python_Pin.dll -m strace.py -- program.exe`

# Comments
This project 32 bit only Pin Tool
