# C++ to Python and/or Matlab Starter

Template repository for interfaces for your C++ code so that you can call it from python or Matlab. 

Note: Code only tested on unix systems. Expect issues with Windows 🪟.

## ⚙️ Installation

This repo comes with some sample c++ code which is wrapped via pybind for usage in python has matlab mex wrappers for usage in matlab 💡

Installation is farily simple:

🐍 Python

Simply download the repo and `python setup.py install` (you need working c++ compiler + cmake installed on your machine)

or

Simply type in `pip install git+https://github.com/paul0noah/cpp-pybind-mex-starter`

🔺 Matlab

See example file `BUILD_MEX.sh` on how to compile matlab mex wrapper. ⚠️ Do not simply run the `.sh` file as you need to adjust the variables `Matlab_MEX_EXTENSION` and `Matlab_ROOT_DIR` depending on your system.
```
#!/bin/bash
mkdir build
cd build
cmake .. -DBUILD_MEX_FILE=True -DMatlab_MEX_EXTENSION="mexmaca64" -DMatlab_ROOT_DIR=/Applications/MATLAB_R2022b_beta.app/
make -j 4 cpppymex_myfunc0 cpppymex_myfunc1
```

You can find the generate mex file in `/build/mex/` directory in your project (just copy this file into your matlab project and you can call it as shown above).

📝 Note when building mex-wrappers on macOS you might need to provide `-DMatlab_MEX_EXTENSION="mexmac64` and `-DMatlab_ROOT_DIR=path/to/your/matlab/install` to your cmake command so that it looks e.g. like

```
mkdir build
cd build
cmake .. -DBUILD_MEX_FILE=True -DMatlab_MEX_EXTENSION="mexmaca64" -DMatlab_ROOT_DIR=/Applications/MATLAB_R2024b.app/
make -j 4 cpppy_myfunc
``` 

## ✨ Usage
🐍 Python
```python
import cpppymex
np_array_output0, np_array_output1 = cpppymex.myfunc0()
np_array_output0, np_array_output1 = cpppymex.myfunc1(np_array_input0, "stringinput")

myclass = cpppymex.MyClass("name")
myclass.print_name()

```

🔺 Matlab
```matlab
func_id = 0
[array_out_0, array_out_1] = cpppymex_myfunc(func_id);
func_id = 1
[array_out_0, array_out_1] = cpppymex_myfunc(func_id, array_input_0, 'stringinput'); % make sure to use '' instead of "" here!
```

## Attribution 🎓
When using this code for your own projects please cite the followig:

```bibtex
@misc{decimatec2f,
  title = {Decimate Coarse to Fine},
  author = {Paul Roetzer},
  note = {https://github.com/paul0noah/pp-pybind-mex-starter},
  year = {2025},
}
```

## License 🚀
This repo is licensed under MIT licence.
