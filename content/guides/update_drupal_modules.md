+++
title = "Update Drupal 7 Modules"
date =  2019-03-17T14:45:13+01:00
weight = 15
toc = true
+++

## Introduction

Drupal 7 has a built-in updater that updates everything that needs to be updated. However, it requires FTP access but we use SFTP so it does not work. Luckily, we can use [drush](/other_applications/drupal7) instead.

## Instructions

{{% notice warning %}}
Read through the update changes for every module before you update. Some updates requires you to do some changes
{{% /notice %}}

1. Use *ssh* to access the server: `ssh <your-username>@babbage.utn.se`

2. Change directory to the public folder: `cd public`

3. Run `drush -y up`

Let drush run and you should have an updated website.
