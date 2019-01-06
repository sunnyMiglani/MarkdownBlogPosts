# System's Security

4th year MEng University of Bristol module

Author: Sunny Miglani

**Module description**:
Basically the course is structured to not depend 100% on slides for the exam.
"Anything in security in the world can be asked" (lol)

# Lecture 1 (Intro - 2nd Oct):
How would you define a system?
It's a collection of components, with relationship and connections to achieve a goal in an environment.

Imagine a system, and think of the different components that are required.

For example, thinking of a server for a website, we consider
Hardware:
- Electricity and redundant servers
- Hardware connections to the internet
- Failsafes + notifications incase it goes down

Software:
- Montiored and secure internet connection
- encrypted communication
- authorised access
- user / admin identification
- known attacks (DDoS, SQL etc)

and many more?

Emerging behaviour in security comes from the idea that **a system is more than the sum of it's parts**

Think about how systems integrate, think about testing possible faults and vulnerabilities.

Components may be secure together, but will they be secure alone? And is there the "weakest link in a chain" effect for the systems?

### Example of a System and a fault
Emails are a common system.

People who designed/used the system thought email passwords should be enough to keep them secure and restrict access

People instead started resetting the passwords by answering security questions they obtained through phishing. (**Especially in an era where everyone has things online and public**)


Now a more specific example is how different systems while secure alone might cause horrible problems when mixed with other systems.

For example, gmail password reset going to apple's password reset email. Apple's reset required 4 digits of a credit card.
Now amazon would let you reset an account, and only asks for your credit card number as a verification tool. However, displays the last 4 digits to the user.
This meant that the attacker could take over the apple's acc without needing to hack into amazon
which meant the attacker could now attack google and therefore obtain the information he needed in the first place.

Goes into the ideas that the people didn't think in terms of combined results, but individually secure.


### 2 Factor authentication problems:

Great to secure things if objects are independent of each other.

If you look into the principles of security, i.e. 
1. Things you know (password, PINs)
2. things you are (fingerprint, iris, voice etc)
3. things you have (phones, bank pin consoles etc)

Now there was an idea that secure systems should use atleast 2 of the above three, and aim for all three.

Good example of it, is **two factor authentication**
Which has problems such as:
1. What if the user is in a situation where they cannot access the secondary device (look at the A in the C,I,A principles of security)
2. What if the device is insecure in itself (email notifications being open/clear on lock screen)
3. What if you can fake 2 factor authentication, because people might believe they've logged into the correct website and they get an SMS confirming a code. This false security could make them feel comfortable to give away sensitive information (passwords, bank deets etc) into a website.

# Lecture 2 (Safety 5th Oct)

Terminology:
1. Accident: unplanned and undesired event
2. Hazard: Condition that can lead to an accident in an environment
3. Incident: Things that happen but isn't an accident
4. Safety: Freedom from accident (caused without intent)
5. Security: Freedome from incidents (caused maliciously)


People say security "incident", not really "accident"

### Safety Measures:
In order of effectiveness, these are how you make something _safe_
1. Mitigate: reduce damage that might happen in an accident
2. Control the environment or control the system
3. Reduce likelihood of the occurence
4. Eliminate the hazard that might cause the accident

Types of safety measures:
1. **Passive**: Presence contributes to saftey, like building fences around train tracks
2. **Fail-safes**: Systems that if they fail, reach a safe state like trains stopping on open doors etc
3. **Active safety measures**: montior systems and intervine like putting off a fire on a train if it starts.

### Risk
Risk is defined as loss X probability of occurance
- First reduce the probability
- Then reduce the loss

There's an industry defined **ALARP**: As low as reasonably practical.

This means reduce down the chances of an occurance as much as possible, but it should still be usable and cost effective as a solution.

Digging deeper into the idea of **cost effectiveness**:
If we look at the idea that it might cost a company £100,000 pounds to add as security layer, but if it was exposed it would only cost the company £10,000 to fix / pay the fines/users then a company would rather do the £10,000.

This has been slowly changing because of new regulations about privacy. For example GDPR, where the government forces companies to pay a fine of upto 4% of the GLOBAL turnover if there is a fault, making that £10,000 rise upto £100,000+ really quickly depending on the scale of the company.

Not to mention with social media and people's views on privacy and generally security, even the presence of a data leak or the news of it could bring down the opinion of everyone of a company giving a more long term loss to the brand and system (e.g yahoo)



