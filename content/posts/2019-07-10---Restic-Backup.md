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
to loss of our data such as lovely pictures of memorable moments, we ought to do regular backups of our data.
Naturally, the backup involves storing our data in some other external hardware memory that is only used for backups.
However, there is a chance that this hardware can go wrong and because of that, it requires regular maintenance.
To avoid buying extra hardware and maintaining it, we can decide to save our data in "The cloud".

Then, of course, a new problem arises called Privacy, which means when uploading our pictures to
Google Drive or Dropbox, we are solely accepting to
share our data with unknown entities.

![ecj-facebook-safe-harbor.jpg](/media/ecj-facebook-safe-harbor.jpg)

Well, the solution for that is, of course, encrypting your data when it leaves your computer.

In this manner, after trying various tools for backing up my data i've chosen to use [Restic](https://restic.net/).
A command-line based backup tool written in Go language, that supports various cloud provider storages and also encrypts the data using
**AES-256** symmetric encryption.

My personal setup involves using restic for backing up documents and pictures to the [Mega](https://mega.nz/) Cloud provider.
The reason why i choosed it is because 50GB of free storage for now fits my needs and it is working smootly with restic.
In order to support backups to mega, [Rclone](https://rclone.org/) is required to be installed and configured.
To configure Rclone you are required, after installation, to run command `rclone config` and populate mega cloud provider credentials.
Previosly configured rclone configuration must be saved under alias and this alias is needed in order to create restic repository.
In restic world, a repository represents place where you will store backed up data and each data you perform a backup a snapshot is created in the repository.
Each snapshot can be used to restore backup.

In order to initialize repository using rclone and mega you need to run following command:
```
restic --repo rclone:<rclone-config-alias>:<pathing-inside-mega> init
```
"rclone-config-alias" represents alias of the rclone configuration and "pathing-inside-mega" represents pathing inside the mega storage.
For example if you choose "foo" your backups will be stored inside "foo" directory.
After executing given command, you will be prompted to enter password, that password is used to generate encryption key for encrypting your backup
and each time you want to access your backup you are required to enter this password.


