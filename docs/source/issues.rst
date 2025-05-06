******
ISSUES
******

Hints on the Server Configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

One of the issues observed is related to the init_family_vars tasks. This task is implemented
as a Python script that needs to be run in the proper environment, defined by the python version
that appears in the shebang of the script. 

To be sure of using the proper python environment there are 2 possibilities:

* create the server AFTER having activated the ecflow conda environment.
* modify the absolute path of python version in the shebang to point to the desired python version.


