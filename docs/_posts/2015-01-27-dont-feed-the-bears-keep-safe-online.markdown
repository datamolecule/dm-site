---
layout: post
title: "Don’t feed the bears… keep safe online"
date: 2015-01-27 00:00:00 -0800
categories: [security]
---

# Don’t feed the bears… keep safe online

Internet security habits to help you stay safe online: a different password for each account, thinking before you click and keeping an up to date system.

I like to think about information security as an iceberg floating in the ocean of Internet. Like a real iceberg, part of it is below the water surface, this represents the security of the infrastructure and the services that we use. From how administrators keep their systems up to date and diligently monitor logs for suspicious activities to the way management allocate resources to secure the assets under their responsibility. The other part of the iceberg, the one that is visible above the water line, represents the security of our devises and actions as a user. The difference is that there is generally nothing you can do about what lies under water, it is out of reach. What shows above the water however is mostly under your control and this is what I will be focusing on.

So what does all this have to do with feeding bears? Well, you have most likely heard of the two fellows being chased by a hungry bear. One of them complains about not having running shoes on and the other replies that even with running shoes the bear is still faster. Then comes the punch line “I don’t need to run faster than the bear, I just need to run faster than you!” The same could be said about your security online. Some people will run slower and be easier to catch than others; don’t be one of them, adopt good habits and don’t feed the bears.

## First habit – use a different password for each account

