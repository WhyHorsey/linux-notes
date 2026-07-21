**Date Started:** July 2026

---

# 🔑 Why SSH exists

Ok, before we talk about commands, algorithm, math and such, let me ask you a simple question first.

Imagine, you have a computer in America, but your **server** is in, let's say UK.

How do you exactly access this server?? Well, simple enough you might say, we just provide it with our good 'ol username and password... right?

Now look, that's not entirely wrong, even I think like this beforehand, but... let's address the **biggest** problem we're having with this method.

That problem is that... the password and username you send, is being sent through the **internet**. It's not actually a direct connection to your server, no, in fact, it's more like... this:

Laptop ---> Home router ---> ISP ---> Router A ---> Router B ---> Router C ---> Your server.

Yeah.... it took quite a long time to get there, does it?

If you still can't see the problem, here, let me give you an example.

Imagine if someone, somehow gain access to the information that are tranfered troughout this router, what do you think they gonna do??

Well, not somehting good for you, **definitely**.

Let's use a letter as a example.

You sent a letter to your server, containing your precious username and password.

Now, here's the thing, everyone who have access to that letter can read it if they want.

The postman, the courier, some people that you might not even know.... everyone.

How do we solve this issue? Well, the simples solution is to just sent the letter wih a safe deposit and lock it. That way the courier, or anyone who tries to interract with the letter, can still see it being delivered but not actually know the content. This is called, **Encryption**

So really the problem is not that our password is sent through the internet, it's just that, if the message just contain a plain text like: Password123....

This means, everyone who can see the message being the delivered can also see the content. Meanwhile, if it's encrypted like this for example: 8F3A90AB1C0D98...

Then, what they can see now is just an abstract string of words.

But now... you may have another question... how do exactly, the server in this case, **decrypt** those encrypted message??

If we continue with our letter example from earlier, after we sent the letter with a safe deposit box and **lock it**, the server now also need the **key** to open those safe box, 'cause if it don't open it... well, you wouldn't have access to your server anymore.

But... how do we actually sent the key? If we just sent it with our letter, that's just the same as before.

Everyone now have access to the content of the letter, because that safe box is useless now.

This is one of the biggest problem in the world of computing for years!

They constantly trying to make a way for two computers to have 2 of the same "secrets".

Or, more accurately, how to make two computers can have the same **key**, without actually sending the key??

This is where **SSH**, or **Secure Shell** comes in. Through it's incredible and magical "key". 

**Public Key** and **Private Key**.

---

# 🔐 Public Key and Private Key 

The first time I learned about this concept, I was in... complete disbelief.

This is honestly something that shouldn't have work, but somehow it does anyway.

So remember our problem with the letter right? We sent the letter with a safe box but to open it, the receiver needs a key, the same one used to lock it.

If we sent the key alongside the letter, than what's the point of securing our letter in the first place? (lol).

But imagine if there's someone in the faraway land, deep on the mountain.... that are able to create a special, kinda weird padlock .

This padlock is not weird because it's shape or something, no, this padlock is weird because its unique nature/trait. This "padlock" apparently has a rule.

The rule state that, everyone can have a copy of YOUR padlock whenever they want, and you... shouldn't worry too much about it.

Because this particular "padlock" can only be open with ONE key, unique to you. Only **you** have this key in the entire world.


















 




