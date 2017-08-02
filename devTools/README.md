# Downloads

## Java 8 JDK Download

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

## IntelliJ

https://www.jetbrains.com/idea/

## STS Windows 64 Bit:

http://download.springsource.com/release/STS/3.8.4.RELEASE/dist/e4.6/spring-tool-suite-3.8.4.RELEASE-e4.6.3-win32-x86_64.zip

## Mac 64 Bit

http://download.springsource.com/release/STS/3.8.4.RELEASE/dist/e4.6/spring-tool-suite-3.8.4.RELEASE-e4.6.3-macosx-cocoa-x86_64.tar.gz

# Set up

## Gradle

Gradle will be the build tool and dependancy management tool of choice. Maven will not be an option.

First install Gradle on your machine:

https://gradle.org/install

In STS Gradle support needs to be added. At the time of writing this Gradle Buildship was not working with STS. Instead classic Gradle was installed.

Get the dashboard open.

Select the IDE Extensions

Select the Gradle Classic Extension

## Lombok

Lombok makes creating domain objects easy. Rather than coding all the boiler plate constructors and methods we normally need, with Lombok we can create JPA Entity Bean with everything we need like this:

```java

@Entity
@Table(name="product")
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Product implements Serializable {
    private static final long serialVersionUID = 1L;

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    @Getter @Setter
    private Long id;
    
    @Getter @Setter
    private String name;
    
    @Getter @Setter
    private Double price;
    
    @Getter @Setter
    private String description;
    
    @Getter @Setter
    private Integer quantity;

}

```
To get Lombok running we need to do three things:

1. Download the jar (https://projectlombok.org/download.html)
2. Install it into the IDE by double click the jar file. The jar will search for all eclipse instances including STS and asks for update. After the installation, the jar file - lombok.jar - is placed under the eclipse directory and "-javaagent:lombok.jar" is added in eclipse.ini.
2. Add it as a Gradle dependancies: compileOnly "org.projectlombok:lombok:1.16.14"

Watch the following video to learn how to use Lombak (https://projectlombok.org/videos/lombok.ogv)

# Services 

### Postgres

#### Development
One of our services is backed with a relation DB. This can be installed locally without much pain:

https://www.postgresql.org/download/

#### Cloud

PWS's market place offers Postgres (Elephant SQL). PCF Dev only offers MySQL, due to the way we develop our applications the SQL will not have to change. PWS will take care of puttting in the correct DB driver, for PCF Dev the application package will need to contain the correct driver

### Rabbit MQ

Our services use Rabbit MQ to communicate.

#### Development

Rabbit can be installed locally:

https://www.rabbitmq.com/download.html

It also can be obtained via Docker:

To start rabbit on the Docker images:

docker run -d -p 15672:15672 -p 5672:5672 rabbitmq:3.6.6-management

#### Cloud

PWS's market place offers Rabbit as does PCF Dev

### Redis

Redis is used as a system of record for the Order service.

#### Development

Redis can be installed locally:

https://redis.io/topics/quickstart

There is also a Docker image:

https://hub.docker.com/_/redis/

#### Cloud

PWS market place offers a Redis services
