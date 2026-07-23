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

Creating a pair of SSH key is honestly such a simple process, but I'm here gonna talk more about what actually happening behind the scene. 

But first, we need to generate our pair of key.

The command we will be using is called, `ssh-keygen`.

More importantly, we will be using the ed22529 algorithm (we will talk about this in-depth later). So the command should look like this, `ssh-keygen -t ed25519`

After we run those command, we were prompted to choose the location of where we will stored the key. It then will create an `.ssh` folder in our choosened location, containing our private key (`id_ed25519`) and public key (`id_ed25519.pub`).

Now... it's actually done, believe it or not. You might want to setup an ssh agent if you want (use the `eval "$(ssh-agent -s)"` command) but aside from that, your pair of magical key is good to go. If you want to setup an GitHub authentication using SSH, then just copy content your public key file to GitHub and.... just that actually, you don't need to do anything more (lol).

I need to remind you tho, if you somehow lost this file, from like accidentally deleting it, or your ssd corrupt, or.. something, you **DO** need to create another ssh key pair and revoke your old key in the service you are using to authenticate.

It also a good practice to have a different pair of key for different computer, 'cause if your laptop key is lost for example, then you just need to revoke that one key specifically and your other key, like your pc or server key, is still untouched.

## The Algorithm of SSH Key

Okay, now we're done of all of that, what is exactly `ssh-keygen` doing behind the scene to create those key??

Ohhh boy, buckel up, 'cause this is gonna be a wild ride. Seriously, this is, without a doubt, my "ohhhh, that's how it works???!!" moment lol.

What actually happen when we run those commad is that, `ssh-keygen` is not creating a two file, no no, it actually creating a two different set of **NUMBERS**.

If you happened to see what contained in your public and private key file, you will see a bunch of random number. I say "random" here, but, they're not actually **that** random either.

We're gonna talk about math here for a moment, I will try to make it simple (please don't go!!!!), but honestly you don't need to worry too much about it... I hope so.

For example, your private key, in a concept, is like this:

8173941739481749283819472917391....

It's a collection of numbers that are really loooooooonggggggg.

After it created this monster of a number, it then run an **algorithm**, an math operation that, when done, will be able to generate us our public key, which *based* on our private key.

Remember how I talk about ed22519 earlier? Yeah, those are one of many algorithm that you can use to do this process. The reason why we choose this particular algorithm though.... well aside from the fact that everybody is using it, the reason is really comes down that it is one of the most secure, lightweight, and fast public key algorithm right now available.

Ok, ok that's fine and all, but..... if we're basically creatin public key using the private key... can we just do the same thing but in reverse???

This is one of, if not, my biggest question when I tried to learn about this concept. Because, if you think about it, it kinda makes sense right??

If one number is created using a highly algorithmic mathematical operation based on another number, why can't we just run the same algorithm and reverse-engineering it?? Surely that's possible, right???

Well, not quite. You see, not every math operation has it's "reverse".

For example, for 5 + 7 = 12, sure you can "reverse" to 12 - 7 = 5. That's simple enough.

Another example, let's use a color right now. You mix yellow and blue to produce green, great. But, can you "reverse" green back to blue and yellow???? Yeah, that's what I thought.

We can't do this because **the information of the molecule of yellow and blue is already mixed.**

Crypthography is the same, they want to also create/search a mathematical operation that are like that. An operatiom that can create something fast and easily, but to "reverse" it, will take a huge amount of work and time.

Another example, this is more connected to the whole math theme going on. So, I give a computer a number, 123456789, and I want it to calculate, 123456789 mod 17.

It will give a pretty fast response... 1. Just like that.

But, if I now give the number 1... and ask it to "give me the starting number that's resulting in this number"....

Well, sure it can, but the result will be 18,35,52,69,86,......

Because all of that number is resulting in 1 if it mod by 17.

So, notice how, there's an **information missing here that the machine cannot processed**. That's really the reason why these machine will take a long time to calculate the "private key", because they don't have enough information, there's just no known efficient enough algorithm to recover the private key from the public key. Especially considering a huge amount of number that are posiible to the starting number.

Let's use another example finally (hopefully) gives you an understanding to these concept. 

Imagine you have a private key, and for it to "find" the public key, it needs to travel 1.000.000.000 steps. But, at long last, it arrive at the destination and find the public key. 

Now, if someone else see that, they can absolutely just concluded that, to find the "starting point" of private key, they just need walk back 1.000.000.000 steps right?

But how did they do that? Even if they can walk back 1 million steps, they cannot entirely sure if it's really the starting point. They just now the "end point" not the entire "track"

Now in theory, yes you can absolutely reverse-engineered yor way to find the private key, but buddy, it will surely takes a loooooooooonnggggg time. Probably even longer that waiting for GTA 6.... times 11 (kekw).

This whole problem is called, **"Discrete Logarithm Problem"**. If you want to understand about this topic more in-depth, then feel free to do your own research, that's a whole new rabbit hole of information.

Nowadays, there's not really a algorithm that are fast enough to reverse-engineered this whole mess. But, when that's happened, well, it will be an intresting sight to see.

---

# 🗞️ Challenge–Response Authentication

So now we know that, for a service like GitHub to verify our identity, it required our device to "signed" something using our private key.

What's that "something" you might ask? Well it's a "challenge".

Allow me to break it down for you. So whenever we tried to interract with GitHub using SSH, it sends our device with a series of "challenge", in this case, we will use this number as challenge:

928374982734987234

