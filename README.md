# GWT Module Migration
To prepare GWT for J2CL the GWT modules need to separated from GWT.
There fore we need to create separate artifacts for each module. These artifacts will be located in separate repos. 

## Module Requirements
We made several decisions how to set up and implement the modules:

1. every module will have it's own repository
2. use Maven as build tool
3. structure the Maven project like this:
    * parent module
        * one Maven child module for the module itself (name: **gwt-[module name]**)
        * one Maven child module for GWT2-tests (name: **gwt2-tests**)
        * one Maven child module for j2cl-tests (name: **j2cl-tests**)
        * one Maven child module for junit-tests (name: **junit-tests**), if needed
4. locate the source code inside the jar
5. use the [fmt-maven-plugin](https://github.com/coveooss/fmt-maven-plugin) to format the code
6. use the [license-maven-plugin](https://github.com/mycila/license-maven-plugin) to set up the license header
7. add a `README.md`-file that describes the purpose of the module
8. add a `LICENSE`-file containing the Apache 2 license
9. add a `AUTHORS`-file 
10. add a `travis.yaml`-file 
11. add a `.gitignore`-file 
12. add additional docs

**Important Note** 

Even we are using a Maven multi module structure, the Maven child modules do not refer the parent pom!


## Example
[gwt-timer](https://github.com/FrankHossfeld/gwt-timer) is already migrated and uses the example structure. You can copy the files and structure from this Repo and use it as a base to start.

## Branching
During development and before the module is deployed to Maven Central, we will work with one branch (**master**).

Once we have deployed the module to Maven Central, we will use two branches in the module repos:
1. a **master** branch. This branch will contain the last deployed version and will only updated in case of a new deploy.
2. a **development** branch. We will use this branch for active development 

## Formatting
We will use the [fmt-maven-plugin](https://github.com/coveooss/fmt-maven-plugin) to format the code.

The plugin uses the [google-java-format](https://github.com/google/google-java-format) which follows [Google's code styleguide](https://google.github.io/styleguide/javaguide.html).

If you want your IDE to stick to the same format, check out the [available configuration files](https://github.com/google/styleguide).

* [Eclipse](https://github.com/google/styleguide/blob/gh-pages/eclipse-java-google-style.xml)
* [IntelliJ IDEA](https://github.com/google/styleguide/blob/gh-pages/intellij-java-google-style.xml)

and import this file to your IDE.
