# Node.JS Project Structure Best Practices

## Divided your solution into components
One of the hardest things for larger applications is to maintain a huge code base with tons of dependencies. This slows down production and development while adding new features. According to [Node.js](https://nodejs.org/en/) best practices, we should divide the entire codebase into smaller components so that each module gets its own folder, and certain that each module is kept simple and small.

Like [MVC](https://www.geeksforgeeks.org/mvc-design-pattern/) architecture

![alt text](http://url/to/img.png)




## Layering components

Layering is important and thus each component is designed to have ‘layers’. As a node.js best practices, these layers have a dedicated object that can be used on the web, logic, and data access code. By doing this, it can make a clean separation of performance issues and can significantly differentiate processes from mock and test codes.
Many developers mix the layers by passing the layer objects ([Express](https://expressjs.com/) req, res) to the Service layer and data layers. This makes your application tightly coupled. your app performance is tightly coupled.

## Use ``` npm init ```for a new project

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

https://gist.github.com/ASHoKuni/c9f7ae749248070c32da33fa895447e7#file-npm_init_for_a_new_project-txt

## Separate express ‘app’ and ‘server’

The most common mistake that many developers do in any project is to define the entire express application process on  huge files. Instead of doing that, we should separate the ‘[Express](https://expressjs.com/)’ definition into at least two different files. One for the API declaration (app.js) and another one for the network concerns. We can also locate our API declarations within multiple components.
Avoiding Garbage in-app

Node js has a default limit of 1.5 GB Single CPU core  as process manager but still, it uses a greedy and lazy garbage collector. It waits until the memory usage is reached and gets recovered on its own.If you want to gain more control over the garbage collector then we can set the flags on V8.
        
	```bash
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
		```python
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
https://gist.github.com/ASHoKuni/645436461d677c4301b75ee992c4d4b7#file-gistfile1-txt

## Handling Errors Centrally
Every logic that handles errors like logging performance , sending mails regarding error should be written in such a way so that all APIs, night-jobs, unit testing can debug messages and call this method whenever any error occurs.

## Validating Request Body
Developers can use available open-source packages like Joi to ensure the request body is proper and does not contain any malicious content. We can validate all the request parameters and body parameters to meet the expected schema before executing actual logic. By doing so we can throw an error to the user input that the requested body is not valid before executing actual logic.
Code Style Node.js Best Practices

## Use Linting Packages
There are many linting tools available, ESLint is one the most popular linting package which is used to check possible errors in code otherwise you can  also check code styles to meet best practices standards. It identifies spacing issues to any potential code patterns that could lead to any security threats as well as possible app-breaking that could occur in the future.
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
null == undefined   // true                       null === undefined //false
true == 'true'    // false			 true === 'true'    // false
false == undefined  // false		 false === undefined  // false
'' == '0'           // false			 '' === '0'           // false
false == '0'        // true			false === '0'        // false
0 == '0'            // true			0 === '0'            // false
' \t\r\n ' == 0     // true			' \t\r\n ' === 0     // false
0== ''             // true			0=== ''             // false
false == null       // false			false === null       // false
 
```
All above statements will return false when === is used.

## Using Arrow Functions (=>)
The Arrow functions make the code more compact and keep the lexical context of the root function (i.e. this). However, it is a suggestion to use async-await applications to stop the use of functional parameters when they are working with old API’s which can accept promises or callbacks.

