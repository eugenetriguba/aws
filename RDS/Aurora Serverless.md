* Scalable - ACU - Aurora Capacity Units
* Aurora Serverless cluster has a MIN and MAX ACU
* Cluster adjusts based on load
* Can go to 0 and be paused
* Consumption billing per-second basis
* Same resilience as Aurora (6 copies across AZs)
* Much simpler and removes a lot of the complexity of managing DB instances and capacity
* Easier to scale
* Cost effective (only pay for what you consume)
* ACUs are decreased/increased based on load. AWS has managed pool of instances that get allocated when needed, always have the storage.

Proxy fleet

* App goes to proxy fleet
* They will broker a connection between application and ACUs
* Because app is never directly connecting to instances, the scaling can be more fluid and can scale in/out.

Use cases

* Infrequently used applications
* New applications
  * If you used the provisioned instance, you'd need to take the DB down to adjust the size/capacity/performance. With serverless, that isn't the case. It scales and adjusts to the load as needed.
* Variable workloads
* Unpredictable workloads
* Development/test databases
* Multi-tenant applications
  * Load tied to revenue
