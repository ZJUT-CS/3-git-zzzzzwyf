[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/qUf8f6Oh)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=22080409)
# 作业说明：GitHub Classroom + Git 入门 + Python 自动评分

> 本 README 是给同学看的 step-by-step 指南。  
> 你**不会 Git 也没关系**，跟着步骤一步一步来就行。你只需要会一点 Python。

---

## 0. 作业目标是什么？

通过本次作业，你要完成三件事：

1. 会用 **GitHub Classroom** 接收作业、获得自己的代码仓库；
2. 会用 **git** 把仓库克隆到本地，修改代码、提交并推送；
3. 修改一个简单的 Python 函数，让自动测试（pytest）全部通过，从而拿到自动评分。

---

## 1. 仓库里有什么？（文件结构）

当你通过 GitHub Classroom 接受作业后，会自动生成一个 **只属于你自己的** 仓库，主要包含：

- `hello.py`  
  Python 源代码文件，里面有一个函数 `hello_world()`，目前是**故意写错的**。

- `hello_test.py`  
  使用 `pytest` 写的测试文件，用来检查你的 `hello_world()` 是否返回了正确的字符串。

- `README.md`  
  就是你现在正在看的这份说明。

当前状态：  
`hello.py` 中的函数返回的字符串和测试期望的字符串不一样，所以 **测试会失败**。  
你的任务就是**改对这个函数**，让测试通过。

---

## 2. 你需要提前准备什么？

### 2.1 GitHub 账号

- 如果你还没有 GitHub 账号，请先注册一个：https://github.com

### 2.2 安装 Git

- Windows：推荐安装 **Git for Windows**（自带 Git Bash 终端）。
- macOS：可以在终端中尝试 `git --version`，如果没有，会提示安装 Xcode Command Line Tools。
- Linux：通常可以通过包管理器安装，比如 `sudo apt install git`。

安装完成后，在终端（或 Git Bash）中输入：

