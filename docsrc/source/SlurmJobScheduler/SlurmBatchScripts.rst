SlurmBatchScripts
===================

This article describes pre-written batch scripts provided for users of the HPC cluster.

Pre-written batch scripts are provided for HPC users in the following cluster location: /mnt/hpc_users/share/bin that is in your $PATH.

    submit_to_a100.sh
        for running command line programs on the cluster a100 nodes
        usage: submit_to_a100.sh *your command* (program name plus arguments)
    submit_to_a5000.sh
        for running command line programs on the cluster a500 nodes
        usage: submit_to_a5000.sh *your command* (program name plus arguments)
    submit_to_gpu.sh
        for running command line programs on the cluster gpu nodes (a100 and a5000)
        usage:
        submit_to_gpu.sh *your command* (program name plus arguments)
    submit_to_cpu.sh
        for running command line programs on the cluster a100 nodes
        usage:

Batch scripts for submitting Relion jobs are here: /mnt/hpc_users/share/sbatch

    relion_template_cpu.sh
        This template is for running Relion jobs that cannot take advantage of GPU processing. On the Relion running tab choose Submit to Queue: yes, Queue name: cpu and Queue submit command: sbatch.

    relion_template_gpu.sh
        This template is for running Relion jobs that can take advantage of GPU processing. On the Relion running tab choose Submit to Queue: yes, Queue name: gpu, a100 or a5000 and Queue submit command: sbatch. One of the other job tabs should have an option to choose Use GPU acceleration: yes.

