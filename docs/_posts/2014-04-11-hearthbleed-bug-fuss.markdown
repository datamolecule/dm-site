---
layout: post
title: "What is this heartbleed bug and what is the fuss all about?"
date: 2014-04-11 00:00:00 -0800
categories: [security]
---

# What is this heartbleed bug and what is the fuss all about?

![What is this heartbleed bug and what is the fuss all about?](/assets/images/heartbleed_header.png)

Let me tell you a story. It’s a story about Alice and Bob, playing a game just like the telephone game you probably played as a kid. This is more or less how it goes. \*

The rules of the game are simple. There are only 3 steps to win this game.  
1\. Alice sends a message to Bob.  
2\. Bob sends the message back to Alice.  
3\. Alice compares the message received from Bob with the one she sent. If they are identical they win the game!

Now, this is where it gets complicated. You see, Alice and Bob are actually computers and they are not very smart so someone had to tell them exactly what to do. So the two following rules are added to the game:  
1.1 The number of characters in the message must be sent.  
1.2 The message can’t be longer than 64K characters.

This is a sample message for Alice to Bob:  
9 characters; “All Good!”

![Message exchange between Alice an Bob](/assets/images/heartbleed_alice.png)

Message exchange between Alice an Bob

Bob unfortunately is very distracted. This is because he keeps on doing a bunch of different things while playing this game with Alice. He needs to write things down so he doesn’t forget what Alice told him. Luckily he carries a little black board all the time with him so he can jot down notes. On this board he writes down everything that comes his way, both work and play.

Alice can send a short message like “Hi Bob”, she can also send over a poem she wrote or part of a chapter from her favourite book. This is because the rule of the game says that she can send thousands of characters in her message to Bob.

So Bob listens carefully, finds a place on the board where he can write things down and gets going. When the board is full, he finds a place where he can erase what was there before and then starts to write down the message from Alice. First the number of characters in the message followed by the message itself.

So far so good. But remember, Bob is distracted, he’s multitasking and playing all those games all the time so just to make sure he doesn’t freeze like a deer caught in the headlights while playing the game with Alice, he writes a reminder in the corner of his board. Something like this.

How to reply when playing the telephone game:  
1\. Read the number of characters, write it in the reply message.  
2\. Go to the beginning of the message and copy as many characters as read in step 1 in the reply message.  
3\. Send the message!

Sounds simple, and it is. But it is also tragically flawed. This is where the problems begin.

Along comes Oscar, he starts chatting with Bob and wants to play the telephone game too. Bob, not one to refuse such an invitation tells Oscar: “Go ahead, I’m listening.”

Here is what Oscar’s message looks like:  
64K characters; “What do we have here?”

![Message exchange between Oscar an Bob](/assets/images/heartbleed_oscar.png)

Message exchange between Oscar an Bob

So Bob gets busy, he looks around for a nice spot on his board to write this down. Then he goes back to his note and proceeds according to the plan. Copies the number of characters in the reply, 64K, then he starts counting along as he copies the message “1 W, 2 h, 3 a, etc.”

Here it dawns on you that something might be wrong. But Bob doesn’t and he goes on and on “17 h, 18 e, 19 r, 20 e, 21 ?” and he doesn’t stop there. But doesn’t the message end here? Well yes, but Bob is following his instructions and he just keeps going, copying thousands of characters from his board into the message he is about to send back to Oscar.

But what about step 3 then, the message Oscar will receive will not match the one he sent and the game will be lost. Sadly no, because Oscar is playing a different game. Although for Bob it seems just like he was playing a game of telephone, Oscar plays the panning for gold game. When you pan for gold, you know you will get loads of mud most of the time but once in a blue moon you might get a tiny nugget of pure gold in there.

So what does gold look like on Bob’s black board? Well, you see, Bob is not actually playing telephone games all day long. He also has a full time job. He is part of the team that works on encrypting secrets as they travel around on Internet. Part of his job is to handle encrypted data.

You know what they told you, that your data was safe and encrypted as it travelled around the Internet? Although that is usually true, Bob’s job is to sit at the other end of the tunnel and decrypt the sensitive data before handing it over to the web server. It can be serious data like your tax filing, not so serious data like cute kitten pictures and it can also be your login name and passwords. Doesn’t matter, for Bob it’s all the same.

So where does Bob keeps all of that sensitive data while he is busy encrypting and decrypting? He keeps it right there, on his little black board, next to that sneaky message from Oscar and this is what the fuss is all about.

## Epilogue

So what can you and me do about this? Not much I’m afraid, not directly at least. What system administrators can do is upgrade the instructions followed by Bob, so he won’t reply to the heartbeat while playing the telephone game when the length of the received message doesn’t match the number of characters specified or tell Bob not to play the telephone game anymore.

What can we, as users, do to mitigate the impacts of this bug? First is to identify which sites we are using that were impacted and once the problem is fixed on those web sites, go there and change our password.

Next, and this has got to be the moral of the story: you need to use a different password for each web site where you have an account. This way, if your password is found on one compromised site, it will not open the door to the rest of your accounts.

> The moral of the story: you need to use a different password for each web site where you have an account.

\* Give or take a considerable amount of simplifications. Read this one more time before going back to the text. Seriously.

# Further reading:

[The messenger and the source of the bleeding heart image](https://heartbleed.com/ "The messenger and the source of the bleeding heart image"): https://heartbleed.com/  
[Interactively test a site](https://filippo.io/Heartbleed/ "Interactively test a site"): https://filippo.io/Heartbleed/  
[How serious is it?](https://www.schneier.com/blog/archives/2014/04/heartbleed.html "On the scale of 1 to 10, this is an 11."): https://www.schneier.com/blog/archives/2014/04/heartbleed.html  
[The responsible code explained](https://blog.cryptographyengineering.com/2014/04/08/attack-of-the-week-openssl-heartbleed/ "The responsible code explained"): https://blog.cryptographyengineering.com/2014/04/08/attack-of-the-week-openssl-heartbleed/  
[Ongoing coverage](https://arstechnica.com/search/?query=Heartbleed "Ongoing coverage"): https://arstechnica.com/search/?query=Heartbleed  
[What is likely to be the next step](https://en.wikipedia.org/wiki/Perfect_forward_secrecy "What is likely to be the next step"): https://en.wikipedia.org/wiki/Perfect\_forward\_secrecy

