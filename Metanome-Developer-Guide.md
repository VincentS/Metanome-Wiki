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
The easiest way to start a new profiling algorithm is to copy the template project _algorithm_template_ from the _algorithm_template_root_ project of the Metanome GitHub repository into your private workspace on your local maschine. Then, import the copied project into your development IDE of choise (e.g. Eclipse or IntelliJ) as Maven project. Afterwards, change the name of the algorithm from _algorithm_template_ to the name of your algorithm and change the package name. These changes also require you to change the according names in the pom.xml file of your project.

Having configured your project, change the implemented Metanome interfaces in the code files according to the type of profiling algorithm that you want to implement. An overview over the provided interfaces is given below. 

Hint: It has been shown that separating the profiling algorithm from the interface implementation is a good pattern. So you could have one class _MyAlgorithm_ that is the implementation of your new profiling algorithm and one class e.g. _MyAlgorithmConfigurator_ that implements the Metanome algorithm interface and configures your algorithm. Thereby, _MyAlgorithmConfigurator_ can ether subclass _MyAlgorithm_ or wrapper _MyAlgorithm_ to set the configuration parameters given by Metanome on the actual algorithm. Note that _MyAlgorithmConfigurator_ must then be the bootstrap class defined in the pom.xml.

Finally, you can use maven to compile your algorithm into a Metanome conform jar. This jar file can then be registered in a running Metanome instance.

### The Metanome algorithm interface
The _algorithm_integration_ project offers a set of interfaces for different purposes. First, your algorithm should implement one (or more) task interfaces e.g. _UniqueColumnCombinationsAlgorithm_,  _InclusionDependencyAlgorithm_ or _FunctionalDependencyAlgorithm_. This automatically defines the kind of output that Metanome expects from your algorithm. 

The algorithm must furthermore define the kind of input data that it can process. For instance, _FileInputParameterAlgorithm_ says that (csv) files can be processed and _DatabaseConnectionParameterAlgorithm_ says that a database connection can be used as data source. Note that an algorithm can only use one of these interfaces. It both files and databases can be used as input, then _RelationalParameterAlgorithm_ is the interface to go with.

Finally, the algorithm can specify parameter types e.g. _IntegerParameterAlgorithm_, _BooleanParameterAlgorithm_ or _StringParameterAlgorithm_. This allows the algorithm to query parameters of the respective type from Metanome. 

When implementing the configuration specification interfaces note that Metanome will set only those parameters that have been requested by the algorthm before!

### Building a TestRunner
The algorithm that you build can run within Metanome but you cannot start it in your IDE. So you need to compile and package the algorithm and put it into a running Metanome instance in order to test it. That is nice for shipping your algorithm but impracticable for development. For this reason, we propose to write a TestRunner project that mocks the functionality of Metanome and lets you execute and debug your algorithm in your IDE.

A TestRunner is a project that declares the Metanome _backend_ project as dependency in its pom.xml file. In this way, it has access to all Metanome classes. Additionally, it declares the new profiling algorithm as dependency. As the TestRunner can now utilize both Metanome and algorithm classes, it can instantiate the algorithm, set the required parameter and execute it. 

Students of the Data Profiling and Data Cleansing lecture are given a MetanomeTestRunner project that can serve as a template for the TestRunner. Like the algorithm development project, this project needs to be imported into your development IDE as Maven project as well. Afterwards, change the pom.xml of the project so that it references your new algorithm instead of BINDER. Then, change the MetanomeMock class in order to configure your algorithm instead of BINDER. You can change the configuration values in the Config class as well to serve your needs. Your algorithm will require at least an InputGenerator and a ResultReceiver. It is absolutely fine if no further parameters are needed! Finally, you have to configure the execution of your algorithm. You will find the main() function in the Main class and examples for execution code in the MetanomeTestRunner class. However, it depends on your experiments, your settings and your data how the execution should look like. 

