Cluster policies
===================

HPC Administrator: Jennifer Scheuren jfscheuren@wisc.edu

Most inquiries will be responded to within hours. The HPC cluster team aims to respond to all inquiries within one business day.  


User training:

    Periodic user trainings will be scheduled by HPC staff. In addition, users may request training from the HPC staff.

Project consulting:

    HPC staff are available to consult on use of the HPC cluster for specific projects. To set up an initial meeting please e-mail cryoem@biochem.wisc.edu.

Accounts:

    To request access to the HPC cluster please fill out the following form https://explore.wisc.edu/cryoem_hpc_access_request
    Users in the Department of Biochemistry who are sponsored by a faculty member (PI) may request access to the HPC cluster. Outside users with an MCCET affiliation may also be granted access to the HPC cluster.
    Removal: HPC cluster accounts will be audited each month. UW-Madison users who have not used the cluster in more than three months will be contacted to verify that they still need access. PIs of research groups are responsible for contacting the HPC staff when a user has left their group.
    Locking: Accounts may be locked without warning for users misusing the cluster. If your account is locked, you will receive an e-mail from the HPC staff with steps to unlock your account.  

Guidelines for Use:

    Processing-intensive (and GPU-requiring) jobs must be run on the compute nodes and never on the login node.
    User data should be stored in your home directory. For UW users this is  /mnt/hpc_users/home/NetID.
    Data should be transferred to the cluster via Globus. Instructions for this are `here. <https://uwcryoem.github.io/docs/Storage.html/>`_

Software:

    Commonly used software is available in a shared directory on the cluster at: /mnt/cryofs_applications. These applications include SBGrid and Alphafold.
    Users may request additional software to be added to the cluster.
    Users may install additional software in their home directory.

Security:

    HPC users must comply with all campus IT and Cybersecurity policies. Please see https://it.wisc.edu/ to review these policies. Completion of the Campus Cybersecurity Awareness training is required prior to using the cluster.
    Using sensitive or restricted data such as PII or HIPAA data on the HPC cluster is not permitted. Please see the university policy on handling sensitive data https://it.wisc.edu/learn/handling-sensitive-university-data/ and UW System Administrative Policy 1031.

Downtime and Maintenance:

    If needed, cluster maintenance will occur periodically during off hours.
    Cluster users will be notified in advance of any scheduled maintenance.
    Cluster users will be notified via e-mail of any unplanned emergency maintenance.
    During maintenance periods, currently running jobs will be suspended.  When maintenance is complete, jobs will be resumed. Users will be notified if a job is unable to be resumed or requeued.

Resource Policies:

    The login node (cryoemcluster.biochem.wisc.edu should be used only to ssh into worker nodes. Jobs should not be run on the login node. Any user using significant resources on the login node will be given a warning or have their account locked.
    Large datasets should be removed from the cluster storage when jobs are complete. Cluster space will be audited periodically and users storing large amount of data will be contacted.
    Users may store up to 5TB of data in the cluster. Temporary exceptions to this rule may be granted.
    Data storage will periodically be audited on the cluster. Users will be asked to move data if it has not been accessed in more than two weeks.

Reservations:

For time-sensitive jobs, cluster reservations may be granted. Reservations can include specific nodes or partitions in a specific time frame. E-mail cryoem@biochem.wisc.edu to request a reservation.

Misc. Policies:

    Users should report and acknowledge use of the HPC cluster in publications using the following statement:

“The authors acknowledge resources made available for conducting the research reported in this paper from the Midwest Center for Cryo-ET’s (MCCET) high performance computing (HPC) cluster of the Department of Biochemistry at the University of Wisconsin-Madison, supported by the NIH Common Fund Transformative High Resolution Electron Microscopy program (U24 GM139168).”

    Users should notify the HPC team of any published results.
    Users must abide by all software licensing requirements for cluster software and software installed in their own home directories.

Warnings:

    Use of the cluster is only permitted for CEMRC and MCCET users.
    User data on the cluster is not backed up. In the event of a system failure, user data may be lost. Please copy your data off the cluster as soon as possible when your jobs are complete.
    Users may not share accounts or login information.
    System updates may affect current software support. Every effort will be made to test software on a non-HPC machine prior to updating the cluster. If you experience software issues after an update, please e-mail the HPC team at cryoem@biochem.wisc.edu.
    Using sensitive or restricted data on the HPC cluster is not permitted. Please see the university policy on handling sensitive university data https://it.wisc.edu/learn/handling-sensitive-university-data/ and UW System Administrative Policy 1031.

