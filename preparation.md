---
layout: default
title: Preparation
nav_order: 2
---
<!-- 
(OPTIONAL) This will be the page going over any installation or registration requirements.
Add, edit, or remove any content below for the workshop in question. 
-->

# Workshop preparation 

<!-- 
Seperate preparation into account creation, file downloads, and software downloads.
However, you can format this as you wish.
An example is provided below.
-->
## 1. Create a GitHub account
- [Navigate to GitHub](https://github.com/) and sign up for an account if you don’t already have one.
- After registering, sign in to your account.

## 2. Install Git
- [Navigate to Git downloads](https://git-scm.com/downloads) and choose your operating system.
- Follow the instructions provided to download and install Git.

### Installation for Windows users

When installing Git, choose the following options.

- **Adjusting the name of the initial branch in new repositories**
  - Override the default branch name for new repositories. Set this to `main`.
- **Choosing the default editor used by Git**
  - Choose your preferred editor. If you're unsure, select "Notepad".
- **Adjusting your PATH environment**
    - Git from the command line and also from 3rd-party software.
- **Choosting the SSH executable**
    - Use bundled OpenSSH.
- **Choosing HTTPS transport backend**
    - Use the OpenSSL library.
- **Configuring the line ending conversions**
    - Checkout Windows-style, commit Unix-style line endings.
- **Configuring the terminal emulator to use with Git Bash**
    - Use MinTTY (the default, terminal of MSYS2).
- **Choose the default behaviour of 'git pull'**
    - Default - (fast-forward or merge).
- **Choose a credential helper**
    - Git Credential Manager.
- **Configuring extra options**
    - Enable file system caching.
- **Configuring experimental options**
    - *Do not select anything and click install*

When using Git throughout the workshop and in the future, use the Git Bash application.
