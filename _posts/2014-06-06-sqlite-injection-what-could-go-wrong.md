---
layout: post
title: "SQLite Injection - What could go wrong?"
description: "Examining the security issues with SQLite injections."
modified: 2014-06-13 17:05:54 -0700
tags: [technical, sqlite, databases, phase 0]
image:
  feature:
  credit:
  creditlink:
comments: true
share: true
---

As far as embedded databases go, SQLite is a popular choice. It’s a relational database management system that follows much of SQL standards. Since it needs no standalone processes, its library communicates and links with the server becoming an inherent component utilized by many web browsers. It’s ACID-compliant (Atomicity, Consistency, Isolation, Durability) and uses a dynamic yet weakly typed syntax. This is where things can begin to go wrong. That syntax doesn’t ensure the domain or database integrity.

<figure><img src="../images/syringes.jpg" alt="Three Empty Syringes" width="100%"></figure>

We’ve become more accustomed to hearing about security breaches and compromised databases. We think we’re protected by our favorite online shopping site or social network but then we receive the dreaded notice of hacks and prompts to update our passwords. While not all compromises are generated out of SQLite, it’s unfortunately a relatively easy program to manipulate and thus a popular option for those seeking to attack.

The typical embedded database, such as those utilized by web applications, populate its data when we enter in the requested information such as our names, email addresses and passwords. While that’s what we typically do, that’s not what an attacker does. Rather than inputting say, an email address, they can enter or inject a relatively simple line of code. That could prompt the database to output all types of sensitive data or even corrupt and bring down the database all together.

So how do we guard from such attacks? As consumers, we of course remain diligent with updating our passwords and selecting two-step verification when available. From the programmers perspective, there are also steps that can be taken to guard against such compromises. Website entry forms and consumer end-points can be coded to not just accept what’s inputted. Rather, they can utilize input validation techniques such as expected input matching and authentication based on defined rules such as length, type and syntax. They can also be coded to parameterize query APIs with placeholder substitution markers. Finally, programmers and companies alike can utilizing encryption of the data. This way, regardless of  where the compromise generated, the stolen data would be less useful.

### Learn More

Database security is of course a big topic that needs constant attention and diligence. If you’re curious to learn more about SQL, SQLite and injection issues, check out these articles.

* [Wikipedia - SQLite](http://en.wikipedia.org/wiki/SQLite)
* [Tutorialspoint - SQLite - Injection](http://www.tutorialspoint.com/sqlite/sqlite_injection.htm)
* [Code Project - SQL Injection Attacks and Some Tips on How to Prevent Them](http://www.codeproject.com/Articles/9378/SQL-Injection-Attacks-and-Some-Tips-on-How-to-Prev)
* [ProgammerInterview.com - Provide an example of SQL Injection](http://www.programmerinterview.com/index.php/database-sql/sql-injection-example/)

There are many steps that can be taken by programmers to safeguard the applications they write. Being aware of, and taking measures to guard against malicious SQL injection attacks is one even new developers can utilize.
