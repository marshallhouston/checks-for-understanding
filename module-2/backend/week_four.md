## Week Four Recap

### Instructions
Fork this repository. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

* What is a cookie?  
  A cookie is a way to store data on the browser.  

* What’s the difference between a session and a cookie?  
  A cookie stores data on the client side, whereas a session stores data on the server side.  

* What’s a flash and when do you want to use flashes?  
  A flash is a temporary way to store data between two HTTP requests; we use flash most frequently with messages to tell the client that something has been successfully created/updated or when something is invalid (email/password info).  

* Why do people say “HTTP is stateless”?  
  HTTP is stateless because, by default, data doesn't persist from one HTTP request to another. Each new request/response is entirely separate from previous and future requests/responses.  

* What’s authentication? Explain.  
  Authentication is "are you who you say are?" We use authentication to validate if a user actually is the user they're saying they are.  

* What’s the difference between authentication and authorization?  
  Authorization is about limiting or exposing access to areas in an application based on the user role (example: admin, user, guest); a guest might have much more limited access when compared to a user, and a user has less functionality compared to an admin. For example, an admin might be able to create/delete resources, but a user might only be able to see these resources in an index/show.  

* What’s a before filter?  
  A before filter is one way to determine if someone has proper authorization to access an area in an application; we've defined before_filters in the application controller in order to give controllers that inherit from the application controller access to the filter. Two before filters that we've created are ```current_user``` and ```current_admin?``` The ```current_user``` method checks to see if we have a logged in user, and if we don't, it attempts to find the user in the database. The ```current_admin?``` method will check if the user is an admin.  

* How do we keep track of a user once they’ve logged in?  
  We keep track of a user through the sessions hash.  

* When do you want to namespace a resource? When do you want to nest a resource? What's the differences between those two approaches?  

  When you want to authorize specific users to have access to a resource, namespacing is an option. When namespacing, you may create more functionality on a resource that can only be accessed through the namespaced route.

  Nesting a resource is used when a resource relies directly to another resource; nesting will create paths that link these resources.  

* At a high level, what tools can you use to implement authorization? How would you use them?  

  You can use before_filters that are defined at the application controller level to determine if a current user has access to pages (or to check current admin).

  Anytime someone tried to visit a part of the application that requires a logged in status or admin role, I would require the before filter (a before_action on that method that is a filter).

* What's an enum, and what advantages does it offer? What data type needs to be in your database to use an enum? Where do you declare an enum?

  An enum is a way to use integers in a database column that correspond to a word that has been defined on the model level. For example, with user roles, you could add an enum on the user model specifically for the role column; after specifying the column that the enum corresponds to, you declare the values that the integers in the database relate to.

  ```ruby
    enum role: ["default", "admin", "superadmin"]
  ```

  In this example, 0 in the db refers to "default", 1 to "admin", and 2 to "superadmin".

  Once an enum is defined, you have access to additional methods, such as user.default?, user.admin?, and user.superadmin? These methods are booleans that can allow you to check a user's role for authorization purposes.

* What are some strategies you can use to keep your views DRY?

  Partials can be used to help DRY up the views so that code can be used in many views but only written in one place. To render a partial, use
  ```ruby
  <%= render partial: "location_of_partial" %>
  ```

  The location of the partial is relative to app/views, so you are able to render partials anywhere from the views folder.
