# SQL Injection
Sql injection is a vulnerability that allows an attacker to inject malicious sql query to the input field of the application which is requesting to database of the application. By which attacker can see and retrieve all the data from the database.


## How to detect SQLI


* Putting single quote character ' in the input field and look for syntax error.
* Boolean conditions such as OR 1=1 and OR 1=2, and look for differences in the application's responses.
* Payloads designed to trigger time delays when executed within a SQL query, and look for differences in the time taken to respond.
* OAST payloads designed to trigger an out-of-band network interaction when executed within a SQL query, and monitor any resulting interactions.


## Exploitation ( Step by Step )

### Finding number of columns

In this example, I will take the reference of portswigger labs. 

* For this portswigger lab the query is ending by this query " ?category=Accessories ".
* We will just put ' ORDER BY 10 -- .  { Explaination Order by will determine the number of columns should be same and will rearrange if it is not then it will generation an error. -- This will comment out the rest of the part the Application's SQL query.
<img width="670" height="304" alt="image" src="https://github.com/user-attachments/assets/4d2b356e-215a-47b3-bc1a-fe35b4fa444c" />
