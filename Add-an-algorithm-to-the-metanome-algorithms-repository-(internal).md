In the internal metanome algorithms repository profiling algorithms are added, once they deliver reliable functionality. The algorithms are continously build and can automatically be added to the metanome distribution.
To add an existing algorithm project to the repository of metanome algorithms the following steps should be followed:

1. copy the maven project into a subdirectory of the algorithms repository
1. add the algorithm module to the root pom of the repo
1. in all of your poms set the parent pom to root pom like the following

    ```
    <parent>
      <groupId>de.uni-potsdam.hpi.metanome</groupId>
      <artifactId>algorithms</artifactId>
      <version>0.0.2-SNAPSHOT</version>
      <relativePath>../../pom.xml</relativePath>
    </parent>
    ```

1. remove the version tag from your modules the same version as in the root pom is used
1. remove unnecessary repository information e.g. all repos that are defined in root/parent should not be duplicated
1. all versions of metanome dependencies should be set to ${metanome.version}