We all know how to come up with a [good password](https://www.schneier.com/blog/archives/2014/03/choosing_secure_1.html "good password") or even a [good passphrase](https://theworld.com/~reinhold/diceware.html "good passphrase") right? But they are hard to remember and a pain to type each time you need to access a service. Why not craft one perfect password and reuse it everywhere?

The main reason against reusing a single password across sites is that once you type it in and submit your password, you don’t know what the site at the other end does with your password. Is it properly filtered out of the logs and passed through a secure hash function? If the company gets hacked or a disgruntled employee runs away with the database and it gets posted online for all to see, what will the world find out?

If the email address associated with the account is stored in plain text or decrypted as part of the extraction process and the password is recovered, it gives the attacker a valid set of credentials to access all your other accounts using the same password, no matter how strong it is.

### Is your password weak?

Even if your password doesn’t make it to the “[Worst Passwords](https://splashdata.com/press/worst-passwords-of-2014.htm "Worst Passwords")” list like “123456”, the 2014 winner, seemingly robust passwords like “momof3g8kids” or “n3xtb1gth1ng” get sliced and diced [if the security of the site is weak](https://arstechnica.com/security/2013/05/how-crackers-make-minced-meat-out-of-your-passwords/ "if the security of the site is weak") behind the scene.
In the Ars article, the passwords were hashed unsalted with the MD5 algorithm, a legacy secure hash function now known to be vulnerable and “[unsuitable for further use](https://en.wikipedia.org/wiki/MD5 "unsuitable for further use")”.
Sample MD5 Hash
```
$ md5 -s "qeadzcwrsfxv1331"
MD5 ("qeadzcwrsfxv1331") = 3e93fb79e0970b6b8229ff8bec22d069
```
Also, contrary to what we [often read](https://www.usatoday.com/story/news/usanow/2014/05/21/ebay-breach/9368969/ "often read") in [the press](https://www.theguardian.com/technology/2014/may/21/ebay-urges-users-to-reset-passwords-after-cyberattack "the press"), passwords should not be encrypted by web sites operators, they should be salted and hashed.

Check out this short humorous video if you would like to know more about the difference between encryption and password in the context of user password management. Take it with a grain of salt too; [SHA-1](https://en.wikipedia.org/wiki/SHA-1 "SHA-1") is not so shiny anymore. In fact, it is already [on the way out](https://community.qualys.com/blogs/securitylabs/2014/09/09/sha1-deprecation-what-you-need-to-know "on the way out")…

[![](https://img.youtube.com/vi/FYfMZx2hy_8/0.jpg)](https://www.youtube.com/watch?v=FYfMZx2hy_8 "Don't encrypt passwords")

So what is the solution to remembering all those passwords? **Using a password manager**.

Not only will the application generate strong pseudo-random passwords of as many characters as you like using a mix of letters, numbers and special characters, it means you only need to remember 1 strong password.

One more reason to adopt this approach is that if you find out that a site you use was breached, you don’t need to scramble to change your password all around the Web. You only need to change one!

Going back to the iceberg analogy, as you don’t know what the maintainers of the site are doing with your password, choosing a different password for each account is the best approach to protect yourself.

### Bonus steps

- Want to go a little further? Enable 2-factor authentication

For high value targets like your bank, email, blog, etc. many providers offer 2-factor authentication. This is not 100% bullet proof, nothing is, but it provides an additional hurdle.

- Configure out of band communication channel

Some service providers allow you to configure a mobile phone number where a recovery code can be sent in case you need to reset your password, etc.

## Second habit – stop, look and think before you click

While we all value our privacy, identity thieves strike millions of people every year. In the US only, in 2013, an estimated [13 million people](https://www.geico.com/information/aboutinsurance/id-theft/ "13 million people") had their identity stolen. In this challenging environment, phishing is a persistent threat that takes aim at what is often referred to as the weakest link in the chain of security, humans. From the classic Nigerian scam to elaborate brand spoofing attacks, these are the once in a lifetime opportunities, the offers that are too good to be true, the urgent situations where someone of great authority really goes out of his way to save us from a certain doom.

> The human factor is truly security’s weakest link…  
> –Kevin D. Mitnick

Just like drivers often see pedestrians who boldly step across the street without a pause or even a glance, many web users will follow a link or click on a shiny object without any second thought of what is waiting for them once they reach their destination. Phishing criminals will go to great length to make it seamless for you to enter your personal information into their online forms, crafting sites that look similar to the legitimate site they are impersonating.

Be especially careful of links in unsolicited emails that claim to come from sites where you might, or might not, have an account. There are often spikes of such scam following tragedies that capture global attention or after a break-in at a big name company as criminals try to ride the wave and capitalize on the public awareness of the event.

Typical hooks often involve calls to give to phony charities or urgent request for you to login to a special portal in order to make sure everything is OK with your private information. This Visa information site also has great information on identifying phishing scams: [www.visa.ca/phishing](https://web.archive.org/web/20160813151404/http://www.visa.ca/en/personal/securewithvisa/phishing.jsp "www.visa.ca/phishing")

### What’s in a link?

One indication of malicious intention is the URL where the link takes you and the subtlety of the specification of the request. For example secure.bigbank.com and www.bigbank.com are two sub domains that belong to the owner of the bigbank.com domain name while secure-bigbank.com is a different domain name that could be under the control of a completely different organization.

The rules that define the precise way to interpret URLs found in publicly available request for comments (RFC) documents are notoriously complex. Even determining if an email address is valid or not is a treacherous exercise. You can take a look at this instructive and entertaining post to find out more about it: [I Knew How To Validate An Email Address Until I Read The RFC](https://haacked.com/archive/2007/08/21/i-knew-how-to-validate-an-email-address-until-i.aspx/ "I Knew How To Validate An Email Address Until I Read The RFC")

The RFC 3986 on the “Uniform Resource Identifier (URI): Generic Syntax” gives the following [example of semantic attack](https://tools.ietf.org/html/rfc3986#section-7.6 "example of semantic attack").
ftp://cnn.example.com&story=breaking\_news@10.0.0.1/top\_story.htm
The URI above “might lead a human user to assume that the host is ‘cnn.example.com’, whereas it is actually ‘10.0.0.1’.”

Sometimes the line is grey and it’s not obvious what you get into either like when the folks at How-To Geek ask “[What Happens When You Install the Top 10 Download.com Apps](https://www.howtogeek.com/198622/heres-what-happens-when-you-install-the-top-10-download.com-apps/ "What Happens When You Install the Top 10 Download.com Apps")” on your PC. In case you are wondering: “Awful things” is the answer and “Danger! Do NOT Try This at Home!” in bold letters is their recommendation.

### Bonus steps

- Create a short list of bookmarks for all the “high value” site you frequently visit

Instead of typing the URL by hand or following a link from an email, legitimate or not, always access high value target sites from your own bookmark.

- Setup a Virtual Private Network (VPN) if you use public Wi-Fi

If you are constantly on the road it might not be possible for you to wait until you get back home to connect to sensitive sites. In this case, it’s safer to access Internet through a VPN. This will help protect your privacy and will prevent some types of [Men In The Middle (MITM) attacks](https://www.darkreading.com/attacks-breaches/sslstrip-hacking-tool-released/d/d-id/1130449 "Men In The Middle (MITM) attacks").

## Third habit – keep your system and applications up to date

I was keeping the easiest habit for this last step! Today, your Operating System (OS) as well as the most sensitive applications installed on your computer have the ability to call home and either notify you or automatically update themselves whenever a new release is available. Keeping both operating system and applications up to date is your first line of defense in keeping secure. Fortunately, it’s mostly fully automated, yes!

Using an anti-virus and a firewall comes next. Keeping an anti-virus up to date and performing a regular scan on your machine is also critical because OS and application release cycles can be long and a zero-day exploit might have already slipped in. Finally, an application level firewall lets you decide which process can talk to the Internet and also which one can accept connections.

### Bonus steps

- Black list “some” of the bad guys, use a host file

For malware, spyware and adware to call home and report on their misdeeds and findings, they will often lookup the address of the server they need to talk to via a DNS query, just like your browser does when you type in a URL like www.google.com. Installing a custom [host file](https://winhelp2002.mvps.org/hosts.htm "host file") on your computer can short circuit this communication and at the same time reduce the number of tracking cookies that leak your browsing habits.

- Handle USB sticks with care

There are several problems with USB devices. One of them is that they might not be what they appear! What looks like a memory stick might actually turn out to be a keyboard. Skeptical? Check out the [USB Rubber Ducky](https://usbrubberducky.com/ "USB Rubber Ducky"). Social engineers are also known to _forget_ infected USB stick in strategically chosen locations at corporations they target. Any suspicious device should be handed over to your friendly IT department for [proper handling](https://superuser.com/questions/709275/what-is-the-danger-of-inserting-and-browsing-an-untrusted-usb-drive/709278#709278 "proper handling").

## Keeping the bears wild

Some security experts disagree with the bear analogy, the idea being that in the real world the bear will eventually come after you. One proposed alternative instead favors [collaboration amongst preys](https://web.archive.org/web/20150315050418/https://ha.ckers.org/blog/20100909/bear-in-woods-or-prairie-dog-ecosystem/ "collaboration amongst preys") in an effort to starve off the attackers.

Clearly, if our mailboxes are continuously the targets of spam and phishing emails, someone still profits from all those activities. This list of tips and habits can hopefully help keep bears wild and the rest of us running faster.
