# HPCT Node Operator

This repo provides two charms:
* [hpct-node](node/README.md) (for general use)
* [hpct-node-subordinate](subordinate/README.md) (example for demonstration)

An HPC cluster bundle mockup is also provided: [hpct-cluster-bundle-mockup.yaml](hpct-cluster-bundle-mockup.yaml).

## Test

Prerequisites:
* snap
* charmcraft (snap package)
* juju (snap package)

Clone this repository:

```
git clone <repourl>
```

Build (may need to run each `charmcraft` twice):

```
cd hpct-node
(cd node; charmcraft -v pack)
(cd subordinate; charmcraft -v pack)
```

Symlink:

```
ln node/hpct-node_ubuntu-22.04-amd64.charm .
ln subordinate/hpct-node-subordinate_ubuntu-22.04-amd64.charm .
```

Run:

```
juju deploy ./hpct-cluster-bundle-mockup.yaml
```

Watch:

```
juju status --watch 5s --relations
```