GitHub basically said "if you're really WhyHorsey, then please signed this number". It kinda like when you go to a secret club or something, and the security guard ask you to say what he said perfectly while holding your identitiy card (something that totally happened and relatable, am I right?).

After your device done signing those "challenge", it will send it back to GitHub who will then verify it using our public key, and... if it's valid, then we're in.

Important note here, when our device "signed" those challenge, it will create a signature for that particular challenge spesifically.

The challenge that GitHub sends is also random everytime we tried to authenticate.

Why? Well, 'cause if someone tried to intervened when the transfering of our signature and signed challenge happened, and decided to "copy" it, then it will become quite a huge problem, don't you think?

If GitHub and our device is not creating a random challenge plus a specific signature for that particular challenge respectively, then that person who just copy the message being delivered can now use that same message to authenticate to GitHub, and they will be in it with no problem.

But, with this current system, everytime we tried to authenticate, a new challenge is created and a new signature unique to that challenge is also created. After it's done verifying, that challenge and signature now is gone and will not be used ever again, becoming invalid.

This whole system is called **"Challenge–Response Authentication"**

And this system is not only for SSH, it's also on TLS, Windows Hello, Passkey...... it's everywhere.

## Known Hosts

So far we've been able to "solve" the issue of verifying our identitiy.

However.... it brings out another question, yes, GitHub, and any other service that are trying to verify our identity using ssh, **can** do exactly that, it's simple enough. But, how do **WE** know that the service we're in connection with, is the real one????

What if it's some malicious hacker trying to intervened in our connection, and disguised as the service??

This situation is famously called, **Man in the Middle** or MITM for short.

The visualisation is kinda like this:

Laptop

↓

😈 Hacker

↓

GitHub

The hacker, quite literally, in the middle.

Now, this not actually bad at all, why? Because even if they successfully disguised themselves "GitHub", they didn't actaully have GitHub *PRIVATE KEY*!!!

Yes, it turns out, GitHub, and any other services for that matter, is also have a pair of these magical keys (lmao). It's..... aghhh I don't even know why this fact didn't even registered to me sooner lol.

Anyway, because of that, everytime we "contact" GitHub, it actaully show its *public host key* to our device, our device then verify that key by matching it to our saved **"known host"**.

When we created our SSH key, and connecting to a server for the first time, SSH will generated a file on our system called "known_hosts".

It usually stored in `~/.ssh/known_hosts`, but honestly it depends on where you stored your shh file.

This file, is basically, as it named suggest, listed off a bunched of server that we have connected before along with its "public host key" and its "fingerprint" which, in simpler term is the "summary of the host key". If you think the host key as 500 page book, then the fingerprint is like the ISBN.

When we tried to, for example, push our local repo to our remote repo to GitHub, our device will then check if the "fingerprint" of this server right no, is the same with the one in "known_hosts". If it's different, turns out SSH will also give you a warning (how nice), by telling you "🚨 WARNING!!! REMOTE HOST IDENTIFICATION HAS CHANGED!" or something like that, I actually haven't gotten this message at all (fortunately, lol).

When this happened, there's two possibilities, either GitHub changed it's public host key, or it's a malicious person trying to disguide themselves as GitHub.

The first one is likely not the case, because even if GitHub does changed it host key, usually they will, y'know, inform their community and user about it.

The second one though.... ho ho ho... yeah, it's probably the second one.

If that's the case, then what you should definitely do is NOT trying to remove your list of "know_hosts". Like, really, please.

Now, what if it's your first time connecting to a server though??? And at the same time, a malicious hacker is also trying to diguised themselves as that server... what did you do???

There's unfortunately, no available way for SSH itself to automatically solve this problem.

This is because our device is not yet established a "connection" to this server, so there's no known hosts to use as a base of verification.

Before you connected through ssh, it will prompted you with this message:

"The authenticity of host 'server.com'

can't be established.

Fingerprint:

SHA256:xxxxxxxx

Continue?

yes/no"

If you click yes in this case, and it's turns out the server is actually just a disguised hacker... well then, good luck brother...

SSH use a system known as **TOFU**, or **"Trust on First Use"**, which mean as long as *you* stated that you trust the "host" it will then trusted those same host for as long as it has the same fingerprint.

Now, you might be, after reading this, feel like that SSH is bad now because of this... But, honestly, try to think of what of the chances of that particular scenarion happening. If you just an ordinary person living ordinary live and just cared a littleeeeee bit about yor network security, then you will almost defintely not encounter this problem at all.

Like, for this to happened, the hacker need:

-To be in your connection line,
-Can intervened with that specific line,
-Be able to disguised as a sever,
-And everything happened at the same time as you first time connected.

Yeah, I rather roll in my newest gacha banner instead of hoping that THIS paritcular scenario is happening (kekw).

This doesn't mean MITM attacks never happen though. They absolutely do, especially on compromised networks. It's just that, for most home users connecting to well-known services like GitHub over HTTPS and SSH, the first connection MITM scenario is relatively a myth.

If you're wondering why SSH doesn't simply ask GitHub every time whether its key is correct, remember that the whole problem is that we don't *yet* know if we're really talking to GitHub. If someone is already disguised as GitHub, then asking "are you really GitHub?" would just result in the hacker answering "yep, of course, trust me bro".

Ok, ok, but how do these server circumvent this??

Well, GitHub for example publicly put out its SSH host key in their documentation, and other server also probably do this as well.

One thing that I found really intresting, is that, some big corporation actually just already have a list of different fingerprint of different server, and every laptop employee is already known all it hosts since the beggining.

