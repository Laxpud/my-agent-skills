# Vibekits Claude Code 插件

这是 my-awesome-vibekits 项目的 Claude Code 插件，提供标准化的代码生成和项目配置能力。

## 功能特性
- 📝 **代码注释标准化**：统一团队代码注释风格，自动遵循注释规范
- 🐍 **PyProject配置标准化**：快速生成符合最佳实践的Python项目配置

## 安装方式

### 1. 项目内使用（推荐）
直接克隆本仓库到你的项目中，Claude Code 会自动识别 `.claude-plugin` 目录：
```bash
git clone https://github.com/MishoreYF/my-awesome-vibekits.git
```

### 2. 全局安装
将 `.claude-plugin` 目录复制到 Claude Code 全局插件目录：
```bash
# Windows
cp -r .claude-plugin ~/.claude/plugins/my-awesome-vibekits

# macOS/Linux
cp -r .claude-plugin $HOME/.claude/plugins/my-awesome-vibekits
```

### 3. 子模块引入
在现有项目中作为子模块引入：
```bash
git submodule add https://github.com/MishoreYF/my-awesome-vibekits.git .vibekits
ln -s .vibekits/.claude-plugin .claude-plugin
```

## 使用方法

### 技能调用
1. **代码注释标准化**：
   ```
   /skill code-comment-standard
   ```
   或在对话中提到"添加注释"、"注释规范"等关键词自动触发。

2. **PyProject配置标准化**：
   ```
   /skill pyproject-standard
   ```
   或在对话中提到"创建pyproject.toml"、"Python项目配置"等关键词自动触发。

### 规则应用
- **代码注释标准规则**：默认自动应用到所有文件，生成注释时会自动遵循规范。

## 目录结构
```
my-awesome-vibekits/
├── .claude-plugin/
│   ├── manifest.json    # 插件配置清单
│   └── README.md        # 本说明文件
├── skills/              # 技能集合目录
│   ├── code-comment-standard/
│   └── pyproject-standard/
└── rules/               # 规则集合目录
    └── code-comment-standard.md
```

## 许可证
MIT License