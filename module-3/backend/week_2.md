## Week Two - Module 3

Some of these questions are from this week, some are from previous weeks, and some are new concepts. Try answering without research first. If you are not sure, take a guess but acknowledge that it's a guess (faking an answer in an interview without acknowledging it as a guess is a bad idea). Follow up with the necessary research to understand these concepts. These tend to be common themes during the job hunt and are worth having a solid understanding of.

1. What's OAuth?  
  Handshake between a user and a 3rd party to verify and authenticate that a user is who they say they are. You will typically receive a code to then send to the callback that will then give you a token that is specific to that user.

1. What are some advantages/disadvantages of implementing OAuth?  
  Pros: a lot simpler and more secure than handrolling your own authentication system. It is using a service that may have more resources than you're able to commit to the authentication.   
  Cons: If that service goes down, logging into your application won't work. You don't have control over the data that is returned, and if it changes the data that you receive and your app requires that information, your application may go down/break/lose users.  
1. What are the four pillars of object oriented design? How do they apply when creating:  
  Four pillars of object oriented design (OOP)
    - Abstraction: logic is abstracted away based on functionality, single responsibility principles that the logic for an object only does that logic.... BUT WHY DOES THIS MATTER?  
    - Encapsulation: joined together with abstraction in that you only expose small parts of the object and all other logic is contained within the logical compartments of the object themselves. A method may receive data, and then call 3 or 4 methods within that one method, but only the initial one is exposed. It makes your application more maintainable/scalable.  
    - Inheritance: gains methods and logic from the base class. inherit the methods and the logic from the base class. inherit from one class, but inheritance chains together so that when you inherit from a class, you gain access to any classes it has inherited from.  
    - Polymorphism: many different classes may have the same method names that are unique or specific to that object. You may also have many different objects that are from the same blueprint but they have the. Vehicle is the original form and consistent, but then you can create subclasses CAR/TRUCK/MOTORCYCLE/BOAT/BICYCLE. You don't affect the original class, the only thing that is changing.  
  * services?
    - Interfacing with an API: it is the point of contact and the bridge between an external api. ask (request) and then response()
    - breaking out pieces into clearly defined purposes: what is the purpose of this class? It should only have code directly related to the function of the class. It isn't a swiss army knife that can do many different pieces.
    - Sends a request to a specific area and then passes this information to another object that is responsible for the creation of the object.
  * PORO's with the data received from an API?
    - object that is domain/app specific, it has data and information specific to your application. Put the data into something that is coherent and allows your
1. What do we use VCR for? Why is it a good idea to use this tool?  
  - VCR is used to save external API requests in order to replay them for testing purposes; it's beneficial because it uses real requests and responses, so you can easily see if the application is handling responses as expected. It's a good idea to use this tool to simulate making API calls instead of hitting APIs every time the test suite is run.
  - Over time, you may need to update the cassettes to ensure that there haven't been changes to the APIs that would make the application fail. Also, if the cassette is made with a failure, this failure will be used in subsequent tests, so you'll have to delete the cassette and save a successful request and response cycle.

1. What does HTTP stand for?  
  - Hyper Text Transfer Protocol. This is the standardized format for submitting requests from a client to a server that includes the HTTP verb, HTTP version, URI (path), and any additional headers (content type, api keys, etc). It may also include a body, but it is not required in the request.
  - The response includes the HTTP version, status code (200 is good, 300 is redirect, 400 is not found - you fucked up as a user, and 500 are a server side error). It also includes headers with content length, date, and other metadata. The response body will include the html, json, xml, or other formatted data.
1. What class does `ApplicationController` inherit from when creating a Rails project with the `--api` flag? What about without the `--api` flag?
  - The `ApplicationController` inherits from ActionController::Base without the --api flag. With the --api flag, it inherits from ActionController::API.

  * What is `protects_from_forgery`?  
   - protects from attacks, something with csrf tokens.
   - malicious folks could use these tokens for other purposes.  

   * What do you need to do differently for your API to accept non-GET requests if you did not use the --api flag?
   - "It could be that you need to set the correct headers before making your post request, in order for rails controller to accept a json response." https://stackoverflow.com/questions/33974142/rails-controller-accept-json-post-request
        ```ruby
        Content-Type: application/json
        Accept: application/json
        ```
    - "If you're writing a web service application, you might find yourself more comfortable accepting parameters in JSON format. If the "Content-Type" header of your request is set to 'application/json', Rails will automatically load your parameters into the params hash, which you can access as you would normally." http://edgeguides.rubyonrails.org/action_controller_overview.html#json-parameters
1. How do you create the following table in SQL? In Active Record?   
   (Users table with columns first_name, last_name, email, and age)   
   ```SQL
   create table users (first_name varchar(64), last_name varchar(64), email varchar(64), age int);
   ```
   ```ruby
   def change
     create_table users do |t|
       t.string first_name
       t.string last_name
       t.string email
       t.integer age
       t.timestamps
     end
   end
   ```
1. What does `inject` do? How should you use it?
  - `inject` is similar to reduce in that it's an aggregate function and allows you to take a starting value, iterate through a collection and perform an operation on each element in the collection and add it to the starting value to find a cumulative output.  
  - from the docs, `Combines all elements of enum by applying a binary operation` and if an initial value is not supplied, the first binary in the collection is used as the starting value.

#### Self Assessment  
Rate yourself on the following scale.  
4 I know and understand all these concepts and did not have to look anything up  
3 I know and understand most of these concepts but had to look something up  
2 I am uncertain about some of these concepts and had to look some things up ^^  
1 I am feeling lost about with these concepts and had to look many things up ^^  

^^ Please let an instructor know where you'd like support to catch you up.
