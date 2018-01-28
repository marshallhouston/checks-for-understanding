## Week 4 - Module 3

1. What's the difference between `joins` and `includes` in ActiveRecord?  
  -
1. How do we test an internal API (in general)?
  - request tests that hit the endpoint, expect certain methods to be called a certain number of times and return specific objects.
  - A pure request test will not focus on the return values of the methods that are called during the controller action; the return values will be tested at the unit level on model tests.  
1. What are two different ways to customize your `json`?  
  - jBuilder and ActiveModel Serializers.  
1. If the the methods below return collections, what object (class) will they return? What kind of objects will be returned inside of that object?
   * `.find_by_sql`  
   -  "Executes a custom SQL query against your database and returns all the results. The results will be returned as an array with columns requested encapsulated as attributes of the model you call this method from. If you call Product.find_by_sql then the results will be returned in a Product object with the attributes you specified in the SQL query.

   If you call a complicated SQL query which spans multiple tables the columns specified by the SELECT will be attributes of the model, whether or not they are columns of the corresponding table."  http://api.rubyonrails.org/classes/ActiveRecord/Querying.html#method-i-find_by_sql
   - Whatever model object that this method is called on will be the type of object returned. The columns requested in the query will be listed as attributes of this model object.
   * `.connection.execute`  
   - results = ActiveRecord::Base.connection.execute("foo") where "foo" is the SQL query we want to execute. Calling connection on a pool of connections object will allow us to setup a single connection, and then we can execute sql. https://stackoverflow.com/questions/22752777/how-do-you-manually-execute-sql-commands-in-ruby-on-rails-using-nuodb
   -  object in the results is the database_type::result: `#<PG::Result:0x007fc57a4a57d0 status=PGRES_TUPLES_OK ntuples=1 nfields=1 cmd_tuples=1>`
   * `.where`
   -  ActiveRecord collection proxy object where each element is an ActiveRecord record object of the type specifed in the where.
1. What's your process for solving advanced SQL or ActiveRecord lookups?  
  - first, I start by looking at the type of records that I'll need, and I start identifying the columns that will be important to retrieve this data. I diagram the relationships between the objects through foreign_keys and joins tables, and I identify the aggregate functions that will be required to start gathering the data.

  - I like to focus on what type of objects or info that I should end with to make sure I end up with these objects.
  - I'll start building smaller queries and checking the output to make sure it's getting what I want along the way. I'll often puts the SQL to the page and then start up a rails dbconsole to see the data in table format.
