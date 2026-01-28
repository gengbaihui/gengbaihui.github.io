# windows本地配置Github SSH 2017-01-10
配置 SSH 密钥是一个“一劳永逸”的操作。配置完成后，你与 GitHub 之间的通信将通过 22 端口建立加密隧道，不再需要输入账号密码或 Token。

以下是 Windows 环境下的标准配置流程：

第一步：检查现有的 SSH 密钥
在生成新密钥之前，先看看你电脑里是不是已经有了。

打开 PowerShell 或 CMD。

输入命令：ls ~/.ssh

结果分析：

如果你看到 id_rsa 和 id_rsa.pub（或者 id_ed25519），说明已经有密钥了，可以直接跳到第三步。

如果提示“文件夹不存在”或里面是空的，请继续第二步。

第二步：生成新的 SSH 密钥
我们将使用目前更安全、更高效的 Ed25519 算法。

在终端输入：

Bash
ssh-keygen -t ed25519 -C "你的邮箱@example.com"
(注：邮箱只是个标签，建议填你的 GitHub 注册邮箱)

连续按三次回车（不用输入密码，除非你希望每次克隆代码都要额外输一次密钥密码）。

第三步：将公钥添加到 GitHub
现在你需要把“锁”给 GitHub，自己留着“钥匙”。

获取公钥内容： 在终端输入以下命令查看并复制内容：

Bash
cat ~/.ssh/id_ed25519.pub
(内容通常以 ssh-ed25519 开头，以你的邮箱结尾)

在 GitHub 上配置：

登录 GitHub，点击右上角头像 -> Settings。

左侧菜单点击 SSH and GPG keys。

点击右上角的 New SSH key。

Title：随便起个名字（比如 "My Windows PC"）。

Key：粘贴你刚才复制的全部内容。

点击 Add SSH key。

第四步：测试连接
这是最重要的一步，验证 22 端口是否畅通。

在终端输入：

Bash
ssh -T git@github.com
你会看到一条警告，问你是否信任该主机，输入 yes 并回车。

成功标志： 如果看到 Hi [你的用户名]! You've successfully authenticated...，说明你已经打通了 SSH 之路！

第五步：以后如何使用？
现在你已经配好了 SSH，以后在 GitHub 找项目点击 Clone 按钮时，记得切换到 SSH 选项卡，复制那个以 git@github.com:... 开头的链接。

克隆示例：

Bash
git clone git@github.com:username/project.git