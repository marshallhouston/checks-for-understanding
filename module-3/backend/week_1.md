## Week One - Module 3

Some of these questions are from this week, some are from previous weeks, and some are new concepts. Try answering without research first. If you are not sure, take a guess but acknowledge that it's a guess (faking an answer in an interview without acknowledging it as a guess is a bad idea). Follow up with the necessary research to understand these concepts. These tend to be common themes during the job hunt and are worth having a solid understanding of.

1. What is `json`, what does it stand for, and why is it important?
`json` is javascript object notation. It's important because it is a standardized way of sharing data between application's that mixes machine readable and human readable language in a memory efficient way.  

1. What kind of object is JSON in Ruby? How do we know it's JSON?
`json` is initially a string in Ruby, but it can be parsed in Ruby to become a hash or an array of hashes. Name-value pairs where the name are strings followed by a colon and then one of the 6 acceptable types of values (numbers-integers and floats, booleans, arrays, null, strings, objects which are hashes in ruby).  

Metadeta may also tell you that it's JSON. Response will have a header with key value pairs that can tell you content-type.

1. What's an API?
Application Programming Interface. It is the interface between a program and an application, and it allows applications to share data with other applications, combine information, and the public methods that other people can use.

1. What's a RESTful API? How does that look in Rails?
A RESTful API follows the expected routes for HTTP verbs, and creating predicable URI routes through namespacing and nesting resources.

1. What is an ORM, what does it stand for, and why is it helpful?
Object Relational Mapping, and it's a way of allowing disparate forms of data to be standardized. An ORM takes records and makes objects out of them, and allows them to be manipulated and have business logic performed on them.

Abstraction above the database level.

1. How do you create a record in the following table in SQL? In Active Record?   
   (Users table with columns first_name, last_name, email, and age)
   insert into users values ('anna', 'boardman', 'anna@gmail.com', 18);
   User.create({first_name: 'anna', last_name: 'boardman', email: 'anna@gmail.com', age: 18})

1. How would you refactor this method?

```
def people_with_brown_hair
  people_with_brown_hair = []

  people.each do |person|
    if person.hair_color == "brown"
      people_with_brown_hair << person
    end
  end

  people_with_brown_hair
end
```

1. Given an array numbers = [1,2,3,4,5], find the sum of the doubles of all the numbers.  
numbers.reduce(0) do |sum, num|
  sum + num * 2
end

numbers.reduce(:+) * 2

numbers.sum * 2

#### Self Assessment  
Rate yourself on the following scale.  
4  I know and understand all these concepts and did not have to look anything up  
3  I know and understand most of these concepts but had to look something up  
2  I am uncertain about some of these concepts and had to look some things up ^^  
1  I am feeling lost about with these concepts and had to look many things up ^^  

^^ Please let an instructor know where you'd like support to catch you up.
