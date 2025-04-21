Slurm User Guide 
=================

Slurm is a cluster management and job scheduling system for Linux clusters. Slurm has three key functions. First, it allocates access to resources (compute nodes) to users so they can perform work. Second, it provides a framework for starting, executing, and monitoring work on the set of compute nodes. Finally, it manages a queue of pending work.

Users will access the main Slurm login node via SSH to run commands.

ssh -YC <NetID>@wisc.edu@cryoemcluster.biochem.wisc.edu

(Include -YC for X11 forwarding for any applications that require X11 windows such as RELION or IMOD).

Frequently used commands for end users:
sbatch: Submit a batch script for later execution

sbatch script.sh
srun: Submit a job to run immediately, run parallel tasks in an sbatch file, run an interactive gui job
srun -N4 -l /bin/hostname -- will run hostname command on 4 nodes
srun -n4 -l /bin/hostname -- will run hostname command on 4 processors

Easy job submission scripts:

Simple commands can be submitted with the helper scripts provided:

`submit_to_cpu.sh <command arguments>` will submit a command into the CPU partition to run on a node, and can be used to quickly submit commands.

`submit_to_a5000.sh <command arguments>` likewise will submit a command to the A5000 partition to run on NVIDIA A5000 GPU nodes.

`submit_to_a100.sh <command arguments>` will submit to the A100 partition to run on the NVIDIA A100 GPU servers.
`submit_to_gpu.sh <command arguments>` will submit to any available GPU-containing server and request GPU resources.

By default, these GPU scripts request all available (4) GPUs per the server node for the submitted job.

Example here for submitting a command to run on a GPU server:

submit_to_a100.sh AreTomo -InMrc 1138_G1__L4_TS_001_aligned.st -OutMrc test_a100/tomogram.mrc -VolZ 1350 -AlignZ 1200 -OutBin 6 -DarkTol 0.1 -FlipVol 1 -Kv 300 -PixSize 1.4 -Wbp 1 -AngFile angles.txt -Patch 4 4 -TiltAxis 89.9
squeue: View information about jobs in scheduling queue. 
   
   squeue -- jobs 12345      view information about job 12345
   squeue  --jobs 12345, 12346, 12347             view information about about jobs 12345, 12346, 12347

$ squeue
 

  JOBID    PARTITION NAME  USER ST       TIME  NODES NODELIST(REASON)
    53       cpu script.s user PD       0:00      1 (Resources)
    54       cpu script.s user PD       0:00      1 (Priority)
    55       cpu script.s user PD       0:00      1 (Priority)
    49       cpu script.s user  R       0:38      1 biocsv-01669L
    50       cpu script.s user  R       0:25      1 biocsv-01670L
    51       cpu script.s user  R       0:22      1 biocsv-01671L
    52       cpu script.s user  R       0:22      1 biocsv-01672L

Job states (ST column):
* Most common states in bold
BF- Boot fail (usually hardware issue - contact Matt or Jennifer)
CA - Canceled
CD - Completed
CF - Configuring
CG - Completing
DL - Deadline (job terminated on deadline)
F - Failed
NF - Node Failed (contact Matt or Jennifer)
OOM - Out of memory
PD - Pending
PR - Job preempted
R - Job currently running
RD - Job being held due to reservation being deleted
RQ - Job being requeued
RH - Held job being requeued
RS - Job is about to change size
RV - Job revoked
SI - Job being signaled
SE - Job requeued in special state
SO - Job is staging out files
ST - Job has been stopped
S - Job has been suspended
TO - Job terminated upon reaching time limit

sinfo: Get information about compute nodes

$ sinfo
PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
a100         up   infinite      2   idle biocsv-01624L,biocsv-01625L
a5000        up   infinite      8   idle biocsv-01661L,biocsv-01662L,biocsv-01663L,biocsv-01664L,biocsv-01665L,biocsv-01666L,biocsv-01667L,biocsv-01668L
cpu*         up   infinite      4   idle biocsv-01669L,biocsv-01670L,biocsv-01671L,biocsv-01672L

sacct: Get information about pending, completed, and running jobs

$ sacct --starttime 2023-11-1
JobID           JobName  Partition  Account    AllocCPUS   State     ExitCode 
------------ ---------- ---------- ---------- ---------- ---------- -------- 
234            hostname_+   a5000              2            FAILED     0:53 
234.batch      batch                           2            CANCELLED  0:53 
235            hostname     a5000              2            FAILED     0:53 

scancel: Signal or cancel jobs, job arrays, or job steps.

scancel 55

   This will cancel job 55. Please don't cancel other user's jobs without speaking with them.

Types of Nodes:

login node - node that schedules jobs for the compute nodes

    Used for data staging and submission of jobs into the SLURM cluster.
    No local job running or CPU-intensive processes.

a100 - uses Nvidia A100 GPUs - 2 of these compute nodes available

    2x AMD 7443 24-Core Processors (total of 96 threads)
    4x A100 GPUs are available
    512 GB total system memory available
    Nodes are reserved for intensive machine learning jobs

a5000 - uses Nvidia A5000 GPUs - 8 of these compute nodes available

    1x AMD EPYC 7713P 64-Core Processor (total of 128 threads)
    4x A5000 GPUs are available
    512 GB total system memory available
    Nodes are best used for conventional GPU processing jobs

r5000 - uses Nvidia RTX 5000 Ada GPUs - 2 of these compute nodes available

    1x AMD EPYC 9534 64-Core Processor (total of 128 threads)
    4x R5000 GPUs are available
    512 GB total system memory
    Nodes are best uses for conventional GPU processing jobs

cpu - uses CPU only - no GPU - 4 of these compute nodes available

    1x AMD EPYC 7713P 64-Core Processor
    No GPUs
    256 GB total system memory available
    Nodes are best used for interactive sessions, and non-GPU work

Using GPUs in jobs: 

example script:
      1 #!/bin/bash
      2
      3 #SBATCH --partition=a5000 --nodelist=biocsv-01662L   --gres=gpu:3. #use 3 gpus for job
      4
      5 srun --gres=gpu:1 hostname. #use 1 gpu for this command

Control where job output goes:
use --chdir=*your directory* to do work in your directory (can be mounted file system ie. /mnt/remote/user
use --output=*your directory*/slurm-%j.out ie. /tmp/

example script:
      1 #!/bin/bash
      2
      3 #SBATCH --partition=a5000 --nodelist=biocsv-01662L   --gres=gpu:3
      4 #SBATCH --chdir=/mnt/remote
      5 #SBATCH --output=/tmp/slurm-%j.out
      6 srun --gres=gpu:1 hostname >> myfile.txt

More Slurm documentation available at: https://slurm.schedmd.com/
