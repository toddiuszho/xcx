* **Provider** - company providing cloud hosting. Azure, AWS, GCP, Rackspace, HP, Oracle, Openshift, etc.
* **Account** - sellable entrypoint into a Provider. An AWS Account
* **Organization** - logical grouping of several Accounts together, usually for consolidated billing and governance. AWS Organizations
* **Environment** is a hard-break dividing separation of concerns, to appease Security. Development + Early Testing vs. Late Testing (discipline your team to treat as much like Production as possible) vs. Production
* **Stage Types** describe an application-agnostic purpose for deployment
  * **demo** - sales demo of a particular version
  * **internal** - end users of internal staff
  * **live** - end users for paying customers
  * **model** - allow internal staff to make dirty writes, where it won't interfere with sales demos
  * **train** - allow internal staff to train on an application version, even if not yet released live
  * **union** - union of cherry-pickedd features to test working together
* **Stage Specifiers** detail how requests for application versions or "featuresets" get deployed to a stage
  * **union** - u#{checksum}-t#{ticket} :: u5c98a-t678ffa
  * **versioned** - ${version}-${ticket} :: v0005-t79a0a
* **Stage** is a destination in an environment for a deployment. ${env_code}-${stage_type}-${stage_specifier} :: qa-demo-v0005-t79a0a
* **Domain** is a combination of stage and application name. ${env_code}-${stage_type}-${stage_specifier}.${app_abbrev}.${apex_domain} :: qa-demo-v0005-t79a0a.iam.toddiuszho.net
* **Region** - geographical region where resources are hosted. Spreading across Regions adds much latency & expense, but grants a great deal of disaster recovery. Some hosted services do not easily add interoperability of resources among different Regions.
* **Zone** - logical subdivision of a Region. Spreading across Zones adds a little latency & expense, but grants a small deal of disaster recovery. Most hosted services support (and even encourage) interoperability of resources among different Zones in the same Region.
