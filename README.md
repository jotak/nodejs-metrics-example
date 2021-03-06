## Node.js with metrics on Kubernetes

This is a slightly modified version of this tutorial: https://developers.redhat.com/blog/2018/12/21/monitoring-node-js-applications-on-openshift-with-prometheus/

### Build

(You can ignore this step, docker image will be dowloaded from my repo)

```bash
npm install
npm build
docker build -t jotak/nodejs-prom-example:latest .
```

### Deploy

Using `oc`

```bash
oc new-project nodejs-prom
oc apply -f Deployment.yml
oc apply -f Service.yml
oc expose svc/nodejs-prom-example
```

### Kiali dashboard

From Kiali sources:

```bash
oc apply -f deploy/dashboards/nodejs.yaml
```
