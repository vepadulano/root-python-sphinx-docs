.. ROOT Python features documentation documentation master file, created by
   sphinx-quickstart on Tue Mar 23 10:25:15 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

ROOT Python features documentation
==============================================================

This documentation aims at describing functionality of ROOT classes and functions which can be accessed within Python.
An example:

.. py:function:: ROOT.RDF.MakeNumpyDataFrame(npyarrays : dict) -> ROOT.RDataFrame

    Create an RDataFrame from a Python dictionary of numpy arrays.

    :param npyarrays: The numpy arrays holding the data.
    :type npyarrays: dict

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   distrdf/introduction

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
