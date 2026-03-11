 
PRACTICAL NO:01 
Aim: Familiarizing Quantum GIS: Installation of QGIS, datasets for both Vector and Raster data, Maps. 
Understanding Quantum GIS: 
Quantum GIS (QGIS) is a user friendly Open Source GIS application licensed under the GNU General Public License. QGIS is an official project of the Open Source Geospatial Foundation (OSGeo). It runs on Linux, Unix, Mac OSX, Windows and Android and supports numerous vector, raster, and database formats and functionalities. 
Like all GIS applications, QGIS provides a graphical user interface allowing display of map layers and manipulation of data for analyses and map-making. 
A Geographical Information System (GIS) is a collection of software that allows you to create, visualize, query and analyze geospatial data. Geospatial data refers to information about the geographic location of an entity. This often involves the use of a geographic coordinate, like a latitude or longitude value. Spatial data is another commonly used term, as are: geographic data, GIS data, map data, location data, coordinate data and spatial geometry data. Applications using geospatial data perform a variety of functions. Map production is the most easily understood function of geospatial applications. Mapping programs take geospatial data and render it in a form that is viewable, usually on a computer screen or printed page. Applications can present static maps(a simple image) or dynamic maps that are customized by the person viewing the map through a desktop program or a web page. 
Many people mistakenly assume that geospatial applications just produce maps, but geospatial data analysis is another primary function of geospatial applications. Some typical types of analysis include computing: 
•	Distances between geographic locations 
•	The amount of area (e.g., square meters) within a certain geographic region • What geographic features overlap other features? 
•	The amount of overlap between features 
•	The number of locations within a certain distance of another and so on... 
These may seem simplistic, but can be applied in all sorts of ways across many disciplines. The results of analysis may be shown on a map, but are often tabulated into a report to support management decisions. The recent phenomena of location-based services promises to introduce all sorts of other features, but many will be based on a combination of maps and analysis. For example, you have a cell phone that tracks your geographic location. If you have the right software, your phone can tell you what kinds of restaurants are within walking distance. While this is a novel application of geospatial technology, it is essentially doing geospatial data analysis and listing the results for you. 
Fundamentals  of  GIS                                                                                                   B.N.N College, Bhiwandi 
 
 
Installation of QGIS: 
Steps: 
1)	Download the latest QGIS setup file (“QGIS-OSGeo4W-3.10.0-2-Setup-x86_64”) from any browser. 
2)	Extract the setup file by clicking the highlighted buttons. 
 

	 
 
 PRACTICAL NO: 02

Aim:
Creating and Managing Vector Data: Adding vector layers, setting properties, formatting, calculating line lengths, and statistics.



Adding vector layers (Polygon, Line, Points):

➤ Polygon layers (We have taken 2 layers: Matunga, Garden)
➤ Line layers (We have taken 3 layers: Small_Roads, Road, Flyover)
➤ Point layers (We have taken 4 layers: Bank, College, Restaurants, ATM)

Setting properties (Labelling, Symbology):

Our aim is to create a map representing a location and its surroundings as follows:
 
Creating Polygon vector layer: 
	Select Project→New 
	Select Layer→Create Layer→New Shapefile Layer
	Following dialog box will appear on the screen. Select Polygon option from Geometry type.
	Fill the appropriate information in each text box.
• File name :
	By default the file will be saved in bin folder. 
	To avoid it click on following button to change the location of file.   
	Field Panel
a.	Add the Attribute you want to show. (Column Name for Table) 
b.	Specify Type (DataType:Text Data/Decimal Data/Whole Number/Date) of Attribute 
c.	Specify the Length of the Attribute. Specify Precision (If Data Type is Decimal) 
	Click on Add to Field List Button.
	You can add as many fields (Column Name) as you want for the layer. 
	Select Geometry Type as follows
• Click on the following button
  
	The CRS dialog box will appear on screen. Click on the WGS84 option and it will be selected as follows. Click on OK
  
 
Follow the steps to plot Polygon features: 
	Select the Polygon Feature( In our case it is Matunga for background) from layer panel.
 
 
the location where you want to place the polygon. for polygon layer minimum 3 points should be selected
  
	Save the newly added polygon as follows.
 
 
	Set style for polygon by using property window(Right click on Matunga Layer)
 
 
	Following screen will appear on the screen. Select pattern as you want and click on OK.
  
 
	Same way we can add one more polygon layer for Gardens.
 
