This Android Gradle C++ project demonstrates generating a version.h file from an environment variable at build time.

```
$ MY_ENV_VERSION=1 ./gradlew assemble
$ cat app/src/main/cpp/version.h
namespace MyNamespace {
    int MY_VERSION = 1;
}
$ MY_ENV_VERSION=2 ./gradlew assemble
$ cat app/src/main/cpp/version.h
namespace MyNamespace {
    int MY_VERSION = 2;              s
}
$ MY_ENV_VERSION=2x ./gradlew assemble
> Task :app:buildCMakeDebug[armeabi-v7a] FAILED
C/C++: version.h:2:23: error: invalid suffix 'x' on integer constant
C/C++:     int MY_VERSION = 2x;
C/C++:                       ^
```

The last one, with erroneous int 2x, shows that the project builds when version.h changes.
