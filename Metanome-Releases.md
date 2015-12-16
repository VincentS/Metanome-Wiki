To release a new version of Metanome the `maven-release-plugin` is used.
Druing the release process, the release has to be signed. Therefore, the [`maven-gpg-plugin`](https://maven.apache.org/plugins/maven-gpg-plugin/usage.html) is used. 

Because travis needs those authentification files, the files has to be copied to travis. 
[Here](https://docs.travis-ci.com/user/encrypting-files/) you can find instructions how it is done.