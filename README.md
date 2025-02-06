# SemFS: Someone Else's Memory FileSystem

Managing Distributed Memory is a qestion of what is the "right abstraction". 
Here the hypothesis is that it is files.
The goal is to provide a mount of the sort:

```
# This folder has all memory located on Machine 1
/mnt/semfs/1
# This folder has all memory located on Machine 2
/mnt/semfs/2
# This folder has all memory located on self
/mnt/semfs/self
# Contents in this folder automatically shard. 
/mnt/semfs/shard
```

The base level abstraction is filesystem for ultimate genericity. 
But libraries can be built using the lower level protocol can be built to provide
 - memory mapping
 - gather primitives (for bulk random reads)
Additional CLI tools can be provided for
 - inter machine file copies/moves (ex: should be able to move from machine A to B
   without first downloading everything from A)

Each machine simply run a daemon with a published allocation 
of memory (disk fallback could be considered). 
Zero fault tolerance is provided. 
