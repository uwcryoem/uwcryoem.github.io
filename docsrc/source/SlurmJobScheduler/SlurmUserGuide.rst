Slurm User Guide 
=================

Slurm is a cluster management and job scheduling system for Linux clusters. Slurm has three key functions. First, it allocates access to resources (compute nodes) to users so they can perform work. Second, it provides a framework for starting, executing, and monitoring work on the set of compute nodes. Finally, it manages a queue of pending work.



**Frequently used commands for end users:**

sbatch: Submit a batch script for later execution
****************************************************


.. code-block:: 

   sbatch script.sh  -- submits script.sh to the job queue

srun: Submit a job to run immediately, run parallel tasks in an sbatch file, run an interactive gui job
*********************************************************************************************************

.. code-block::

   srun -N4 -l /bin/hostname -- will run hostname command on 4 nodes

.. code-block::

   srun -n4 -l /bin/hostname -- will run hostname command on 4 processors

**Easy job submission scripts:**

Simple commands can be submitted with the helper scripts provided:

`submit_to_cpu.sh <command arguments>` will submit a command into the CPU partition to run on a node, and can be used to quickly submit commands.

`submit_to_a5000.sh <command arguments>` likewise will submit a command to the A5000 partition to run on NVIDIA A5000 GPU nodes.

`submit_to_a100.sh <command arguments>` will submit to the A100 partition to run on the NVIDIA A100 GPU servers.
`submit_to_gpu.sh <command arguments>` will submit to any available GPU-containing server and request GPU resources.

By default, these GPU scripts request all available (4) GPUs per the server node for the submitted job.

Example here for submitting a command to run on a GPU server:

.. code-block:: 

   submit_to_a100.sh AreTomo -InMrc 1138_G1__L4_TS_001_aligned.st -OutMrc test_a100/tomogram.mrc -VolZ 1350 -AlignZ 1200 -OutBin 6 -DarkTol 0.1 -FlipVol 1 -Kv 300 -PixSize 1.4 -Wbp 1 -AngFile angles.txt -Patch 4 4 -TiltAxis 89.9


$squeue
********

squeue: View information about jobs in scheduling queue. 
   
.. code-block::

   squeue --job 12345      view information about job 12345

.. code-block::

   squeue  --job 12345,12346,12347      view information about about jobs 12345, 12346, 12347



