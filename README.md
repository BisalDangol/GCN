#Google Cloud network concepts
Google Cloud supports projects, networks, and subnetworks to provide flexible, logical isolation of unrelated resources.

In Google Cloud, networks provide data connections into and out of your cloud resources (mostly Compute Engine instances). Securing your networks is critical to securing your data and controlling access to your resources.

Projects are the organizing entity for what you're building, for example the settings, permissions, and other metadata that describe your applications. Any Google Cloud resources you allocate and use must belong to a project.

Many developers map projects to teams since each project has its own access policy (IAM) and member list. Projects also collect billing and quota details reflecting resource consumption.

Resources within a single project work together, for example by communicating through an internal network, subject to the regions-and-zones rules. A project can't access another project's resources unless you configure a connection method such as Shared VPC or VPC Network Peering.

Networks directly connect your resources to each other and to the outside world. Networks, using firewalls, also house the access policies for incoming and outgoing connections. Networks can be global (offering horizontal scalability across multiple Regions) or regional (offering low-latency within a single region).

A VPC network is a virtual network inside of Google Cloud. A VPC network is a global resource that consists of a list of regional virtual subnetworks (subnets) in data centers, all connected by a global wide area network. VPC networks are logically isolated from each other in Google Cloud.

Subnetworks allow you to group related resources (Compute Engine instances) into RFC1918 private address spaces. Subnetworks can only be regional. A subnetwork can be in auto mode or custom mode.

An auto mode network has one subnet per region, each with a predetermined IP range and gateway. These subnets are created automatically when you create the auto mode network, and each subnet has the same name as the overall network.
A custom mode network has no subnets at creation. To create an instance in a custom mode network, you must first create a subnetwork in that region and specify its IP range. A custom mode network can have zero, one, or many subnets per region.
## Set your region and zone
Certain Compute Engine resources live in regions and zones. A region is a specific geographical location where you can run your resources. Each region has one or more zones.
  ```bash
  gcloud config set compute/zone "{your zone}"
export ZONE=$(gcloud config get compute/zone)

gcloud config set compute/region "{your region}"
export REGION=$(gcloud config get compute/region)
