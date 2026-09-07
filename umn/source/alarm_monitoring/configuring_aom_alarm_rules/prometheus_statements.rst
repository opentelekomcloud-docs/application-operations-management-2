:original_name: mon_01_0043.html

.. _mon_01_0043:

Prometheus Statements
=====================

AOM is interconnected with Prometheus Query Language (PromQL), which provides various built-in functions. These functions can be used to filter and aggregate metric data. You can run Prometheus statements to add metrics.

Prometheus Statement Syntax
---------------------------

For details about the Prometheus statement syntax, go to the `Prometheus official website <https://prometheus.io/docs/prometheus/latest/querying/basics/>`__.

Examples of Using Prometheus Statements
---------------------------------------

-  **Example 1: Memory usage of a specified pod in a node (excluding the control node)**

   -  Define variables:

      -  Used memory of the containers in a pod (a pod may contain multiple containers or instances): **aom_container_memory_used_megabytes**
      -  Total memory of the node: **aom_node_memory_total_megabytes**

   -  Query logic:

      -  For **aom_container_memory_used_megabytes**, use the aggregation function **sum** to calculate the actual used memory of a specified pod under a specified node based on the node IP address and pod ID.
      -  For **aom_node_memory_total_megabytes**, use the aggregation function **sum** to calculate the total memory of a specified node based on the node IP address.
      -  Both of them are filtered **by node IP address**. Therefore, the obtained metric values have the same metric dimension. (Only the values are different.)
      -  The actual memory usage of the pod can be obtained by performing the "/" operation on the values of the preceding two metrics.

   -  To query the actual memory usage of the pod, use the following statement:

      .. code-block::

         sum(aom_container_memory_used_megabytes{podID="2261xxxxxxxxfc1213",nodeIP="192.xx.xx.xx"}) by (nodeIP) / sum(aom_node_memory_total_megabytes{nodeIP="192.xx.xx.xx"}) by (nodeIP)

-  **Example 2: CPU usage of a specified pod in a node (excluding the control node)**

   -  Define variables:

      -  Used CPU cores of the containers in a pod: **aom_container_cpu_used_core**
      -  Actual total number of CPU cores of the node: **aom_node_cpu_limit_core**

   -  Query logic:

      -  For **aom_container_cpu_used_core**, use the aggregation function **sum** to calculate the used CPU cores of a specified pod under a specified node based on the node IP address and pod ID.
      -  For **aom_node_cpu_limit_core**, use the aggregation function **sum** to calculate the total CPU cores of a specified node based on the node IP address.
      -  Both of them are filtered by node IP address. Therefore, the obtained metric values have the same metric dimension. (Only the values are different.)
      -  The actual memory usage of the pod can be obtained by performing the "/" operation on the values of the preceding two metrics.

   -  To obtain the actual CPU usage of the pod, use the following statement:

      .. code-block::

         sum(aom_container_cpu_used_core{nodeIP="192.xx.xx.xx ",podID="3361xxxxxxxxab1613"}) by (nodeIP) / sum(aom_node_cpu_limit_core{nodeIP="192.xx.xx.xx"}) by (nodeIP)

-  **Example 3: Requested memory of a pod/Allocable memory of the node where the pod is located**

   -  Define variables:

      -  Memory allocated to the containers in a pod: **aom_container_memory_request_megabytes**
      -  Total memory of the node: **aom_node_memory_total_megabytes**

   -  Query logic:

      -  For **aom_container_memory_request_megabytes**, use the aggregation function **sum** to calculate the allocated memory of a specified pod under a specified node based on the node IP address and pod ID.
      -  For **aom_node_memory_total_megabytes**, use the aggregation function **sum** to calculate the total memory of a specified node based on the node IP address.
      -  Both of them are filtered by node IP address. Therefore, the obtained metric values have the same metric dimension. (Only the values are different.)
      -  The actual memory usage of the pod can be obtained by performing the "/" operation on the values of the preceding two metrics.

   -  To obtain the actual memory allocation ratio of the pod, use the following statement:

      .. code-block::

         sum(aom_container_memory_request_megabytes{podID="2363xxxxxxxxab1315",nodeIP="192.xx.xx.xx"}) by (nodeIP) / sum(aom_node_memory_total_megabytes{nodeIP="192.xx.xx.xx"}) by (nodeIP)

