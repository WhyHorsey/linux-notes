**Date Started:** July 2026

---

# 🤔 What is Git 

I didn't know about this at first, really, heck I've never even heard about just "Git" before. 

But it turns out, it actually became something that I use pretty often and wanted to learn more about. 

Before that though, we need to understand what Git is, and as for what I already meantion on previous chapter, this will not be like a "guide" or "git 101", this is more of like my journey learning, more than anything.

So, what is Git? 

Think of Git like a tool that keep snapshot of your work

Git records snapshots of the changes that you choose to "commit", like for example, deleting something, fixing a typo, or adding a new file. So, instead of saving only the latest version of your project, Git keeps a history of snapshots that you can go back to whenever you need.

The folder of your work or project is called **Working Directory**, think of it like your workspace, and once you happy with your current work right now, you can then tell Git which changes you want to include in your next snapshot, your next "commit". This place in which you tell Git is called the **Staging Area**.

Think of it like this, imagine you doing a photoshoot, then in **Working Directory** you're in the phase of "finding the pose", it hasn't been photographed yet, you just working on your pose right now, before finding the "right one". **Staging Area** is the phase where you already find the right "pose" and the photographer is finally decide to "shoot" it. After the shooting process, the "photo" then are printed out and be prepared to be added to the "album", this is called a **commit** and the album in this case is your local Git repository (`.git`).

When you feel ready, then you can upload your "album" to GitHub, think of it like a copy of your album in this case, because if GitHub is down or your internet is down, you still have all of your "photo" in your "album". This process is called a **push**. It's not the same as saving it, because, Git actually didn't just throw out those snapshot once it has been commited, Git actually stored them locally on your computer. What this mean is that, if wanna "go back in time" cause you don't like your new "photo", you can just go back to your previous snapshot, your previous **commit**.

That's is basically the "basic" of Git is, and honestly even to this day I'm still learning. The photograph analogy maybe not technically perfect, but it made the concepts click in my head.

At first I thought Git is just "GitHub in the terminal" so why would I learned it if I can just use GitHub?. I couldn't understand why people kept telling me to learn Git when GitHub already lets me upload files through the browser.

Well, turns out, y'know...... it's more than that. Git and GitHub solve two completely different problems. 

And I'm honestly so excited to learn more.

## Why Git Exists

Imagine you're working on a project right, let's called it, like `program.py` or something. 

So one day you decide to edit your project and done for the day.

But the next day you found just a little "something" that's bugged you out, so, you changed it, and done for the day.

The next day, oh boy would you believe it, you found an even bigger "something" that reaalllly bugged you out, so again, you changed it.

And so on and so forth..... but what if you don't like the new changes in your current project? What if you wanna go back because you realize that it's already good and complete beforehand???????

You.... unfortunately can't, because your computer and your program where you make your project, probably only keeps the latest version of the file. Once you save your changes, the previous version is usually gone unless you made a backup yourself.

So, for your next project, you decided to make every change you make on a diffrent copy of your project so whenever you feel like to go back, you can do it.

But..... it creates another problem, cause your folders probably look like this......

`program-final.py`
`program-final-fix.py`
`program-final-real.py`
`program-final-real2.py`
`program-final-real2-fixed.py`

Yeah.... it looked like a complete mess.

So, that's where Git comes, it completely solve all of this problem because if you don't like your latest commit, you can just.... go back. 

It's really that simple.

I, and probably you, at first maybe thought Git exists because some programmers want an easier way to upload to GitHub, but Git was actually solving a completely different problem long before GitHub existed.

---

# 📁 Creating My First Repository 

Now, after all of that, let me tell you how I finally made my first Git repository.

Well... after accidentally running `git init` in the wrong directory a couple of times.

Turns out, that hidden .git folder really matters (lol). 

First thing first, I need to create a folder where I will stored all my future and current projects.

To do this is simple enough, of course you can do it in your file manager, but that's not really in the spirit of this whole Git thing y'know? Also it's actually, believe it or not, become more convienient to me to just do everything on the terminal. I know, crazy. Is this what linux does to mentally stable people? 

Anyway enough rambling, so I open my terminal and create a new directory using the `mkdir` (make directory) command.

Then, I enter newly created directory using the `cd` (change direcotry) command.

