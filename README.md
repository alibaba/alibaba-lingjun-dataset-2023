# Alibaba GPU Cluster Dataset 2023

We released the dataset we used to study the communication contention among deep learning training (DLT) jobs in GPU clusters.
Some of the findings are summarized in the paper,

Jiamin Cao, Yu Guan, Kun Qian, Jiaqi Gao, Wencong Xiao, Jianbo Dong, Binzhang Fu, Dennis Cai, Ennan Zhai, Alibaba Cloud. 2024. Crux: GPU-Efficient Communication Scheduling for Deep Learning Training. In ACM SIGCOMM 2024 Conference (ACM SIGCOMM ’24), August 4–8, 2024, Sydney, NSW, Australia. ACM.

Please cite the paper if you use the dataset :-)

# What is included in the dataset?


This dataset contains all the DLT jobs (e.g., job ID, start time, end time, resource allocation, etc.) running in one of our in-production GPU clusters during two weeks in August 2023.
This cluster includes more than 800 hosts interconnected by a three-layer Clos network.

The layout of the dataset:

1. `job.csv`: Containing information about each job

2. `worker.csv`: Containing information about each worker of each job

3. `topo.csv`: Containing information about the network topology of the cluster

## Job information

Each row in `job.csv` corresponds to a job, containing information about the job name, ID, type (e.g., PyTorch and TensorFlow), start time, end time, etc.

## Worker information

Each row in `worker.csv` corresponds to a worker of a job, containing information about the associated job, type (master or worker), start time, end time, host IP, resource usage (e.g., GPUs and CPUs), etc.

## Topology information

Each row in `topo.csv` corresponds to a host, containing information about its location within the three-layer Clos network, i.e., which ASW (ToR switch), PSW (aggregation switch), and DSW (core switch) it is connected to.
