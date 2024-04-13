# App of Apps

This repository contains the root application responsible for deploying all
other applications in my private Kubernetes cluster through Argo CD. It
implements the Argo CD App-of-Apps pattern.

## Helm Charts & OLM

Some applications that are deployed through this repository do not have
officially supported Helm charts. In these cases, I have created my own. Some
applications are deployed through the Operator Lifecycle Manager (OLM) instead,
and in this repository they are added as `Subscription` resources.

## CI/CD

There is limited opportunity for CI/CD in this repository as it exists today.
Where applicable, ephemeral environments may be created through Argo's
`ApplicationSet` resource, which has support for GitHub merge requests. To show
differences in how applications will turn out, a workflow was added to run
`argocd app diff` for the root application, with plans to expand to all
applications that are being modified in the future.
