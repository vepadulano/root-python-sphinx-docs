ROOT.RDF.Experimental.Distributed
=================================

RDataFrame supports distributing applications through external backends such as
Apache Spark or Dask, through the use of the python package
`ROOT.RDF.Experimental.Distributed`. In this package the submodule `Backends`
includes all the supported backends for distributed execution, which in turn
expose their own `RDataFrame` object. The aim is to support the same API as
`ROOT.RDataFrame`, so that an example application may look like::


    import ROOT

    # Point RDataFrame calls to the Spark specific RDataFrame
    RDataFrame = ROOT.RDF.Experimental.Distributed.Spark.RDataFrame

    # It still accepts the same constructor arguments as traditional RDataFrame
    df = RDataFrame("mytree","myfile.root")

    # Continue the application with the traditional RDataFrame API

.. toctree::
    :maxdepth: 2
    :caption: Contents:

    api
    clustered_ranges