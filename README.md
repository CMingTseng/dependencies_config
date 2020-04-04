# Android dependencies Config

# Ref :

  -  [Artifact Mappings]
-  [Android 项目实例config.gradle配置]


### How to Use ?
1. fork the project to your public repo

2. add  deps_xxxx_config.gradle into build.gradle (at root-project)


```sh
apply from : 'https://raw.github.com/{your github account}/dependencies_config/master/deps_androidx_test_config.gradle'

apply from : 'https://raw.github.com/CMingTseng/dependencies_config/master/deps_androidx_test_config.gradle'
```

at sub-project dependencies  replace rootProject.ext.dependencies["XXXXXX"]
```sh
testImplementation 'junit:junit:4.12' -->  testImplementation rootProject.ext.dependencies["junit"]
```


### Full Example

build.gradle at root project 

```sh
apply from : 'https://raw.github.com/{your github account}/dependencies_config/master/deps_androidx_test_config.gradle'

buildscript {
    repositories {
        google()
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.6.1'
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        google()
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```

build.gradle at app (sub-project) 

```sh
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation rootProject.ext.dependencies["arch-core-common"]
    androidTestImplementation rootProject.ext.dependencies["espresso-core"]
    testImplementation rootProject.ext.dependencies["junit"]
    androidTestImplementation rootProject.ext.dependencies["test-junit"]
}
```



   [Artifact Mappings]: <https://developer.android.com/jetpack/androidx/migrate/artifact-mappings>
   
   [Android 项目实例config.gradle配置]: <https://blog.csdn.net/Kenway090704/article/details/76930451>
