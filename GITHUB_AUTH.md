# GitHub 授权指南

## 方案 1: 生成 Personal Access Token（推荐）

这是让我能直接推送代码到你的仓库的最简单方式。

### 步骤：

1. **登录 GitHub**，点击右上角头像 → Settings
2. 左侧菜单最底部 → **Developer settings**
3. 左侧 → **Personal access tokens** → **Tokens (classic)**
4. 点击 **Generate new token (classic)**
5. 配置：
   - **Note**: `Design Studio Deploy`
   - **Expiration**: 7 days（或你选择的时间）
   - **Scopes**: 勾选以下权限：
     - ✅ `repo`（完整仓库访问）

6. 点击 **Generate token**
7. **复制生成的 token**（重要：只显示一次！）

### 给我权限：

把 token 发给我，格式如下：
```
Token: ghp_xxxxxxxxxxxxxxxxxxxx
仓库: https://github.com/raymondxu1883-gif/Design-Studio
```

⚠️ **安全提示**：
- Token 只在对话中传递
- 建议设置 7 天有效期
- 部署完成后可以在 GitHub 删除 token

---

## 方案 2: 你自己推送（更安全）

如果你不想分享 token，可以复制以下命令在本地执行：

```bash
# 1. 进入项目目录
cd studio-website

# 2. 初始化 git
git init

# 3. 添加所有文件
git add .

# 4. 提交
git commit -m "Initial commit: Design Studio website"

# 5. 添加远程仓库
git remote add origin https://github.com/raymondxu1883-gif/Design-Studio.git

# 6. 推送代码
git push -u origin main
```

如果提示输入用户名密码，输入：
- 用户名：你的 GitHub 用户名
- 密码：你的 Personal Access Token（不是 GitHub 密码）

---

## 方案 3: 我生成代码压缩包

我可以把代码打包成 zip，你下载后解压并手动上传到 GitHub。

---

选择哪种方案？推荐 **方案 1**，最快最方便！
