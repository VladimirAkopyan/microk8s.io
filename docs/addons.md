---
layout: docs
title: "MicroK8s Addons"
---

# MicroK8s Addons

To be as lightweight as possible, MicroK8s only installs the basics of a usable
Kubernetes install:

 - api-server
 - controller-manager
 - scheduler
 - kubelet
 - cni
 - kube-proxy

While this does deliver a pure Kubernetes experience with the smallest of
resource footprints, there are situations where you may require additional
services. MicroK8s caters for this with the concept of "Addons" - extra
services which can easily be added to MicroK8s. These addons can be enabled
and disabled at any time, and most are pre-configured to 'just work' without
any further set up.

For example, to enable the CordDNS addon:

```bash
microk8s.enable dns
```

These add-ons can be disabled at anytime using the `disable` command:

```bash
microk8s.disable dns
```

... and you can check the list of available and installed addons at any time
by running:

```bash
microk8s.status
```

## Current MicroK8s Addons

**dashboard**: The standard Kubernetes Dashboard.

**dns**: Deploys CoreDNS. This add-on may be required by others - it is
recommended you always enable it. In restricted environments you may need to
update the upstream DNS servers.

**[fluentd](addon-fluentd)**: Deploy the [Elasticsearch-Fluentd-Kibana][kibana-docs] logging and
monitoring solution.

**gpu**:  Enable support for GPU accelerated workloads using the NVIDIA runtime.

**ingress**: A simple ingress controller for external access.

**istio**: Adds the core [Istio][istio-docs] services.

**jaeger**: Deploy the [Jaeger Operator][jaeger-docs] in the “simplest”
configuration.

**knative**: Adds the [Knative][knative-docs] middleware to your cluster.

**linkerd**: Deploys the [linkerd][linkerd-docs] service mesh.

**metrics-server**: Adds the [Kubernetes Metrics Server][metrics-design-doc]
for API access to service metrics.

**prometheus**: Deploys the [Prometheus Operator][prometheus-docs].

**rbac**: Enable Role Based Access Control for authorisation. Note that this is
incompatible with some other add-ons.

**registry**: Deploy a private image registry and expose it on localhost:32000.
The storage add-on will be enabled as part of this add-on. See the registry
documentation for more details.

**storage**: Create a default storage class which allocates storage from a
host directory.


<!-- LINKS -->

[efk-upstream]: https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/
[istio-woe]: https://istio.io/docs/concepts/what-is-istio/
[istio-docs]: https://istio.io/docs/
[jaeger-docs]: https://github.com/jaegertracing/jaeger-operator
[linkerd-docs]: https://linkerd.io/2/overview/
[kibana-docs]: https://www.elastic.co/guide/en/kibana/current/discover.html
[metrics-design-doc]:https://github.com/kubernetes/community/blob/master/contributors/design-proposals/instrumentation/metrics-server.md
[knative-docs]: https://knative.dev/
[prometheus-docs]: https://prometheus.io/docs/