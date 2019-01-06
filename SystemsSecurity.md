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

