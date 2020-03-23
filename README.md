# elasticsearch
Need to modify virtual memory using root user
1.  sysctl -w vm.max_map_count=262144
2. ulimit -u 4096

Elasticsearch uses a mmapfs directory by default to store its indices. The default operating system limits on mmap counts is likely to be too low, which may result in out of memory exceptions.

On Linux, you can increase the limits by running the following command as root:

sysctl -w vm.max_map_count=262144

Elasticsearch uses a number of thread pools for different types of operations. It is important that it is able to create new threads whenever needed. Make sure that the number of threads that the Elasticsearch user can create is at least 4096. This can be done by setting ulimit -u 4096 as root

unzip using below command
tar -xzvf es.tar.gz
vim elasticsearch.yml  -configure
/bin/elasticsearch  --start

Configure ES:-
cluster.name:
node.name:
node.master: true
node.data: true
path.data: /home/data/es
path.logs: /elasticsearch/logs/

#Set the bind address to specific ip
network.host: 1.1.1.1

#the list of nodes to set
discovery.zen.ping.unicst.hosts: ["1.1.1.1","2.2.2.2","3.3.3.3"]
#set the minimum no. of  master eligible nodes
discovery.zen.minimum_master_nodes: 2

#bootstrap the cluster using initial sssssssset of master eligible  nodes
cluster.initial_master_node: ["111","2.2.2.2","3.3.3.3"]

To secure using readOnly rest -Download readOnly rest zip & extractusing
bin//belasticsearch-plugin  readOnlyRest.zip

vim readonlyreat.yml in config folder


