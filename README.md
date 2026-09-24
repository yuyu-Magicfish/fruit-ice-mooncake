# Fruit Ice Mooncake Skill

生成「水果冰皮月饼」系列生图提示词的 Agent Skill —— 水晶通透质感、低角度平视、两块叠放构图，并在用户确认后调用生图模型出图。

## 能做什么

你只需说出水果名（蓝莓、草莓、芒果、牛油果……），Skill 会：

1. 从已验证的槽位表取出该水果的 **冰皮色渐变 / 内馅 / 果粒 / 点缀形态**；
2. 套进通用模板，拼出一条高稳定度的生图提示词 + 固定负向提示词；
3. 询问你是否出图，确认后调用生图模型（`seedream_5.0_pro`，3:4，1536×2048）出图。

表内已内置 **15 款水果** 槽位和 **5 种背景风格**（秋日清新、深蓝夜空、宫廷暖调家宴、宋画淡墨风、园林漏窗）。表里没有的水果，按真实果肉特征自行填槽。

## 目录结构

```
fruit-ice-mooncake/
├── SKILL.md                    # 主文件：工作流 + 通用提示词模板 + 稳定关键点
└── references/
    ├── fruits.md               # 15 款水果槽位速查表 + 新水果填槽规则
    └── backgrounds.md          # 5 种背景风格及配套描述
```

## 安装

把 Skill 放进 Agent 的技能目录即可。**默认技能目录**：

| 系统 | 路径 |
|---|---|
| Windows | `C:\Users\<你的用户名>\.workbuddy\skills\` |
| macOS / Linux | `~/.workbuddy/skills/` |

### 方式 A：一条命令（推荐）

```bash
git clone https://github.com/yuyu-Magicfish/fruit-ice-mooncake.git ~/.workbuddy/skills/fruit-ice-mooncake
```

Windows 的 PowerShell 里同样可用（`~` 就是 `$HOME`）。

### 方式 B：下载 zip

1. 仓库页 → `<> Code` → **Download ZIP**
2. 解压，把里面的 `fruit-ice-mooncake` 文件夹**整个**拖进技能目录

### 方式 C：让 Agent 帮你装

在 WorkBuddy 对话里直接发：

> 帮我安装这个 skill：https://github.com/yuyu-Magicfish/fruit-ice-mooncake

### ⚠️ 目录层级别搞错

```
✅ ~/.workbuddy/skills/fruit-ice-mooncake/SKILL.md            # SKILL.md 直接在第二层
❌ ~/.workbuddy/skills/fruit-ice-mooncake/fruit-ice-mooncake/SKILL.md   # zip 解压常多套一层，识别不到
```

放好后重启客户端或开一个新会话即可生效。

### 前置依赖

- 只想生成**提示词文本**：无依赖，任何支持 Agent Skills 的客户端都能跑
- 要**直接出图**：需要客户端支持 `image_gen` 生图工具（本 Skill 默认用 `seedream_5.0_pro`，3:4，1536×2048）

## 用法示例

- 「生成蓝莓冰皮月饼的提示词」
- 「草莓月饼，背景换深蓝夜空」
- 「牛油果冰皮月饼，要更通透、加水珠」

只给水果名时按默认「秋日清新」背景推进，不会反复追问。

## 稳定关键点

提示词里这几句不可省略，否则出图容易歪：

- 上方月饼稳稳直立、底部完全贴合不倾斜 —— 保证立得住
- 冰皮晶莹剔透像水晶玻璃、光线穿透冰皮 —— 保证通透感
- 盘边水果只在画面边角露出 —— 保证主体占比

## License

MIT
