# Metanome Frontend

The frontend of Metanome is build with AngularJS and based on the Google Material Design guidelines.

The frontend is structured the following way:
~~~
├──  src/
│   ├──  main/
│   │   ├──  java/
│   │   ├──  resources/
│   │   ├──  webapp/
├──  pom.xml
~~~
The `webapp` folder contains the actual frontend. It is structured according to the [Best Practice Recommendations for Angular App Structure](https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub). 

## Development setup

The project is build with gulp, a streaming build system. The libraries are defined by bower, so that you first have to install all dependencies. Therefore, we use the [maven-frontend-plugin](https://github.com/eirslett/frontend-maven-plugin). So, when you initially run `mvn clean install` all dependencies will be installed. The installation step will be skipped the next time you run that command.


To start the backend jetty-server do the following:

1. Run `mvn clean install` for building the `.war` file in the `target` directory.
2. Start the jetty-server with `mvn jetty:run-war`

Each time you make changes to the backend you have to run these steps again.

When the backend is running you can start the frontend by executing `gulp serve` in the `src/main/webapp` directory. This launches a browser sync server on your source files, so you do not have to start the frontend again while making changes to your webapp.
You can then open the frontend under [http://localhost:3000/](http://localhost:3000/).


For building an optimized version of the metanome application you have to execute `gulp` of `gulp build` in `src/main/webapp`. The optimized version can then be found in `/src/main/webapp/metanome`.
