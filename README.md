This is a README file for GIT.

I'm learning how to use the system.

Useful commands will be posted in the files to be updated in this repository.

Tony: 29 April, 2020 @ 01:33 EDT

------------------------------------------------------

the ssh-agent needs keys added manually.

ssh-add ~/.ssh/id_rsa

then check if ssh-agent is running

eval $(ssh-agent -s)

This should return the process id of the SSH agent.

------------------------------------------------------

I tested using ps ef which returned:

$ ps ef
      PID    PPID    PGID     WINPID   TTY         UID    STIME COMMAND
     1701       1    1701      14160  ?         197610   May  5 /usr/bin/ssh-agent
     2010    1908    2010       7560  pty0      197610 23:22:53 /usr/bin/ps
     1907       1    1907      14284  ?         197610 23:18:43 /usr/bin/mintty
     1908    1907    1908      16288  pty0      197610 23:18:43 /usr/bin/bash

------------------------------------------------------

But look at the following:

andrew@MATHENGE MINGW64 ~/Documents/src/temp (master)
$ ps aflW
      PID    PPID    PGID     WINPID   TTY         UID    STIME COMMAND
     1701       1    1701      14160  ?         197610   May  5 /usr/bin/ssh-agent
     1907       1    1907      14284  ?         197610 23:18:43 /usr/bin/mintty
     1908    1907    1908      16288  pty0      197610 23:18:43 /usr/bin/bash
     2026    1908    2026      16088  pty0      197610 23:23:55 /usr/bin/ps

andrew@MATHENGE MINGW64 ~/Documents/src/temp (master)
$ eval $(ssh-agent -s)
Agent pid 2031

andrew@MATHENGE MINGW64 ~/Documents/src/temp (master)
$ ps ef
      PID    PPID    PGID     WINPID   TTY         UID    STIME COMMAND
     1701       1    1701      14160  ?         197610   May  5 /usr/bin/ssh-agent
     2035    1908    2035      16812  pty0      197610 23:24:39 /usr/bin/ps
     1907       1    1907      14284  ?         197610 23:18:43 /usr/bin/mintty
     1908    1907    1908      16288  pty0      197610 23:18:43 /usr/bin/bash
     2031       1    2031      14860  ?         197610 23:24:26 /usr/bin/ssh-agent

NOTICE THE ADDITIONAL ssh-agent AT THE END OF THE LISTING.

------------------------------------------------------

And then I added the key:

andrew@MATHENGE MINGW64 ~/Documents/src/temp (master)
$ ssh-add ~/.ssh/id_rsa
Enter passphrase for /c/Users/andrew/.ssh/id_rsa:
Identity added: /c/Users/andrew/.ssh/id_rsa (rsa-key-20200430)

andrew@MATHENGE MINGW64 ~/Documents/src/temp (master)
$
