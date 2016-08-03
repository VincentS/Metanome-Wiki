##Adding a new Configuration Parameter

For adding a new configuration parameter, you have to do the following steps:

**alogorithm_integeration**

1. Implement a configuration setting in `de.metanome.algorithm_integration.configuration`: A configuration setting contains all values, which are set in the frontend and needed for execution. Your setting should extend either `ConfigurationSettingPrimitive` or `ConfigurationSettingDataSource`. 
2. Implement a configuration requirement in `de.metanome.algorithm_integration.configuration`: A configuration requirement contains a list of configuration settings. It should extend `ConfigurationRequirement`.
3. Add an interface for your configuration parameter `in de.metanome.algorithm_integration.algorithm_types`:
Each algorithm, which uses your configuration parameter, has to implement this interface. You should name the method according to following pattern: `set<value_name>ConfigurationValue(String identifier, <value_type>... values) throws AlgorithmConfigurationExecution`
4. Add the method `ConfigurationValue build(<your-configuration-requirement> requirement) throws AlgorithmConfigurationException` to `de.metanome.algorithm_integration.configuration.ConfigurationFactory`.

**backend**

1. Implement a configuration value in `de.metanome.backend.configuration`, which implements the interface `ConfigurationValue`.
2. Add your configuration value to `de.metanome.backend.configuration.DefaultConfigurationFactory`

**testing_algorithms**

Adapt one testing algorithm so that it uses your configuration requirement.

**frontend**

In `new.controller` update the methods `updateParameter` and `readParamsIntoBackendFormat`.


***

**Add and update test!!!** 
This list might be incomplete, please update it!