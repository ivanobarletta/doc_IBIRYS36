*********
Resources
*********

Graphical User Interface (GUI)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Suite State Visualization 
^^^^^^^^^^^^^^^^^^^^^^^^^

Using the GUI is not always possible or, when it is, can be cumbersome in case of low connection. As an alternative to the GUI, the 
suite status can be visualized in a brief manner through the script 

.. collapse:: ecflow_get_state.sh

    .. literalinclude:: data/ecflow_get_state.sh

    :caption: ecflow_get_state.sh

with simple usage. First make the script executable and copy it in your ~/bin

.. code-block:: bash

    chmod u+x ecflow_get_state.sh
    cp ecflow_get_state.sh ~/bin

then execute it specifying the name of the suite:

.. code-block:: bash 

    ecflow_get_state.sh nameOfYourSuite # without .def!

Specifying the name of the suite is necessary only in case you have more than one loaded in your server. In case you have only 
one just type:

.. code-block:: bash 

    ecflow_get_state.sh 

.. image:: docs/data/ecflow_get_state_example.png
   
   Example output from ecflow_get_state.sh 
