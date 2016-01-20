To release a new version of Metanome the `maven-release-plugin` is used.

A summary of how to pushing to Maven Central with Sonatype can be found here [here](http://bealetech.com/blog/2013/04/10/pushing-to-maven-central-with-sonatype/).

Druing the release process, the release has to be signed. 
Therefore, the [`maven-gpg-plugin`](https://maven.apache.org/plugins/maven-gpg-plugin/usage.html) is used. 
The `maven-gpg-plugin` is capseld in a profile named `performRelease`.
So you only need the gpg authentification files, if you want to release Metanome. 
To turn on the profile add `-DperformRelease=true` to your maven command when releasing Metanome.

For pushing Metanome to Sonatype you need the correct access rights.
Therefore you have to create a Jira account and open a ticket to get developer access to Metanome.
For details see [here](http://central.sonatype.org/pages/ossrh-guide.html#SonatypeOSSMavenRepositoryUsageGuide-8a.ReleaseIt).

To check weather you have the correct access rights or not, see this [page](http://blog.sonatype.com/2010/11/what-to-do-when-nexus-returns-401/#.Vp9K-XUrJvA).

Note: Currently the URL `https://oss.sonatype.org` is used as Repository URL for release deployment instead of `https://oss.sonatype.org/service/local/staging/deploy/maven2/`. I got `Unauthorized` when publishing to `https://oss.sonatype.org/service/local/staging/deploy/maven2/`.