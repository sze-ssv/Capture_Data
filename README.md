# Capture Data 

The following flow shows an example on how to capture trainings data for a machine learning model via Node-RED. 
The flow allows logging of training and test data to a csv file as well as visualization of the measured values. In addition to the measured values, the timestamp and the corresponding labels are also added to the csv file.

![alt-text][Flow]

[Flow]: https://github.com/sze-ssv/Capture_Data/blob/c5b37f9055b667a83350c7f6125c7b61545024b1/Flow.png

On the right side of the window, next to the debug window, you can also find the dashboard tab. 
The dashboard looks like following: 

![alt-text][Dashboard]

[Dashboard]: https://github.com/sze-ssv/Capture_Data/blob/a5237569338459fa83816db67f0014b5c5a0027a/Dashboard.png

A button on the dashboard can be used to start logging to the csv file. The counter visualizes how many data sets are added to the file. As soon as the flow is redeployed, the counter starts at zero. 