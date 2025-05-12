***************
Python Programs
***************

.. _ease_env-label:

Install EASE conda environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Several programs of IBIRYS36 are coded in python. Before installing them is 
better to create a common conda environment. If you have access to MOi gitlab
repository you can clone the ease repository 

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




Install Python Programs Environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The python programs of IBIRYS36 require a specific environment. This is defined in the following configuration
file

.. code-block:: yml


    name: ease_env
    channels:
      - https://nexus.mercator-ocean.fr/repository/conda-proxy
      - defaults
    dependencies:
      - _libgcc_mutex=0.1=main
      - _openmp_mutex=5.1=1_gnu
      - blas=1.0=mkl
      - brotli=1.0.9=h5eee18b_7
      - brotli-bin=1.0.9=h5eee18b_7
      - bzip2=1.0.8=h7b6447c_0
      - c-ares=1.19.1=h5eee18b_0
      - ca-certificates=2023.12.12=h06a4308_0
      - cartopy=0.21.1=py310h1176785_0
      - certifi=2023.11.17=py310h06a4308_0
      - contourpy=1.2.0=py310hdb19cb5_0
      - cycler=0.11.0=pyhd3eb1b0_0
      - fonttools=4.25.0=pyhd3eb1b0_0
      - freetype=2.12.1=h4a9f257_0
      - giflib=5.2.1=h5eee18b_3
      - intel-openmp=2021.4.0=h06a4308_3561
      - jpeg=9e=h5eee18b_1
      - kiwisolver=1.4.4=py310h6a678d5_0
      - krb5=1.20.1=h568e23c_1
      - lcms2=2.12=h3be6417_0
      - ld_impl_linux-64=2.38=h1181459_1
      - lerc=3.0=h295c915_0
      - libbrotlicommon=1.0.9=h5eee18b_7
      - libbrotlidec=1.0.9=h5eee18b_7
      - libbrotlienc=1.0.9=h5eee18b_7
      - libcurl=8.2.1=h91b91d3_0
      - libdeflate=1.17=h5eee18b_1
      - libedit=3.1.20230828=h5eee18b_0
      - libev=4.33=h7f8727e_1
      - libffi=3.3=he6710b0_2
      - libgcc-ng=11.2.0=h1234567_1
      - libgomp=11.2.0=h1234567_1
      - libnghttp2=1.52.0=ha637b67_1
      - libpng=1.6.39=h5eee18b_0
      - libssh2=1.10.0=h37d81fd_2
      - libstdcxx-ng=11.2.0=h1234567_1
      - libtiff=4.5.1=h6a678d5_0
      - libuuid=1.41.5=h5eee18b_0
      - libwebp=1.3.2=h11a3e52_0
      - libwebp-base=1.3.2=h5eee18b_0
      - lz4-c=1.9.4=h6a678d5_0
      - matplotlib-base=3.8.0=py310h1128e8f_0
      - mkl=2021.4.0=h06a4308_640
      - mkl-service=2.4.0=py310h7f8727e_0
      - mkl_fft=1.3.1=py310hd6ae3a3_0
      - mkl_random=1.2.2=py310h00e6091_0
      - munkres=1.1.4=py_0
      - ncurses=6.4=h6a678d5_0
      - openjpeg=2.4.0=h3ad879b_0
      - openssl=1.1.1w=h7f8727e_0
      - packaging=23.1=py310h06a4308_0
      - pillow=10.0.1=py310ha6cbd5a_0
      - pip=23.3.1=py310h06a4308_0
      - proj=9.3.1=he5811b7_0
      - pyparsing=3.0.9=py310h06a4308_0
      - pyproj=3.6.1=py310h6370d16_0
      - pyshp=2.1.3=pyhd3eb1b0_0
      - python=3.10.4=h12debd9_0
      - python-dateutil=2.8.2=pyhd3eb1b0_0
      - readline=8.2=h5eee18b_0
      - setuptools=68.2.2=py310h06a4308_0
      - shapely=2.0.1=py310h006c72b_0
      - six=1.16.0=pyhd3eb1b0_1
      - sqlite=3.41.2=h5eee18b_0
      - tk=8.6.12=h1ccaba5_0
      - wheel=0.41.2=py310h06a4308_0
      - xz=5.4.5=h5eee18b_0
      - zlib=1.2.13=h5eee18b_0
      - zstd=1.5.5=hc292b87_0
      - pip:
        - alabaster==0.7.16
        - babel==2.14.0
        - bcrypt==4.1.2
        - beautifulsoup4==4.13.3
        - blinker==1.7.0
        - blosc2==2.4.0
        - bs4==0.0.2
        - cffi==1.16.0
        - cftime==1.6.3
        - charset-normalizer==3.3.2
        - click==8.1.7
        - cloudpickle==3.0.0
        - combine-delta==0.0.1
        - configparser==7.2.0
        - coverage==7.4.0
        - cryptography==41.0.7
        - dask==2022.5.2
        - docutils==0.20.1
        - exceptiongroup==1.2.0
        - fast-histogram==0.12
        - flask==3.0.0
        - fsspec==2023.12.2
        - geos==0.2.3
        - gsw==3.6.16.post1
        - h5netcdf==1.3.0
        - h5py==3.10.0
        - idna==3.6
        - imagesize==1.4.1
        - iniconfig==2.0.0
        - itsdangerous==2.1.2
        - jinja2==3.1.3
        - joblib==1.3.2
        - llvmlite==0.38.1
        - locket==1.0.0
        - lxml==5.1.0
        - markupsafe==2.1.3
        - moiinterptools==0.0.13
        - mpi4py==3.1.3
        - mpl-scatter-density==0.7
        - msgpack==1.0.7
        - ndindex==1.7
        - netcdf4==1.5.8
        - noobs==1.17.12
        - numba==0.55.2
        - numexpr==2.8.8
        - numpy==1.22.4
        - pandas==1.4.2
        - paramiko==3.4.0
        - partd==1.4.1
        - pluggy==1.3.0
        - properscoring==0.1
        - py-cpuinfo==9.0.0
        - py4ease==0.0.124
        - pycparser==2.21
        - pyfiglet==0.8.post1
        - pygments==2.17.2
        - pykdtree==1.3.5
        - pynacl==1.5.0
        - pyregrid==1.2.5
        - pytest==7.4.4
        - pytest-cov==4.1.0
        - pytz==2023.3.post1
        - pyyaml==6.0.1
        - requests==2.31.0
        - rsam2f==0.0.3
        - scikit-learn==1.3.2
        - scipy==1.8.1
        - seawater==3.3.4
        - siphonf==0.1.3
        - snowballstemmer==2.2.0
        - soupsieve==2.6
        - sphinx==7.2.6
        - sphinx-rtd-theme==3.0.2
        - sphinxcontrib-applehelp==1.0.8
        - sphinxcontrib-devhelp==1.0.6
        - sphinxcontrib-htmlhelp==2.0.5
        - sphinxcontrib-jquery==4.1
        - sphinxcontrib-jsmath==1.0.1
        - sphinxcontrib-qthelp==1.0.7
        - sphinxcontrib-serializinghtml==1.1.10
        - style==1.1.0
        - suncalc==0.1.2
        - sysdiag==0.0.3995
        - tables==3.9.2
        - threadpoolctl==3.2.0
        - tomli==2.0.1
        - toolz==0.12.0
        - typing-extensions==4.12.2
        - tzdata==2023.4
        - update==0.0.1
        - urllib3==2.1.0
        - werkzeug==3.0.1
        - xarray==2022.3.0
    prefix: /path/to/your/environments/conda/envs/ease_env  #modify this!


