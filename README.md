p2-------------------------------------
git init
git add .
git commit -m "Initial commit"
git remote add origin <your-repository-url>
git push -u origin master

mvn clean install
git add docs/*
git commit -m "Deploy site to GitHub Pages"
git push origin master
access the website in pages


package org.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;


import static org.testng.Assert.assertTrue;


public class WebpageTest {

private static WebDriver driver;

 @BeforeTest
public void openBrowser() throws InterruptedException {
driver = new ChromeDriver();
 driver.manage().window().maximize();
Thread.sleep(2000);
driver.get("https://sauravsarkar-codersarcade.github.io/CA-MVN/"); // "Note: You should use your
GITHUB-URL here...!!!"

}

@Test
 public void titleValidationTest(){
String actualTitle = driver.getTitle();
 String expectedTitle = "Tripillar Solutions";
Assert.assertEquals(actualTitle, expectedTitle);

assertTrue(true, "Title should contain 'Tripillar'");
}
 @AfterTest
public void closeBrowser() throws InterruptedException {
Thread.sleep(1000);
driver.quit();
}
}

pom.xml


<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>yashaswini_maven_excerise</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.28.1</version>
        </dependency>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>7.4.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-resources-plugin</artifactId>
                <version>3.2.0</version>
                <executions>
                    <execution>
                        <phase>prepare-package</phase>
                        <goals>
                            <goal>copy-resources</goal>
                        </goals>
                        <configuration>
                            <outputDirectory>${project.basedir}/docs</outputDirectory> <!-- Deploy to /docs folder -->
                            <resources>
                                <resource>
                                    <directory>src/main/resources</directory>
                                    <includes>
                                        <include>*/</include> <!-- Copy all files in src/main/resources -->
                                    </includes>
                                </resource>
                            </resources>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.1.0</version>
                <configuration>
                    <!-- Specify the main class to be executed -->
                    <archive>
                        <manifestEntries>
                            <Main-Class>org.example.Main</Main-Class> <!-- Replace with your actual main class -->
                        </manifestEntries>
                    </archive>
                </configuration>
            </plugin>

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-site-plugin</artifactId>
                <version>3.12.1</version>  <!-- Use the latest version -->
            </plugin>
        </plugins>
    </build>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>


mvn test
mvn clean package
java -jar target/your-project-name.jar









p4 -------------------------------------------------------------

Open the pom.xml file.
Add the following inside the <project> tag:

<build>
<plugins>
<!-- Compiler Plugin -->
<plugin>
<groupId>org.apache.maven.plugins</groupId>
<artifactId>maven-compiler-plugin</artifactId>
<version>3.8.1</version>
<configuration>
<source>1.8</source>
<target>1.8</target>

</configuration>

</plugin>
<!-- Jar Plugin -->
<plugin>
<groupId>org.apache.maven.plugins</groupId>
<artifactId>maven-jar-plugin</artifactId>
<version>3.2.0</version>
<configuration>
<archive>
<manifest>
<mainClass>com.example.App</mainClass>
</manifest>
</archive>
</configuration>
</plugin>
</plugins>
</build>



mvn clean compile
mvn package
                     (Locate the JAR File
After running the above, your .jar file will be located at:)

D:\Idea Projects\MVNGRDLDEMO\target\MVNGRDLDEMO-1.0-SNAPSHOT.jar
                 Run the JAR File
      To run the generated JAR file, use:
java -jar target\MVNGRDLDEMO-1.0-SNAPSHOT.jar

gradle init --type pom

Open build.gradle in IntelliJ IDEA.
plugins {
id 'java'
}
group = 'com.example'
version = '1.0-SNAPSHOT'
repositories {
mavenCentral()
}
dependencies {
testImplementation 'junit:junit:4.13.2'
}
jar {
manifest {
attributes(
'Main-Class': 'com.example.App'
)
}
}


gradle clean build
java -jar build/libs/MVNGRDLDEMO-1.0-SNAPSHOT.jar










P3 GRADLE-------------------------------------------------------------------------
plugins {
id 'java'
id 'application'
}
repositories {
mavenCentral()
}
dependencies {
testImplementation 'org.junit.jupiter:junit-jupiter:5.8.1'
}
application {
mainClass = 'com.example.Main'
}
dependencies {
testImplementation 'org.seleniumhq.selenium:selenium-java:4.28.1' // use the latest stable version
testImplementation 'org.testng:testng:7.4.0' // use the latest stable version
}
test {
useTestNG()
}

gradle run
docs copy paste the docs folder

git init
git add .
git status
git commit -m "Deploy website using Gradle"
git remote add origin (new repo link paste)
git push -u origin master


package org.test;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;
import static org.testng.Assert.assertTrue;
public class WebpageTest {
private static WebDriver driver;

@BeforeTest
public void openBrowser() throws InterruptedException {
driver = new ChromeDriver();
driver.manage().window().maximize();
Thread.sleep(2000);
driver.get("https://sauravsarkar-codersarcade.github.io/CA-GRADLE/");
}
@Test
public void titleValidationTest(){
String actualTitle = driver.getTitle();
String expectedTitle = "Tripillar Solutions";
Assert.assertEquals(actualTitle, expectedTitle);
assertTrue(true, "Title should contain 'Tripillar'");
}
@AfterTest
public void closeBrowser() throws InterruptedException {

Thread.sleep(1000);
driver.quit();
}
}

gradle test

type this in build.gradle at last
jar {
manifest {
attributes 'Main-Class': 'com.example.Main'
}
}

gradle jar

java -jar build/libs/(copythejarname).jar
