# Aspire_test
Code challenge ,



package testng_day1;

import org.testng.annotations.Test;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;

public class Day1_TestNG {
	
	WebDriver driver;
	
	@SuppressWarnings("deprecation")
	@BeforeMethod
	
	public void Home_page() throws InterruptedException {
		
		
		System.setProperty("webdriver.chrome.driver", "/Users/avishw16/Downloads/chromedriver");
		driver = new ChromeDriver();
		driver.get("https://aspireapp.odoo.com/");
		driver.manage().window().maximize();
        driver.manage().timeouts().implicitlyWait(60, TimeUnit.SECONDS);
        driver.manage().timeouts().pageLoadTimeout(60, TimeUnit.SECONDS);
        
        
	
	}
	
	@Test
        public void TC_01 () throws InterruptedException {
		
		WebElement username = driver.findElement(By.xpath("//input[@name='login']"));
		username.sendKeys("user@aspireapp.com");
		WebElement password = driver.findElement(By.xpath("//input[@name='password']"));
		password.sendKeys("@sp1r3app");
		WebElement submit = driver.findElement(By.xpath("//button[@type='submit']"));
		submit.click();
		driver.findElement(By.xpath("//a[@class='o_app o_menuitem'  and @id='result_app_1']")).click();
		
		WebElement ele = driver.findElement(By.xpath("//a[@role='menuitem']//span[contains(text(),'Products')]"));
		JavascriptExecutor executor = (JavascriptExecutor)driver;
		executor.executeScript("arguments[0].click();", ele);
		driver.findElement(By.xpath("//button[@class='btn btn-primary o-kanban-button-new']")).click();
		driver.findElement(By.xpath("//input[@class='o_field_char o_field_widget o_input o_field_translate o_required_modifier']")).sendKeys("Test6Test");
		driver.findElement(By.xpath("//span[normalize-space()='Update Quantity']")).click();
		driver.findElement(By.xpath("//button[@class='btn btn-primary o_list_button_add']")).click();
		
		
		Actions action = new Actions(driver);
		
		
		driver.findElement(By.xpath("//div[@name='location_id']//input[@type='text']")).sendKeys("WH/Stock");
		
		Thread.sleep(2000);
		
		
		action.sendKeys(Keys.TAB).build().perform();
	
		
		driver.findElement(By.xpath("//div[@name='package_id']//input[@type='text']")).sendKeys("1");
		
		Thread.sleep(2000);
		
		action.sendKeys(Keys.TAB).build().perform();
		
		Thread.sleep(2000);
		
		driver.findElement(By.xpath("//input[@name='inventory_quantity']")).clear();
		
		driver.findElement(By.xpath("//input[@name='inventory_quantity']")).sendKeys("10000");
		
		action.sendKeys(Keys.TAB).build().perform();
		
		
		driver.findElement(By.xpath("//button[normalize-space()='Save']")).click();
	}
	
	
	
	@Test
    public void TC_02 () throws InterruptedException {
	
	WebElement username = driver.findElement(By.xpath("//input[@name='login']"));
	username.sendKeys("user@aspireapp.com");
	WebElement password = driver.findElement(By.xpath("//input[@name='password']"));
	password.sendKeys("@sp1r3app");
	WebElement submit = driver.findElement(By.xpath("//button[@type='submit']"));
	submit.click();
	
	
	driver.findElement(By.xpath("//a[@id='result_app_2']//div[@class='o_app_icon']")).click();
	driver.findElement(By.xpath("//button[normalize-space()='Create']")).click();	
	Thread.sleep(1000);
	
	
	driver.findElement(By.xpath("//input[@class='o_input ui-autocomplete-input']")).sendKeys("Test6Test");
	Thread.sleep(2000);
	
	
	
	Actions action = new Actions(driver);
	action.sendKeys(Keys.TAB).build().perform();
	
	Thread.sleep(5000);
	

	
	driver.findElement(By.xpath("//a[contains(text(),'Add a line')]")).click();
	
	driver.findElement(By.xpath("//td[@class='o_data_cell o_field_cell o_list_many2one o_required_modifier']//div[@name='product_id']//input[@type='text']")).sendKeys("Test6Test");
	Thread.sleep(2000);
	action.sendKeys(Keys.TAB).build().perform();
    Thread.sleep(2000);

	driver.findElement(By.xpath("//input[@name='product_uom_qty']")).clear();
    Thread.sleep(2000);
	driver.findElement(By.xpath("//input[@name='product_uom_qty']")).sendKeys("12");
	Thread.sleep(2000);
	action.sendKeys(Keys.TAB).build().perform();
	
	
	
	//driver.findElement(By.xpath("//button[normalize-space()='Save']")).click();
	
	
	driver.findElement(By.xpath("//span[normalize-space()='Confirm']")).click();
	
	Thread.sleep(2000);
	
	driver.findElement(By.xpath("//input[@class='o_field_float o_field_number o_field_widget o_input text-left']")).clear();
	Thread.sleep(2000);
	driver.findElement(By.xpath("//input[@class='o_field_float o_field_number o_field_widget o_input text-left']")).sendKeys("12");
	Thread.sleep(2000);
	driver.findElement(By.xpath("//span[normalize-space()='Mark as Done']")).click();
	Thread.sleep(3000);
	
	
	}
	
	
	
	
	

	@AfterMethod
	public void teardown() {
		
		driver.quit();
	}
}



