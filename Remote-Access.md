## Remote Access

To enable remote access we configured Jetty in a way that it listens to all hosts. 
Therefore, we set the default host to `0.0.0.0` in `jetty.xml`.

The frontend needs to distinguish between development and production.
If you are in development mode, all your request go to `localhost:8888`. 
However, if you use Metanome in production mode, the backend can be started at any url. 
Your request have to go against that url.
Therefore, we have to configure the request, which are made from the frontend. 
We are using `gulp-ng-config` for that purpose. 
In the file `config.json` the urls for the different purposes are defined.
Having an empty url for production mode means, that the requests from the frontend are appended to the url the frontend is started at.