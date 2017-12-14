# Test Release 0.1 - Draft Plan -13-Dec-2017

## Overview
### Objectives

* Deliver a first release of the SKOPE application to a test environment.
* Demonstrate data discovery via the search page, and exploration of selected data in the workspace.
* Confirm that a release comprising multiple services running in different Docker containers can be deployed easily to a computing environment supporting Docker.

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
* [Task board](https://github.com/orgs/openskope/projects/6)  for Release 0.1.

---
## Deliverables

We will deliver the following artifacts as part of the release. These artifacts are to be considered specific to this release and expected to change in future releases.

### Docker images

* **Docker image for running the Meteor application.**  The running container will serve the web pages rendered in the user's web browser.

* **Docker image for running the Elasticsearch service.**  The running container will store and make searchable information about each of the data sets accessible in the web application. The metadata will include the the information required by the web application to request map tiles from the GeoServer service.

* **Docker image for running the GeoServer service.**  The running container will provide a service that dynamically generates map layer tiles for display on the Workspace page of the web application.

* **Docker image for running the Nginx reverse-proxy service.**  The running container will host the sole Internet-facing network port. The user's web browser will load the application from this port and will send and receive requests to the Elasticsearch and GeoServer services through this port.  Nginx will transparently route these requests to the appropriate backend services and route responses back to the web browser clients.

### Deployment scripts

* **Docker Compose File** for starting the docker containers comprising the running application, establishing the network connections between them, and mounting host storage volumes required by each service.

* **Elasticsearch index initialization script** for loading the documents describing the data sets accessible to the web application into a new instance of Elasticsearch.

### Raster data sets
The following data sets will be stored as GeoTIFF files and used by GeoServer to render map tiles displayed in the web application.  Each data set will have an associated JSON document describing the data set and representing the information stored and searchable via the Elasticsearch service.

* Outputs of the **PaleoCAR** run previously accessible through the SKOPE I prototype, at the same resolution and temporal and spatial extents.

* A version of the **PRISM** data sets than can be freely distributed without a licensing agreement (resolution and spatial extent TBD).

* The **National Elevation Dataset** (resolution and spatial extent TBD).

---
## Out of scope for this release

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
