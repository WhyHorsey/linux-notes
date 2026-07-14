**Date Started:** July 2026

---

# 📖 Why Linux?

I will be studying Cyber Security later in September, so, in preparation, I decided to switch from Windows to Linux.

Not because Windows is bad.

But because I started to feel like Linux was a better fit for what I wanted to learn.

Some of my reasons for switching:

- I wanted to understand the operating system more deeply.
- Many Cyber ​​Security tools run more comfortably on Linux.
- I prefer the open source philosophy.
- I wanted to learn more than just using a computer.
- Linux is HIGHLY customizable, which is just something that I can't do enough on Windows.

Now, to be fair, I was a bit scared. Switching something that you already used for a long time, especially your whole operating system on your computer for that matter, can be a bit daunting. This become more apparent by the "stereotype" that Linux already had, like "Oh, it's just for the tech enthuasiast" or  "Most program that you use CAN'T run on Linux", etc.

But, turns out... so far it's actually been fun.

But before we start, I think I need to preface that this is NOT a guide, this is just me explaining my experience and things I learned along the way on my Linux journey.

---

# 💻 Hardware

Laptop:

- ASUS Zenbook 14 OLED
- Intel Core Ultra 7 255H
- 32 GB RAM
- 1 TB SSD

Operating System:

- Fedora KDE Plasma

The reason why I pick Fedora, especially the KDE variant, is because is one of a few "leading-edge" distro, meaning it's stable enough in it's current form but also not entirely missing out on the latest update to the whole system. Unlike rolling-release distros that push updates continuously, Fedora strictly tests and stabilizes the newest Linux technologies on a rapid, predictable 6-month release cycle.

As for KDE Plasma, it's because it look a lot like Windows..... nothing more.

---

# 🚀 Installing Fedora

The first thing I learned was the Linux installation process.

Which turned out... it wasn't as scary as I imagined.

Before you install linux, you need to download the ISO file of your Linux distribution of your choice.

Then, you need to create a bootable usb. There's a lot of software that let you do this, but personally I use Ventoy since it allowed me to create multiple bootable usb.... with just one usb stick (isn't that so cool?).

During the installation, I learned several new concepts.

## Dual Boot

Dual Boot allows a single computer to run more than one operating system.

In my case:

Windows and Fedora.

When booting, I can choose whether to boot into Windows or Fedora.

Something that you need to be careful when dual booting though, is that you need to have both of your OS in separate drive.

For example, my C drive is entirely only for Windows (around 180 gb) meanwhile my D drive (around 750 gb) is where I stored all my data. 

When you dual booting, I recommend you shrink your D drive around 100-200 gb for your Linux OS, because usually when Windows rolls out a major update, it can messed with your other OS.

---

## Secure Boot

At first, I thought Secure Boot...... y'know,  just made booting more secure.

It turns out its function is to ensure that the bootloader and kernel being run are truly trusted by the firmware.

This way, malware can't easily insert itself before the operating system is running.

---

## Full Disk Encryption (LUKS)

This is one of the features I immediately activated, even though at that time I literally have no idea what it means, it's just seem like everytime I see a security-related feature, I immediately turn it on (lol).

Turns out, LUKS encrypts the entire contents of the Linux partition.

As a result, every time I turned on the laptop, I had to enter a passphrase before the system could read the SSD contents.

At first, I created a passphrase that was... pretty brutal, to say the least.

Now I understand why this passphrase is different from a Linux login password.

The login password only unlocks the account.

The LUKS passphrase, on the other hand, unlocks the disk contents.

---

# 🐧 The First Thing I Learned

## Linux is not Windows

The first thing I noticed the most... Linux doesn't force me to use one method.

Almost everything is changeable. And I mean EVERYTHING.

Desktop Environment.

File Manager.

Terminal.

Browser.

Even the shell.

At first, I was quite surprised that an operating system could be this flexible. But it also made me actually want to tinker on my computer (something that Windows definitely not really good at).

---

## Terminal

Before using Linux, I thought the terminal was "a black screen where hackers type quickly."

Now I understand. The terminal is just an application. The shell actually runs commands.

Terminal ≠ Bash.

Bash ≠ Linux.

They're all different.

Almost all the task that you can think of, you can do it on the Terminal. 

