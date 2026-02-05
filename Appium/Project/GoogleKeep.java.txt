package com.ibm.appium.Appium_Project;

import java.net.MalformedURLException;
import java.net.URL;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.Assert;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileElement;
public class GoogleKeep {
	 WebDriverWait wait;
	 AppiumDriver<MobileElement> driver= null ;
	
	 @BeforeTest
	 public void setup() throws  MalformedURLException
	 {
		 //Set the desired capabilities
		 DesiredCapabilities caps= new DesiredCapabilities();
		 caps.setCapability("deviceName", "pixel4Android");
		 caps.setCapability("platformName","android");
		 caps.setCapability("appPackage", "com.google.android.keep");
		 caps.setCapability("appActivity", ".activities.BrowseActivity"); 
		 // instantiate Appium Driver
		 driver =new AppiumDriver<MobileElement>(new URL("http://0.0.0.0:4723/wd/hub/"),caps);
		//  wait=new WebDriverWait(driver,30);			
		  driver.manage().timeouts().implicitlyWait(30,TimeUnit.SECONDS);
		  MobileElement GetStartedButton=driver.findElementById("com.google.android.apps.tasks:id/welcome_get_started");
		  GetStartedButton.click();
		}	 
  @Test
   public void Create_New_Note() throws InterruptedException
   {
	  MobileElement Add_Notes_Button=driver.findElementById("com.google.android.keep:id/notes");
		  Thread.sleep(1000);
	  Add_Notes_Button.click();
	  MobileElement Title_Element=driver.findElementById("com.google.android.keep:id/browse_note_interior_content");
	  Title_Element.sendKeys("");
	  MobileElement Desc_Element=driver.findElementById("com.google.android.keep:id/edit_note_text");
	  Desc_Element.sendKeys("Description"); 
	  MobileElement BackButton=driver.findElementByAccessibilityId("Open navigation drawer");
	  BackButton.click();
	  MobileElement  Verify_Added_Note=driver.findElementByLinkText("Description");
	  Assert.assertEquals(Verify_Added_Note, true);
   }
   
   @AfterTest
   public void teardown()
   {
	   driver.quit();
   } 
}
	