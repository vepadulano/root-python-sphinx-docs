Automatic partitioning of a ROOT dataset
========================================

In order to distribute the workload over multiple cluster nodes, the input ROOT
dataset is automatically partitioned. The number of partitions can be decided by
the user, otherwise ROOT will try to guess a right number of partitions for the
analysis.

The ROOT TTree data is by design saved in chunks, called clusters, that
represent the smallest amount of data that can be read from disk without reading
other portions of the dataset.

Before sending the computation to the cluster, the input files of the RDataFrame
are queried just enough to retrieve the information needed to build the list of
clusters of the dataset, that looks like the following::


    [
        (0, 100, 0, ("filename_1.root", 0)),
        (100, 200, 0, ("filename_1.root", 0)),
        ...,
        (10000, 10100, 10000, ("filename_2.root", 1)),
        (10100, 10200, 10000, ("filename_2.root", 1)),
        ...,
        (n, n+100, n, ("filename_n.root", n)),
        (n+100, n+200, n, ("filename_n.root", n)),
        ...
    ]


Then the algorithm will transform this list into a list of ``Range`` objects
like the following::


    [
        Range(start=0,
            end=42287856,
            filelist=['Run2012B_TauPlusX.root',
                        'Run2012C_TauPlusX.root'],
            friend_info=None),
        Range(start=6640348,
            end=51303171,
            filelist=['Run2012C_TauPlusX.root'],
            friend_info=None)
    ]

Each worker node on the distributed cluster will receive only the contents of a
``Range`` object and will run the computation graph on those entries.