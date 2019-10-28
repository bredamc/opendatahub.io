---
layout: docs
title: Quick Installation
permalink: /docs/getting-started/quick-installation
style_class: quick-installation
---

### Pre-requisites

Installing ODH requires OpenShift 3.11 or 4.x. Documentation for OpenShift can be located ([here](https://docs.openshift.com/container-platform/4.1/welcome/index.html)).  All screenshots and instructions are from OpenShift 4.1.  For the purposes of this quick start, we used [try.openshift.com](https://try.openshift.com/) on AWS.  Tutorials have also been tested on [Code Ready Containers](https://code-ready.github.io/crc/) with 16GB of RAM.


### Installing the Open Data Hub Operator

The Open Data Hub operator is available in the OpenShift 4.x Community Operators section. You can install it from the OpenShift webui by following the steps below:

1. From the OpenShift console, log in as a user with `cluster-admin` privileges.  For a developer installation from [try.openshift.com](https://try.openshift.com/) including AWS and CRC, the `kubeadmin` user will work.
![Log in to OpenShift]({{site.baseurl}}/assets/img/pages/docs/quick-installation/1-login.png "Log in to OpenShift")
1. Create a new namespace for your installation of Open Data Hub.
![Create Namespace]({{site.baseurl}}/assets/img/pages/docs/quick-installation/2-create-namespace.png "Create Namespace")
1. Find `Open Data Hub` in the `OperatorHub` catalog.
   1. Select the new namespace if not already selected.
   1. Under `Catalog`, select `OperatorHub` for a list of community operators.
   1. Filter for `Open Data Hub` or look under `Big Data` for the icon for `Open Data Hub`.
![OperatorHub]({{site.baseurl}}/assets/img/pages/docs/quick-installation/3-operator-hub.png "OperatorHub")
1. Click the `Install` button and follow the installation instructions to install the Open Data Hub operator.
![Install]({{site.baseurl}}/assets/img/pages/docs/quick-installation/4-install.png "Install")
1. To view the status of the Open Data Hub operator installation, find the Open Data Hub Operator under `Catalog` -> `Installed Operators` (inside the namespace you created earlier). Once the STATUS field displays `InstallSucceeded`, you can proceed to create a new Open Data Hub deployment.
![Installed Operators]({{site.baseurl}}/assets/img/pages/docs/quick-installation/5-installed-operators.png "Installed Operators")

### Create a New Open Data Hub Deployment

The Open Data Hub operator will create new Open Data Hub deployments and manage its components.  Let's create a new Open Data Hub deployment.

1. Find the Open Data Hub Operator under `Installed Operators` (inside the namespace you created earlier)
![Installed Operators]({{site.baseurl}}/assets/img/pages/docs/quick-installation/5-installed-operators.png "Installed Operators")

1. Click on the Open Data Hub Operator to bring up the detail.
![Open Data Hub Operator]({{site.baseurl}}/assets/img/pages/docs/quick-installation/6-odh-operator.png "Open Data Hub Operator")

1. Click `Create New` to create a new deployment.
![Create New ODH]({{site.baseurl}}/assets/img/pages/docs/quick-installation/7-new-deployment.png "Create New ODH")

1. Here you'll be presented with a YAML file to customize your deployment.  Most options are disabled, and for this tutorial we'll leave them that way and stick with the defaults.  Take note of some parameters:
    - the name of your deployment `example-opendatahub`
```yaml
metadata:
    name: example-opendatahub
```
    - the deployed components designated by `odh_deploy`:
```yaml
spec:
    aicoe-jupyterhub:
        odh_deploy: true
    spark-operator:
        odh_deploy: true
```

1. Leave the YAML intact and click `Create`.  If you accepted the default YAML, this will trigger an Open Data Hub deployment named `example-opendatahub` with JupyterHub and Spark.

1. Verify the installation by viewing the Open Data Hub tab within the operator details.  You Should see `example-opendatahub` listed.
![ODH List]({{site.baseurl}}/assets/img/pages/docs/quick-installation/8-odh-list.png "ODH List")

1. Verify the installation by viewing the project status.  JupyterHub, Spark, and Prometheus should all be running.
![Verify Status]({{site.baseurl}}/assets/img/pages/docs/quick-installation/9-verify-pods.png "Verify Status")

{% include next-link.html label="Basic Tutorial" url="/docs/getting-started/basic-tutorial.html" %}