## flux bootstrap github

Bootstrap toolkit components in a GitHub repository

### Synopsis

The bootstrap github command creates the GitHub repository if it doesn't exists and
commits the toolkit components manifests to the main branch.
Then it configures the target cluster to synchronize with the repository.
If the toolkit components are present on the cluster,
the bootstrap command will perform an upgrade if needed.

```
flux bootstrap github [flags]
```

### Examples

```
  # Create a GitHub personal access token and export it as an env var
  export GITHUB_TOKEN=<my-token>

  # Run bootstrap for a private repo owned by a GitHub organization
  flux bootstrap github --owner=<organization> --repository=<repo name>

  # Run bootstrap for a private repo and assign organization teams to it
  flux bootstrap github --owner=<organization> --repository=<repo name> --team=<team1 slug> --team=<team2 slug>

  # Run bootstrap for a repository path
  flux bootstrap github --owner=<organization> --repository=<repo name> --path=dev-cluster

  # Run bootstrap for a public repository on a personal account
  flux bootstrap github --owner=<user> --repository=<repo name> --private=false --personal=true

  # Run bootstrap for a private repo hosted on GitHub Enterprise using SSH auth
  flux bootstrap github --owner=<organization> --repository=<repo name> --hostname=<domain> --ssh-hostname=<domain>

  # Run bootstrap for a private repo hosted on GitHub Enterprise using HTTPS auth
  flux bootstrap github --owner=<organization> --repository=<repo name> --hostname=<domain> --token-auth

  # Run bootstrap for a an existing repository with a branch named main
  flux bootstrap github --owner=<organization> --repository=<repo name> --branch=main

```

### Options

```
  -h, --help                    help for github
      --hostname string         GitHub hostname (default "github.com")
      --interval duration       sync interval (default 1m0s)
      --owner string            GitHub user or organization name
      --path safeRelativePath   path relative to the repository root, when specified the cluster sync will be scoped to this path
      --personal                is personal repository
      --private                 is private repository (default true)
      --repository string       GitHub repository name
      --ssh-hostname string     GitHub SSH hostname, to be used when the SSH host differs from the HTTPS one
      --team stringArray        GitHub team to be given maintainer access
```

### Options inherited from parent commands

```
      --arch arch                  cluster architecture, available options are: (amd64, arm, arm64) (default amd64)
      --branch string              default branch (for GitHub this must match the default branch setting for the organization) (default "main")
      --cluster-domain string      internal cluster domain (default "cluster.local")
      --components strings         list of components, accepts comma-separated values (default [source-controller,kustomize-controller,helm-controller,notification-controller])
      --components-extra strings   list of components in addition to those supplied or defaulted, accepts comma-separated values
      --context string             kubernetes context to use
      --image-pull-secret string   Kubernetes secret name used for pulling the toolkit images from a private registry
      --kubeconfig string          path to the kubeconfig file (default "~/.kube/config")
      --log-level logLevel         log level, available options are: (debug, info, error) (default info)
  -n, --namespace string           the namespace scope for this operation (default "flux-system")
      --network-policy             deny ingress access to the toolkit controllers from other namespaces using network policies (default true)
      --registry string            container registry where the toolkit images are published (default "ghcr.io/fluxcd")
      --timeout duration           timeout for this operation (default 5m0s)
      --token-auth                 when enabled, the personal access token will be used instead of SSH deploy key
      --verbose                    print generated objects
  -v, --version string             toolkit version (default "latest")
      --watch-all-namespaces       watch for custom resources in all namespaces, if set to false it will only watch the namespace where the toolkit is installed (default true)
```

### SEE ALSO

* [flux bootstrap](flux_bootstrap.md)	 - Bootstrap toolkit components

