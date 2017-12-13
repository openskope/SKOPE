# Test Release 0.1 - Draft Plan -13-Dec-2017

## Objectives

* Deliver a first release of the SKOPE application to a test environment.
* Demonstrate data discovery via the search page, and exploration of selected data in the workspace.
* Confirm that a release comprising multiple services running in different Docker containers can be deployed easily to a computing environment supporting Docker.

## Subsystems we will include in this release

* Meteor application for the user interface.
* GeoServer for dynamic map tile generation.
* Elasticsearch for data discovery.
* Nginx for reverse proxy.

## Features that we will demonstrate in this release

* Browsing of all data sets available through the system via the search page. 
* Optional filtering of data sets displayed on the search page using model or data set name (e.g. "PaleoCAR", "PRISM"), data type (e.g. precipitation), temporal extent (e.g., 1900-2000), and geographic coordinates (single point).
* Toggling of map layers in the data set displayed on the map.
* Map pan and zoom.

## Features that we *may* demonstrate in this release

* Timeseries graphs of conditions at selected point on map.


## Documents and project status
* [Task board](https://github.com/orgs/openskope/projects/6)  for Release 0.1.

---

## Future features we will *not* include in this release

* Search by spatial extent.
* Concurrent display of data from different data sets.
* User accounts, authentication, and authorization.
* Saving or sharing of state between sessions.
* Data download.
* Automated registration and metadata extraction for new data sets.
* Execution of models.
* Provenance query, reporting, and visualization.

## Future services and subystems we will *not* include in this release

* Clowder.
* RabbitMQ.

