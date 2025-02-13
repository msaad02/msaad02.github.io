---
layout: single
title: "Coding on my Macbook with an RTX3090"
excerpt: "Explanation for ZeroTier, one of the greatest free services I've used, and SSH over WSL for self-hosted remote development."
toc: true
read_time: true
date: 2023-12-28
---

# Intro

Throughout college, I was a commuter, which meant long rides back and forth between school and home. I ended up coding a lot on my laptop, which worked fine — until I needed to run something computationally intensive. Fortunately, I have a desktop at home, originally with an RTX 2070, now upgraded to an RTX 3090.

The problem? How do I use my desktop's GPU while I'm away? Especially when I’m at school, completely off my home network?

You might be thinking, *“just make a home VPN,”* and you’d be right. I started down that path, Raspberry Pi in hand, when I realized my ISP uses CGNAT, which makes it impossible to port forward (or at least, I’d have to pay a monthly fee for a static IP). No port forwarding = no VPN = no remote access.

And then, the hero of the story appeared:

**Enter ZeroTier.**

# What is ZeroTier?

ZeroTier is a service that lets you create a virtual network between your devices, no matter where they are. It's like a VPN, but better — technically it is an SD-WAN (Software-Defined Wide Area Network). You can access your devices as if they were on the same network, even if they aren’t. I never knew this was possible, but it’s been a game-changer.

# How Does It Work?

ZeroTier works by creating a virtual network adapter on each connected device. You install the client, join your devices to the same ZeroTier network, and — boom — they can talk to each other just like they’re on the same LAN. No port forwarding, no static IP, no hassle.

I’ve even been able to RDP into my desktop from my phone while on a cellular network... Absolutely insane.

To give credit where it's due, TailScale is another fantastic service that does the same thing. TailScale is a bit more polished in some ways, and also free. They’re both great, but for my use case, ZeroTier has been flawless.

Once connected, your device gets a ZeroTier-assigned IP, which shows up in your network settings. Here's what it looks like on my desktop in Task Manager:

<img src="/assets/images/task_manager_zerotier.png" alt="ZeroTier in Windows Task Manager" style="height: 30em;">

I've removed the actual IP address, but it shows up in the network list. This is the IP I plug into my SSH commands to connect from my MacBook to my desktop. I also use it for remote desktop access, which is extremely useful when WSL isn’t cooperating with SSH.

# SSH Over WSL

I’ve been using WSL (Windows Subsystem for Linux) for the better part of a year now, and it’s been one of the best tools for development on Windows. Running a real Linux shell alongside Windows means I don’t have to touch Windows Command Prompt, which is already a huge win.

Setting up SSH in WSL is just like any other Unix system. I have OpenSSH installed, and I’ve configured my SSH keys on both my MacBook and my phone.

**Security Setup**
- Password authentication is disabled – It’s key-based authentication only for security reasons.
- MacBook firewall blocks all incoming traffic – Even if something were exposed, nothing gets in unless I explicitly allow it.
- ZeroTier isn’t always running on my phone – It can be a battery drain, so I only enable it when needed.

With these settings, SSH over ZeroTier is simple, secure, and rock solid.

# VS Code Remote Development

VS Code has one of the most mind-blowing features I’ve ever used: remote development over SSH.

I can SSH into my desktop from my MacBook, then open and edit files seamlessly in VS Code as if they were local. What makes this so good is that it doesn’t stream a GUI — it "just" syncs files and runs everything on the remote machine. No lag, no latency.

And it gets even better—VS Code handles auto port forwarding over SSH, meaning I can:
- Run Jupyter notebooks on my desktop but access them in a local browser.
- Use GUI-based ML tools remotely as if they were local.
- Debug apps with remote ports exposed automatically.

It just works. No manual tunneling, no extra setup — VS Code takes care of everything behind the scenes.

This entire document, in fact, was written through VS Code remote development — my MacBook is just the frontend, while my desktop is doing the heavy lifting. A side benefit is that my MacBook’s battery life is extended, since it’s not running any heavy processes.

# ZeroTier Reliability

I cannot overstate how good ZeroTier has been. In all the time I’ve used it, I have never—not once—had an issue. No dropped connections. No weird latency spikes. No random failures.

It’s one of the most solid, well-built pieces of software I’ve ever used. Combined with WSL and VS Code remote development, it completely changes the way I work. I don’t even think about it anymore—it’s just there, handling everything.


Even the smallest details make it great. Auto port forwarding, seamless cross-platform support, and absolutely zero hassle to set up. If I had to make a list of my all-time favorite tools, ZeroTier would be near the top.

# Conclusion

This post is mostly for me to document how I’ve been working lately, but if someone else stumbles across it, I hope it’s helpful.

ZeroTier has fundamentally changed how I use my desktop remotely. It’s free, insanely reliable, and ridiculously easy to set up. Combined with WSL + VS Code Remote Development, it makes coding from anywhere feel just as smooth as sitting at my desk.

If you ever need remote access to your devices—without dealing with port forwarding or static IPs—ZeroTier is 100% worth trying.

{% include toc %}