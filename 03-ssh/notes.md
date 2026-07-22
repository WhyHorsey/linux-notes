**Date Started:** July 2026

---

# 🔑 Why SSH Exists

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

Here's an example, let say that I'm a **server** in this case.

You decided to sent me, the server, a message.

So, you pick up my weird "padlock" (because everyone can have a copy of my padlock), put your message, lock it, and then send it to me.

However, in the middel of delivery, there's a "person with evil intentions" to say the least, that are trying to view the content of that package.

He has the same padlock, well, everyone has it, but.... he still can't open the message, 'cause the **key** is still with me, and only THAT key can open it.

After the package is arrived, I, the server, can then just pick up my "key" to open the package and read the message.

This is basically the gist of it.

Why we shouldn't worry if our public key is known you ask?? Well... 'cause it's supposed to be PUBLIC, it's in the name, duh.

This is because the purpose of public key is to **LOCK** the content, not open it.

Ok, so now we have:

Public key ---> Lock
Private key ---> Unlock

This where the whole idea started to take shape. Before, everyone who has your key can use it to not only lock a content, but also unlock it.

But now, there's a system where everyone can have the same key that you have to lock a content, but only one key can unlock it, your key.

## Authentication

You might think that the problem is solved now right?!.... Well, I'm also used to be as optimistic as you do my friend.

Unfortunately though, things is not always fine and dandy.

Let use our example from earlier, I'm the server, you have my public key (my "padlock"), and you decided to send me a message.

The package is safely being delivered to me.... but in the middle of the road, there's someone who decide to "look" inside that package.

Now this fine, 'cause at the end of the day, only I have the private key to unlock it. But here's another problem.

What really stoping that person, to completely throw out that package and replace it with a new one??? And to make the matters worse, he also have my "padlock", so he can just lock it like normal and it become completely distinguishable from the real package.

The pakcage is sure will arrive to me safely but... how do I know exactly **WHO** sent that package??

This why ecryption of message is not completely solved all the problem, yes by using ecryption the perosn who didn't have the key cannot decrypt the message, but the thing is, encryption haven't fully addressed the problem of "who exactly send this message?".

The problem presented here is really the whole reason why this new "idea" was born.

If before we have public key to "lock" and private key to "unlock", then... hear me out... we use the private key first!!!

This... completely left me flabergasted when I first learned about this whole cryphtography thingy. Like, they can just do THAT?! They can be reversed????

Well.. yeah they can. And when that happens, the public key in this case is not act like a "lock" anymore, but instead act like a **verifier**. This whole concept is called a **Digital Signature**.

So really that pair of a key that you have, is actually have two functions.

Encryption, so the message cannot be read by others. And digital signature, so the receiver is sure of who sent the message.

### Digital Signature

Okay, let's not use a padlock analogy in this one, but instead we're going to use a more simpler example.

Imagine I want to... write a formal message to you, in this case. Now I have a stamp which can "indicate" that the message is signed by me.

Let's say the message is this:

"Transfer me $1.000.000.000 or else...

Signed

WhyHorsey"

Now look, that might be a bad example, 'cause I will DEFINITELY not threatened you for 1 million dollar... right? haha.. (*sweat nervously). 

But, joking aside... how do people exactly sure that it's me though??? I mean, you can find a stamp everywhere nowadays.

What's stoping people to just.... use my name????

So just a name is not enough, we need something that can only be made by **me**.

This where the second function of private key comes in, it purpose is to **signed** the message.

For example, I want to write a message to GitHub like....

"Hello GitHub

Signed 

A83F912B..."

The question is, can people just recreate that signature? No! because that signature is made using MY private key, which only I have in the entire world.

Now, here's another question, how exactly GitHub verify that it's really me? Well, this is where the second function of public key comes in, it purpose in this case is to act as a verifier to my signature.

Think of private key as a pen that can create a ink which contain a pattern that cannot ever be recreated. You singed you message with this pen like normal, because... it looked exactly normal on the surface. But on the microscopic level, there's a pattern that only that pen can create.

For public key, think of it like magnifying glass. Everyone can have this paricular copy of my magnifying glass, and whenever my message comes to them, they can then check the legitimacy of said message, using the magnifying glass to view the microscopic pattern on the ink of the signature.

This is why when you verify using your SSH on GitHub, it never ask you for a private key, you only need to gives GitHub your public key and whenever Git needs to communicate with GitHub over SSH, it can immediately know that it's you. On the authentication process GitHub basically ask your laptop to show prove that you are "real", then your laptop grab your private key to make a "signature" and send it back to GitHub, it then verify that signature using your public key, your magnifying glass.

If it's valid, then there's only one posibilities, (that is if your private key haven't been compromise), which is, you are in fact, the real owner of this account.

Now, here's some misconception that a lot of people, including me, have before. The thing is, GitHub never "see" you private key, you laptop only send a signature using your private key so GitHub can then verify it using our pulic key.

---

### Passphrase 

I mentioned a bit of the posibilities of you private key being compromise, or stolen.

Now if your'e someone responsible, you should not have this issue in the first place. But hey, bad luck happens, I guess.

But, what did you do in this situation though? Because as long as someone else also have your private key, it basically become kinda like identity theft.

Well, may I introduce you to the glorious **Passphrase**.

I'm gonna use another analogy to explain this thing (don't worry it's not the last one, kekw), so bear with me for a moment here.

Let's imagine private key as a... well a key. Your bedroom key to be exact. You put this key on the drawer in the living room.

It's fine most of the time, but if somehow, someone you don't want to enter your bedroom happen to grab those key, they can easily do the exact thing that you don't want them to do.

So... you don't want that, so you take the extreme case of over-reaction by putting that key to a safe box. Pretty normal. Nothing wrong here (lol).

Now, how do you open the safe box? Well, by using a password, or I more accurately, a **passphrase**.

Passphrase basically act as a safety measure to your private key file, because before you set up you passphrase, if someone just stole your private key, they can just immediately using it.

But now, they need to enter a passphrase, which, hopefully, is secure enought to make the thief gives up trying to open it. (seriously, try to make your passphrase as secure as possible).

This is now basically solved and all of our issue so far, and hoestly it's fine to keep it at that.

However, it becomes quite a chore to continously entering the same passphrase over and over again in a day don't you think? Especially if you have a lot of task that require you to make "signature" using your private key.

This where our last piece of "puzzle" play a part. **SSH Agent**.

Think of it like security guard to your safe box.

You give it your passphrase, and everytime a someone try to verify your identity, it can just enter your passphrase to use your private key, and then return it. It's that simple.

---

# 🔓 Generating An SSH Key 
































 




