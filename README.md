# foss2020-reproducibility-tutorial
February 19, 2020
Repository for running the FOSS 2020 CyVerse Reproducibility Tutorial 
https://learning.cyverse.org/projects/cyverse-cyverse-reproducbility-tutorial/en/latest/index.html

Set-Up instructions (from linux history)

### Start a CyVerse Atmosphere Instance
From Windows Subsystem for Linux (WSL) 2 (Ubuntu Terminal)
```ssh bridgethass@128.196.142.50```

### Clone the github repo
```
git clone https://github.com/bridgethass/foss2020-reproducibility-tutorial.git 
```

### Download and install Miniconda3
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh 
bash Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda 
```

### Create aliases for conda packages (bin and lib)
```
ln -s /opt/conda/pkgs/*/bin/* /bin 
ln -s /opt/conda/pkgs/*/lib/* /usr/lib
```

### Install JupyterLab 1.2.3, JavaScript, Bash
```
/opt/conda/bin/conda install -c conda-forge -y jupyterlab=1.2.3 
/opt/conda/bin/conda install -c conda-forge -y nodejs=10.13.0 
/opt/conda/bin/pip install bash_kernel 
/opt/conda/bin/pip install ipykernel 
/opt/conda/bin/python3 -m bash_kernel.install
```

### Test conda installation and jupyter lab
```
/opt/conda/bin/conda search -c bioconda htseq 
/opt/conda/bin/jupyter lab --no-browser --allow-root --ip=0.0.0.0 --NotebookApp.token='' --NotebookApp.password='' --notebook-dir='/scratch/foss2020-reproducibility-tutorial/' 
```

### Install snakemake and create aliases
```
/opt/conda/bin/conda search -c bioconda snakemake 
/opt/conda/bin/conda install -c bioconda -c conda-forge -y snakemake=5.8.1 
ln -s /opt/conda/bin/* /bin 
ln -s /opt/conda/lib/* /usr/lib 
snakemake --version
```

### Docker pre-install & add docker key
```
sudo apt-get update 
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common 
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - 
sudo add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" 
```

### Install and test docker
```
sudo apt-get update 
sudo apt-get install -y docker-ce docker-ce-cli containerd.io 
docker run hello-world 
```
