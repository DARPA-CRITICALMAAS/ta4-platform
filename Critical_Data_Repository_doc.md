### Jataware

Our plans for data repository needs are... 

### Macrostrat

Our plans for data repository needs are... 

### MTRI

Our plans for data repository needs are... 

The current data repository expectations primary consist of being able to have programmatic access to existing data repositories. Thus far in our stage of development we have not yet consolidated a plan for creating a new data repository.

Planned repositories for data access:
* ScienceBase
* USGS MR Data
* Macrostrat
* TA1 and TA2 outputs

Have tested the USGS created python library sciencebasepy for accessing the data repository. Currently this is not integrated into our software workflow but is anticipated to fulfill our needs.

Have worked towards accessing the underlying vector data from the map service tiles provided by Macrostrat. This is showing promising integration, but has also yet to be worked into the software workflow.

For data management and caching services we are looking to utilze the python library pooch. Pooch works to download and cache locally to prevent duplicate downloading of data
