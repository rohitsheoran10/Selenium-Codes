# Selenium-Codes
Selenium codes


Code for UdemyGenTest.java

package com.udemy.GenTests;

import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class UdemyGenTest {

	@Test
	public void test1() {

		WebDriver driver = new FirefoxDriver();

		driver.get("http://www.udemy.com");

		WebElement query = driver.findElement(By.linkText("Login"));

		query.click();

		// Fill Out UserName
		
		WebDriverWait wait =new WebDriverWait(driver, 4000);
		wait.until(ExpectedConditions.elementToBeClickable(By.id("id_email")));
		

		query = driver.findElement(By.id("id_email"));

		query.sendKeys("TestBillLogin@bcc.com");

		// Fill out Password

		query = driver.findElement(By.id("id_password"));

		query.sendKeys("TestBillPassword");

		// Click Login

		query = driver.findElement(By.cssSelector("input[type='submit'][value='Login']"));

		query.click();
		
		wait.until(ExpectedConditions.elementToBeClickable(By.xpath(".//*[@id='login-form']/div[1]/ul/li")));

		query = driver.findElement(By.xpath(".//*[@id='login-form']/div[1]/ul/li"));

		String errText = query.getText();
	}
}


















Code for the POM File:




<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.udemy</groupId>
	<artifactId>GeneralTests</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>GeneralTests</name>
	<description>General Tests for Udemy</description>
	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<junit.version>4.10</junit.version>

	</properties>

	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>${junit.version}</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-java</artifactId>
			<version>2.52.0</version>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-failsafe-plugin</artifactId>
				<version>2.19.1</version>
				<executions>
					<execution>
						<goals>
							<goal>integration-test</goal>
							<goal>verify</goal>
						</goals>
					</execution>
				</executions>
				<configuration>
					<includes>
						<include>**/*Test.java</include>
						<include>**/when*.java</include>
					</includes>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-plugin</artifactId>
				<version>2.19.1</version>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.5.1</version>
				<configuration>
				<fork>true</fork>
				<executable>C:\Program Files\Java\jdk1.8.0_66\bin\javac.exe</executable>
					<!-- put your configurations here -->
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>
