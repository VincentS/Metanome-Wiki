## Result Post Processing

The result post processing is based on the work of a master project.
They analyzed and interpret the result of data profiling algorithms.
Therefore, they add some visualizations and statistics to Metanome.
Everything located in `de.metanome.backend.result_postprocessing` is based on the code from the master project.

After an algorithm execution is done, the results are written to disk. 
To show them in the frontend they have to be read again.
This is the first step, which is done in the `ResultPostProcessor`.
Afterwards, the results may be further analyzed and ranked.
A `ResultAnalyzer` is responsible for analyzing the results.
In a first step the `ResultAnalyzer` converts the results into a new result type based on the original one.
The new result type basically holds the old result type and adds some additional statistics to it.
The conversion of the result is done in the `ResultAnalyzer`.
If the user decides to further analyze the result a `ResultRanker` is created and the additional statistics are calculated.
Those statistics are then stored in the new result.
By default, Metanome is not using the extended result, because its calculation can take a while.
Having the result, a `ResultStore` is created.
The `ResultStore` is responsible for keeping the result of an execution in memory.
Having the result in the `ResultStore`, the frontend can request it via an api call.