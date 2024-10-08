# Chakshu Services Documentation

## Overview

Chakshu is installed on almost every cluster we manage. The main directory where all Chakshu-related files are stored is located at:

`/home/apps/chakshu`

This documentation focuses on the specific services related to Chakshu, which are found under:

`/home/apps/chakshu/systemd_services`

# Cluster Structure

Before diving into the services, it's important to understand the general structure of the cluster and how different nodes are connected.

## Nodes Overview

1. **Login Node**: When you log in to the cluster, you typically land on the login node. However, for managing Chakshu services, the login node is not required.

2. **Mgmt Node**: This is the primary node used for managing Chakshu-related services.

3. **Master Node**: In some clusters, Chakshu services might be present on the master node instead of the mgmt node.

![alt text](image.png)

## Node Usage

**Mgmt Node**: This is the preferred node for managing Chakshu services.

**Master Node**: If the services are not found on the mgmt node, check the master node.

## Chakshu Services

The following are the key services related to Chakshu that can be found on either the mgmt or master node but mostly present on mgmt nodes:

### 1. `gunicornd.service`

**Description**: This service starts the C-Chakshu Server using `gunicorn`.

Commands:


**`sudo systemctl start gunicornd.service`**

**`sudo systemctl stop gunicornd.service`**

**`sudo systemctl status gunicornd.service`**



### 2. `master-chakshud.service`
**Description**: This service runs the **aquire_general_data.py** script, which is essential for data acquisition in Chakshu.

Commands:

**`sudo systemctl start master-chakshud.service`**

**`sudo systemctl stop master-chakshud.service`**

**`sudo systemctl status master-chakshud.service`**


### 3. `mongod.service`
**Description**: This service activates the MongoDB Database Server, which is crucial for storing and managing data used by Chakshu.

Commands:

**`sudo systemctl start mongod.service`**

**`sudo systemctl stop mongod.service`**

**`sudo systemctl status mongod.service`**

### 4. `node-chakshud.service`
**Description:** This service is deployed on CN, GPU, and HM nodes and runs the aquire_node_data.py script for data collection.

Managing Services on CN, GPU, and HM Nodes:

Get Node Information: Use sinfo to format node information for pdsh:

sinfo -o %N

check Service Status: From the master node, use pdsh to check the status of node-chakshud.service on CN, GPU, and HM nodes. Note that you need root privileges:


**`sudo pdsh -w cn[001-235],gpu[01-23],hm[001-255] "systemctl status node-chakshud.service"`**

Copy Service File: If the service file is not present on the nodes, copy it to /etc/systemd/system:

**`sudo pdsh -w cn[001-235],gpu[01-23],hm[001-255] "cp /home/apps/chakshu/systemd_services/node-chakshud.service /etc/systemd/system"`**


Reload Systemd: After adding or modifying service files, reload the systemd manager configuration:


**`sudo pdsh -w cn[001-235],gpu[01-23],hm[001-255] "systemctl daemon-reload"`**


Start the Service:


**`sudo pdsh -w cn[001-235],gpu[01-23],hm[001-255] "systemctl start node-chakshud.service"`**


Stop the Service:


**`sudo pdsh -w cn[001-235],gpu[01-23],hm[001-255] "systemctl stop node-chakshud.service"`**


Restart the Service:


**`sudo pdsh -w cn[001-235],gpu[01-23],hm[001-255] "systemctl restart node-chakshud.service"`**


