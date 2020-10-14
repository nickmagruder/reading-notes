# Revisions and the Cloud

Table of Contents
* [Home](https://nickmagruder.github.io/reading-notes/)
* [Embracing the Growth Mindset](growth_mindset.md)
* [Read 01: Markdown](markdown.md)
* [Read 02: Text Editors and Command Prompt](text_editors.md)
* [Read 03: Revisions and the Cloud](read_03.md)
* [Read: 04 - Structure web pages with HTML](read_04.md)
* [Read: 05 - Design web pages with CSS](read_05.md)
* [Read: 06a - Dynamic web pages with JavaScript](read_06a.md)
* [Read: 06b - Computer Architecture and Logic](read_06b.md)
* [Read: 07 - Programming with JavaScript](read_07.md)
* [Read: 08 - Operators and Loops](read_08.md)
* [Read 04: HTML & Design](read_04.md)

## Git!
### Distributed Version Control
DVCS allows clients to create mirrored repositories. These data backups can be easily be placed on the server to replace any lost information.

### What is git?
GIt has its roots in the Linux kernel. Linus Torvalds, the chief architect of the Linux kernel, began creating Git. With the intention of creating a DVCS with a workflow design similar to that of BitKeeper, which was also fast, Git allowed for non-linear development via multiple branches, could support large projects, possessed strong mechanisms preventing corruption, and had a simple design.

#### Snapshots
Each time you save a change, git creates a snapshot

#### States
Files in Git can reside in three main states: committed, modified and staged.

#### Committed
Data is securely stored in a local database

#### Modified
File has been changed but not committed to the database

#### Staged
Flagged a file’s changed version to be committed in the next snapshot

### Getting Help - There are three ways to get more information on a particular command, by accessing the manual:
git help command
git command --help
man git-command

### Stashing Changes
When you are not ready to commit changes but do not want to lose them either, git stash is a great option. This command temporarily removes changes and hides them, giving you a clean working directory. When you are ready to continue working on the changes, simply use the git stash apply command to retrieve the hidden changes.

### Seeing Your Remotes
By running the git remote command, you can view the short names, such as “origin,” of all specified remote handles.

By using git remote -v, you can view all the remote URLs next to their corresponding short names.
