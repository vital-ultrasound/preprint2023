# Dependencies
Dependencies and libraries for Ubuntu 20.04x64.

## Virtual Environment

Open the terminal for installation, update and load of the ve. 
```
cd $HOME/repositories/2022-echocardiography-proceedings/dependencies/virtual-environment
conda env create -f ve.yml 
conda env update --file ve.yml --prune
conda activate echo-paper-ve
```
See [README](virtual-environment/) for further details.
