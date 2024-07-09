## 配置新的Ubuntu系统

### 安装字体

1、去nerd font官网下载你想用的字体

2、执行以下命令进行安装

```bash
sudo unzip ${font} -d /usr/share/fonts/${font}
cd /usr/share/fonts/${font}
sudo mkfontscale
sudo mkfontdir
fc-cahe -rv
```



## 安装虚拟终端terminal

```bash
sudo add-apt-repository ppa:gnome-terminator
sudo apt update
sudo apt install terminator
```

```bash
[global_config]
  focus = system
  title_transmit_bg_color = "#d30102"
  suppress_multiple_term_dialog = True
[keybindings]
[profiles]
  [[default]]
    background_color = "#2e3436"
    background_darkness = 0.9
    cursor_color = "#2D2D2D"
    font = Monospace Regular 14
    foreground_color = "#8ae234"
    show_titlebar = False
    scrollback_infinite = True
    palette = "#2d2d2d:#f2777a:#99cc99:#ffcc66:#6699cc:#cc99cc:#66cccc:#d3d0c8:#747369:#f2777a:#99cc99:#ffcc66:#6699cc:#cc99cc:#66cccc:#f2f0ec"
    use_system_font = False
    copy_on_selection = True
[layouts]
  [[default]]
    [[[child1]]]
      type = Terminal
      parent = window0
      profile = default
    [[[window0]]]
      type = Window
      parent = ""
[plugins]

```





## 安装Neovim

在GitHub中下载对应版本的Neovim安装包，

解压在你想让它呆在的位置

然后将这个目录添加到`.bashrc`中

```bash
PATH="$PATH:/usr/sbin:/sbin"
PATH="$PATH:$HOME/software/nvim-linux64"
```



## 安装zsh 以及 oh-my-zsh 并简单配置

**安装zsh**

```bash
# 更新软件源
sudo apt update && sudo apt upgrade -y
# 安装 zsh git curl
sudo apt install zsh git curl -y
```

```bash
chsh -s /bin/zsh
```

**安装 oh-my-zsh**

| Method                                           | Command                                                      |
| :----------------------------------------------- | :----------------------------------------------------------- |
| **curl**                                         | `sh -c "$(curl -fsSL https://install.ohmyz.sh/)"`            |
| **wget**                                         | `sh -c "$(wget -O- https://install.ohmyz.sh/)"`              |
| **fetch**                                        | `sh -c "$(fetch -o - https://install.ohmyz.sh/)"`            |
| 国内curl[镜像](https://gitee.com/pocmon/ohmyzsh) | `sh -c "$(curl -fsSL https://gitee.com/pocmon/ohmyzsh/raw/master/tools/install.sh)"` |
| 国内wget[镜像](https://gitee.com/pocmon/ohmyzsh) | `sh -c "$(wget -O- https://gitee.com/pocmon/ohmyzsh/raw/master/tools/install.sh)"` |

## 配置clangd + llvm + vscode

**安装llvm**

```bash
sudo apt install llvm
```

**安装clang**

```bash
sudo apt install clang
```





