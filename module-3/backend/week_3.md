## Week Two - Module 3 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

1. What is Multitenancy how does it add value as a multitenancy provider?  
  - multitenancy is the idea that there are multiple stores or tenants in a platform that serves as an aggregate of the individual tenants. As a user, you could shop at many of these different stores and checkout once, and depending on how the app is set up, orders will be created for each of the tenants.

2. How might multitenancy impact your routes/controllers?  
  - the routes for an individual stores might be namespaced so that a user can visit a single store and see an index of all items for that specific store. You might have a stores/items#index and stores/items#show to view items that are tied specifically to the store.  
3. What is a strategy for authorization when dealing with multitenancy?  
  - one strategy for authorization is utilizing a permissions service that would determine a user's access to various areas on the site depending on the user role (registered user, store manager, store admin, platform admin). Each of these roles would be given access to certain controllers and actions with an `authorize!` method that is defined at the application controller that sends the current_user information to the PermissionsService to send a true/false response.  
4. What are some strategies you can use to abide by the one instance variable per controller action rule?  
  - some strategies include presenters or decorators that would send a collection to the view and then call methods on the collection in the view.  

#### Review  

7. What is a callback? How many of them can you list?  
  - a callback is a certain method that is called at a certain point in time in the creation or updating of a resource.
  "created, saved, updated, deleted, validated, or loaded from the database"
  - before_save, after_save, before_validation, after_validation, before_action, after_action  
8. How do you create a Database named Turing in raw SQL and in a Rails environment?  
  ```SQL
  CREATE DATABASE Turing;
  ```
  ```rails
    rake db:create
  ```
9. What does a Ruby Class inherit from?
  - unless explicitly stated at the top of the class through inheritance, a class inherits from Module.  

#### Self Assessment  
Rate yourself on the following scale.  
4 I know and understand all these concepts and did not have to look anything up  
3 I know and understand most of these concepts but had to look something up  
2 I am uncertain about some of these concepts and had to look some things up ^^  
1 I am feeling lost about with these concepts and had to look many things up ^^  

^^ Please let an instructor know where you'd like support to catch you up.
