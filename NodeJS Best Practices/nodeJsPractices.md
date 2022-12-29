# Node.JS Best Practices

## Divided Your Solution Into Components
One of the hardest things for larger applications is to maintain a huge code base with tons of dependencies. This slows down production and development while adding new features. According to [Node.js](https://nodejs.org/en/) best practices, we should divide the entire codebase into smaller components so that each module gets its own folder, and certain that each module is kept simple and small.

Like [MVC](https://www.geeksforgeeks.org/mvc-design-pattern/) architecture

<img src="../NodeJS Best Practices/images/Components.png" style=" width:30% ; height:30% " >



## Layering Components

Layering is important and thus each component is designed to have ‘layers’. As a node.js best practices, these layers have a dedicated object that can be used on the web, logic, and data access code. By doing this, it can make a clean separation of performance issues and can significantly differentiate processes from mock and test codes.
Many developers mix the layers by passing the layer objects ([Express](https://expressjs.com/) req, res) to the Service layer and data layers. This makes your application tightly coupled. your app performance is tightly coupled.

## Use ``` npm init ``` for a New Project

```npm init``` will automatically generate a package.json file for your project that shows all the packages/node app of npm install has the information of your project.

```
$ mkdir demo-node app
$ cd demo-node app
$ npm init –yes
 
Now you need to specify an engine’s key with the currently installed version of node (node -v):
 
"engines": {
  "node": "19.2.0"
}

```

## Separate express ‘app’ and ‘server’

The most common mistake that many developers do in any project is to define the entire express application process on  huge files. Instead of doing that, we should separate the ‘[Express](https://expressjs.com/)’ definition into at least two different files. One for the API declaration (app.js) and another one for the network concerns. We can also locate our API declarations within multiple components.
Avoiding Garbage in-app

Node js has a default limit of 1.5 GB Single CPU core  as process manager but still, it uses a greedy and lazy garbage collector. It waits until the memory usage is reached and gets recovered on its own.If you want to gain more control over the garbage collector then we can set the flags on V8.
```
         web: node --optimize_for_size --max_old_space_size=920 --gc_interval=100 server.js
```
You can also otherwise try to run the application using the Docker image. This is important if the app is running in an environment with less than 1.5 GB of available memory usage. For example, if you’d like to tailor a node.js to a 512 MB container, try:
```bash
          web: node --optimize_for_size --max_old_space_size=460 --gc_interval=100 server.js
```
# Error Handling of the App

## Using Async-Await or Promises
Good development practices say to use javascript ‘synchronous function’ for multiple callbacks inside promises to handle async error; this process results in a callback hell problem. We can take a look at the available libraries or async and await of javascript to overcome this performance issue. The process manager will use the promises function to catch code error. It reduces code complexity and makes code more readable.
Code Example –  use promises
```bash
		return A()
		  .then((a) => B(a))
		  .then((b) => C(b))
		  .then((c) => D(c))
		  .catch((error) => logger.error(error))
		  .then(E())
		Code Example - using async/await to catch errors
		async function E() {
		  try {
		    const a= await A();
		    const b= await B(a);
		    const c= await C(c);
		    return await D(c);
		  }
		  catch(error) {
		    logger.error(error);
		  }
```

## Handling Errors Centrally
Every logic that handles errors like logging performance , sending mails regarding error should be written in such a way so that all APIs, night-jobs, unit testing can debug messages and call this method whenever any error occurs.

## Validating Request Body
Developers can use available open-source packages like [Joi](https://joi.dev/api/?v=17.7.0) to ensure the request body is proper and does not contain any malicious content. We can validate all the request parameters and body parameters to meet the expected schema before executing actual logic. By doing so we can throw an error to the user input that the requested body is not valid before executing actual logic.
Code Style Node.js Best Practices

## Use Linting Packages
There are many linting tools available, [ESLint](https://eslint.org/) is one the most popular linting package which is used to check possible errors in code otherwise you can  also check code styles to meet best practices standards. It identifies spacing issues to any potential code patterns that could lead to any security threats as well as possible app-breaking that could occur in the future.
There are also other tools available that automatically format code and put it in a more readable way. Also, it resolves minor syntax errors like adding semicolons at the end of each statement, etc.

## Name Your Functions
You can name all the functions which may include the closures and callbacks. You can restrict the use of anonymous functions. Make sure you use the Naming function. Naming will allow you to simply implement what you want and then Take a snapshot of memory usage.
Proper Naming Conventions for Constants, Variables, Functions, and Classes
As a standard best practice, we should use all constants, functions, variables, and class names in lowercase when we declare them. Also, we should not use any short forms instead use only full forms that are easily understandable by everyone using it. We should use an underscore between two words.
Code Example:

```bash
// for class name we use Uppercase
class MyClassExample {}
// Use the const keyword and lowercase
const conf = {
  key: 'value'
};
// for variables and functions names use lowercase
let variableExample = 'value';
function foo(){}
```

## Use Const Over Let, Do Not Use Var
Const variables assigned cannot be changed, this will help you prevent the use of a single variable multiple times so that way we can keep our code clean. In some scenarios where we need to re-assign variables, we will use the let keyword. For example, in a loop, if we want to re-declare variable value we can use let.
Apart from this, “let variables” have blocked the scope, meaning they are accessible inside of a particular block where they are declared. Variables declared using var can be used anywhere inside the function.
The process manager is a simple command-line interface that keeps the inflow of scripts continuously in all the projects.

## Add Required Modules at the Beginning, Avoid Inside Functions
We should put required modules at the beginning of the and avoid putting them in the middle of the function. By doing this we can easily identify dependencies of the entire file and avoid some of the potential performance issues.

## Use of Strict Equality Operator (===)

Use the strict equality operator === instead of weaker abstract equality operator = ==. == will convert two variables to a common type then compare them while === doesn’t type case variables, and ensures that both variables are of the same type and equal.
Example:
```bash
null == undefined   // true                    
true == 'true'    // false			      
false == undefined  // false		        
'' == '0'           // false			
false == '0'        // true			
0 == '0'            // true			
' \t\r\n ' == 0     // true			
0== ''             // true			
false == null       // false			
 
```
All above statements will return false when === is used.
```bash
null === undefined //false
true === 'true'    // false
false === undefined  // false
'' === '0'           // false
false === '0'        // false
0 === '0'            // false
' \t\r\n ' === 0     // false
0=== ''             // false
false === null       // false

```

## Using Arrow Functions (=>)
The Arrow functions make the code more compact and keep the lexical context of the root function (i.e. this). However, it is a suggestion to use async-await applications to stop the use of functional parameters when they are working with old API’s which can accept promises or callbacks.

# Testing And Overall Quality Practices

## Include 3 Parts in each test name 

**Do**: A test report should tell whether the current application revision satisfies the requirements for the people who are not necessarily familiar with the code: the tester, the DevOps engineer who is deploying and the future you two years from now. This can be achieved best if the tests speak at the requirements level and include 3 parts:
<img src="../NodeJS Best Practices/images/aaa.png" style=" width:30% ; height:30% ">

1. What is being tested? For example, the ProductsService.addNewProduct method
2. Under what circumstances and scenario? For example, no price is passed to the method
3. What is the expected result? For example, the new product is not approved

**Otherwise**: A deployment just failed, a test named “Add product” failed. Does this tell you what exactly is malfunctioning?

Example using [Jest](https://jestjs.io/)

```
//1. unit under test
describe("GET /api/getRoles", () => {
   test("it should get all the roles", async () => {
   // 2. Scenario 
     await supertest(app)
       .get("/api/getRoles")
       .set({ Authorization: `Bearer ${token}` })
       .then((response) => {
	//3. expectation
         expect(response.statusCode).toBe(200);
       })
       .catch((error) => {
         console.log(error);
       });
   });
 });
```

Doing It Right Example: A test name that constitutes 3 parts


## Structure tests by the AAA pattern

Do: Structure your tests with 3 well-separated sections **Arrange, Act & Assert (AAA)**. Following this structure guarantees that the reader spends no brain-CPU on understanding the test plan:

* **1st A - Arrange:** All the setup code to bring the system to the scenario the test aims to simulate. This might include instantiating the unit under test constructor, adding DB records, mocking/stubbing on objects, and any other preparation code
* **2nd A - Act:** Execute the unit under test. Usually 1 line of code
* **3rd A - Assert:** Ensure that the received value satisfies the expectation. Usually 1 line of code

Otherwise: Not only do you spend hours understanding the main code but what should have been the simplest part of the day (testing) stretches your brain

Doing It Right Example: A test structured with the AAA pattern
```

describe("Customer classifier", () => {
  test("When customer spent more than 500$, should be classified as premium", () => {
    //Arrange
    const customerToClassify = { spent: 505, joined: new Date(), id: 1 };
    const DBStub = sinon.stub(dataAccess, "getCustomer").reply({ id: 1, classification: "regular" });

    //Act
    const receivedClassification = customerClassifier.classifyCustomer(customerToClassify);

    //Assert
    expect(receivedClassification).toMatch("premium");
  });
});
```

Anti-Pattern Example: No separation,one bulk,harder to interpret
```

test("Should be classified as premium", () => {
  const customerToClassify = { spent: 505, joined: new Date(), id: 1 };
  const DBStub = sinon.stub(dataAccess, "getCustomer").reply({ id: 1, classification: "regular" });
  const receivedClassification = customerClassifier.classifyCustomer(customerToClassify);
  expect(receivedClassification).toMatch("premium");
});
```


## Describe expectations in a product language: use BDD-style assertions


Do: Coding your tests in a declarative-style allows the reader to get the grab instantly without spending even a single brain-CPU cycle. When you write imperative code that is packed with conditional logic, the reader is forced to exert more brain-CPU cycles. In that case, code the expectation in a human-like language, declarative BDD style using expect or should and not using custom code. If Chai & Jest doesn't include the desired assertion and it’s highly repeatable, consider extending Jest matcher (Jest) or writing a custom Chai plugin.

Otherwise: The team will write less tests and decorate the annoying ones with .skip()


Anti-Pattern Example: The reader must skim through not so short, and imperative code just to get the test story.

```
test("When asking for an admin, ensure only ordered admins in results", () => {
  //assuming we've added here two admins "admin1", "admin2" and "user1"
  const allAdmins = getUsers({ adminOnly: true });

  let admin1Found,
    adming2Found = false;

  allAdmins.forEach(aSingleUser => {
    if (aSingleUser === "user1") {
      assert.notEqual(aSingleUser, "user1", "A user was found and not admin");
    }
    if (aSingleUser === "admin1") {
      admin1Found = true;
    }
    if (aSingleUser === "admin2") {
      admin2Found = true;
    }
  });

  if (!admin1Found || !admin2Found) {
    throw new Error("Not all admins were returned");
  }
});

```


Doing It Right Example: Skimming through the following declarative test is a breeze

```
it("When asking for an admin, ensure only ordered admins in results", () => {
  //assuming we've added here two admins
  const allAdmins = getUsers({ adminOnly: true });

  expect(allAdmins)
    .to.include.ordered.members(["admin1", "admin2"])
    .but.not.include.ordered.members(["user1"]);
});
```

## Don’t catch errors, expect them

Do: When trying to **assert** that some input triggers an error, it might look right to use try-catch-finally and asserts that the catch clause was entered. The result is an awkward and verbose test case (example below) that hides the simple test intent and the result expectations
A more elegant alternative is the using the one-line dedicated Chai assertion: expect(method).to.throw (or in **Jest: expect(method).toThrow()**). It’s absolutely mandatory to also ensure the exception contains a property that tells the error type, otherwise given just a generic error the application won’t be able to do much rather than show a disappointing message to the user.

Otherwise: It will be challenging to infer from the test reports (e.g. CI reports) what went wrong.

**Anti-pattern Example: A long test case that tries to assert the existence of error with try-catch**

```
it("When no product name, it throws error 400", async () => {
  let errorWeExceptFor = null;
  try {
    const result = await addNewProduct({});
  } catch (error) {
    expect(error.code).to.equal("InvalidInput");
    errorWeExceptFor = error;
  }
  expect(errorWeExceptFor).not.to.be.null;
  //if this assertion fails, the tests results/reports will only show
  //that some value is null, there won't be a word about a missing Exception
});
```

**Doing It Right Example: A human-readable expectation that could be understood easily, maybe even by QA or technical PM**

```
it("When no product name, it throws error 400", async () => {
  await expect(addNewProduct({}))
    .to.eventually.throw(AppError)
    .with.property("code", "InvalidInput");
});

```
# Security Best Practices

## Embrace linter security rules

Make use of security-related linter plugins such as [eslint-plugin-security](https://github.com/nodesecurity/eslint-plugin-security) to catch security vulnerabilities and issues as early as possible, preferably while they're being coded. This can help catching security weaknesses like using **eval, invoking a child process or importing a module** with a string literal (e.g. user input).

 What could have been a straightforward security weakness during development becomes a major issue in production. Also, the project may not follow consistent code security practices, leading to vulnerabilities being introduced, or sensitive secrets committed into remote repositories.

Security plugins for **ESLint** and **TSLint** such as [eslint-plugin-security](https://github.com/nodesecurity/eslint-plugin-security) and [tslint-config-security](https://www.npmjs.com/package/tslint-config-security) offer code security checks based on a number of known vulnerabilities, such as unsafe **RegEx**, unsafe use of **eval()**, and non-literal filenames being used when accessing the file system within an application. The use of git hooks such as [pre-git](https://github.com/bahmutov/pre-git) allows to further enforce any rules on source control before they get distributed to remotes, one of which can be to check that no secrets were added to source control.

**eslint-plugin-security example**

**Some examples of unsafe practice rules detected by eslint-plugin-security:**
```
detect-pseudoRandomBytes
const insecure = crypto.pseudoRandomBytes(5);

detect-non-literal-fs-filename
const path = req.body.userinput;
fs.readFile(path);
detect-eval-with-expression
const userinput = req.body.userinput;
eval(userinput);

detect-non-literal-regexp
const unsafe = new RegExp('/(x+x+)+y/)');
```

**Eslint-plugin-security installtion**

1. Install  [eslint-plugin-security](https://www.npmjs.com/package/eslint-plugin-security)
```
npm install --save-dev eslint-plugin-security
```
2. Scan all **vulnerabilities**
```
    npm audit 
```
  <img src="../NodeJS Best Practices/images/audit.png" style=" width:30% ; height:30% ">
  
3. Fix the vulnerability using below command 
```
   npm audit fix --force
   ```
## Limit concurrent requests using a middleware

DOS attacks are very popular and relatively easy to conduct. Implement rate limiting using an external service such as cloud load balancers, cloud firewalls, nginx, [rate-limiter-flexible](https://www.npmjs.com/package/rate-limiter-flexible) package, or (for smaller and less critical apps) a rate-limiting middleware (e.g. [express-rate-limit](https://www.npmjs.com/package/express-rate-limit))

An application could be subject to an attack resulting in a denial of service where real users receive a degraded or unavailable service.

Rate limiting should be implemented in your application to protect a Node.js application from being overwhelmed by **too many requests at the same time**. Rate limiting is a task best performed with a service designed for this task, such as nginx, however it is also possible with [rate-limiter-flexible](https://www.npmjs.com/package/rate-limiter-flexible) package or middleware such as [express-rate-limiter](https://www.npmjs.com/package/express-rate-limit) for Express.js applications.


Code Example : Node.js  app with [rate-limiter-flexible ](https://www.npmjs.com/package/rate-limiter-flexible)

```javascript
const http = require('http');
const redis = require('redis');
const { RateLimiterRedis } = require('rate-limiter-flexible');

const redisClient = redis.createClient({
 enable_offline_queue: false,
});

// Maximum 20 requests per second
const rateLimiter = new RateLimiterRedis({
 storeClient: redisClient,
 points: 20,
 duration: 1,
 blockDuration: 2, // block for 2 seconds if consumed more than 20 points per second
});

http.createServer(async (req, res) => {
  try {
  const rateLimiterRes = await rateLimiter.consume(req.socket.remoteAddress);
  // Some app logic here

  res.writeHead(200);
  res.end();
  } catch {
  res.writeHead(429);
  res.end('Too Many Requests');
  }
})
 .listen(3000);
```

You can find more examples in the [documentation](https://github.com/animir/node-rate-limiter-flexible/wiki/Overall-example).

## Extract secrets from config files or use packages to encrypt them

Never store **plain-text secrets** in configuration files or source code. Instead, make use of secret-management systems like Vault products, Kubernetes/Docker Secrets, or using environment variables. As a last resort, secrets stored in source control must be encrypted and managed (rolling keys, expiring, auditing, etc). Make use of **pre-commit/push hooks** to prevent committing secrets accidentally.

Source control, even for private repositories, can mistakenly be made public, at which point all secrets are exposed. Access to source control for an external party will inadvertently provide access to related systems (databases, apis, services, etc).
The most common and secure way to provide a **Node.js** application access to keys and secrets is to store them using **environment variables** on the system where it is being run. Once set, these can be accessed from the **global process.env object**. A litmus test for whether an app has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials.
For rare situations where secrets do need to be stored inside source control, using a package such as [cryptr ](https://www.npmjs.com/package/cryptr)allows these to be stored in an encrypted form as opposed to in plain text.


Example 

Accessing an API key stored in an environment variable:

```
 const azure = require('azure');

 const apiKey = process.env.AZURE_STORAGE_KEY;
 const blobService = azure.createBlobService(apiKey);
```

Using [cryptr](https://www.npmjs.com/package/cryptr) to store an encrypted secret:
```

const Cryptr = require('cryptr');
const cryptr = new Cryptr(process.env.SECRET);
 
let accessToken = cryptr.decrypt('e74d7c0de21e72aaffc8f2eef2bdb7c1');
 
console.log(accessToken);  // outputs decrypted string which was not stored in source control

```
## Adjust the HTTP response headers for enhanced security

Your application should be using secure headers to prevent attackers from using common attacks like cross-site scripting (XSS), clickjacking and other malicious attacks. These can be configured easily using modules like [helmet](https://www.npmjs.com/package/helmet)

Attackers could perform direct attacks on your application's users, leading to huge security vulnerabilities.


**Install helmet**
```
npm  i helmet
```

Example:
```
const express = require("express");
const helmet = require("helmet");

const app = express();
app.use(helmet()); 

```
Ref :  

[Read on OWASP Secure Headers Project](https://www.owasp.org/index.php/OWASP_Secure_Headers_Project#xfo)

[Node.js Security Checklist (RisingStack)](https://blog.risingstack.com/node-js-security-checklist/)