### Security 
It's what a system does to protect the Confidentiality, Integrity and Availablity of an automated system.

| Safety | Security |
|---|---|
|Hazard|vulnerability|
|?|threat|
|safety measure|countermeasure|
|risk|risk|
|accidents/incidents|incidents|

### Definition of an Attack

It's the realisation of a threat

And it's a sequence of actions that result in a loss

> {threatAgents} -> {threats} -> {vulnerabilities} -> {attack}

> hackers -> SQL Injections -> Login Form's code -> Deface the website 

### Countermeasures

1. Prevent first
2. Detect Next
3. Recover third

You can have both technical and procedural systems. i.e. train people not to put their passwords online and also have 2 factor so you need more than password!

Have methods to detect and ensure everyrhing being released is secure!

### Computer Security

The whole system is basically C-I-A
1. C: Confidentiality (only you & lectuerer see your marks)
2. I: Integrity (only lecturere chaanges it)
3. A: Availability (you can always see and lectueres can always change)

**Threat model**: Make assumptions about the adversary, the system and the environment. We use this when **evaluating** and testing our security.

It's actually quite hard to test security, it's hard to define what the powers the attacker might have, and what smaller things build up.

However even threat models may not help because sometimes _the users can do stupid things_.
Having a super special password and keeping it all secure and fancy, but the user writes it on a piece of paper on his desk and then posts it on insta with a coffee cup cos #aesthetics could lead to a very bad result.

The capacities and power that the adversary can have might change as well. For example, encryption standards may change, protocols, APIs etc might change and have an unexpected effect on the system that you're securing. (quantum computing)

Assuming knowledge of the attacker is an important aspect as well, because what if they have access to more knowledge than you think? (multiple email accounts, the 2nd factor in 2 factor etc)

For example, they'd attack your servers instead of your website or the hosted DB instead of the website. Maybe even not attack the server, but attacks the OS / host / internet connection.


### "What can go wrong?"
Example, you can do 100% and secure the whole software side, and trust everything on the hardware side, but then something like the `Spectre/Meltdown` system could mess up everything you've done.

It wasn't anything to do with the OS, or the security patches or anything. It was a problem with the hardware, things made by ARM, AMD, Intel were all affected because there was a problem with the actual CPU architecture that everyone used.


#### Spectre/Meltdown explained:

Take an instruction pipeline, it's not always A then B then C then D 
but it's A then AB then ABC then ABCD during the program

To make pipelines efficient, you must always try and keep the CPU be busy trying to the next thing. But if you've reached a conditional/jump, what do you do?

You have to make a `branch predictor` that would obtain the next possible / expected instruction and start processing data that's needed for that.

If the system didn't actually go there, it's usually not too bad because the `CPU State` is reverted as you can continue the computation, however the `CPU cache` was **NOT** reset / updated. We may even have half executed instructions in the pipeline.

What did Spectre/Meltdown do?
- Exploited the branch prediction
- You can get access to the data in the pipeline cache
- Access check is done when instructions are "executed" not actually when they're being predicted. The data is collected, but not shown until you've confirmed you have access.
- However this was the fault as it basically convinced the predictor to get the sensitive data by inching closer and closer in memory to it, using a constantly executing loop. And after some X iterations, because the CPU may have half stored the data and was ready with the pipeline to proceed to the next "retrieve data" instruction, make the only thing change be _where_ the data was pointing. 
- This would then get that data from the cached sensiive information, through hardware even if the software side didn't give permission yet.


So, more detail bout these bois:


Meltdown breaks down the mechanism that keeps applications from arbitrarily accessign the data in system memory.

Spectre tricks applications into accessing the arbitrary locations in their memory therefore exposing the data. They both use side channel attacks to obtain the information from the accessed memory locations.

**Cool cloud computing detail**: If theres any computer that's fully virualised, (not docker etc, think more VMBox), then the host kernel is not affected, just the guest kernel.

# Lecture 3 (Buffer Overflow)

## Stack
Goes from bottom to top 

In order (bot to top):
1. Arguments of the function being called
2. Local variables + saved context register
3. Old base pointer
4. +++ Caller's stack frame.

## Buffer Overflows

So buffer overflows happen because the stack isn't protected per say. 

What happens if you go past the boundary of the buffer in a stack? It means you'd start accessing the values and the variables stored by the calling program

You could even change the return address of the previous call to a malicious function, giving you the ability to change what the computer does as much as you'd like.

