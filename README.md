# Splunk Log Collect for Windows Kubernetes Nodes #

`splunk-k8s-win-logging` is a customization base on the official solution [`splunk-kubernetes-logging`] https://github.com/splunk/splunk-connect-for-kubernetes/tree/develop/helm-chart/splunk-connect-for-kubernetes/charts/splunk-kubernetes-logging. It is a [Helm](https://github.com/kubernetes/helm) chart that creates a kubernetes daemonset along with other kubernetes objects in a kubernetes cluster to collect application logs from the windows nodes.

The daemonset runs [fluentd](https://www.fluentd.org/) with the [Splunk HEC output plugin](https://github.com/splunk/fluent-plugin-splunk-hec) to watch, collect and send all containers logs over [Splunk HEC](http://docs.splunk.com/Documentation/Splunk/7.1.0/Data/AboutHEC). The default path is /var/log/containers/*.log.


## Install ##

See also [Using Helm](https://docs.helm.sh/using_helm/#using-helm).

First, set a values file with the appropriate values and run the following commands:

```bash
$ helm package charts/splunk-k8s-win-logging --version <chartVersionNumber> --app-version <appVersionNumber>
$ helm install --name splunk-logging -f my_values.yaml splunk-k8s-win-logging-<chartVersionNumber>.tgz
```

## Uninstall ##

To uninstall/delete a deployment with name `splunk-logging`:

```bash
$ helm delete splunk-logging
```

The command removes all the Kubernetes components associated with the chart and deletes the release.
