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


Examples of sbld files:
^^^^^^^^^^^^^^^^^^^^^^^

.. collapse:: example of assim.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/assim.yml
            
    :caption: Example of assim.yml     
         
.. collapse:: example of expdtree.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/expdtree.yml
            
    :caption: Example of expdtree.yml     

.. collapse:: example of model.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/model.yml
            
    :caption: Example of model.yml     

.. collapse:: example of modules.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/modules.yml
            
    :caption: Example of modules.yml     

.. collapse:: example of obsopr.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/obsopr.yml
            
    :caption: Example of obsopr.yml     

.. collapse:: example of site.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/site.yml
            
    :caption: Example of site.yml     

.. collapse:: example of system.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/system.yml
            
    :caption: Example of system.yml     

.. collapse:: example of tasks.yml

    .. literalinclude:: data/NEATL36_ASSIM_test0/sbld/tasks.yml
            
    :caption: Example of tasks.yml     


pre, run and post Folders
^^^^^^^^^^^^^^^^^^^^^^^^^

The configuration directory contains also the templates of the namelists for the several IBIRYS36 programs. 



