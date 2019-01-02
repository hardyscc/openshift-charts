# helm-repo-in-gitlab

This is a sample for how to setup a helm repo in gitlab without pages. This is usable even for private repositories.

# Build the dependency

```bash
$ helm dependency update $YOUR_CHART_PATH/ # build the dependency tgz file
$ helm dependency build $YOUR_CHART_PATH/ # build the dependency tgz file
```

# Adding a new version or chart to this repo

```bash
$ helm package $YOUR_CHART_PATH/ # build the tgz file and copy it here
$ helm repo index . # create or update the index.yaml for repo
$ git add .
$ git commit -m 'New chart version'
```

# How to use it as a helm repo

You might know gitlab has a raw view. So simply use the following:

```bash
$ helm repo add openshift 'http://gitlab.apps.sysforce.com/tommy/charts/raw/master'
$ helm repo update
$ helm search nodejs
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
openshift/nodejs        0.1                             An example Node.js application with no database. For more...
```
