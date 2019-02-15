Zest rubygem build instructions

1.  Setup pulplift: https://github.com/pulp/pulplift
2.  Checkout zest within pulplift, your directory structure should look like:
```
$ ls -l pulplift/
ansible.cfg
ansible-pulp3
forklift
playbooks
README.md
roles
vagrant
Vagrantfile
zest
```

3.  Set the build version, in zest/playbook.yml
4.  Within pulplift, run:
```
ansible-playbook zest/playbook.yml  -e pulplift_state=up
```

This will spinup a pulp3 vagrant box, generate a new zest gem and copy it back to the pulplift directory.

5.  To push to rubygems.org (if you have permissions): 
```
gem push zest-0.0.z.gem
```

6.  Destroy your box:
```
ansible-playbook zest/playbook.yml  -e pulplift_state=down
```
