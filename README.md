automatic-server-discovery-configuring
======================================

When a new server is brought online in a cluster it's it first task should be to determine what it's role should be. This process should be part of base image of that server. Upon startup it determines what role is required by the cluster it will automatically provision it's self with the tools it need to become a webserver, database, etc and install any applications needed. 

# Goal

Demonstrate a cluster of three machines or more that making use of service discovery and distrubted consensious to automaically deploy a new server to the cluster, have it obtain it's role, provision it's self, and deploy and applications required to run on that server. 

## Requirements

- Watch for change in k/v store and start new machine when qty_server is bumped.
- Create a base image with minimal requirements defined.
- Upon startup machine will register it's self as a part of a cluster.
- Machine will check k/v store to discover the type of server it should be.
- Machine will pull down provisioning and run provisioning to the type of server it should be.
- Machine will install any required application and start them up.
- Machine will say it's ready to receive traffic.
- k/v store becomes the source of truth for the cluster and will contain all metadata about what that cluster is made up of. (applications and what version, base os image, age, ip, role of server)

Outstanding Questions

- When deploying multiple machines at once how do we ensure that they don't grab duplicate roles?
- How do we decommision old machine images and gracefully replace them with new ones?
- What do we do in the case a machine is deemed unhealthy? 
- How do we gracefully remove it from the cluster?
- Do we immediately deploy a new machine to replace it when it's not healthy?
