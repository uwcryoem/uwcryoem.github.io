Open Composer
===================

Open Composer is an application for creating and submitting jobs on the HPC Cluster via Open OnDemand.
Open Composer can be accessed on the main Open OnDemand page or via the Apps dropdown in Open OnDemand.


.. image:: /images/OpenComposer.png
  :width: 600
  :alt: Image of the Open OnDemand UI showing the OpenComposer app button

---------------------------------
Open Composer Quick Start Guide
---------------------------------

1. After opening the Open Composer app click on the Slurm Workload Manager button to open the Slurm application.
2. You will see a form where you can control various settings for your job.

	* Script Location (required) - Choose the location your script will be created in your home directory on the cluster

	* Script Name (required) - Select the name your script will be saved as in the script locations

	* Job Name (optional) - Select a name for your job. This name will show up as on the Job History page.

	* Partition: Select the partition you'd like the job to run on. For jobs requiring a GPU you should use the a100, a5000, or gpu queue. For jobs requiring only cpus, choose the cpu queue. Partition hardware information is `here <https://uwcryoem.github.io/GettingStarted/Hardware.html>`_.

	* Number of Cores: Select the number of CPU cores you'd like for your job. 