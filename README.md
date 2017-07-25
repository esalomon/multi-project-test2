# multi-project-test2
This project contains a Grails Application and a Grails Plugin, the application is configured to use the plugin and there is no more. It was created using the Grails 3.2.11 version.

# Creation
Following the Plugins and [Multi-Project Builds](http://docs.grails.org/3.2.11/guide/plugins.html) section at the Grails 3 manual, a Multi-project could be configured following the next commands in a terminal:

```
echo "Creating the root folder..."
mkdir multi-project-test1
cd multi-project-test1

echo "Creating the settings.gradle file..."
echo "include 'myapp', 'myplugin'" >> settings.gradle

echo "Creating the Grails application..."
grails create-app myapp

echo "Creating the Grails plugin..."
grails create-plugin myplugin

echo "Configuring the dependency between the application and the plugin..."
echo "grails { plugins { compile project(':myplugin') } }" >> myapp/build.gradle 

echo "Executing the Grails application..."
cd myapp
grails run-app 
```

Note, sdk is used to handle the Grails versions and the commands were executed using Java 1.7 and Yosemite:

    JVM: 1.8.0_131 (Azul Systems, Inc. 25.131-b11)
    OS:  Mac OS X 10.11.6 x86_64

# Output

The grails run-app` command did not execute the application because it threw the next errors:

```
$ cd myapp
$ grails run-app
| Resolving Dependencies. Please wait...

FAILURE: Build failed with an exception.

* Where:
Build file '/Users/esalomon/grails3tests/multi-project-test2/myapp/build.gradle' line: 64

* What went wrong:
A problem occurred evaluating root project 'myapp'.
> Project with path ':myplugin' could not be found in root project 'myapp'.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

CONFIGURE FAILED

Total time: 12.072 secs
| Error Error initializing classpath: Project with path ':myplugin' could not be found in root project 'myapp'. (Use --stacktrace to see the full trace)
```
