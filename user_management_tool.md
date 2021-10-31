### Adding Users

>You can use the adduser or the useradd command. The adduser command contains more helpful features such as making a home directory and more. There are configuration files for adding new users that can be customized depending on what you want to allocate to a default user.
<pre>
$ sudo useradd bob
</pre>
>You'll see that the above command creates an entry in /etc/passwd for bob, sets up default groups and adds an entry to the /etc/shadow file.

### Removing Users

>To remove a user, you can use the userdel command.
<pre>
$ sudo userdel bob
</pre>

>This basically does its best to undo the file changes by useradd.

### Changing Passwords
<pre>
$ passwd bob
</pre>

>This will allow you to change the password of yourself or another user (if you are root).