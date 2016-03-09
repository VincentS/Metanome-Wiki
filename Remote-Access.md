## Remote Access

To enable remote access we configured Jetty in a way, that it listens to all hosts. 
Therefore, we set the default host to `0.0.0.0` in jetty.xml.

The frontend needs to distinguish between development and production.
If you are in development mode, all your request should go to `localhost:8888`. 
However, if you deployed Metanome, the backend could be started at any url. 
Therefore, we have to configure the api calls. 
We are using `gulp-ng-config` for that purpose. 
In the file `config.json` the urls for the different purposes are defined.