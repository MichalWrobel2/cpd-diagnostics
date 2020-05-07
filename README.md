# Cloud Pak For Data Serviceability CLI

##### Overview
Cloud Pak For Data Serviceability CLI provides range of commands to help diagnose and fix cluster services when user interface is not available.


##### Commands
```
cpdcli
```
Root command. Launches CLI in interactive mode

```
auth
```
Sends authorization request to the cluster the user is working with.
Consumes accounts managed with Cloud Pak For Data

```
diagnostics
```
Calls diagnostics API to collect container and custom logs for Cloud Pak For Data and add-ons.
Requires serviceability service and its dependecies to be up and running.

```
healthcheck
```
Calls serviceability service and reports about nodes availabity, top cpu and memory pods, persistent volume claims, gluster status and events.

```
openshift-diagnostics
```
Gathers information about nodes, pods with logs, persistent volume claims, persistent volumes, storage classes, projects(namespaces).
This command requires API address and token and is completely independent from Cloud Pak For Data services.
