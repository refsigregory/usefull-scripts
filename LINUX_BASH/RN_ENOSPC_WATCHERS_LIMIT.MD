# React Native Error: ENOSPC: System limit for number of file watchers reached

The error is thrown becauset the number of files monitored by the system has reached the limit.

> Result: The command executed failed! Or a warning is shown (such as executing a react-native start VSCode)"

Solution:

Modify the number of system monitoring files:

Ubuntu:

`sudo nano /etc/sysctl.conf`

Add a line at the bottom:

`fs.inotify.max_user_watches=524288`

Then save and exit! Run:

`sudo sysctl -p`
