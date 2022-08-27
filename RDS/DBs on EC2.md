* Small cost to transfer data across AZs

Need

* OS level access (Question if you really need to)
* Advanced DB Option tuning (DB root)
  * Many cases AWS allows you to control many of these parameters
* Vendor demands
* DB or DB version AWS don't provide
* Specific OS/DB combination AWS doesn't provide
* Architecture AWS doesn't provide (replication/resilience)
* Decision makers who "just want it"

Why you really shouldn't

* Admin overhead
  * Managing EC2 and DB Host
* Backup / DR Management
* EC2 is a single AZ
* Features 
  * Some of AWS DB products are great
* EC2 is ON or OFF
  * No serverless
  * No easy scaling
* Replication
  * Skills, setup time, monitoring, and effectiveness
* Performance
  * AWS invest time into optimization and features
