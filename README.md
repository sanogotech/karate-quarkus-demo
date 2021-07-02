# karate-quarkus-demo project

https://blog.ineat-group.com/2020/06/ceinture-noire-en-test-api-passez-au-dan-superieur-avec-karate/

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```
./mvnw quarkus:dev
```

## Packaging and running the application

The application can be packaged using `./mvnw package`.
It produces the `karate-quarkus-demo-1.0-SNAPSHOT-runner.jar` file in the `/target` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/lib` directory.

The application is now runnable using `java -jar target/karate-quarkus-demo-1.0-SNAPSHOT-runner.jar`.

## Creating a native executable

You can create a native executable using: `./mvnw package -Pnative`.

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: `./mvnw package -Pnative -Dquarkus.native.container-build=true`.

You can then execute your native executable with: `./target/karate-quarkus-demo-1.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/building-native-image.

## Init dev environment

Mongo, Keycloak and Postgres can be initialized with a docker-compose file :

```
docker-compose -f src/main/docker/docker-compose up
```

## Test

You can run Karate Tests with the following command :

```
mvn clean test -DargLine="-Dkarate.env=local" -Dtest=FeatureRunner 
```

## In summary, to run this example

1 - Initialize the dev stack (mongo, keycloak, postgres)
```
docker-compose -f src/main/docker/docker-compose.yml up -d
```

2 - Compile / run the application locally
```
mvn clean compile quarkus:dev
```

3 - Run NRT locally
```
mvn clean test -DargLine=“-Dkarate.env=local” -Dtest=FeatureRunner
```
