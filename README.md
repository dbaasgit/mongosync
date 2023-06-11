# mongosync
cluster-to-cluster sync
Cluster-to-Cluster Sync provides continuous data synchronization or a one-time data migration between two MongoDB clusters in the same or hybrid environments. You can enable Cluster-to-Cluster Sync with the mongosync utility.

mongosync can continuously synchronize data between two clusters. You can use mongosync to create dedicated analytics, development, or testing clusters that mirror your production environment. Synchronized clusters can also support locality requirements for audit and data residency compliance.


In addition to continuous data synchronization, mongosync can also facilitate a one time data migration between clusters.

**Steps to use this utility**
1. create a bash script called mongosync.sh
   and provice the source and destination cluster information with username and password.
   
   #!/bin/bash
mongosync \
   --cluster0 'mongodb+srv://username:password@cluster0.yjgdosg.mongodb.net' \
   --cluster1 'mongodb+srv://username:password@app.mdp6vhu.mongodb.net'
   
2. use API call to run pause resume and commit the sync 
to start sync process run below API call:-
    curl localhost:27182/api/v1/start -XPOST \
--data '
   {
      "source": "cluster0",
      "destination": "cluster1"
   } '
   
   to check the running and progress:-
   
   curl localhost:27182/api/v1/progress -XGET
   
   to pause the sync:-
   
   curl localhost:27182/api/v1/pause -XPOST --data '{ }'
   
   to resume the sync:-
   
   curl localhost:27182/api/v1/resume -XPOST --data '{ }'
   
   to commit the sync(the final cutover the sync)
    
    curl localhost:27182/api/v1/commit -XPOST --data '{ }'




**General Limitations**

The minimum supported server version is MongoDB 6.0.

The source and destination clusters must have the same release version.

The minimum supported 
Feature Compatibility Version
 is 6.0.

The source and destination clusters must have the same Feature Compatibility Version.

The destination cluster must be empty.

mongosync does not validate that the clusters or the environment are properly configured.

Other clients must not write to the destination cluster while mongosync is running.

If write blocking is disabled, the client must prevent writes to the source cluster before starting the commit process.

Synchronizing a subset of the source data, "Filtered Synchronization", is not supported.

Network compression is not supported.

applyOps
 operations from the source cluster are not supported.

system.* collections
 are not replicated.

Documents that have dollar ($) prefixed field names are not supported. See 
Field Names with Periods and Dollar Signs.

Serverless clusters are not supported.

The MongoDB Shared Tier is not supported.

Queryable Encryption
 is not supported.