```bash
git --version
````

能看到版本号说明安装成功。

### 2.3 安装 Python（和可选的虚拟环境）

* 确保本地有 **Python 3.x**，在终端输入：

  ```bash
  python --version
  ```

  或

  ```bash
  python3 --version
  ```

* 推荐使用虚拟环境（可选但推荐）：

  ```bash
  # 1) 进入你准备放作业代码的目录
  cd /path/to/your/workspace

  # 2) 创建虚拟环境（名字叫 venv）
  python -m venv venv

  # 3) 激活虚拟环境
  # Windows（PowerShell）：
  .\venv\Scripts\activate
  # macOS / Linux：
  source venv/bin/activate
  ```

* 安装 pytest（后面跑测试会用到）：

  ```bash
  pip install pytest
  ```

---

## 3. 第一步：通过 GitHub Classroom 接受作业

1. 老师会发一个 GitHub Classroom 作业链接（https://classroom.github.com/a/qUf8f6Oh）。
2. 点击链接，用你的 GitHub 账号登录。
3. 点击 **Accept this assignment**（接受作业）。
4. 等几秒钟，页面会自动为你创建一个**专属仓库**（仓库名通常带有你的 GitHub 用户名）。
5. 在作业页面中找到 “Your repository” 或类似链接，点进去就能看到你的仓库地址（URL）。

**后面所有操作都只针对你这一份仓库。**

---

## 4. 第二步：把仓库克隆到本地

在终端中操作：

1. 进入你希望保存作业的目录，例如：

   ```bash
   cd /path/to/your/workspace
   ```

2. 克隆仓库（把 `<repo-url>` 替换成你仓库的地址）：

   ```bash
   git clone <repo-url>
   ```

   例如：

   ```bash
   git clone https://github.com/your-org/autograding-example-python-yourname.git
   ```

3. 进入克隆下来的目录：

   ```bash
   cd autograding-example-python-yourname
   ```

---

## 5. 第三步：本地跑一遍测试（第一次失败是正常的）

在仓库目录下运行：

```bash
pytest
```

* 如果你看到类似下面的输出：

  * 显示有 1 个测试（`test_hello`）；
  * 结果是 **failed**（失败）；

  这是**正常的**，说明：

  * 测试确实在运行；
  * 目前的代码没有满足测试要求（这是故意的）。

接下来你要做的，就是修改 `hello.py` 让测试通过。

---

## 6. 第四步：修改 `hello.py` 让测试通过

1. 用你喜欢的编辑器打开 `hello.py`，找到类似下面的代码：

   ```python
   def hello_world():
       return "Hello!"
   ```

2. 再打开 `hello_test.py` 看看测试期待的结果，大致形式是：

   ```python
   import hello

   def test_hello():
       assert hello.hello_world() == "Hello World!"
   ```

   可以看到，测试要求 `hello_world()` 返回的字符串是 `"Hello World!"`（注意大小写、空格、感叹号等都要完全一致）。

3. 按照测试的要求修改 `hello_world()`，例如：

   ```python
   def hello_world():
       return "Hello World!"
   ```

4. 保存文件。

5. 回到终端，再次运行：

   ```bash
   pytest
   ```

   * 如果看到 `1 passed`，说明测试已经全部通过 🎉
   * 如果还是失败，请仔细对比测试期望的字符串和你的返回值，检查是否有多余/少了空格、符号、大小写错误等。

---

## 7. 第五步：用 Git 提交你的修改

现在你已经在本地修好了代码，测试也通过了。接下来要用 Git 记录你的修改，并推送到 GitHub。

### 7.1 查看当前修改

```bash
git status
```

你应该能看到 `hello.py` 被标记为 “modified”。

### 7.2 把修改加入暂存区

```bash
git add hello.py
```

### 7.3 提交（commit）

```bash
git commit -m "Fix hello_world output"
```

* `-m` 后面的内容是本次提交的说明，可以用中文或英文；
* 建议写得有一点意义，比如 `"修改 hello_world 返回值"` 而不是 `"test"`。

---

## 8. 第六步：把提交推送到 GitHub

在终端中运行：

```bash
git push
```

* 第一次 push 时，可能会弹出登录或 token 相关提示，按提示操作即可；
* 推送成功后，你在 GitHub 网站上就能看到最新的代码修改。

---

## 9. 第七步：查看自动评分结果（Autograding）

1. 打开你的 GitHub 仓库网页；

2. 或者回到 GitHub Classroom 的作业页面；

3. 每次你 `git push` 后，GitHub Classroom 会自动触发一次评分流程：

   * 它会在云端执行类似的命令：

     ```bash
     pip install pytest
     pytest
     ```

4. 等一会儿（几十秒到几分钟不等），你会看到评分结果：

   * ✅ 绿色对勾：测试全部通过，你的自动评分就是满分（或设定的最高分）；
   * ❌ 红色叉号：说明仍有测试失败，可以点进去看失败信息，根据提示继续修改代码，再次 `git add` → `git commit` → `git push`。

> **注意：**
> 你可以多次提交、多次 push，系统会自动重新评分。老师一般会以截止时间前最后一次的成绩为准（具体以老师说明为准）。

---

## 10. 作业完成标准（总结）

请检查以下事项是否全部完成：

* [ ] 已通过 GitHub Classroom 接受作业，拥有自己的仓库；
* [ ] 能在本地用 `git clone` 克隆仓库并进入目录；
* [ ] 能在本地运行 `pytest`，并最终让测试显示 `1 passed`；
* [ ] 已使用 `git add` / `git commit` 提交本次修改；
* [ ] 已使用 `git push` 推送到远程仓库；
* [ ] 在 GitHub Classroom 中看到自动评分正常运行，且为通过状态（绿勾）。

如果以上都完成，就说明你已经完成了本次 “Git + GitHub Classroom + Python 自动评分” 的入门作业 🎉

---

## 11. 常见问题（FAQ）

**Q1：`pytest` 命令找不到怎么办？**
A：说明 Python 环境里没有安装 pytest。请在虚拟环境或系统环境中执行：

```bash
pip install pytest
```

再次运行 `pytest` 即可。

---

**Q2：运行 `pytest` 时，提示找不到 `hello` 模块？**
A：请确认你在仓库所在目录下运行 `pytest`，例如：

```bash
cd autograding-example-python-yourname
pytest
```

---

**Q3：本地测试通过了，但 Classroom 上还是失败？**
A：

1. 确认你已经 `git push`（本地 commit 不会自动上传）；
2. 等几十秒后再刷新 Classroom 页面；
3. 如果还是失败，点击详情，查看自动运行时的报错信息，和你本地环境可能有差异（例如 Python 版本、依赖问题等）。

---

**Q4：我完全不会 git，怕搞乱怎么办？**
A：这是一次练习作业，你可以放心尝试。
实在搞乱了，你可以：

1. 把当前目录删掉；
2. 重新 `git clone <repo-url>`；
3. 按步骤一步步来，多练习几次就熟悉了。

---

祝你玩的开心，也希望通过这次作业，你对 **Git + GitHub + 自动评分** 有一个直观的初体验 😊

