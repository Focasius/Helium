# Helium 项目贡献指南

感谢您对 Helium 项目的关注！本指南将帮助您了解如何有效地为项目做出贡献。无论您是经验丰富的开发者还是开源新手，我们都欢迎您的参与。

## 开发环境配置

### 必需组件
- **操作系统**: Linux (推荐 Ubuntu 22.04 LTS)
- **Rust 工具链**: 最新稳定版 (通过 https://rustup.rs/ 安装)
- **Vulkan 开发库**: `libvulkan-dev` (Ubuntu) / `vulkan-devel` (Fedora)
- **构建工具**:
  - `make` (GNU Make 4.0+)
  - `g++` (用于本地依赖编译)

### 环境设置
```bash
# 安装 Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env

# 安装构建依赖
sudo apt install -y build-essential libvulkan-dev
```

### 项目初始化
```bash
git clone https://github.com/your-project/helium.git
cd helium
make setup  # 安装子模块和依赖项
make build  # 编译整个项目
```

## 代码规范

### 语言规范
- **Rust**: 遵循官方https://doc.rust-lang.org/1.0.0/style/，使用 `rustfmt` 格式化
- **Bash**: 遵循 https://google.github.io/styleguide/shellguide.html

### 通用规则
1. 所有公共 API 必须有文档注释
2. 新功能必须附带单元测试
3. 避免引入第三方依赖，必需依赖需经讨论
4. 保持模块化设计，单一职责原则

## 提交规范

采用https://www.conventionalcommits.org/：
```
<类型>[可选 范围]: <描述>

[可选 正文]

[可选 脚注]
```

**有效提交类型**:
| 类型     | 描述                   |
| -------- | ---------------------- |
| feat     | 新增功能               |
| fix      | 修复缺陷               |
| refactor | 重构代码（不改变功能） |
| docs     | 文档更新               |
| test     | 测试相关               |
| chore    | 构建过程或辅助工具变更 |
| perf     | 性能优化               |
| ci       | CI 配置变更            |

**示例**:
```
feat(render): 添加 Vulkan 纹理支持

实现 VKTexture 结构体支持基础纹理映射
新增 texture 单元测试套件

关闭 #123
```

## PR 流程

1. 从 `main` 创建特性分支 (`feat/xxx`, `fix/xxx`)
2. 开发完成后运行完整测试套件：
   ```bash
   make test-all  # 包括 Rust 单元测试和 .NET 集成测试
   ```
3. 确保代码通过静态分析：
   ```bash
   make lint
   ```
4. 推送分支并创建 PR 到 `dev` 分支
5. 填写 PR 模板，描述变更内容和影响
6. 等待 CI 构建通过后，请求核心成员审查
7. 根据反馈修改，直到获得 2 个 LGTM (Looks Good To Me)
8. 由维护者合并

## 行为准则

我们遵守https://www.contributor-covenant.org/version/2/0/code_of_conduct/：
- 尊重不同背景和经验水平的贡献者
- 建设性表达意见，避免人身攻击
- 禁止任何形式的歧视或骚扰行为
- 争议通过项目管理委员会仲裁解决

## 沟通渠道

| 渠道                   | 用途                   |
| ---------------------- | ---------------------- |
| [GitHub Issues]        | Bug 报告和功能请求     |
| [GitHub Discussions]   | 设计讨论和提案         |


> 您的每一行代码都将帮助构建更好的虚拟世界！