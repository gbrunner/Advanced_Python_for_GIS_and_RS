## Preparation: [Watch this video on mapping and data science](https://www.youtube.com/watch?v=DdUBrV2zpvI&t=11s)

## Lecture:
Let's pick up where we left off last week and Look at **Week 7, Problem 4**
### 1. St. Louis Crime Aggregation
#### Let's start by revisiting last weeks **Challenge** Problem.
1. Let's aggregate the crime points in ArcGIS Online.
2. We load:
  - Crime points
  - Ward
  - And run Aggregate...
  - Easy, right?

#### Let's do this using Python!
- Walk through Week7's solution
- Highlight that I can grab the dataframe object and *show* the tabular results via ```crime_aggregate_fc.query().df```

#### Go to the Help Documentation
- Here is how you interface with these capabilities.
- Note the inputs
- Point to samples

### 2. Population Analysis in California
#### Via Geoenrichment
Go through Geoenrichment notebook

#### Via a Population Image Service
Follow up with how to use image services.

## In Class Exercises:
- Fighting forest fires notebook: https://developers.arcgis.com/python/sample-notebooks/fighting-california-forest-fires-using-spatial-analysis/

- [Geoenrichment](https://developers.arcgis.com/python/guide/performing-geoenrichment/)

## In Class Problems:
1. **What is the Total population of St. Louis City?** Following from the [Geoenrichment example](https://developers.arcgis.com/python/guide/performing-geoenrichment/), create a notebooks that:
- Gets the USA geoenrichment data
- lists the datasets within the geoenrichment dataset for the USA
- Lists the USA subgeographies ```usa.subgeographies.states```
- Uses *Missouri* as the state and to find the places within *Missouri* ```usa.subgeographies.states['Missouri'].places```
- Creates a Map object over St. Louis that plots the boundary of St. Louis over the topographic basemap
  - Hint: Make sure that you have the right place_name in ```usa.subgeographies.states['Missouri'].places['place_name'].geometry```
- Uses the enrichment capability ```stl_df = enrich(``` to find the *Total Population* ```'TOTPOP'``` of St. Louis.
- What is the Total Population of the City of St. Louis?

2. Go into [ArcGIS Online](http://slustl.maps.arcgis.com/). Perform the following analysis on the STL Crime features that you published last week.
- Analysis -> Analyze Patterns -> Calculate Density
- Analysis -> Analyze Patterns -> Find Hot Spots

3. After running that analysis in ArcGIS Online, run them through Python. Using Python, add the objects to a map (separate maps for each) and save the map as a Web Map. Take a look at the help documentation for each tool. Do the results from running through ArcGIS Online match up with the results from Python?
- [Find Hot Spots](https://esri.github.io/arcgis-python-api/apidoc/html/arcgis.features.analysis.html?highlight=hot%20spot#find-hot-spots)
- [Calculate Density](https://esri.github.io/arcgis-python-api/apidoc/html/arcgis.features.analysis.html?highlight=density#arcgis.features.analysis.calculate_density)

4. **Challenge** 
- Publish the *STL-Police-Districts-2014-2* data as a feature service. 
- Aggregate your crime feature layer by Police District
- For each district, use the Geoenrichment capability to find the population per district
- Determine which district has the highest crimes per population

## Homework:
1. Complete and submit the prolems listed above.
2. read the following chapters of the *Python Data Science Handbook*
  - Chapter 3: [Introduction to Pandas](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/03.00-Introduction-to-Pandas.ipynb) 
  - Chapter 3: [Introducing Pandas Objects](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/03.01-Introducing-Pandas-Objects.ipynb)
  - Chapter 3: [Data Indexing and Selection](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/03.02-Data-Indexing-and-Selection.ipynb)
  - Chapter 3: [Operations in Pandas](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/03.03-Operations-in-Pandas.ipynb)
  - If you like learning this, don't limit yourself to just these chapters becuase this is the only class where we will focus on Pandas.
3. Project 3 Assigned.

## Helpful Links
- Data Science Example: https://developers.arcgis.com/python/sample-notebooks/historical-wildfire-analysis/
- Raster\Image Service exmaple: https://developers.arcgis.com/python/sample-notebooks/tour-the-world-with-landsat-imagery-and-raster-functions/
