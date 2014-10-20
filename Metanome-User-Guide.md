### Download
You can download a Metanome build at the [download page](https://www.hpi.uni-potsdam.de/naumann/sites/metanome/files/) . The _deployment\<version\>.zip_ file contains all Metanome binaries and a Jetty web server. Extract it to a location of choice. 

Please note that if you started Metanome once, you should not copy or rename the _deployment\<version\>_ folder afterwards. Otherwise, you would loose all your data within Metanome, because due to the use of relative pathes the data is then not correctly referenced any more!

### Start
To start Metanome, extract the _deployment<version>.zip_ and run either _deployment<version>\run.bat_ if you are using Windows or _deployment\<version\>\run.sh_ if you are using Linux. Both scripts start a Jetty web server and automatically deploy Metanome. A console will show you the status of the deployment. When the console outputs "Started SelectChannelConnector@0.0.0.0:8080", your Metanome instance is running and ready to be used. 

Now start a web browser like Firefox, enter "localhost:8080" in the address bar and hit enter. The browser then connects to your Metanome instance and you can start profiling.

When you first start Metanome, there are several example datasets and algorithms. Most of the algorithms are only placeholders and do not provide real functionality. A good idea is to first delete all input sources and algorithms in your Metanome instance. Then, add your own sources and algorithms. You can find real algorithms at, for instance, the [Metanome home page](https://hpi.de/naumann/projects/data-profiling-and-analytics/metanome-data-profiling.html)

_(It is currently not possible to remove datasets or algorithms if they have already been executed, because they are linked to their results. We work on that issue.)_

### Stop
To stop Metanome, go to the console with the server's log messages and hit Ctrl+c. Then, accept the termination request. All data sources, algorithms and results will be stored in the _deployment\<version\>_ folder. So, if you start Metanome again later, they are still available.

### Manage Algorithms
On the Algorithms tab within Metanome, you can remove and add algorithms. You can choose a new algorithm as soon as you obtained the according Metanome-conforme jar-file and placed it in Metanome's algorithm folder: 

**deployment\<version\>/WEB-INF/classes/algorithms/**

If the algorithm does not appear in the dropdown list although it was placed in the correct folder, please refresh the web page.

### Manage Input Sources
Adding new input sources is similar to adding new algorithms. First, place the input file(s) in Metanome's input folder:

**deployment\<version\>/WEB-INF/classes/inputData/**

You can also setup a database and place your data there. Then, go to Metanome's Data Sources tab and use the form at the end of that page to specify a new input source. It is very important to specify the correct advanced options for your dataset, for instance, the used separator character, quote character, or escape character. If you make a mistake here, Metanome cannot parse the source correctly!

### General Notes
If you did a change and the change is not directly visible in the Metanome frontent, try to refresh the web page. This often helps if frontend and backend are out of sync. 