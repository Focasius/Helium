# Helium Project Contribution Guide

Thank you for your interest in the Helium project! This guide will help you understand how to effectively contribute to our open-source initiative. Whether you're an experienced developer or new to open-source, your contributions are welcome and valued.

## Development Environment Setup

### Prerequisites
- **OS**: Linux (Ubuntu 22.04 LTS recommended)
- **Rust Toolchain**: Latest stable version (via https://rustup.rs/)
- **Vulkan Libraries**: `libvulkan-dev` (Ubuntu) / `vulkan-devel` (Fedora)
- **Build Tools**:
  - `make` (GNU Make 4.0+)
  - `g++` (for native dependency compilation)

### Environment Setup
```bash
# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env

# Install build dependencies
sudo apt install -y build-essential libvulkan-dev
```

### Project Initialization
```bash
git clone https://github.com/helium-project/helium.git
cd helium
make setup  # Installs submodules and dependencies
make build  # Compiles the entire project
```

## Coding Standards

### Language Conventions
- **Rust**: Follow official https://doc.rust-lang.org/1.0.0/style/, format with `rustfmt`
- **Bash**: Follow https://google.github.io/styleguide/shellguide.html

### General Rules
1. All public APIs must include documentation comments
2. New features require accompanying unit tests
3. Avoid adding dependencies unless essential (requires discussion)
4. Maintain modular design with single-responsibility principle
5. Use descriptive variable/function names (avoid abbreviations)

## Commit Convention

We follow https://www.conventionalcommits.org/:
```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

**Valid commit types**:
| Type     | Description                                  |
| -------- | -------------------------------------------- |
| feat     | New feature implementation                   |
| fix      | Bug resolution                               |
| refactor | Code restructuring (no functionality change) |
| docs     | Documentation updates                        |
| test     | Test-related changes                         |
| chore    | Build process or tooling updates             |
| perf     | Performance improvements                     |
| ci       | CI configuration changes                     |

**Example**:
```
feat(render): add Vulkan texture support

Implement VKTexture struct for basic texture mapping
Add texture unit test suite

Closes #123
```

## Pull Request Process

1. Create feature branch from `main` (`feat/xxx`, `fix/xxx`)
2. After development, run full test suite:
   ```bash
   make test-all  # Includes Rust unit tests and .NET integration tests
   ```
3. Ensure code passes static analysis:
   ```bash
   make lint
   ```
4. Push branch and create PR to `dev` branch
5. Complete PR template describing changes and impact
6. Wait for CI pipeline success
7. Request review from core maintainers
8. Address feedback until receiving two LGTM (Looks Good To Me)
9. Maintainer merges after approval

## Code of Conduct

We adhere to https://www.contributor-covenant.org/version/2/0/code_of_conduct/:
- Respect contributors of all backgrounds and experience levels
- Provide constructive feedback, avoid personal criticism
- Prohibit discrimination or harassment of any kind
- Resolve disputes through project steering committee

## Communication Channels

| Channel              | Purpose                                            |
| -------------------- | -------------------------------------------------- |
| [GitHub Issues]      | Bug reports and feature requests                   |
| [GitHub Discussions] | Design discussions and proposals                   |


## Contribution Areas

We particularly welcome contributions in:
- **Graphics Programming**: Vulkan/OpenGL renderer improvements
- **Network Engineering**: Multiplayer backend systems
- **Physics Simulation**: Collision detection and response
- **UI/UX Development**: Interface design and implementation
- **Documentation**: API references and tutorials

> Every line of code helps build a better virtual world!