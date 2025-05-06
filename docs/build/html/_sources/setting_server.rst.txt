****************************
Setting up The Ecflow Server
****************************

The functionality of the suite relies on the configuration of the server, which is the central
point. For details on the ecflow server capabilities / functionalities check the page 

    https://ecflow.readthedocs.io/en/5.14.0/glossary.html#term-ecflow_server

Setting up PORT and HOST
^^^^^^^^^^^^^^^^^^^^^^^^

The essential parameter associated to the ecflow server are the PORT and the HOST variables. The PORT and the HOST
are used to interact with the server in case there are different servers active on the same machine. 

.. code-block:: bash

   ecflow_client --port=4545 --host=hostname --stats

this will interact only with the server identified with port=4545 and host=hostname. 

It is advisable to set up the ecflow server by running the script ecflow_start.sh. The script, though, does 
not allow to create a server with a specific hostname but only allows to specify the port through command line
argument. The hostname is taken from the prompt

.. code-block:: bash

   [username@hostname ~]$ 

where hostname, on FTIII, is NOT always the same. One workaround is to do ssh into the desired hostname, and then
run the ecflow_start.sh script

.. code-block:: bash

   ssh username@desired-hostname
   ecflow_start.sh -p port_number


