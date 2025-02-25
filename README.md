# terminal-tools
List of useful terminal tools that I enjoy.  Saved here for posterity so I don't forget them.

1.  `ghostty` - [GhosTTY](https://ghostty.org/) - Great modern terminal
    1.  GhosTTY theme browser : `ghostty +list-themes`
2.  `kitty` - [kiTTY](https://sw.kovidgoyal.net/kitty/) - A close second to GhosTTY for a modern terminal
3.  `btop` - [btop](https://github.com/aristocratos/btop) - Modern/awesome `top` replacement
4.  `lazygit` - [lazygit](https://github.com/jesseduffield/lazygit) - TUI for Git
5.  `k9s` - [k9s](https://github.com/derailed/k9s) - TUI for k8s
6.  `lazydocker` - [lazydocker](https://github.com/jesseduffield/lazydocker) - TUI for docker (works with Podman)
7.  `bat` - [bat](https://github.com/sharkdp/bat) - `cat` but with auto-paging and syntax highlighting
8.  `broot` - [broot](https://github.com/Canop/broot) - TUI file system explorer with previews
9.   `wttr.in` - [wttr.in](https://github.com/chubin/wttr.in) - Terminal weather forecast (`curl wttr.in?M`)
10.  `minikube` - [minikube](https://minikube.sigs.k8s.io/docs/) - Local Kubernetes cluster / playground
11.  `podman` - [podman](https://podman.io/) - Rootless, open source, Docker Desktop (and CLI w/ alias) replacement.  100% interchangeable with Docker commands so `alias docker="podman"` is suggested if your fingers are accustomed to typing "docker".
12.  `starship` - [Starship](https://starship.rs/) - Terminal decorator with lots of helpful info.  "[Tokyo Night](https://starship.rs/presets/#tokyo-night)" is my favorite theme so far (replace 🍏 with 🐧 and add error return code - see Configuration/Starship).

## Aliases
Related useful aliases
```bash
alias docker="podman" # though it's probably better to link $PATH/docker to $PATH/podman
alias minikubestart="minkube start --driver=podman --container-runtime=cri-o"

```

## Configurations
### Starship (Tokyo Night Preset)
Add return code to prompt when an error occurs : 
```bash
[status]
style = "bold red"
format = "[\\[$status\\]]($style) "
disabled = false
pipestatus = true
```
