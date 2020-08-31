*tonamed - Pipe to named pipe**

https://github.com/jakeogh/toname

GOAL: Take stdin and redirect it to a temporary named pipe.

**Theory:**

 1. Create a FIFO named pipe that does not already exist.
 2. Write stdin to that named pipe.
 3. Delete the named pipe on exit or error.

**General Install:**

Place in $PATH

```
    git clone https://github.com/jakeogh/toname
    sudo cp commandlock/toname /usr/bin/toname
```

**Gentoo Install:**
```
   su
   layman -o https://raw.githubusercontent.com/jakeogh/jakeogh/master/jakeogh.xml -f -a jakeogh
   echo "source /var/lib/layman/make.conf" >> /etc/portage/make.conf
   layman -S
   emerge toname
```

**Use:**

```
$ echo "the great awakening" | toname /tmp/some_new_fifo &
$ cat /tmp/some_new_fifo
the great awakening
```

**Design notes:**

- Attempts to be POSIX compliant.
- Does not depend on bash-specific features.

