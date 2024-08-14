# Data[](https://docs.geonode.org/en/4.3.0/usage/data/index.html#data "Permalink to this heading")

Data management tools built into GeoNode allow integrated creation of resources eg datasets, documents, link to external documents, map visualizations and other configured geonode apps. Each resource in the system can be shared publicly or restricted to allow access to only specific users. Social features like user profiles and commenting and rating systems allow for the development of communities around each platform to facilitate the use, management, and quality control of the data the GeoNode instance contains.

# Data Types[](https://docs.geonode.org/en/4.3.0/usage/data/data_types.html#data-types "Permalink to this heading")

GeoNode welcome page shows a variety of information about the current GeoNode instance.

You can explore the existing data using many search tools and filters (see [Finding Data](https://docs.geonode.org/en/4.3.0/usage/data/finding_data.html#finding-data)) or through the links of the navigation bar at the top of the page.

There are five main types of resources that GeoNode can manage:

1. Datasets
2. Maps
3. Documents
4. GeoStories
5. Dashboards

Each resource type has its own menu and can be reached through Datasets, Maps, Documents, GeoStories and Dashboards buttons on the navigation bar.

## Datasets[](https://docs.geonode.org/en/4.3.0/usage/data/data_types.html#datasets "Permalink to this heading")

Datasets are a primary component of GeoNode.

Datasets are publishable resources representing a raster or vector spatial data source. Datasets also can be associated with metadata, ratings, and comments.

By clicking the Datasets link you will get a list of all published datasets. If logged in as an administrator, you will also see the unpublished datasets in the same list.

GeoNode allows the user to upload vector and raster data in their original projections using a web form.

Vector data can be uploaded in many different formats (ESRI Shapefile, KML and so on…). Satellite imagery and other kinds of raster data can be uploaded as GeoTIFFs.

## Maps[](https://docs.geonode.org/en/4.3.0/usage/data/data_types.html#maps "Permalink to this heading")

Maps are a primary component of GeoNode.

Maps are comprised of various datasets and their styles. Datasets can be both local datasets in GeoNode as well as remote datasets either served from other WMS servers or by web service datasets such as Google or MapQuest.

GeoNode maps also contain other information such as map zoom and extent, dataset ordering, and style.

You can create a map based on uploaded datasets, combine them with some existing datasets and a remote web service dataset, share the resulting map for public viewing. Once the data has been uploaded, GeoNode lets the user search for it geographically or via keywords and create maps. All the datasets are automatically reprojected to web mercator for maps display, making it possible to use popular base maps such as [OpenStreetMap](https://www.openstreetmap.org).

## Documents[](https://docs.geonode.org/en/4.3.0/usage/data/data_types.html#documents "Permalink to this heading")

GeoNode allows to publish tabular and text data and to manage metadata and associated documents.

Documents can be uploaded directly from your disk (see [Upload/Add Documents](https://docs.geonode.org/en/4.3.0/usage/managing_documents/uploading_documents.html#uploading-documents) for further information).

The following documents types are allowed: txt, .log, .doc, .docx, .ods, .odt, .sld, .qml, .xls, .xlsx, .xml, .bm, .bmp, .dwg, .dxf, .fif, .gif, .jpg, .jpe, .jpeg, .png, .tif, .tiff, .pbm, .odp, .ppt, .pptx, .pdf, .tar, .tgz, .rar, .gz, .7z, .zip, .aif, .aifc, .aiff, .au, .mp3, .mpga, .wav, .afl, .avi, .avs, .fli, .mp2, .mp4, .mpg, .ogg, .webm, .3gp, .flv, .vdo, .glb, .pcd, .gltf.

Through the document detailed page is possible to view, download and manage a document.

## GeoStories[](https://docs.geonode.org/en/4.3.0/usage/data/data_types.html#geostories "Permalink to this heading")

GeoStory is a MapStore tool integrated in GeoNode that provides the user a way to create inspiring and immersive stories by combining text, interactive maps, and other multimedia content like images and video or other third party contents. Through this tool you can simply tell your stories on the web and then publish and share them with different groups of GeoNode users or make them public to everyone around the world.

## Dashboard[](https://docs.geonode.org/en/4.3.0/usage/data/data_types.html#dashboard "Permalink to this heading")

Dashboard is a MapStore tool integrated in GeoNode that provides the user with a space to add many Widgets, such as charts, maps, tables, texts and counters, and can create connections between them in order to:

- Provide an overview to better visualize a specific data context

- Interact spatially and analytically with the data by creating connections between widgets

- Perform analysis on involved data/layers.


# Finding Data[](https://docs.geonode.org/en/4.3.0/usage/data/finding_data.html#finding-data "Permalink to this heading")

This section will guide you to navigate GeoNode to find datasets, maps and documents and other resource types by using different routes, filters and search functions.

On every page you can find some quick search tool.

The _Search_ box in the navigation bar (see the picture below) let you type a text and find all the resource which have to deal with that text.

![../../_images/search_tool.png](https://docs.geonode.org/en/4.3.0/_images/search_tool.png)

_Search tool in GeoNode welcome page_[](https://docs.geonode.org/en/4.3.0/usage/data/finding_data.html#id2 "Permalink to this image")

When you trigger a search you are brought to the _Search_ page which shows you the search result through all data types.

![../../_images/search_page.png](https://docs.geonode.org/en/4.3.0/_images/search_page.png)

_The Search page_[](https://docs.geonode.org/en/4.3.0/usage/data/finding_data.html#id3 "Permalink to this image")

This page contains a wealth of options for customizing a search for various information on GeoNode. This search form allows for much more fine-tuned searches than the simple search box is available at the top of every page.

It is possible to search and filter data by Text, Types, Categories, Keywords, Owners, Regions, Group, Limitations on public access, Date and Extent.

Try to set some filter and see how the resulting data list changes accordingly. An interesting type of filter is _EXTENT_: you can apply a spatial filter by moving or zooming a map within a box as shown in the picture below.

![../../_images/search_filter_by_extent.png](https://docs.geonode.org/en/4.3.0/_images/search_filter_by_extent.png)

_Search filter by EXTENT_[](https://docs.geonode.org/en/4.3.0/usage/data/finding_data.html#id4 "Permalink to this image")

Data can be ordered by Most recent, Less recent, Name and Popularity.

![../../_images/ordering_data.png](https://docs.geonode.org/en/4.3.0/_images/ordering_data.png)

_Ordering Data_[](https://docs.geonode.org/en/4.3.0/usage/data/finding_data.html#id5 "Permalink to this image")