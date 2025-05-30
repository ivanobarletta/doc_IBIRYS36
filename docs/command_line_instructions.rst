*************************
Command Line Instructions
*************************

.. _create-exp-label:

Create An EASE Experiment
^^^^^^^^^^^^^^^^^^^^^^^^^

Once you have installed ease (see :ref:`ease_env-label`), you have a folder with pre-defined 
configurations (ease/configs) that can be used as prototype for a more taylored setup. The content of ease/configs folder is like

.. code-block:: bash

    eNEATL36_ASSIM_PROTO
    iORCA025_ERA5_CEP_PROTO
    iORCA025_IFS_CLIMBASIS_PROTO
    iORCA12_ERA5_CLIMBASIS_ECMWF_PROTO
    NEATL36_ASSIM_PROTO


If you want to assume NEATL36_ASSIM_PROTO as prototype of experiment you can set the following

.. code-block:: bash

    PATH2CONF=/path/to/ease/configs
    CONFIG=NEATL36
    SYSTEM=IBIRYS36
    PROTO=${CONFIG}_ASSIM_PROTO
    VERSION=test0
    EXPNAME=${CONFIG}_ASSIM_${VERSION} 
    SUITE=${USER}_$EXPNAME
    LUSTRE=/path/of/calc/dir


And then, after having activated the conda environment for ease executables (:ref:`ease_env-label`) , run the ease command **create_exp** to create the experiment folder

.. code-block:: bash 

    ease_createxp -proto_dir ${PATH2CONF}/${PROTO} -exp_dir ${PATH2CONF}/${EXPNAME} -b_dir ${LUSTRE}/RUNS/${SYSTEM}/${VERSION} -c_dir ${PATH2CONF}/${PROTO}/sbld/expdtree.yml -host ${ECF_HOST} -storage 'default' -exemode REA -nens_in 000

This command generates a folder named NEATL36_ASSIM_test0. For further details on the experiment setup see (:ref:`experiment-setup-label`).

The breakdown of previous command is (run ease_createexp --help for more info)

.. code-block:: bash

    -proto_dir ${PATH2CONF}/${PROTO}            # reference configuration (or prototype)
    -exp_dir ${PATH2CONF}/${EXPNAME}            # configuration folder to be created
    -b_dir ${LUSTRE}/RUNS/${SYSTEM}/${VERSION}  # directory of temporary folders for computation
    -c_dir ${PATH2CONF}/${PROTO}/sbld/expdtree.yml  # structure of folders
    -host ${ECF_HOST}                           # hostname
    -storage 'default' 
    -exemode REA                                # Reanalysis
    -nens_in 000                                # specify the number of ensemble members    


Create workflow Definition File for the Experiment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ease_suitegen generates the definition file of the suite based on the informations found in the folder ${EXPNAME}

.. code-block:: bash 

   ease_suitegen -sname $EXPNAME -sys_arch sbld/site.yml -sys_schd sbld/tasks.yml -sys_modenv sbld/modules.yml -generate_scripts -sys_mode ReaNemo3 -sys_info sbld/system.yml -model_info sbld/model.yml -assim_info sbld/assim.yml -obsopr_info sbld/obsopr.yml -day0 20230823 -dayF 20230823 -rday0 20080102 -lcycle 7 -scheduler slurm -nens 1 -enslim 10 -postlim 10


Run the suite
^^^^^^^^^^^^^

.. code-block:: bash 

    # RUN EXPERIMENT
    ec --load="$SUITE.def" force
    #***** Queue suite
    ec --alter=change defstatus "queued" /${SUITE}
    #***** Lauch suite
    ec --begin="/$SUITE"



Interaction with Ecflow Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The communication with the ecflow server can be made through the command-line program `ecflow_client
<https://ecflow.readthedocs.io/en/5.13.7/glossary.html#term-ecflow_client>`_. 

After the creation of the server the status can be viewed with the command

.. code-block:: bash

    ecflow_client --port=$ECF_PORT --host=$ECF_HOST --stats

An example result is

