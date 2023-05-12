### Log in to Wolfpack/DICE

```
# Make sure to connect to VPN or ethernet
ssh USERNAME@@dice01.garvan.unsw.edu.au
ssh USERNAME@@dice02.garvan.unsw.edu.au
```
You will be navigated to your home directory. <br><br><br>



### Using conda on Wolfpack


```
# navigate to your home dir
cd ~

# install miniconda
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh

# conda create an environment
conda create -n ENV_NAME
conda activate ENV_NAME

e.g., to create an environment (e.g., r_env) for using R on wolfpack
conda create -n r_env r-essentials r-base
conda activate r_env

# search for all available r versions
conda search r-base
conda install -c conda-forge r-base=4.3.0

```
