Running jobs on the cluster
=============================

There are multiple ways to run jobs on the cluster. Some software such as Relion have built in ways to submit jobs. Jobs can also be submitted via a script from the command line. We have created multiple helper scripts to make job submission as easy as possible.

Helper script locations: /mnt/hpc_users/share/bin

.. list-table:: Script locations and usage
   :widths: 25 25 45
   :header-rows: 1

   * - Script
     - Purpose
     - Usage
   * - submit_to_a100.sh
     - submits a command to the a100 queue
     - submit_to_a100.sh *your command*
   * - submit_to_a5000.sh
     - submits a commmand to the a5000 queue
     - submit_to_a5000.sh *your command*
   * - submit_to_cpu.sh
     - submits a command to the cpu queue
     - submit_to_cpu.sh 

   * - alphafold-monomer.sh
     -  
     -  
   * - alphafold-multimer.sh
     - 
     - 
.. list-table:: Relion script locations and usage
     :widths: 25 25 45
     :header-rows: 1
  
     * - Script
       - Purpose
       - Usage
     * - relion_template_cpu_mpi.sh
       - 
       - 
     * - relion_template_cpu.sh
       - 
       - 
     * - relion_template_gpu_mpi.sh
       - 
       - 
     * - relion_template_gpu_mpi_limited.sh
       -
       -
     * - relion_template_gpu.sh
       -
       -
   