-  **Example 4: Requested CPU cores of a pod/Allocable CPU cores of the node where the pod is located**

   -  Define variables:

      -  CPU cores allocated to the containers in the pod: **aom_container_cpu_limit_core**
      -  CPU cores allocated to the node: **aom_node_cpu_limit_core**

   -  Query logic:

      -  For **aom_container_cpu_limit_core**, use the aggregation function **sum** to calculate the CPU cores allocated to a specified pod under a specified node based on the node IP address and pod ID.
      -  For **aom_node_cpu_limit_core**, use the aggregation function **sum** to calculate the total CPU cores of a specified node based on the node IP address.
      -  Both of them are filtered by node IP address. Therefore, the obtained metric values have the same metric dimension. (Only the values are different.)
      -  The actual CPU usage of the pod can be obtained by performing the "/" operation on the values of the preceding two metrics.

   -  To obtain the actual CPU allocation ratio of the pod, use the following statement:

      .. code-block::

         sum(aom_container_cpu_limit_core{podID="5663xxxxxxxxcd3265",nodeIP="192.xx.xx.xx"}) by (nodeIP) / sum(aom_node_cpu_limit_core{nodeIP="192.xx.xx.xx"}) by (nodeIP)

Common Prometheus Commands
--------------------------

:ref:`Table 1 <mon_01_0043__table1340718919434>` lists the common Prometheus commands for querying metrics. You can modify parameters such as the IP address and ID based on site requirements.

.. _mon_01_0043__table1340718919434:

.. table:: **Table 1** Common Prometheus commands

   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Metric                                    | Tag Definition                                      | PromQL                                                                                                                                                                  |
   +===========================================+=====================================================+=========================================================================================================================================================================+
   | Host CPU usage                            | {nodeIP="", hostID=""}                              | aom_node_cpu_usage{nodeIP="192.168.57.93",hostID="ca76b63f-dbf8-4b60-9c71-7b9f13f5ad61"}                                                                                |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host application request throughput       | {aomApplicationID="",aomApplicationName=""}         | http_requests_throughput{aomApplicationID="06dc9f3b0d8cb867453ecd273416ce2a",aomApplicationName="root"}                                                                 |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Success rate of host application requests | {aomApplicationID="",aomApplicationName=""}         | http_requests_success_rate{aomApplicationID="06dc9f3b0d8cb867453ecd273416ce2a",aomApplicationName="root"}                                                               |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host component CPU usage                  | {appName="",serviceID="",clusterId=""}              | aom_process_cpu_usage{appName="icagent",serviceID="2d29673a69cd82fabe345be5f0f7dc5f",clusterId="00000000-0000-0000-0000-00000000"}                                      |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host process threads                      | {processCmd="",processName=""}                      | aom_process_thread_count{processCmd="cdbc06c2c05b58d598e9430fa133aff7_b14ee84c-2b78-4f71-9ecc-2d06e053172c_ca4d29a846e9ad46a187ade88048825e",processName="icwatchdog"}  |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cluster disk usage                        | {clusterId="",clusterName=""}                       | aom_cluster_disk_usage{clusterId="4ba8008c-b93c-11ec-894a-0255ac101afc",clusterName="aom-test"}                                                                         |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cluster virtual memory usage              | {clusterId="",clusterName=""}                       | aom_cluster_virtual_memory_usage{clusterId="4ba8008c-b93c-11ec-894a-0255ac101afc",clusterName="aom-test"}                                                               |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Available cluster virtual memory          | {clusterId="",clusterName=""}                       | aom_cluster_virtual_memory_free_megabytes{clusterId="4ba8008c-b93c-11ec-894a-0255ac101afc",clusterName="aom-test"}                                                      |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Workload file system usage                | {appName="",serviceID="",clusterId="",nameSpace=""} | aom_container_filesystem_usage{appName="icagent",serviceID="cfebc2222b1ce1e29ad827628325400e",clusterId="af3cc895-bc5b-11ec-a642-0255ac101a0b",nameSpace="kube-system"} |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Pod kernel usage                          | {podID="",podName=""}                               | aom_container_cpu_used_core{podID="573663db-4f09-4f30-a432-7f11bdb8fb2e",podName="icagent-bkm6q"}                                                                       |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Container uplink rate (BPS)               | {containerID="",containerName=""}                   | aom_container_network_transmit_bytes{containerID="16bf66e9b62c08493ef58ff2b7056aae5d41496d5a2e4bac908c268518eb2cbc",containerName="coredns"}                            |
   +-------------------------------------------+-----------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
