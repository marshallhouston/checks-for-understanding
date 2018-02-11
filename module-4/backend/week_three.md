## Week Three - Module 4 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR.

1. At a high level, what is Node?  

  At a high level, Node is program that allows JavaScript to be written and run from the command line. It is built using Chrome's v8 engine. Prior to Node, JavaScript could only be run in the browser.

2. What is Express? What is Express similar to in the Ruby world?  

  Express is a lightweight application framework used to create JavaScript apps. It is comparable to Sinatra in the Ruby world because of it's lightweight nature and lack of opinion in how the application is structured.  

3. How do we setup a route when creating an API with Node and Express? Please provide a code snippet.

  In app.js, we can import a route file and then tell the app which file to use for specific endpoints. It is not necessary to separate routes into different files, but it does improve organization.

  Consider a resource `books` with a routes file /routes/books.js.
    ```js
      var books = require('./routes/books')
      app.use('/books', books)
    ```

  Anytime the application receives a request to `/books`, it will look in the books route file. We'll add the route handling inside the `/routes/books.js` file.

  ```js
    var express = require('express')
    var router = express.Router()

    router.get('/', (req, res, next) => {
      // code to get all Foods.
    })
  ```

  Now the application can handle a GET request to the books endpoint, and we can add additional handling to return the specified resources.  

4. What do we use Knex for?  

  We use Knex to interact with the database to create and run migrations, write queries to retrieve records, and perform any other database operations.  

  Knex has built in functions to query the database, but you can also write raw SQL.

5. How **could** you organize your code to follow the MVC design pattern in your Quantified Self project?  

  Following the MVC model in an express app would require creating directories for routes, controllers, and models.

  The routes file would make a call to a controller action, and then the controller action would make calls to the model. With this organization, the model is the only layer that interacts directly with the database.  

6. How do you execute raw SQL in node?  

  Assuming that a database variable has been set at the top of the file, you can use Knex's `raw` function to write the SQL query.

  ```js
    return database.raw('SELECT * FROM foods;')
    .then(foods => {
      return foods.rows
    })
  ```

7. What are some advantages to having your front end and back end code live in separate applications? What are some disadvantages?  

  Some advantages to separating the front-end and back-end are increased modularity so that changes in a specific application does not affect the other application. The interaction is limited to the API endpoints. With a separate backend application, other applications could use the endpoints to fetch data.

  A disadvantage to separating the applications is handling CORS requests, which means that a server has received a request from a different origin.  

#### Review  

8. Describe DNS.  

  ?? Not confident in this answer at all, so this is without any additional research. ??  

  DNS represents `Domain Name Service`, and it is used to connect a URL with a specific IP address to make visiting websites more human readable. At a high level, it is similar to a phonebook. When a client makes a request, the DNS looks up the URL to connect it to an IP address, and then routes the request to that specific IP address. Once the response is sent, the DNS then routes it to the client.

9. What does writing clean code mean to you?  

  Writing clean code means that there is a clear structure to directories/files that group related functionality. It also means writing methods and functions that focused on SRP to make them modular and reusable. It also means being consistent in syntax, indentation, and naming.  

10. If you were building an application that models hotels, what classes would you need? What classes would be responsible for what functionality? Hint: think about what tables you would need in the database, how those records would relate to each other, and good OOP.  

  I would setup the following tables: hotels (id, name, address), employees (id, name, hotel_id), rooms (id, room_number, hotel_id, price, type), guests (id, name, phone_number, email), and guest_rooms (joins between rooms and guests with id, guest_id, room_id, and occupied_status).

  Each of these tables would have a separate classes to break out the functionality. A hotel would have many rooms and many employees, and a guest could book a room at a hotel that creates a new record in the guest_rooms table and sets the occupied_status to true. Once a guest checks out, the occupied_status on the specific row would be set to false.

  If we wanted to make it more flexible, occupied_status could be an enum with 0 representing not booked, 1 representing reserved, and 2 represented currently occupied.
