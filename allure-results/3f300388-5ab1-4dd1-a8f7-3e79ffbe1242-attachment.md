# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: DDTUsingExcel.spec.ts >> Add an item to cart ADIDAS ORIGINAL
- Location: tests\DDTUsingExcel.spec.ts:31:5

# Error details

```
Test timeout of 30000ms exceeded.
```

```
Error: page.goto: Test timeout of 30000ms exceeded.
Call log:
  - navigating to "https://rahulshettyacademy.com/client/#/auth/login", waiting until "load"

```

# Page snapshot

```yaml
- generic [ref=e3]:
  - banner [ref=e4]:
    - generic [ref=e5]:
      - generic: Ecom
      - generic [ref=e9]:
        - link " dummywebsite@rahulshettyacademy.com" [ref=e11] [cursor=pointer]:
          - /url: emailto:dummywebsite@rahulshettyacademy.com
          - generic [ref=e12]: 
          - text: dummywebsite@rahulshettyacademy.com
        - generic [ref=e13]:
          - link "" [ref=e14] [cursor=pointer]:
            - /url: "#"
          - link "" [ref=e16] [cursor=pointer]:
            - /url: "#"
          - link "" [ref=e18] [cursor=pointer]:
            - /url: "#"
          - link "" [ref=e20] [cursor=pointer]:
            - /url: "#"
  - generic [ref=e22]:
    - generic [ref=e23]:
      - heading "We Make Your Shopping Simple" [level=3]
      - heading [level=1] [ref=e24]:
        - text: Practice Website for
        - emphasis [ref=e25]: Rahul Shetty Academy
        - text: Students
      - link "Register" [ref=e26] [cursor=pointer]:
        - /url: "#/auth/register"
    - generic [ref=e28]:
      - paragraph [ref=e29]:
        - generic [ref=e30]: Register to sign in with your personal account
      - generic [ref=e31]:
        - heading "Log in" [level=1] [ref=e32]
        - generic [ref=e33]:
          - generic [ref=e34]:
            - generic [ref=e35]: Email
            - textbox "email@example.com" [ref=e36]
          - generic [ref=e37]:
            - generic [ref=e38]: Password
            - textbox "enter your passsword" [ref=e39]
          - button "Login" [ref=e40] [cursor=pointer]
        - link "Forgot password?" [ref=e41] [cursor=pointer]:
          - /url: "#/auth/password-new"
        - paragraph [ref=e42] [cursor=pointer]: Don't have an account? Register here
  - generic [ref=e43]:
    - heading "Why People Choose Us?" [level=1] [ref=e46]
    - generic [ref=e47]:
      - generic [ref=e48]:
        - generic [ref=e49]: 
        - generic [ref=e51]:
          - heading "3546540" [level=1]
          - paragraph [ref=e52]: Successfull Orders
      - generic [ref=e53]:
        - generic [ref=e54]: 
        - generic [ref=e56]:
          - heading "37653" [level=1]
          - paragraph [ref=e57]: Customers
      - generic [ref=e58]:
        - generic [ref=e59]: 
        - generic [ref=e61]:
          - heading "3243" [level=1]
          - paragraph [ref=e62]: Sellers
    - generic [ref=e63]:
      - generic [ref=e64]:
        - generic [ref=e65]: 
        - generic [ref=e67]:
          - heading "4500+" [level=1]
          - paragraph [ref=e68]: Daily Orders
      - generic [ref=e69]:
        - generic [ref=e70]: 
        - generic [ref=e72]:
          - heading "500+" [level=1]
          - paragraph [ref=e73]: Daily New Customer Joining
```

# Test source

```ts
  1  | 
  2  | // this is called as login page class 
  3  | // here all the locator and methods belongs to login page will be written here 
  4  | 
  5  | import { Locator,Page } from "@playwright/test";
  6  | 
  7  | // import - importing file/data from library
  8  | // 
  9  | 
  10 | export class LoginPage {
  11 | 
  12 |     page :Page
  13 |     email: Locator
  14 |     password:Locator
  15 |     loginButton:Locator
  16 |     errorMessage:Locator
  17 |     homePageIdentifier:Locator
  18 | 
  19 | // create the constructor 
  20 | // all locators goes inside the constructor
  21 |     constructor(page:Page){
  22 |         this.page = page
  23 |         this.email = this.page.getByPlaceholder('email@example.com')
  24 |         this.password= this.page.locator('#userPassword')
  25 |         this.loginButton= this.page.locator('#login')
  26 |         this.errorMessage= this.page.locator('#toast-container')
  27 |         this.homePageIdentifier= this.page.locator('[routerlink="/dashboard/"]')
  28 |     }
  29 | 
  30 |     // methods or actions 
  31 |     // any hardcoded value will not be present inside your testclass
  32 |     async launchUrl(url:string){
> 33 |         await this.page.goto(url)
     |                         ^ Error: page.goto: Test timeout of 30000ms exceeded.
  34 |     }
  35 |     async loginIntoApplication(username:string, password:string){
  36 |         await this.email.fill(username)
  37 |         await this.password.fill(password)
  38 |         await this.loginButton.click()
  39 |     }
  40 | 
  41 | }
  42 | 
```