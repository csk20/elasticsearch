# elasticsearch
Need to modify virtual memory using root user
1.  sysctl -w vm.max_map_count=262144
2. ulimit -u 4096

Elasticsearch uses a mmapfs directory by default to store its indices. The default operating system limits on mmap counts is likely to be too low, which may result in out of memory exceptions.

On Linux, you can increase the limits by running the following command as root:

sysctl -w vm.max_map_count=262144

Elasticsearch uses a number of thread pools for different types of operations. It is important that it is able to create new threads whenever needed. Make sure that the number of threads that the Elasticsearch user can create is at least 4096. This can be done by setting ulimit -u 4096 as root
