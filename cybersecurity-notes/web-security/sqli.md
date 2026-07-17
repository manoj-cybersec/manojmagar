# SQL Injection
Sql injection is a vulnerability that allows an attacker to inject malicious sql query to the input field of the application which is requesting to database of the application. By which attacker can see and retrieve all the data from the database.


## How to detect SQLI


* The single quote character ' and look for errors or other anomalies.
* Some SQL-specific syntax that evaluates to the base (original) value of the entry point, and to a different value, and look for systematic differences in the application responses.
* Boolean conditions such as OR 1=1 and OR 1=2, and look for differences in the application's responses.
* Payloads designed to trigger time delays when executed within a SQL query, and look for differences in the time taken to respond.
* OAST payloads designed to trigger an out-of-band network interaction when executed within a SQL query, and monitor any resulting interactions.
