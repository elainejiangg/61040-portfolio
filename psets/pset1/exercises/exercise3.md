
# Exercise 3: Comparing concepts


*Deliverables: a concept specification for PersonalAccessToken and a succinct note about how it differs from PasswordAuthentication and how you might change the GitHub documentation to explain this.*

> ...So what exactly is the difference between the standard PasswordAuthentication concept and the PersonalAccessToken concept? Read the Github page carefully, and write a minimal specification of the PersonalAccessToken concept, paying particular attention to the purposes and operational principle. Now consider how the two concepts differ. Finally, say briefly whether you think the GitHub page could be improved, and if so how....

> Note: consider only “personal access tokens (classic)” and not “fine-grained personal access tokens.”

1. PersonalAccessToken Concept Specification

<div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

**concept:** PersonalAccessTokenAuthentication  
**purpose:** allow authenticated access to a user’s resources using scoped, revocable, and expirable tokens in place of a password for CLI and API use  
**principle:** after a user generates a token, they can authenticate with the same username and token and be treated as that user within the token’s scopes until the token expires or is revoked; a user may hold multiple tokens and revoke any token without changing their password

**states:**

a set of Tokens with  
&nbsp;a user User  
&nbsp;a tokenString String  
&nbsp;a set of scopes  
&nbsp;an expiration Date  
&nbsp;a revoked Flag  

**actions:**  
generate(user: User, scopes: Set, expiration: Date): (token: Token)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;user exists  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;creates a new token tied to the user, scopes, and expiration; revoked = false  

authenticate(username: String, tokenString: String): (user: User)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;a token exists with this tokenString and it is not expired or revoked  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;returns the corresponding user  

revoke(token: Token)  

&nbsp;**requires**  
&nbsp;&nbsp;&nbsp;&nbsp;token exists  

&nbsp;**effects**  
&nbsp;&nbsp;&nbsp;&nbsp;sets revoked = true  

</div>


2. How PersonalAccessToken differs from PasswordAuthentication?

<div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

According to GitHub’s documentation, personal access tokens let a user create multiple credentials, each with its own access limits and expiration. Passwords, by contrast, are a single global credential used for logging in. Tokens are mainly used for scripts or command-line access, and they give more control since they can be deleted or limited without affecting the main account.  
</div>


3. Whether you think the GitHub page could be improved, and if so how?

<div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

Yes, the GitHub page could be clearer. Saying “treat your access tokens like passwords” oversimplifies things and misses the key differences. Tokens are scoped, non-interactive credentials meant for automation and command-line use, not general login. A quick explanation/example of when to use a token versus a password would make the docs would be helpful.
</div>



---

<div align="center">
  <a href="./exercise3.md">⬅️ Go to Exercise 2</a>&emsp;&emsp;&emsp;
  <a href="./exercise4.md">➡️ Go to Exercise 4</a>
</div>

<div align="center" style="margin-top: 1em;">
  <a href="../pset1.md">🏠 Go to Pset 1 Table of Contents</a>
</div>