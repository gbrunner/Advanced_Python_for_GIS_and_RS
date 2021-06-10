## Preparation: [Publishing](https://www.youtube.com/watch?v=4AzOodYTHs4) and [Automating your WebGIS](https://www.youtube.com/watch?v=0LfJrk2_VRg)

## Lecture:
### Into to Publishing Data
Let's work with some [Open Data from St. Louis](https://www.stlouis-mo.gov/data/)
1. Using ArcGIS Pro or Arcmap, publish some data to ArcGIs Online.
  - [stl_boundary.zip](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%207/stl_boundary.zip)
  - [streets.zip](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%207/streets.zip)
2. Log into AGOL from Pro or ArcMap or just publish through ArcGIS Online.
3. Change Symbology of Web Map.
4. Publish features with Feature Access.
5. Go to ArcGIS Online and open the new feature service.
6. Add the feature service to a Map.
7. Restyle if necesary.

### Analysis using ArcGIS Online
1. Next show how we can aggregate those point features by the STL polygon.

### Automating it with Python
Demonstrate how we can automate the workflow above with Python

## Classwork Exercises:
1. [Import data from a Shapefile](https://developers.arcgis.com/labs/python/import-data/). After doing this exercise, you can go on to the **Classwork Problems**. Just note that the examples below will be helpful to look at.
2. **Optional** [Publishing from a pandas dataframe](https://developers.arcgis.com/python/sample-notebooks/html-table-to-pandas-data-frame-to-portal-item/)
3. **Optional** [Publishing from a Shapefile](https://developers.arcgis.com/python/sample-notebooks/publishing-sd-shapefiles-and-csv/#Publish-a-feature-service-from-a-shapefile-and-update-the-item-information)
4. **Optional** [Publishing from a CSV](https://developers.arcgis.com/python/sample-notebooks/publishing-sd-shapefiles-and-csv/#Publish-a-CSV-file-and-move-it-into-a-folder)


## Classwork Problems:
As you go through these problems, 
- check to make sure the content gets added to your ArcGIS Online account
- try to give nique names to the content
- and don't be afraid to explore!

1. Using Python, publish the rainfall data contained in the **national_rainfall_data.zip** file. Be sure to verify that the service publishes by calling ```display(published_shp)``` and then calling ```add_layer(...)``` to add the layer to a map.
2. The [UNHCR Data API](http://popdata.unhcr.org/wiki/index52ce.html?title=API_Documentation) provides robust statistics on immigration accross the work. Using the data API, publish 5 new items in ArcIGS Online of the location and number of assylum seekers from each location seeking assylum in England (GBR), France (FRA), Australia (AUS), Germany (DEU), and the USA (USA). Please see the UNHCR Sample Notebook to help get you started. The code pattern that I think you should establish should look something like the following:
```
for c in country_list:
    print('looking at ' + c)
    df = pd.read_json(...)
    resettlment_stats = gis.content.import_data(df, {"Address" : "country_of_origin_en"})
    item_properties = {...
    }
    item = gis.content.add(item_properties)
```
[Some helpful details can be found i the HTML table to pandas dataframe to portal item tutorial](https://developers.arcgis.com/python/sample-notebooks/html-table-to-pandas-data-frame-to-portal-item/)

Please verify that these were published by going into ArcGIS Online after you think it has been successful.

3. Pubilish the following:
- The zipped geodatabase containing the St. Louis crime data (STL_Crime.gdb.zip).
- The zipped shapefiles of St. Louis Neighborhoods (nbrhds_wards.zip).
After publishing them, make sure they exist in ArcGIS Online. You can give your features unique names when you publish them by filling in the json in the ```gis.content.add``` method as follows:
```
gis.content.add({"title":"stl_wards_by_greg"}, wards)
```
Note that you can add other properties like a *description*, *snippets*, adn *tags*

4. **Challenge** Next week we will see how to use ArcGIS Online to process data. If you are up for a challenge, after publishing the crime data and wards, aggregate the crime data by ward following the examples in:
- [Summarizing Feature Data](https://developers.arcgis.com/python/guide/summarizing-feature-data/)
- [Aggretate Earthquakes by State](https://developers.arcgis.com/python/guide/summarizing-feature-data/#Aggregate-earthquakes-by-state)

To help you, here is a snippet of code that shows how to aggregate crime by ward:
```
from arcgis.features import summarize_data
crime_summary = summarize_data.aggregate_points(point_layer = published_crime, 
                                                output_name="stl_crime_by_ward_gjb",
                                                polygon_layer = published_wards.layers[0],
                                                keep_boundaries_with_no_points=False)
```                                            


## Homework:
1. Please complete the **Problems** above and submit them as **Assignment 7**
2. Please watch the following video: [ArcGIS Python API for Data Scientists](https://www.youtube.com/watch?v=DdUBrV2zpvI&t=11s)
3. **Project 2** due next week!
