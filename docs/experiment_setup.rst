****************
Experiment Setup
****************

After the creation of an experiment folder with ease_createxp 

.. code-block:: bash

   ease_createxp -proto_dir ${PATH2CONF}/${PROTO} -exp_dir ${PATH2CONF}/${EXPNAME} -b_dir ${LUSTRE}/RUNS/${SYSTEM}/${VERSION} -c_dir ${PATH2CONF}/${PROTO}/sbld/expdtree.yml -host ${ECF_HOST} -storage 'default' -exemode REA -nens_in 000 

unless the PROTO experiment folder in not properly configured already, it is necessary to adjust the configuration that has been just created. The configuration
is specified as follows:

.. code-block:: bash

    cd ${PATH2CONF}/${EXPNAME}
    /sbld/
        assim.yml       # configuration parameters for MROA and BIAS 
        expdtree.yml    # structure of folder (not necessary to modify)
        model.yml       # configuration parameters of NEMO
        modules.yml     # specify modules to load for each group of tasks
        obsopr.yml      # configuration of noobs
        site.yml        # paths for troika configuration / ecflow jobs logs / path of conda ease_env 
        system.yml      # specify paths of calc folder / output folder / structure of output folder
        tasks.yml       # specify resources to assign to each group of tasks



.. collapse:: example of assim.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/assim.yml
            
    :caption: Example of assim.yml     
         