Creating Line vector layer: 
	Repeat the same steps as we have done for polygon layer.
	Select geometry type Line.
 
 
 
Road layer 
	To plot road click on Add Line Feature
 
 
	Click on the map where you want to draw line.
 
	Once you are done then right click on map (Dotted line turn into solid line).
  
	Save your data.
 
 
 
	Set style for Roads in the same way as we have done for polygon.
 
 
 
	Road will look as below.
 
 
  
 
	To label your roads Right click on Road layer .Go to properties window then select label and set single label property.
  
	Following window will appear on the screen.
 
 
 
	Roads will look like these.
 
	To merge roads
• Go to properties of road then select symbology. Click on Advanced button select Symbol levels.
  
 
	Check Enable symbol levels option.
 
 
 
	Click ok & Road will appear as follows.
 
 
 
Creating Point vector layer: 
	Repeat same steps to add point layers as we have done in previous layers.(For ATM, Restaurants, Banks, Bus Stops etc).
  
Final output: 
 
 
 
 
Calculating line lengths and statistics: 
	Go to Layer → Add Layer → Add Vector Layer
	Add the following file to project
 
"\GIS_Workshop\Practicals\Practical_01\D\DATA\IND_rrd\IND_rails.shp" Press “ADD” 
 
	Also add India Administrative Map. 
“GIS_Workshop\Practicals\Practical_01\D\DATA\IND_adm\IND_adm0.shp” Double Click on IND_adm0
 
 
	Select   → Select any outline style from below given options.
 
 
 
	Press OK
	The display window will appear like
 
 
  
	In Layer Pane, Right click on IND_rails → Open Attribute Table
 
 
 
	Press Toggle Editing button using button, on Attribute table window toolbar.
	Press Open Field Calculator using button.
 
 
	Set the output field as “Track_Len”, field type to “Decimal Number”.
 
	From Function List search $length or go to Geometry → Select $length
  
	Set expression as
 
	Press “OK”
	A new column is added to the attribute table with value representing the length of track in KM.
 
	Press CTRL+S or click on Save Edits option on tool bar
 
 
	Close the attribute table window
	For calculating the total length of Railway tracks in India.
	Select Vector→ Analysis Tools→ Basic Statics for Fields
 
	Select IND_rails layer from input layer. And select Track_Len in “Field to Calculate statistics on”
  
	Press RUN
	The Result is
 
 
	Open the “output.html” file to get the field statistics.
 
 
  
	The above statistics show that the total length of Railway track in India is 60,479.32 KM. 





 
PRACTICAL NO:03 
Aim: Exploring and Managing Raster data: Adding raster layers, raster styling and analysis, raster mosaicking and clipping. 




Adding raster layers: 
	From menu bar select Layer → Add Layer → Add Raster Layer
	Select Gridded Population of the World (GPW) v3 dataset from Columbia University, Population Density Grid for the entire globe in ASCII format and for the year 1990 and 2000. 
“\GIS_Workshop\Practicals\Practical_02\A\Data\gl_gpwv3_pdens_90_ascii_one\glds90ag60.  
asc” 
“\GIS_Workshop\Practicals\Practical_02\A\Data\gl_gpwv3_pdens_90_ascii_one\glds00ag60.  
asc”.
  
right corner.
	Select WGS 84 EPSG: 4326 and Press OK.
 
 
Raster Styling and Analysis: 
	To start with analysis of population data, convert the pixel from grayscale to Color.
	Select “glds90ag60.asc” Layer form layer Pane → select property OR double click on it.
 
 
 	 
	Press “APPLY”.
	Repeat the same for “glds00ag60.asc” Layer
 
 
Layer output after applying style. 
	The objective this experiment is to analyze raster data, as an example we will find areas with largest population change between 1990 and 2000, by calculating the difference between each pixel values.
	Go to Raster → Raster Calculator
 
 
  
	Put the expression "glds00ag60@1" - "glds90ag60@1"
	Select the output file location & name and Press OK.
	Remove the other two layers i.e. glds00ag60.asc and glds90ag60.asc Double click on pop_diff layer.
 	 
 
Set Render Type to “Single band Pseudo color”, Interpolation as Discrete, and remove all 
classification and add as shown in figure above using   button. After all settings press “OK”. Layer will appear like
 
 
classification rule.
	The red pixel shows negative changes and blue shows positive changes.
 
 
