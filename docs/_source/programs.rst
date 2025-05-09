********
Programs
********

Install EASE conda environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Several programs of IBIRYS36 are coded in python. Before installing them is 
better to create a common conda environment. If you have access to MOi gitlab
repository you can

.. code-block:: bash

    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/ease.git ease
    conda env create -f conda-env.yml
    conda activate ecflow
    cd ease/
    pip install ./



Install NOOBS
^^^^^^^^^^^^^

NOOBS is the observation operator

.. code-block:: bash

    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/noobs.git
    cd noobs/
    pip install ./



