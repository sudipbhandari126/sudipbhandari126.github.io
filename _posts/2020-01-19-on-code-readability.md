---
layout: post
title: On Code Readability 
tags: [code, coding-practice]
---

Almost everyone starts off coding in a very imperative fashion. You figure out the rules, syntax of the language and you figure out the logical solution to the problem and start off coding. As you start doing so
you discover some idiosyncracies of the language and you start focusing on making the code more and more 'concise'. If unchecked this can lead to obfuscation where you just increase the cognitive load of the program. You write a very smart-ass and clever piece of code which can take hours to decipher. The code is concise and does what you want but think in terms of the maintainer or even you yourself, fiew years/months down the line. May be you switched to another programming language and are probably thinking 'who the fuck wrote that?' until you 'git blame' it and find that it's you after all.

```sh
~/projects/my-project/.git/objects/1a(my-branch) » pigz -d < 58989906551da9cd7f2395c640e0b90667aa27
commit 677tree f1c83252e98f54138359308ef247193bf4e0bef4
parent 1747b1d081167971b9612ad75862943e8a9f344c
author Mister Author <mister-author@host.com> 1567673031 +0000
committer Mister Author <mister-author@host.com> 1567673031 +0000

Merged in feature/somebranch (pull request #426)

blah  blah message

```

pigz is the unix utility to view the content of the file.

Branches are stored inside .git/refs/heads which just contain the commit id.

These objects can belong to either category:

   1. blob — A blob object is used for storing the contents of a single file.

   2. tree — A tree object contains references to other blobs or subtrees.

   3. commit — A commit object contains the reference to another tree object and some other information(author, committer etc.)

   4. tag — A tag or a tag object is just another reference to a commit object and just makes for easier referencing.
