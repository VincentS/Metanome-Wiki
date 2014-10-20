### The Metanome Repository
As a web application, Metanome consists of two major projects: The _backend_ project and the _frontend_ project. A third project, the _algorithm_integration_, contains the Metanome algorithm interface that we need to include in our profiling algorithm in order to run within Metanome. In the following, we list and describe all sub-projects of Metanome in more detail:

* **algorithm_helper**: This project contains useful classes and functions for the development of profiling algorithms. Some contructs like _position list indices_ or _sub set graph_ might be useful for different algorithms, so we collect such datastructures in a dedicated package.
* **algorithm_integration**: This project contains the Metanome interfaces that a profiling algorithm needs to implement in order to run within Metanome. The profiling task of the algorithm defines which interfaces are necessary and which are not. Metanome uses the interface to set configuration parameters, define the input data, start the algorithm and collect the results.
* **algorithm_template_root**: This project contains a template with which a developer can start an own algorithm. The template shows how the maven pom.xml file of a Metanome profiling algorithm should look like and how Metanome should be referenced. 
* **backend**: This project contains the backend logic of Metanome. It defines how algorithms are executed and how assets are stored on disk. If a developer wants to learn how Metanome works, this is the project to explore first.
* **deployment**: This project defines how Metanome is packaged and deployed for the user. It contains the batch files with which Metanome can be deployed on a Jetty server.
* **docs**: This project should contain documentation for Metanome, but since Metanome is under havy development the given meterial might not always be up to date.
* **frontend**: This project contains the web frontend of Metanome. It is based on the Google Web Toolkit (GWT) and implements the user interaction of Metanome.
* **test_helper**: This project contains common testing functionality for Metanome. It is used in Metanome's JUnit tests.
* **testing_algorithms**: This project contains (dummy) profiling algorithms used by Metanome's automated test cases. The purpose of these algorithms is to check the functionality of the Metanome algorithm interfaces. But a developer can also inspect these algorithms to get an idea of how to implement the Metanome interfaces. 

### Starting a new profiling algorithm
The easiest way to start a new profiling algorithm is to copy the template project _algorithm_template_ from the _algorithm_template_root_ project of the Metanome GitHub repository. For convenience, import the copied project into your development IDE of choise (e.g. Eclipse or IntelliJ) as Maven project. Then, change the name of the algorithm from _algorithm_template_ to the name of your algorithm and change the package name. These changes also require to change the according names in the pom.xml file of your project.

Having configured your project, check the Metanome interfaces and change them according to the type of profiling algorithm that you want to implement. An overview over the provided interfaces is given below. 

Hint: It has been shown that separating the profiling algorithm from the interface implementation is a good pattern. So you could have one class _MyAlgorithm_ that is the implementation of your new profiling algorithm and one class e.g. _MyAlgorithmConfigurator_ that implements the Metanome algorithm interface and configures your algorithm. Thereby, _MyAlgorithmConfigurator_ can ether subclass _MyAlgorithm_ or wrapper _MyAlgorithm_ to set the configuration parameters given by Metanome on the actual algorithm. Note that _MyAlgorithmConfigurator_ must then be the bootstrap class defined in the pom.xml.

Finally, you can use maven to compile your algorithm into a Metanome conform jar. This jar file can then be registered in a running Metanome instance.

### The Metanome algorithm interface


### Building a TestRunner


