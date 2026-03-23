Advanced Slurm Concepts
=========================

Request a variable number of workers:

You can request a variable number of compute nodes by including a range in your Sbatch script. The code below will request between 2 and 4 nodes depending on how many cluster resources are idle. 

.. code-block:: 
    #SBATCH --nodes=2-4 


Job Arrays: 
Job arrays allow you to submit similar jobs quickly.

sbatch --array=0-10
