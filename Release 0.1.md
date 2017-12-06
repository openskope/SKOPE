# Test Release 0.1 Plan

## Objectives

* Deliver a first release of the SKOPE application to a test environment.
* Demonstrate data discovery via search, and display of the selected data set on a map.
* Confirm that a release comprising multiple services running in different Docker containers can be depoloyed easily to any computing environment supporting Docker.

## Subsystems included in this release

* Meteor application for the user interface.
* GeoServer for dynamic map tile generation.
* Elasticsearch for data discovery.
* Nginx for reverse proxy.

## Features to demonstrate in this release

* Search for raster data using model name (e.g. "PaleoCAR", "PRISM"), environmental condition type (e.g. precipitation), and temporal extent (e.g., 1900-2000).
* Selection of data set from search results for display on map.
* Toggling of map layers in the data set displayed on the map.
* Map pan and zoom.


## Documents and project status
* [Task board](https://github.com/orgs/openskope/projects/6)  for Release 0.1.

---

## Future features NOT included in this release

* Search by geographic extent.
* Concurrent display of layers from different data sets.
* User accounts, authentication, and authorization.
* Saving or sharing of state between sessions.
* Data download.
* Data charting.
* Point data sets.
* Automated registration and metadata extraction for new data sets.
* Execution of models.
* Provenance query, reporting, and visualization.

## Future services and subystems NOT included in this release

* Clowder.
* RabbitMQ.

