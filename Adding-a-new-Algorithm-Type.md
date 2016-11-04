## Adding a new Algorithm Type

For adding a new algorithm type, you have to do the following steps:

**algorithm_integration**

1. Add a new interface to `de.metanome.algorithm_integration.algorithm_types`. It should extend the `Algorithm` interface.
2. Add your new result type to `de.metanome.algorithm_integration.results`. The new result must implement the interface `Result`.
3. Add a new result receiver interface to `de.metanome.algorithm_integration.result_receiver`.
4. Add the new result receiver interface to `OmniscientResultReceiver` in `de.metanome.algorithm_integration.result_receiver`.

**backend**

1. Add your new algorithm type to the algorithm type enum (`de.metanome.backend.results_db.AlgorithmType`).
2. Add your new result type to the result type enum (`de.metanome.backend.results_db.ResultType`).
3. Update the Algorithm class in `de.metanome.backend.results_db`. Add a variable for your algorithm type, create getter and setter for it and update the constructor.
4. Update the AlgorithmContentEquals class (`de.metanome.backend.results_db.AlgorithmContentEquals`).
3. In `de.metanome.backend.algorithm_execution.AlgorithmExecutor` add an `if`-statement in the `executeAlgorithm` method for your algorithm type.
4. In `de.metanome.backend.algorithm_loading.AlgorithmAnalyzer` add an `if`-statement in the `analyzerInterfaces` method.
5. In `de.metanome.backend.resources.AlgorithmResource` add a method for listing all algorithms of your type. Also update the `listAlgorithms` and `setAlgorithmTypes` methods.
6. Add missing methods to all result receivers in the package `de.metanome.backend.result_receiver`. Besides, an `if`-statement for reading the results has to be added in `ResultReader`. You can either use your own format or use JSON. (Using JSON might be slower.)
7. Update the result post processing:
 * Create a `ResultAnalyzer`, `ResultStore`, `ResultComparator`, `ResultRanking` and a new `Result` for your new result type.
 * Add `if`-statement to `de.metanome.backend.result_postprocessing.ResultPostProcessor`.
 * For details about the result post processing, see [here](https://github.com/HPI-Information-Systems/Metanome/wiki/Result-Post-Processing).

**frontend**

Update the javascript and html files in the 

The relevant folders are `src/app/new` and `src/app/result`

**testing_algorithms**

Create a testing algorithm for you new algorithm type.



***


**Add and update test!!!** 
This list might be incomplete, please update it!