.. code-block:: bash

   Server statistics
   Version                         Ecflow version(5.9.2) boost(1.78.0) compiler(gcc 10.4.0) protocol(JSON cereal 1.3.0) openssl(enabled) Compiled on Dec  8 2022 23:53:23
   Status                          RUNNING
   Host                            login210-19
   Port                            4040
   Up since                        2025-Apr-02 09:59:46
   Job sub' interval               60s
   ECF_HOME                        /home/empresa/now/iba/ecflow_server
   ECF_LOG                         /mnt/netapp2/Home_FT2/home/empresa/now/iba/ecflow_server/login210-19.4040.ecf.log
   ECF_CHECK                       /home/empresa/now/iba/ecflow_server/login210-19.4040.check
   ECF_SSL                         disabled
   Check pt interval               120s
   Check pt mode                   CHECK_ON_TIME
   Check pt save time alarm        20s
   Number of Suites                0
   Request's per 1,5,15,30,60 min

   Restart server                  1
   Ping                            1
   Get full definition             278
   Server version                  40
   Sync                            618
   Sync full                       390
   Sync suite clock                10
   News                            3084

   Task init                       650
   Task complete                   497
   Task abort                      142

   Load definition                 27
   Begin                           27
   Requeue                         34
   Node suspend                    8
   Node resume                     3
   Node status                     4
   Run                             4
   Force                           95
   Edit script                     9
   Alter                           3874
   Group                           179
   stats cmd                       15

   File job                        30
   File Job out                    13
   File manual                     17

It is advisable to specify the ---port and ---host when using ecflow_client to be sure of pointing to the server createid with
the specific port and host. Check the section with suggestions on how to create the server :ref:`port-host-label` 

The ecflow_client command use can be sped up by means of an alias in your .bashrc

.. code-block:: bash

    export ECF_HOST=login210-19     # host and port used to start the server
    export ECF_PORT=4040

    alias ec="ecflow_client --port=${ECF_PORT} --host=${ECF_HOST}"

To load a definition file of a suite do:

.. code-block:: bash

    ecflow_client --port=${ECF_PORT} --host=${ECF_HOST} --load=suite_name.def 

if suite_name.def is already loaded the last command will raise an error. If you want to force the 
loading of the suite just add **force** to the command

.. code-block:: bash

    ecflow_client --port=${ECF_PORT} --host=${ECF_HOST} --load=suite_name.def force 

The command line allows a full interaction with the ecFlow server. The manual can be accessed through

.. code-block:: bash

    ecflow_client --help


or, to get a general view on the commands with a brief description

.. code-block:: bash

   ecflow_client --help=summary


The command line allows to execute single tasks of a given suite

.. code-block:: bash

   ecflow_client --port=${ECF_PORT} --host=${ECF_HOST}  --run=/suite_name/f1/t1

The last command might lead to undesired outcome, since the **run** command does not check if the given task depends on other. The **run** command should be used in case the dependencies (such as files produced by previous tasks / namelist ) required by such tasks are already satisfied.    

For further details on the ecflow_client commands you can check out the  
`Command Line Interface (CLI) <https://ecflow.readthedocs.io/en/5.13.7/client_api/index.html>`_ section in the **ecFlow** documentation. 

To check the **state** of your workflow type the following:

.. code-block:: bash

    ecflow_client --port=${ECF_PORT} --host=${ECF_HOST} --get_state                 # if you have only 1 suite loaded
    ecflow_client --port=${ECF_PORT} --host=${ECF_HOST} --get_state=${suiteName}    # specify which suite if you
                                                                                    # more than 1 loaded           


The previous command gives an exhaustive summary but also very long. You can consider of filtering the output as follows:

.. code-block:: bash

   ecflow_client --port=${ECF_PORT} --host=${ECF_HOST} --get_state=${suiteName} grep --color=always -E "suite | task | family "

to get only the lines for the suite name, families and tasks.  

.. collapse:: example of get_state output

    .. literalinclude:: data/example_get-state.txt

    :caption: Example of get_state

