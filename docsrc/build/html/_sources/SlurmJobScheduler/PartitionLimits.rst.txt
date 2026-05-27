
Partition Limits 
=====================================

As more users being using the cluster, we've had to put some limits on the number of processing machines a user can use at one time. Currently, these limits apply to jobs on the A100, A5000 and GPU nodes. For example, I can run jobs on two of the A100 nodes while also running jobs on two of the a5000 nodes. The Open On Demand desktop nodes and the CPU nodes are  currently exempt from this limit. 

It may be useful for some users to request a variable number of nodes at a time. For example, if you want your job to use four nodes but four nodes aren't available you can request one to four nodes. To do this you can use the following in your sbatch script:

.. code-block:: 
    #SBATCH --nodes=1-4 

Please note if you request more than four nodes even in a variable request, your job will not run. 

For example, the following job will never run:

.. code-block:: 
    #SBATCH --nodes=2-5 

