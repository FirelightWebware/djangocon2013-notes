# Getting Started with Salt

_Speaker: Peter Baumgartner_


Saltstack is configuration management.

- Version-control your servers.
- Self-documenting.
- Repeatable.
- Reusable.
- Remote Execution.
    - deploy
    - run one-off scripts

## Why saltstack instead of Chef/Puppet

- Familiar tools
    - YAML configuration
    - Python source
    - Jinja templates
- Great documentation
- Responsive community (#salt on IRC)
- Backed by a for-profit org


### And why not?

- young project
- moves fast
- not ssh (but that's coming soon)


## Learning Salt

- **master**: server that manages others
- **minion**: connects to master
- **state**: declaritive repr of system state, configuration
- **grain**: static information about a minion, e.g. what os? how much ram?
- **pillar**: variable for one or more minion (ports, file paths, config params)
- **top file**: matches states or pillars to minions
- **high state**: all the state data for a minion

Master hold states and pillars and connects to minions which each have grains
that tell the master about them. Master uses top file to verify what goes on
the minion. Master has a grains cache.

### Installation

You can use pip to install it. There also http://bootstrap.saltstack.org.

    root@master: apt-get install salt-master
    root@minion: apt-get install salt-minion

accept the minion key on the master

    salt-key -a minion.domain.name

### Write first state

/srv/salt/mystate.sls

    nginx:
        pkg.installed

### Create top file

/srv/salt/top.sls

    base:
        myserver.mydomain.com
        state:
            highstate 

_^^^ don't know if that's right __

Then you can push the high state from the master, or pull from the minion.

### Create a user state

    pete:
        user.present:
            - shell: /bin/bash
            - home: /home/pete
            - groups:
                - sudo
        ssh_auth.present:
            - user: pete
            - source: salt://pete.pub
            - require:
                - user: pete

### Code repo

    git@github.com/ipmb/mysite.git:
        git.latest:
            ...

There are over 50 built-in states. Pip, virtualenv, postgres, files, cron, or
you can build your own in Python.


### Example Pillar

    mysite:
        - branch: develop

/srv/pillar/top.sls

    base:
        '*':
            - default
        '*.mydomain.com':
            - mydomain
        'os.Ubuntu':
            - match: grain
            - pkgs.ubuntu


git@github.com/..:
    git.latest:
        -rev: {{ pillar.mysite.branch }}
        - target: /usr/local/src/mysite
        - require:
            - pkg: git-core


## Tips & Tricks

- Use `output_mode: mixed` in your minions' config.
- Jinja2 is powerful, don't go nuts with it or it'll be more difficult to
  maintain and understand.
- Update often and review the changelog (salt moves fast)
- Test before you deploy -- use vagrant or docker


## Reference

### Speaker

@ipmb  
Founder of Lincoln Loop
