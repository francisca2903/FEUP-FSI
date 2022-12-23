# Tarefas para a semana 12 e 13

## Task 1: Becoming a Certificate Authority (CA)

For this task, we want to become a CA so that we can issue a certificate for others. To be able to achieve that, we started by copying the OpenSSL configuration file into our Labsetup folder by doing the following command:

**cp /urs/lib/ssl/openssl.cnf ./openssl.cnf**

What our Labsetup looks like:

![image70.png](images/image70.png)

After that, insid the *openssl.cnf* file, the following content needs to be present:

![image71](images/image71.png)

Afterwards we need to create the *demoCA* folder and add all the necessary files into it, and the we are going to start generating the self-signed CA certificate using the command given previously.

![image72.png](images/image72.png)

We can then do the following commands to look at the decoded content of the X509 certificate and the RSA key as plain text:

**openssl x509 -in ca.crt -text -noout <br>
openssl rsa  -in ca.key -text -noout**

![image73.png](images/image73.png)
![image74.png](images/image74.png)
![image75.png](images/image75.png)
![image76.png](images/image76.png)
![image77.png](images/image77.png)
![image78.png](images/image78.png)
![image79.png](images/image79.png)
![image80.png](images/image80.png)
![image81.png](images/image81.png)

Then we answered some questions:

**What part of the certificate indicates this is a CA’s certificate?**

CA:TRUE

![image82.png](images/image82.png)

**What part of the certificate indicates this is a self-signed certificate?**

Because X509v3 Subject Key Identifier = X509v3 Authoriry Key Identifier

![image83.png](images/image83.png)

**In the RSA algorithm, we have a public exponent e, a private exponent d, a modulus n, and two secret numbers p and q, such that n = pq. Please identify the values for these elements in your certificate and key files.**

The values are shown in the following order: n (modulus), public exponent (publicExponent), d (privateExponent), p (prime1) and q (prime2), as seen in the screenshots above.

## Task 2: Generating a Certificate Request for Your Web Server

We used the following command to generate a request using the new server key:

![image84.png](images/image84.png)
![image85.png](images/image85.png)

## Task 3: Generating a Certificate for your server

The following command turns the certificate signing request (server.csr) into an X509 certificate (server.crt), using the CA’s ca.crt and ca.key:

![image86.png](images/image86.png)

For security reasons, the default setting in *openssl.cnf* doesn't allow the *openssl ca* command to copy the extension field from the reuqest to the final certificate so, to complete this task, we need to enable it. To achieve that we just need to uncomment the line underlined in the following screenshot:

![image87.png](images/image87.png)

Then we just need to use the following command to print out the decoded content of the certificate:

![image88.png](images/image88.png)
![image89.png](images/image89.png)
![image90.png](images/image90.png)

## Task 4: Deploying Certificate in an Apache-Based HTTPS Website

For this task, we started by creating a new directory, *task4*, inside Labsetup, then, inside is a Dockerfile that we called **l08g04_apache_ssl**, the two index files that were previously provided, and a folder *certs*.

![image91.png](images/image91.png)

The **l08g04_apache_ssl.cnf** contains the following:

![image92.png](images/image92.png)

We then changed the *docker-compose* file to contain the build we want.

![image93.png](images/image93.png)

We can then run it inside the container:

![image94.png](images/image94.png)

We then enter the link.

![image95.png](images/image95.png)

## Task 5: Launching a Man-In-The-Middle Attack

For this task, we targeted the website www.example.com. After that, we modified the /etc/hosts file to emulate the result of a DNS cache positioning attack by mapping the hostname to our web server: 10.9.0.80   www.example.com.
After that, when we access www.example.com, we are able to see the page, but with a warning about it's insecurity. This happens because, at this point, we had a CA's certificate does not contain the example website.

![image97.png](images/image97.png)
![image98.png](images/image98.png)

## Task 6: Launching a Man-In-The-Middle Attack with a Compromised CA

For this task, we had to assume that our CA was compromised by an attacker, so that the attacker can generate its own certificates for the website.

First, we need to generate the certificate for our website www.example.com, with the following command:

![image99.png](images/image99.png)

Afterwards we needed to sign our certificate with our CA:

![image100.png](images/image100.png)

After we also needed to add it to the Dockerfile:

![image101.png](images/image101.png)

Then we could rebuild our container and start it, and when loading into the website we obtain the following:

![image102.png](images/image102.png)

# CTF semana 12 e 13

## Desafio 1

First we need to find our enc_flag by doing the following:

![image103.png](images/image103.png)

Then we put together our exploit:

![image104.png](images/image104.png)

And obtain our flag:

![imag105.png](images/image105.png)
