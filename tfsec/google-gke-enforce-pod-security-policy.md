Pattern: Pod security policy enforcement not defined

Issue: -

## Description

By default, Pods in Kubernetes can operate with capabilities beyond what they require. You should constrain the Pod's capabilities to only those required for that workload.

Kubernetes offers controls for restricting your Pods to execute with only explicitly granted capabilities. 

Pod Security Policy allows you to set smart defaults for your Pods, and enforce controls you want to enable across your fleet. 

The policies you define should be specific to the needs of your application

**Resolution**: Use security policies for pods to restrict permissions to those needed to be effective.

## Examples

Example of **incorrect** code:

```terraform
resource "google_container_cluster" "bad_example" {
	pod_security_policy_config {
        enabled = "false"
	}
}
```

Example of **correct** code:

```terraform
resource "google_container_cluster" "good_example" {
	pod_security_policy_config {
        enabled = "true"
	}
}
```