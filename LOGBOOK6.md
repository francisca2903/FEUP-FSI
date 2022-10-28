# Tarefa para a semana #7

##Task 1: Crashing the Program

At first we started by sending a *hello* message, and the program sent a *returned properly* message.

![image-3.png](./image-3.png)

![image-2.png](./image-2.png)

After that, the goal of task is to exploit the format-string vulnerability. In this case, we are going to exploit the the *printf()* function as well as the format-string.

In our string, we are going to add *%n* so that when the function *printf()* runs and tries to print the string, it will overwrite the return address to exit the function, which means that our program gets stuck, aka crashing the program. 
This happens because the *%n* in a string loads the variable where the pointer is located and change the value of the variable to the number of characters printed by *printf()* so far.

![image.png](./image.png) 

![image-1.png](./image-1.png)

## Task 2: Printing Out the Server Program's Memory

### Task 2.A

To help us this exploit, we are using the *%x*, by writing it as needed ultil we reach our string "0xbfffeeee". We figured we needed to inject a total of 63 *%x* by trial and error until we finally reached our string. The *%x* allows unlimited dumping of the memory segment values. 

![image-5.png](./image-5.png)
![image-4.png](./image-4.png)

### Task 2.B

To perform this task, we needed to alter our string to the address of the secret message that the server already provides us (0x080b4008). Then, we do part of what we already did in the previous task, use the *%x* to jump through the memory and we also execute a *%s* to print the string.
By executing our build_string.py, we see that the secret message was "A secret message".

![image-7.png](./image-7.png)
![image-6.png](./image-6.png)

