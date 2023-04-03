# Selenimum là gì
Selenium Testing Framework là một công cụ tự động hóa thử nghiệm phần mềm dùng để kiểm tra ứng dụng web trên nhiều trình duyệt khác nhau và nền tảng hệ điều hành khác nhau. Selenium Testing Framework cung cấp một giao diện đơn giản để thao tác với trình duyệt web và kiểm tra các yếu tố của trang web, như văn bản, hình ảnh, các trường dữ liệu, nút, form, v.v. Công cụ này hỗ trợ nhiều ngôn ngữ lập trình, cho phép người dùng viết mã thử nghiệm dễ dàng hơn.

Chi tiết tài liệu [ở đây](https://www.selenium.dev/)

# Components
- [Selenium WebDriver](https://www.selenium.dev/documentation/webdriver/)
- [Selenium IDE](https://selenium.dev/selenium-ide/)
- [Selenium Grid](https://www.selenium.dev/documentation/grid/)

Hiện tại SBC đang sử dụng Selenium để test một số tính năng frontend quan trọng.

Selenium hiện tại hỗ trợ:
- Java
- Python
- CSharp
- Ruby
- JavaScript
- Kotlin

Dưới đây là một số ví dụ sử dụng ngôn ngữ Java.

Các IDE có thể dùng là:
- Visual Code
- IntelliJ IDEA
- Eclipse Java
- NetBean

Đề xuất sử dụng Visual Code vì Free và dễ dùng.

# Examples
- Hello World
```
package dev.selenium.hello;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class HelloSelenium {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();

        driver.get("https://selenium.dev");

        driver.quit();
    }
}

```
- Ví dự để mở trình duyệt và tìm từ khóa trên Google
```
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class GoogleSearch {
    public static void main(String[] args) {
        // Khởi tạo đối tượng WebDriver và chỉ định đường dẫn tới ChromeDriver
        System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");
        WebDriver driver = new ChromeDriver();
        
        // Đi tới trang web Google
        driver.get("https://www.google.com");
        
        // Tìm phần tử đầu tiên có tên là "q" (search box) và gửi từ khóa "selenium" vào đó
        WebElement searchBox = driver.findElement(By.name("q"));
        searchBox.sendKeys("selenium");
        
        // Submit form (tương đương với nhấn phím Enter)
        searchBox.submit();
        
        // Chờ cho kết quả hiển thị và đóng trình duyệt
        try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        driver.quit();
    }
}

```

Trong ví dụ trên, đầu tiên chúng ta khởi tạo đối tượng WebDriver và chỉ định đường dẫn tới ChromeDriver. Sau đó, chúng ta mở trang web Google và tìm kiếm từ khóa "selenium" bằng cách tìm phần tử đầu tiên có tên là "q" và gửi từ khóa đó vào đó. Tiếp theo, chúng ta submit form và chờ cho kết quả hiển thị trong vòng 5 giây trước khi đóng trình duyệt.

- Test chức năng đăng nhập trang web
```
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");

        WebDriver driver = new ChromeDriver();

        // Navigate to the website
        driver.get("https://example.com");

        // Locate the login button and click it
        WebElement loginButton = driver.findElement(By.id("login-button"));
        loginButton.click();

        // Enter username and password
        WebElement usernameField = driver.findElement(By.id("username-field"));
        WebElement passwordField = driver.findElement(By.id("password-field"));
        usernameField.sendKeys("myusername");
        passwordField.sendKeys("mypassword");

        // Submit the form
        WebElement submitButton = driver.findElement(By.id("submit-button"));
        submitButton.click();

        // Verify that login was successful
        WebElement welcomeMessage = driver.findElement(By.id("welcome-message"));
        String messageText = welcomeMessage.getText();
        if (messageText.contains("Welcome")) {
            System.out.println("Login successful!");
        } else {
            System.out.println("Login failed!");
        }

        // Close the browser
        driver.quit();
    }
}

```

Trong ví dụ này, chúng ta sử dụng Selenium để tìm các phần tử trên trang web và thực hiện các hành động như nhập liệu và bấm nút để kiểm tra chức năng đăng nhập trang web. Cuối cùng, chúng ta xác minh rằng việc đăng nhập đã thành công bằng cách kiểm tra xem thông báo chào mừng có chứa từ "Welcome" hay không.