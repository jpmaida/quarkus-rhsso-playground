# Quarkus + Red Hat Single Sign-On Playground

## Description
Application built using Quarkus which performs authentication and authorization using OpenID Connect on Red Hat Single Sign-On. 

## Prerequisites
* OpenJDK 11
* Red Hat Single Sign-On 7.6

## Making it work

Download Red Hat Single Sign-On using the following link https://access.redhat.com/products/red-hat-single-sign-on/ and 
extract the zip file wherever you choose. Once you've done that you need to create an administrative user. Let us suppose that you've 
extracted that in `/opt`.

```shell script
cd rh-sso-7.6
./bin/add-user-keycloak.sh -u admin
```

The script will prompt a password request to the new user. Choose one. This playground uses **admin** as password.

You are ready to go now !!! Execute the following command to start Red Hat Single Sign-On.

```shell
./bin/standalone.sh -Djboss.socket.binding.port-offset=100
```

The port offset is needed because the quarkus application uses 8080 as http port. You will probably have no surprises at this point. Red Hat Single Sign-On will start successfully.

Once it's started, start the application. For that your current directory must be the one in which you've clone this repo.

```
./mvnw quarkus:dev
```

Access the application using: http://localhost:8080/hello

In order to run the full playground is necessary to create a new realm, client id and user inside RHSSO's configurations. Use the link below:

https://developers.redhat.com/articles/2022/04/21/add-security-quarkus-application-using-red-hats-sso#