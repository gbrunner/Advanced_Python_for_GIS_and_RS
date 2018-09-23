## Preparation
Watch Jacob Wasilkowski's lecture from April 2018.
[The lecture notes and materials are available here.](https://github.com/gbrunner/Python_for_GIS_and_RS/tree/master/Week_14)

## Lecture

## Github
- Let's got to [github.com](www.github.com)
- Login
- Create a new repo and initialize with a readme. Name the repo *GIS 5091 - Week 1* 
- Download and install the [Github Windows Client](https://desktop.github.com/)
- Login
- Clone your *GIS 5091 - Week 1* repo. 
- Let's put all of our work in there today!

### Let's Learn Leaflet!!!
Leaflet -> Is an open-source JavaScript library for interactive web maps. It's lightweight, simple, and flexible, and is probably the most popular open-source mapping library at the moment. Leaflet is developed by Vladimir Agafonkin (currently of MapBox) and other contributors.

**What Leaflet does:** "Slippy" maps with tiled base layers, panning and zooming, and feature layers that you supply. It handles various basic tasks like converting data to map layers and mouse interactions, and it's easy to extend with plugins. It will also work well across most types of devices. See Anatomy of a Web Map for an introduction to the most common kinds of web maps, which is what Leaflet is good for.

**What Leaflet does not do:** Provide any data for you! Leaflet is a framework for showing and interacting with map data, but it's up to you to provide that data, including a basemap. Leaflet is also not GIS, although it can be combined with tools like CartoDB for GIS-like capabilities. If you need total freedom of form, interaction, transitions, and map projections, consider working with something like D3.

Check out thie tutorial from [Maptime Boston](https://maptimeboston.github.io/leaflet-intro/) to learn more.

### Let's Get Started!
#### The Anatomy of a Web Mapping Application using Leaflet.
- HTML
  - HyperText Markup Language
  - Provides the layout for a webpage
  - Is at the core of every web page
- CSS
  - Whereas HTML was the basic structure of your website, CSS is what gives your entire website its style. 
  - slick colors, interesting fonts, and background images -> thanks to CSS
- JavaScript
  - Programming language that lets web developers design interactive sites
  - Most of the dynamic behavior you'll see on a web page is thanks to JavaScript
  - And it's become a lot more than this!!!
  
#### Our first Leaflet map
Let's use the Leaflet [Quick Start Guide](https://leafletjs.com/examples/quick-start/) to create our first map!

Let's do this in [JSBin](https://jsbin.com/)

Let's use the same example, but change the JS to be the following:
```
var mymap = L.map('mapid').setView([41.8781, -87.6298], 13);
L.tileLayer('https://stamen-tiles.a.ssl.fastly.net/{z}/{x}/{y}.png', {
    attribution: 'Map tiles by Stamen Design, under CC BY 3.0.',
    maxZoom: 18,
    id: 'stamen.toner'
}).addTo(mymap);
```
What city are we centered over?

#### How does this look if we jam it into a single HTML file?
See quickstart.html

Let's complete the tutorial and see where we end up :)

### Working with Data in Leaflet
Data is read in [GeoJSON](http://geojson.org/) format, a format for encoding a variety of geographic data structures.

#### Let's Add Some Objects in GeoJSON format
Following from the leaflet tutorial, [let's add some features in GeoJSON format](https://leafletjs.com/examples/geojson/).

### Reading GeoJSON and Using it
1. Use the Boston GeoJSON example here. https://gbrunner.github.io/Advanced_Python_for_GIS_and_RS/Week%2011/boston_heatmap.html
2. Use the Chicago ZIPs example too to show polygons. https://gbrunner.github.io/Advanced_Python_for_GIS_and_RS/Week%2011/chicago_zips.html


### Powerful, fun capabilities of Leaflet

#### Leaflet Heatmap
Who doesn't like a *heatmap*?

Ever wonder how that works?

Demonstrate the Boston Heatmap example.

#### Leaflet Clustermap
Clustermaps are fun too!

Demonstrate the Boston Clustermap too. https://gbrunner.github.io/Advanced_Python_for_GIS_and_RS/Week%2011/boston_cluster.html

## Classwork Problems
1. Create a Leaflet map of 5 restaurants that you'd like to go to in St. Louis. Include popups! If you're up to it, change the symbology for the points.
*Hints:*
- look at [quickstart_final.html](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/quickstart_final.html). 
- In quickstart_final.html, add 5 markers. For example:
```
var marker1 = L.marker([41.873, -87.629]).addTo(mymap);
var marker2 = L.marker([41.812, -87.628]).addTo(mymap);
.
.
.
```
- Bind a Popup to each one:
```
marker1.bindPopup("<b>Resturant 1</b><br>Spiros").openPopup();
marker2.bindPopup("<b>Resturant 2</b><br>Annie Gunns").openPopup();
.
.
.
```
- Remove the other markers (Circle, Polygon, etc.)

2. Create a Leaflet showing the San Francisco Crime points from the GeoJSON found [here](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/sf_crime.geojson). Please add a relevant icon to the points. See the [Leaflet tutorial here](https://maptimeboston.github.io/leaflet-intro/) if you need help with that.
*Hints:*
- Start with the [bonston_geojson.html](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/boston_geojson.html) example.
- Change the ```view``` to be over San Francisco: ```var map = L.map('map').setView([42.35, -71.08], 13);```
- Change the basemap to a Stamen Basemap ```L.tileLayer('http://tiles.mapc.org/basemap/{z}/{x}/{y}.png'``` that is listed below.
- Change ```$.getJSON("rodents.geojson",function(data){``` to look at the [sf_crime.geojson](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/sf_crime.geojson) file
- Add the symbol following from the [leaflet tutorial](http://maptimeboston.github.io/leaflet-intro/) like:
```
 var ratIcon = L.icon({
    iconUrl: 'rat.gif',
    iconSize: [50,40]
  }); 
  L.geoJson(data  ,{
    pointToLayer: function(feature,latlng){
	  return L.marker(latlng,{icon: ratIcon});
    }
  } 
```

3. **Challenge** Create a Leaflet heatmap from the crime points GeoJSON that you used above.
*Hints:*
- Start with [boston_heatmap.html](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/boston_heatmap.html)
- Change the view of the map ```var map = L.map('map').setView([42.35, -71.08], 13);``` to be over San Francisco.
- Change the basemap to a Stamen Basemap ```L.tileLayer('http://tiles.mapc.org/basemap/{z}/{x}/{y}.png'``` that is listed below.
- Change *rodents.geojson* to the [sf_crime.geojson](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/sf_crime.geojson)

4. **Challenge** Create a Leaflet cluster map from the crime points GeoJSON that you used above. Make sure you have a default icon set. Can you change the color on the clusters?
- Start with [boston_cluster.html](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/boston_cluster.html)
- Change the view of the map ```var map = L.map('map').setView([42.35, -71.08], 13);``` to be over San Francisco.
- Change the basemap to a Stamen Basemap ```L.tileLayer('http://tiles.mapc.org/basemap/{z}/{x}/{y}.png'``` that is listed below.
- Change *rodents.geojson* to the [sf_crime.geojson](https://github.com/gbrunner/Advanced_Python_for_GIS_and_RS/blob/master/Week%201/sf_crime.geojson)
- Change the icon url ```iconUrl: 'http://andywoodruff.com/maptime-leaflet/rat.png',```
- Change:
```
<link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.css"/>
<link rel="stylesheet" href="MarkerCluster.css" />
<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
```
to:
```
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.css"/>
<link rel="stylesheet" href="MarkerCluster.css" />
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.js"></script>
```
Github serves things through **https** and therefore the libraries you reference must use **https**.


## If you finish this in class, there's one more thing I want to show you
[Esri Leaflet Examples](https://github.com/Esri/geodev-hackerlabs/tree/master/develop/leaflet)

## Homework
1. Complete the classwork problems and submit them as **Assignment 1**. If #1 and #2 were easy, please try to do #3 and\or #4.
2. Please read Chapters 1, 2, and 3 of [Introducing ArcGIS API 4 for JavaScript](https://www.apress.com/us/book/9781484232811). Chapeters 1 and 2 are really short!

## Setting up IIS
Can I setup IIS on SLU lab machines?

For geojson to work:
1. Go to IIS Manager
2. Set MIME type: ```.geojson, application/json```

## Fun Links
Basemaps from Stamen Design http://maps.stamen.com
- [Stamen Watercolor](http://maps.stamen.com/#watercolor) `https://stamen-tiles.a.ssl.fastly.net/watercolor/{z}/{x}/{y}.png`
- [Stamen Toner](http://maps.stamen.com/#toner) `https://stamen-tiles.a.ssl.fastly.net/toner/{z}/{x}/{y}.png`
- [Stamen Terrain](http://maps.stamen.com/#terrain) `https://stamen-tiles.a.ssl.fastly.net/terrain/{z}/{x}/{y}.png`
- [Coca-Cola from Stamen Watercolor](http://a.sm.mapstack.stamen.com/(watercolor,$eb0000[hsl-color])[soft-light]/0/0/0.png) ```http://a.sm.mapstack.stamen.com/(watercolor,$eb0000[hsl-color])[soft-light]/{z}/{x}/{y}.png```

[GeoJSON Viewer](https://github.com/gavinr/geojson-viewer)

[Convert CSV to GeoJSON](https://github.com/gavinr/csv-to-geojson)

[GeoJSON.io](http://geojson.io/)

[More than you ever wanted to know about GeoJSON](https://macwright.org/2015/03/23/geojson-second-bite.html#projections)

[Esri-Leaflet](https://esri.github.io/esri-leaflet/examples/) - Use Esri services with Leaflet. Probably a more advanced topic, but something you should know about.

[Awesome Leaflet Basemaps](https://leaflet-extras.github.io/leaflet-providers/preview/)
