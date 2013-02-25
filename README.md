Maven
=====

Temporary Maven repository, until I add my artifacts to Maven Central ...

Most things here should be Apache licensed, but please check the individual projects.

Maven Instruction :

* This script expects the following projects pulled from Github in one parent folder (all should be at same level):

	* /skunkiferous/Maven.
	* /skunkiferous/Base40
	* /skunkiferous/Common.
	* /skunkiferous/Primitiveable.
	* /skunkiferous/PrimitiveFunc.

* Run to build any one of these project.
	mvn -DaltDeploymentRepository=internal::default::file://<ABSOLUTE_PATH_TO_MAVEN_PROJECT_FOLDER> deploy -pl ../Base40 -am deploy
  Switch '-am' builds the other projects that this project is dependent on. 
* Verify and commit the artifacts in github.
* IMPORTANT : Increment the versions of all the projects that were deployed and pushed to github so that the future release artifacts will not overwrite them.


