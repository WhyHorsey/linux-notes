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





