docker-hadoop-build
===================

## Build Apache Hadoop
Often when we use Apache Hadoop and would like to make a custom build (stock or forked) you'll have to rebuild the whole Hadoop, native libs, etc ... which takes 30+ minutes, and carries lots of dependencies (libraries, protobuf, etc - at a given version).

This Docker image contains the build process of Hadoop 2.4.1 nativelibs. Also the 64b version of nativelibs is released at our [RPM repository](http://dl.bintray.com/sequenceiq/sequenceiq-bin/hadoop-native-64-2.4.1.tar).

## Build the image
```
docker build -t sequenceiq/hadoop-nativelibs .
```

## Run the container
```
docker run -it --name hadoop-build sequenceiq/hadoop-nativelibs /bin/bash
```

## Run the container and publish to bintray

```
docker run -it -e BINTRAY_USER=xxx -e BINTRAY_KEY=xxx --name hadoop-build sequenceiq/hadoop-nativelibs /bin/bash
```

## Copy files from the container
```
docker cp hadoop-build:/tmp/hadoop-2.4.1-src/hadoop-dist/target/hadoop-2.4.1/lib/native/ DESTINATION
```

_Note: the name `hadoop-build` is specified at the time when launching the container using `--name hadoop-build`_

