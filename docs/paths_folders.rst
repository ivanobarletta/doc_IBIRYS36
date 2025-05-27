.. _paths-folders-label:

***************
Paths & Folders
***************

To operate properly, the workflow requires the set up of several paths on the filesystem. Navigating the intricate set of directory paths can 
initially be, though, a disorienting experience for first-time users.

This chapter helps to navigate and configure all necessary file paths. 


Configuration Folder
^^^^^^^^^^^^^^^^^^^^

The sbld/ folder in your configurations folder contains the files site.yml and system.yml:

.. code-block:: bash

   /path/to/ease/install/folder/
        configs/
            ${SYSTEM}_ASSIM_${VERSION}/                                 # SYSTEM=NEATL36
                pre/
                run/
                post/
                sbld/
                    ..
                    site.yml
                    system.yml
                    ..

.. container:: code-caption

     **site.yml**

.. code-block:: bash
                      

   # edit please:
   # Third party package ecf_submit information
   troika: '/path/to/conda/envs/ecflow/bin/troika'                     # conda env defined in ease package 
   troika_config: '/path/to/ease/intallation/directory/troika.yaml'    # troika.yaml is in the ease installation dir
   
   # calc information
   calc_host: ${ECF_HOST}  
   calc_user: ${username}
   calc_outdir: path/to/calc_dir/${SYSTEM}/${VERSION}/ecflow-jobs      # calculation directory (see sbld/system.yaml for
                                                                       # definition of calc_dir)
                                                                       # SYSTEM=NEATL36
                                                                       # VERSION=user_choice_name


   front_host: login
   front_host_port: '${ECF_PORT}'
   ecflow_server_dir: /path/to/ecflow_server/                          # directory containint ecflow_server logs and sbatch jobs
                                                                       # of the workflow tasks.
                                                                       # under the directory ecflow_server_dir/ you have:
                                                                       # ecflow_server_dir/
                                                                       #   ${username}_${SYSTEM}_ASSIM_${VERSION}/
                                                                               pre/
                                                                                  ..
                                                                                  recup_atmf.job1
                                                                                  recup_atmf.job1.jid
                                                                                  recup_atmf.job1.orig
                                                                                  recup_atmf.job1.submitlog
                                                                                  ..
                                                                              run/
                                                                                  fcst/
                                                                                      model_run.job1
                                                                                      model_run.job1.jid
                                                                                      model_run.job1.orig
                                                                                      model_run.job1.submitlog
                                                                                      model_run.job2
                                                                                      model_run.job2.jid
                                                                                      model_run.job2.orig
                                                                                      model_run.job2.submitlog

                                                                                   best/
                                                                               post/
                                                                           
                       
   front_user: ${username}
   front_outdir: /path/to/calc_dir/${SYSTEM}/${VERSION}/ecflow-jobs
   
   calc_host_conda_env: /path/to/ibirys36_env
   
   # The suite will be hosted at chain_dir/ecflow/%SUITE_NAME%
   chain_dir: /path/to/ease/installation/directory/ 

Relevant paths are:

    * troika: path to troika executable
    * calc_out_dir: folder where you have sbatch job files and standard output / error of the tasks
    * front_out_dir: same as calc_out_dir (depending on the machine architecture, these paths might differ, but not in FT3 case) 
    
The system.yml allows to provide more details, such as the structure of calc directory


.. container:: code-caption

   **system.yml**

