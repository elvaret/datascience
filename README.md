			== Tutorial install anaconda dengan docker di wsl 2==

>> with miniconda

docker search continuumio

docker pull continuumio/miniconda3

docker run -i -t -p 8888:8888 continuumio/miniconda3 /bin/bash \ -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir \ /opt/notebooks && /opt/conda/bin/jupyter notebook \ --notebook-dir=/opt/notebooks --ip='*' --port=8888 \ --no-browser --allow-root"

### every time u want to rerun the container, it would fail at second attemp. So run this command below (with -p):

docker run -i -t -p 8888:8888 continuumio/anaconda3 /bin/bash -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir -p /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser --allow-root"

==============================================================================
==============================================================================

>> with anaconda3

docker run -i -t -p 8888:8888 continuumio/anaconda3 /bin/bash -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir -p /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888 --no-browser --allow-root"

>>to restart a stop container

docker start <CONTAINER_ID>


============================================================================================================================================================
>> with anaconda3 (saving file in wsl 2) --> by mount docker

docker run -i -t -p 8888:8888 -v "$PWD":/home --name myanaconda3 continuumio/anaconda3:latest

docker exec -it myanaconda3 /bin/bash

run this in container: jupyter lab --ip='0.0.0.0' --port=8888 --no-browser --allow-root --notebook-dir=/home 

## type again if the container is closed 
