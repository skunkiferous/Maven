Maven
=====

Temporary Maven repository, until I add my artifacts to Maven Central ...

Most things here should be Apache licensed, but please check the individual projects; there might be forks of thrid-party projects too.

Maven Instruction :

* This script expects the following projects pulled from Github in a single parent folder (all the projects should be at same level):

	* /skunkiferous/Maven.
	* /skunkiferous/Common.
	* /skunkiferous/PrimitiveFunc.


* Run the following command to build any one of these project.

``` 	
	mvn -DaltDeploymentRepository=internal::default::file://<ABSOLUTE_PATH_TO_MAVEN_PROJECT_FOLDER> ^
	deploy -pl ../Common -am deploy
```

Example:

mvn -DaltDeploymentRepository=internal::default::file://D:/GithubPublic/Maven deploy -pl ../oss-parent

*Note:*
 * Recently, I got errors if a project *and it's parent* are both refered at the same time as modules. So I need to deploy them "separetly".
 * This command is being executed from 'Maven' project directory.
 * Switch '-am' ('also make') also builds the other projects that this project is dependent on.
 * remove '-pl ../Common -am deploy' part to build all the projects.

* Verify and commit the artifacts in github.

* IMPORTANT : Increment the versions of all the projects that were deployed and pushed to github so that the future release artifacts do not overwrite them.

* To include these artifacts as dependencies use following repository entry in your pom.xml.

```xml
	<repositories>
		<repository>
			<id>blockwithme-mvn-repo</id>
			<url>https://raw.github.com/skunkiferous/Maven/master</url>
		</repository>		
	</repositories>
```
