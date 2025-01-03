# Common software installation problems (win11)

This page is curated to record issues and solutions to common software install problems encountered by the author.

About the author:  
The author is a passionate computer vision / robotics hobbyist. Therefore if you are in the same field you are likely to encounter the same issues.  
Note that this page writes down only very non-task speciifc installation problems.  
Problems pertaining to a single github project will likely not end up here.  

## Syntax
It is important to define every single term or syntax when writing an explanation blog post. Note that these are my preferred notations, and will be certainly different than other tutorials and blogs you read elsewhere.  
<>  this indicates a non-optional argument (word) that must be used. The variable contained within these brackets indicates a string which **you will name by yourself**, and the name which I give is suggestive of what it does, but is not the actual string of letters you (must) put down.   
<< >> this indicates an optional argument.  

## PyTorch
Q: Torch not compiled with CUDA enabled  
A: The  ''Torch not compiled with CUDA enabled'' error is likely to occur when the user does not have CUDA Toolkit installed in their Python environment.

Q: I installed PyTorch on Win11 with Cuda option, but when I verify my installation

Q: Cuda toolkit for conda?  
A: tldr conda is a terrible package manager that searchers for your specified installation version and its dependencies in different ways. To install say CUDA 12.1, this is the command you should run:  
`conda install nvidia/label/cuda-12.1.0::cuda-toolkit -c nvidia/label/cuda-12.1.0`  
This is because when conda installing packages, for package itself, it would look for the channel you specified before '::'. But for its dependences, it will search them channel by channel under the priority it shows you.  

Q: What is the difference between `nvcc --version` and `nvidia-smi`?  
A: `nvcc` shows the cuda-toolkit installed. Different versions could be installed in each conda environment, catering to different requirements. The Cuda-toolkit is usually **not** backwards-compatible.  
`nvidia-smi` on the other hand shows the CUDA driver version in the computer. This is shared across all virtual environments. Fortunately, higher CUDA driver versions are usually backwards compatible.

Reference: https://stackoverflow.com/questions/78484090/conda-cuda12-incompatibility

## R on vscode
Q: My variables does not register in the workspace viewer in Vs-code, why?
A: My solution is to first create the R-workspace in Rstudio. Then, go back to Vscode, and there you'll find workspace properly registered now.

Q: How do I run R code in vscode?
A: There are multiple options:  
### Option1:
To open an R-terminal, run: `pip install radian`.  
Finally, type radian in the powershell terminal in vscode to launch the R-terminal.
### Option 2:
Launch an R-interactive terminal by first installing R by downloading and installing the `.exe` file from the official website. Then, install the R extension on vs-code in the Marketplace. Next,


## Docker

Q : Docker: daemon access permission denied issue  

A : sudo groupadd docker

sudo usermod -aG docker $USER   # add user to group

newgrp docker    # Log in to the new docker group

docker run hello-world     # checks if runs normally

(optional):

sudo systemctl restart docker

reboot


## Git
Q: What are the essential commands that allow me to use git with github?  
A: The most basic commands are "add", "commit" and "push". This allows changes in your local directory to be updated in your (online) github repository. 
`git add <FILE>` or `git add .`  
`git commit -m 'MESSAGE'`  
`git push origin -u main`  
Sometimes instead of master, your branch is instead called main. Check the name of your branch by calling `git branch`.  

Q: How does forking work?  
A: Forking means creating a copy of another repo (original), which you can then work on without affecting the original. When the original updates itself, you are given the option to update with it. Your forked repo can then merge back to the original repo by a "pull request".

## Conda (Anaconda)
Note: within this context, the following terminologies are interchangeable:  
package <-> module <-> library  
env <-> conda environment

Q: What are the essential commands in conda that allows me to get started?  
A: In my opinion, these commands are indispensible:  
1. `conda create -n <ENV_NAME>` this allows you to create a new conda environment
2. `conda activate <ENV_NNAME>` this activates an existing environment  
3. `conda list <<PACKAGE>>` lists all downloaded libraries in this conda environment
4. `conda env list`  - lists all available environments
5. `conda env remove -n <YOUR_ENV>` - deletes an existing environment
6. `conda install <PACKAGE>` - installs the library
7. `conda uninstall <PACKAGE>` - uninstalls the library
8. `conda create --clone <OLD_ENV> -n <NEW_ENV>` - clones the activated environment

Q: How is 'conda install' different from 'pip install'?  
A: 

Q: How to download file from Google Drive using the conda terminal?  
A: `pip install gdown`

`gdown https://drive.google.com/uc?id=<file_id>`  # for files  
`gdown <file_id>`                                 # alternative format  
`gdown --folder https://drive.google.com/drive/folders/<file_id>`  # for folders  
`gdown --folder --id <file_id>`                                   # this format works for folders too  

The file id should look like this:    
Files:  
`https://drive.google.com/file/d/<file_id>/view?usp=sharing`  
Folders:  
`https://drive.google.com/drive/folders/<file_id>`  

## installing cpp-llama (win11)
Q: Install errors showing comments like "Cannot find C-compiler" etc.  
A: First make sure G++, GCC and Cmake are installed on your system.

In windows, do as many of these as required:  

`$env:CMAKE_C_COMPILER = "C:\msys64\ucrt64\bin\gcc.exe"`  

`$env:CMAKE_CXX_COMPILER = "C:\msys64\ucrt64\bin\g++.exe"`  

`$env:CMAKE_GENERATOR = "MinGW Makefiles"`  

`$env:CMAKE_ARGS = "-DGGML_OPENBLAS=on -DCMAKE_C_COMPILER=C:/msys64/ucrt64/bin/gcc.exe -DCMAKE_CXX_COMPILER=C:/msys64/ucrt64/bin/g++.exe"`  

$env:CMAKE_GENERATOR = "MinGW Makefiles"

$env:CMAKE_ARGS = "-DGGML_OPENBLAS=on -DCMAKE_C_COMPILER=C:/msys64/bin/gcc.exe -DCMAKE_CXX_COMPILER=C:/msys64/bin/g++.exe"

There is no trick to it. Just add as many environmental variables as paths as you can.  


Q: Can't find 'nmake' or 'CMAKE_C_COMPILER'  
A: If you run into issues where it complains it can't find 'nmake' '?' or CMAKE_C_COMPILER, you can extract w64devkit as mentioned in llama.cpp repo and add those manually to CMAKE_ARGS before running pip install:

`$env:CMAKE_GENERATOR = "MinGW Makefiles"  
$env:CMAKE_ARGS = "-DGGML_OPENBLAS=on -DCMAKE_C_COMPILER=C:/w64devkit/bin/gcc.exe -DCMAKE_CXX_COMPILER=C:/w64devkit/bin/g++.exe"`

See the above instructions and set CMAKE_ARGS to the BLAS backend you want to use.

##
