# pubman

A gradle script for publishing Android library to Bintray jCenter.

# Usage

### 1. Config Bintray API Key

Open the `local.properties` file in root project, append the following properties.

```
bintray.user=<your-login-id>
bintray.apikey=<your-api-key>
```

### 2. Add Bintray and Maven plugins

Open the `build.gradle` file in root project, add the following classpathes.

```groovy
buildscript {
    // ...
    dependencies {
        // ...
        classpath 'com.github.dcendents:android-maven-gradle-plugin:2.0'
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.8.0'
    }
}
```

### 3. Using pub.gradle

Go into the `build.gradle` file in a library module.

#### 3.1 Define pubspec as a extension property of `project`.

**NOTE: All properties are required of pubspec extension currently.**

```groovy
ext.pubspec = [:]

pubspec.groupId = '<library-group-id>'
pubspec.artifactId = '<library-id>'
pubspec.name = '<library-name>'
pubspec.description = '<library-description>'
pubspec.repo = '<library-repo>' // names of repos in Bintray, like: maven
pubspec.version = "<library-version>"
pubspec.packaging = '<library-packaging>'
pubspec.url = '<library-homepage>'
pubspec.gitUrl = '<library-git-url>'
pubspec.issueUrl = '<library-issue-url>'
pubspec.developerId = '<library-developer-id>'
pubspec.developerName = '<library-developer-name>'
pubspec.developerEmail = '<library-developer-email>'
pubspec.licenseName = '<library-license-name>'
pubspec.licenseUrl = '<library-license-url>'
pubspec.licenses = ["<library-license-name>"] // licenses' names available in Bintray. like MIT, Apache-2.0
```

##### A pubspec sample

```groovy
pubspec.groupId = 'com.samelody.livebattery'
pubspec.artifactId = 'livebattery'
pubspec.name = 'LiveBattery'
pubspec.description = 'A LiveData for monitoring Android battery.'
pubspec.repo = 'maven'
pubspec.version = deps.libVersionName
pubspec.versionCode = deps.libVersionCode
pubspec.packaging = 'aar'
pubspec.url = 'https://github.com/samelody/livebattery'
pubspec.gitUrl = 'https://github.com/samelody/livebattery.git'
pubspec.issueUrl = 'https://github.com/samelody/livebattery/issues'
pubspec.developerId = 'belinwu'
pubspec.developerName = 'Belin Wu'
pubspec.developerEmail = 'belinwu@qq.com'
pubspec.licenseName = 'Apache License 2.0'
pubspec.licenseUrl = 'https://raw.githubusercontent.com/samelody/livebattery/master/LICENSE'
pubspec.licenses = ["Apache-2.0"]
```

#### 3.2 Apply pub.gradle

```groovy
apply from: "https://raw.githubusercontent.com/samelody/pubman/master/pub.gradle"
```

### 4. Buind and Publish

```shell
gradlew clean build bintrayUpload
```

# License

```
Copyright 2019 Samelody.com

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```