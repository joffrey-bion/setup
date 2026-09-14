# Kubernetes CLI setup

For more info about the actual cluster(s) setup, see [kubernetes-config](https://github.com/BroTeam/kubernetes-config)
(private).

## Basic kubectl CLI

If you just need `kubectl`:
```
winget install Kubernetes.kubectl
```

If you have some externally-provided config, write it as a `~/.kube/config` file.

## Digital Ocean

```
winget install DigitalOcean.Doctl
```

## Helm

```
winget install Helm.Helm
```

## Krew

Install [Krew](https://krew.sigs.k8s.io/) to manage k8s plugins:

```powershell
winget install krew
krew install krew
[Environment]::SetEnvironmentVariable("Path", [Environment]::GetEnvironmentVariable("Path", "User") + ";$HOME\.krew\bin", "User")
```

> [!NOTE]
> The `krew install krew` might seem weird, but it installs the Krew plugin for k8s (`kubectl-krew`) under `~/.krew/bin`,
> so we can later run `kubectl krew <args>`

> [!NOTE]
> `$HOME\.krew\bin` contains all plugins installed by Krew. Adding it to the `PATH` effectively makes them available to
> `kubectl` as subcommands.
