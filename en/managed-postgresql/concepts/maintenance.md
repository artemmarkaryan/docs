# Maintenance

Maintenance means:

* Automatic installation of DBMS updates and revisions for hosts (including disabled clusters).
* Changes to the host class and storage size.
* Other maintenance activities.

In {{ mpg-name }} single-host clusters, a master host undergoes maintenance. So, such a cluster becomes unavailable if a master host needs to be restarted during maintenance.

In multi-host clusters, the maintenance procedure is as follows:

1. [Replica hosts](replication.md) undergo maintenance consecutively. The replicas are queued randomly. A replica becomes unavailable while it's being restarted during maintenance.
1. A master host undergoes maintenance and gets updated. If it's restarted during maintenance and becomes unavailable, one of the replicas assumes its role.

   If you access the cluster using the FQDN or IP address of the master host, such a cluster may become unavailable. To make your application continuously available, access the cluster using a [special FQDN](../operations/connect.md#using-fqdn-master) always pointing to the master host.

Changing a DBMS version isn't part of maintenance. For more information about version changes, see [{#T}](../operations/cluster-version-update.md).