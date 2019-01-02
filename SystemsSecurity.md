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

# Lecture 3 ()
