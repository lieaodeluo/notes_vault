# Git 使用方法

## 基本配置

### 设置用户名和邮箱
```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
```

### 查看配置
```bash
git config --list
git config user.name
git config user.email
```

## 基础操作

### 初始化仓库
```bash
git init
```

### 克隆远程仓库
```bash
git clone 仓库地址
git clone 仓库地址 本地文件夹名
```

### 添加文件到暂存区
```bash
git add 文件名
git add .          # 添加所有文件
git add -A         # 添加所有文件（包括删除的）
```

### 提交更改
```bash
git commit -m "提交信息"
git commit -am "提交信息"  # 自动暂存已跟踪的文件并提交
```

### 查看状态
```bash
git status
git status -s       # 简洁模式
```

### 查看提交历史
```bash
git log
git log --oneline   # 简洁模式
git log -n 数量     # 查看最近n条
git log --graph     # 图形化显示分支
```

## 分支管理

### 查看分支
```bash
git branch          # 列出本地分支
git branch -a       # 列出所有分支（包括远程）
git branch -r       # 列出远程分支
```

### 创建分支
```bash
git branch 分支名
git checkout -b 分支名    # 创建并切换
git switch -c 分支名      # 创建并切换（现代命令）
```

### 切换分支
```bash
git checkout 分支名
git switch 分支名        # 现代命令
```

### 合并分支
```bash
git merge 分支名
```

### 删除分支
```bash
git branch -d 分支名      # 安全删除
git branch -D 分支名      # 强制删除
```

## 远程操作

### 添加远程仓库
```bash
git remote add origin 仓库地址
```

### 查看远程仓库
```bash
git remote -v
```

### 推送代码
```bash
git push origin 分支名
git push -u origin 分支名  # 关联并推送
git push --force          # 强制推送（慎用）
```

### 拉取代码
```bash
git pull origin 分支名
git pull                  # 拉取当前分支
```

### 拉取远程分支到本地
```bash
git checkout -b 本地分支名 origin/远程分支名
```

### 删除远程分支
```bash
git push origin --delete 远程分支名
```

## 撤销与回退

### 撤销工作区的修改
```bash
git checkout -- 文件名
git restore 文件名        # 现代命令
```

### 取消暂存
```bash
git reset HEAD 文件名
git restore --staged 文件名
```

### 回退提交
```bash
git reset --soft HEAD~1   # 保留修改在暂存区
git reset --mixed HEAD~1  # 保留修改在工作区（默认）
git reset --hard HEAD~1   # 丢弃所有修改
```

### 创建反向提交
```bash
git revert 提交ID
```

## 储藏工作

### 储藏更改
```bash
git stash
git stash save "备注信息"
```

### 查看储藏列表
```bash
git stash list
```

### 应用储藏
```bash
git stash apply           # 应用最新储藏
git stash apply stash@{0}  # 应用指定储藏
git stash pop             # 应用并删除最新储藏
```

### 删除储藏
```bash
git stash drop stash@{0}
git stash clear           # 清空所有储藏
```

## 标签管理

### 创建标签
```bash
git tag 标签名
git tag -a 标签名 -m "标签说明"
```

### 查看标签
```bash
git tag
git show 标签名
```

### 推送标签
```bash
git push origin 标签名
git push origin --tags    # 推送所有标签
```

### 删除标签
```bash
git tag -d 标签名
git push origin --delete 标签名
```

## 常用技巧

### 查看差异
```bash
git diff                  # 工作区 vs 暂存区
git diff --staged         # 暂存区 vs 最新提交
git diff 分支1 分支2      # 分支间差异
```

### 查看文件在某个提交中的内容
```bash
git show 提交ID:文件名
```

### 查找提交
```bash
git log --author="作者"
git log --grep="关键字"
git log -S "代码内容"      # 搜索包含特定代码的提交
```

### 清理未跟踪文件
```bash
git clean -n              # 预览将要删除的文件
git clean -f              # 删除未跟踪文件
git clean -fd             # 删除未跟踪文件和目录
```

### 设置别名
```bash
git config --global alias.别名 命令
# 示例
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```
