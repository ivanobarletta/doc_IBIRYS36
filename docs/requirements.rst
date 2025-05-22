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

where the files in the 1990,2000,2010,2020 folders are simply links to the root directory.


BIAS
^^^^

The bias_HTS folder must contain the following:

.. code-block:: bash

    EN4.2.0/
        1990/
        2000/
        2010/
            EN4.2.0_01_Sal_mercator_1degree_fortran.nc
            EN4.2.0_01_Tem_mercator_1degree_fortran.nc
            EN4.2.0_02_Sal_mercator_1degree_fortran.nc
            EN4.2.0_02_Tem_mercator_1degree_fortran.nc
            EN4.2.0_03_Sal_mercator_1degree_fortran.nc
            EN4.2.0_03_Tem_mercator_1degree_fortran.nc
            EN4.2.0_04_Sal_mercator_1degree_fortran.nc
            EN4.2.0_04_Tem_mercator_1degree_fortran.nc
            EN4.2.0_05_Sal_mercator_1degree_fortran.nc
            EN4.2.0_05_Tem_mercator_1degree_fortran.nc
            EN4.2.0_06_Sal_mercator_1degree_fortran.nc
            EN4.2.0_06_Tem_mercator_1degree_fortran.nc
            EN4.2.0_07_Sal_mercator_1degree_fortran.nc
            EN4.2.0_07_Tem_mercator_1degree_fortran.nc
            EN4.2.0_08_Sal_mercator_1degree_fortran.nc
            EN4.2.0_08_Tem_mercator_1degree_fortran.nc
            EN4.2.0_09_Sal_mercator_1degree_fortran.nc
            EN4.2.0_09_Tem_mercator_1degree_fortran.nc
            EN4.2.0_10_Sal_mercator_1degree_fortran.nc
            EN4.2.0_10_Tem_mercator_1degree_fortran.nc
            EN4.2.0_11_Sal_mercator_1degree_fortran.nc
            EN4.2.0_11_Tem_mercator_1degree_fortran.nc
            EN4.2.0_12_Sal_mercator_1degree_fortran.nc
            EN4.2.0_12_Tem_mercator_1degree_fortran.nc
        2020/            
    mask_3D_gridbias05_3dvar_eNEATL36.nc
    mask_3D_gridbias05_z23_3dvar_eNEATL36.nc
    maskfull_3D_gridbias05_3dvar_eNEATL36.nc
    weights/
        weights_bilin_BIAS05-IBI36RYS_gridt.nc
        weights_bilin_BIASreg-IBI36RYS_gridt.nc
        weights_bilin_IBI36RYS-BIAS05full_gridt.nc



Static Ocean
^^^^^^^^^^^^

The ocean folder must contain the following:

.. collapse:: ls ocean
    
    
    .. literalinclude:: data/lsocean.txt
        :emphasize-lines: 61,61    

    :caption: files to be present in ocean folder

and that the rnf_forcing folder contains the files:

.. code-block:: bash

   CATALOG_RUNOFF_BGC
   runoff_BIO_clim_T.nc
   runoff_BIO_T_y1992.nc
   runoff_BIO_T_y1993.nc
   ...
   runoff_BIO_T_y2024.nc


MODES
^^^^^

Harmonics
=========

To create files containing the tidal harmonics check the dedicated section :ref:`create-harm-label`. 

