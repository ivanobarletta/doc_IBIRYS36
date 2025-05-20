******
ISSUES
******

Hints on the Server Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

One of the issues observed is related to the init_family_vars tasks. This task is implemented
as a Python script that needs to be run in the proper environment, defined by the python version
that appears in the shebang of the script. 

To be sure of using the proper python environment there are 2 possibilities:

* create the server AFTER having activated the ecflow conda environment.
* modify the absolute path of python version in the shebang to point to the desired python version.

Jobs Marked as Submitted but Not Appearing in the Scheduler
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This kind of issue is likely to be appointed in bad spelling of the sbatch job header of the task(s) involved.

If you use the GUI to queue / re-queue the task or the family, these will be marked out as "submitted" in the GUI 
regardless any possible error in the job submission to the scheduler. In case these jobs / tasks do not appear
among the scheduled jobs check for possible misspelling in the job header:

.. code-block:: bash 

    #!/bin/bash
    #SBATCH --output=/mnt/lustre/scratch/nlsas/home/empresa/now/iba/RUNS/IBIRYS36/test0/ecflow-jobs//emnowiba_NEATL36_ASSIM_test0/pre/recup_obs_R20230823-20250513-1034.1
    #SBATCH -J recup_obs.1-test0-20230823
    #SBATCH --reservation=TEST
    #SBATCH -N 1
    #SBATCH --ntasks-per-node=1
    #SBATCH --time=00:15:00
    #SBATCH --mem=1G
    #SBATCH --no-requeue
    #SBATCH --mail-type=FAIL
    #SBATCH --mail-user=ivano.barletta@nowsystems.eu
    export JOB_ID=${SLURM_JOBID}

In the example above the job script assumes that the reservation named "TEST" is active. If the node reservation is not active the job
will not be submitted while the ecFlow server assumes that it has been. 

In case no spelling errors are present, in order to troubleshoot you can go to the ecflow-jobs folder, search for the specific job and submit it
manually:

.. code-block:: bash

   sbatch task_name.job1

and check for issues concerning inconsistency in the demand of resources or other issues.
