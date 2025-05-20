.. _create-harm-label:

**********************
Create Harmonics Files
**********************

Some files need to be treated without the contribution of tides. The removal of tide effect from fields is done through pyhana, that
requires static files that contatin tidal harmonics informations. 

The pyhana requires, additionally, that the number of files containing the harmonics informations equals the number of XIOS tasks
used in the NEMO computations. More specifically, pyhana requires files organized in the following manner:

.. code-block:: bash

    path/to/temp_harmonic_analysis_computation/
        0000/res_harm_ssh_0000.nc
        0001/res_harm_ssh_0001.nc
        0002/res_harm_ssh_0002.nc
        ..
        ..

        0031/res_harm_ssh_0031.nc
        
            
where "res_harm_ssh_????.nc" are the aforementioned files for the case of 32 XIOS processes. Setting the following paths

.. code-block:: bash

    DIRRUN=/path/to/temp_harmonic_analysis_computation/                         # path where to create harmonics files
    DIRDAT=/path/to/your/static/ocean/                                          # path with static ocean files
    DIRNML=/path/to/RUNS/IBIRYS36/{nameoftest}/paraminput/obsopr/FCST/M000/     # path containing noobs namelist


and assuming that the file containing the harmonics for the whole domain is in ${DIRDAT} and is named tide_dta_grid_T.nc and 
that the NOOBS namelist is in ${DIRNML} and is named like NOOBS_modelgrid_R{cycledate}.nml you can do the following:

.. code-block:: bash

    NTASK=32                                                                                    # set the # of XIOS tasks
    NTASKM1=$(( ${NTASK} -1 ))

    mkdir -p $DIRRUN                                                                            # force creation of out folder
    
    prefix=tide_elev_
    
    cd ${DIRRUN}
    # Split tides
    cp ${DIRDAT}/tide_dta_grid_T.nc ${prefix}FULL.nc
    cp ${DIRNML}/NOOBS_modelgrid_R{cycledate}.nml NOOBS.nml
    
    envName=/mnt/netapp2/Store_uni/home/empresa/now/iba/tools/ease_lib_IBIRYS36/ease_env        # activate the ease_env 
    conda activate ${envName}                                                                   # to use noobs programs      
    
    noobs_split -f ${prefix}FULL.nc -nxios ${NTASK}                                             # use noobs to split the file
    #for i in $(seq 0 ${NTASKM1}); do printf -v ii "%04d" $i; mkdir -p ${ii}; mv ${prefix}${ii}.nc ${ii}/;done
    for i in $(seq 0 ${NTASKM1}); do printf -v ii "%04d" $i; mv ${prefix}${ii}.nc ${ii}/;done   # move and rename
    rename ${prefix} res_harm_ssh_ */*.nc
    
    # Rename harmonics
    for i in $(seq 0 ${NTASKM1}); do                                                            # rename variables
       printf -v ii "%04d" $i
       echo "---------$ii---------"
       for harm in K1 K2 M2 M4 Mf Mm N2 O1 P1 Q1 S2; do
          ncrename -v .${harm}_z1,${harm}_x_elev ${ii}/res_harm_ssh_${ii}.nc;
          ncrename -v .${harm}_z2,${harm}_y_elev ${ii}/res_harm_ssh_${ii}.nc;
       done
    done

This will create the desired files to be used by pyhana. 
