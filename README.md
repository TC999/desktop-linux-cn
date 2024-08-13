### [GitHub Desktop](https://desktop.github.com) - Linux分支

[[CI](https://github.com/shiftkey/desktop/actions/workflows/ci.yml/badge.svg)](https://github.com/shiftkey/desktop/actions/workflows/ci.yml)

[GitHub Desktop](https://desktop.github.com/) 是一款基于 [Electron](https://www.electronjs.org/) 的开源 GitHub 应用程序。它使用 [TypeScript](https://www.typescriptlang.org) 编写，并且采用了 [React](https://reactjs.org/)。

<picture>
  <source
    srcset="https://user-images.githubusercontent.com/634063/202742848-63fa1488-6254-49b5-af7c-96a6b50ea8af.png"
    media="(prefers-color-scheme: dark)"
  />
  <img
    width="1072"
    src="https://user-images.githubusercontent.com/634063/202742985-bb3b3b94-8aca-404a-8d8a-fd6a6f030672.png"
    alt="GitHub Desktop 应用程序的截图，展示正在查看和提交更改的过程，其中有两个共同作者被归功"
  />
</picture>

#### 这个仓库是做什么的？

这个仓库包含了一些针对上游 `desktop/desktop` 仓库的特定补丁，用于支持 Linux 系统的使用。

此外，它还发布了适用于不同 Linux 发行版的版本：

- AppImage (`.AppImage`)
- Debian (`.deb`)
- RPM (`.rpm`)

#### 通过包管理器安装

您可以使用操作系统自带的包管理器来安装 `github-desktop` 并保持其更新至最新版本，在 Debian 和基于 RPM 的发行版上。

##### Debian/Ubuntu

有两个可用的 APT 包源，均托管在美国。您只需添加其中一个即可，因为它们都是基于此仓库发布的版本生成的。

###### @shiftkey 包源

```sh
wget -qO - https://apt.packages.shiftkey.dev/gpg.key | gpg --dearmor | sudo tee /usr/share/keyrings/shiftkey-packages.gpg > /dev/null
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/shiftkey-packages.gpg] https://apt.packages.shiftkey.dev/ubuntu/ any main" > /etc/apt/sources.list.d/shiftkey-packages.list'
```

###### @mwt 包源

```sh
wget -qO - https://mirror.mwt.me/shiftkey-desktop/gpgkey | gpg --dearmor | sudo tee /usr/share/keyrings/mwt-desktop.gpg > /dev/null
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/mwt-desktop.gpg] https://mirror.mwt.me/shiftkey-desktop/deb/ any main" > /etc/apt/sources.list.d/mwt-desktop.list'
```

##### 安装

配置好包源后，运行以下命令来安装应用程序：

```sh
sudo apt update && sudo apt install github-desktop
```

##### Red Hat/CentOS/Fedora

有两个可用的 RPM 包源，均托管在美国。您只需添加其中一个即可，因为它们都是基于此仓库发布的版本生成的。

###### @shiftkey 包源

```sh
sudo rpm --import https://rpm.packages.shiftkey.dev/gpg.key
sudo sh -c 'echo -e "[shiftkey-packages]\nname=GitHub Desktop\nbaseurl=https://rpm.packages.shiftkey.dev/rpm/\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://rpm.packages.shiftkey.dev/gpg.key" > /etc/yum.repos.d/shiftkey-packages.repo'
```

###### @mwt 包源

```sh
sudo rpm --import https://mirror.mwt.me/shiftkey-desktop/gpgkey
sudo sh -c 'echo -e "[mwt-packages]\nname=GitHub Desktop\nbaseurl=https://mirror.mwt.me/shiftkey-desktop/rpm\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://mirror.mwt.me/shiftkey-desktop/gpgkey" > /etc/yum.repos.d/mwt-packages.repo'
```

##### 安装

配置好包源后，运行以下命令来安装应用程序：

```sh
# 如果您的包管理器是 yum
sudo yum install github-desktop

# 如果您的包管理器是 dnf
sudo dnf install github-desktop

# 如果您的包管理器是 zypper
sudo zypper ref && sudo zypper in github-desktop
```

##### OpenSUSE

有两个可用的 RPM 包源，均托管在美国。您只需添加其中一个即可，因为它们都是基于此仓库发布的版本生成的。

###### @shiftkey 包源

```sh
sudo rpm --import https://rpm.packages.shiftkey.dev/gpg.key
sudo sh -c 'echo -e "[shiftkey-packages]\nname=GitHub Desktop\nbaseurl=https://rpm.packages.shiftkey.dev/rpm/\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://rpm.packages.shiftkey.dev/gpg.key" > /etc/zypp/repos.d/shiftkey-packages.repo'
```

###### @mwt 包源

```sh
sudo rpm --import https://mirror.mwt.me/shiftkey-desktop/gpgkey
sudo sh -c 'echo -e "[mwt-packages]\nname=GitHub Desktop\nbaseurl=https://mirror.mwt.me/shiftkey-desktop/rpm\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://mirror.mwt.me/shiftkey-desktop/gpgkey" > /etc/zypp/repos.d/mwt-packages.repo'
```

##### 安装

```sh
sudo zypper ref && sudo zypper in github-desktop
```

#### 其他发行版

##### Arch Linux

Arch Linux 用户可以从 [AUR](https://aur.archlinux.org/packages/github-desktop-bin/) 安装 GitHub Desktop。

`gnome-keyring` 是必需的，并且守护进程必须在登录时或启动 X 服务器时启动。通常这由显示管理器处理，但在其他情况下，遵循 [Arch Wiki](https://wiki.archlinux.org/index.php/GNOME/Keyring#Using_the_keyring_outside_GNOME) 上的说明可以解决无法保存登录凭据的问题。

##### 跨平台包

GitHub Desktop 同样作为 [Flatpak](https://github.com/flathub/io.github.shiftey.Desktop) 和 [AppImage](https://appimage.github.io/GitHubDesktop/) 提供跨平台支持。

##### deb-get

Debian/Ubuntu 用户也可以直接从这个仓库使用 `deb-get` 来安装：`deb-get install github-desktop`。

#### 已知问题

如果您在使用 Desktop 时遇到问题，请参阅 [已知问题](docs/known-issues.md#linux) 文档以获取指导和常见限制的解决方案。

如果您的包管理器仍在尝试连接到 PackageCloud，请参阅 [清理说明](docs/known-issues.md#the-packagecloud-package-feed-is-no-longer-working)，了解有关迁移的详细信息。

#### 更多信息

请查阅上游 [GitHub Desktop 项目](https://github.com/desktop/desktop#github-desktop) 的 [README](https://github.com/desktop/desktop#github-desktop) 和 [desktop.github.com](https://desktop.github.com/) 了解更多关于 GitHub Desktop 的产品信息。

参见我们的 [入门文档](https://docs.github.com/en/desktop/overview/getting-started-with-github-desktop) 以了解如何设置、验证和配置 GitHub Desktop。

#### 许可

**[MIT](LICENSE)**

MIT 许可协议并不涵盖 GitHub 的商标，包括徽标设计。GitHub 保留对其所有商标和版权的权利。GitHub 的徽标包括但不限于位于以下文件夹中的带有 "logo" 文件名标题的 Invertocat 设计：[logos](app/static/logos)。

GitHub® 及其各种变体以及 Invertocat 商标均为 GitHub 的商标或注册商标。在使用 GitHub 的徽标时，请确保遵守 GitHub 的 [徽标指南](https://github.com/logos)。
