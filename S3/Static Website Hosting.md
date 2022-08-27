* Normal access to S3 is via the AWS APIs
* However, we can also access it via HTTP.
  * When you enable it, you need to set an index document and a error document.
  * Static website endpoint is created (influenced by bucket name and region, auto generated)
  * Custom Domain via R53 (Bucket name matters! Bucket name has to match the domain)

## Use Cases

Offloading

* Move all media from compute service to static media hosting
  * HTML file will point to S3 bucket for the media, which will likely be cheaper than in a compute service.

Out-of-band pages

* A method of accessing something that is out of the main way.
* If our server is offline for maintenance or it is experiencing stability or performance issues, we can change our DNS and point customers to a backup maintenance website on S3.

## Billing

* Cost to store data, expressed as a per GB per month fee.
* Transfer data into S3 is free but transferring data out of S3 has a per GB per month fee.
* Charged a certain amount for requesting data per X amount of requests (GET/PUT/etc.)
* Often really tiny amounts of money relative to the value (cantrill.io, 17 cents most has been charged in one month)