Raster Mosaicking and Clipping: 
A mosaic is a combination or merge of two or more images. 
In GIS, a single raster dataset can be created from multiple raster datasets by mosaicking them together. 
 
 
 
	Go to Layer → Add Layer → Add Raster Layer.
 
	Select the following “.tif” raster images for India from data folder.
	FAS_India1.2018349.terra.367.2km.tif 
	FAS_India2.2018349.terra.367.2km.tif 
	FAS_India3.2018349.terra.367.2km.tif 
	FAS_India4.2018349.terra.367.2km.tif 
 
 
	Press open.
	In data source manager | Raster window click Add.
 
 
	Go to Raster → Miscellaneous → Merge
 
 
In the Merge dialog window.
 
	Select all layers and Press OK.
 
 
	In Merge dialog window select a file name and location to save merged images.
 
 
	Save the file to “GIS_Workshop/Practicals/Practical_02/C/” location with the name as Merge_Files.tif
	Press Run and after completion of operation close the Merge window dialog box.
 
 
	You can now deselect individual layers from layer pane and only keep the merged raster file.
 
	Go to Layer→ Add Vector Layer → Select
\GIS_Workshop\Practicals\Practical_02\C\IndiaAdminBoundry\IND_adm0.shp  file. 
 → select any one of the following
 
	The result will be
 
 
	Go to Raster → Extraction → Clip Raster by Mask Layer.
 
 
	Select the merge raster image as input and Ind_adm0 as mask layer.
 
 
Select a file name and location for clipped raster as /Practical_02/C/Clipped_File.tif.
 
	Press RUN.
 
 



 
PRACTICAL NO:04




Aim: Making a Map, Working with Attributes, Importing Spreadsheets or CSV files, Using Plugins, Searching and Downloading OpenStreetMap Data. 
Making a Map: 
	Create a new Thematic Map or open and existing one.
	Consider the following map as an example map.
 
 
	Go to Project → New PrintLayout
 
 
	Insert a suitable title and press “OK”.
 
 
A new Print Layout window will open.
 
 
	Select Add Item → Add Map
 
 	 
 
 
 
After adding map go to ItemProperties → Map1→ Layers Check on Lock Layers and Lock Styles for Layers
  
This will ensure that if any change in layers or change their styles, the Print Layout view will not change. 
	Go to Add Item → Add Picture → Place a picture box at appropriate location.
 
 
	Also adjust Image Rotation to its appropriate value. Item Properties → Image Rotation
 
 
	Add an inset Using Add Item → Add Picture → Select an area to be highlighted on main Map. Set a frame for Inset by enabling the check box for Frame.
 
 
To highlight the area shown in Inset
	Select the Picture representing main Map from Items pane.
	In Item Properties → Overviews → using   icon add an overview.
	Select the checkbox Draw Overview
	Name the Picture object representing inset (Map1 in our case).
 
 
	The Print Layout will appear like
 
 
	Add Item → Add Label
	Change the Label text To “Mumbai Map”, Set appropriate font size and color using Item 
Properties→ Main Properties.
 
 
  
	Add Item → Add Legend→ Place the legend indicator at appropriate location. Uncheck auto update and use suitable legend indicator label.
 
 
	The Print Layout will appear
 
 
Add Item →Add Scale Bar
 
 
	Add Item → Add Label→Add a Label using HTML rendering.
 
 
	A Map can be saved in Image or PDF using Layout → Export as Image / Export as PDF
 
 
 
Save the Map to a location appropriate location as PDF or Image.
 
 
	Open the PDF or Image from location.
 
 
Importing Spreadsheets or CSV files: 
 
	Many times the GIS data comes in a table or an Excel spreadsheet or a list lat/long coordinates, therefore it has to be imported in a GIS project.
	Sample file for Earthquake data will be used in this practical. Go to Layer → Add Layer → Add Delimited text Layer
 
 
	Data Source Manager | Delimited Text window will appear.
	Select the \GIS_Workshop\Practicals\Practical_03\C\Sample.csv file from data folder.
 
 	 
Press ADD and close the window.
 
Output: 
 
 
 
 
 
