To release a new version of Metanome the `maven-release-plugin` is used.
Druing the release process, the release has to be signed. 
Therefore, the [`maven-gpg-plugin`](https://maven.apache.org/plugins/maven-gpg-plugin/usage.html) is used. 
The `maven-gpg-plugin` is capseld in a profile named `performRelease`.
So you only need the gpg authentification files, if you want to release Metanome. 
To turn on the profile add `-DperformRelease=true` to your maven command when releasing Metanome.