So buffer overflows happen because **arrays in C don't really exist**. It's essentially just notation for pointers. 

- Ask for a buffer
- Place malicious code on the buffer
- Overflow the stack
- Change the return address to your malicious code.

**usual attack is to replace the running program with your malicious program using exec()**

### Problems with Buffer Overflows:

So suppose you have some cool kid malicious code right?
To insert it into the program, you're smart and use a string. However, you're not that smart, so you end up with instructions that have string terminating characters, for example `0x0C`, `0x00` etc. 

---- This was the CW ----

### Protection from Buffer Overflows (PREVENT):

Solution A:
- Prevent Bugs in your code!
- Check usages of problematic C functions
- Use compiler flags for this, and use new built programs that have restricted access of the buffers
- Avoid raw pointer manipulations! 
- Understand code from libraries you use!

Solution B:
- Build tools in the program
- Static Analysis on programs
- Fuzzing -> Push random values into your programs, and see if it crashes. Because that usually means it's doing something that wasn't accounted for which means you've made assumptions and that can lead to vulnerabilities.

Solution C:
- Use languages that are memory safe (java, haskell etc)

### Detection from Buffer Overflows:

#### Stack Canaries:
Basically a value stored in the stack, which is meant to detect changes to the stack.

If the canary value has changed, that means something has messed with the stack.

Problem however, is if the attacker knows _of_ the canary or knows what the canary's value should be.

**But what values can you use?**:
1. Cannot use a deterministic value, since that's going to be guessed and avoided.
2. Cannot use a special character, since if you're using a string manipulation program, it could break it. This means it only works for specialist functions
3. Random values with low entropy could be detected by an attacker, and it's not always the best method.
4. Canaries don't work directly if the attacker doens't actually return to the initial function (if they rewrite the return addr)
5. Canaries don't work if there's any malloc or free as the main problem in the code. I.e. that they cannot detect malloced or free'd code (since it's not on the stack, malloc and free hit the heap).
6. Canaries add computation overhead.

##### Malloc/Free with Canaries:
Malloc and Free on the heap. The aim is to get the malloc function to point to the address of a password or address of a place that's sensitive.

If the attacker gains access to the values in a malloc or free () call, then the attacker can overwrite the free memory pointers to point to something else to either read or rewrite or clear the data, which can be a BIG problemo.

Canaries can't protect because this operations is on the heap, not the stack.


#### Protecting against Heap / Canary failures (Guard Pages)

Use a `Guard Page`, which is hardware protected and will raise a fault or an error if someone tries to change, read or write on the memory in those pages.

This is different from the canary, as here we're depending on the harware protection, not the software protection.

This stops them from overwriting the area where the buffer overflow can do damage, since these pages are placed amongst various other memory blocks.

However this is not the best if you have small memory as this may consume a large amount of memory.

This is best used in debugging / testing with some fuzzy testing as it can make sure there's no memory leaks amongst the stack. It's great against program bugs that while not crashing the program, could be overwriting memeory unexpectedly.

#### Bounds Checking:
Basically make sure a pointer refers to a specific memory object, and doesn't go out of that object.
It's great to do on _paper_, however in more complicated structures and codes it starts to break.

This might not stop the attacker, but limits the impact.

#### Fat Addresses:
A normal address is 4 bytes

For a fat address, you'll have
- 4 bytes for Base addr
- 4 bytes for end addr
- 4 bytes for current addr

This means you can detect problems if the memory address is going out of bounds.

However, this would need compiler support, and it might not work with libraries that already exist.

This means that any pointer based calls become non atomic operations. i.e. they become 2 checks more minimum per address based instruction.

## Worms

### Morris Worm // Great Worm

Basically would go to a node in a network, put the payload on the node and check all the related nodes in the network and see whether they have the "worm" already.

If the worm already exists, don't need to add it? 
Naah, add it anyway. Add it 1/7th of the time.

This meant that all the machines on the internet were affected by this and ended up messing up everyone.


### Blaster -- Buffer overflow worm

Basically used a "Remote Procedure Call" (RPCs) by running a **buffer overflow attack**.

- Get a shell with admin priviliges
- Download the payload with the ftp
- install the worm

And how to survive
- Try not getting detected
- Don't make thousands of threads, only make 1 or 2
- Wait for a specific threshold (time, size, day etc)
- The first thread did a DDoS attacks on Microsoft update.

