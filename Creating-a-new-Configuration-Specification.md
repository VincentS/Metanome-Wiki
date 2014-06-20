### alogorithm_integeration.configuration

1. Implement a configuration setting <br> 
A configuration setting contains all values, which are set in the frontend and needed for execution.

2. Implement a configuration specification <br> 
A configuartion specification contains a list of the configuration settings you just created. Do not forget to make it serializable in GWT.

### algorithm_integeration.algorithm_types

3. Add a interface for your configuration value <br> 
Each algorithm, which uses your configuration value, has to implement this interface. You should name the method according to following pattern: <br>
set<value_name>ConfigurationValue(String identifier, <value_type>... values) throws AlgorithmConfigurationExecution.

### backend.configuration

4. Implement a configuration value <br>
Implements the interface ConfiguratoinValue

5. Add your configuration value to the ConfigurationValueFactory

### testing_algorithms

6. Adapt one testing algorithm so that it uses your configuration specification

### frontend.client.parameter

7. Implement a input field for your value (Name of input: <value_name>Input)

8. Implement a input parameter widget <br>
Implements the interface InputParameterWidget