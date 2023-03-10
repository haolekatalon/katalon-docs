---
title: "Resolve external dependencies for a plugin"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-store/docs/publisher/resolve-external-dependencies.html
redirect_from:
    - "/katalon-store/docs/publisher/resolve-external-dependencies/"

description: Guides to resolve external dependencies for a plugin and examples
---

This article shows you how to resolve external dependencies for a plugin. 

## Upload your dependencies to Maven Central Repository

> If your dependencies are already available on the Maven Central Repository, skip this step.

To upload your dependencies to the Maven Central Repository, you can refer to this guide in the Maven document: [Guide to uploading artifacts to the Central Repository](https://maven.apache.org/repository/guide-central-repository-upload.html#guide-to-uploading-artifacts-to-the-central-repository).

## Add your dependencies to the `build.gradle` file

Once your dependencies are available on Maven Central Repository, you can add them to the `build.gradle` file. 
You can refer to the `build.gradle` file in our sample project here on Github: [Zip custom keywords plugin](https://github.com/katalon-studio/katalon-studio-zip-keywords-plugin/blob/master/build.gradle).

To open the `build.gradle` file in Katalon Studio, do as follows:

1. Go to **File** > **New** > **Project**, check the **Generate build.gradle file** box. 

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-store/docs/publisher/KS-8.2.5-Generate-build.gradle-file.png" width=70% alt="Generate build.gradle file">

Katalon Studio will generate a default `build.gradle` template.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-store/docs/publisher/KS-8.2.5-Template-build-gradle.png" width=100% alt="The build.gradle template">

2. Add your dependencies to the `build.gradle` file. For example, we want to add our external dependencies to the **Zip custom keywords** plugin. We enter the following code in the `build.gradle` file:

<details><summary>For Gradle 7</summary>

```
plugins {
  id 'java-library'
  id 'groovy'
  id 'com.github.johnrengelman.shadow' version '7.1.2'
  id 'com.katalon.gradle-plugin' version '0.1.1'
}

repositories {
  mavenCentral()
}

def pluginSources = [
  'Keywords',
  'Test Listeners',
  'Include/scripts/groovy'
]

sourceSets {
   main {
    groovy {
      srcDirs = pluginSources
      srcDir 'Libs' // generated by Katalon Studio
    }
  }
}

shadowJar {
  exclude 'Temp*.class'
}

groovydoc {
  source = pluginSources
  docTitle = 'Zip Custom Keywords'
}

dependencies {
  implementation 'net.lingala.zip4j:zip4j:1.3.2'
}
```

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-store/docs/publisher/KS-8.2.5-Gradle-7.png" width=100% alt="The build.gradle file for Gradle 7">

</details>


<details><summary>For Gradle 5-6</summary>

```
plugins {

  id 'java'

  id 'groovy'

  id 'com.github.johnrengelman.shadow' version '4.0.4'

  id "com.katalon.gradle-plugin" version "0.0.7"

}

repositories {

  jcenter()

  mavenCentral()

}

sourceSets {

  main {

    groovy {

      srcDirs = ['Keywords', 'Libs', 'Test Listeners', 'Include/scripts/groovy']

    }

  }

}

dependencies {

  compile 'net.lingala.zip4j:zip4j:1.3.2'

}

shadowJar {

  exclude 'Temp*.class'

}

katalon {

  dependencyPrefix = "com.katalon"

  minimize = false

}
```

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-store/docs/publisher/KS-8.2.5-Gradle-5-6.png" width=100% alt="The build.gradle file for Gradle 5-6">

</details>

By doing this, your dependencies are repackaged to avoid conflicts with other plugins.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-store/docs/publisher/repackaged.png" width=100% alt="Repackaged dependencies in Gradle">

## See also

- [Develop a custom keywords Plugin](https://docs.katalon.com/katalon-store/docs/publisher/develop-custom-keywords.html)