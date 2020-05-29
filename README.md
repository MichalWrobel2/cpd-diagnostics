#### Logs Collection via CLI
In case, cloud pak for data user interface is not accessible, the system provides a command line interface to collect logs. 

**Prereqs**
* Access to a machine to run the command line utility 
    * This can be any x86 machine running RHEL, Windows or iOS (mac)
    * The machine should be able to reach the infrastructure node of the cluster on port 8443 and 443 ports. Sometimes infrastructure nodes are clubbed with master nodes so in that case, one should be able to reach the master nodes on the above-mentioned ports

* Have credentials to connect to CPD
    * You must know the credentials for a cloud pak for data user on CPD with administrator privileges
    * You must know the cloud pak for data URL
* Have credentials to connect to Openshift Cluster API server (optional)
    * This is a required if users are not able to reach the CPD User Interface and we would need to fall back on openshift to collect diagnostics
    * You must know the API server URL
    * You must know the username and password with cluster privileges.

**Steps**

Download the cli command suitable for your operating system from github
https://github.com/IBM-ICP4D/cpd-diagnostics.git

1. Execute the utility to collect **health metrices** information with following option
    ```
    -a  Openshift API server URL < cpd-xyz.demo.ibmcloudpack.com:8443 >
    -d  Cloud Pak for data URL < zen-cpd-zen.apps.XXX.com>
    -u  Cloud Pak for data User with administrator role <admin>
    -p  Password to authenticate the Cloud pak for data user 
    -t  Access token from Openshift. This can be requested by logging into the Openshift console or from cli with authenticated oc command by running – oc whoami -t
    ```
    Here is a sample command line 
    ```
    ./cpdcli healthcheck  -a cpd-xyz.demo.ibmcloudpack.com:8443 -d zen-cpd-zen.apps.XXX.com -u admin -p mypassword -t K7NQsPy-GHxG4oL5GkOoOVX2Sfl7j5UBW3AQe6Angk0
    ```
    
2. Execute the utility to collect diagnostic logs with following option
    ```
    -a  Openshift API server URL < cpd-xyz.demo.ibmcloudpack.com:8443 >
    -d  Cloud Pak for data URL < zen-cpd-zen.apps.XXX.com>
    -u  Cloud Pak for data User with administrator role <admin>
    -p  Password to authenticate the Cloud pak for data user 
    -t  Access token from Openshift. This can be requested by logging into the Openshift console or from cli with authenticated oc command by running – oc whoami -t
    ```
    Here is a sample command line 
    ```
    ./cpdcli diagnostics  -d zen-cpd-zen.apps.XXX.com -u admin -p mypassword
    ```
    The utility authenticates the user and provides option to pick the components. Select the “IBM Cloud Pak For Data” as mandatory and rest based on the issue being reported. If you are not sure which components would be relevant, pick all of them.

    On successful execution a job is submitted in the background and  a request ID is generated.
    
3. Check the status of the job
    The status of job can be retrieved by running passing `-j` option
    ```
    -a  Openshift API server URL < cpd-xyz.demo.ibmcloudpack.com:8443 >
    -d  Cloud Pak for data URL < zen-cpd-zen.apps.XXX.com>
    -u  Cloud Pak for data User with administrator role <admin>
    -p  Password to authenticate the Cloud pak for data user 
    -t  Access token from Openshift. This can be requested by logging into the Openshift console or from cli with authenticated oc command by running – oc whoami -t
    -j  Retrieves status of all the diagnostics jobs
    ```
    Here is a sample command line
    ```
    ./cpdcli diagnostics  -d zen-cpd-zen.apps.XXX.com -u admin -p mypassword  -j
    ```
    
4. Download the logs
    Once the status of log collection finishes from the status above, the logs can be downloaded by passing the job id on the command line
    The status of job can be retrieved by running passing `-j` option
    ```
    -a          Openshift API server URL < cpd-xyz.demo.ibmcloudpack.com:8443 >
    -d          Cloud Pak for data URL < zen-cpd-zen.apps.XXX.com>
    -u          Cloud Pak for data User with administrator role <admin>
    -p          Password to authenticate the Cloud pak for data user 
    -t          Access token from Openshift. This can be requested by logging into the Openshift console or from cli with authenticated oc command by running – oc whoami -t
    -j          Retrieves status of all the diagnostics jobs
    --download  <JOB_ID> Downloads <JOB_ID> logs
    ```
    Here is a sample command line
    ```
    ./cpdcli diagnostics  -d zen-cpd-zen.apps.XXX.com -u admin -p mypassword  --download OiqkKvd
    ```
    
    On successful execution a job is submitted in the background and  a request ID is generated.

    
3. Check the status of the job
    The status of job can be retrieved by running passing `-j` option
    ```
    -a  Openshift API server URL < cpd-xyz.demo.ibmcloudpack.com:8443 >
    -d  Cloud Pak for data URL < zen-cpd-zen.apps.XXX.com>
    -u  Cloud Pak for data User with administrator role <admin>
    -p  Password to authenticate the Cloud pak for data user 
    -t  Access token from Openshift. This can be requested by logging into the Openshift console or from cli with authenticated oc command by running – oc whoami -t
    -j  Retrieves status of all the diagnostics jobs
    ```
    Here is a sample command line
    ```
    ./cpdcli diagnostics  -d zen-cpd-zen.apps.XXX.com -u admin -p mypassword  -j
    ```
    
4. Download the logs
    Once the status of log collection finishes from the status above, the logs can be downloaded by passing the job id on the command line
    The status of job can be retrieved by running passing `-j` option
    ```
    -a          Openshift API server URL < cpd-xyz.demo.ibmcloudpack.com:8443 >
    -d          Cloud Pak for data URL < zen-cpd-zen.apps.XXX.com>
    -u          Cloud Pak for data User with administrator role <admin>
    -p          Password to authenticate the Cloud pak for data user 
    -t          Access token from Openshift. This can be requested by logging into the Openshift console or from cli with authenticated oc command by running – oc whoami -t
    -j          Retrieves status of all the diagnostics jobs
    --download  <JOB_ID> Downloads <JOB_ID> logs
    ```
    Here is a sample command line
    ```
    ./cpdcli diagnostics  -d zen-cpd-zen.apps.XXX.com -u admin -p mypassword  --download OiqkKvd
    ```