#### ASIDE: Trusted Platform Modules 
Specialised chip on a computer, it requries that you sign off every program being executed on the machine.

# Lecture 4 (23rd Oct) Authentication [only from lectures, NO MEDIASITE]

Authentication / Identification : Who is this?
Authorisation / Access Control: Are they allowed to do this?

Authentication Principles are based on:
1. who you are (fingerprint)
2. What you have (keycard)
3. What you know (password)

## Passwords:

What is a password?
- Shared secret between a user and a service!

### Threat 1 (Password Storing)
How can you implement it?
A: Have a table from users to passwords!

**nope, because what if an attacker gets the table!**

A2: Have a table from users to hashed(passwords)!

**Welll, common passwords' hashes could be revealed, for example having "password", "1234" etc.**

A3: I'll tell the user they HAVE to add some special characters, and cannot have words from the dictionary

**Well, if you do that then users will end up having simpler patterns on a keyboard, and it becomes super simple to haxx**

A4: I'll salt the password!

**Well, okay so this is decent. Because Hash(salt, password) becomes a bit harder since the salting depends on the user and is independent between users. Salting doesn't need to be a secret either since it's not so easy to find collisions. However, if your password is 1234 and you salt it with a public salt, it may lead to vulnerabilities**

### Threat 2 (Password Recovery):

We know that this basically has messed up a lot of things! We know that recovery questions are poop and are prone to phishing attacks. We know that password recovery is a joke unless it's 2 factor but even 2 factor is a joke sometimes.

Basically password recovery is poop af.

### Threat 3: (Man in the Middle!)

Michael Jackson's man in the mirror is not the man in the middle.

Basically this is focused on transmission:

**How do i transmit the password?**
A1: Clear text!
**No pls, need to encrypt**
A2: Encrypted password on a clear channel
**Essentially the same as a password at this point...**
A3: Clear password on an encrypted channel!
** I could fake being google, and you'll just encrypt your password to me instead!**
A4: I'll make you confirm you're google!
** I could fake being google by faking being you, I could just check online for any auth codes that are needed, and ofc they'd have to be public fi you want access to them!**
A5: I'll use some crypto magic and make you share a secret
**Ah damn, you right that might work!!**

### Threat 4: 'Hammering' the login page!

Basically this is someone straight up trying to brute force their way into a password!
Not the best idea, and quite often basically super simple to prevent
1. Rate limit the users/  IPs
2. Timeouts : PRevent login for the next 20 mins #wasteTheirTime2019

### Solution to Passwords??
Biometrics is a pretty decent stance tbh, especially if you're focusing on Confidentiality and Integrity
1. Effortless for memory
2. Secure and confirmed that it's ONLY you
3. Cannot error often
4. Cannot leak the data properly
5. But EXPENSIVE
6. Not always easy to integrate (websites? do i stick my hand on my computer screen?)
7. Accessibility / Availability when broken
8. Once leaked (a fingerprint for example), basically leaked to the whole world and everything else is AT RISK!

### Two Factor Authentication!! (Our saviour...?)

It's getting common everywhere
We're not super sure of it's security
It's not the best for A in CIA
and tbh, it's not always the most great for C either.

# Lecture 5: Access Control (30/10):

Two types of access control:
1. Physical Access Control: Gates and physical enforcement from area
2. Digital access control: Restrict access to resources and interactions

There are different things to restrict
1. Object: Passive entity like a file, memory location etc
2. Access: Ability to perform an action, or interact with something (looking at info)
3. Subject: Active entity that's requesting access to an object or data in an object. So things like users, processes or functions etc.

In simpler words:
- Object : File
- Access: Read/Write/Send/Share
- Subject: Person!

Access Control:
- Concerened with authorisation i.e. what is the subject allowed to do?
- Mediates a subject's access to an object
- Enforces a security policy, limiting what actions are allowed by a subject.

### Complete Mediation:

- This is our aim
- **Trusted Computing Base**: All hardware and software that's responsible for enforcing a policy. For example the trusted base is the OS kernel, the PC hardware. And a fault in this can cause a huge problem in security (think spectre/meltdown?)
- Try and aim for complete mediation, but light and thin to enforce security but not comprimise computation power / speed.
- **Reference Montior**: Control any access to objects and every subject needs to go through the reference monitor (bouncer in a nightclub).

