Recovery
========

Recovery is the 2nd big action performed when a node starts up, happening after the Discovery phase.  The role of Recovery is to resolve the nodes indice state; to ensure it has a consistent view of the contents of each index the cluster knows about, and ensures it can start participating in search and index requests.

When a node starts up, it retrieves meta-data about the indices within the cluster from the [Gateway](http://www.elasticsearch.org/guide/reference/modules/gateway/).  Within the root of the Gateway location is a 'metadata' directory, which contains a 'metadata-' prefixed file, suffixed with an integer which is an incremental number each time the cluster indice state changes.  

metadata-[0-9]*
================
This metadata- file is a binary format file containing listings all the indices known by the cluster (since the last snapshot), the # replicas and other various high level settings via the [IndexMetaData](https://github.com/elasticsearch/elasticsearch/blob/67d86de7eafbb78b2d5a1faa046bb13290de12ed/modules/elasticsearch/src/main/java/org/elasticsearch/cluster/metadata/IndexMetaData.java) class.

