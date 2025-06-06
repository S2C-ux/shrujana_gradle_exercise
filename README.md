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
