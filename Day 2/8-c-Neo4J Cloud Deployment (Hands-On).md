Neo4j cloud VMs
===============

Basics and file Locations
-------------------------

Based on the Ubuntu distribution of Linux

Must not modify the /etc/neo4j/neo4j.conf file directly, but rather
modify /etc/neo4j/neo4j.template

The system service that restarts Neo4j calls a shell script called
pre-neo4j.sh

VM configuration
----------------

-   In cloud environments, much of the external configuration
    environment may change

-   A machine may have a different IP address or a different set of tags
    when it restarts

-   Because of this, the pre-neo4j.sh script dynamically overwrites the
    normal neo4j.conf file each time the system service starts

-   As a result, you must configure the template to do those
    substitutions and not the configuration file itself, as it will be
    automatically overwritten.

Neo4j on Amazon EC2
===================

Deploying Neo4j on Amazon EC2.
------------------------------

-   There are several options for running Neo4j on AWS EC2, depending on
    what you want to do.

Host a Single Instance of Neo4j on AWS
--------------------------------------

(1) Open the AWS EC2 console, and select Images \> AMIs

(2) Search type -- **Public Images** instead of Owned by me

(3) Search for either \"**neo4j-enterprise**\"

(4) You will know you are using the right one when you see the \"Owner\"
    field showing this number: **385155106615**

(5) AMI ID should be - **ami-068fb3b64fc6d34ed**

(6) Locate the AMI ID and create VM from it

> ![](media/image1.png){width="7.268055555555556in"
> height="2.252083333333333in"}

(7) Add these ports in network security group - 22 7474 7473 7687

![](media/image2.png){width="7.268055555555556in"
height="1.8895833333333334in"}

(8) **Note:** Make sure to create and download the Private Key

(9) Now, let's navigate to https://\[PublicIP\]:7474 and login

    1.  User name / Password: neo4j/ neo4j.

    2.  **Change Password:** secret

(10) SSH into the instance

     1.  Username - ubuntu

     2.  Use Private SSH Key instead of password

Neo4j on Microsoft Azure
========================

Single instances
----------------

a)  **Open:**

> <https://azuremarketplace.microsoft.com/en-us/marketplace/apps/neo4j.neo4j-enterprise-4-1-series?tab=Overview>

Deploy VM following the interactive prompts.

b)  Note Public IP of the VM

c)  **Browse:**

    a.  **Username/Password:** neo4j/neo4j

    b.  **Change Password:** secret

Causal Clusters
---------------

a)  **Open:**

> <https://azuremarketplace.microsoft.com/en-us/marketplace/apps/neo4j.neo4j-enterprise-causal-cluster?tab=Overview>
>
> Deploy following the interactive prompts
>
> Create a new resource group to hold the artifacts of your deployment
>
> Note: Use Standard Disk only. Do not chose SSD

b)  Note Public IP of any of the VM

c)  **Browse:**

d)  **Username/Password:** neo4j/neo4j

### 

### Start using Neo4j Browser

To verify that the cluster has formed correctly, run the following
Cypher statement:

CALL dbms.cluster.overview()

### Access your instance via SSH

Use Mabaxterm to login to the VMs