Before installing the IBIRYS36 python program you have to activate ease_env. It is convenient
to gather all the programs needed by IBIRYS36 in the same folder. In this guide it will be called
$IBIRYS36_PROGRAMS_PATH. 


Install NOOBS
^^^^^^^^^^^^^

NOOBS is the observation operator

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/noobs.git
    cd noobs/
    pip install ./

Install Pyhana
^^^^^^^^^^^^^^

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:mhamon/pyhana.git
    cd pyhana/;
    pip install -e ./
    cd pyhana/hana/;
    make clean; make

Install py4ease
^^^^^^^^^^^^^^

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:internal/py4ease.git
    cd py4ease/
    pip install ./


****************
Fortran Programs
****************

Install BIAS
^^^^^^^^^^^^^^

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_202403 git@gitlab.mercator-ocean.fr:olegallou/bias.git
    cd bias/
    sbatch compile.sub


Install MROA
^^^^^^^^^^^^^^

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b RE_IBIdev_2024 git@gitlab.mercator-ocean.fr:ctestut/MROA.git
    cd MROA/
    sbatch compile_MROA.sub


Install MROATOOLS
^^^^^^^^^^^^^^

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone -b oper_EIS202211 git@gitlab.mercator-ocean.fr:ctestut/MROATOOLS.git
    cd MROATOOLS/
    sbatch compile_MROATOOLS.sub

Install NEMO3.6
^^^^^^^^^^^^^^^^

.. code-block:: bash

    cd $IBIRYS_PROGRAMS_PATH
    git clone git@gitlab.mercator-ocean.fr:internal/nemo3.6_ibirys36.git 
    cd nemo3.6_ibirys36/NEMOGCM/CONFIG/
    sbatch compile_NEMO_3.6.sub # set CONFIG=NEATL36



