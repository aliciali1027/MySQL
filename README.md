# MySQL


Issue 1: How to create a new database host
====
Create a SQL user - To communicate with the database

1) Open the MySQL workbenchmark
choose the first SQL file

2) Create the new user:
CREATE USER 'hbstudent'@'localhost' IDENTIFIED BY 'hbstudent';

GRANT ALL PRIVILEGES ON * . * TO 'hbstudent'@'localhost';


3) Click the lightning button to execute the code and perform the operation:

4) Verify the user:

*Make sure the Username: hbstudent

REMEMBER: the password is hbstudent as well!!!!!!!!!!!

5) Go to the Homepage and see a new user is created now:


Issue 2: failed connection to JDBC Driver in Spring Boot project
====
Step 1: MySQL version is not updated to 8.X.X. 
Update the MySQL dependency in POM.xml:
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.14</version>
    </dependency>
https://blog.csdn.net/waterflying2015/article/details/81047128
*this could also solve the problem "Unable to load authentication plugin 'caching_sha2_password'"

Step 2: Change spring.datasource.driver-class-name=com.mysql.jdbc.Driver to:
        com.mysql.cj.jdbc.Driver 
https://stackoverflow.com/questions/50671681/cannot-load-driver-class-com-mysql-jdbc-driver-spring-boot

Step 3: Reimport POM.xml - Maven - Reimport
        And then: Rebuild the project and run again
       
Issue 3: java.sql.SQLNonTransientConnectionException: Public Key Retrieval is not allowed
====
Solution: Add allowPublicKeyRetrieval=true
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/blog?allowPublicKeyRetrieval=true&useSSL=false&serverTimezone=UTC
https://stackoverflow.com/questions/50379839/connection-java-mysql-public-key-retrieval-is-not-allowed




