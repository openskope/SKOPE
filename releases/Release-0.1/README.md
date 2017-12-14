# Test Release 0.1 - Draft Plan - 13-Dec-2017

## Overview
### Objectives

* Deliver a **first release** of the SKOPE application **to a test environment**.
* Demonstrate data discovery via the **search page**, and exploration of selected data on the **workspace page**.
* Confirm that a release comprising multiple services running in different Docker containers can be deployed easily to a computing environment supporting Docker.
* Seed a pipeline of releases from development, to test, to production.

### Subsystems we will include in this release

* Meteor application for the user interface.
* GeoServer for dynamic map tile generation.
* Elasticsearch for data discovery.
* Nginx for reverse proxy.

### Features that we will demonstrate in this release

* Browsing of all data sets available through the system via the search page. 
* Optional filtering of data sets displayed on the search page using model or data set name (e.g. "PaleoCAR", "PRISM"), data type (e.g. precipitation), temporal extent (e.g., 1900-2000), and geographic coordinates (single point).
* Toggling of map layers in the data set displayed on the map.
* Map pan and zoom.

### Features that we *may* demonstrate in this release

* Timeseries graphs of conditions at selected point on map.

### Documents and project status
* [Task board](https://github.com/orgs/openskope/projects/6) for Release 0.1.

---
## Deliverables

We will deliver the following artifacts as part of the release. These artifacts are to be considered specific to this release and expected to change in future releases.

### Docker images

* **Docker image for running the Meteor application.**  The running container will serve the web pages rendered in the user's web browser.   [[skope-deployment#17](https://github.com/openskope/skope-deployment/issues/17)]

* **Docker image for running the Elasticsearch service.**  The running container will store and make searchable information about each of the data sets accessible in the web application. The metadata will include the information required by the web application to request map tiles from the GeoServer service.  [[skope-deployment#14](https://github.com/openskope/skope-deployment/issues/14)]

* **Docker image for running the GeoServer service.**  The running container will provide a service that dynamically generates map layer tiles for display on the Workspace page of the web application.  [[skope-deployment#12](https://github.com/openskope/skope-deployment/issues/12)]

* **Docker image for running the Nginx reverse-proxy service.**  The running container will host the sole Internet-facing network port. The user's web browser will load the Meteor application from this port and will send and receive requests to the Elasticsearch and GeoServer services through this port.  Nginx will transparently route these requests to the appropriate backend services and route responses back to the web browser clients.   [[skope-deployment#16](https://github.com/openskope/skope-deployment/issues/16)]

### Deployment scripts

* **Docker Compose File** for starting the docker containers comprising the running application, establishing the network connections between them, and mounting host storage volumes accessed directly by each service.   [[skope-deployment#18](https://github.com/openskope/skope-deployment/issues/18)]

* **Elasticsearch index initialization script** for loading the documents describing the data sets accessible to the web application into a new instance of Elasticsearch.   [[skope-deployment#15](https://github.com/openskope/skope-deployment/issues/15)]

### Raster data sets
The following data sets will be stored as GeoTIFF files and used by GeoServer to render map tiles displayed in the web application.  Each data set will have an associated JSON document describing the data set and representing the information stored and searchable via the Elasticsearch service.

* Outputs of the **PaleoCAR** run previously accessible through the SKOPE I prototype, at the same resolution and temporal and spatial extents. [[skope-deployment#19](https://github.com/openskope/skope-deployment/issues/19)]

* A version of the **PRISM** data sets than can be freely distributed without a licensing agreement (resolution and spatial extent TBD).  [[skope-deployment#20](https://github.com/openskope/skope-deployment/issues/20)]

* The **National Elevation Dataset** (resolution and spatial extent TBD).

### Computing Resources

* **Test VM for running the SKOPE application.**  This OpenStack instance running on Nebula will host each test release in succession.  Its configuration will be identical to a future 'Production VM' instance on Nebula that will host the current production instance of the SKOPE application.  [[skope-deployment#11](https://github.com/openskope/skope-deployment/issues/11)]

* **Disk volume for storing data files accesible to the Test VM.**  This volume will be mounted via NFS on the Test VM. Data will be deployed to this volume for each test release.  [[skope-deployment#13](https://github.com/openskope/skope-deployment/issues/13)]

### Documentation

* **List of properties for filtering data sets listed in search results.** Each property will have a description of the valid values for the property, e.g. numerical range, set of allowed values, unstructured text.  [[SKOPE#14](https://github.com/openskope/SKOPE/issues/14)]

* **Schema for JSON documents describing raster data sets available through the web application.**  These documents will be indexed by Elasticsearch and the properties in these documents searchable through the web application.  [[skope-deployment#22](https://github.com/openskope/skope-deployment/issues/22)]

* **Procedure for setting up a new OpenStack VM configured to serve as either a Test or Production VM.**  This will allow developers to set up their own development VMs identically to the Test and Production VMs.  The procedure will include configuring user accounts, mounting NFS volumes, installing and configuring Docker and its dependencies, and maintaining system security.  [[skope-deployment#21](https://github.com/openskope/skope-deployment/issues/21)]

---
## Limitations

### Future features we will *not* include in this release

* Search by spatial extent.
* Concurrent display of data from different data sets.
* User accounts, authentication, and authorization.
* Saving or sharing of state between sessions.
* Data download.
* Automated registration and metadata extraction for new data sets.
* Execution of models.
* Provenance query, reporting, and visualization.

### Future services and subystems we will *not* include in this release

* Clowder.
* RabbitMQ.
