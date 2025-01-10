# SELENIUM-WEBDRIVER.

**COMPANY NAME**: CODTECH IT SOLUTION PVT.LTD

**NAME**: OM JOSHI

**INTER ID**: CT6WKCL.

**DOMAIN**: SOFTWARE TESTING.

**BATCH DURATION**: January 5th,2025 to February 20TH,2025.

**MENTOR NAME**: NEELA SANTHOSH

**DESCRIPTION**: NAVIGATION FUNCTIONALITY USING SELENIUM WEBDRIVER.
Automating Navigation Functionality Using Selenium WebDriver
Automating navigation functionality is an essential part of web application testing, ensuring that users can seamlessly interact with a website by clicking links, using menus, and moving through different pages or sections. Selenium WebDriver provides an effective way to automate such navigation actions in web applications, helping QA teams confirm that the navigation flows are working as expected.

In this guide, we will walk through how to use Selenium WebDriver to automate the navigation functionality of a sample web application. This includes actions like clicking links, verifying page loads, and interacting with menus or other navigational elements.

Prerequisites
To begin automating navigation, you will need the following:

Selenium WebDriver: A powerful tool for automating browsers.
JUnit or TestNG: A framework to structure and run tests.
Maven or Gradle: For managing project dependencies.
Java: The programming language for writing test scripts.
Browser Drivers (e.g., ChromeDriver, GeckoDriver): These are needed for Selenium to interact with the browser.
Step 1: Setting Up the Project
First, create a Maven project in your IDE (e.g., IntelliJ IDEA, Eclipse) and set up the necessary dependencies for Selenium WebDriver and JUnit in your pom.xml file.

xml
Copy code
<dependencies>
    <!-- Selenium WebDriver dependency -->
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.0.0</version>
    </dependency>

    <!-- JUnit dependency for testing -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.7.0</version>
        <scope>test</scope>
    </dependency>
</dependencies>
Make sure to download the appropriate WebDriver for the browser you will be automating (e.g., ChromeDriver for Google Chrome).

Step 2: Writing the Test Script
Next, create a Java class for your navigation tests. We will automate the following actions:

Open the browser and navigate to a website.
Click on various navigation links or buttons.
Verify that the correct pages load.
Interact with other navigational elements such as dropdown menus.
Below is an example of a Selenium WebDriver script to automate these tasks:

java
Copy code
import org.junit.jupiter.api.*;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import static org.junit.jupiter.api.Assertions.*;

public class NavigationTest {

    WebDriver driver;

    @BeforeEach
    public void setUp() {
        // Set the path for ChromeDriver
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        driver = new ChromeDriver();
    }

    @Test
    public void testNavigationThroughLinks() {
        // Open the homepage
        driver.get("https://example.com");

        // Click the "About Us" link and verify the page is correct
        WebElement aboutLink = driver.findElement(By.linkText("About Us"));
        aboutLink.click();
        assertEquals("https://example.com/about", driver.getCurrentUrl());

        // Navigate back to the homepage
        driver.navigate().back();

        // Click the "Services" link and verify the page is correct
        WebElement servicesLink = driver.findElement(By.linkText("Services"));
        servicesLink.click();
        assertEquals("https://example.com/services", driver.getCurrentUrl());
    }

    @Test
    public void testNavigationUsingDropdown() {
        // Open the homepage
        driver.get("https://example.com");

        // Locate and interact with a dropdown menu
        WebElement menuButton = driver.findElement(By.id("menuButton"));
        menuButton.click();

        // Select an option from the dropdown (e.g., "Contact")
        WebElement contactOption = driver.findElement(By.linkText("Contact"));
        contactOption.click();
        assertEquals("https://example.com/contact", driver.getCurrentUrl());
    }

    @Test
    public void testForwardAndBackNavigation() {
        // Open the homepage
        driver.get("https://example.com");

        // Navigate to another page
        WebElement blogLink = driver.findElement(By.linkText("Blog"));
        blogLink.click();
        assertEquals("https://example.com/blog", driver.getCurrentUrl());

        // Use the browser's back and forward functionality
        driver.navigate().back();
        assertEquals("https://example.com", driver.getCurrentUrl());

        driver.navigate().forward();
        assertEquals("https://example.com/blog", driver.getCurrentUrl());
    }

    @AfterEach
    public void tearDown() {
        // Close the browser after each test
        driver.quit();
    }
}
Explanation of the Code
Setting up the WebDriver:

In the setUp method, we configure the WebDriver for Chrome and initialize it.
You can replace ChromeDriver with other drivers (like FirefoxDriver or EdgeDriver) depending on the browser you want to use.
Test 1: Navigation Through Links:

We start by opening the homepage (https://example.com).
We locate the "About Us" link and click it using findElement(By.linkText("About Us")). After clicking, we assert that the current URL matches the expected URL for the "About Us" page.
We navigate back to the homepage using driver.navigate().back() and repeat the process for the "Services" link.
Test 2: Navigation Using Dropdown:

We open the homepage and interact with a dropdown menu by first locating and clicking the menuButton.
After opening the dropdown, we select the "Contact" link and verify the URL.
Test 3: Forward and Back Navigation:

After visiting the homepage, we navigate to the "Blog" page and verify the URL.
Then we test the browser's forward and backward navigation using driver.navigate().back() and driver.navigate().forward().
Teardown:

After each test, the tearDown method closes the browser using driver.quit() to ensure that no browser instances remain open.
Step 3: Running the Test
To execute the tests, you can run the tests directly from your IDE (e.g., using JUnit). Alternatively, use Maven from the command line:

bash
Copy code
mvn test
This will run all the tests and produce a report showing the success or failure of each test.

Step 4: Enhancing the Tests
Explicit Waits: Selenium tests can sometimes fail if elements take time to load. Using WebDriverWait, you can make the tests more robust by waiting for elements to be visible or clickable before interacting with them.
java
Copy code
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
WebElement aboutLink = wait.until(ExpectedConditions.elementToBeClickable(By.linkText("About Us")));
aboutLink.click();
Handling Alerts: If your application uses JavaScript alerts or popups, you can handle these using Selenium’s Alert interface.
java
Copy code
Alert alert = driver.switchTo().alert();
alert.accept();  // Accept the alert
Parameterized Tests: You can use parameterized tests to run the same navigation tests with different URLs or page names.
Conclusion
Automating navigation with Selenium WebDriver ensures that the navigation functionality of a web application is thoroughly tested, including clicking links, interacting with dropdowns, and verifying page loads. This reduces the likelihood of broken links or navigation issues in the application and helps in maintaining a seamless user experience. With Selenium's rich set of browser interaction features, you can extend these tests to include more complex navigation workflows and edge cases, providing higher coverage for your web application.



