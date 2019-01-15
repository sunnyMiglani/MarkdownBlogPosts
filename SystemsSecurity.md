# System's Security

4th year MEng University of Bristol module

Author: Sunny Miglani

**Module description**:
Basically the course is structured to not depend 100% on slides for the exam.
"Anything in security in the world can be asked" (lol)

# Table of Contents 
- [Lecture 1 (Intro - 2nd Oct):](#lecture-1-intro---2nd-oct)
    - [Example of a System and a fault](#example-of-a-system-and-a-fault)
    - [2 Factor authentication problems:](#2-factor-authentication-problems)
- [Lecture 2 (Safety 5th Oct)](#lecture-2-safety-5th-oct)
    - [Safety Measures:](#safety-measures)
    - [Risk](#risk)
    - [Security](#security)
    - [Definition of an Attack](#definition-of-an-attack)
    - [Countermeasures](#countermeasures)
    - [Computer Security](#computer-security)
    - ["What can go wrong?"](#what-can-go-wrong)
      - [Spectre/Meltdown explained:](#spectremeltdown-explained)
- [Lecture 3 (Buffer Overflow)](#lecture-3-buffer-overflow)
  - [Stack](#stack)
  - [Buffer Overflows](#buffer-overflows)
    - [Problems with Buffer Overflows:](#problems-with-buffer-overflows)
    - [Protection from Buffer Overflows (PREVENT):](#protection-from-buffer-overflows-prevent)
    - [Detection from Buffer Overflows:](#detection-from-buffer-overflows)
      - [Stack Canaries:](#stack-canaries)
        - [Malloc/Free with Canaries:](#mallocfree-with-canaries)
      - [Protecting against Heap / Canary failures (Guard Pages)](#protecting-against-heap--canary-failures-guard-pages)
      - [Bounds Checking:](#bounds-checking)
      - [Fat Addresses:](#fat-addresses)
  - [Worms](#worms)
    - [Morris Worm // Great Worm](#morris-worm--great-worm)
    - [Blaster -- Buffer overflow worm](#blaster----buffer-overflow-worm)
      - [ASIDE: Trusted Platform Modules](#aside-trusted-platform-modules)
- [Lecture 4 (23rd Oct) Authentication [only from lectures, NO MEDIASITE]](#lecture-4-23rd-oct-authentication-only-from-lectures-no-mediasite)
  - [Passwords:](#passwords)
    - [Threat 1 (Password Storing)](#threat-1-password-storing)
    - [Threat 2 (Password Recovery):](#threat-2-password-recovery)
    - [Threat 3: (Man in the Middle!)](#threat-3-man-in-the-middle)
    - [Threat 4: 'Hammering' the login page!](#threat-4-hammering-the-login-page)
    - [Solution to Passwords??](#solution-to-passwords)
    - [Two Factor Authentication!! (Our saviour...?)](#two-factor-authentication-our-saviour)
- [Lecture 5: Access Control (30/10):](#lecture-5-access-control-3010)
    - [Complete Mediation:](#complete-mediation)
    - [Protection State:](#protection-state)
    - [Access Control Matrix:](#access-control-matrix)
    - [Mechanisms and Models (Defintiions):](#mechanisms-and-models-defintiions)
    - [Access Control List:](#access-control-list)
    - [Discretionary / Mandatory](#discretionary--mandatory)
    - [Role Based Access Control:](#role-based-access-control)
    - [Information Flow Control](#information-flow-control)
        - [Integrity using IFC - Biba Model:](#integrity-using-ifc---biba-model)
    - [Brewer And Nash Model (Chinese Wall?)](#brewer-and-nash-model-chinese-wall)
    - [Clark Wilson Model (Integrity of data, used in banks)](#clark-wilson-model-integrity-of-data-used-in-banks)
- [Lecture 6 Web Security (2nd Nov) - Client Side Security](#lecture-6-web-security-2nd-nov---client-side-security)
  - [MIME Sniffing Attack:](#mime-sniffing-attack)
      - [MIME SNIFFING ATTACK:](#mime-sniffing-attack)
      - [Avoiding MIME Sniffing Attacks](#avoiding-mime-sniffing-attacks)
  - [DNS Exploit](#dns-exploit)
  - [Private Browsing](#private-browsing)
- [Lecture 7 (Web Security II) 6th October](#lecture-7-web-security-ii-6th-october)
  - [Timing Attacks:](#timing-attacks)
  - [Protecting against these attacks](#protecting-against-these-attacks)
- [Lecture 8: (9th Nov) Public Key Infrastructure](#lecture-8-9th-nov-public-key-infrastructure)
  - [Certificates in Encryption](#certificates-in-encryption)
  - [Digital Certificate (X509)](#digital-certificate-x509)
  - [Certificate Authority (CA):](#certificate-authority-ca)
    - [Certificate being used, (TLS Example):](#certificate-being-used-tls-example)
  - [Certificate Chain:](#certificate-chain)
  - [Certificate Expirations:](#certificate-expirations)
  - [Registration Authority:](#registration-authority)
    - [Certificate Revocation List:](#certificate-revocation-list)
  - [Key Escrows](#key-escrows)
  - [Problems with Certifications (Google review) [not in the slides]:](#problems-with-certifications-google-review-not-in-the-slides)
- [Lecture 9 (13th Nov) : Network Security](#lecture-9-13th-nov--network-security)
  - [Types of Attacks in networks](#types-of-attacks-in-networks)
  - [Examples of Vulnerabilities](#examples-of-vulnerabilities)
    - [DNS Resolve & Cache (DNS Poisioning)](#dns-resolve--cache-dns-poisioning)
    - [Slow Loris Attack:](#slow-loris-attack)
- [Lecture 10 : Anonymous Communication (16th November)](#lecture-10--anonymous-communication-16th-november)
    - [Define: Anonymity](#define-anonymity)
    - [Define : Unlinkability, Unobservability](#define--unlinkability-unobservability)
  - [VPNs](#vpns)
  - [TOR (Circuit):](#tor-circuit)
  - [Directory Authorities:](#directory-authorities)
  - [Tor Vulnerabilities:](#tor-vulnerabilities)
    - [Passive Attacks:](#passive-attacks)
    - [Active Attacks:](#active-attacks)
- [Lecture 11: Firewalls (27th Nov)](#lecture-11-firewalls-27th-nov)
  - [DMZ of a Network:](#dmz-of-a-network)
  - [Types of firewall](#types-of-firewall)
    - [Packet Filters:](#packet-filters)
    - [Stateful Filtering:](#stateful-filtering)
    - [Application level proxy](#application-level-proxy)
    - [Client Level Proxy](#client-level-proxy)
    - [Personal Firewall](#personal-firewall)
  - [Network Address Translation (NAT)](#network-address-translation-nat)
  - [Firewalls and Attack Prevention:](#firewalls-and-attack-prevention)
  - [The Great Firewall of China](#the-great-firewall-of-china)
  - ["iptables" Firewalls on Linux](#iptables-firewalls-on-linux)
- [Lecture 12: Isolation (4th Dec)](#lecture-12-isolation-4th-dec)
  - [System level sandbox:](#system-level-sandbox)
  - [Security and Virtualisation / Sandboxing:](#security-and-virtualisation--sandboxing)
    - [Container Based Sandboxing:](#container-based-sandboxing)
  - [UniKernel](#unikernel)
  - [SGX Hardware supported memory enclaves](#sgx-hardware-supported-memory-enclaves)
- [Lecture 13: Hardware Root of Trust (7th Dec)](#lecture-13-hardware-root-of-trust-7th-dec)
  - [RootKit](#rootkit)
  - [Software approach to Trust](#software-approach-to-trust)
    - [Return Oriented Programming Attack](#return-oriented-programming-attack)
  - [Hardware Approach for Attestation](#hardware-approach-for-attestation)
    - [Static Root of Trust:](#static-root-of-trust)
  - [Trusted Platform Module Based Computed (TPM)](#trusted-platform-module-based-computed-tpm)
    - [TPM Registers:](#tpm-registers)
    - [TPM and Remote Attestation:](#tpm-and-remote-attestation)
- [Lecture 13: Blockchain (14th December)](#lecture-13-blockchain-14th-december)
  - [Proof Of Work](#proof-of-work)
  - [Transactions](#transactions)
  - [Chain](#chain)
  - [How can i mine for some of that blockchain gold?](#how-can-i-mine-for-some-of-that-blockchain-gold)

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
In order of effectiveness, these are how you make something _safe_ (most effective is at the other end!)
1. Mitigate: reduce damage that might happen in an accident
2. Control the environment or control the system
3. Reduce likelihood of the occurence
4. Eliminate the hazard that might cause the accident



Types of safety measures:
1. **Passive**: Presence contributes to saftey, like building fences around train tracks (eg. Stack Canaries)
2. **Fail-safes**: Systems that if they fail, reach a safe state like trains stopping on open doors etc (eg. Guard Pages)
3. **Active safety measures**: montior systems and intervine like putting off a fire on a train if it starts. (Bounds checked in a compiler/hardware)

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

| Safety              | Security       |
| ------------------- | -------------- |
| Hazard              | vulnerability  |
| ?                   | threat         |
| safety measure      | countermeasure |
| risk                | risk           |
| accidents/incidents | incidents      |

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
7
**I could fake being google, and you'll just encrypt your password to me instead!**
A4: I'll make you confirm you're google!

**I could fake being google by faking being you, I could just check online for any auth codes that are needed, and ofc they'd have to be public fi you want access to them!**

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

OSI Model:
1. Application Layer
2. Presentation Layer
3. Session Layer
4. Transport Layer
5. Network Layer
6. Data Link Layer
7. Physical Layer

OSI model doesn't fit exactly reality, it's a nice way of understanding the overall system

The actual running model is the TCP/IP model:
1. Application Layer (HTTP, FTP)
2. Transport Layer (TCP)
3. Internet Layer (IP)
4. Network layer


**TLS/SSL** for example are in application layer in the TCP/IP model and the presentation layer in the OSI model.

Encapsulation is taking the message you want to send from the application level and sending it down the stack. 
Decapsulation is the opposite.

Structure is like so (A -> B means B covers A)
> (http header/httpPayload) -> (tls header/tls payload) -> (tcp header/tcp payload) -> (ip header/ip payload) -> ... -> packet


Security is stored on the different layers as well, and they're focused on different aspects of the security.

To add security to existing protocols, we add **optional layers** into the system to ensure that there's backward compatibility in the network.

## Types of Attacks in networks

1. Traffic Analysis
2. Message disclosure
3. masquerade
4. message modification
5. replay 
6. topology disclosure
7. unauthorised access
8. denial of service

There are two types of targets
- Network data
- Systems connected to the network or within the network (switches, routers etc)

Types of attacks:
- Passive Attacks
- Active Attacks

**Traffic Analysis**:
- Attacker can see who is exchanging messages
- Number of messages, time they're sent and the patterns in which they're sent. 
- They are usually done as timing analysis

Example: SSH Timing attack, that looks at how many packets are sent in an interactive session and learns details of typing behaviour of a user.

**Message Disclosure**:
Attacked aimed to extract specific information about a website such as software distributions, version numbers, patch levels etc.
- Attacker can read the content or some content of the exchanged message
- Countermeasure: encryption
- Although size of the messages/packets can reveal some information. 

**Masquerade**:
- Pretending to be someone else
- TCP Hijacking
- Changing IP address in the DNS etc.
- Conducted through the use of stolen login information, IDs, and passwords!

**Message Modification**:
- Similar to a man-in-the-middle attack, where the attacker does the following
- Receives message from A
- Modifies the message
- Sends it to bob as A
- Blocsk the traffic between Bob and Alice so he can keep the attack going with Bob thinking he's alice


**Replay Attack**:
- Data maliciously _retransmitted_ (imagine a transaction).

**Topology Disclosure**:
- Discover nodes connected to a network
- Discover services running on those nodes
- **Port scans** in the network, (morris worm is an example of this)

**Unauthorized Access**:
- Break into a system
- Many ways to do so, like phishing, password guessing, brute force etc.

**Denial of Service**:
- Attacker wants to block the usage of something in a network, for example a node or router etc
- Example is overloading a server with a large number of reqeusts etc.



## Examples of Vulnerabilities

TCP Packets main things
1. Sequence number
2. Ack number
3. Ack Flag
4. Syn Flag

TCP handshakes are used to send some sequence numbers and acknowledgement numbers so the two devices in the communication are aware of packets being sent and can identify missing or collided packets.

- Sequence numbers are not random
- they're designed to prevent collision
- Things can go wrong like getting haxed
- Attackers can **GUESS** the sequence numbers!

THIS ALLOWS FOR **Session Hijacking!!** by an attacker once they guess your number.

**Oh but i'm protected from an attacker coz i can see which IP my packet is coming from!**
NOPEEEEE

This is bad because anyone can fake an IP address, specifically they can change the actual packet data (like we did in labs wowza) to fake a user's ip. It's a masquarade attack! 

Using TCP can also have problems with 
1. Reset Attacks: Can spoof an ip packet and send a TCP RESET request that could break any application that relied on long-lived connections (imagine DL ssh)
2. Data Injection: Wait until application level authorisation has been achieved, insert a packet as if it was coming from the initial user. Masquarade as the server for the response and mimic man-in-the-middle for the rest of it.

TODO: Read on SynFlood Attacks



**How do i attack knowing the topology of a network?**:

Basically you can disconnect routers by using SynFloods, DoS attacks or even Reset Attacks!
This works if there's only IP based authorisation.

There's a fix against this, i.e. that a smart network admin could enforce two hardware connected routers to have a TTL being set to 255 (max value, TTL reduces per hop in a network). If the incoming packet has a TTL of less than 255, then it's obviously not from the hardware connected router, and is therefore an attacker or some malicious force. 


### DNS Resolve & Cache (DNS Poisioning)

DNS has a map from domain to an IP address.
You attack the DNS to replace the IP address from a website to lead to your IP instead.

For example, replace the IP related to bank.com to lead to your ip, which hosts a fake website. This could also be a valid attack for the bank.com to lead to an invalid IP therefore causing a form of a DOS attack!

Steps for this attack:
1. Exploil vulnerability in the DNS server
2. Man in the middle (send a fake response)
3. Modify the client host file
4. Domain high-jack (point to a different DNS server)
5. Masquareade type attack!

Steps to block this attack! (DNSSEC)
1. Sign the (domain name, IP Addr) pair with the domain's owner certificates!
2. Problem! : What if you map between domains, i.e. from foo.bris.ac.uk to bar.bris.ac.uk??? 
3. The above fault could lead to a **topology disclosure** where the attacker could identify the topology by looping over the domains from a->aa, etc.

### Slow Loris Attack:

- The same as a normal DOS attack, overload the server's resources
- Slow loris is a protocol level attack, and requries v v little computer power from the attacker
- HTTPS request is always finished by \n\n, this means that you can send https requests slowly in small and small packets.
- Before it times out, send another character for the HTTPs request. Keep doing that
- Keep doing it from different connections, so then you can keep sending slowly data. This means that all your active connections would stop.
- Low Bandwidth too



# Lecture 10 : Anonymous Communication (16th November)

Attackers can observe network traffice very easily, and even without looking at the actual data, you can learn a LOT.

ISP's for example, know the `domain`, the `ip`, the `ports` the `packet size`. 

Why should you have anonymity?
- Law enforcements doens't want to tip their targets
- Minority Groups that are under attack
- Journalists, Lawyers etc.

There's a few things that try their best for you to try this (tor)


### Define: Anonymity
- Prevent an observer on a network to link a participant to an action
- Private browsing (like incognito) is useless for observers, it just doesn't store data in local files, everything else is the same.

If people can be linked to websites, then they can be linked to certain behaviours. For example Alice visiting asos means she's probably buying clothes! Depending on the sale and her behaviour you can probabalisitcally say she's aiming to buy shoes instead! 

### Define : Unlinkability, Unobservability
Unlinkability: Cannot link Alice to some online identity or platform via observations

Unobservability: Cannot tell Alice is on the internet or more specifically cannot tell if alice is using some anonymity tool!

Confidentiality != Anonymity

## VPNs
VPNs provide a relay for the users to connect through to their actual networks. For example, Alice, Bob and Charlie can all connect through this relay to connect to their actual websites.

To an observer on Alice's local network, who cannot observe the data directly in the packets, it'd be hard to tell what exactly Alice is doing as based solely on IPs you'd see a connection to another server which isn't specific to what website she's actually visiting. However, with any form of deep packet inspection, this data can be quickly recovered.

Now if the attacker had access to the other side of the relay as well, and knew that Alice Bob and Charlie (specifically Alice amongst X others) is transmitting their data through the relay, it wouldn't be impossible to identify the packets being sent from/to Alice.

Specifically looking at things like 
- Response time
- Size of packets

To get away from the above, instead of the relay transmitting the data instantly like a 1-1 mapping from Alice to website, the relay would group the packets and send it all at once to deal with the data.

## TOR (Circuit):

Instead of using a single relay like a VPN, make the connection bounce amongst multiple relays
This means that an attacker would have to have access to the start relay and the end relay, and find a way to achieve that is hard.

So now for Alice to send a message through this structure of multiple relays, she needs to prepare for encrypting this data amongst the relays.

If alice doesn't trust the relays to not sniff the packets and not observe / alter the data, she needs to encrypt from start to end.

Specifically, encrypting in the decreasing order she gets to the relays
For example, imagine relay1, relay2

Alice would first have to encrypt the data with relay2 symmetric key, then encrypt that packet with relay1 symmetric key.

This is to allow relay1 to read the data relevant to it, but not touch the data relevant to relay2.

**BUT REMEMBER**, that the data from the last relay to the final result is **unencrypted**. This could be fixed by adding the last layer of encryption

**Tor Vulnerabilities?**:
1. Alice is communicating with the relays over TLS but the last relay is communicating with the webiste using either IP or TCP. However, you can mask these with some nice TLS-IP layering.
2. Any address-name-resolution, or DNS resolution caching should be done **THROUGH TOR**, otherwise Alice is just exposing who she's speaking to directly through this. This is valid for any Authorisation certificates as well.
3. Remember that End-Server can still track you (things like cookies + machine IDs + unique IDs)


## Directory Authorities:
- There's a few of them in the Tor Network
- You can use them to download a list of known relays
- The use consensus protocols to decide trusted relays

## Tor Vulnerabilities:
- Very hard to deanonymize everyone all the time
- Definitely possible to deanonymize the same person somtimes.
- As in it's hard to basically identify exactly who everyone is in the entire tor network, but you can see that one or two users behave exactly similar each time and can start to identify who these users are!


### Passive Attacks:

1. **Size and Timing based attacks!**
- Possible if the attacker can observe the in and out relays
- attacker can either own a lot of the relays, so maybe traffic will be sent through his relay
- Or have some way to observe the whole network!

2. **Service Fingerprint**:
- Build a pattern of size/timing of a service response
- Observe an entry node and try and match it to a user
- You can learn which users specifically are accessing a service you care for, even if you can't see what else they're tracking.

### Active Attacks:
1. **Steal a key in the TLS encryption between relays**:
- Steal the keys between the relays, this would mean that the data that's sent through is visible to someone who has access to snoop it
- It's hard for the attacker to keep it running, just because TOR recycles the keys regularly.
- It's a high cost attack.


2. **Iterated Compromise**:
- If you find vulnerability, then you can infect one relay to another. (So attack sequentially for a whole path). 
- But Tor changes the circuit regularly for each user.
- If the tor servers cross borders, then legal authorities don't have access to legally follow the path.

3. **Run a Relay**:
- If the attackers control a large number of relays, it's likely they'll have access to both ends
- They need to own a significant portions of relays
- It's costly.

4. **Smear Attacks**:
- Purpose is to force end-nodes to shutdown, which means the attacker can own more end-nodes.
- Make requests legally, so people end up trustring tor less.
- Attacker runs a lot of illegal traffic through your nodes, forcing the government to make it shut down.
- You can however run normal relays, as long as they're not end nodes! 

5. **DOS on directory authority**:
- Could just stop the network by stopping people from downloading the nodes and available relay lists.

6. **Run/Compromise directory authority:**
- There's a consensus protocl that stops any trivial compromised, you'd have to buy a large number of them. Maybe you can DoS the other ones.

7. **Block Relay**:
- Everyone can access the directory authority, so an attacker (or the government) could block the IPs and make the directory authorities illegal
- TOR bridges are ways around this, and are not advertised.

8. **Block Bridges**:
- Look at SSL traffic
- Connection to TOR bridges has some recognizable traffic and aretfacts.
- Connect to it yourself (as a government) and see if it's a TOR bridge. If it is then break them down!
- China is doing this


# Lecture 11: Firewalls (27th Nov)

**Firewalls** are good for high likelyhood simple attacks. Things like DDoSing (which aren't too complex) 

- Protect LAN
- Interpose between the internet and a local network
- Used as a perimeter defence, and is at the single point of entry. It isolates the local system from the outside world

**Design Goals of a firewall**:
- ALL Traffic must pass through the firewall
- only authorised traffic is allowed to pass through (remember ip checks, etc)
- Firewall itself must be immune to penetration
- **works between the network interface to the applications**


Example of a firewall at http is china using deep packet inspection to look into where the data is coming from / going to.

## DMZ of a Network:
Demilitarized zone of a network is the area where public facing resources are hosted. However they should still be accessible from the inside network.

The policy may be different (you cannot do ssh from the internet, but it's ok to connect from a LAN addr)

**From the internal side**:
The idea is to have only one specific node that can access this DMZ and to block off the rest of the internals using a firewall. This controls who has and how they have access to the dmz. DMZ itself is prone to attacks such as DNS, DDoS etc, and would therefore require a firewall itself against simpler attacks that are obviously not users.

There can be multiple types of DMZ policies:
- Block all traffic by default (whitelist the YESs)
- Allow all by default (blacklist the Baddies)

Why use a blacklist versus a whitelist?
- Blacklists can be delegated to third parties for any decision that needs to be made. They can be auto updated by anti-viruses and it's overall easier to administrate. However it makes it hard to block new attacks unless they've been noticed.
- Ecommerce loves blacklisting rather than whitelisting because they'd rather take the hit from one or two fake transactions and feel it's better to have a hundred other valid ones. The idea of blocking out a user is scary to small platforms.
- Whitelisters prefer whitelisting just to allow easily accessible and controllable flow of data. Having the idea of "oh we'll block a virus" is good until the virus eats up your computer. It's better to avoid getting ill, rather than run around looking for medicines and doctors when you are ill.
- "Who do you let into your home?" (support for white listing)
- Whitelisting is good for well defined traffic (changes to a repo)
- Blacklisting is good for free flow of traffic.

## Types of firewall
1. Packet Filters
2. Stateful Filtering
3. Application-level proxy
4. Circuit-Level Proxy
5. Personal Firewall

### Packet Filters:
Applies rules to each packet, based on the TCP/IP Headers. For example allowing access for ssh only from local computers but allowing any http connection for websites.
DPI (Deep Packet) looks at the higher layers as well, past http, where you can disallow certain websites.
Can be done on a separate machine / router which can apply rules to a whole network.

### Stateful Filtering:
Essentially more complex versions of processing packets, usually based on some context. For example blocking outside connections from connecting to a localhost but allowing connections that were already running and set up to keep running. You can verify that the types of incoming/outgoing packets match as well.
Example: Stopping DDoS attacks because they always are sent with the same packet / same IP. So you have some stateful information that lets you block out the new requests.

### Application level proxy
Proxy is applied at the applicaiton level, therefore every interaction with the outside world has to go through the proxy. 

The idea is to seperate you from the outside world. 
You can authenticate the proxy seperately and essentially the flow of the network is then
   
    Client <-> Proxy <-> Server

The idea being that the data should always go through the proxy both ways. However for the proxy to understand the routing, it needs to be able to understand the protocol that you're using (tls is blocked on purpose)

This allows for a lot more depth analysis, however it basically removes any privacy. So they can see everything that's being used for communication.

This acts as a performance bottleneck though, as it would have to keep checking it.


### Client Level Proxy
TOR is a client level proxy as an example. Similar to the application level proxy, but it relays TCP packets that are being transferred.

### Personal Firewall
Built and supported by the OS
Set access rules to each program, check whether they're allowed to connect to the internet. For example, why should notepad need internet access?

## Network Address Translation (NAT)
- Translate IP Address from the internet to your local network.
- Works at the IP layer
- Limits what connectiosn can go outside and what can connect back into it.
- This allows port forwarding as a policy as well.

## Firewalls and Attack Prevention:

**Slow Loris Attack**: Apply application level proxies or even stateful filtering.

**Network Observation?**: Client Level proxy (for example TOR)

**IP Spoofing**: Packet filtering application

## The Great Firewall of China
Blocks the data based on 
- IP Address
- URLs
- Keywords
- Might even scan page content

Uses **TCP Packet Reset** to reset the connection constantly and prevent any real communication from going through and might drop connection

Newer versions of this includes some form of pattern recognition through ML that can be used to block communication based on behaviour (remember the tor example)

Constantly competing with TOR, to stop any new implementations they make that keep the attacks going.

## "iptables" Firewalls on Linux
- Old and not used anymore
- nftable is the newest version (with a complex implementation)
- It defines a bunch of different applications (ip filtering, etc)

We're going to focus on iptables:
It's represented by using different tables that represent different stages of packet flow through the netfilter or network stack.

Each table, the packet traverses a chain of functions to determine if the packet is transformed or dropped.

There's Tables and CHAINS (convention says caps)
**Tables:**
1. Filter
2. Nat
3. Mangle (do complex packet modficiation)
4. raw (it's called first and is used for low resource functionality like packet filtering)
5. security (used to support MAC)

**CHAINS**:
1. PREROUTING 
2. INPUT
3. FORWARD
4. OUTPUT
5. POSTROUTING


Note: Not all these exist in all tables

**nat table**:
Network address translation,
runs PREROUTING and POSTROUTING and modifies incoming and outgoing packets.


# Lecture 12: Isolation (4th Dec)

**What are the threats?**:
- Vulnerable software: Broken code that has vulnerabilities like buffer overflow etc.
- Malware: Software is designed to act maliciously, ususally downloaded from compromised websites or malicious webistes.

**What is the objective of isolation?**:
- Those programs (evil) execute locally with some user privilege
- It's definitely going to happen at some point, especially in old softwares like flash having it's constant problems

**Isolation based sandboxing**:
- Run each application in an isolated sandbox environment
- Can access the resources only in the sandbox (cannot access external data)

## System level sandbox:

This would be a complete environment for the Operating system. It's done using a virtualisation, using a hypervisor.  (VMware as an example)
You can multiplex hardware to run hardware level VMs

**TODO: Look up and read about virtualisation, it's in cloud computing as well**.

**Type A: Hardware Virtualisation**
- Guest does not need to know it's virtualised
- VMware, VirtualBox etc.

**Type B: Paravirtualisation**:
- Guest knows it's virtualised
- Guest can use specific APIs to increase performance
- example : Xen.

## Security and Virtualisation / Sandboxing:
- Cloud computing context
- One compromised application doesn't affect the other ones. Each OS has it's own OS stack and doesn't share resources.
- EXCEPT, WAIT A SEC, THEY SHARE HARDWARE!

**VMs share hardware**: This means they have a shared hardware cache, and shared instructions pipelines by the hardware / host OS.
This can be vulnerable in general, but you can even do things like side channel attacks via the shared resources.
This also means that if there's shared resources, you can DoS the other VMs by hogging the services etc.


**Limitations of attacks:** Since the attacks are side channels and hardware level resources based, it's not that trivial.
The attackers need to get lucky and ensure that they have co-tenancy in the cloud context (if that's the target). They people need to run on the same physical machine.

**How do i share co-residency?**:
1. Brute force it, but this costs £££
2. Placement locality abuse: This is basically focused on the fact that if you launch the VMs and create them at the same time, higher chance of being placed in similar locations. This works for localised in the worlds etc.
3. Forcing scaling: You can force scaling of both your target and yourself allowing higher chance that you'll share the VM hosts.


### Container Based Sandboxing:
- Share kernel but sperate user space resources
- More efficient performance!
- But containers don't exist in the kernel by defaultm so you use a combination of features such as namespaces, overlayFS(file system for this) etc. 
- Give the VMs the illusion of being alone in the VMs
- Attack surface is **much larger in this compared to full virtualisation**. 
- The above applications that are used to create this pseudo virtualisation may not be built for it. It could have faults and insecure systems. 

## UniKernel
It's a single address space machine image constructed using library OSs. Developer will select which features he needs and the OS will be built specifically to match those from a library of different functions. The idea is that this will run directly to a hypervisor or hardware
- It's generally light in comparison
- More "secure" than containers, and can trust the OS in this case. 
- However classical VM vulnerabilities (side channel attacks) are still present in this.

## SGX Hardware supported memory enclaves
SGX refers to Software Guard Extensions. They're a set of CPU instructions (built by intel) that allows user level code to allocate "enclaves" for private memory regions. 

Idea behind SGX is that running an application in isolation so it cannot be affected by other systems. This is done if you don't trust the OS or the Hypervisor, and implies that you only need to trust the hardware. However there are also faults in this system. (caches are still shareddd)

What SGX does is that it encrypts the data anytime it leaves the CPU. So if another system tries to gain access to the enclave, it's encrypted so cannot see the data. If they try and change the data, then the unencryption will fail and will alert the data how it's changed.

A lot of different applications are currenlty being tried to be run in the enclave, for the sole reason that it's hard for attackers to obtain or alter your data. While you're still prone to DoS attacks, the integrity and confidentiality of your data can still be maintained.

# Lecture 13: Hardware Root of Trust (7th Dec)
Trusted Computing: _How can we tell whether a machine has been compromised?_

To understand you have malware in the computer, you need to be able to oversee it's actions. For example if it's a malware application, then you want to be in the kernel. If it's a kernel malware then you want to be in the layer below that i.e. hypervisor / hardware.

That's difficult to do with a rootkit:

## RootKit

**Rootkit:** It's a computer program designed to provide privilge access to a computer while hiding it's presence.  It started off as a collection of tools for admin level access. Rootkits nowadays are associated with malware such as trojans, worms and viruses.  
They're variant at different levels, and can have multiple ones.
They can even infect your boot sector which means that formatting the OS woulnd't make a difference.

Imagine a malware X
- It may be a kernel module (like a driver)
- Could `ls` filter results to exlucde malware files, prevent deletion of files and prevent killing the process
- You cannot kill (or even see) the rootkit from above (if you're OS and it's kernel).

## Software approach to Trust

How can we detect a compromised system?
We want to remotely verify the **integrity** of the system

**Remote Attestation**: Method by which a host authenticates it's hardware and software configuration to a remote host. The goal of the attestation is to enable a remote system to determine the levle of trust and integrity of platform of another system. 

The flow of this is done like so:
1. Untrusted Prover "P" and trusted verifier "V"
2. V knows P's memory content (stack of software running on P)
3. V sends a challenge with a `nonce` to P (`nonce`: some random value )
4. P computes a checksum (hash it with the nonce)
5. V verifies the checksum.

What does remote attestation actually tell you?
- Positive Result : Correct memory content and device is okay
- Negative Result: May be malfunctioning, or maybe malicious device
- No Response: Similar to Negative result.

**Problem with this**: Basically what stops a rootkit from acting like it's all okay? Assuming that the rootkit understands what memory / application layout the V is expecting, it could instantly fake it (if it's at the kernel level) and send back a valid resposne but still be malicious.

### Return Oriented Programming Attack

**Return Oriented Programming:** (something a rootkit can do).
Basically this uses a similar point as buffer overflow. It's used to grab the return pointer to `libc` and therefore gaines access to the code in the computer. It **won't add any code itself** as that might break the checksum, instead it will find instructions that does what it wants and will chain these as needed to get it to do what it likes. 

- Powerful attack: Uses standard and well known and understood techniques. It's difficult to prevent
- Examples of this attack exist
- It's hard to detect if done well, and it's hard to remove as well.

Because of **ROP, we know Software Based Attstation is not possible / secure**

This is why we need hardware level attestation
## Hardware Approach for Attestation

We need to rely on hardware to provide some strong guarantee:
- Prevent booting modified image (secure boot)
- Proving integrity of running software (attestation)
- Protecting secret from a modiefied OS (sealing)
- Proving identity (authentication)

For example Intel SGX -> Sealed execution

### Static Root of Trust:
1. Provide a measurement of code at loading time. 
 It's basically hashing the code before loading
 stores the hash in a TPM register (seperated from the CPU, it's for security) (`tpm`: trusted platform module)
 Values can be used as a rpoof of the system
2. Secure Boot
  It's a fixed boot loader in the ROM, it contains a public key, will load the code and verify the signature with the public key. If it's a valid, then execute else halt.

**Problem against static root of trust**:
- It can verify only static information 
- If there's a long running application on the server but we need to test the integrity of the program this wouldn't be able to provide it.
- The runtime status of a device is not known. I.e. an attacker can compromise a system during execution
- Reboot isn't sufficient, an adversary can ensure that certain code doesn't run when it's safe booting.

**Solution to that problem:** SGX / ARM trust zones!

## Trusted Platform Module Based Computed (TPM)

A lot of programs and OS and computers come with a trusted platform module (`tpm`).

The TPM is used for
1. Disk encryption
2. System integrity
3. Password Protection 
4. etc

**what's the difference between Trusted Computing and Secure Boot?**:
Secure boot allows any signed software to execute.
Authenticated booting:
- takes measurement of the software being executed
- can be verified by third parties

TPM ensures that it's secure by:
1. Ensuring only windows associated programs will run in the first step
2. It runs an anti malware software before anything else to prevent a rootkit from taking over the anti malware
3. it only secures the boot process not the whole OS

### TPM Registers:
1. Platform Configureation Registers
2. PCR hold a summary of series of a value
3. A PCR register is extended. Shielded the TPM's location and cannot be modified from outside.

### TPM and Remote Attestation:
1. PCR Cannot be modified
2. TPM Contains a key to sign the attestation
3. Verifier verifies the TPM key and the PCRs


# Lecture 13: Blockchain (14th December)

Bitcoin uses these as the building blocks for it to exist:
1. Network protocols
2. Cryptographic functions
3. Game theory - Equilibrium / Economics

The unique factor in this is the innovative combination of the technologies.

## Proof Of Work

It uses **SHA256** as it's main factor, which is a One Way Hash Function that produces 256 bits.

An old spam filter used to require the user to complete 1000 SHA256 hashes of the message, and if the message verified correctly then they could post. Attackers would've wasted a lot of resoruces, whereas genuine users were fine!

Generating a SHA256 for the message is about identifying what values can create the SHA, and it's the proof of work. I.e. brute forcing the message acts as the proof of work.

Difficulty changes as the blocks go along in blockchain, to ensure that program can catch and run beyond the current longest change.

Proof of work converts into electricity consumptions, i.e this takes power to compute and therefore has a financial cost. If you work well, you get a reward.

Checking the last X amounts of transactions for the chain generates a reward as well. Anyone who confirms these transactions can add a little bit on top of the transaction for themselves.

## Transactions

Blockchain enabled bitcoin which is essentially an e-currancy with a **distributed** generation and distribution of money.

These transactions are :
- Irreversable
- Inexpensive
- Anonymous as they're done on a peer-peer network
- Broadcast in seconds and can be verified (added to the chain) very quickly
- You can verify the costs by using a **public key** and pay for something using a private key (signing it).
- Double spending is prevented using a **distributed ledger**.

**Important factor is the fact that these transactions are not anonymous, they're just pseudonymous, as each transaction can be traced and if you want to pull the money out of the network, you'd have to pull it into actual currency which would reveal you.**

Even the communication with the network is done over IP so that can identify you easily.

## Chain

The "Chain" in blockchain is a **public decentralized register/ledger**. 

It keeps track of transactions that transfer value from a sender to a recipent and this is protected by a signature.

The integrity of the ledger is verified by miners, using audit transactions, proof of work for consensus and the miners can give themselves a reward.

**What if two transactions are computed in parallel**

Then the two branches are computed on by different nodes/miners in the network, and if one of the chains becomes longer that's usually the one thats adopted.

Transactions aren't lost in this system, as they're still broadcast and will still be included in the chains that are "correct".

## How can i mine for some of that blockchain gold?

You'll need:
1. High computational resource
2. Cheap electricity
3. Good network access (fast mining and fast retrieving and fast sending)