Using Plugins: 
 
	Core plugins are already part of the standard QGIS installation. To use these, just enable them. Open QGIS. Click on Plugins → Manage and Install Plugins....
 
 
	To enable a plugin, check on the checkbox next to Plugin. This will enable the plugin to use it.
	External plugins are available in the QGIS Plugins Repository and need to be installed by the users before using them.
	Click on Not Installed or Install from ZIP.
	Once the plugin is downloaded and installed, you will see a confirmation dialog.
	Click on Plugins → <<new Plugin Name>>
 
The Plugin if marked Experimental plugin can be installed, from Setting→ check on
 
	 A 
	Click on a plugin name and Click Install.
 
 
 
Searching and Downloading OpenStreetMap Data: 
 
OpenStreetMap (OSM) created by Steve Coast in the UK in 2004 is a collaborative project to create a free editable map of the world. Rather than the map itself, the data generated by the project is considered its primary output. The creation and growth of OSM has been motivated by restrictions on use or availability of map information across much of the world, and the advent of inexpensive portable satellite navigation devices. 
	Add “Open Layer” and “OSM Search” Plugin from Not Installed option from Plugin Manager Dialog Box.
	The OSM Place Search plugin will install itself as a Panel in QGIS, if not go to View → Panels→ select OSM Place Search. 
 
 
Go to Web → OpenLayer Plugin and select Open Street Map
 
 
	A World map will appear on screen.
	If an error occurs in loading maps, go to project properties → CRS →
 
 
 
 
 
	In OSM Place search Pane → Enter Mumbai or any place name to search
	Double click on the desired place in OSM Place search Panel or Click and press  .Output: 




 
PRACTICAL NO:05 
Aim: Working with attributes, terrain Data. 
Working with attributes: 




	Start a new project.
	Go to Layer → Add Layer → Add Vector Layer Select
“\GIS_Workshop\Practicals\Practical_04\A\Data\ne_10m_populated_places_simple.zip” 
 
 
 
	Right click on Layer in Layer Panel → Open Attribute Table.
	Explore various attributes and their values in the Attribute table.
	To find the Place with maximum population click on “pop_max” file.
 button the following window will appear.
 	Enter pop_max>100 and pop_max<10000 and click   button to get all the places with population between 100 and 10000.
	The places matching the criteria will appear in different color.
 
 
	Different queries can be performed using the dataset. Try this. 
Terrain Data and Hill shade analysis: 
A terrain dataset is a multiresolution, TIN-based surface built from measurements stored as features in a geodatabase. Terrain or elevation data is useful for many GIS Analysis like, to generate various products from elevation data such as contours, hillshade etc. 
 
	Go to Layer → Add Raster Layer → select “10n060e_20101117_gmted_mea300.tif”, from Data folder.
 
 
	The Lower altitude regions are shown using dark color and higher using light shade as seen on top region containing Himalaya and Mt Everest.
	Mt. Everest - is located at the coordinates 27.9881° N, 86.9253° E.
	Enter 86.92, 27.98 in the coordinate field, Scale 900000 and Magnifier 100% at the bottom of QGIS.
 
 
	Press enter the view port will be centered on Himalaya Region.
 
 
	Crop the raster layer only for the region under study.
	Go to Raster → Extraction→ Clip Raster by Extent.
 
 
	Select the raster layer (if project contains multiple layers).
	Select the clipping area by selecting the option Use Canvas Extends if the visible part of map is to be selected or manually select an area on canvas by using Select Extent on Canvas.
	Select the location and file name for storing clipped raster layer.
 
 
	Press RUN.
	Deselect the original layer and keep the clipped one.
	The Clipped raster layer is representing altitude are from 103 Meters.

Clipped Raster 
	Counter lines are the lines on a map joining points of equal height above or below sea level. A contour interval in surveying is the vertical distance or the difference in the elevation between the two contour lines in a topographical map.
	To derive counter lines from given raster.
	Go to Raster → Extraction→ Contour
 
 
	The Contour configuration window will appear.
 
 
	Select the input raster layer name. Set contour interval 100.00 meters, select the output file name & location and check the option to add output file to project after processing.
	Press “RUN”.
	The contour layer will appear like this
 
 
	Label the layer using “ELEV” field and set appropriate symbols for line.
 
 
	In the Layer panel right click on Contour Raster Layer and select “Open Attribute table”.
	Arrange the table in descending order based on the value of “ELEV” column.
 
 
  
