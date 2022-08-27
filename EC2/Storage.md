Key Terms

* Direct (local) attached Storage
  
  * Storage on the EC2 Host (Instance Store)
  * Generally super fast but if hardware fails or EC2 instance moves between hosts, the storage can be lost.
* Network attached Storage
  
  * Volumes delivered over the network (EBS)
  * Generally highly resilient
  * Separate from the instance hardware
* Ephemeral Storage
  
  * Temporary storage
  * i.e Instance Store
* Persistent Storage
  
  * Permanent storage
  * Lives on past the lifetime of the instance
  * i.e. EBS
* Block storage
  
  * Volume presented to the OS as a collection of addressable blocks
  * No structure provided
  * Mountable
  * Bootable
* File storage
  
  * Presented as a file share
  * Has structure
  * Mountable
  * NOT bootable
* Object storage
  
  * Collection of objects (and metadata)
  * Generally provide key and get back value
  * Flat structure
  * Not mountable
  * Not bootable
  * Super scalable

Storage Performance

* IO (block) Size
  * "Size of wheel"
  * Size of blocks of data that is being written to disk
* IOPS
  * "Revolutions per second the engine can generate"
  * Number of IO operations a storage system can accomodate per second
* Throughput
  * "Final speed of wheel"
  * Rate of data a storage system can store on a particular piece of storage (generally MB/s)
* IO/block size X IOPS = Throughput
* 