### Protection State:
- Security context is information that's used to make an informed decision. For example in an airport, a passport could be your _authentication_. However you need a visa as your **authorisation**.
- Protection state: It's a state of the security sensitive actions a subject is able to do, for example a user changign to sudo.
- Transition between these states is tightly controlled and must be secured.

### Access Control Matrix:
- Simplest way to present protection state of a system
- Table that represents every object and every subject and the permitted actions between them.

But the Access Control Matrix is a very **theoretical model**. Imagine trying to find a mapping like that on facebook for every entity and every object. And this is hard to map over time, as they can change as it goes along.

**What is it good for?**:
- Express formally / informally what is allowed in the system
- Generally express confidentiality / integrity requirements from the system. 

### Mechanisms and Models (Defintiions):

**Mechanism:** How is the policy enforced? 
**Model**: How do you represent these policies?

### Access Control List:

It's an alternative format of an access control matrix
Where you group the data into types.

- Object Centric access control
- Subject centric capabilities

### Discretionary / Mandatory 
**Discretionary:** Owner of a resource, and defines and delegates the right to other users
-  Requires the notion of the owner (what does owning something mean?)
-  Resource owner defines the associated policy.

**Mandatory:** Policies set centrally by an administrator.
- Notion of an owner is optional
- Great for an organisation that may own the data

Example: 
Google Drive by UoB:
- Users / Students create the file, and define who has access into the file to the point of read, write and other systems
- The University sets the default policies of sharing and distributing data. Limits what _can_ and cannot be sahred etc.
- Difference in this example is that students can share outside of UoB. Imagine if that wasn't allowed, then that would be a restriction placed by the uni on this.

### Role Based Access Control:

Group the users into different roles.
1. Owners
2. Group 
3. Others!

[ TODO: Read the info about RBAC (NIST) from the lectures ]
- RBAC 0 [Flat]: Users have a role, roles have permissions
- RBAC 1 [Hierarchial] : Roles can be inherited
- RBAC 2 [Constraints] : Allows for seperation of duties
- RBAC 4 [Consolidated] : All of the above

### Information Flow Control
Defintions:
1. Read: Receieve information from another entity
2. Write: Sending information to another entity

Example Model: Bell Lapadula
Think of different levels of clearance
- Top Secret
- Secret
- Unclassified

The policy is defined by these constraints:
1. Cannot read up:  I.e. cannot get info from higher level of data. so cannot read somthing with a higher classification
2. Cannot write down: I.e cannot send info to the lower level of the data, so cannot declassify something

Problems with this?
1. Classification of the data becomes a bit harder, until you need to put in other policies to deal with declassificiation.

So in a large organisation you want to keep track of various groups and permission levels in the range. For example if you're in the navy, you don't need to know the secrets of the air force. 
So they add a **Discretionary Access Control** aspect which adds categories to the model.

We use the same classifications as before (Top Secret, Secret, Unclassified etc) but we add a special group / categories into the system which means we can define access a bit better.

You even have something called a **Mandatory Access Control** like the principle of a Top Secret being a lot more strict than secret.

You can have a **discretionary access control** policy so it forces restricted access to that using a model of sets. For example classified documents AB contain A
so you can restrict access for user1 to only A, and user2 to AB, where user1 cannot access A, but user2 can access both A and B in AB.

This is similar to what's used in **SELinux** which is used in android as well.

An extension of the above is to combine the two, combining **Mandatory Access** with **Discretionary access grouping**. This means you can be top secret in one group but only secret in another.


##### Integrity using IFC - Biba Model:

You can have a system of three classifications
1. Fact
2. Belief
3. Rumor

You cannot turn a belief into a fact, but you can turn fact into a belief (similar to the write-up read-down restrictions)
You can add the **Discretionary access control** into the system.

### Brewer And Nash Model (Chinese Wall?)

Imagine you're PWC, and have access to BA, HSBC, Santander, EasyJet etc etc.

You shall define a grouping of "conflict of interest"
so putting companies into these groups and therefore restricting who has access to each.

