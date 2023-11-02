Description of functions the plug-in will have.

# Project Set-Up

## Initiate CMA

_Description:_ Creates a set of boilerplate project files associated for starting a critical mineral assessment (CMA). User defines extent, coordinate system, and resolution. These parameters can also be copied from an existing dataset. User has the option to check the estimated memory allocation for a single band raster at the specified resolution before creating the project directory and files.

_Functions:_

* Input Meta Data
  * User name - user name to generate workflow provenance
  * CMA mineral - current critical mineral assessment target
  * Comments - allows user to add additional comments on the current critical mineral assessment
* Project Settings
  * Set project directory - select an output directory from browser or by inserting path to save project to
  * Define project bounds - drop down to select project boundary from raster or vector layer in table contents. _\*Future Functionality Options_: allow user to browse for a layer, draw an extent, or specify from coordinates
  * Define project CRS - select CRS from drop down of frequently used CRS or browser pop-up query
  * Define pixel size - select pixel resolution (unit defined by CRS)
  * Add buffer - option to buffer selected project bounds by a specified distance
  * Check memory size – reports the approximate file size for each raster layer formatted to this CMA. Notification appears in a blue banner along the top of the project
  * Create project files - creates 1) template blank raster (TIF), 2) project raster to which data layers will be added (TIF), and 3) project metadata file (JSON) for current CMA in the set project directory
* Choose JSON File to Resume a Project
  * Insert or browse to past project - user can resume a past CMA project from JSON
  * Set project - sets the selected project as active
  * It is anticipated that this json file will be continuously updated while a user is working on the project, recording information about layers added, data sources tapped into, etc

# Data Acquisition and Management

## \*Query Database

_\*Future Functionality Option_

_Description:_ Connects to a data repository and allows user to query data. Query results can be selected as individual layers or into groups to be pulled into other tools.

_Functions:_

* Connect to database - connects to [MRData](https://mrdata.usgs.gov/), [ScienceBase](https://www.usgs.gov/tools/sciencebase), Macrostrat, or other specified database (eg. TA-11 and TA-2)
* Query by project extent - searches all data within the current CMA extent
* Query database by datatype – raster or vector
* Query by name - input dataset name
* Query by topic - input key word to search by
* Add to current project - selects desired layer(s) from query results and adds to project
* _Save selected data to group - can save out layer(s) to defined group for batch processing_

## \*Group Manager

_\*Future Functionality Option_

_Description:_ Allows user to edit saved query data.

_Functions:_

* Select group to edit
* Edit selected data
  * Rename
  * Add to group
  * Drop from group
  * Merge groups
* Save changes

# Raster Layer Derivation Tools

## \*Rasterize Vector Data

_\*Future Functionality Option_

_Description:_ General set of tools for converting various vector data into raster with user specifications. All outputs will conform to the template raster.

_Functions:_

* Rasterize lines, points, polygons
* Rasterize by vector numeric attribute
* Reclassify non-numeric attributes to values and rasterize
  * Auto populates a reclassified table with numbers and unique values
    * May need option to classify if too many unique values
* Additional options as needs arise

## \*Bedrock Tools

_\*Future Functionality Option_

_Description:_ Gives user the option to prioritize areas within polygon type bounds or areas along the edges between boundaries.

_Functions:_

* Select data
* Select focus region
  * If boundary selected for prioritization, secondary option to choose buffer around boundary
* Rasterize layer

## Interpolate Point Data

_Description:_ Interpolates values between point data (e.g., geochemistry) into output data raster. Though many of the tools will be generalized, the planned set of tools will be offered as specific to geochemical interpolation needs (constrained by polygons representing bedrock types, fill within catchment, etc)

_Functions:_

* Point sample data - select data to interpolate
* Method - select interpolation method from drop down list (eg. IDW, various kriging, clough-tocher, etc)
* Element - select which element to generate an interpolated layer for
* Add interpolation boundary - select boundaries, such as bedrock layers, to constrain interpolation
* Create interpolated data raster

## Proximity Layers

_Description:_ Calculates distance from vector features (e.g., fault lines) into output raster

_Functions:_

* Select vector layer - drop down of layers, drag in layer, or browse from folder
* Use selected features only - Option to use all features layer or only those currently selected by user
* Calculate distance - calculates distance of each cell to feature
* Threshold - option to threshold to only cells within a specified distance to the features

## Add Layer(s) to Data Raster

_Description:_ Adds selected layers to CMA raster stack.

_Functions:_

* Add layer - opens pop up window
  * Get from loaded later - drop down of current layers in project
  * Get from file path - browse to location of desired data. \*_Future functionality option_: takes in URL, data bucket path, saved group from query
  * Select resample method - drop down list of resampling methods
  * Add text description for band name - create name for this data band in raster stack
  * Confirm selection - OK to add layer to main window
* Rearrange layer order in display window
* Add to raster stack - reprojects, resamples, and clips selected data layer to match current CMA template and adds data as unique bands to the raster stack
* In addition to being used to add known existing data to the data raster this functionality is planned as a step following the raster layer derivation tools after creating an acceptable layer it can then be appended to the data raster

# Modelling

## \*Training Data Evaluation

_\*Future Functionality Option_

_Description:_ Tool to allow the user to explore trends in the training data

_Functions_:

* Select training data layer
* K-means
  * Number of clusters
  * Detect number of clusters
* Plot PCA
  * PCA dimensions for x- and y- axis
* Spectral plots

## Prepare Training Data For Inference

_Description:_ Perform necessary data transformations for passing raster data and training data to conform to TA-3 needs

_Functions:_

* Sample raster data at points
  * Within specified buffer
* Rasterize training data - creates a raster layer of the same profile as the data raster where positive values are 1 and other is 0
  * Within specified buffer

## Run Prediction Algorithms

_Description:_ Takes in data stack and training data, runs prediction algorithms, and outputs prediction and uncertainty raster layers. Model accuracy and band importance metrics will also be reported for the model. Note - this is expected to be largely supplanted by TA-3 algorithms

_Functions:_

* Set raster stack input
* Set training data input
  * Option to buffer points
  * Option to rasterize training points
    * Select field to assign as raster values
* Train Model - currently one class SVM
* Map Model - Map SVM Scores
* Outputs
  * Prediction raster
  * Uncertainty raster
  * Model accuracy metrics
  * Band importance outputs - which variables are contributing the most to the prediction
  * Uncertainty evaluation - which variables are contributing the most to the uncertainty

## Prediction Thresholding

_Description:_ Ability to narrow in on predictions of interest by allowing user to threshold probability and uncertainty at user specified values.

_Functions:_

* Set Thresholds - Probability (0.0-1.0) and Uncertainty (0.0-1.0)
* Remove hanging pixels - performs a morphological closing after the thresholds to
* Convert outputs to polygon - attributes each polygon with mean and std probability and threshold within it

## \*HITL Data Editor

_\*Future Functionality Option_

_Description:_ Allows user to view training point data in multiple windows with the same extent at the same time. User can also edit training data in that window as a way to QAQC data.

_Functions:_

* Select training data
* Select number of windows
* Drop down of which layer to view in each window - will automatically match all extents as user pans and zooms
* Option to zoom to specified point or to iterate through all points
* Edit training data point
* Save edits

# Statistical Analyses and Data Visualization

## \*PCA Plots

_\*Future Functionality Option_

_Description:_