Compare the above counter line raster layer with the previous Google map image or visit https://www.google.com/maps/@27.9857765,86.9285378,14.75z/data=!5m1!1e4?hl=en-US 
 
 
A Hillshade is a grayscale 3D representation of the surface, showing the topographical shape of hills and mountains using shading (levels of gray) on a map, just to indicate relative slopes, mountain ridges, not absolute height. 
For Hill Shade surface analysis: 
	Go to Plugin → Install Georeferencer GADL.
	After successful installation of plugin Go to Raster → Analysis → Hill Shade
 
 
	Select the input raster layer, select file name and location for storing Hill Shade output file.
 
 
	Press “RUN” and Close the Hill Shape Dialog window.
	After Raster styling the Output will appear like this.
 
 



 
PRACTICAL NO:06 
Aim: Working with Projections and WMS Data. 




A Web Map Service (WMS) is a standard protocol developed by the Open Geospatial Consortium in 1999 for serving georeferenced map images over the Internet. These images are typically produced by a map server from data provided by a GIS database. 
	Start a new Project.
	Layer → Add Layer →Vector Layer
	Select “ne_10m_admin_0_countries.zip” Layer from data folder.
	Go to Layer → Save As
Select format as ESRI Shape File 
Select folder location and file name 
Set CRS North_America_Albers_Equal_Area_Conic EPSG: 102008 
 
 
	Press “OK”.
	Deselect the original Image and keep the projected layer visible.
 
 
	Select Layer → Add Layer → Add Raster Layer → Select MiniScale_(standard)_R17.tif from Location.“GIS_Workshop\Practicals\Practical_05\DATA\minisc_gb\minisc_gb\data\RGB_TIF_compre  s sed\MiniScale_(standard)_R17.tif”. 
	The Layer appears on a different location than the location where Great Britain is shown on 
Map.
  
	Open Layer Properties→CRS → Search bri → select British National Grid EPSG 27700. Processing may take some time.
	Locate United Kingdom on Layer; the vector layer exactly coincides by the raster layer covering United Kingdom.
  



 
PRACTICAL NO:07 
Aim: Georeferencing Topo Sheets and Scanned Maps Georeferencing Aerial Imagery Digitizing Map Data. 





Georeferencing Topo Sheets and Scanned Maps: 
	Start a new project.
	Go to Layers → Add Layer → Add vector Layer.
	Select GIS_Workshop\Manual\Prac06\IND_adm0.shp
	Zoom in to Mumbai region in the layer.
 
 
	Go to Plugins→ Manage and Install Plugins.
	Ensure that   is checked, if not install Georeferencer GDAL plugin. Go to Raster → Georefrencer
 
 
	A new Georeferencer window will open
 
 
	File → Open Raster
 
 
	Select file “Bombay_1909.jpg” from project data folder.
 
 
	Go to Settings →Transformation Settings.
 
 
	In the Transformation Settings window
•	Select Transformation type → Thin Plate Spline • Re-sampling Method → Nearest Neighbour
•	Target TRS → Everest 1830 datum: EPSG 4044
•	Select Output Raster Name and Location
•	Check the Load in QGIS When Done Option
•	Press “OK”.
 
 
  
	In Georeferencer window Go to Edit → Add Points
 
 
 
 
 
	Select the set of control points.
	Go to Setting → transformation settings.
 
 
  
	Press “RUN”
	In Georeferencing window go to → File → Start Georeferencing
 
	The progress indicator will appear
  
	The canvas area will now have the scanned map of Mumbai referenced with control points.
	Select the newly added layer in Layer Panel Right click and go to property.
 
	Set Transparency level of raster layer to appropriate level.
  
 
 
Output: 
 
 
The Scanned Image map coincides with the existing map. 
 
 
Georeferencing Aerial Imagery: 
	Install plugin OpenStreetMap and OSM Place Search
	Go to Web Menu → OpenLayerPlugin → OpenStreetMap→ OpenStreetMap
 
	Go to Project → Properties → Set CRS to EPSG 3857
	Go to View → Panels → select OSM Place search
 
	The Gateway of India, Mumbai is located at 18.92°N 72.83°E
	Search Gateway of India in OSM Search Panel
 
 
  
	Zoom in to appropriate level.
	The map will appear like this
 
	Go to Raster → Georefrencer
  
	A new Georeferencer window will open
 
	File → Open Raster
  
	Select file “Gateway_Imagery.tif” from project data folder
 
 
  
	Go to Edit → Add Point
	Select control points from map (Indicated in red color).
	Go to Setting → Transformation Setting
  
	Go to File → Start Georeferencing or Press the button in Georegerencing Window. The progress indicator will appear
 
	Observe that the aerial image of the Gateway of India is georeferenced on OSM in the map canvas.
  