In this direcotry I create another folder again, this one I named "linux-notes" (the one you're reading right now).

In that folder, I then create my `README.md`. 

For the longest time, I actually don't know what README actually mean or why it exist on every repository on GitHub (even outside it).

`README.md` is basically like a introductory to your project, you can explain what the goal of your project, how it will be maintained, how it works, etc. See my README.md if you want an example.

It's the first thing people will see on your repo, so not only you should make it easily explain the purpose of your projects, you should also persuade anyone who even willing to go to your repo in the first place of why they want to continue looking.

You can create `README.md` in your terminal using the `touch` command, it basically a command to create a text file, in this case a "markdown" file.

You can then edit it using the text editor of your choice, there's a lot of them, so just pick and choose. Or you can just use `nano` which is the default text editor for a lot of linux distro. Bonus point if you're using `vim` and tell everybody that you use it (jk lol).

After a short editing, I finally ready to create my own Git repository (locally at least). To do this turns out I just need type in `git init`. Git then will create a 
.git folder in my directory. This folder is where Git will stored all of my project history, all of my snapshot. Think of it like the brain of your repo.

Now, this is not what I though the first time I run this command (of course lol). At first I though it just somehow "connected" my projects to GitHub, but turns out, what it really does is very simple.

I also realized a very handy command that turns out, everyone who uses Git, used it almost everyday.

The command is `git status`. What it does is really simple, and you maybe will say the first time you see it that it's not really that important in the grand scheme of things (at least that's what I though).

It purpose is basically to show the current status of your repository at that time. Sounds really not that important right? 

But when constantly makes changes to your repo, you DO want to know what the state of your repo when you in the middle of creating that changes. 

Not only it gives a peace of mind when something goes as planed, it also become your safety net in case you make a "mistake". For example, if it turns out theres a folder in that you don't want to commit but it still come along, you can now safely removed it before commiting.

After I check my repo status to confirm nothing goes wrong, only then can I add it to my Git repo using the `git add` command.

`git add .` will add all my files while `git add <my-files>` will add only that spesific file that I choose.

I then run `git status` again to make sure everything is right.

And finally, I can run the `git commit -m` to finally commit my first file to my Git repo. A quick tip, you can actually name the commit that you make, for example `git commit -m "example'`. I recommend you do this 'cause it will save you a lot of time when viewing your repo commit history. A good commit message should describe WHAT changed, not WHY you're committing.

But.... we're not done yet, the files have only been commited to our local repo, so if we want to upload to GitHub we need to "link' our GitHub repo with our local repo. We.... will save that for the the next chapter because I think it's more appropriate to talk about uploading my file to GitHub in the "GitHub" chapter.

After this, my workflow is basically....

Edit file ---> `git add` ---> `git commit -m "the name of this commit` ---> `git push` (we will talk about this later).

