# Scalas Dockerfile

This repository contains **Dockerfile** of [Scalas](http://www.scala-sbt.org/0.13/docs/Scripts.html) and is based on [scala-sbt](https://github.com/hseeberger/scala-sbt)


## Base Docker Image ##

* [openjdk:8](https://hub.docker.com/_/openjdk)


## Installation ##

1. Install [Docker](https://www.docker.com)
2. Pull from public [Docker Hub Registry](https://registry.hub.docker.com):
```
docker pull alfredodiaz/scalas
```
Alternatively, you can build an image from Dockerfile:
```
docker build -t alfredodiaz/scalas github.com/alfredodiaz/scalas
```


## Usage Example ##
#### Create file helloworld.scala ####
```
#!/usr/bin/env scalas

/***
retrieveManaged := true
libraryDependencies += "org.slf4j" % "slf4j-log4j12" % "1.7.11"
*/

import org.apache.log4j.{BasicConfigurator, Level, Logger}

BasicConfigurator.configure();
Logger.getRootLogger().setLevel(Level.INFO);

Logger.getLogger(this.getClass()).info("Hello World")
```


#### Execute the example ####
```
docker run --rm -itv $PWD:/scripts  alfredodiaz/scalas /scripts/helloworld.scala
```

#### Example sharing the ivy2 repository ####
```
docker run --rm -itv $HOME/.ivy2:/home/dev/.ivy2 -v $PWD:/scripts  alfredodiaz/scalas /scripts/helloworld.scala
```


## Contribution policy ##

Contributions via GitHub pull requests are gladly accepted from their original author. Along with any pull requests, please state that the contribution is your original work and that you license the work to the project under the project's open source license. Whether or not you state this explicitly, by submitting any copyrighted material via pull request, email, or other means you agree to license the material under the project's open source license and warrant that you have the legal authority to do so.


## License ##

This code is open source software licensed under the [Apache 2.0 License]("http://www.apache.org/licenses/LICENSE-2.0.html").

