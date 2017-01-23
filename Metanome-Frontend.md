# Metanome Frontend

The frontend of Metanome is build with AngularJS and based on the Google Material Design guidelines.

The frontend is structured the following way:
~~~
├──  src/
│   ├──  <Files from Metanome-Frontend Repository>
│
├──  WEB-INF/
│	├── web.xml 
├──  pom.xml
~~~
The [Metanome-Frontend](https://github.com/HPI-Information-Systems/Metanome-Frontend) repository contains the actual frontend. It is structured according to the [Best Practice Recommendations for Angular App Structure](https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub). 

## Development setup

For local development you first have to install `node`, `bower` and `gulp`.

To ensure that users, who check out Metanome, have all these dependencies we use the [maven-frontend-plugin](https://github.com/eirslett/frontend-maven-plugin). This will locally install the dependencies when calling `mvn clean install`, so that the user does not have to install anything by himself. 

When the backend is running you can start the frontend by executing `gulp serve` in the `src/` directory. This launches a browser sync server on your source files, so you do not have to start the frontend again while making changes to your webapp.
You can then open the frontend under [http://localhost:8080/](http://localhost:8080/).

For building an optimized version of the metanome application you have to execute `gulp` of `gulp build` in `src/main/webapp`. The optimized version can then be found in `/src/main/webapp/metanome`.


## Define Backend Variables
To define e.g. IP for the backend or other variables defined in `src/app/scripts/config.js` are two possibilities how to define them.

### 1. Export variables as system environment variables 

### 2. Use an `.env` file to define the variables
