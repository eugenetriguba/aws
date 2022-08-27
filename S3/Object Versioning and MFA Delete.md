# Object Versioning

* Controlled at the bucket level
* Disabled by default.
* If you enable versioning on a bucket, you can never disable it again. However, you can suspend it and reenable it.
* Without versioning, each bucket is solely identified by its key i.e. it's name. If you modify an object, the original version of that object is replaced.
* Versioning lets you store multiple versions of objects within a bucket. Operations which would modify objects generate a new version.
* The newest version of a object is known as the current or latest version. If you don't specify the id, it is expected you want to interact with the current/latest version.

## Structure

* KEY = photo.jpg
* id = null (with versioning off)
* id = 111111 (with versioning on)

There is also a delete marker that is used has a hiding feature that hides all previous versions of the object. But you can also undelete the delete marker and make the versions active again.

There is also a full delete that fully deletes a particular version of the object.
Space is consumed by ALL versions. Therefore, you all billed for ALL versions. Only way to 0 costs is to delete the bucket.

# MFA Delete

* Enabled in versioning configuration
* MFA is required to change bucket versioning states
* MFA is required to delete versions
* Serial number (MFA) + code passed with API calls
