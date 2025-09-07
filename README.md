# terminal-tools
List of useful terminal tools that I enjoy.  Saved here for posterity so I don't forget them.

1.  `ghostty` - [GhosTTY](https://ghostty.org/) - Great modern terminal
    1.  GhosTTY theme browser : `ghostty +list-themes`
2.  `kitty` - [kiTTY](https://sw.kovidgoyal.net/kitty/) - A close second to GhosTTY for a modern terminal
3.  `btop` - [btop](https://github.com/aristocratos/btop) - Modern/awesome `top` replacement
4.  `zellij` - [zellij](https://zellij.dev/) - Modern/awesome terminal multiplexer (like `tmux` and/or `screen`, but better)
    5. `zellij-datetime` - [zellij-datetime](https://github.com/h1romas4/zellij-datetime) - Zellij plugin that adds the date/time at the top right.
    6. See "Zellij-DateTime Layout Config" under "Configurations" below for the configuration file.
6.  `glances` - [glances](https://github.com/nicolargo/glances) - Similar to `top`/`btop` but can also monitor containers (docker/podman) and potentially other resources.
7.  `lazygit` - [lazygit](https://github.com/jesseduffield/lazygit) - TUI for Git
8.  `k9s` - [k9s](https://github.com/derailed/k9s) - TUI for k8s
9.  `lazydocker` - [lazydocker](https://github.com/jesseduffield/lazydocker) - TUI for docker (works with Podman)
10.  `bat` - [bat](https://github.com/sharkdp/bat) - `cat` but with auto-paging and syntax highlighting
11.  `broot` - [broot](https://github.com/Canop/broot) - TUI file system explorer with previews
12.   `wttr.in` - [wttr.in](https://github.com/chubin/wttr.in) - Terminal weather forecast (`curl wttr.in?M`)
13.  `minikube` - [minikube](https://minikube.sigs.k8s.io/docs/) - Local Kubernetes cluster / playground
14.  `podman` - [podman](https://podman.io/) - Rootless, open source, Docker Desktop (and CLI w/ alias) replacement.  100% interchangeable with Docker commands so `alias docker="podman"` is suggested if your fingers are accustomed to typing "docker".
15.  `starship` - [Starship](https://starship.rs/) - Terminal decorator with lots of helpful info.  "[Tokyo Night](https://starship.rs/presets/#tokyo-night)" is my favorite theme so far (replace 🍏 with 🐧 and add error return code - see Configuration/Starship).
16.  `neofetch` - [neofetch **deprecated**](https://github.com/dylanaraps/neofetch) - Simple but helpful system information.  Non-deprecated alternatives can be found below (untested - I'll pare this list down to one primary and replace `neofetch` after evaluation) : 
     1.   [fastfetch](https://github.com/fastfetch-cli/fastfetch)
     2.   [screenfetch](https://github.com/KittyKatt/screenFetch)
     3.   [macchina](https://github.com/Macchina-CLI/macchina)
     4.   [nerdfetch](https://github.com/ThatOneCalculator/NerdFetch)
     5.   [hyfetch](https://github.com/hykilpikonna/hyfetch)

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
### Zellij

**DateTime Plugin, Layout Configuration**
`~/.config/zellij/layouts/default.kdl`
```
layout {
    pane size=1 borderless=true {
        plugin location="file:~/.config/zellij/plugins/zellij-datetime.wasm"
    }
    pane size=1 borderless=true {
        plugin location="tab-bar"
    }
    pane
    pane size=1 borderless=true {
        plugin location="status-bar"
    }
}
```

