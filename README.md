# reproducibility-tutorial
# Cyverse tutorial - week 3
    1  cd /scratch

#check for available disc space
    2  df -h

##computer setup
#clone your git repository and change to that directory.
    3  git clone https://github.com/murphykr/reproducibility-tutorial.git
    4  ls
    5  ls reproducibility-tutorial/

#download the miniconda installer
    7  wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

#install miniconda silently (-b) in path (-p) /opt/conda   
    8  bash Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda
   
#make sure all conda packages are in path by symbolic links to /bin
   10  ln -s /opt/conda/pkgs/*/bin/* /bin
   11  ln -s /opt/conda/pkgs/*/lib/* /usr/lib

#install jupyter lab version 1.2.3
   12  /opt/conda/bin/conda install -c conda-forge -y jupyterlab=1.2.3
   13  /opt/conda/bin/conda install -c conda-forge -y nodejs=10.13.0
  
   14  /opt/conda/bin/pip install bash_kernel
   15  /opt/conda/bin/pip install ipykernel
   16  /opt/conda/bin/conda search qiime
   17  /opt/conda/bin/python3 -m bash_kernel.install

#test jupyterlab
   20  /opt/conda/bin/jupyter lab --no-browser --allow-root --ip=0.0.0.0 --NotebookApp.token='' --NotebookApp.password='' --notebook-dir='/scratch/reproducibility-tutorial/'


#install snakemake   21  /opt/conda/bin/conda search -c bioconda snakemake
   22  /opt/conda/bin/conda install -c bioconda -c conda-forge -y snakemake=5.8.1
   23  ln -s /opt/conda/bin/* /bin
   24  ln -s /opt/conda/lib/* /usr/lib
#verify snakemake version
   25  snakemake --version

#install docker
#update ubuntu apt-get package manager
   26  sudo apt-get update
#install some needed packages 
   27  sudo apt-get install -y ca-certificates curl gnupg-agent software-properties-common
#add the docker key
   28  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
#add the repository
   29  sudo add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   30   $(lsb_release -cs) \
   31   stable"
#update apt-get with new repository info
   32  sudo apt-get update
# install docker
   33  sudo apt-get install -y docker-ce docker-ce-cli containerd.io
#test docker
   34  docker run hello-world

#change into our project directory
   51  cd /scratch/reproducibility-tutorial/

#append your bash hsitory to the README.MD file
   67  history >>README.md

#use nano to edit the history down to the relevant commands
#use markdown to make this into a readable report
nano README.MD

#from a terminal on your local computer, do an scp trnsfer to the Atmos computer of the SraRunTable.txt file
#adjust the code below to reflect your personal information
scp ~/Downloads/SraRunTable.txt YOURCYVERSEUSERNAME@123.456.78.9:/scratch/reproducibility-tutorial/

#Move back to the Atmos computer instance
#Make a directory to move the metadata to
# -p flag makes the last directory and all prior directories needed to
# complete the path you have described
   77  mkdir -p /scratch/reproducibility-tutorial/experiment/sra_files/metadata
   80  mv SraRunTable.txt /scratch/reproducibility-tutorial/experiment/sra_files/metadata
    1  cd /scratch
    2  df -h
    3  git clone https://github.com/murphykr/reproducibility-tutorial.git
    4  ls
    5  ls reproducibility-tutorial/
    6  miniconda
    7  wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
    8  bash Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda
    9  ls
   10  ln -s /opt/conda/pkgs/*/bin/* /bin
   11  ln -s /opt/conda/pkgs/*/lib/* /usr/lib
   12  /opt/conda/bin/conda install -c conda-forge -y jupyterlab=1.2.3
   13  /opt/conda/bin/conda install -c conda-forge -y nodejs=10.13.0
   14  /opt/conda/bin/pip install bash_kernel
   15  /opt/conda/bin/pip install ipykernel
   16  /opt/conda/bin/conda search qiime
   17  /opt/conda/bin/python3 -m bash_kernel.install
   18  conda search qiime
   19  /opt/conda/bin/conda search qiime2
   20  /opt/conda/bin/jupyter lab --no-browser --allow-root --ip=0.0.0.0 --NotebookApp.token='' --NotebookApp.password='' --notebook-dir='/scratch/reproducibility-tutorial/'
   21  /opt/conda/bin/conda search -c bioconda snakemake
   22  /opt/conda/bin/conda install -c bioconda -c conda-forge -y snakemake=5.8.1
   23  ln -s /opt/conda/bin/* /bin
   24  ln -s /opt/conda/lib/* /usr/lib
   25  snakemake --version
   26  sudo apt-get update
   27  sudo apt-get install -y ca-certificates curl gnupg-agent software-properties-common
   28  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   29  sudo add-apt-repository  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   30   $(lsb_release -cs) \
   31   stable"
   32  sudo apt-get update
   33  sudo apt-get install -y docker-ce docker-ce-cli containerd.io
   34  docker run hello-world
   35  exit

#Week 4 Homework
   36  mkdir reproducibility-tutorial
   37  ls
   38  cd reproducibility-tutorial/
   39  ls
   40  history >>README.md
   41  nano README.md 


   42  git clone https://github.com/murphykr/reproducibility-tutorial.git
   43  ls
   44  ls ./reproducibility-tutorial/
   45  cd .
   64  git clone https://github.com/murphykr/reproducibility-tutorial.git
   65  ls
   66  cd reproducibility-tutorial/
   67  history >>README.md
   68  ls
   69  nano README.md 
   71  chown -R murphykr /scratch/reproducibility-tutorial/
   72  chown -R murphykr@cyverse.org /scratch/reproducibility-tutorial/
   73  chown -R kmurphy425 /scratch/reproducibility-tutorial/
   74  scp ~/Downloads/SraRunTable.txt kmurphy425@128.196.142.2:/scratch/reproducibility-tutorial/
   75  ls
   76  cut -f1 SraRunTable.txt -d ,
   77  mkdir -p /scratch/reproducibility-tutorial/experiment/sra_files/metadata
   78  ls
   79  ls ./experiment/
   80  mv SraRunTable.txt /scratch/reproducibility-tutorial/experiment/sra_files/metadata
   81  ls ./experiment/
   82  ls ./experiment/sra_files/
   83  ls ./experiment/sra_files/metadata/
   84  history >>README.md
   85  nano README.md 
   86  nano README.md 
   87  git status
   88  git add experiment/
   89  git commit -am "update readme and record project metadata"
   90  git push
   91  git push
   92  iinit
   93  ils
   94  imkdir reproducibility_tutorial
   95  iput -rPV /scratch/reproducibility-tutorial reproducibility_tutorial
   96  exit

#Starting FOSS2020 Week 5 - Computer Setup
   97  cd /scratch
   99  sudo apt-get update
  100  docker run hello-world
  108  git clone https://github.com/murphykr/reproducibility-tutorial.git
  109  cd reproducibility-tutorial/
  112  history
  113  history >> README.md
