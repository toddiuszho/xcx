* **Provider** - company providing cloud hosting. Azure, AWS, GCP, Rackspace, HP, Oracle, Openshift, etc.
* **Account** - sellable entrypoint into a Provider. An AWS Account
* **Organization** - logical grouping of several Accounts by the _same Provider_ together, usually for consolidated billing and governance. AWS Organizations
* **Environment** is a hard-break dividing separation of concerns, to appease Security. Development + Early Testing vs. Late Testing (discipline your team to treat as much like Production as possible) vs. Production
* **Portal** - describes an application-agnostic purpose for deployment
  * **partner** - resellers, brokers, partners, suppliers
  * **customer** - staff of customers (not their end users)
  * **demo** - sales demo of a particular version
  * **internal** - internal staff of your own company
  * **member** - normal end users of paying customers
  * **model** - allow internal staff to make dirty writes and experiment with end results, where it won't interfere with sales demos or live data
  * **premium** - premium end users of paying customers
  * **train** - allow internal staff to train on an application version, even if not yet released live
* **Specifier** detail how requests for application versions or "featuresets" atop a version get deployed to a stage
  * **union** - u#{checksum}-v#{version}-t#{ticket} :: `u5c98a-v0005-t678ffa`
  * **versioned** - v#{version}-t#{ticket} :: `v0005-t79a0a`
  * **whitelabeled** - w#{label}-v#{version}-t#{ticket} :: `w34a6e-v005-t810a2`
* **Stage** - destination in an environment for a deployment. #{env_code}-#{portal}-#{specifier} :: `qa-demo-v0005-t79a0a`
* **Apex** - registered domain name, one label nested under an ICANN TLD :: `toddiuszho.net`
* **Domain** - FQDN. combination of stage and application name as subdomain nested under an Apex. #{env_code}-#{portal}-#{specifier}.#{app_abbrev}.#{apex} :: `qa-demo-v0005-t79a0a.shopping.toddiuszho.net`
* **Alias** - Floating, stable FQDN. Every deployment to a stage gets its own unique FQDN. It's common after smoke testing it, to repoint an Alias FQDN to this unique FQDN (using DNS records like CNAME and ALIAS), to direct traffic from an older stage to this new one. #{env_code}-#{portal}.#{app_abbrev}.#{apex} :: `qa-member.shopping.toddiuszho.net`
  * **Degenerate Aliases:**
    * No **env_code** needed for Production :: `premium-shopping.toddiuszho.net`
    * No **portal** needed for an application that's shared across all audiences :: `dev.iam.toddiuszho.net`
* **Region** - geographical region where resources are hosted. Spreading across Regions adds much latency & expense, but grants a great deal of disaster recovery. Some hosted services do not easily add interoperability of resources among different Regions.
* **Zone** - logical subdivision of a Region. Spreading across Zones adds a little latency & expense, but grants a small deal of disaster recovery. Most hosted services support (and even encourage) interoperability of resources among different Zones in the same Region.
* **Application Breakdown**
  * **Suite** `operations`
    * **Application** `iam`
      * **Component** `tls-verifier`
* **Hosting Breakdown**
  * **Cluster** `prod-logging-elasticsearch`
    * **Component** `prod-logging-elasticsearch-ingress`
      * **Node** `prod-logging-elasticsearch-ingress-0001`
