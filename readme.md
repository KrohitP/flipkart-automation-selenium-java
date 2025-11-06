Flipkart Payment Journey Automation

This project automates the **Flipkart purchase flow** up to the **OTP (second-factor authentication)** screen using **Selenium WebDriver**, **Java**, and **Maven**.

---

Tech Stack

- **Java 21**
- **Selenium WebDriver 4.x**
- **Maven**
- **JUnit 5**
- **WebDriverManager**
- **Google Chrome**

---

Scenario Covered

1. Launches the Flipkart website  
2. Closes the login popup (if it appears)  
3. Searches for *iPhone 17 Pro Max*  
4. Opens the product page in a new tab  
5. Adds the product to the cart  
6. Proceeds to the “Place Order” page  
7. Enters a sample mobile number  
8. Reaches the OTP (2FA) page — end of flow  

------

Prerequisites

Before running the test, make sure you have:

-  [Java JDK 21+](https://www.oracle.com/java/technologies/javase-jdk21-downloads.html) installed  
-  [Maven](https://maven.apache.org/download.cgi) installed and added to `PATH`  
-  [Google Chrome](https://www.google.com/chrome/) installed  
-  [Git](https://git-scm.com/downloads) (to clone this project)  

---

Project Setup

Clone the Repository
bash
git clone https://github.com/<your-username>/flipkart-automation-selenium-java.git
cd flipkart-automation-selenium-java