. Digitizing Map Data: 
	Go to Layer ‣ Add Raster→ Select “Christchurch Topo50 map.tif” from project Folder.
 
	QGIS offers a simple solution to make raster load much faster by using Image Pyramids.
	Right-click the Christchurch Topo50 map.tif layer and select Properties.
 
	Choose the Pyramids tab. Hold the Ctrl key and select all the resolutions offered in the 
Resolutions panel.
  
	Click Build pyramids. Then click OK.
	Go to Settings →Options ..... Select the Digitizing tab in the Options dialog.
 
 
	Set the Default snap mode to vertex and segment.
 
	Press OK.
	Go to Layer → Add Layer → Add Spatialite Layer.
 
 
	Select the name and location for Spatial database eg: 
“GIS_Workshop\Practicals\Practical_06\C\MySpatialDataBase.sqlite”
	Name the Layer as “Digitized_Road”
	Set Geometry type as “Line”
	Set CRS EPSG:4167 – NZGD2000
 
 
	Add “Name” and “Class” fields using “Add to Fields List”
 
 
	Once the layer is loaded, click the Toggle Editing button to put the layer in editing mode.
	Click the   Add Line feature button. Click on the map canvas to add a newvertex. Add new vertices along the road feature. Once you have digitized a road segment, right- click to end the feature. 
  
	On Layer Panel Right Click on Digitze_Road, Select the Style tab in the Layer Properties dialog.
  
	Select appropriate style to see the digitized road feature clearly.
 
 
	After creating a new Spatialite layer
 
 
	Select Digitized_Garden layer in Layer Panel and click on Toggle Editing   button and 
then Add Polygon Feature   button on Tool bar.
	Add two gardens to the region by adding polygon.
 
 
	The Layer will appear on map canvas
 
 
	Using the above procedure a point feature can also be digitized.
	The digitizing task is now complete. You can play with the styling and labeling options in layer properties to create a nice looking map from the data you created.









 
PRACTICAL NO:08 
Aim: Managing Data Tables and Saptial data Sets: Table joins, spatial joins, points in polygon analysis, performing spatial queries. 
Table joins: 









	Start a new project.
	Go 	to 	Layer 	→ 	Add 	Layer 	→ 	Add 	new 	Vector 	Layer 
“I:\GIS_Workshop\Practicals\Practical_07\A\Data\tl_2013_06_tract.zip”
	We could import this csv file without any further action and it would be imported. But, the default type of each column would be a String (text). That is ok except for the D001 field which contains numbers for the population. Having those imported as text would not allow us to run any mathematical operations on this column. To tell QGIS to import the field as a number, we need to create a sidecar file with a .csvt extension.
  
	This file will have only 1 row specifying data types for each column. Save this file as ca_tracts_pop.csvt in the same directory as the original .csv file.
	Go to Layer → Add Layer → Add Delimited Text Layer
And add I:\GIS_Workshop\Practicals\Practical_07\A\Data\ca_tacts_pop.csv” 
 
 
	In the layer panel, Right click on “tl_2013_06_tract”, layer and select Properties.
 
  button to add new table join.
	In the Add Vector Join window set the following properties and click OK.
 
 
	After performing join
 
 
	For more clear output, select “tl_2013_06_tact” from Layer Panel, right click and select properties. Go to Symbology and set the following properties.
 
 
 
	A detailed and accurate population map of California can be seen as the result. Same technique can be used to create maps based on variety of census data.
  
Spatial Joins: 
	Go to Layer → Add Layer → Add Vector Layer → Select 
	“I:\GIS_Workshop\Practicals\Practical_07\B\Data\nybb_12c\nybb_13c_av\nybb.shp” 	and 
“I:\GIS_Workshop\Practicals\Practical_07\B\Data\OEM_NursingHomes_001\OEM_Nursing  
Homes_001.shp”, from data folder.
  
	Go to attribute table and observe the data.
	Table before performing Join
 
 
	Go to Vector → Data Management Tools → Join Attributes by Location
 
 
  
	Attribute table after join
 
 
