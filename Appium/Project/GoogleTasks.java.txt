package com.ibm.appium.Appium_Project;

import java.net.MalformedURLException;
import java.net.URL;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileElement;

public class GoogleTasks {
	 WebDriverWait wait;
	 AppiumDriver<MobileElement> driver= null ;
	
	 @BeforeTest
	 public void setup() throws  MalformedURLException
	 {
		 //Set the desired capabilities
		 DesiredCapabilities caps= new DesiredCapabilities();
		 caps.setCapability("deviceName", "pixel4Android");
		 caps.setCapability("platformName","android");
		 caps.setCapability("appPackage", "com.google.android.apps.tasks");
		 caps.setCapability("appActivity", ".ui.TaskListsActivity"); 
		 // instantiate Appium Driver
		 driver =new AppiumDriver<MobileElement>(new URL("http://0.0.0.0:4723/wd/hub/"),caps);
		  wait=new WebDriverWait(driver,30);			
		  driver.manage().timeouts().implicitlyWait(10,TimeUnit.SECONDS);
		  MobileElement GetStartedButton=driver.findElementById("com.google.android.apps.tasks:id/welcome_get_started");
		  GetStartedButton.click();
	 }	 
	 
	 @Test(priority=0)
	 public void add_Complete_Activity_with_Google_Tasks()
	 {
		driver.manage().timeouts().implicitlyWait(10,TimeUnit.SECONDS);
		MobileElement CreateNewTask_Element=driver.findElementByAccessibilityId("Create new task");
		CreateNewTask_Element.click();
		MobileElement Add_Title=driver.findElementById("com.google.android.apps.tasks:id/add_task_title");
		Add_Title.sendKeys("Complete Activity with Google Tasks"); 
		MobileElement Save=driver.findElementById("com.google.android.apps.tasks:id/add_task_done");
		Save.click();
	 }
	 
	 @Test(priority=1)
	 public void add_Complete_Activity_with_Google_Keep()
	 {
		    driver.manage().timeouts().implicitlyWait(10,TimeUnit.SECONDS);
			MobileElement CreateNewTask_Element=driver.findElementByAccessibilityId("Create new task");
			CreateNewTask_Element.click();
			MobileElement Add_Title=driver.findElementById("com.google.android.apps.tasks:id/add_task_title");
			Add_Title.sendKeys("Complete Activity with Google Keep"); 	 
			MobileElement Save=driver.findElementById("com.google.android.apps.tasks:id/add_task_done");
			Save.click();

	 }	 
	 @Test(priority=2)
	 public void add_Complete_the_second_Activity_Google_Keep_Task()
	 {
		    driver.manage().timeouts().implicitlyWait(10,TimeUnit.SECONDS);
			MobileElement CreateNewTask_Element=driver.findElementByAccessibilityId("Create new task");
			CreateNewTask_Element.click();
			MobileElement Add_Title=driver.findElementById("com.google.android.apps.tasks:id/add_task_title");
			Add_Title.sendKeys("Complete the second Activity Google Keep"); 
			MobileElement Save=driver.findElementById("com.google.android.apps.tasks:id/add_task_done");
			Save.click();

	 }	 
	 @AfterTest
	 public void TearDown()
	 {
		driver.quit(); 
	 }
	 
}
