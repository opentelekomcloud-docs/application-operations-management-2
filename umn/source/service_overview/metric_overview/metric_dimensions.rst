:original_name: aom_01_0025.html

.. _aom_01_0025:

Metric Dimensions
=================

Dimensions of VM Metrics Reported by ICAgents
---------------------------------------------

.. table:: **Table 1** Dimensions of VM metrics reported by ICAgents

   ====================== ================== ==========================
   Category               Metric Dimension   Description
   ====================== ================== ==========================
   Network metrics        clusterId          Cluster ID
   \                      hostID             Host ID
   \                      nameSpace          Cluster namespace
   \                      netDevice          NIC name
   \                      nodeIP             Host IP address
   \                      nodeName           Host name
   Disk metrics           clusterId          Cluster ID
   \                      diskDevice         Disk name
   \                      hostID             Host ID
   \                      nameSpace          Cluster namespace
   \                      nodeIP             Host IP address
   \                      nodeName           Host name
   Disk partition metrics diskPartition      Partition disk
   \                      diskPartitionType  Disk partition type
   File system metrics    clusterId          Cluster ID
   \                      clusterName        Cluster name
   \                      fileSystem         File system
   \                      hostID             Host ID
   \                      mountPoint         Mount point
   \                      nameSpace          Cluster namespace
   \                      nodeIP             Host IP address
   \                      nodeName           Host name
   Host metrics           clusterId          Cluster ID
   \                      clusterName        Cluster name
   \                      gpuName            GPU name
   \                      gpuID              GPU ID
   \                      npuName            NPU name
   \                      npuID              NPU ID
   \                      hostID             Host ID
   \                      nameSpace          Cluster namespace
   \                      nodeIP             Host IP address
   \                      hostName           Host name
   Cluster metrics        clusterId          Cluster ID
   \                      clusterName        Cluster name
   \                      projectId          Project ID
   Container metrics      appID              Service ID
   \                      appName            Service name
   \                      clusterId          Cluster ID
   \                      clusterName        Cluster name
   \                      containerID        Container ID
   \                      containerName      Container name
   \                      deploymentName     Workload name
   \                      kind               Application type
   \                      nameSpace          Cluster namespace
   \                      podID              Instance ID
   \                      podIP              Pod IP address
   \                      podName            Instance name
   \                      serviceID          Inventory ID
   \                      nodename           Host name
   \                      nodeIP             Host IP address
   \                      virtualServiceName Istio virtual service name
   \                      gpuID              GPU ID
   \                      npuName            NPU name
   \                      npuID              NPU ID
   Process metrics        appName            Service name
   \                      clusterId          Cluster ID
   \                      clusterName        Cluster name
   \                      nameSpace          Cluster namespace
   \                      processID          Process ID
   \                      processName        Process name
   \                      serviceID          Inventory ID
   ====================== ================== ==========================
