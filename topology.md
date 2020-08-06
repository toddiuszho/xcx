* **Provider** - company providing cloud hosting. Azure, AWS, GCP, Rackspace, HP, Oracle, Openshift, etc.
* **Account** - sellable entrypoint into a Provider. An AWS Account
* **Organization** - logical grouping of several Accounts together, usually for consolidated billing and governance. AWS Organizations
* **Environment** is a hard-break dividing separation of concerns, to appease Security. Development + Early Testing vs. Late Testing (discipline your team to treat as much like Production as possible) vs. Production
* **Stage** nests under an Environment and serves an application-agnostic purpose
  * **demo-${version}-${ticket}** - sales demo of a particular version
  * **train-${version}-${ticket}** - allow internal staff to train on an upcoming version before it's released
  * **model-${version}-${ticket}** - allow internal staff to make dirty writes to an upcoming version, where it won't interfere with sales demos
  * **union-${checksum}-${ticket}** - union of cherry-pickedd features to test working together
* **Region** - geographical region where resources are hosted. Spreading across Regions adds much latency & expense, but grants a great deal of disaster recovery. Some hosted services do not easily add interoperability of resources among different Regions.
* **Zone** - logical subdivision of a Region. Spreading across Zones adds a little latency & expense, but grants a small deal of disaster recovery. Most hosted services support (and even encourage) interoperability of resources among different Zones in the same Region.
