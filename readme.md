# This page is curated to record issues and solutions to common software install problems encountered by the author.

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

## Git
Q: What are the essential commands that allow me to use git with github?  
A: The most basic commands are "add", "commit" and "push". This allows changes in your local directory to be updated in your (online) github repository. 

Q: How does forking work?  
A: 

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
