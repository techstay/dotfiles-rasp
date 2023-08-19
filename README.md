# dotfile-rasp

我的树莓派 dotfiles。

其实这个树莓派的 dotfiles 本来是放在主 dotfiles 的一个分支中，这样部分配置文件可以共享。但是实际用下来我发现，这样反倒不是很好用。因为树莓派分支是挂在主分支上的，而且要经常 rebase 到主分支上，这样每次同步的时候都很麻烦，因为提交记录一直在变。这反而和 dotfiles 为了方便同步配置文件的初衷相悖。

而且我的主 dotfiles 使用 arch，树莓派的系统基于 debian，很多配置也不通用，搞着搞着就乱了。所以干脆再开一个仓库专门用来放树莓派的 dotfiles。这次重新整理 dotfiles，顺便也去掉了之前塞在 shell 里面的一些花里胡哨的东西。其实本来默认配置就不错，加的东西多了反而比较复杂，没有那种开箱即用的效果了。当然其实最麻烦的还是代理问题，如果没有这个问题的话，大不了弄个启动脚本，把各种安装步骤全写进去。但是有这个代理问题，就很尴尬，只能说凑合着用得了。

## 开始使用

### 安装

安装一些必备包

```sh
sudo apt update && sudo apt upgrade -y && sudo apt install yadm fzf zsh git lua5.4 exa
```

tailscale

```sh
curl -fsSL https://tailscale.com/install.sh | sh
```

docker

```sh
sudo apt install docker.io docker-compose
sudo gpasswd docker -a "$(whoami)"
```

nala，从[项目网站](https://gitlab.com/volian/nala/-/releases)下载deb包，然后安装。

克隆 dotfiles，然后将终端设置为 zsh`chsh -s /bin/zsh`。

```sh
yadm clone https://github.com/techstay/dotfile-rasp.git
```

bootstrap 脚本里目前没想好应该写点什么东西，以后应该会加一点安装脚本之类的。不过再想到那个网络问题，顿时有点头痛。哼哧哼哧写了半天，然后后面安装不上，那可太尴尬了。之前 cloudflare 的 warp 我觉得挺好用的，但是尝试安装之后发现，它不支持 arm 平台，实在是太可惜了。


### 笔记

我的[笔记](https://studynotes.techstay.tech/notes/linux/raspberry.html)里也记录了一些关于树莓派的玩法，可以作为参考。

## 同步文件

- zsh
- fish
- git
- ssh
- proxy
- docker
  - adguardhome
  - heimdall
  - kitty
  - portainer
  - stashapp
  - uptime-kuma
  - qinglong
