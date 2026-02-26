---
name: "pyproject-standard"
description: "Enforces standard configuration for pyproject.toml. Invoke when creating or modifying pyproject.toml to ensure compliance with project standards."
---

# Pyproject Standard

This skill defines the standard structure and required fields for `pyproject.toml` files in this workspace.

## Core Rules

1.  **Build System**: MUST use `hatchling` as the build backend.
2.  **Package Management**: MUST be compatible with `uv`.
3.  **Mirror Configuration**: MUST include the Tsinghua mirror for `uv` acceleration.
4.  **Versioning**: MUST use dynamic versioning sourced from `src/__init__.py`.
5.  **License**: MUST reference an external `LICENSE` file.
6.  **Dynamic Content**:
    *   **Classifiers**: Include basic classifiers (OS, Python version). Add specific Topic/Audience classifiers ONLY if relevant to the project domain.
    *   **Scripts (CLI)**: Define `[project.scripts]` ONLY if the project has executable CLI tools.
    *   **Plugin Entry Points**: Define `[project.entry-points]` ONLY if the project exposes plugins for other applications.
    *   **Optional Dependencies**: Define `[project.optional-dependencies]` ONLY if there are distinct feature sets (e.g., `plot`, `test`, `dev`) that require extra packages.

## Template

Use the following template as the baseline. **Review and Uncomment/Remove optional sections based on project needs.**

```toml
[project]
name = "<project-name>"
dynamic = ["version"]
description = "<description>"
readme = "README.md"
requires-python = ">=3.10"
license = { file = "LICENSE" }
authors = [
    { name = "MiShore", email = "mishoreyf@nuaa.edu.cn" }
]
keywords = ["<keyword1>", "<keyword2>"]

# [Mandatory Classifiers]
classifiers = [
    "Programming Language :: Python :: 3",
    "Programming Language :: Python :: 3.10",
    "Programming Language :: Python :: 3.11",
    "Programming Language :: Python :: 3.12",
    "Operating System :: OS Independent",
    # Add domain-specific classifiers here if applicable (e.g., "Topic :: Scientific/Engineering")
]

dependencies = [
    # Add core dependencies here (e.g., "numpy>=1.26.0")
]

# [Optional] Define optional dependencies if needed
# [project.optional-dependencies]
# plot = ["matplotlib>=3.8.0"]
# dev = ["pytest>=8.0.0", "black>=24.0.0"]

# [Optional] Define CLI entry points if needed
# [project.scripts]
# my-tool = "package.module:function"

# [Optional] Define Plugin entry points if needed
# [project.entry-points."plugin_namespace"]
# plugin_name = "package.module:object"

[project.urls]
Repository = "<repository-url>"

[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[tool.hatch.version]
path = "src/__init__.py"

[tool.hatch.build.targets.wheel]
packages = ["src"]

# 配置 uv 使用清华镜像源加速下载
[[tool.uv.index]]
name = "tsinghua"
url = "https://pypi.tuna.tsinghua.edu.cn/simple"
default = true
```

## Checklist Before Completion

- [ ] `[build-system]` is set to `hatchling`.
- [ ] `dynamic = ["version"]` is present and linked to `src/__init__.py`.
- [ ] `license = { file = "LICENSE" }` is set.
- [ ] Tsinghua mirror configuration is present under `[[tool.uv.index]]`.
- [ ] **Optional sections (`scripts`, `entry-points`, `optional-dependencies`, specific `classifiers`) are reviewed and included only if necessary.**
