# Capture Data 

The following flow shows an example on how to capture trainings data for a [machine learning model](https://github.com/SSV-embedded/TinyML_IR-Sensor) via Node-RED. 
The flow allows logging of training data and test data to a csv file as well as visualization of the measured values. In addition to the measured values, the timestamp and the corresponding labels are also added to the csv file.

![alt-text][Flow]

[Flow]: https://github.com/sze-ssv/Capture_Data/blob/c5b37f9055b667a83350c7f6125c7b61545024b1/Flow.png

On the right side of the window, next to the debug window, you can also find the dashboard tab. 
The dashboard looks like following: 

![alt-text][Dashboard]

[Dashboard]: https://github.com/sze-ssv/Capture_Data/blob/a5237569338459fa83816db67f0014b5c5a0027a/Dashboard.png

A button on the dashboard can be used to start logging to the csv file. The counter visualizes how many data sets are added to the file. As soon as the flow is redeployed, the counter starts at zero. 
Moreover the dashboard visualizes the data. The connected sensor measures 64 temperature values in an 8x8 array. 

## Loading Palette Nodes

The flow uses the following nodes which you need to install, before you can run the flow successfully: 

[Serial In](https://flows.nodered.org/node/node-red-node-serialport) \
[Heatmap](https://flows.nodered.org/node/node-red-contrib-ui-heatmap) \
[Counter](https://flows.nodered.org/node/node-red-contrib-counter) \
[Dashboard](https://flows.nodered.org/node/node-red-dashboard)



## Input Data 

For capturing the data we are [running Node-RED on windows](https://nodered.org/docs/getting-started/windows). The sensor is connect to the PC via USB. As an input node we are therefor using the `serial in`. The Serial Port can be found via the device manager. The input data is a JSON String. In the second step, the JSON string is converted to a JSON object. The sensor measuers the temperature. After converting the input data to a JSON object the `msg.paylpoad` therefore contains the 64 temperature values.  

## To CSV

The node `toCSV` can be used to add the timestamp and the label to the data. The preinstalled flow contains as class a zero. Changes to the class can be made in the following line of the node. Please note that the following [machine learning model](https://github.com/SSV-embedded/TinyML_IR-Sensor) can only classify numbers. 

``` 
msg.payload = data + ',' + msg.payload + ',' + "0"; 
```

Using the node `CSVtoFile` the storage location is defined. Make sure to enter the entire file path. Running Node-RED on windows you can access the file directly from your explorer. If you are running Node-RED on a Raspberry Pi you should use a FTP client to access the file. 