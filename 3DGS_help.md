# 3DGS help

#### I cannot install simple-knn and diff-gaussian-rasterization.
Install from (original) source using git, instead of building from the submodules folder.  I.E.,
`pip install git+https://gitlab.inria.fr/bkerbl/simple-knn.git`

#### how do I run code in the background in terminal?  
Preferrably you run in background AND send the error log into a file.  
`nohup ./hello.sh > myoutput.txt >2&1 `
