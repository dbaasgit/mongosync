# mongosync
cluster-to-cluster sync
Cluster-to-Cluster Sync provides continuous data synchronization or a one-time data migration between two MongoDB clusters in the same or hybrid environments. You can enable Cluster-to-Cluster Sync with the mongosync utility.

mongosync can continuously synchronize data between two clusters. You can use mongosync to create dedicated analytics, development, or testing clusters that mirror your production environment. Synchronized clusters can also support locality requirements for audit and data residency compliance.


In addition to continuous data synchronization, mongosync can also facilitate a one time data migration between clusters.

General Limitations
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