For each object in your model, you'll identify the following:
1. O = Objects (Client's files!)
2. C = Clients
3. CoI(o) = Conflict of Interest Group
4. x(o): owner, y(o): conflict class CoI(o) - x(o)

Now you'd define the policy as:
1. Define n(s,o): This returns true if `s` has ever accessed `o`.


Now `s` can only access an object `o` if:
- For all o' st n(s,o') = true, y(o) = y(o') or y(o) doesn't belong to x(0')

That basically means that o is from the same company as previously read objects or o belongs to a different conflict of interest class.

`S` can write `o` if:
- S can read o
- And there doesn't exist another file `o'` that you've already read with the same conflict class.
- You cannot write client data if reading anyone else's data. Unless the other data has been sanitised.

This menas you now need a sanitation and declassification policy


### Clark Wilson Model (Integrity of data, used in banks)
The integrity is defined as a set of constraints for the data
- Data in a valid state when it meets the constraints
- Today's Balance = Yesterday's Balance + Today's Deposit - Today's withdrawl

Have well formed transactions, and move systems safely from one state to another.

Have seperation of duty
- Who certifies transactions
- who confirms that these match the constraints 

Some objects / classifications in this model
1. Constrained Data Item  (CDI) - Bank Details
2. Unconstrained Data Items (UDI) - User input
3. Transformation Procedure (TP) 
4. Integrity Verification Procedure (IVP)
5. Permission is a triple {user, TP, CDIs}
6. Transfer{CDI:account, UDI:reference}

Certification rules:
1. CDI State validated by IVP
2. TPs preserve valid states
3. speration of duty
4. TPs wrtie to the log
5. UDIs are validates by TPs

Enforcement Rules:
1. only TPs can change CDIs
2. TPs require authorisation
3. All users are authenticated
4. Only authorised peopl can change permissions

# Lecture 6 Web Security (2nd Nov) - Client Side Security 

-- Note: Big man Tom forgot to record the screen so this is all from the slides.

On a website right now there's  a lot of ads, a lot of analytics being run, a lot of javascript being run. Along with the page's html / js. 

As we move through websites and the _information highway_, we expect things, values and information to be passed through to different websites. For example the **"same origin policy"** allows a web browser in the first web page to access the data from a second web page **if** they come from the same origin. 

An "origin" is defined using:
1. URI scheme
2. Host name 
3. port number

This prevents malicious scripts on one page from obtaining access to sensitive data on another page.

There are 4 fundamental ideas behind same origin policy:
- A: Each origin has client side resources (DOM trees, cookies, JS namespaces etc)
- B: Each frame gets the origin of it's URL
- C: Each JS Script executes with the authority of it's frame (both websites need to accept certain actions)
- D: Passive content get 0 authority (images, CSS etc)


But what does rule **D** do?

It is meant to prevent something called a **MIME sniffing attack!**

## MIME Sniffing Attack:
MIME sniffinc is a technique used by browsers to find the actual type of a particular asset.

Assets are written with a file format, and it's hard to tell what the type might be just from the meta data sometimes, and therefore this requires the browser to MIME sniff.

This is a big vulnerability as the attacker can leverage MIME sniffing to send an XSS attack (Cross Site Scripting). 

MIME sniffing (not the attack) is:
1. Web browser requests a particular asset which responds with no content type or a content type set by he previous owner
2. Web browser "sniffs" the content to analyse the file format
3. Once the browser has completed it's analysis, it compares what it found against the web server's provided type in the header. 
4. If there's a mistmach, the browser uses the MIME type that it determined to be associated with the asset.

#### MIME SNIFFING ATTACK:
Essentially the vulnerability comes from the concept of the users being able to upload data to a website.

Suppose a website accepts a `JPG` or `PNG` type, but a user uploads the file as a type of `html`. This would pass through the upload system, however the next user who visits the site and looks at the image would identify it as actually being an html file through the MIME sniffing, and it might enable the html file to run javascript and therefore run some XSS (cross site scripting) attacks.

#### Avoiding MIME Sniffing Attacks
1. Stop smelling everything you see damn man.
Formally: Set a nosniff content type option in your http header.

This would disable the browser from sniffing the content.

2. Use a subdomain to avoid XSS attacks, as this would prevent the script from gaining authorisation.


## DNS Exploit 

The internet and users heavily rely on DNSs to find any web page and browse through the internet overall.
A DNS exploit is the vulnerability in the DNS through which an attacker can infiltrate a network.

Approach
1. Create a domain attacker.com
2. User visits attacker.com
3. Browser generates a DNS request to attacker.com
4. Attacker response is v short lived (small TimeToLive)
5. Attacker binds attacker.com to victim.com's IP address
6. Ajax request aimed at attacker.com ends up going to victim.com
7. the Ajax runs code that was supposed to be on attacker in the internal part of a company

## Private Browsing

Client Side Privacy: Incognito aint anything except a forgetful browser.

Private Browsing reveals a lot still, things like DNS caches, RAM left over data (page swaps, temp files etc).

It's basically not hard at all to recover such data!

# Lecture 7 (Web Security II) 6th October

Attack 1:
- CSS Based attack
- Get the victim to visit attacker.com
- Learn what other websites have been visited (purple links?)
- Exploit the colour of the links to see if they've visited them
- Gain information like this.
- **Solution:** Lie to JS about this, and say that no website has ever been visited.

Attack 2:
- Cache Based Attack
- Get the victim to visit attacker.com
- Learn what other webites they've visited
- This is based on loading times for objects like google map tiles etc.
- **Solution:** No caching on the client side, but if that's slow go for origin based caching, or maybe even non local caches!

Attack 3:
- Rendering Engine based attack
- Get victim to visit attacker.com
- Learn what other website the victim has visited.
- Attacker wants to make a copy of the login pages, and then steal your data. If they make copies of the same images used in the actual login page, then they can see whether you're logged in or not in the other pages.
- **Fixing** it : apply the same origin policy on shader effects


## Timing Attacks:

The overall goal is to see the response time in a cross site scripting response.
The attacker will send a XSS request to the other website that they're trying to target, and if the response is quick (very quick) then they know that you have accessed the website recently due to the caching from it.

So other than just seeing whether a website has been visited. You can do other stuff top, like just see some details from the caches 

Thing like requesting
1. Get q=in:sent&from:Bob could reveal whether they received any mesages from Bob.

If the response is quick, then obviously the data was accessed quickly, and if the response is slow then it wasn't visited / didn't happen from the other website


**Goal of the attack:**:
Find the answer to a boolean question:
1. Transform the question into a search request
2. Send the search request and collect samples
3. Analyse resposne time -> answer the question

**Steps of the attack**:
- Run it once with a negative response so you know the baseline for negative responses
- Run it multiple times for positive resposnes so you can analyse the data (it's not a simple Yes/No per req)
- Is there a statistical difference between the Yes and No responses.


We do this above multi-sample testing because of congestion and concurrent requests on the client and server.  Things liek traffic might affect the response time.

- Keep requests minimal, to avoid DDoS requests
- Keep requests quick due to short visits from users.


To increase the difference b/w positive and negative responses:
1. Response inflation, so expect the parameters reflected in the URLs to be a lot higher, so it'll take longer to get the request if it's valid. However will quickly say no if invalid for the first req.
2. **What if there's no paramets in te url?** Then you send a dummy question you know is going to have a negative response with some extra maths, and it'll give back a negative. Then you send a valid question with some extra maths, and it'll reply back a bit longer.

> actual examples are:
> dummy: in:sent&from:xiquisddk&hasnot:{rjew+...+iqejh}
> question: in:sent&from:alice&hasnot:{rjew+...+iqejh}


**What if the other website is rate limited and might see you spamming requests?**

Answer: **Use the `serviceWorker.cache`**, this is a file that's stored on the victim's browser (and not another site), and you can send requests for full pages to it rather than direct questions but the response times will be different if the pages have been visited or not. This will not be rate limited and therefore technically undetectable

**What else can you do?** if inflatinon isn't possible?

Attacker can manipulate the target by making the value appear several times, so if you're searching for a positive reaction email, send them 100 emails wiht a lot of spam words so it lands in spam and ensures that the user doesn't see it. You can then group requests to see how many times you get a response for your mail + the targetmail and do stat analysis there.




## Protecting against these attacks
1. Don't allow external queries: but this might not work for a large class of applications
2. Reduce query expressivity: It might have an impact on the usability / utility of the system
3. Rate limit query: Attacker can go around this using the browser cache.
4. Detection: Attack detection is the new research topics.


# Lecture 8: (9th Nov) Public Key Infrastructure

I've ignored the PKI and SI explanations because ew

Problem we're trying to solve:
In a PKI structure, how do i know who Bob is and if his publickey is actually his?

You need to use authentication.

## Certificates in Encryption

## Digital Certificate (X509)

- Help with authentication
- Binds an identity with a public key
- Issued by a Certificate Authority (people your trust!)

## Certificate Authority (CA):
- Responsible for issuing and signing certificates
- Often a trusted third party, (digicert, verisign)
- Companies and organisations have their own CAs

### Certificate being used, (TLS Example):
- Bob has a pk, and a certificate with a pk
- Alice has the pk of the CA
- Sends bob hello, bob replies with a hello and a certificate
- Alice validates the certificate, and generates a `pre master secret`, and bob takes the the `pre master key`, and Bob and Alice generate a secret key from this pre master key and continue communication with a secret key, symmetric enctyption.


Usage Example:
**Handshake**:
- Auth one or both sides
- negotiate algorithms and params
- establish a secret **session key**.

**Record Protocol**:
- Exchange individual messages
- protected under symmetric key

**Mutual Authentication Definition**: It's when two parties authenticate each other at the same time, and it's the default mode in some protocols, and optional in others.

**mTLS: Mutual TLS authentication**: It's much more widespread in business-to-business applications, where a limited number of clients are connecting to specific web services. This is usually because the security requirements are a lot higher in companies than consumer environments.

Its usually handled by machines not by the users until it fails.


In the TLS handshake, we use a **random value** to send to Bob with the first message, which not just use the premaster in the first case so you reduce communictions?

A: Because the attacker could immitate being you and then do a "replay attack!" (what i'm feeling listening to these lectures). This "replay attack" could be used to do repeating transactions and keep sending the same values again and again.

## Certificate Chain:

Well, basically trying to get everyone signed by one authority all the time would be hard and complicated as it scales. So instead CAs can sign a signature, and this could be used to sign another signature. Basically building a chain of certificates.

Keep checking the signatures until you find a one you trust.

These intermediate certificate people (the ones who got signed by a CA) get a constraint, and it stops them from signing any keys, but fixes them towards specific domains (For example @ bristol.ac.uk)

## Certificate Expirations:

The certificate can expire based on the policy set by those signing it.

If a certificate is expired in a chain then all certificates signed by those is invalid as well. 

A -> B -> C
If B is invalid, then C is insecure / unsecure?

## Registration Authority:

- Front end entity you interact with to obtain a cert
- Provide the RA with information, for example being physically present
- RA verifies your identity
- Once this is confirmed, it's sent to the CA and the public key is signed.
- Does not sign the certificate itself.
- Ususally a government agency?

### Certificate Revocation List:

The CA publishes and maintains a list of Certificates that cannot be used anymore

Basically certificates that aren't secure anymore 
This happens if
- compromised private key
- HR reasons (do we truss the person's pk?)
- Company changes details of themseleves
- Discretion to the CA

the list is **public** to prevent anyone from using a compromised or exposed / untrustworthy CA

Browsers actually implement this list to point out authenticated signatures that aren't valid.

## Key Escrows

Basically the private keys (whether symmetric or PKI) are stored in an escrow by companies or employers or organisations in the cases where the it may arise that these keys are needed to gain access to the data encrypted by the employees or workers. 

The problem is restricting access to the keys if they've been exposed in this manner. the third party access should be permitted only under carefully considered conditions. 

Court orders are usually the reasons. This is controversial in many countries due to the technical mistrust of the security of the escrow itself. And this might extend even to untrust of the entire system if it functions as designed.

## Problems with Certifications (Google review) [not in the slides]:

[This was a refrenced link that he recommended people read](https://www.certificate-transparency.org/)

[This however is easier to read](https://www.certificate-transparency.org/what-is-ct) because it's direct.

Essentially sometimes CAs might leak or might be comprimised, which means that some certificates issued by them could be grabbed and used maliciously.

Certificate transparency has three main goals.
1. Make it impossible for a CA to issue an SSL certificate without the certificate being visible to the owner of the domain
2. Provide an open auditing and monitoring system that lets any domain owner / CA determine whether certificates have been mistakingly issued.
3. Protect users from being duped by false certificates.

It uses the following components **to build a framework for the goals mentioned above**:
1. _Certificate logs_: Append only network structure that is cryptographically assued. Allows anyone to submit certificates to a log, but usually CAs are usually the foremost submitters. Anyone can query a log for cryptographic proof to verify the log. These servers can be operated independently or by an ISP
2. _Monitors_ are publically run servers that contact all log servers certificates and watch for any suspicious certificates. These are usually run by goverments or people like Google/Banks etc. Others are run as subscription service that CA can buy into. It's open for public to run their own as well.
3. _Auditors_: are lightweight software components that typically perform 2 funtions. They can verify logs are behaving correctly and consistently.


The entire framework is built to function with these principles:
1. Earlier detection of faults
2. Faster Mitigation
3. Better oversight.

# Lecture 9 (13th Nov) : Network Security






