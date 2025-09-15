
# Exercise 2: Extending a familiar concept

*Deliverables: Succinct answers to each of the questions with the required additional specification fragments.*

# Questions
1. _Complete the definition of the concept state._

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

    **state**
    a set of Users with 

    &nbsp;a username String

    &nbsp;a password String
    </div>

2. _Write a requires/effects specification for each of the two actions. (Hints: The register action creates and returns a new user. The authenticate action is primarily a guard, and doesn’t mutate the state.)_

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    
    **actions**

    register (username: String, password: String): (user: User)
      
    &nbsp;**requires** no user exists with provided username
    
    &nbsp;**effects** create a new user with this username and password, add to Users set, and return the user

    authenticate (username: String, password: String): (user: User)
    
    &nbsp;**requires** a user exists with this username and password

    &nbsp;**effects** return the matching user with that username


    </div>


3. _What essential invariant must hold on the state? How is it preserved?_
    
    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

    No two users can have the same username which is preserved by `register` action's precondition that requires no user exists with this username before creating a new user. The authenticate action doesn't modify state, so it cannot violate the invariant.
    </div>

4. _One widely used extension of this concept requires that registration be confirmed by email. Extend the concept to include this functionality. (Hints: you should add (1) an extra result variable to the register action that returns a secret token that (via a sync) will be emailed to the user; (2) a new confirm action that takes a username and a secret token and completes the registration; (3) whatever additional state is needed to support this behavior.)_
    
    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

    **states:**

    a set of Users with  
    &nbsp;a username String  
    &nbsp;a password String  
    &nbsp;a confirmed Flag  

    a set of PendingConfirmations with  
    &nbsp;a username String  
    &nbsp;a secretToken String  

    **actions:**  
    register (username: String, password: String): (user: User, token: String)  

    &nbsp;**requires**  
    &nbsp;&nbsp;&nbsp;&nbsp;no user exists with this username  

    &nbsp;**effects**  
    &nbsp;&nbsp;&nbsp;&nbsp;create a new User with this username, password, sets confirmed = false  
    &nbsp;&nbsp;&nbsp;&nbsp;create a new PendingConfirmation with the username and a fresh secretToken  
    &nbsp;&nbsp;&nbsp;&nbsp;return the created User and the secretToken  

    authenticate (username: String, password: String): (user: User)  

    &nbsp;**requires**  
    &nbsp;&nbsp;&nbsp;&nbsp;a confirmed User exists with this username and password  

    &nbsp;**effects**  
    &nbsp;&nbsp;&nbsp;&nbsp;return the matching User  

    confirm (username: String, token: String)  

    &nbsp;**requires**  
    &nbsp;&nbsp;&nbsp;&nbsp;a pending confirmation exists for this username with this token  

    &nbsp;**effects**  
    &nbsp;&nbsp;&nbsp;&nbsp;remove the PendingConfirmation  
    &nbsp;&nbsp;&nbsp;&nbsp;set confirmed = true for the matching User  

</div>



---

<div align="center">
  <a href="./exercise1.md">⬅️ Go to Exercise 1</a>&emsp;&emsp;&emsp;
  <a href="./exercise3.md">➡️ Go to Exercise 3</a>
</div>

<div align="center" style="margin-top: 1em;">
  <a href="../pset1.md">🏠 Go to Pset 1 Table of Contents</a>
</div>