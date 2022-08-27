Configures a lambda to pull in additional code and content in the form of layers.

A layer is a .zip archive that contains libraries, a custom runtime, or other dependencies. With layers, we can use libraries in our function without needing to include them in our deployment package.

The zip file is extracted in the `/opt` folder.

These layers allow us to use new runtimes that aren't currently supported by AWS and allow libraries to be externalized. Deployment ZIPs are smaller, with shared libraries reused between functions.

Deployment optimization, not a package manager substitute.

Pros

* Great for sharing large, seldom-changed files.
  * Custom Lambda Run-times
  * Binary dependencies that aren't distributed via PyPI such as FFMPEG.
  * https://github.com/mthenw/awesome-layers
* Allows viewing and editing of the source code for a lambda (not necessarily a direct lambda layer benefit but if we bring in dependencies, we have this issue)
