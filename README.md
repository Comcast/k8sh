# k8sh

![k8sh Screenshot](/screenshot.png?raw=true)

A shell wrapper for bash including aliases for kubectl that makes it easy to navigate between and execute commands on different kubernetes clusters and namespaces.

## First time

Clone the repo and then make sure `k8sh` has execute permissions:
```
chmod +x k8sh
```

Now you can execute k8sh!
```
./k8sh
```

Add to a PATH directory to execute anywhere.

k8sh will automatically look at your current kubectl configuration to determine your current kubernetes context and namespace.

## Switching contexts and namespaces

*k8sh* automatically keeps track of the current context and namespace you are operating in. These are displayed when starting up k8sh and on the k8sh prompt.

To switch contexts just enter:
```
ct <context_to_switch_to>
```

To switch namespaces just enter:
```
ns <namespace_to_switch_to>
```

NOTE: When changing the context, the change is made globally to kubectl as if you did a `kubectl config use-context` yourself. The namespace, however, is kept track of by k8sh. The standard `kubectl` command is aliased to always include the namespace that is currently selected within k8sh.

## Aliases

As stated above, when inside of *k8sh* the standard `kubectl` command is aliased to always include the namespace that is currently selected. k8sh also includes many other aliases to make accessing commonly used kubectl commands a snap.

### k
**k** is an easy shorthand for `kubectl`

### Common Actions
Shorthands for common actions

* **describe** -> k describe
* **get** -> k get
* **create** -> k create
* **apply** -> k apply
* **delete** -> k delete
* **scale** -> k scale
* **rollout** -> k rollout
* **logs** -> k logs

### Query for common resources (kubectl get)
Instead of typing out `kubectl get pods/services/replicationcontrollers/etc` you can simply type the following aliases to get a list of those resources:

* **pods**
* **services**
* **deployments** / **dep**
* **replicasets**
* **replicationcontrollers** / **rc**
* **nodes**
* **limitranges**
* **limits**
* **events**
* **persistentvolumes** / **pv**
* **persistentvolumeclaims** / **pvc**
* **namespaces**
* **ingresses** / **ing**
* **configmaps**
* **secrets**

## .k8sh_extensions
On startup *k8sh* looks for a `.k8sh_extensions` file in your home directory. If it is there, it loads it as an inline bash script so you can supply your own aliases and functions to execute within k8sh.

To force the extensions file to be reloaded while in a k8sh session you can run:
```
reloadExtensions
```

See `examples/k8sh_extensions` for some examples of what extensions can do.

## Todo
* Get the standard `kubectl` tab completion to work with aliases.
