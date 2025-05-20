************
Requirements
************

Necessary Programs
==================

To install the necessary programs to run IBIRYS36 check the dedicated section :ref:`programs-label`.

Necessary Static Files
======================

Make sure in your filesystem to have a folder with the following structure:

.. code-block:: bash

    assim
    bias_HTS
    MODES
    ocean

Assim
^^^^^

Make sure the assim folder to contain the following:

.. collapse:: ls assim
    
    
    .. literalinclude:: data/lsassim.txt
        :emphasize-lines: 15,15    

    :caption: files to be present in assim folder

with "000IBIRYS36_swnode_zone_nxios32.pck" matching the number of XIOS processes in NEMO runs and 
and that the monthly_climato folder contains the following files:

.. code-block:: bash

   Levitus13/
        Levitus13_Sal_NEATL36m01.nc
        Levitus13_Sal_NEATL36m02.nc
        ...
        Levitus13_Tem_NEATL36m12.nc
        Levitus13_Tem_NEATL36m01.nc
        Levitus13_Tem_NEATL36m01.nc
        ...
        Levitus13_Tem_NEATL36m12.nc
        1990/
            Levitus13_Sal_NEATL36m01.nc -> ../Levitus13_Sal_NEATL36m01.nc
            Levitus13_Sal_NEATL36m02.nc -> ../Levitus13_Sal_NEATL36m02.nc
            ...
            Levitus13_Sal_NEATL36m12.nc -> ../Levitus13_Sal_NEATL36m12.nc
            Levitus13_Tem_NEATL36m01.nc -> ../Levitus13_Tem_NEATL36m01.nc
            Levitus13_Tem_NEATL36m02.nc -> ../Levitus13_Tem_NEATL36m02.nc
            ...
            Levitus13_Tem_NEATL36m12.nc -> ../Levitus13_Tem_NEATL36m12.nc
        2000/
            Levitus13_Sal_NEATL36m01.nc -> ../Levitus13_Sal_NEATL36m01.nc
            Levitus13_Sal_NEATL36m02.nc -> ../Levitus13_Sal_NEATL36m02.nc
            ...
            Levitus13_Sal_NEATL36m12.nc -> ../Levitus13_Sal_NEATL36m12.nc
            Levitus13_Tem_NEATL36m01.nc -> ../Levitus13_Tem_NEATL36m01.nc
            Levitus13_Tem_NEATL36m02.nc -> ../Levitus13_Tem_NEATL36m02.nc
            ...
            Levitus13_Tem_NEATL36m12.nc -> ../Levitus13_Tem_NEATL36m12.nc
        2010/
            Levitus13_Sal_NEATL36m01.nc -> ../Levitus13_Sal_NEATL36m01.nc
            Levitus13_Sal_NEATL36m02.nc -> ../Levitus13_Sal_NEATL36m02.nc
            ...
            Levitus13_Sal_NEATL36m12.nc -> ../Levitus13_Sal_NEATL36m12.nc
            Levitus13_Tem_NEATL36m01.nc -> ../Levitus13_Tem_NEATL36m01.nc
            Levitus13_Tem_NEATL36m02.nc -> ../Levitus13_Tem_NEATL36m02.nc
            ...
            Levitus13_Tem_NEATL36m12.nc -> ../Levitus13_Tem_NEATL36m12.nc
        2020/
            Levitus13_Sal_NEATL36m01.nc -> ../Levitus13_Sal_NEATL36m01.nc
            Levitus13_Sal_NEATL36m02.nc -> ../Levitus13_Sal_NEATL36m02.nc
            ...
            Levitus13_Sal_NEATL36m12.nc -> ../Levitus13_Sal_NEATL36m12.nc
            Levitus13_Tem_NEATL36m01.nc -> ../Levitus13_Tem_NEATL36m01.nc
            Levitus13_Tem_NEATL36m02.nc -> ../Levitus13_Tem_NEATL36m02.nc
            ...
            Levitus13_Tem_NEATL36m12.nc -> ../Levitus13_Tem_NEATL36m12.nc



Static Ocean
^^^^^^^^^^^^

The ocean folder must contain the following:

.. collapse:: ls ocean
    
    
    .. literalinclude:: data/lsocean.txt
        :emphasize-lines: 15,15    

    :caption: files to be present in ocean folder



MODES
^^^^^

Harmonics
=========

To create files containing the tidal harmonics check the dedicated section :ref:`create-harm-label`. 

