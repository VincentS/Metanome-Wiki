**General rules for Metanome Developer:**

1. We are working with feature branches: Create a branch for each issue/feature you are working on.
2. Delete branches, which are not used anymore.
3. Reference the issue you are working on in your commits.
4. Follow the [coding style guidelines](https://code.google.com/p/google-styleguide/).
5. Write useful commit messages! What have you done? Explain, why the change was necessary.
6. Write comments for all important classes and methods.
7. Test first!
8. Write a short summary for your pull requests.
9. Pull request should be reviewed and merged by another person.
10. Push often, so that other developers can see and review your progress.


**Metanome Frontend Submodule**
The Metanome Frontend repository is included in the Metanome Frontend as an [git submodule](https://git-scm.com/docs/git-submodule)
into the Metanome project directory ```frontend/src``` and is maintained separately.

If changes are made to the Metanome Frontend the submodule reference has to be updated to the current HEAD of the Metanome Frontend repository using.

*Work in progress*

**Metanome API**

The documentation of the API of Metanome is written in [API Blueprint](https://apiblueprint.org/) and can be found [here](http://docs.metanome.apiary.io/#).

**Some useful links:**

* [How to set up development on frontend](https://github.com/HPI-Information-Systems/Metanome/wiki/Metanome-Frontend)
* [How to install the google style guide](https://github.com/HPI-Information-Systems/Metanome/wiki/Installing-the-google-styleguide-settings-in-intellij-and-eclipse)
* [How to publish a new Metanome release](https://github.com/HPI-Information-Systems/Metanome/wiki/Metanome-Releases)
* [Remote Access](https://github.com/HPI-Information-Systems/Metanome/wiki/Remote-Access)
* [Details about the result post processing](https://github.com/HPI-Information-Systems/Metanome/wiki/Result-Post-Processing)
* [How to add a new algorithm type](https://github.com/HPI-Information-Systems/Metanome/wiki/Adding-a-new-Algorithm-Type)
* [How to add a new configuration parameter](https://github.com/HPI-Information-Systems/Metanome/wiki/Adding-a-new-Configuration-Parameter)
