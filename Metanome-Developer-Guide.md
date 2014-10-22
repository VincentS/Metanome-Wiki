### The Metanome Repository
As a web application, Metanome consists of two major projects: The _backend_ project and the _frontend_ project. A third project, the _algorithm_integration_, contains the Metanome algorithm interface that we need to include in our profiling algorithms in order to run them in Metanome. In the following, we list and describe all sub-projects of Metanome in more detail:

* **algorithm_helper**: This project contains useful classes and functions for the development of profiling algorithms. Some contructs like _position list indices_ or _sub set graphs_ might be useful for different algorithms, so we collect such data structures in a dedicated package.
* **algorithm_integration**: This project contains the Metanome interfaces that an algorithm needs to implement in order to run within Metanome. The profiling task of the algorithm defines which interfaces are necessary and which are not. Metanome uses the interface to set configuration parameters, define the input data, start the algorithm and collect the results.
* **algorithm_template_root**: This project contains a template with which a developer can start an own profiling algorithm. The template shows how the Maven pom.xml file of a Metanome profiling algorithm could look like and how Metanome should be referenced. 
* **backend**: This project contains the backend logic of Metanome. It defines how algorithms are executed and how assets are stored on disk. If a developer wants to learn how Metanome works, this is the project to explore first.
* **deployment**: This project defines how Metanome is packaged and deployed for the user. It contains the batch files with which Metanome can be deployed on a local Jetty web server.
* **docs**: This project should contain documentation for Metanome, but since Metanome is under heavy development the given material might not always be up to date.
* **frontend**: This project contains the web frontend of Metanome. It is based on the Google Web Toolkit (GWT) and implements the user interaction of Metanome.
* **test_helper**: This project contains common testing functionality for Metanome. It is used in Metanome's JUnit tests.
* **testing_algorithms**: This project contains (dummy) profiling algorithms used by Metanome's automated test cases. The purpose of these algorithms is to check the functionality of the Metanome algorithm interfaces. But a developer can also inspect these algorithms to get an idea of how to implement the Metanome interfaces. 

### Starting a new profiling algorithm
The easiest way to start a new profiling algorithm is to copy the template project _algorithm_template_ from the _algorithm_template_root_ project of the Metanome GitHub repository into your private workspace on your local machine. Then, import the copied project into your development IDE of choice (e.g. Eclipse or IntelliJ) as Maven project. Afterwards, change the name of the algorithm from _algorithm_template_ to the name of your algorithm and also change the package names if needed. These changes also require you to change the according names in the pom.xml file of your project.

Having configured your project, change the implemented Metanome interfaces in the code files according to the type of profiling algorithm that you want to implement. An overview of the provided interfaces is given below. 

Hint: It has been shown that separating the profiling algorithm from the interface implementation is a good pattern. So you could have one class _MyAlgorithm_ that is the implementation of your new profiling algorithm and one class e.g. _MyAlgorithmConfigurator_ that implements the Metanome algorithm interface and configures your algorithm. Thereby, _MyAlgorithmConfigurator_ can either subclass _MyAlgorithm_ or wrapper _MyAlgorithm_ to set the configuration parameters given by Metanome on the actual algorithm. Note that _MyAlgorithmConfigurator_ must then be defined as the bootstrap class in the pom.xml of the profiling algorithm.

Finally, you can use maven to compile your algorithm into a Metanome conform jar. This jar file can then be registered in a running Metanome instance as described [here](https://github.com/HPI-Information-Systems/Metanome/wiki/Metanome-User-Guide#manage-algorithms).

![Interface of the BINDER Inclusion Dependency algorithm](https://hpi.de/fileadmin/hpi/FG_Naumann/projekte/repeatability/DataProfiling/Metanome/interface.png)

### The Metanome algorithm interface
The _algorithm_integration_ project offers a set of interfaces for different purposes. First, your algorithm should implement one (or more) **task interfaces** e.g. _UniqueColumnCombinationsAlgorithm_,  _InclusionDependencyAlgorithm_ or _FunctionalDependencyAlgorithm_. This automatically defines the kind of output that Metanome expects from your algorithm. 

The algorithm must, furthermore, define the kind of **input data** that it can process. For instance, _FileInputParameterAlgorithm_ says that (csv) files can be processed and _DatabaseConnectionParameterAlgorithm_ says that a database connection can be used as data source. Note that an algorithm can only use one of these interfaces. If both files and databases can be used as input, then _RelationalParameterAlgorithm_ is the interface to go with.

Finally, the algorithm can specify **parameter types** e.g. _IntegerParameterAlgorithm_, _BooleanParameterAlgorithm_ or _StringParameterAlgorithm_. This allows the algorithm to query parameters of the respective type from Metanome. 

When implementing the configuration specification interfaces note that Metanome will set only those parameters that have been requested by the algorithm in _getConfigurationRequirements()_ before!

![](https://github.com/HPI-Information-Systems/Metanome/wiki/algorithm_types.png)

### Running your Algorithm

#### Run in Metanom 
The algorithm that you build can run within Metanome but you cannot start it in your IDE, because it needs external configuration. So you need to compile and package the algorithm and put it into a running Metanome instance in order to execute it on a specific dataset (as described [here](https://github.com/HPI-Information-Systems/Metanome/wiki/Metanome-User-Guide#manage-algorithms)). That is nice for the shipping of your algorithm but impracticable for development. For this reason, we propose to write a TestRunner project that mocks the functionality of Metanome and lets you execute and debug your algorithm in your IDE.

#### Building a TestRunner
A TestRunner is a project that declares the Metanome _backend_ project as dependency in its pom.xml file. In this way, it has access to all Metanome classes. Additionally, it declares the new profiling algorithm as a dependency. As the TestRunner can now utilize both Metanome and algorithm classes, it can instantiate the algorithm, set the required parameters and execute it. 

Students of the "Data Profiling and Data Cleansing" lecture are given a _MetanomeTestRunner_ project that can serve as a template for the TestRunner. Like the algorithm development project, this project needs to be imported into your development IDE as a Maven project. Afterwards, change the pom.xml of the project so that it references your new algorithm instead of BINDER. Then, change the _MetanomeMock_ class in order to configure your algorithm instead of BINDER. You can change the configuration values in the _Config_ class as well to serve your needs. Your algorithm will require at least an _InputGenerator_ and a _ResultReceiver_. It is absolutely fine if no further parameters are needed! Finally, you have to configure the execution of your algorithm. You will find the _main()_ function in the _Main_ class and examples for execution code in the _MetanomeTestRunner_ class. However, it depends on your experiments, your settings and your data how the execution should look like. To run the TestRunner, you have to run Maven's _package_ goal first so that it downloads all Metanome dependencies. Then, you can run the TestRunner as a common java project within your IDE.

