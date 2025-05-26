.. _experiment-setup-label:

****************
Experiment Setup
****************

After the creation of an experiment folder with ease_createxp (see :ref:`create-exp-label` for more details)

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
    pre/
    run/
    post/


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

The folders pre, run and post contain further yml description files with paths that need to be correctly spcified. The EASE documentation 
gives more insights on the `Experiment Configuration <https://internal.pages.mercator-ocean.fr/ease/configs.html>`_.

The pre,run and post folder must contain the following files:

.. code-block:: bash

    pre/bdyf.yml                                # modify dbase path
    pre/obs.yml                                 # modify dbase path
    pre/atmf.yml                                # modify dbase path
    pre/outputdir.yml
    run/assim/bias/delta.yml
    run/assim/bias/namelist_bias
    run/assim/bias/namelist_pyregrid_preBIAS.nml        # modify dirweights,maskin,maskout paths
    run/assim/cassim.yml                                
    run/assim/interpdelta/namelist_pyregrid_BIAS.nml    # modify maskin,maskout paths
    run/assim/mroa/definestatevector.xml                # modify paths
    run/assim/mroa/oce/definecov_oce.txt                
    run/assim/mroa/oce/defineroa_oce.txt
    run/assim/mroa/oce/definestructdta_oce.txt
    run/assim/mroa/oce/mroanml_ctl_oce
    run/assim/mroa/oce/mroanml_obs_oce
    run/model/000/README.namelists
    run/model/000/README.rst
    run/model/000/bgc/namelist_pisces_cfg
    run/model/000/bgc/namelist_pisces_ref
    run/model/000/bgc/namelist_top_cfg
    run/model/000/bgc/namelist_top_ref
    run/model/000/ocean/namelist_ref
    run/model/000/ocean/namelist_cfg
    run/model/000/xios/axis_def.xml
    run/model/000/xios/domain_def.xml
    run/model/000/xios/field_def.xml
    run/model/000/xios/file_def.xml
    run/model/000/xios/file_def_crs.xml
    run/model/000/xios/grid_def.xml
    run/model/000/xios/iodef.xml
    run/model/cmodel.yml
    run/obsopr/cobsopr.yml
    run/obsopr/noobs/NOOBS_modelgrid.nml
    post/cmxz/plt_cmxz_2d.yml
    post/cplot.yml
    post/ola/ola2dia_regions.yml
    post/ola/ola2dia_regions_ice.yml
    post/ola/plt_ola_2d.yml
    post/storagedir.yml

where the comments indicate paths that must be set properly.

