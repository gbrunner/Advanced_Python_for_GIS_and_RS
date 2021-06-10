## Preparation:
Please read [Raster processing using Python Tools](https://geohackweek.github.io/raster/).
- [Introduction](https://geohackweek.github.io/raster/01-introduction/)
- [Geospatial Concepts: Raster Data](https://geohackweek.github.io/raster/02-rasterconcepts/)
- [Encodings, Formats and Libraries](https://geohackweek.github.io/raster/03-encodingsandformats/)
- [Working with Raster Datasets](https://geohackweek.github.io/raster/04-workingwithrasters/)
- [Rainier DEM Example](https://geohackweek.github.io/raster/06-pygeotools_rainier/)
We will not follow this, verbatin, but we will go though the techniques that are shown here.

Also, please take a look at this tutorial for [using imagery layers that are hosted online](https://developers.arcgis.com/python/guide/using-imagery-layers/). If we have time, we wil cover this too.

## Lecture 1:
Following from the **Raster processing** tutorial, demonstrate;
1. Read Landsat images into a numpy array
2. Show images using *matplotlib*
3. Make sure to read in projection info for export back to TIFF
4. Calculate NDVI from numpy array
5. Show NVDI imapge using *matplotlib*
6. *Apply QA band Mask* -> Talk about advanced Numpy concepts
7. Show Raster in *matplotllib*
8. Save image back to disk
9. Load image into ArcMap

## In Class Problem 1:
Following from what was shown in the lecture, do the following:
1. Read in the DEM into a numpy array and it's georeference information from the DEM included in the folder. What are the dimmensions of the image? ```dem.shape```
2. Display it using *matplotlib*
3. Create a slope raster from the dem using the following slope function:
```
def slope_function(dem, cellsize):
    #Modified from calculation found here:
    #http://geoexamples.blogspot.com/2014/03/shaded-relief-images-using-gdal-python.html

    x, y = np.gradient(dem, cellsize, cellsize)
    #slope = np.pi/2.0 - np.arctan(np.sqrt(x*x + y*y))
    slope = np.arctan(np.sqrt(x*x + y*y))
    return slope
 ```
 4. Display the slope using imshow in *matplotlib*
 5. Export the raster to a TIFF
 6. View in Arcmap
 7. **Challange!** Building on the workflow here, go back to Jupyter and create a Hillshade raster from the DEM. Follow the code found [here](https://github.com/rveciana/geoexamples/blob/master/python/shaded_relief/hillshade.py)
 ```
def hillshade(array, azimuth, angle_altitude): 
   
    x, y = np.gradient(array)
    slope = np.pi/2. - np.arctan(np.sqrt(x*x + y*y))
    aspect = np.arctan2(-x, y)
    azimuthrad = azimuth*np.pi / 180.
    altituderad = angle_altitude*np.pi / 180.
    

    shaded = np.sin(altituderad) * np.sin(slope)\
        + np.cos(altituderad) * np.cos(slope)\
        * np.cos(azimuthrad - aspect)
    return 255*(shaded + 1)/2
 ```
 8. View the hillshade in matplotlib
 9. Export the hillshade to a TIFF

## In Class Problem 2:
The Climate Hazards Group at UC Santa Barbera produces a 30+ year quasi global dataset called [CHIRPS](http://chg.geog.ucsb.edu/data/chirps/). You can download the precipitation data as rasters here: ftp://ftp.chg.ucsb.edu/pub/org/chg/products/CHIRP/. 

For this exercise:
1. Download the first 36 rasters here: ftp://ftp.chg.ucsb.edu/pub/org/chg/products/CHIRP/dekads/. 
    - This data has 3 precipitation rasters per month, 1 every ten days, totaling 36 rasters in a year. 
2. Read each raster into a numpy array and concatenate those numpy arrays into a matrix of dimmension (36,x,y)
3. Using *matplotlib*, plot a few slices of the array so that we can see the rainfall over time.
4. **Are the rainfall trends periodic?**
5. **Challenge** Extract the time frame the filenames and plot some rainfall values (on the y-axis) vs. time (on the x-axis).

Submit your Jupyter notebook.

## Homework:
In preparation for next week's class, please read the the following sections from the Python Data Science handbook:
- [Introduction to Matplotlib](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.00-Introduction-To-Matplotlib.ipynb)
- [Simple Scatterplots](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.02-Simple-Scatter-Plots.ipynb)
- [Errorbars](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.03-Errorbars.ipynb)
- [Density and Contour Plots](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.04-Density-and-Contour-Plots.ipynb)
- [Histograms and Binnings](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.05-Histograms-and-Binnings.ipynb)
- [Visuallization with Seaborn](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.14-Visualization-With-Seaborn.ipynb)
~~Watch the following video on [ArcGIS Python Raster Functions](https://www.youtube.com/watch?v=OgwnKRrVHN0)~~
~~2. Work on Project 3!~~
