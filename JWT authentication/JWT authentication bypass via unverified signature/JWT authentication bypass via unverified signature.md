
### Scenario 1: JWT Authentication Bypass via Unverified Signature

To begin with the practical side of JWT attacks, I started with PortSwigger’s lab on **JWT authentication bypass via unverified signature**. This lab demonstrates a common implementation flaw where the server accepts JWTs without validating their signature, allowing modified tokens to be trusted. The objective of the lab is to abuse this weakness, gain access to the admin panel

![[Pasted image 20260709011242.png]]

Click on ***Access THE LAB*** to start the lab

login to My account



![[Pasted image 20260709011145.png]]


***login to My account***

![[Pasted image 20260709012007.png]]

![[Pasted image 20260709012109.png]]



![[Pasted image 20260709012401.png]]

We successfully logged in, now let’s refresh the page and intercept it using Burpsuite Interceptor& poxy tab

and request send to repeater

![[Pasted image 20260709013022.png]]

If you observe carefully, every request contains a session token that is sent to the server and the token appears to be in JWT format


There are many tools to decode JWT tokens such as JWT Editor
![[Pasted image 20260709013525.png]]

![[Pasted image 20260709014755.png]]


![[Pasted image 20260709014838.png]]


![[Pasted image 20260709015745.png]]

![[Pasted image 20260709020206.png]]



