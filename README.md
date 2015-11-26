mongodb-replica-set
===================

This Ansible role provides a module for managing MongoDB Replica Sets.


Usage
-----

```yaml
# initiate a replica set
- mongodb_replica_set: state=initiated

# Reconfigure the settings of a replica set
- mongodb_replica_set: state=reconf woption:2 wtimeout:100 joption:true

# add a replica set member
- mongodb_replica_set: member=secondary.example.com state=present

# add an arbiter on custom port
- mongodb_replica_set: member=arbiter.example.com:30000 arbiter_only=yes state=present

# remove a replica set member
- mongodb_replica_set: member=secondary.example.com state=absent

# use all possible parameters when adding a member
# (please don't do that in production):
- mongodb_replica_set: >
    member=secondary.example.com
    state=present
    arbiter_only=yes
    build_indexes=no
    hidden=yes
    priority=0
    slave_delay=3600
    votes=42
```

How to use it?
-----

Copy the *library/mongodb_replica_set* python script to your ansible playbook library folder. Then you can use it in your roles.

Dependencies
-----

+ python-pip
+ pymongo
