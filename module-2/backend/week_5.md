1. How do we make flash messages display on a page?  

  To make a flash message on the page, we first have to set the message in the controller action that will redirect to the page that shows up.  

  In order to set the flash message, we use the flash hash and specify a key value pairing.  

  ```flash[:success] = "Successful login!"```  

  Then, we render the message on the page by including the following block of code in the application_html.rb document.  

  ```ruby
  <% flash.each do |type, message| %>
  <%= message %>
  <% end %>
  ```

2. Where is cart information/temporary information usually stored?  
  Typically, we'll create a PORO cart that is initialized with the information stored in the sessions hash; we can define ```session[:cart]``` to represent the item's id and quantity.  

3. What might be some reasons not to store cart in our database? Are there any reasons why we would want to persist that information?  

  We wouldn't want to store the cart info in our database because a cart might be updated frequently while a user is deciding what to order; we don't actually need the information of what a user adds or deletes from a cart. We would only be concerned with storing information for the actual order.  

  Though we don't want to store the cart information in the database, we would want a user's cart information to persist between pages so that a user doesn't have to re-add selected information to the cart every time they change pages.  

4. What is the purpose of the asset pipeline?  
The purpose of the asset pipeline is to minify and compile the stylesheets, javascript, and images necessary for an application.  

5. Why do we precompile our assets?
We precompile assets to increase loading times on the app; though we might have multiple stylesheets to make stylesheets easier to understand for developers, a machine doesn't need the separate stylesheets. It can read a minified version of the stylesheets, so we precompile them.  

6. What do each of the following tags do?

  ```ruby
  <%= stylesheet_link_tag "application" %>
  <%= javascript_include_tag "application" %>
  <%= image_tag "rails.png" %>
  ```  

  The stylesheet_link_tag tells the path for the stylesheets in the application.  
  The javascript_include_tag tells the path for the javascript files in the application.
  The image_tag tells the path of the image.  

  All of these tags are rails helpers that will then create the appropriate html structure to be rendered on the page.  

7. What are some of the elements of a great read me? What are some of the benefits of taking the time to update a readme for our project?  

  A great readme will include all the information necessary for someone to get your application up and running in less than 10 minutes; it also clearly states any dependencies and common errors.  

  Updating a readme can help lower the barriers of entry to actually using your application; developers and users will be more likely to give your application a go and possibly recommend your application to others!  

8. What are the top four accessibility issues that we as developers should be aware of?  

  As developers, we should consider the navigability of our site for users who may have cognitive disabilities or use a keyboard only on our site; we should consider how a screenreader will work on a site for users who have a vision disability. We should also consider users who are color blind and if our color schemes are high contrast.

9. `before_save` is an example of a what? Where in our Rails application would we find a `before_save`?

  `before_save` is an example of a callback; we specify a method that should be called before saving a record to the database. We've used a `before_save` when generating slugs to save in our database.  

10. Given the following object, how would we create a scope for all users who are active?

```ruby
User.create(name: "Happy", active: true)
```

  ???

11. What is the difference between a scope and a class method?
  ???
