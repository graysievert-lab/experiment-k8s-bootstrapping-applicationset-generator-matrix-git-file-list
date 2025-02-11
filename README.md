# Experiment: Cluster bootstrapping using ArgoCD ApplicationSet and matrix-git:file-list generator

Assumption: Repo contains necessary charts and valuefiles, or valuefiles for charts in public Helm repos, or manifests.
Supposedly resonable for the cluster tooling repo.

Cons:

- configs resemble application manifest too much. Though could be optimised further.
- Still ended up with helm-style go-templating.
- repos in ArgoCD can't be project scoped

Pros:

- even less copy pasting.
- copy pasting happens in one file
- one config as a list of applications fully decoupled from kubernetes applications folders/repos.
- approach allowes to reference kubernetes applications stored anywhere: the ones that are in the same repo as the appset, and the ones that are stored in some other repos
- yaml anchors could be used in config file. This is a quick way to mass change `repoURL` or any other value if it repeats a lot.

VERDICT: the best variant so far.

Closest alternative: App of Apps with helm template to render applications and value file containing the same config as here.
