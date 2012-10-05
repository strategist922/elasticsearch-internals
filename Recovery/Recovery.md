Recovery
========

Recovery is the 2nd big action performed when a node starts up, happening after the Discovery phase.  The role of Recovery is to resolve the nodes indice state; to ensure it has a consistent view of the contents of each index the cluster knows about, and ensures it can start participating in search and index requests.

The basic sequence of Recovery is:

1. Work out what the known indices of the cluster are
2. *(This needs checking)* Based on Allocation logic, determine which shards this node should be responsible for
3. determine which node in the cluster holds the primary shard for each shard within an index this node needs to Recover
4. Setup communication channels between this node and the primary shard holder
5. Submit to the primary shard holder details of existing index data this node has for comparison
6. Resolve missing/out-of-date shard index information by receiving from the primary shard holder correct data.
7. *(is this delete down during recovery or later??)*  Remove any local storage for index/shards this node is not responsible for

When a node starts up, it retrieves meta-data about the indices within the cluster from the [Gateway](http://www.elasticsearch.org/guide/reference/modules/gateway/).  Within the root of the Gateway location is a 'metadata' directory, which contains a 'metadata-' prefixed file, suffixed with an integer which is an incremental number each time the cluster indice state changes.  

metadata-[0-9]*
================
This metadata- file is a binary format file containing listings all the indices known by the cluster (since the last snapshot), the # replicas and other various high level settings via the [IndexMetaData](https://github.com/elasticsearch/elasticsearch/blob/67d86de7eafbb78b2d5a1faa046bb13290de12ed/modules/elasticsearch/src/main/java/org/elasticsearch/cluster/metadata/IndexMetaData.java) class.


