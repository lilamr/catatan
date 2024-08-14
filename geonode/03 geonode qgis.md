# Using GeoNode with Other Applications[](https://docs.geonode.org/en/4.3.0/usage/other_apps/index.html#using-geonode-with-other-applications "Permalink to this heading")

Your GeoNode project is based on core components which are interoperable and as such, it is straightforward for you to integrate with external applications and services. This section will walk you through how to connect to your GeoNode instance from other applications and how to integrate other services into your GeoNode project. When complete, you should have a good idea about the possibilities for integration, and have basic knowledge about how to accomplish it. You may find it necessary to dive deeper into how to do more complex integration in order to accomplish your goals, but you should feel comfortable with the basics, and feel confident reaching out to the wider GeoNode community for help.

# QGIS Desktop[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#qgis-desktop "Permalink to this heading")

QGIS is a professional GIS application that is built on top of and proud to be itself Free and Open Source Software (FOSS). QGIS is a volunteer driven project if you are interested you can find more information at [https://www.qgis.org](https://www.qgis.org).

![../../../_images/geonode_qgis_desktop.PNG](https://docs.geonode.org/en/4.3.0/_images/geonode_qgis_desktop.PNG)

_QGIS Desktop Main Window_[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#id1 "Permalink to this image")

## How can I connect to Geonode?[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#how-can-i-connect-to-geonode "Permalink to this heading")

Open QGIS Desktop and go to **Layer Menu > Data Source Manager**. At the bottom of Data Source Manager, you can see a tab with the name and an icon related to Geonode. This is because Geonode is recognized as a data source inside QGIS.

![../../../_images/geonode_datamanager_dialog.PNG](https://docs.geonode.org/en/4.3.0/_images/geonode_datamanager_dialog.PNG)

_Data Source Manager Dialog_[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#id2 "Permalink to this image")

Note

It’s possible as well load Geonode instances from an existence file this is useful to share between users or to backup existence connections.

To add a new Geonode instance, in the Geonode tab selected click on **New** and you will see the following dialog:

![../../../_images/geonode_connection_details.PNG](https://docs.geonode.org/en/4.3.0/_images/geonode_connection_details.PNG)

_Details of Geonode instance Dialog_[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#id3 "Permalink to this image")

In the dialog Fill the name as you like and in the URL put the link of the Geonode instance. It’s possible edit some WFS and WMS options to optimize the connection. If everything is ok you will receive the following successful connection dialog:

![../../../_images/geonode_success_connection.PNG](https://docs.geonode.org/en/4.3.0/_images/geonode_success_connection.PNG)

_Successful connection Dialog_[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#id4 "Permalink to this image")

After the successful dialog it’s now possible to load all layers of the Geonode instance clicking on **Connect** button. You can see both WMS and WFS connections of the Geonode and you can load to QGIS Desktop.

![../../../_images/geonode_load_layers.PNG](https://docs.geonode.org/en/4.3.0/_images/geonode_load_layers.PNG)

_Geonode instance layers Dialog_[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#id5 "Permalink to this image")

After select a layer (WMS or WFS) click on the **Add** button and the layer will be displayed in the main window of QGIS.

![../../../_images/geonode_example_layer.PNG](https://docs.geonode.org/en/4.3.0/_images/geonode_example_layer.PNG)

_Example of Geonode layer_[](https://docs.geonode.org/en/4.3.0/usage/other_apps/qgis/index.html#id6 "Permalink to this image")

Warning
This procedure only work with public layers. If the layers are for private use is necessary to do the standard qgis add remote WMS/WFS layers (through **Data Source Manager**) along with basic auth method and specific endpoints.