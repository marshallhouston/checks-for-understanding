## Week Two - Module 4 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR.

1. What's one difference between ES5 and ES6?  

  One difference between ES5 and ES6 is the introduction of  `const` and `let` in ES6. ES5 only had `var` when assigning variables. `const` represents constant that can be assigned to a function or a value, and it is used when something should not change in runtime. `let` allows for block scoping.  

2. What's the difference between asynchronous and synchronous JavaScript?  

  Synchronous runs in a single thread, where each function must wait on the prior function to finish executing before it is executed. Asynchronous JavaScript utilizes the event loop and event queue to run functions once the stack is cleared. For example, a function may be called initially that gets added to the event queue, and then the code after this function gets executed without having to wait for the initial function to complete.  

3. What are the four pillars of Object Oriented programming?  

  - Abstraction: this pillar focuses on using code to represent real-world ideas/objects that have behaviors (properties) and state (current values of the characteristics).

  - Encapsulation: this pillar focuses on breaking down behaviors into smaller methods and only publicly exposing a larger method that is made up of the smaller, encapsulated methods. It also focuses on the idea that the behaviors of an object are defined/contained within it.

  - Polymorphism: this pillar means that the same method name can be used by different objects that have this method defined according to the specifics of the object. For example, both a `car` and `bike` object might have a `tires` method that is calculated differently but uses the same method name.  

  - Inheritance: this pillar allows behaviors to be defined on a parent class and then a child class gets access to these methods. An object can only inherit from a single class, but an object has access to all the methods of its parent and anything that the parent has inherited from (ancestors).

4. What are some tools available in JavaScript to help you write object oriented code?  

  For OOP with JavaScript, classes can be a form of encapsulation for related behaviors and represent abstraction of a real world object. We can also extend classes so that behaviors can be shared.

5. What are some key concepts to be aware of when refactoring your JavaScript?  

  As I'm refactoring in JavaScript, I think about it from low-level refactors to higher-level refactors. On the lower end, I look at specificity in naming, consistency in function declaration (function name() {} vs name = () => {}), and semicolon usage. On the higher-level, I look at decoupling methods to ensure modularity and single responsibility principle to allow reusability.  

6. What's a callback function and what are some reasons when we use/need callback functions?  

  A callback function is a function that will be run once the prior function finishes executing; it is a key aspect to the asynchronicity of JavaScript that allows a program to continue to execute code and then run the next pieces of code within the callback function once the stack is empty.  

7. What are the different scopes of variables in Javascript? When would you want to define global variables?  

  JavaScript scoping includes global, local, and block scope (ES6). A globally scoped variable is accessible throughout the entire program, a locally scoped variable is accessible throughout the function, and a block scoped variable is available within the specific block (through `let` in ES6).  

8. What's the difference between `==` and `===` in JavaScript?  
  `==` represents loose equality and `===` represents strict equality. With loose equality, JavaScript will attempt type coercion, and `1 == "1"` evaluates to true, even though these are different types. With strict equality, `1 === "1" ` evaluates to false because these are of different types.  

9. Why do front end frameworks exist?  
  Front end frameworks exist to provide additional functionality for developers so that they don't have to write only in vanilla JavaScript, HTML, and CSS.  

#### Review  

10. Why do people say "HTTP is stateless"?  
  People say HTTP is stateless because each request/response cycle is independent, which means that it doesn't hold information about previous requests or future requests. However, there are ways to save information (cookies on the client-side, sessions on the server-side) that can be used in conjunction with the HTTP request/response cycle.  

11. Describe a RESTful API.
  A RESTful API follows specific conventions with HTTP verbs and URI paths for accessing resources. Imagine a resource called `players`.
    - GET to /players will return a collection of all players
    - GET to /players/:player_id will return a single player resource
    - PUT/PATCH to /players/:player_id updates this single player resource with the information sent in the body of the request.
    - POST to /players will create a new player resource
    - DELETE to /players/:player_id will delete a single player

  RESTful APIs are used so that other developers can use an API and have it respond in expected ways. There are other ways to build APIs that follow different conventions.  

12. What are some main characteristics of a team following an agile workflow?  
  When a team uses agile, they typically focus on sprints (1-2 weeks) that are focused on building a subset of features in order to get customer feedback and then implement that feedback on the upcoming features. Agile is focused on MVP, minimally viable product, and using client feedback throughout the entire product cycle.  

  Within a sprint, the team frequently has standup meetings where teammates update each other on progress they've made and any blockers they're facing. Agile teams will also use a project management tool to break down features into smaller pieces that need to be completed in this sprint. At the end of the sprint, teams will retro to reflect on the development process and improving the team/product moving forward.  

13. What are some advantages **and** disadvantages to using OAuth to authenticate a user?  

  Using OAuth is advantageous because it gives you peace of mind that an organization with significant engineering teams (GitHub, Google, Twitter, Facebook, etc) has focused on the security of login and has a proven track record of uptime on servers. Users may also trust those companies more than your own handrolled login system.  

  However, a disadvantage is that you have limited flexibility to deviate from what the OAuth provider says. If their terms of service change and provide different information that before, you have to update your authentication system to handle these changes. You also run the risk that these companies have an outage that impacts a user's ability to log into your application.
