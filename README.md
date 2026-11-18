# PR 实操练习仓库 🎓

这是一个专门用来练习 **GitHub Pull Request（PR）完整流程** 的教学仓库。

在这里你会亲手走一遍真实团队开发的标准流程: fork → 建分支 → 改代码 → 提 PR → Code Review → 合并。

---

> 🎓 **第一次做 PR？先看这份 [PR 实操示范文档](PR-DEMO.md)** —— 基于一条真实 PR 的完整演示，从 fork 到合并讲得明明白白。

## 📚 你将学到什么

- Fork 别人仓库到自己账号
- 用分支隔离改动,不污染主干
- 写一个清晰、可被 review 的 PR
- 处理 Reviewer 的修改意见
- 理解 `base` / `compare` 分支的区别

---

## 🚀 开始练习（按顺序做）

### 第 0 步:准备工作

1. 点击右上角 **Fork**,把这个仓库 fork 到你自己的 GitHub 账号下
2. 把你 fork 出来的仓库 clone 到本地:

```bash
git clone https://github.com/你的用户名/pr-workshop.git
cd pr-workshop
```

3. 添加原仓库为 `upstream`（方便同步最新内容）:

```bash
git remote add upstream https://github.com/jiangwang-coding/pr-workshop.git
```

### 第 1 步:选一个任务

打开 [Issues](https://github.com/jiangwang-coding/pr-workshop/issues) 标签页,找一个带 `good first issue` 标签的任务,在评论里回复"我来做",避免和别人撞车。

### 第 2 步:建分支

**永远不要直接在 main 分支上改代码。**

```bash
git checkout main
git pull upstream main
git checkout -b feat/你的名字-任务编号
# 例如: git checkout -b feat/zhangsan-issue1
```

### 第 3 步:改代码并提交

按 issue 里的要求修改文件,然后:

```bash
git add .
git commit -m "feat: 完成 xxx 任务"
git push -u origin feat/你的名字-任务编号
```

### 第 4 步:发起 Pull Request

1. 打开你 fork 的仓库页面,点击 **Pull requests** → **New pull request**
2. 关键:确认分支方向
   - **base repository**: `jiangwang-coding/pr-workshop`（原仓库）
   - **base branch**: `main`
   - **head repository**: `你的用户名/pr-workshop`
   - **compare branch**: `feat/你的名字-任务编号`
3. 按 PR 模板填写标题和说明
4. 点击 **Create pull request**

### 第 5 步:等待 Review 并修改

- 老师会在 PR 里留言,收到意见后**在同一个分支继续改**:

```bash
# 改完代码后
git add .
git commit -m "fix: 根据 review 意见修改 xxx"
git push
```

- 只要还是同一个分支,push 后 PR 会**自动更新**,不用重新提

### 第 6 步:合并成功 ✅

Review 通过后,老师会合并你的 PR。合并后记得同步你的 fork:

```bash
git checkout main
git pull upstream main
git push origin main
```

---

## ⚠️ 常见错误

| 错误 | 后果 | 正确做法 |
|------|------|----------|
| 直接改 main 分支 | PR 里混入无关提交 | 先建 feature 分支 |
| base 分支选错 | PR 内容错乱、难以合并 | 认准 base 是原仓库 main |
| 一个 PR 塞多个任务 | review 困难,容易被打回 | 一个 PR 只做一件事 |
| 收到意见后新建分支 | PR 不更新,老师看不到修改 | 在原分支继续 commit + push |

---

## 📁 仓库结构

```
pr-workshop/
├── README.md                       # 本文件:完整操作指南
├── .github/
│   ├── PULL_REQUEST_TEMPLATE.md    # PR 模板
│   └── ISSUE_TEMPLATE/
│       └── practice-task.md        # 任务 issue 模板
├── tasks/
│   └── MEMBERS.md                  # 练习用:成员名单(任务1要改它)
└── src/
    └── profile.html                # 练习用:个人主页(任务2要改它)
```

祝练习顺利!有问题在 Issue 里提问 🙋