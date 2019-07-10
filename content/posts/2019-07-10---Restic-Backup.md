---
title: Doing Backups of your personal data with Restic
date: "2019-07-10T14:00:00.169Z"
template: "post"
draft: true
slug: "/posts/restic-backup/"
category: "Tech"
tags:
  - "Restic"
  - "Backup"
description: "A post about using Restic a backup tool for personal data."
---

Hardware is meant to be used and after some time it will be prone to failure. In order not to propagate this failure
to loss of our personal data such as lovely pictures of memorable momments, we ought to do regular backups of our data.
Naturally, backup involves storing our data in some other hardware memory that is being used only for this purpose, but in
most cases we want to delegate the failure of the hardware someone else. **"The cloud"!**

Then, of course, a new problem arises called Privacy, which means when uploading our pictures to
Google Drive or Dropbox, we are solely accepting to
share our data with unknown entities.

![ecj-facebook-safe-harbor.jpg](/media/ecj-facebook-safe-harbor.jpg)

Well, solution for that is of course encrypting your data when it leaves your computer.

In that manner, after trying various tools for backing up my data i've chosen to use  [Restic](https://restic.net/).
A command line based backup tool written in Go language, that supports various cloud provider storages and also encrypts the data using
**AES-256** symmetric encryption.

