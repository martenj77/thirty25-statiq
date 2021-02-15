---
title: A short story on upgrading your Ghost instance running on Ubuntu
description: Ghost rider in the sky
tags: 
  - Ghost
date: 2020-05-25
image: ghost.jpg
---
Here are some notes I took while upgrading Ghost from 3.3.0 to 3.16.1.

**Before you start: Make backups first. If you're using Digital Ocean you can go the easy way by making a snapshot through the Digital Ocean app. Otherwise, look at [this info from Ghost.org](https://ghost.org/update/?v=3.3.0).**

## Update your server

Login to the server, ```ssh user@ip-address```.

Run some basic upgrade commands.

``` bash
sudo apt-get update
sudo apt-get upgrade
```

You can also do a more thorough upgrade with..

``` bash
sudo apt-get dist-upgrade
```

And lastly.. reboot.

``` bash
sudo reboot
```

## Now that we've got that out of the way: Update Ghost

Login again after the reboot, ```ssh user@ip-address```.
Switch to a non-root-user.

``` bash
su your-username
```

Go to the Ghost instance you want to upgrade. If you're following the [Ghost and Digital Ocean-way](https://ghost.org/docs/install/ubuntu) it should be in /var/www/ghost or something alike.

``` bash
cd /var/www/ghost
```

Now you can do your upgrading.
First upgrade ghost CLI, then Ghost.

``` bash
sudo npm install -g ghost-cli@latest
ghost update
```

Sometimes the ghost update fails with some incorrect permissions, set them by this command and then run `ghost update` again.

``` bash
sudo find ./ ! -path "./versions/*" -type f -exec chmod 664 {} \;
```

## Wrapping up

If you like me have multiple Ghost instances on the same machine you need to go to the other directory(s) where it's installed and run the upgrade.

And - once you feel confident everything is working ok then you might delete the snapshot created even though it's not many cents extra keeping it around for a while - just in case.