.. code-block:: bash 


   config: NEATL36
   system: IBIRYS36
   expnam: test0                   # to be changed 
   exemode_capital: REA
   # Suite directories
   # Dir at local ecflow server host
   exp:
     config_dir: '/path/to/ease/installation/directory/configs/${SYSTEM}_ASSIM_${VERSION}'
     postdir: '{exp.config_dir}/post'
     predir: '{exp.config_dir}/pre'
     run: '{exp.config_dir}/run'
   
   # Dir at calc host
   dir_calc:
     base_dir: '/path/to/calc_dir/RUNS'                                        # this path defines the directory were
                                                                               # all computations are done. see next section
                                                                               # for more details    

     selected_data: '{dir_calc.base_dir}/{system}/{expnam}/SELECT_DATA'        # structure of RUNS dir
     atm_forcing: '{dir_calc.base_dir}/{system}/{expnam}/ATM_FORCING/'
     bdy_forcing: '{dir_calc.base_dir}/{system}/{expnam}/BDY_FORCING/'
     obc_forcing: '{dir_calc.base_dir}/{system}/{expnam}/OBC_FORCING/'
     static: '{dir_calc.base_dir}/{system}/staticinput'
     exe: '{dir_calc.base_dir}/{system}/{expnam}/config'
     tmp: '{dir_calc.base_dir}/{system}/{expnam}'
     param: '{dir_calc.base_dir}/{system}/{expnam}/paraminput'
   # Dir and type of storage host
   storage:
     dir: '/path/to/outputs/{system}/{expnam}'                                 # directory where assimilation cycle are 
                                                                               # stored.            
     fsys: 'default'
   ### From herein all should be revisited. MOI_dirout_xxx will be constructed in init_envvars
   dirout:
     log: 'LOG'
     build: 'BUILD'
     ola: 'OLA'
     dia: 'DIA'
     dup: 'DUP'
     rst: 'RESTART'
     cmxz: 'CMXZ'
     free:
       cdf: 'FREE/CDF'
       state: 'FREE/STATE'
       stat: 'FREE/STAT'
       moorings: 'FREE/MOORINGS'
     now:
       cdf: 'FCST/CDF'
       state: 'FCST/STATE'
       stat: 'FCST/STAT'
       moorings: 'FCST/MOORINGS'
     ana:
       cdf: 'BEST/CDF'
       state: 'BEST/STATE'
       stat: 'BEST/STAT'
       moorings: 'BEST/MOORINGS'
   # cleanup frequency in number of cycles
   cleanup_freq:
     log: "100"
     ola: "100"
     dup: "3"  # comm between noobs and MROA
     modes: "3"
     dia: "100"
     ncdf: "3"
     cmxz: "3"
     stat: "3"
     rst: "3"
     mooring: "100"
     list: "MOI_cleanup_freq_log:MOI_dirout_log
            MOI_cleanup_freq_ola:MOI_dirout_ola
            MOI_cleanup_freq_dup:MOI_dirout_dup
            MOI_cleanup_freq_cmxz:MOI_dirout_cmxz
            MOI_cleanup_freq_dia:MOI_dirout_dia
            MOI_cleanup_freq_dia:MOI_dirout_binnedola
            MOI_cleanup_freq_mooring:MOI_dirout_fcst_mooring
            MOI_cleanup_freq_ncdf:MOI_dirout_fcst_cdf
            MOI_cleanup_freq_stat:MOI_dirout_fcst_stat
            MOI_cleanup_freq_mooring:MOI_dirout_best_mooring
            MOI_cleanup_freq_ncdf:MOI_dirout_best_cdf
            MOI_cleanup_freq_stat:MOI_dirout_best_stat
            MOI_cleanup_freq_mooring:MOI_dirout_free_mooring
            MOI_cleanup_freq_ncdf:MOI_dirout_free_cdf
            MOI_cleanup_freq_stat:MOI_dirout_free_stat
            MOI_cleanup_freq_rst:MOI_dirout_restart"
   


Execution Folder
^^^^^^^^^^^^^^^^

The resulting execution folder looks like the following:

.. code-block:: bash 

    /path/to/calc_dir/RUNS/${SYSTEM}/
        staticinput/
        ${VERSION}/
            ATM_FORCING/
            BDY_FORCING/
            BIAS/
            ecflow-jobs/
                ${username}_${SYSTEM}_ASSIM_${VERSION}/
                    pre/
                        ...
                        recup_statics.job1                          # sbatch job script for recup_statics task
                        recup_statics_R20230823-20250404-0919.1     # standard output / error of task with cycle date and actual
                        recup_statics_R20230823-20250404-1202.1     # run date / time
                        recup_statics_R20230823-20250404-1205.1
                        recup_statics_R20230823-20250408-0800.1
                        recup_statics_R20230823-20250408-1012.1
                        ...
                    run/
                    post/
            MODEL_SSH/
            MODES/
            OBC_FORCING/
            paraminput/
            R20230816M000_000/
            R20230823M000_000/
            SELECT_DATA/
            TMPRUN/




Outputs Folder
^^^^^^^^^^^^^^


