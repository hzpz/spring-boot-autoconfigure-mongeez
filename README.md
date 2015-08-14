[![Maven Central](https://img.shields.io/maven-central/v/io.github.hzpz.spring.boot/mongeez-spring-boot-starter.svg)](http://search.maven.org/#artifactdetails|io.github.hzpz.spring.boot|mongeez-spring-boot-starter|1.0.0|jar)

# Spring Boot Starter for Mongeez
[Mongeez][mongeez] is a change management tool for Mongo databases. 
This project is a [starter][spring-boot-starter] for Spring Boot that can automatically configure Mongeez and run migration scripts.
The auto-configuration makes sure that the migrations happen before any Spring Data Mongo beans are initialized.

## Usage
 * Make sure Spring Data Mongo is configured properly. 
 * Add dependencies to Mongeez and the Spring Boot starter:

<!-- -->
    <dependency>
        <groupId>io.github.hzpz.spring.boot</groupId>
        <artifactId>mongeez-spring-boot-starter</artifactId>
        <version>1.0.0</version>
    </dependency>
    <dependency>
        <groupId>org.mongeez</groupId>
        <artifactId>mongeez</artifactId>
        <version>0.9.4</version>
    </dependency>

 * [Create a mongeez.xml file that includes all change logs][mongeez.xml] at `db/mongeez.xml`.
 
## Configuration
Mongeez can be configured by setting properties with the prefix `mongeez` or by using the `MongeezProperties` bean directly.

### Disable auto-configuration
To disable the auto-configuration of Mongeez completely, set the property `mongeez.enabled` to `false`.

### Location of migration script
The default expected location of the migration script (see [Create a mongeez.xml file that includes all change logs][mongeez.xml])
is `db/mongeez.xml`. The simplest way to override the location is by the setting the property `mongeez.location`.

### Database
By default, the auto-configuration will configure Mongeez to use the same database that is configured for Spring Data Mongo
(either by setting the property `spring.data.mongodb.database` or by using the `MongoProperties` bean directly). Override 
the database by setting the property `mongeez.database`.

[mongeez]: http://secondmarket.github.io/mongeez/
[mongeez.xml]: https://github.com/secondmarket/mongeez/wiki/How-to-use-mongeez#create-a-mongeezxml-file-that-include-all-change-logs
[spring-boot-starter]: http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using-boot-starter-poms
