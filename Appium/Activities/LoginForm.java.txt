package com.ibm.appium.Appium_Project;

import java.net.MalformedURLException;
import java.net.URL;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.Test;

import io.appium.java_client.AppiumDriver;
import io.appium.java_client.MobileElement;

public class LoginForm {

	 WebDriverWait wait;
	 AppiumDriver<MobileElement> driver= null ;
	
	// @BeforeTest
	 @Test
	 public void setup() throws  MalformedURLException
	 {
		 //Set the desired capabilities
		 DesiredCapabilities caps= new DesiredCapabilities();
		 caps.setCapability("deviceName", "A2QDU17616002998");
		 caps.setCapability("platformName","android");
		 caps.setCapability("appPackage", "com.android.chrome");
		 caps.setCapability("appActivity", "com.google.android.apps.chrome.Main"); 
		 // instantiate Appium Driver
		 driver =new AppiumDriver<MobileElement>(new URL("http://0.0.0.0:4723/wd/hub/"),caps);
		  driver.manage().timeouts().implicitlyWait(30,TimeUnit.SECONDS);
		  driver.get("https://www.training-support.net/selenium");
         MobileElement LoginButton=driver.findElementById("");
         LoginButton.click();
		  
	 }
	 
}
