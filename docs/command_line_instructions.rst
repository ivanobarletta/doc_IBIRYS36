*************************
Command Line Instructions
*************************

Create An EASE Experiment
^^^^^^^^^^^^^^^^^^^^^^^^^

Once you have installed ease (see :ref:`ease_env-label`), you have a folder with pre-defined 
configurations (ease/configs) that can be used as prototype for a more taylored setup. 

.. code-block:: bash 

    ease_createxp -proto_dir ${PATH2CONF}/${PROTO} -exp_dir ${PATH2CONF}/${EXPNAME} -b_dir ${LUSTRE}/RUNS/${SYSTEM}/${VERSION} -c_dir ${PATH2CONF}/${PROTO}/sbld/expdtree.yml -host ${ECF_HOST} -storage 'default' -exemode REA -nens_in 000



