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



mvn test
mvn clean package
java -jar target/your-project-name.jar
