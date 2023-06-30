---
layout: default
title: Lesson 1 - Using Git
nav_order: 1
parent: Lessons
---
<!-- 
This page is an example lesson template.
Add, edit, or remove any content below for the workshop in question. -->

<!-- Putting a {: .no_toc} above a header removes it from the table of contents -->

{: .no_toc}  
# Lesson 1 - Using Git

99% of the time, you will be using the same six or so Git commands. Starting to learn Git is hard, but it gets a lot easier after you get past the entry barrier.

<!-- This is your table of contents. You don't need to touch it, it automatically creates it when you add or remove headers. If you do not want a header to be included, put {: .no_toc } above the header line, as you can see above with Lesson 1 - Lesson Name. Make sure that there's also an empty line above {: .no_toc }... Markdown is picky about this :( -->
<details markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

<!-- Here are your learning objectives. Just like in the introduction, but more specific for this lesson. -->
## Lesson Objectives
- Set up Git
- Create a Git repository
- Commit changes to a Git repository
- View a log of changes made

<!-- A video for your lesson (if applicable) -->
<!-- ## Lesson Video
The following video demonstrates each of the steps outlined below in text.

<iframe height="416" width="100%" allowfullscreen frameborder=0 src="https://echo360.ca/media/a65689c0-c35c-4f33-9c12-f0ac97883f54/public?autoplay=false&automute=false"></iframe>
[View original here.](https://echo360.ca/media/a65689c0-c35c-4f33-9c12-f0ac97883f54/public?autoplay=false&automute=false) -->

<!-- Text content format for your lessons if you don't want to rely on videos, or want to provide another format of learning consumption. -->
## Setting up Git

Open up your shell terminal window (or Git Bash if you're on Windows). This is where we'll be interacting with Git.

Before we start using Git, we need to set up some configuration options. If you're on Windows, it's possible that most of the settings are already set up, but it's always good to double check.

### Git Config - Viewing Current Config

To view our current Git config, use the following command:

```bash
git config --list
```

Depending on your OS and whether or not you've used Git before, it's possible that you will only see one line of config, or 20 lines.

### Git Config - Username and Email

The first settings we want to set up are our Git username and email. Your Git username will be used to record the author of any changes made.

{: .warning }
Make sure to use the same email you used when creating your GitHub account.

```bash
git config --global user.name "Your Name"
git config --global user.email "yourname@domain.name"
```

Replace "Your Name" with your desired username and "yourname@domain.name" with your email. If there is no output, that means the command succeeded. This is often the case with command-line interfaces.

Now, if you check the config list again, you should see that your username and email are set.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git config --list
```

{: .label .label-green }
Output
```
...
user.name=Your Name
user.email=yourname@domain.name
...
```
</div>

### Git Config - Default Text Editor

Occasionally, when using Git, it'll ask you to edit text in a text editor. By default, Git uses Vim, a text editor within the command-line interface. This is a popular choice for many, but it's also difficult to learn and use if you're new to the command-line interface. 

To set up a custom text editor, we have to change the `core.editor` config setting. On Windows, Notepad is a popular option. MacOS and Linux users may prefer the `nano -w` setting.

```bash
git config --global core.editor "notepad"
```

```bash
git config --global core.editor "nano -w"
```

### Git Config - Default Branch Name

By default, Git uses the term "master" to refer to the default branch. 

Don't worry if you don't know what a branch is; we won't cover branches because they're out of scope for the purposes of this workshop. To quickly define a branch, think of them as a  separate area of development. The master branch is where the "release" version of content is held, and more branches can be made to add more features or content to the project without disrupting the master branch. Once the new feature is finished, it can be merged into the master branch.

However, GitHub and most developers nowadays have started to name the default branch as the "main" branch. To prevent any issues with GitHub, we will change the default branch name to  "main" using the `init.defaultBranch` config.

```bash
git config --global init.defaultBranch "main"
```

## Creating a Git Repository

Now that Git is set up, we can go ahead and start using Git! 

Let's start by creating a new directory, which will be where we'll store our "project". Once again, while Git is mostly used for software projects, it can also be used for writing books, journals, storing data, and more.

You can do this in however way you want, in a Documents folder, on your desktop, or wherever. If you want to do it using the command-line interface, you can use the `ls` command to list the directories and files in your current working directory.

```bash
ls
```

Then, use `cd` to move through directories. Use `cd ..` to go back a directory.

```bash
cd Documents
```

Finally, use the `mkdir` command to make a directory and then `cd` into it.

```bash
mkdir hello-world
cd hello-world
```

At the root of every project that uses Git is a Git repository. A repository is just like any other directory, but it also contains a hidden `.git` folder inside. This folder contains all the information that Git uses to keep track of all the changes you've made. 

To initialize a Git repository, we need to use the `git init` command.

```bash
git init
```

Your directory should now be a Git repository. If you can't find the `.git` folder, that's alright. It’s hidden by default as you’re not meant to go in there and edit the files.

## Displaying a Repository's Status

The `git status` command displays the current status of our Git repository.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git status
```

{: .label .label-green }
Output
```
On branch main
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```
</div>

You can see here that we're on the main branch, as discussed earlier. Since we haven't made any changes to our Git repository since we created it, there won't be any commits or changes to commit.

## Adding and Commiting

Git does not automatically save work, thus requiring you to manually save. To save any changes, we need to **add** the files we want to save and then **commit** those changes. This gives us control over what files we want to save or not save.

To create an empty text file, let's use the `touch` command.

```bash
touch note.txt
```

Using the `ls` command, we'll see that a new file called `note.txt` has been created. Let's check the status of our repository using `git status` again.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git status
```

{: .label .label-green }
Output
```
On branch main
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    note.txt

nothing added to commit but untracked files present (use "git add" to track)
```
</div>

Git automatically detected that there have been changes made (creation of `note.txt`), but it says that they're untracked. To add it to our tracked files, we need to use `git add`.

```bash
git add note.txt
```

This adds our `note.txt` file into the staging area. The staging area is the area where Git checks for files to commit or save. We can check this using `git status` again.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git status
```

{: .label .label-green }
Output
```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   note.txt
```
</div>

Now our file is ready to be committed and saved. Before we do that, let's add some text to the `note.txt` file and see how Git responds to it. You can add the text to `note.txt` using any means you wish.

Once that is done, do `git status` again.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git status
```

{: .label .label-green }
Output
```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   note.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   note.txt
```
</div>

Git recognizes that `note.txt` has been modified, but it hasn't added it to our staging area for commits. We still have to use `git add` to keep track of that change.

```bash
git add note.txt
```

Now that we've added all our changes to the staging area, let's create our first commit. When committing changes, Git will keep track of the author of the commit, the current time and date, and any changes made to the project. To commit our changes, we use the `git commit -m "message"` command, where we replace "message" with our own message.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git commit -m "Create note.txt"
```

{: .label .label-green }
Output
```
[main (root-commit) 820ab37] Create note.txt
 1 file changed, 1 insertion(+)
 create mode 100644 note.txt
```
</div>

The output message tells us a few things. This commit was made in the `main` branch, with the `820ab37` tag. It also repeats our commit message and summarizes the changes made in that commit.

## Viewing the Logs

To get a log of all the changes made throughout a project's history, we can use the `git log` command.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git log
```

{: .label .label-green }
Output
```
commit 820ab3702280dd79f240e8cd4d63e48efb88ed03 (HEAD -> main)
Author: myusername <myemail>
Date:   Mon Jun 26 14:39:50 2023 -0400

    Create note.txt
```
</div>

Let's create another commit to see how `git log` changes. Edit `note.txt` again in whatever way you'd like. 

If you simply want to add **all** changes and commit them in one line, use `git commit -am "message"`. This will stage all changes and commit them.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git commit -am "Add line to note.txt"
```

{: .label .label-green }
Output
```
[main 8440b88] Add line to note.txt
 1 file changed, 2 insertions(+), 1 deletion(-)
```
</div>

Let's use `git log` again.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git log
```

{: .label .label-green }
Output
```
commit 8440b88c34cadc7e964592b980cc135395e4433e (HEAD -> main)
Author: myusername <myemail>
Date:   Mon Jun 26 14:45:49 2023 -0400

    Add line to note.txt

commit 820ab3702280dd79f240e8cd4d63e48efb88ed03
Author: myusername <myemail>
Date:   Mon Jun 26 14:39:50 2023 -0400

    Create note.txt
```
</div>

As we can see, the output lengthened quite a bit to make room for the new commit. We can use `git log --oneline` to summarize the log.

<div class="code-example" markdown="1">

{: .label }
Input
```bash
git log --oneline
```

{: .label .label-green }
Output
```
8440b88 (HEAD -> main) Add line to note.txt
820ab37 Create note.txt
```
</div>

## Key Points / Summary

- To save a change, you need to **add** and **commit** changes
- `git log` shows the history of commits made
