### Tarefas para as semana 8 e 9 

## Task 1: Get Familiar with SQL Statements

First we need to get control of the MYSQL container and then start MySQL.

![image36.png](images/image36.png)

The querie that gives us access to the employee Alice profile information is: 

SELECT * FROM credential WHERE Name = 'Alice'

image

## Task 2: SQL Injection Attack on SELECT Statement

# Task 2.1: SQL Injection Attack from webpage

For this task, it was asked for us to access the admin account, while only knowing the username. So, for the username field, we put *admin'#* so it can comment the part that had the password variable. By doing this, we were able to see the admin information.

image

# Task 2.2: SQL Injection Attack from command line

For us to complete this task without using the webpage, we did the following in the command line and got the access to see the admin information:

**curl 'www.seed-server.com/unsafe_home.php?username=admin%27%23&Password='**

image

# Task 2.3: Append a new SQL statement

For this task we tried to run two SQL statements foe the attack, but it wasn't possible because of the PHP MYSQLi extension. This extesion doesn't allow the execution of multiple queries.

image

## Task 3: SQL Injection Attack on UPDATE Statement

# Task 3.1: Modify your own salary

To change Alice's salary we first need to log as Alice, by giving the username field the input *alice'#* since we don't know her password. After that we are going to use the edit profile functionality to achieve our task, by putting in the nickname field *', salary='50000* and then we can also change the SQL UPDATE statement to update the salary as well.

image

# Task 3.2: Modify other people’ salary

For this task we need to alter someone else's salary and to do that, we just need to do **', salary=1 WHERE Name='Boby';# ** on the nickname field of Alice's profile.

image

# Task 3.3: Modify other people’ password

The goal of this task is to change Boby's password. We started by hashing a new password *password* .
Then on Boby's edit profile page we do the command ** and sucessfully changed his password.

image

We can now log into his account using our password.

image



