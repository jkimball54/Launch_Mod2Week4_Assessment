# Week 4 Assessment

### Setup
* Fork this repository
* You may make edits directly in github
* For the Exercise section, you will want to be logged in to [replit](https://replit.com)

## Questions (8 points possible)
1. In your own words, how would you define an ORM?
        ORM - Object Relational Mapping. It is the generic term for a framework that connects an OOP language to a database. In the case of C# it is entity framework. This allows you to do CRUD operations in C# and have those be automatically transferred to sql queries.
2. Given the two classes for bike and owner, update the classes to include a one-to-many relationship where each bike has one owner, and each owner can have many bikes.

    ```C#
    namespace BikeApp
    {
        public class Bike
        {
            public int Id { get; set; }
            public string Type { get; set; }
            public DateTime PurchaseDate { get; set; }
            public Owner Owner {get; set;}
        }
    }

    namespace BikeApp
    {
        public class Owner
        {
            public int Id { get; set; }
            public string Name { get; set; }
            public int Zipcode { get; set; }
            public List<Bike> bikes {get; set;} = new List<Bike>();
        }
    }
    ```

3. When adding a new pizza table to our database, which of the following two commands would we run first? Why is it important to run these two line in that order?
        add-migration is done first, it is similar to a commit in that it will save the local changes we have made, it also allows the framework to cross reference the older migrations and make note of what is new in the most recent migration. Afterwards we run update-database to push that change to our database.
    ```
    add-migration AddPizzaTable
    ```
    ```
    update-database
    ```

4. For all three parts of this question, imagine that you have used Entity Framework to create a database table using the following class and context. 
    * What will the table name be?
        bike
    * What will the column name(s) be?
        id, type, date
    * What is the name of the database you are connecting to?
        Bikes

    ```C#
    namespace BikeApp
    {
        public class Bike
        {
            public int Id { get; set; }
            public string Type { get; set; }
            public DateTime Date { get; set; }
        }
    }

    namespace BikeApp
    {
        public class BikeContext : DbContext
        {
            public DbSet<Bike> Bikes { get; set; }
            protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder) => optionsBuilder.UseNpgsql("Host=localhost;Username=postgres;Password=password123;Database=Bikes").UseSnakeCaseNamingConvention();
        }
    }
    ```

5. What type of data does the `Contains` LINQ method return?
    c. Boolean
    <br> a. String 
    <br> b. Integer 
    <br> c. Boolean

## Exercise (5 points possible)

Fork the Replit below, and complete the 5 LINQ exercises.  Add a link to your forked repl here: <YOUR LINK HERE>

[https://replit.com/@launch-team/Mod2Week4Assessment](https://replit.com/@launch-team/Mod2Week4Assessment?v=1)

### Submission
* Submit a link to your forked repository in the Submission form provided in your slack channel.

## Rubric

This assessment has a total of 13 points possible.  A score of **9** or higher is a pass.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