You don't, and I repeat, don't need to run `git init` anymore, especially when you run it in the wrong directory (yes I'm talking to you, WhyHorsey from 2 days ago).

## Common Git Commands 

| Command       | What it does                                                              |
| ------------- | ------------------------------------------------------------------------- |
| `git init`    | Initializes a local Git repository by creating a hidden `.git` directory. |
| `git status`  | Shows the current state of your repository.                               |
| `git add`     | Stages changes for the next commit.                                       |
| `git commit`  | Creates a snapshot of the staged changes.                                 |
| `git log`     | Shows the commit history.                                                 |
| `git diff`    | Shows the differences between versions of your repository.                |
| `git restore` | Restores files to a previous state.                                       |

There's a lot more command than this, but as I said from the very beggining, I'm also still learning, so I still have a lot to learn myself. But hey, at least we're learning together.

As for other commands that I do know but decide to not show here like, `git push`, `git pull`, `git clone`, `git remote`.....

I will explain them in the next chapter which is ........

---

# 🌐 GitHub 

As many of you, I really though that Git and GitHub are just the same thing, but after learning and explaining how Git works, why it exists, and the use case of Git in the previous chapter, I'm sure you, and even I if my memory somehow erased by now, will probably starting to understand what GitHub really is.

GitHub is basically a server to host and upload your local Git repository. Think of it like this:

Git ---> MS Word/Documents

GitHub ---> Google Drive

Pretty simple right?

After finally understanding all of that I think I'm ready to finally "publish" my repository to GitHub. 

But first I need to introuduce to the gloriou SSH key and how it connected to your GitHub authentication.

Now, I will actually talk about this more in depth on different notes altogether, so keep that in my mind. However, I will still try to gives you a rough idea of what is SSH key is based on my understanding and experience. We will mostly talk about the "key" here, because that's what relevant to our case here of connecting to GitHub.

If you heard of home server and self-hosting, you might be familiar with the term already because it's everywhere in that community. So, when I learn about them for the first time, I just think they're just one of the component of building a home server and nothing else. But the more I learn about them, the more I actually become amaze about what they can REALLY DO.

Think of SSH key like a two-piece "padlock" system that allows you to open a secret "door" without needing a password. Instead of one metal key, it uses two special "key" that are mathemathically related (don't worry too much about it, for now at least), a Public Key (the lock) and a Private Key (the precious secret key).

Public Key ---> This is a "padlock" that you can make copies of and give to anyone. You throw this padlock onto the remote door (in this case GitHub). Everyone can see it, but having the lock doesn't let them open the door.

Private Key ---> This is the one and only physical key that fits perfectly into that padlock. You must keep this safely hidden inside your own computer and never show it to anyone.

You might see what I'm going with this, so essentially you give GitHub your public key. Later, whenever you connect, GitHub sends your computer a random "challenge". Your computer then uses your private key to create a digital signature proving that it owns the matching key pair. GitHub can verify that signature using your public key, without ever seeing your private key. Why it can do this you ask? Well it deserves it owns notes, because seriously, it will blow your mind (it did to me).

This is all for, well to secure your account and repostory of course, because if you don't have a way to authenticate yourself, anyone can just edit and upload nonsense to your repo and account as long as they link the proper url.

So, after learning that, of course I immediately decided to setup it.

And surprisingly enought, it went pretty smoothly.

First you need to actually make a GitHub account if that's haven't clear enough.

Then I found that I need to run the command `ssh-keygen -t ed25519 -C "emailgithub@example.com"` to generate a SSH key. The reason for why I want to use the `Ed25519` algorithm is....... that's for another day. (I actually didn't know the difference between all of this algorithm lol, at least not yet).

After I run those command, turns out it will create a .ssh folder in my home directory.

It then prompt me to create a passphrase, now look, this is optional, but whenever I see a security feature there's just an itch in my brain to immediately use it. (I think Windows and all of it's malware and data leaks kinda traumatize me a bit lol).

Now I need to run the SSH agent, which basically act like a y'know, agent to "help" you so you don't need to enter your passphrase over and over again when trying to connect to a server.

A simple `eval "$(ssh-agent -s)"` will do the job.

Now I just need to add the key, by using the command `ssh-add ~/.ssh/id_ed25519`. If you create a passphrase, then you need to enter it here.

And..... basically done, I totally didn't expect for it go so smoothly. Now I just need to copy my public key to GitHub, and I'm fine.

After that, I just need to test it if works by using the `ssh -T git@github.com` and finally, the message that I was waiting for "Hi WhyHorsey! You've successfully authenticated..."........ 

It's just feel so good.

Thatt is certainly a long one, but after this, we actually just need to connect our repo to GitHub using the `git remote` command, I just need to run `git remote add origin git@github.com:youraccount/example-projects.git` and will do the rest for me.

Now I just need to run the final command to finally.... upload my repo to GitHub.

`git push -u origin main`...... and then when I check GitHub, it's there. My repo is there!!!!

That's honetly feel soo satistfying and I don't know why, maybe it's feeling of completing a task, or a feeling of understanding new things, or maybe just a feeling of realizing the first step towards something greater than this.

## Command Breakdown 

| Command       | What it does                                                                      |
| ------------- | --------------------------------------------------------------------------------- |
| `git push`    | Push (upload) your local repostitory to GitHub.                                   |
| `git pull`    | Pull new changes made onto your GitHub repository to your local repo, merging it. |
| `git remote`  | Connect your local repository to you GitHub repo, basically set it's destination. |
| `git fetch`   | Same with pull but only downloads the data. You must manually merge it later.     |
| `git merge`   | Merge changes from another branch into your current branch.                       |
| `git clone`   | Downloads an exact copy of an existing GitHub repo onto your local computer.      |

For `push`: 

Edit file
     │
     ▼
`git add`
     │
     ▼
`git commit` (Local Repository (.git))
     ▼
`git push`
     │
     ▼
GitHub

