### The Metanome Repository
As a web application, Metanome consists of two major projects: The _backend_ project and the _frontend_ project. A third project, the _algorithm_integration_, contains the Metanome algorithm interface that we need to include in our profiling algorithm in order to run within Metanome. In the following, we list and describe all sub-projects of Metanome in more detail:

* **algorithm_helper**: This project contains useful classes and functions for the development of profiling algorithms. Some contructs like _position list indices_ or _sub set graph_ might be useful for different algorithms, so we collect such datastructures in a dedicated package.
* **algorithm_integration**: This project contains the Metanome interfaces that a profiling algorithm needs to implement in order to run within Metanome. The profiling task of the algorithm defines which interfaces are necessary and which are not. Metanome uses the interface to set configuration parameters, define the input data, start the algorithm and collect the results.
* **algorithm_template_root**: This project contains a template with which a developer can start an own algorithm. The template shows how the maven pom.xml file of a Metanome profiling algorithm should look like and how Metanome should be referenced. 
* **backend**: This project contains the backend logic of Metanome. It defines how algorithms are executed and how assets are stored on disk. If a developer wants to learn how Metanome works, this is the project to explore first.
* **deployment**: This project defines how Metanome is packaged and deployed for the user. It contains the batch files with which Metanome can be deployed on a Jetty server.
* **docs**: This project should contain documentation for Metanome, but since Metanome is under havy development the given meterial might not always be up to date.
* **frontend**: This project contains the web frontend of Metanome. It is based on the Google Web Toolkit (GWT) and implements the user interaction of Metanome.
* **test_helper**: This project contains common test functionality for Metanome. 
* **testing_algorithms**: This project contains (dummy) profiling algorithms used by Metanome's automated test cases. The purpose of these algorithms is to check the functionality of the Metanome algorithm interfaces. But a developer can also inspect these algorithms to get an idea of how to implement the Metanome interfaces. 

### Starting a new profiling algorithm
copy template
change package and file names
change the interfaces to what you need

good pattern: algorithm in one class and a sub-class/wrapper class to implement the interface

### The Metanome algorithm interface


### Building a TestRunner


