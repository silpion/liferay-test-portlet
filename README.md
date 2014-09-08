# Liferay Test Portlet

This _Liferay Test Portlet_ serves as a showcase for the _Liferay development
setup with Vagrant_. It deploys/copys the Liferay extensions to the auto deploy
directory of the Liferay server that is accessible from outside the VM.

The deployment/copying of each extension archive the the Liferay server is bound
to the _install_ phase of the *Maven* build lifecycle.


## Prerequisites

The development of the Liferay extensions requires:

* [Maven](http://maven.apache.org)
* Your favourite IDE (like Eclipse or IntelliJ Idea)


## Configuration

The deployment of the Liferay extensions requires the auto deploy directory to
be configured. There are 3 ways to set the required configuration:

* Define an environment variable `LIFERAY_AUTO_DEPLOY_DIR`.
* Set a system property `liferay.auto.deploy.dir` for the *Maven* build:

      mvn clean install -Dliferay.auto.deploy.dir=/my/auto/deploy/dir

* Create a properties file `liferay-dev.properties` in the users home directory
  and configure the `liferay.auto.deploy.dir` property in there.

*Note*: Builds will fail, when the Liferay auto deploy directory is not set.


## Extension Deployment

The archives of the Lifeay extensions (portlets etc.) to be deployed can simply
be copied to the `liferay-deploy` directory of the Vagrant VM containing the
Liferay server, which will deploy them automatically from there. When running a
standard *Maven* build, the packaged extension archive is automatically copied
to the deploy directory during the `install` phase of the *Maven* build lifecycle.

The setup uses the ```liferay-maven-plugin```. It executes the service builder
to generate the service classes (based on a ```service.xml``` file) and deploys
the extension archives to a Liferay server. Furthermore it provides a bunch of
other (hopefully) useful goals.
