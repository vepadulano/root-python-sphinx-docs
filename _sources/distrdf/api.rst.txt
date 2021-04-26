API docs
=============

.. py:function:: ROOT.RDF.Experimental.Distributed.Spark.RDataFrame(*args[, sparkcontext : pyspark.SparkContext, npartitions : int]) -> DistRDF.DataFrame

    RDataFrame factory function for the `Spark` backend submodule. Supports the same input
    parameters as `ROOT.RDataFrame`

    :param pyspark.SparkContext sparkcontext: A SparkContext object to connect this RDataFrame to a Spark cluster.
    :param int npartitions:  Desidered number of partitions to split the input data. Each partition will correspond to
        a task on the distributed workers.

.. py:function:: ROOT.RDF.Experimental.Distributed.initialize(fun, *args, **kwargs) -> None

    Set a function that will be executed as a first step on every backend before
    any other operation. This method also executes the function on the current
    user environment so changes are visible on the running session.

    This allows users to inject and execute custom code on the worker
    environment without being part of the RDataFrame computational graph.

    :param fun: Function to be executed
    :param list args: Variable length argument list used to execute the function
    :param dict kwargs: Keyword arguments used to execute the function
