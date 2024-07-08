# Features

## Scan Card

### 1.0 Configure your repository with PaySwitcher dependency

Add the following maven repository to the settings.gradle file

```gradle
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        maven {
            url "https://maven.payswitcher.com/release/production/android/maven/${version}"
        }
    }
}
```

### 1.1 Add the Scan Card dependency

Add this scan card dependency to your build.gradle file

```gradle
dependencies {
  implementation 'io.payswitcher:react-native-payswitcher-scancard:0.0.1'
}
```

