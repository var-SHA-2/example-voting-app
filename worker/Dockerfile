FROM maven:3.5-jdk-8-alpine as build
WORKDIR /code
COPY . .
RUN mvn package -D skipTests

FROM openjdk:8-jre-alpine as run
WORKDIR /run
COPY --from=build /code/target/worker-jar-with-dependencies.jar /run/worker.jar
CMD java -jar /run/worker.jar