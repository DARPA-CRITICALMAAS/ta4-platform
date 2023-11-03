# TA4 CriticalMAAS Data Repository

We are building data stores for a variety of purposes to support TA1-3 data workflows.
Right now we are in the phase of cataloging existing data and tools, with the goal of
defining coherent structures for shared data-management needs during Phase 1 of the project.

We are compiling a [list of CriticalMAAS tools and data stores](https://docs.google.com/spreadsheets/d/1x5C73yOq6vIbRpuItCSdtQdzkFOmBxYfZbJ2zH1qqxU/edit?usp=sharing) that will
assist us in maintaining a coherent data strategy across teams. We encourage all CriticalMAAS performers to help us compile this list.
Once we stabilize somewhat, we will reproduce this structure here.

## Key goals

- Support CMA workflows with flexible and use-oriented data handling approaches
- Build from common needs into shared functionality where applicable
- Coordinate across teams on data standards, tools, and shared ownership

## Team-specific goals

### Jataware

Our plans for data repository needs are... 

### Macrostrat

- Macrostrat broadly seeks to build data pipelines and stores to host geological map datasets (TA1 outputs and NGMDB vectorized products), combine them with geological context information, and provide them to TA3 as a coherent platform for geological data.
- We also have a need for data services related to raster maps (especially TA1 inputs) and hope to collaborate with Jataware and TA1 performers on the structure of this system
- Our integration with [xDD](https://xdd.wisc.edu) provides a host of tools for storing and working with PDFs which may be relevant to TA2 data curation needs.

### MTRI

The current data repository expectations primary consist of being able to have programmatic access to existing data repositories. Thus far in our stage of development we have not yet consolidated a plan for creating a new data repository.

Planned repositories for data access:
* ScienceBase
* USGS MR Data
* Macrostrat
* TA1 and TA2 outputs

Have tested the USGS created python library sciencebasepy for accessing the data repository. Currently this is not integrated into our software workflow but is anticipated to fulfill our needs.

Have worked towards accessing the underlying vector data from the map service tiles provided by Macrostrat. This is showing promising integration, but has also yet to be worked into the software workflow.

For data management and caching services we are looking to utilze the python library pooch. Pooch works to download and cache locally to prevent duplicate downloading of data
