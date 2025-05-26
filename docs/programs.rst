.. _programs-label:

*****************
IBIRYS36 Programs
*****************

This section is dedicated to the programs involved in the IBIRYS36 workflow.

.. _ease_env-label:

Install EASE conda environment
==============================

It is convenient to create a conda environment that has both EASE and Ecflow functionalities. If you have access to MOi gitlab
repository you can clone the EASE repository 

.. code-block:: bash

    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/ease.git ease

In the root directory of the repository there is the description file of the conda environment 
to create. Before using it, it is recommended to append to conda-env.yml the prefix directive

.. code-block:: bash
   
    cd ease/
    echo "prefix: /path/to/your/environments/conda/envs/ecflow" >> conda-env.yml
    conda env create -f conda-env.yml
    conda activate ecflow
    pip install ./

This environment contains both executables of EASE and Ecflow (under the /bin directory). It is convenient to include this
directory in the $PATH variable in your .bashrc

.. code-block:: bash

   export PATH=${PATH}:/path/to/your/environments/conda/envs/ecflow/bin

Python Programs
===============


Install Python Programs Environment
"""""""""""""""""""""""""""""""""""

The python programs of IBIRYS36 require a specific environment. This is defined in the following configuration
file


.. collapse:: ibirys36_env.yml

    .. literalinclude:: data/ibirys36_env_ibirys36.yml

    :caption: Conda environment for IBIRYS36 programs  


Before installing the IBIRYS36 python program you have to activate the ibirys36_env. It is convenient
to gather all the programs needed by IBIRYS36 in the same folder. In this guide it will be called
$IBIRYS36_PROGRAMS_PATH. 


Install NOOBS
"""""""""""""

NOOBS is the observation operator used in the IBIRYS36 assimilation method. After activating the ibirys36_env to install NOOBS do:

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/noobs.git
    cd noobs/
    pip install ./

Install Pyhana
""""""""""""""

Pyhana is the program used to remove the tidal trend from NEMO model outputs. To install it do the following:

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:mhamon/pyhana.git
    cd pyhana/;
    pip install -e ./
    cd pyhana/hana/;
    make clean; make

Install py4ease
"""""""""""""""

py4ease is a set of tools to handle files created in the workflow and is part of the IBIRYS36 set of programs

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/py4ease.git
    cd py4ease/
    pip install ./


Fortran Programs
================

The following are the remaining Fortran programs that IBIRYS36 is grounded on. Make sure of loading the 
proper modules on your HPC system before compiling.

Install BIAS
""""""""""""

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_202403 git@gitlab.mercator-ocean.fr:olegallou/bias.git
    cd bias/
    sbatch compile.sub


Install MROA
""""""""""""

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:ctestut/MROA.git
    cd MROA/
    sbatch compile_MROA.sub


Install MROATOOLS
"""""""""""""""""

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b oper_EIS202211 git@gitlab.mercator-ocean.fr:ctestut/MROATOOLS.git
    cd MROATOOLS/
    sbatch compile_MROATOOLS.sub

Install NEMO3.6
""""""""""""""""

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone git@gitlab.mercator-ocean.fr:internal/nemo3.6_ibirys36.git 
    cd nemo3.6_ibirys36/NEMOGCM/CONFIG/
    sbatch compile_NEMO_3.6.sub # set CONFIG=NEATL36




