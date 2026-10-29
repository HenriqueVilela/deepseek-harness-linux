# DeepSeek Harness

[English](README.md) | 中文

DeepSeek Harness（`dsh`）是由 [DeepSeek AI](https://deepseek.com) 开发的开源 agent harness（智能体框架）。

它构建于**一切皆插件**的架构之上，由 [Cordis](https://github.com/cordiverse/cordis) 驱动，其设计参见论文 [_A Programming Paradigm for Spatiotemporal Composability_](https://arxiv.org/abs/2608.25512)。

文档：[https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## 开发者预览

DeepSeek Harness 处于 _开发者预览_ 阶段，正在快速迭代。**未来将出现破坏兼容性的变更。**

运行本项目前，请阅读[安全说明](SAFETY.zh.md)。

<a id="run"></a>

## 运行

### 通过 `npm` 运行

安装 `Node.js`，然后运行：

```sh
npx @deepseek-ai/dsh web
```

该命令默认会在 `http://127.0.0.1:3080` 启动 Web UI，本机启动时还会用默认浏览器打开页面。通过 SSH 启动时只打印宿主机 URL，因为本地转发地址由 SSH 客户端或编辑器持有。传入 `--no-open` 可仅运行服务器而不打开浏览器。详见 [Web UI 指南](docs/user/guide/index.zh.md)。

<a id="run-from-source"></a>

### 从源码运行

如需从仓库源码运行：

```sh
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` 会准备仓库产物。`pnpm dsh web` 会直接使用这些已构建产物，不会重新构建。

### Linux（Ubuntu / Debian）

#### 桌面端应用（.AppImage 与 .deb）

DeepSeek Harness 桌面端支持 Linux，提供面向 `x64` 和 `arm64` 架构的 **AppImage** 与 **Debian 安装包（.deb）**。

##### 运行 AppImage

```sh
# 赋予执行权限并启动
chmod +x deepseek-harness-*-linux-x64.AppImage
./deepseek-harness-*-linux-x64.AppImage
```

> [!TIP]
> 在 Ubuntu 24.04 及更高版本上，如系统尚未预装 FUSE 2，请安装 `libfuse2t64`：
> ```sh
> sudo apt update && sudo apt install -y libfuse2t64
> ```

##### 安装 Debian 软件包（.deb）

```sh
sudo apt update
sudo apt install -y ./deepseek-harness-*-linux-amd64.deb

# 从应用程序启动器或终端运行
deepseek-harness
```

#### 从源码构建并运行 Linux 桌面端

1. **安装系统依赖：**
   - Node.js >= 24.9.0 与 pnpm >= 11
   - 基础编译链与 Python 3：
     ```sh
     sudo apt update && sudo apt install -y curl git python3 build-essential
     ```

2. **克隆仓库并安装依赖：**
   ```sh
   git clone https://github.com/deepseek-ai/deepseek-harness.git
   cd deepseek-harness
   pnpm install
   ```

3. **以开发模式运行桌面端：**
   ```sh
   pnpm run dev:desktop
   ```

4. **打包 Linux 本地安装包（.AppImage 与 .deb）：**
   ```sh
   # 打包 x64
   pnpm run package:desktop:linux:x64

   # 打包 ARM64
   pnpm run package:desktop:linux:arm64
   ```
   构建产物输出至 `apps/desktop/.desktop-build/targets/linux-x64/artifacts/` 目录。

## 社区与支持

- 通过 [GitHub Discussions](https://github.com/deepseek-ai/deepseek-harness/discussions) 提交反馈或 bug 报告。
- 为你的插件仓库添加 [`dsh-plugin`](https://github.com/topics/dsh-plugin) 话题，便于被发现。
- 欢迎加入 DeepSeek Harness 企微群！扫描下方二维码填写入群问卷，小助手会定期发送入群邀请。

<table>
  <thead>
    <tr>
      <th align="center">入群问卷</th>
      <th align="center">微信公众号</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><a href="https://trtgsjkv6r.feishu.cn/share/base/form/shrcnIt5twSVdLGD52KJBckGCgg"><img src="https://cdn.deepseek.com/harness/readme/community-wecom-survey.png" alt="DeepSeek Harness 入群问卷二维码" width="180" height="180"></a></td>
      <td align="center"><img src="https://cdn.deepseek.com/harness/readme/community-wechat-official-account.png" alt="DeepSeek Harness 团队微信公众号二维码" width="180" height="180"></td>
    </tr>
  </tbody>
</table>

## 参与贡献

参见 [CONTRIBUTING.md](CONTRIBUTING.zh.md)。

## 开发

请先阅读[开发指南](docs/development.zh.md)与[架构文档](docs/architecture.zh.md)。

`pnpm run dev:web` 会在一个终端里完成构建、启动，并在源码修改时重建 client bundle；`make help` 列出 Web 与 Desktop 对应的 Make target。完整表格见开发指南的「应用命令」一节。

面向 agent：请遵循 [AGENTS.md](AGENTS.md)。

## 引用

```bibtex
@misc{deepseek-harness2026,
  title={DeepSeek Harness: Everything is a Plugin},
  author={DeepSeek-AI},
  year={2026},
  publisher={GitHub},
  howpublished={\url{https://github.com/deepseek-ai/deepseek-harness}},
}
```

## 许可证

[MIT](LICENSE)

第三方依赖及其许可证见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。
