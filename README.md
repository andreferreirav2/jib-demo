
#### Run a docker registry:
```bash
$ docker run -d -p 5000:5000 --name registry -v /var/tmp:/var/lib/registry --restart always registry:2
```

#### push the openjdk image to your local registry
```
$ docker pull openjdk:8-jre-alpine
$ docker tag  openjdk:8-jre-alpine localhost:5000/openjdk:8-jre-alpine
$ docker push localhost:5000/openjdk:8-jre-alpine
```

#### Build you image
```bash
$ cd complete
$ mvn clean install com.google.cloud.tools:jib-maven-plugin:0.10.1:dockerBuild
```

#### Run you docker image
```bash
$ docker run -p 8080:8080 localhost:5000/jibdemo/helloworld
```