.. list-table:: Job states
   :widths: 50 50
   :header-rows: 1

   * - Code
     - Explanation

   * - BF
     - Boot fail (hardware issue
   
   * - CA 
     - Cancelled
 
   * - CD  
     - Completed

   * - CF 
     - Configuring

   * - CG
     - Completing
 
   * - DL
     - Deadline

   * - F 
     - Failed

   * - NF 
     - Node failed

   * - OOM
     - Out of memory

   * - PD 
     - Pending

   * - PR
     - Job preempted
 
   * - R 
     - Running

   * - RD
     - Reservation deleted

   * - RQ
     - Requeued
  
   * - RH 
     - Held being requeued

   * - RS 
     - Job changing size

   * - RV
     - Job revoked

   * - SI
     - Job bbeing signaled

   * - SE
     - Requeued in special state

   * - SO
     - Staging files

   * - ST 
     - Job stopped

   * - S
     - Job suspended

   * - T 
     - Job terminated





.. list-table:: Examples
       :widths: 10 15 8 6 30
       :header-rows: 1
  
       * - JobID
         - Partition
         - State
         - Nodes
         - Reason


       * - 53
         - cpu
         - PD
         - 1
         - (Resources)

       * - 54
         - gpu
         - running
         - 1 biocsv-01665L
         - ""

       * - 55
         - gpu
         - F
         - 1 biocsv-01665L
         - "" 


$ sinfo
**********

.. list-table:: Sinfo output
   :widths: 20 10 20 10 10 50
   :header-rows: 1

   * - PARTITION 
     - AVAIL  
     - TIMELIMIT  
     - NODES  
     - STATE 
     - NODELIST
 
   * - a100
     - up
     - infinite
     - 2
     - idle
     - biocsv-01624L,biocsv-01625L

   * - a5000
     - up
     - infinite
     - 8 
     - idle
     - biocsv-01661L,biocsv-01662L,biocsv-01663L,biocsv-01664L,biocsv-01665L,biocsv-01666L,biocsv-01667L,biocsv-01668    L

   * - cpu*
     - up
     - infinite
     - 4
     - idle
     - biocsv-01669L,biocsv-01670L,biocsv-01671L,biocsv-01672L



sacct: Get information about pending, completed, and running jobs
*******************************************************************

.. code-block::

   $sacct --starttime 2023-11-1

.. list-table: sacct output
   :widths: 10 15 10 15 10
   :header-rows: 1

   * - JobID
     - JobName
     - Partition
     - AllocCPUS
     - State
 
   * - 235
     - batch 
     - a5000
     - 2
     - RUNNING 


scancel: Signal or cancel jobs, job arrays, or job steps.
***********************************************************

.. code-block::

   $scancel 55


This will cancel job 55. Users can only cancel their own jobs. If you believe another user's job should be cancelled please contact the HPC team.

Types of Nodes:
******************


.. list-table:: Cluster Hardware
   :widths: 25 25 25 25 25 50
   :header-rows: 1

   * - Compute Nodes
     - GPU
     - Memory
     - CPU
     - Number of Nodes
     - Use

   * - a100
     - 4x Nvidia a100
     - 512 GB
     - 2x AMD 48 cores
     - 2
     - Machine learning jobs

   * - a5000
     - 4x Nvidia a5000
     - 512 GB
     - 1x AMD 64 cores
     - 8 
     - Conventional GPU processing jobs

   * - cpu
     - none
     - 256 GB
     - 1x AMD 64 cores
     - 4
     - Interactive sessions and non-GPU processing

   * - r5000
     - 4x Nvidia rtx 5000 Ada generation
     - 512 GB
     - 1x AMD 64 cores
     - 2
     - Conventional GPU processing jobs




**login node** - node that schedules jobs for the compute nodes

    Used for data staging and submission of jobs into the SLURM cluster.
    No local job running or CPU-intensive processes.

**a100** - uses Nvidia A100 GPUs - 2 of these compute nodes available

    a100 nodes are best for intensive machine learning jobs

**a5000** - uses Nvidia A5000 GPUs - 8 of these compute nodes available

    a5000 nodes are best used for conventional GPU processing jobs

**r5000** - uses Nvidia RTX 5000 Ada GPUs - 2 of these compute nodes available

    r5000 nodes are best uses for conventional GPU processing jobs

**cpu** - uses CPU only - no GPU - 4 of these compute nodes available

    cpu nodes are best used for interactive sessions, and non-GPU work

Using GPUs in jobs: 
********************
example script:

.. code-block::

   #!/bin/bash
   #SBATCH --partition=a5000 --nodelist=biocsv-01662L   --gres=gpu:3. #use 3 gpus for job
    srun --gres=gpu:1 hostname. #use 1 gpu for this command

**Control where job output goes:**

use --chdir=*your directory* to do work in your directory (can be mounted file system ie. /mnt/remote/user
use --output=*your directory*/slurm-%j.out ie. /tmp/

example script:

.. code-block::

   #!/bin/bash
   #SBATCH --partition=a5000 --nodelist=biocsv-01662L   --gres=gpu:3
   #SBATCH --chdir=/mnt/remote
   #SBATCH --output=/tmp/slurm-%j.out
   srun --gres=gpu:1 hostname >> myfile.txt


***SSH instructions: ***

Some users will be able to access the main Slurm login node via SSH to run commands. To request this access please email cryoem@biochem.wisc.edu

.. code-block::

    ssh -YC <NetID>@wisc.edu@cryoemcluster.biochem.wisc.edu   

| (Include -YC for X11 forwarding for any applications that require X11 windows such as RELION or IMOD).






More Slurm documentation available at: https://slurm.schedmd.com/
