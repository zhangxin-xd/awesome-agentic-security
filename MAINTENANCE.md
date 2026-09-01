# 维护手册：Awesome Agentic Security

适用仓库：[awesome-agentic-security](https://github.com/zhangxin-xd/awesome-agentic-security)

---

## 一、论文来源：从哪里发现新论文

| 渠道 | 链接 | 频率 |
|------|------|------|
| arXiv cs.CR daily | https://arxiv.org/list/cs.CR/recent | 每天 |
| arXiv cs.AI daily | https://arxiv.org/list/cs.AI/recent | 每天 |
| Hugging Face Papers | https://huggingface.co/papers | 每天 |
| Twitter/X 关键词 | 见下 | 每天 |
| Semantic Scholar Alerts | 设置关键词订阅邮件 | 自动 |
| 顶会 proceedings | CCS / IEEE S&P / USENIX Security / ICLR / NeurIPS / ACL | 每次开会 |

**推荐搜索关键词**：
`prompt injection agent`、`LLM agent attack`、`agentic security`、`MCP poisoning`、`indirect prompt injection`、`multi-agent safety`、`RAG poisoning`、`tool poisoning`、`backdoor agent`

---

## 二、收录标准

### 必须满足

- [ ] 研究对象是 **agentic 系统**（单 agent 或多 agent），不是孤立的 LLM
- [ ] 有实质贡献：新攻击方法、新防御、新基准、或重要的实证发现
- [ ] 有实验/数据支撑，不是纯观点文章

### 加分项

- 发表在顶会：CCS / IEEE S&P / USENIX Security / NDSS / ICLR / NeurIPS / ACL
- arXiv 引用数 > 50（发布超过 3 个月）
- 填补现有分类中的空白
- 有开源代码或可复现的攻击/防御实现

### 直接排除

- ❌ 纯 LLM 安全，无 agentic 场景（如单次对话的 jailbreak，无工具/记忆/多轮）
- ❌ 没有实验的立场文章
- ❌ 与已有条目高度重复（核心思路相同，只换了场景）
- ❌ 发布不足 2 周、引用为 0、且无明显社区关注

### 早期论文的社区关注信号

预印本不足 2 周且引用为 0 时，满足以下任意一条可提前收录：

| 信号 | 参考阈值 | 查看方式 |
|------|---------|---------|
| GitHub 代码仓库 stars | > 200 | 论文页找代码链接 |
| HuggingFace Papers 点赞 | > 50 | huggingface.co/papers |
| Twitter/X 转发+点赞 | > 500（原作者推文）| 搜 arXiv 号 |
| 知名安全研究者公开推荐 | 任意 | Twitter、博客 |
| 被安全公司/团队博客引用 | 任意 | 如 Invariant Labs、Pillar Security |

提前收录时在 CHANGELOG 中标注 `[early, high-attention]`，一个月后复查引用数。

### 快速判断流程

```
读摘要 (30秒)
    │
    ├── 研究对象是 agent？ → No → 排除
    │
    ├── 有新攻击/防御/基准？ → No → 排除
    │
    ├── 顶会 OR 引用 > 50？
    │       ├── Yes → 直接收录
    │       └── No  → 发布不足 2 周？
    │                   ├── No → 填补空白？
    │                   │         ├── Yes → 收录，备注 "fills gap"
    │                   │         └── No  → 暂缓
    │                   └── Yes → 社区关注信号？
    │                               ├── Yes → 收录，备注 "[early, high-attention]"
    │                               └── No  → 暂缓 2 周后复查
    │
    └── 放入正确的攻击/防御分类
```

---

## 三、收录格式

```markdown
| [论文标题](arxiv或论文链接) | 会议/期刊 年份 | 贡献一句话；局限一句话 |
```

**评注写法规范**：
- 前半句：贡献（这篇做了什么，结果如何）
- 后半句：局限（假设、场景限制、或缺少什么）
- 用分号隔开，控制在 20 词以内
- 不写"this paper"，直接陈述结论

**示例**：
```
First paper to formalize cross-agent prompt injection propagation; shows exponential spread in large MAS
```

**放入哪个分类**：

| 内容 | 对应分类 |
|------|---------|
| 攻击者直接控制用户输入 | §1.1 Direct Prompt Injection |
| 攻击内容藏在环境中（网页、文档、API 返回）| §1.2 Indirect Prompt Injection |
| 污染 RAG 知识库或外部记忆 | §1.3 Memory & RAG Poisoning |
| 污染工具描述或 MCP 服务器 | §1.4 Tool & MCP Poisoning |
| 训练数据/few-shot 投毒 | §1.5 Backdoor Attacks |
| 攻击在多个 agent 间传播 | §1.6 Multi-Agent Propagation |
| 输入过滤、分类器、护栏 | §2.1 Input Filtering & Guardrails |
| 指令优先级机制 | §2.2 Instruction Hierarchy |
| 沙箱、权限控制 | §2.3 Sandboxing & Permission Control |
| 多 agent 信任协议 | §2.4 Multi-Agent Trust Protocols |

---

## 四、每日 Log

在仓库根目录维护 `CHANGELOG.md`，每次更新追加：

```markdown
## 2026-05-14

### Added
- [CacheTTL](https://arxiv.org/abs/2511.02230) → §1.6 | agentic KV cache TTL scheduling; 8× throughput gain for multi-turn agents
  - 来源：arXiv daily
  - 收录理由：agent-specific serving，高关注度 [early, high-attention]

### Considered but Rejected
- [论文标题](链接) | 排除原因：无 agentic 场景，属于纯 LLM jailbreak

---
```

**拒绝的论文也要记录**，防止重复评估。

---

## 五、定期维护

### 每周
- [ ] 检查各渠道新论文，按流程筛选
- [ ] 更新 CHANGELOG.md
- [ ] 更新 README 顶部 `updated` badge 日期
- [ ] Push 到 GitHub

### 每月
- [ ] 复查上月标注 `[early, high-attention]` 的条目，补充引用数和量化数据
- [ ] 检查已有条目是否有论文发布新版本修正了结论
- [ ] 检查 Open Problems（如有）：是否有新论文填补了已列出的 gap

### 每次顶会放榜后
- [ ] 下载 proceedings，搜索关键词批量筛选
- [ ] 重点关注安全四大顶会：CCS / IEEE S&P / USENIX Security / NDSS

---

## 六、Git 提交规范

```bash
# 新增论文
git commit -m "add: [PaperName] → §1.2 indirect injection"

# 修正评注
git commit -m "fix: update commentary for AgentDojo based on v2"

# 结构调整
git commit -m "refactor: split §2.1 into filtering and detection"
```

---

## 七、快速参考卡

```
新论文 → 30秒读摘要 → 三问：
  1. Agent 场景（有工具/记忆/多轮）？
  2. 新攻击 / 新防御 / 新基准？
  3. 顶会 / 高引 / 社区高关注 / 填空白？

全Yes → 写一行加进去 → 记 CHANGELOG → push

格式：
  | [标题](链接) | 会议 年份 | 贡献; 局限 |
```