For `pull`:

GitHub
     │
     ▼
`git pull`
     │
     ▼
Local Repository

For `fetch`:

GitHub
     │
     ▼
`git fetch`
     │
     ▼
Local Repository
     │
     ▼
`git merge`

---

# 🪾 Branches 

This will be a doozy one, because I myself is confused by this subject for quite some time.

So, I think we need to start with understanding branches first.

Imagine you have a repository, and in it, there's a `README.md` and a `program.py`. Your'e already commit a few times so, like, commit A, then B, then C and so on.

Suddenly, one of your collaborator comes with a request to make, let's say a "dark mode" to your `program.py`.

Ok, that's fine and dandy, so anyway, your started to code.

But it turns out, that implementing that dark mode, requires a lot more than you think.

You maybe need to change the UI, config, database, etc. So now your'e program is a mess.

Butttt.... here's the thing, there's still some people that are using the latest commit on your "main" branch, so if you continue to commit on it, the latest version that are stable right now, are now become unusable.

The solution to this before Git is to do.... whatever this is....

`program/`
`program_new/`
`program_new2/`
`program_darkmode/`
`program_darkmode_fix/`
`program_darkmode_final/`

Yeah, I'm not a fan of it. This is essentially the same problem with in the previous "Why Git Exists" chapter, but this time it's not history, but rather, experiment.

This where branches comes in, soooo..... what exactly is **Branches**????

Think of it like a timeline different from your main branch. Like this for example:

        main
          ↓
A ---- B ---- C  
          ↑
feature-darkmode

When we make a new branch, or timeline, it still will be pointed to the same last commit that our main branch pointed at. Pay close attention because THIS will be important (trust me, I know).

So when does the branches, well, started to be branched???

If we let's say try to switch from our main branch to our feature branch, by using `git switch your-branch` command and started to make commit on those branch, we will have a graph of something like this:

main

A ---- B ---- C

feature-darkmode

A ---- B ---- C ---- D

Now, this is not entirely accurate because this seem like everytime we make a new branch, Git just copy the "up to the last progress" to it, but we will talk about that later in this chapter. Now let's focus on thi first.

When I know about this feature for the first time I thought it was soooo cool, because it's literally solve all of our problem from earlier.

Now if the user download the program from the main branch, they will still got the latest stable realease. Meanwhile, we still will be able to experiment with our feature without effecting the main branch.

And after we're done with our feature, we can just, "merge" it. And the result:

A ---- B ---- C -------- F
              \        /
               D ---- E

F is the commit, cause by the result of merging the feature branch with the main branch.

What if the experiment turned out to be not succesfull? Well just delete it. Main branch still not affected, life is good.

## Pointer

This where a lot of misconception comes, even I become sooooo confused when learning about this. A lot of people, including me, probably thinks that everytime we make a branch, Git just copy the progress up to the last commit and start from there, but if that's the case, well, it will require a LOT of storage don't you think? So how do think they circumvent this?? Ohhhhh boy, your'e in for a treat.

Ok, let's say....

          main
            ↓
A ---- B ---- C

"Main" here is just a label. That's it. Nothing more, nothing less. Right now it point to C because it was our last commit, but, if we make a new commit, for example....

               main
                 ↓
A ---- B ---- C ---- D

You can see that "main" now point to our latest new commit, which is D.

When we make a branch, Git just add a new label to our existing graph. When we commit on said branch, it's more accurate to illustrate it like this:

        main
          ↓
A ---- B ---- C
              \
               D
               ↑
feature-darkmode

Notice how, our main branch still pointed at C, meanwhile our feature branch now pointed at D. And also pay attention of how D is actually PART of C, why?, well guess what, turns out ALL of our commit is also a pointer (yes, this is completely blow my mind when I learn it lol).

So, for example right, commit C it's not just contain a file, it also contain that it "comes from commit B".

Commit B is the same, it also contain that it "comes from commit A". And so on....

So it's actually like this:

A <---- B <---- C

The arrow point to the **Parent**.

This.... literally flip my understanding of Git upside down, wtf kekw.

So back to our question earlier, when Git make a new branch it will NOT copy the progress we make to that newly created branch. Git just need to create a new label that point to the last commit, for example D, and when we or Git ask for it "history", D can just say, "well if you wanna know my history, just ask my parent." And so on until we comes to the earliest point in our commit.





















