---
title: "Obsidian Sync Git"
date: 2023-11-12T15:14:22+08:00
author: "marcusz"
draft: true
description: "Syncing notes with Obsidian and Git"
---

I use Obsidian as a personal notetaking app which is based on Markdown files. I also use Git to sync my notes across devices. This is a guide on how to set up Obsidian to sync with Git.

***Why not use Obsidian Sync?***
Its a premium feature and I don't want to pay for it. For convience it's a win-win, however there are alternatives that are free and open source and accessible on (almost) any device.

**We're using Obsidian G...**
This plugin is great but its messy to use and it's not really a good way to sync notes across devices. We instead do this manually by just pushing our vault directory to GitHub. Convince me otherwise.

## Setting up Obsidian
Download [Obsidian](https://obsidian.md/) and install it. Then create a new vault that can be accessible by Git.

or if you have an existing vault already, you can take note where the vault is located and make sure you can access it with Git.

## Setting up GitHub repository and Git
Download git from [git-scm.com](https://git-scm.com/downloads) and install it. Then create a GitHub account if you don't have one.

Create a very blank repository on GitHub, which will be used to store your notes. It can be either public or private (I'd recommend to make it private for personal notes).

You don't need to initialize the repository with a README file or with a .gitignore and LICENSE file. You can do that later manually to ensure that the repository initialisation is done properly

### Setting up Git
After you created a repository on GitHub. Once you setup your vault where `git` can access to, you can make your Obsidian vault directory a Git repository. You can use the following commands to initialize a Git repository in your Obsidian vault directory, make sure you know your git repository URL and your obsidian vault directory path.
```
git init
git commit -m "Initial commit"
git branch -M main
git remote add origin <your github repository url>
git push -u origin main
```
---------------------------
:warning: If this is the first time you're using git, make sure you set your git username and email address using the following commands:
```
git config --global user.name "<Your Name>"
git config --global user.email "<Your Email>"
```
---------------------------
:warning: You also need to obtain [Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token) from GitHub and use it as your password when pushing to GitHub. This is because GitHub will no longer accept password authentication

Alternatively, you can use [GitHub CLI](https://cli.github.com/) and authenticate yourself with `gh auth login` so it won't ask for your username and password every time you push to GitHub. All you need is to accept to use your GitHub account as git credentials.

# Accessing your notes on other devices
On another device, just clone it and access the vault as usual.

## On Android device
On devices like Android, you can use [Termux](https://termux.com/) to clone the repository and access the vault directory. However, this procedure is very tricky but its worth a shot. You could try git apps for Android but I don't know if it works or not, whatever its easy for you.

To access the vault directory, you need to install `git` package on Termux
```
pkg install git
```
Then clone the repository in `/sdcard` directory 

---------------------------
:warning: You need to grant Termux storage permission to access `/sdcard` directory

---------------------------

---------------------------
:warning: Because Obsidian doesn't support [Storage Access Framework](https://developer.android.com/guide/topics/providers/document-provider), you can only access it to `/sdcard` directory, since git is not very friendly with Android's filesystem, you can instead separate git repo in Termux home directory and work tree in shared storage:

```
git --git-dir=$HOME --work-tree="/sdcard/Obsidian Vaults" clone <your github repository url>
```
Git operations will be done on your Termux home directory where the git directory for your repository is stored, but the actual files will be stored in `/sdcard/Obsidian Vaults` directory

---------------------------

Then access the vault directory and open it with Obsidian as usual.
