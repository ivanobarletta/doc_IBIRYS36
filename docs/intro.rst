*************
Introduction
*************

The present documentation gathers up the relevant steps made to port the `IBI Reanalysis <https://data.marine.copernicus.eu/product/IBI_MULTIYEAR_PHY_005_002/description>`_ system software 
framework on the FinisTerraeIII (FTIII) machine. Such framework is grounded on a set of programs (FORTRAN and Python)
coordinated within a workflow. The workflow for this assimilation system is designed by Mercator Ocean International
(MOi) and build by means of `EASE <https://internal.pages.mercator-ocean.fr/ease/index.html>`_ package that creates
the formal definition of the workflow (in short, the definition file) that can be handled by `ecflow <https://ecflow.readthedocs.io/en/5.13.7/>`_ 
server, that constitutes the core of the workflow. 

In short, EASE can be seen as a wrapper to ecflow, with the aim of simplifying the construction of the workflow. 



