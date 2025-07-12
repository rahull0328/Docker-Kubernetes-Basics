# Kubectl Command Cheatsheet

Kubectl is the command line configuration tool for Kubernetes that communicates with a Kubernetes API server. Using kubectl allows you to create, inspect, update, and delete Kubernetes objects.

## Cluster Management

Display endpoint information about the master and services in the cluster

```js
kubectl cluster-info
```

Display the Kubernetes version running on the client and server

```js
kubectl version
```

Get the configuration of the cluster

```js
kubectl config view
```

List the API resources that are available

```js
kubectl api-resources
```

List the API versions that are available

```js
kubectl api-versions
```

List all the namespace

```js
kubectl get all --all-namespaces
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Daemonsets

**Shortcode = ds**

List one or more daemonsets

```js
kubectl get daemonset
```

Edit and update the definition of one or more daemonset

```js
kubectl edit daemonset <daemonset_name>
```

Delete a daemonset

```js
kubectl delete daemonset <daemonset_name>
```

Create a new daemonset

```js
kubectl create daemonset <daemonset_name>
```

Manage the rollout of a daemonset

```js
kubectl rollout daemonset
```

Display the detailed state of daemonsets within a namespace

```js
kubectl describe ds <daemonset_name> -n <namespace_name>
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Deployments

**Shortcode = deploy**

List one or more deployments

```js
kubectl get deployment
```

Display the detailed state of one or more deployments

```js
kubectl describe deployment <deployment_name>
```

Edit and update the definition of one or more deployment on the server

```js
kubectl edit deployment <deployment_name>
```

Create one a new deployment

```js
kubectl create deployment <deployment_name>
```

Delete deployments

```js
kubectl delete deployment <deployment_name>
```

See the rollout status of a deployment

```js
kubectl rollout status deployment <deployment_name>
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>