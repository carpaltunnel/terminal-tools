# terminal-tools
List of useful terminal tools that I enjoy.  Saved here for posterity so I don't forget them.

1.  `kitty` - [kiTTY](https://sw.kovidgoyal.net/kitty/) - Great modern terminal with ncurses like tabs
2.  `ghostty` - [GhosTTY](https://ghostty.org/) - Another great modern terminal, this one has graphical window decorator tabs
    1.  GhosTTY theme browser : `ghostty +list-themes`
3.  `btop` - [btop](https://github.com/aristocratos/btop) - Modern/awesome `top` replacement
4.  `zellij` - [zellij](https://zellij.dev/) - Modern/awesome terminal multiplexer (like `tmux` and/or `screen`, but better)
    5. `zellij-datetime` - [zellij-datetime](https://github.com/h1romas4/zellij-datetime) - Zellij plugin that adds the date/time at the top right.
    6. See "Zellij-DateTime Layout Config" under "Configurations" below for the configuration file.
6.  `glances` - [glances](https://github.com/nicolargo/glances) - Similar to `top`/`btop` but can also monitor containers (docker/podman) and potentially other resources.
7.  `lazygit` - [lazygit](https://github.com/jesseduffield/lazygit) - TUI for Git
8.  `k9s` - [k9s](https://github.com/derailed/k9s) - TUI for k8s
9.  `lazydocker` - [lazydocker](https://github.com/jesseduffield/lazydocker) - TUI for docker (works with Podman - See Configuration section at the bottom for how to set things up for usage with Podman)
10.  `bat` - [bat](https://github.com/sharkdp/bat) - `cat` but with auto-paging and syntax highlighting
11.  `broot` - [broot](https://github.com/Canop/broot) - TUI file system explorer with previews
12.   `wttr.in` - [wttr.in](https://github.com/chubin/wttr.in) - Terminal weather forecast (`curl wttr.in?M`)
13.  `minikube` - [minikube](https://minikube.sigs.k8s.io/docs/) - Local Kubernetes cluster / playground
14.  `podman` - [podman](https://podman.io/) - Rootless, open source, Docker Desktop (and CLI w/ alias) replacement.  100% interchangeable with Docker commands so `alias docker="podman"` is suggested if your fingers are accustomed to typing "docker".
15.  `starship` - [Starship](https://starship.rs/) - Terminal decorator with lots of helpful info.  "[Tokyo Night](https://starship.rs/presets/#tokyo-night)" is my favorite theme so far (replace 🍏 with 🐧 and add error return code - see Configuration/Starship).
     1.   To function properly, this requires a proper [NerdFont](https://www.nerdfonts.com/) to be installed.  I like [DroidSansM](https://www.programmingfonts.org/#droid-sans).
16.  `helix` - [helix](https://helix-editor.com/) Full fledged terminal IDE.  Not ""just"" a text editor.  Key bindings are __similar__ to VIM but many differ, which takes some getting used to.  But, LSP support and standard IDE functionality (go to definition, find all references, rename symbol, etc) make it worth adapting to.
17.  `neofetch` - [neofetch **deprecated**](https://github.com/dylanaraps/neofetch) - Simple but helpful system information.  Non-deprecated alternatives can be found below (untested - I'll pare this list down to one primary and replace `neofetch` after evaluation) : 
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
### Lazydocker with Podman (non-root)
```bash
systemctl --user enable --now podman.socket
# You'll probably want to put this in your .bashrc or relevant RC file for your shell
export DOCKER_HOST=unix:///run/user/1000/podman/podman.sock
# lazydocker invokes the "docker" command so you MUST alias it to Podman to work.
alias docker='podman' # This is a duplicate of one of the aliases in a section above - only do it once.
```

### Starship (Tokyo Night Preset)
```bash
starship preset tokyo-night -o ~/.config/starship.toml
```

Add return code to prompt when an error occurs (`~/.config/starship.toml`): 
```bash
# Update the "format" setting to use a penguin and include the command status (replace or modify the first section of the config file to be) :
format = """
[░▒▓](#a3aed2)\
[ 🐧 ](bg:#a3aed2 fg:#090c0c)\
[](bg:#769ff0 fg:#a3aed2)\
$directory\
[](fg:#769ff0 bg:#394260)\
$git_branch\
$git_status\
[](fg:#394260 bg:#212736)\
$nodejs\
$rust\
$golang\
$php\
[](fg:#212736 bg:#1d2230)\
$time\
[ ](fg:#1d2230)\
$status\
\n$character"""

## Leave the rest of this unchanged ##

# Add this at the end of the configuration file
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

