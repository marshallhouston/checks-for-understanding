## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

1. List the five common HTTP verbs and what the purpose is of each verb.  
GET: request a resource for view
POST: create a new resource
PUT: update all of a resource
PATCH: update part of a resource
DELETE: delete a resource  

2. What is Sinatra?  
Sinatra is a application framework.  

4. What is MVC?  
MVC is the interaction pattern that represents the actions an app takes once a request is sent from a client. After the MVC interaction, the server sends a response back to the client.
M represents model, and the model has the following responsibilities:
- query the database to retrieve information
- complete any logic on the data
V represents view, and the view is responsible for rendering the data to be included in the HTTP response.
C represents controller, and the controller has the following responsibilities:
- parse the HTTP request from the client
- communicate with the model so that the model can retrieve the correct data
- receive data from the model and pass it to the view
- receive data from the view and send the HTTP response to the client  

5. Why do we follow conventions when creating our actions/path names in our Sinatra routes?  
We follow ReST (representational state transfer) so that it's easier for others to understand and use our app.  

6. What types of variables are accessible in our view templates without explicitly passing them?  
Global variables (?)  

7. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?  

  ```ruby
  get '/horses' do
    @count = 1
    erb :index local_variables: {name: 'Mr. Ed'}
  end
  ```

8. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?  
See above (very unsure about this one)  

9. What's the purpose of ERB?  
ERB (embedded ruby) allows us to run ruby code inside an HTML document. To render ruby code, we use <%= %>; if we just want to run the code without rendering it to the page, we use <% %>.  

10. Why do I need a development AND test database?  
A development database will have the seeded data for us, and a test database will only have the data that's explicitly loaded in the test setup. The test database will run much quicker because we're using the minimum amount of data for each test.  

11. What is CRUD and why is it important?  
CRUD is the basic action of applications (Create, Read, Update, and Delete). It's important because it describes the essential pieces of functionality of a database app.  

12. What does HTTP stand for?  
Hypertext Transfer Protocol  

13. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?  
<%= %>, <% %>. If the equals operator is included, the return value of the interpolated code will be rendered to the page; otherwise, the code will run without rendering on the page.  

14. What's an ORM?  
An Object Relationship Mapper is the layer that standardizes data types into a specified and usable form. ORMs allow you to take in disparate forms of data and transform it into objects that we can use.

15. What's the most commonly used ORM in ruby (Sinatra & Rails)?  
ActiveRecord  

16. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.  

```ruby
get '/restaurants' do
  @restaurants = Restaurant.all
  erb :index
end
```

```ruby
get '/restaurants/:id' do
  @restaurant = Restaurant.find(params[:id])
  erb :show
end
```

```ruby
get '/restaurants/new' do
  erb :new
end
```

```ruby
get '/restaurants/:id/edit' do
  @restaurant = Restaurant.find(params[:id])
  erb :edit
end
```

```ruby
put '/restaurants/:id/edit' do |id|
  Restaurant.update(params[:id])
  redirect '/restaurants/#{id}'
end
```

```ruby
post '/restaurants/:id/' do |id|
  Restaurant.create(params[:id])
  redirect '/restaurants/#{id}'
end
```

```ruby
delete '/restaurants/:id' do
  Restaurant.delete(params[:id])
  redirect '/restaurants'
end
```

17. What's a migration?  
A migration is a file that lays out the specifics of the database. We've been using the ActiveRecord change method with create_table to create a new table; we then determine the type of data and the column name inside this method.

A migration can also be used to add columns to a specific table. In this case, we would use add_column and then pass three arguments: the name of the database, the name of the column, and the data type in this column.  

18. When you create a migration, does it automatically modify your database?  
It doesn't modify the database until you run rake db:migrate.  

19. How does a model relate to a database?  
The model is the mechanism that is used to query the database; it's the layer of the app that directly interacts with the database and turns the rows into objects; each row of data in a table represents an instance, but we need the model to transform that data in an object.  

20. What is the difference between `#new` and `#create`?  
New makes a new entry, but it doesn't store it in the database. Create will make and save a new entry. New is useful for validation testing.
