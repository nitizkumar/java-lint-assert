<h1 align="center">Pluggable linting utility for Java tests</h1>


[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://choosealicense.com/licenses/apache-2.0/)

The plugin for Java Gradle `test` task that reports presence of `assert`s in a test method body. 

## Features:
1. prints the number of assert calls in each test method to the console
1. limits the scan to recursively search from a top level package (for ex. 'com.jpmorgan')
1. allows verbose output


## Supported Testing Frameworks:
- JUnit 4
- JUnit 5

## Supported build types:
- Gradle 4.9 and above

## Installation:
1. git clone [https://github.com/jpmorganchase/java-lint-assert.git](https://github.com/jpmorganchase/java-lint-assert.git)
2. run `gradle clean build publish` from the root of the project. This will
* build core module
* build plugin module
* install core and plugin jars into your local maven repo and into `build` dir under the project root 

To see the plugin in action, `cd .\client` 
and run `gradle cleanTest test -i` . You should see the summary table:
 
 | Package  | Test file name | Test method name  | # asserts  |
 | :-------------: |:-------------:| :-------------:|  :-------------:|  
 | com/jpmorgan/java/lint  | PlaceholderTest.java | dummy | 0 | 
 
##Use:


#### Gradle:

In your `build.gradle` 

I: add the `java-lint-plugin` dependency to the `buildscript` section: 
```
buildscript {
   dependencies {
        classpath 'com.jpmorgan.java.lint:plugin:0.1.0-SNAPSHOT'
    }
}
```
II: Add the plugin: `apply plugin: com.jpmorgan.java.lint.LintTestsPlugin`

III: Configure lint:
```
test{
    lintAssert{
        packageName = "com.jpmorgan.java.lint" //optional or scan all
        verbose = true //optional, defaults to false
    }
}
```
IV: run your tests with `-i` on: `gradle test -i`


## License

The Apache 2.0 License). Please see [License](https://choosealicense.com/licenses/apache-2.0/) for more information.