Output: 
 
 
 
 
Points in polygon analysis: 
	Go to Layer → Add Layer → Add Delimited Text Layer 
Select “EarthQuakeDatabase.txt”
  
	Go to Layer → Add Layer → Add Delimited Text Layer 
“I:\GIS_Workshop\Practicals\Practical_07\C\Data\ne_10m_admin_0_countries.zip”
	Go to Vector → Analysis Tools → Count Points in Polygon
 
  
	Also a new column is added to attribute table “NumPoints” indicating number of earth quake points in each country.
  
 
 
Performing spatial queries: 
	Go to Layer → Add Layer → Add Vector Layer and load 
“\GIS_Workshop\Practicals\Practical_07\D\Data\ne_10m_populated_places_simple\ne_10m_populat  ed_places_simple.shp” and 
“I:\GIS_Workshop\Practicals\Practical_07\D\Data\ne_10m_rivers_lake_centerlines\ne_10m_rivers_lake_centerlines.shp” from project data folder. 
  
	Open project Properties → Set CRS “World_Azimuthal_Equidistant EPSG 54032” . The map will be re-projected as
  
	Go to Vector → Geoprocessing Tool → Buffer
 
 
	Repeat the step to create River Buffer
 
 
	Create a buffer for River
 
 
	Go to Vector → Research Tool → Select By Location
 
 
	This will highlight only those rivers containing a populated place within 2 KM


 
 
 
PRACTICAL NO:09 
Aim: Advanced GIS Operations 1: Nearest Neighbor Analysis, Sampling Raster Data using Points or Polygons, Interpolating Point Data. 







Nearest Neighbor Analysis: 
	Go to Layer → Add Vector Layer → Select “ne_10m_populated_places_simple.shp”
 
 
	Add Delimited Layer → Select “earthquakes.tsv”
 
 
 
 
	Press Add.
 
 
	Go to Processing → Toolbox → Vector Geometry → Null Geometries
 
 
	Click Save to File → “Neighbor9a.gpkg” → RUN
	Output:
 
 
 
 
 
 
Go to Processing Toolbox → Vector Analysis → Distance Matrix → Distance to nearest hub (line to hub)
  
	Click Save to File → “NearestNeighbor9a.gpkg” → RUN
Output: 
 
 
 
 
 
Sampling Raster Data using Points or Polygons: Points 
	Go to Layer → Add Raster Layer →Select “us.tmax_nohads_ll_20140525_float.tif ”
 
 
	Add Delimited Layer → Select “2013_Gaz_ua_national.txt”
 
 
	Press Add.
 
	Go to Processing	Toolbox →Raster Analysis → Sample Raster Values
 
 
	Press RUN.
Output: 
 
 
 
 
 
 
Polygons 
	Go to Layer → Add Vector Layer → Select “tl_2018_us_county.shp”
 
 
 
	Go to Processing	Toolbox → Raster Analysis → Zonal Statistics
 
 
 
	Press RUN.
	Right click on “tl_2018_us_county.shp” layer → Properties → Symbology
 
 
Click on Classify	Press Apply → Press OKOutput: 
 
 
 
 
 
 
Interpolating Point Data: 
	Add Vector Layer → Select 
“Arlington_Soundings_2007_stpl83.shp”
  
“Boundary2004_550_stpl83.shp” 
 
 
“Islands_2004_550_stpl83.shp”
 
 
	Go to Processing → Toolbox → Interpolation → TIN Interpolation
 
 
	Use Layer Extent
 
 
	Press OK.
 
 
 
  
	Save to File → “Elevation_Tin.tif” → Save → RUNOutput: 
 
 
 
 
	Go to Processing → Toolbox → GDAL → Raster Extraction → Clip raster by mask layer
 
 
	Clipped(mask) → Save to File → “Elevation_Tin_Clipped.tif” → Save
	Press RUN.Output: 
 
 
	Select only the Clipped layer → Properties → Symbology → Render type : Singleband 
Pseudocolor → Classify → Ok
 
 
Output: 
 
 
	Go to Processing → Toolbox →Raster Extraction → Contour
 
 
 
 
	Coutours → Save to File → Cntour.gpkg → Save
 
 
	Press RUN
Output: 
 
 
	Select only the Contour Layer → Properties → Labels → Single labels 
Value: ELEV
Placement: Curved 
 
 
  
	Press OK
Output: 
 
 
