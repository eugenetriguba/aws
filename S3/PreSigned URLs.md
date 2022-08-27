* Give another person or app access to an object inside of an S3 object using credentials
  * Access rights of identity that created them
  * time limited
  * encode all the authentication information needed inside
  * Can be used for upload and download
* Useful for when access to a private S3 bucket needs to be controlled

Exam powerups

* Can create a URL for an object you have no access too
  * Only requirement is specifying a particular object and an expiration date and time
* When using the URL, the permissions match the identity which generated it (and same permissions as the identity that generated it **right now**)
* Access denied could mean the generated ID never had access or doesn't now.
* Don't generate with a role. URL stops working when temporary credentials expire..
