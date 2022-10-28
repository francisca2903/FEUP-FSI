# Tarefa para a semana #7

##Task 1: Crashing the Program

At first we started by sending a *hello* message, and the program sent a *returned properly* message.

After that, the goal of task is to exploit the format-string vulnerability. In this case, we are going to exploit the the *printf()* function as well as the format-string.

In our string, we are going to add *%n* so that when the function *printf()* runs and tries to print the string, it will overwrite the return address to exit the function, which means that our program gets stuck, aka crashing the program. 
This happens because the *%n* in a string loads the variable where the pointer is located and change the value of the variable to the number of characters printed by *printf()* so far.

![image.png](./image.png) 
![image-1.png](./image-1.png)
