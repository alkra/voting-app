FROM hypriot/rpi-java:1.7.0-jdk

RUN apt-get update && apt-get install -y maven && apt-get clean

WORKDIR /code

ADD pom.xml /code/pom.xml
RUN ["mvn", "dependency:resolve"]
RUN ["mvn", "verify"]

# Adding source, compile and package into a fat jar
ADD src /code/src
RUN ["mvn", "package"]

CMD ["/usr/lib/jvm/java-7-openjdk-armhf/bin/java", "-jar", "target/worker-jar-with-dependencies.jar"]
