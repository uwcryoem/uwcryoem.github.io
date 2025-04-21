About Slurm
==============

Slurm is an open-source job scheduling and management tool for Linux clusters. Slurm has three key functions. First, it allocates access to resources (compute nodes) to users so they can perform work. Second, it provides a framework for starting, executing, and monitoring work on the set of compute nodes. Finally, it manages a queue of pending work.



Definitions:

Cluster – set of computers for high-performance computing

Head node – computer from which users can submit jobs

Compute nodes – computers that jobs will be assigned by the scheduler. Users do not log in directly.

Partition (or Queue) – a pool of nodes from some part of the cluster
Ex. “GPU”, ”A5000”, “A100” and “CPU” (what hardware is available in each queue in the cryoemcluster.biochem.wisc.edu)

