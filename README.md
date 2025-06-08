p2-------------------------------------

open pom.xml here copy paste code at last it there 

nxt add the docs folder in src main resources 


git init
git add .
git commit -m "Initial commit"

creat new repo
git remote add origin <your-newrepository-url>
git remote show origin 
git status 

[pom.xml]
mvn clean install 
git add.
git commit -m "Added docs for deployment"
git push -u origin master

go to git settings pages access websites save


src test java (org.test) in that (webpageTest)

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

run this

[pom.xml]
mvn clean package 
java -jar target/your-project-name.jar or press tab

mvn site
mvn deploy

::::pom.xml :::::

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>simple-project</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>3.141.59</version>
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

<distributionManagement>
<repository>
<id>local-repo</id>
<url>file:///D:/my-local-maven-repo</url>
</repository>
</distributionManagement>

</project>








p4 -------------------------------------------------------------

Open the pom.xml file.
add the code after the properties :

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


1.mvn clean compile
2.mvn package
3.java -jar ./target/(prgname).jar
4.mvn clean install
5.java -jar ./target/(prgname).jar
6.gradle init --type pom
  2
  Yes

Open build.gradle in IntelliJ IDEA.
plugins {
id 'java' (this line add in that )
}

also add this at last :

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
java -jar ./build/libs/..jar










P3 GRADLE-------------------------------------------------------------------------
open build.gradle:

plugins {
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

open main class delete if class if we want we can add another line of println at last close }
terminal:
gradle run

paste docs folder in this

open git bash:
git init 
git add .
git status
git commit -m "Added the folder"
git status
git remote add origin (paste the new repo url)
git push -u origin master


In our repo go to settings ,page,....save
now open the website that generated

In build.gradle

at dependencies add this remove that:
dependencies {
testImplementation 'org.seleniumhq.selenium:selenium-java:4.28.1' // use the latest stable version
testImplementation 'org.testng:testng:7.4.0' 
}

before application add this test:

test {
useTestNG()
}

src,main ,java,in package create org.test ,
in that( webpageTest) in java class

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
