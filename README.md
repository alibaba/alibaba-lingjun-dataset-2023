# Alibaba GPU Cluster Dataset 2023

We released the dataset we used to study the communication contention among deep learning training (DLT) jobs in GPU clusters.
Some of the findings are summarized in the paper,

Jiamin Cao, Yu Guan, Kun Qian, Jiaqi Gao, Wencong Xiao, Jianbo Dong, Binzhang Fu, Dennis Cai, Ennan Zhai, Alibaba Cloud. 2024. Crux: GPU-Efficient Communication Scheduling for Deep Learning Training. In ACM SIGCOMM 2024 Conference (ACM SIGCOMM ’24), August 4–8, 2024, Sydney, NSW, Australia. ACM.

Please cite the paper if you use the dataset :-)

# What is included in the dataset?

This dataset described the information on DLT jobs running in one of our production GPU clusters during two weeks in August 2023.
This cluster consists of more than 800 hosts interconnected by a three-layer Clos network.

We blinded sensitive information such as user ID, cluster ID, and tenant ID for confidential reasons.

The layout of the dataset:

1. `job.csv`: Contains information about each job, including the job name, ID, type (e.g., PyTorch and TensorFlow),
model (e.g., ResNet, GPT, and LLama), start time, end time, etc.

2. `worker.csv`: Contains information about each worker of each job, 
including the associated host IP and resource usage (e.g., GPUs and CPUs), etc.

3. `topo.csv`: Contains information about the network topology of the cluster.
Each row in `topo.csv` corresponds to a host and specifies its location within the three-layer Clos network,
i.e., which ASW (ToR switch), PSW (aggregation switch), and DSW (core switch) it is connected to.

Based on above information,
we can identify which jobs (and models) were running on which GPUs of which hosts at any given time,
as well as the interconnections among these GPUs.
By further assuming computation and communication workloads (since we do not know the specific hyperparameters of the running jobs),
we can estimate the overall distribution of computation and communication on the cluster.



