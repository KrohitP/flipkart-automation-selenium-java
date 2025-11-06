package Flipkart.Flipkart;

import java.time.Duration;
import java.util.Set;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import io.github.bonigarcia.wdm.WebDriverManager;

public class AppTest {

    public static void main(String[] args) {
        WebDriverManager.chromedriver().setup(); // Handles driver setup automatically
        WebDriver driver = new ChromeDriver();

        try {
            driver.manage().window().maximize();
            driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));

            WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(20));

            // Step 1: Launch Flipkart
            driver.get("https://www.flipkart.com");

            // Step 2: Close login popup if present
            try {
                WebElement closeLoginPopup = driver.findElement(By.xpath("//button[contains(text(),'✕')]"));
                closeLoginPopup.click();
            } catch (Exception e) {
                System.out.println("No login popup appeared.");
            }

            // Step 3: Search for product
            WebElement searchBox = wait.until(ExpectedConditions.visibilityOfElementLocated(By.name("q")));
            searchBox.sendKeys("iPhone 17 Pro Max");
            searchBox.submit();

            // Step 4: Click on product from search results
            wait.until(ExpectedConditions.elementToBeClickable(
                    By.xpath("//div[contains(text(),'Apple iPhone 17 Pro Max')]"))).click();

            // Step 5: Switch to new window
            String mainPage = driver.getWindowHandle();
            Set<String> allPages = driver.getWindowHandles();
            for (String page : allPages) {
                if (!page.equals(mainPage)) {
                    driver.switchTo().window(page);
                    break;
                }
            }

            // Step 6: Add to Cart
            wait.until(ExpectedConditions.elementToBeClickable(
                    By.xpath("//button[normalize-space()='Add to cart']"))).click();

            // Step 7: Click on Place Order
            wait.until(ExpectedConditions.elementToBeClickable(
                    By.xpath("//span[normalize-space()='Place Order']"))).click();

            // Step 8: Enter Mobile Number
            wait.until(ExpectedConditions.elementToBeClickable(
            		By.xpath("//input[@type='text']"))).sendKeys("8792070524");

            // Step 9: Continue Login
            wait.until(ExpectedConditions.elementToBeClickable(
                    By.xpath("//span[normalize-space()='CONTINUE']"))).click();

            System.out.println("Reached OTP/Second factor screen successfully ");

        } catch (Exception e) {
            System.out.println(" Test failed: " + e.getMessage());
            e.printStackTrace();
        } finally {
            driver.quit();
        }
    }
}
