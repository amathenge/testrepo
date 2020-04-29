This is a README file for GIT.

I'm learning how to use the system.

Useful commands will be posted in the files to be updated in this repository.

Tony: 29 April, 2020 @ 01:33 EDT

----------------

the ssh-agent needs keys added manually.

ssh-add ~/.ssh/id_rsa

then check if ssh-agent is running

eval $(ssh-agent -s)

This should return the process id of the SSH agent.
