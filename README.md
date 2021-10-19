A reproducer for [#518](https://github.com/autonomousapps/dependency-analysis-android-gradle-plugin/issues/518)

This project has one unused dependency:

```shell
> ./gradlew :lib-a:projectHealth

Execution failed for task ':lib-a:projectHealth'.
> Unused dependencies which should be removed:
  - implementation(project(":lib-b"))
```

The problem is in buildHealth:

```shell
./gradlew buildHealth
```

Actual result: success.  
Expected result: failed build.  

Workarounds:

- `strictMode(true)`
