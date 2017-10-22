## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

1. What is the entry at the command line to create a new rails app?  
  ```ruby
    rails new project_name -d postgresql -T --skip-turbolinks --skip-spring
  ```

  -d postgresql sets the database to PostgreSQL instead of SQLite3, -T doesn't use the minitest suite, and the final two skip turbolinks and spring.  

2. What do Models generally inherit from in rails?  
  ApplicationRecord which has inherited from ActiveRecord::Base.  

3. What do Controllers generally inherit from in a rails project?  
  ApplicationController.  

4. How would I create a route if I wanted to see a specific horse in my routes fitle assuming I'm sticking to standard conventions and that I didn't want other CRUD functionality?

  `resources :horses, only: :show`  

5. What rake task is useful when looking at routes, and what information does it give you?  
  rake routes: the information returned from this is a list each prefix, http verb, URI path, and controller#action for each route that has been defined in routes.rb.  

6. What is an example of a route helper? When would you use them?  

  new_horse_path is a helper that corresponds to path /horses/new; the route helper is the prefix from rake routes that is related to the HTTP verb, URI path, and controller#action.  

  I use these when redirecting to a specific page from the create/update/destroy actions for a resource and when using the link helper (link_to) to specify a path.  

7. What's the difference between what `_url` and `_path` return when combined with a routes prefix?  

  (??) `_path` uses the URI, whereas `_url` includes the full locator that could be used to have a link from an external website

8. What are strong params and why are the necessary?  

  strong params are a private method defined in the controller that allows you to only accept the specified information when creating/updating a specific resource; if we didn't have strong params, someone could pass information in the params that didn't correspond to the columns in the database; I imagine that someone could pass malicious information into the application if we didn't have strong params, but I'm not sure how that would work.  

9. What role does `form_for` play in helping us create our forms?  

  `form_for` is a rails helper method creates the appropriate html to render a form to accept information to create or update a resource; it takes an argument that determines which path the form should connect to, and it determines if the form should go to the create or update method on the controller by checking if the resource has persisted.  

10. How does `form_for` know where to submit the user's input?  

  `form_for` checks to see if a resource already exists (persists?), and if it already exists, it submits to the update method on the appropriate controller; if it doesn't exist, it submits the user's input to the create method.

11. Create a form using a `form_for` helper to create a new `Horse`.  

  ```ruby
    <%= form_for @horse do |f| %>

      <%= f.label :name %>
      <%= f.text_field :name %>

      <%= f.submit %>    
    <% end %>
  ```

12. Why do we want to validate our models?

  we want to validate our models in order to make sure that the resource has all the necessary information when we're creating or editing a resource; otherwise, the functionality that we build afterwards may break because we build methods based on certain expectations of that resource.
  
