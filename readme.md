# GemFire Starter Project

This is a simple starter project that has a couple of features most GemFire developers would like.

1. Pre-configured build with the appropriate GemFire dependencies
2. Some scripts to start and shut down a GemFire cluster
3. A very basic Main which connects and performs an operation or two

## How to Run

This document assumes you have downloaded and unzipped GemFire and that its `bin` directory is included in your system's PATH. If you are uncertain about how to do that, the GemFire documentation provides detailed instructions: https://docs.vmware.com/en/VMware-GemFire/10.1/gf/getting_started-installation-install_standalone.html

### Start a GemFire Cluster
Even though starting GemFire with a locator and two servers requires four commands, a `startGemFire` script has been provided in the [scripts](scripts) directory. I've included start scripts for Linux (.sh) and Windows (.bat) platforms.

These scripts highlight how easy it is to automate GemFire. Plus, using one command instead of four (`gfsh`, `start locator`, `start server`, and `start server`) simplifies the process.

### Run the Example

To run the example, use `gradle run` (Linux) or `gradlew run` (Windows). This will compile the Main program, which connects to the local GemFire cluster, performs a `put`, a `get`, and prints the results from the `get`.

Congratulations, you've just run a GemFire app!

### Shut Down GemFire
A [`shutdownGemFire`](scripts) script is also provided for shutting down GemFire. Go ahead and run that once you no longer need GemFire running. I've provided shutdown scripts for Linux (.sh) and Windows (.bat) platforms.

### Any Cleanup

All the scripts tell GemFire to keep all its logs and data in the `project/data` directory. You can simply delete that directory if you don't want this example using extra space on your hard drive.

## Commercial Maven

GemFire uses a commercial repository so you can trust the source of the libraries. However, this also means you need a username and a password to access the repository. Here's how to set that up.

### The build.gradle File

Please note that the Gradle files use some "externalized" properties to avoid publishing the username and password on GitHub. In this example, the username is referenced as `mavenUser` and the password as `mavenPassword`. These properties are read through Gradle loading properties from the standard location `[user_home]/.m2/gradle.properties`.

```gradle
maven {
    credentials {
        username "$mavenUser"
        password "$mavenPassword"
    }
    url "https://commercial-repo.pivotal.io/data3/gemfire-release-repo/gemfire"
}
```
### [user_home]/.m2/gradle.properties
Here's an example of setting the username and password in the properties file:

```properties
mavenUser=example@example.com
mavenPassword=EXAMPLE-PLAINTEXT-PASSWORD
```
The properties file is typically located in the `.m2` directory of your home folder.

### Learn More GemFire Documentation

For more details, refer to the GemFire documentation:

https://docs.vmware.com/en/VMware-GemFire/10.1/gf/getting_started-installation-obtain_gemfire_maven.html
