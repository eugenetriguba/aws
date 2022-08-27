* EBS Snapshots are backups of data consumed within EBS volumes and are stored on S3
* Snapshots are incremental, the first being a full backup and any future snapshots being incremental (diffs between previous and next)
* Data is linked, incremental references the previous for any data that isn't changed.
* Copies data that is used
* Snapshots can be used to migrate data to different availability zones in a region or to different regions of AWS
* If you do delete an incremental snapshot, AWS makes sure the data is moved so all the data after is still functioning (so can be though of as more self sufficient)

Creating

* Blank volume or one based off of snapshot
* Snapshots can be copied between regions and AZs

Performance

* New EBS Volume = full performance immediately
* Snaps restore lazily -- fetched gradually
  * Requested blocks are still fetched immediately
  * Can force a read of all data immediately to have all of it moved over
* Fast Snapshot Restore (FSR) - Immediate restores
  * Up to 50 snapshots per region
  * Set on snapshot and AZ
  * Costs extra
  * Can always achieve same result by doing a force read of all data

Billed

* GB/month
* Billed for used *not* allocated data
* 
