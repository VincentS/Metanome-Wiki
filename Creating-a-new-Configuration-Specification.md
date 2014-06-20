### alogorithm_integeration.configuration

1. Implement a configuration setting
* A configuration setting contains all values, which are set in the frontend and needed for execution.

2. Implement a configuration specification
* Contains a list of the configuration settings you just created
* Make it serializable in GWT

### algorithm_integeration.algorithm_types

3. Add a interface for your configuration value
* Each algorithm, which is using your configuration value, has to implement this interface.

### backend.configuration

4. Implement a configuration value
* Implements the interface ConfiguratoinValue

5. Add your configuration value to the ConfigurationValueFactory

### testing_algorithms

6. Adapt one testing algorithm so that it uses your configuration specification

### frontend.client.parameter

7. Implement a input field for your value (<value_name>Input)

8. Implement a input parameter widget
* Implements the interface InputParameterWidget