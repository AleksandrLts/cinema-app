# Cinema-app
>The REST API application which supports role based authorization(ADMIN, USER) 
> with password encryption stored in DB. Users can view the information about the movies, 
> cinema halls, movie sessions and book tickets in owns shopping carts. Admins can 
> get customer info, add movies, cinema halls, manage movie sessions.
## Features
* Authentication and registration
* Access to endpoints depend on the role
* Create and find movies
* Create, find and update movie sessions
* Create and find cinema halls
* Find available movie sessions
* Add tickets to the shopping cart
* Get information about shopping cart of the user 
* Get the user's orders history
* Complete an order
## How to run?
* Clone this remote repository to your local repository : <code>git clone [https://github.com/AleksandrLts/cinema-app.git](https://github.com/AleksandrLts/cinema-app.git)</code>; 
* Create the empty <code>cinema-app</code> database;
* Configure the database connection parameters in the <code>resources/db.properties</code> file;
* Build the project using Maven command: <code>mvn clean install</code>;
* Deploy the generated WAR file to servlet container such as Tomcat;
* Complete authentication with provided credentials which already injected into our app:
   * Admin: <code>login</code>: admin@i.ua, <code>password</code>: admin123;
   * Registered user: <code>login</code>: user@i.ua, <code>password</code>: user12345;
* Send requests via Postman service
## Project Structure
* <code>config</code> - classes for Spring configuration
* <code>controller</code> - presentation layer, classes for handling http-requests depend on endpoints
  * List of supported endpoints(permissions):
    * <code>POST: /login</code> - authentication(ALL)
    * <code>POST: /register</code> - register new user(ALL)
    * <code>GET: /cinema-halls</code> - display all cinema halls(USER, ADMIN)
    * <code>POST: /cinema-halls</code> - create a new cinema hall(ADMIN)
    * <code>GET: /movies</code> - display all movies(USER, ADMIN)
    * <code>POST: /movies</code> - create a new movie(ADMIN)
    * <code>GET: /movie-sessions/available</code> - display available movie sessions on a specified date(USER, ADMIN)
    * <code>POST: /movie-sessions</code> - create a new movie session(ADMIN)
    * <code>PUT: /movie-sessions/{id}</code> - update the information about movie session by id(ADMIN)
    * <code>DELETE: /movie-sessions/{id}</code> - delete the movie session by id(ADMIN)
    * <code>PUT: /shopping-carts/movie-sessions</code> - add a new ticket to the user shopping cart(USER)
    * <code>GET: /shopping-carts/by-user</code> - display the user shopping cart(USER)
    * <code>GET: /orders</code> - display all user orders(USER)
    * <code>POST: /orders/complete</code> - complete an order(USER)
    * <code>GET: /users/by-email</code> - get the user by email(ADMIN)
    * <code>GET: /logout</code> - invalidate current session
* <code>dao</code> - Data Access Object are responsible for correct CRUD operations with DB
* <code>lib</code> - contains the custom annotations for email and password validation
* <code>dto</code> - Data Transfer Objects are representing communication objects for customer requests and responses
* <code>exception</code> - contains custom exceptions
* <code>model</code> - Plain Old Java Objects (POJOs) that represent data
* <code>service</code> - logic layer, handling all business logic, includes mapper-s for dto
* <code>util</code> - utility class used to determine DateTime pattern
* <code>resources</code> - contains configuration file with JDBC and Hibernate params
## Used technologies
* JDK <code>17</code>
* Apache Maven <code>4.0.0</code>
* MySQL <code>8.0.22</code>
* Hibernate ORM <code>5.6.14.Final</code>
* Spring <code>5.3.20</code>
* Spring Security <code>5.6.10</code>
* Javax Servlets <code>4.0.1</code>
* Javax Annotations <code>1.3.2</code>
* Apache Tomcat <code>9.0.73</code>
## Made By Oleksandr Lutsenko 