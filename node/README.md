# hpct-node

Charmhub package name: HPC node operator
More information: https://charmhub.io/hpct-node

A generic, principal node operator for HPC use.

One or more subordinates may integrate via the "node" relation with
"subordinate" interface. There is currently no integration data
communicated in either direction.

## Usage

# Test with hpct-node-subordinate

# General Use

Deploy principals for various node types:

```
juju deploy hpct-node head-node
juju deploy hpct-node interactive-node
juju deploy hpct-node compute-node
juju deploy hpct-node ldap-node
```

Deploy subordinates (example):

```
juju deploy hpct-node-subordinate ldap-client
juju deploy hpct-node-subordinate ldap-server
```

Relate the principals and subordinates:

```
juju relate head-node:node ldap-client:node
juju relate interactive-node:node ldap-client:node
juju relate compute-node:node ldap-client:node
juju relate ldap-node:node ldap-server:node
```

Scale up some nodes:

```
juju add-unit interactive-node -n 3
juju add-unit compute-node -n 10
```

See all the deployments:

```
juju status --relations
```

This can be extended, as needed.