From installing and uninstalling software, editing files, making a new directory on your files manager, monitor your system, changes your system settings...... 

The point is, there's A LOT that you can do using the terminal, now, of course you can still not use it if you're really scared, but it's still a good idea to just learn the basic, hell, I went from not knowing how to use the Terminal to immediately opening it everytime I boot into my system.

---

## Sudo

One of the most powerful command in the Terminal is `sudo`, but when I start using Linux, I often just type `sudo`........

Without knowing what it meant. I thougt it's just y'know... another command.

But surprise, surprise, it's not like that,

"sudo" means running a command as the "superuser".

Linux intentionally doesn't give regular users full administrator privileges.

So every important action must be done consciously.

There's a saying in Linux community that the pro of using Linux is that, you control everything, and the con of using Linux is that, you...... control everything.

---

## DNF

In Fedora, software installation is done using DNF.

At first, I thought DNF was like the App Store.

It turns out it's more accurately called a "Package Manager".

DNF's tasks are:

- downloading packages
- installing dependencies
- updating packages
- removing packages

Examples of commands I frequently use:

```bash
sudo dnf install ----> to install package 
sudo dnf search ----> to search available package 
sudo dnf remove ----> to remove a file
sudo dnf upgrade ----> to update your system
```

---

## Repository

This concept has confused me for quite some time.

It turns out a repository isn't an application.

A repository is where DNF searches for software.

Fedora has an official repository.

Then I added:

- RPM Fusion
- Google Chrome Repository
- Flathub

Only then did I understand why Linux people always recommend installing software through the repository.

Because updates are automatic if you use the `sudo dnf upgrade` command. But there are some software that are just note available in the repository, so in that case, you need to use the built in "App Store" in KDE which called "Discover". If you want to update them though, you can still use the command line, `flatpak update` will do the job.

---

## RPM Fusion

This is one of the things that you must install imediately when using Fedora.
 
RPM is a package format.

DNF is the package manager that installs the package.

Similar to:

PDF → file format.

Adobe Reader → the reader application.

RPM Fusion however, is a community-maintained software repository that provides add-on packages that Fedora refuses to ship due to strict open-source licensing or legal patent restrictions.

Installing this enable you to install third-party software that are not allowed and deemed "proprietary", such as Steam and Discord.

---

## Flatpak

Flatpak is a different application distribution system than DNF.

The advantages:

- applications are easier to distribute
- newer versions
- runs more isolated

I currently use two software installation methods:

- DNF → if available in the official repository
- Flatpak → if not available or the developer recommends Flatpak

---

# 📂 Linux Structure

Another interesting thing:

Linux has a different folder structure than Windows.

There is no C or D drive.

There is only one root:

/

...

Then below that:

/home
/etc
/usr
/var
/opt

...

Windows is still accessible.

But it must be mounted first. To mount a file system or storage device in Linux, you attach its storage structure to a specific directory (called a mount point).

---

# 🔑 SSH

I also learned a lot about SSH.

I already know at first that  SSH was used for remote servers.

But, turns out...

SSH can also be used to authenticate to GitHub, and MORE!!!!!

SSH and SSH key is basically like "password" that you can use to "log in" to your system, but in a more secure way, since it used an alternative authentication method that uses public-key cryptography instead of regular passwords.

Today I succeeded in:

- creating an SSH key
- understanding public and private keys
- adding a key to GitHub
- trying the first connection

And finally...

```
Hi WhyHorsey!
You've succeesfully authenticated...
```

It genuinely feels almost magical by learning all of this things for the very first time.

---

# 🧠 The Most Memorable Thing

If there's one thing I've learned the most over the past few days...

It's not commands.

It's the Linux way of thinking.

Linux doesn't try to hide how the system works.

Instead... Linux actually invites its users to understand what's going on.

It felt more difficult at first.

But I find it much more fun.

It encourages user to actually tinker and try to understand their own machine, and by doing it, they learn a couple new things along the way.

---

# 📌 Things I Still Want To Learn

- Git
- Ricing 
- Docker
- Bash Scripting
- Networking
- Systemd
- SELinux
- Containers
- Home Server
- Virtual Machines
- Cyber ​​Security

---

This notes will be frequenly updated as I learned new things, so stay tuned! 🫡
