  `sudo rm -rf /etc/localtime`

Identify the timezone you want to configure and create the symbolic link for it:

For instance, I would like to set *Asia/Makassar* timezone:

  `ln -s /usr/share/zoneinfo/Asia/Makassar /etc/localtime`

Now verify it by:

`date`

and the output would be your timezone:

> Sat Jan 30 14:22:17 +0330 2021

