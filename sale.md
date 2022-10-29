User.Tax ： 您专注于核心业务 · 我们负责用户系统

每次写网站，都得开发一套用户系统。
邮件注册、短信发送、移动端适配、扫码登录、双重验证码 、异地登录的安全提示、头像剪裁、实名认证 ……
层出不穷的需求，不断追加的工时，而这些都统统与您的核心业务无关。
用户系统本质上就是『用户税』，不想支付但不得不去支付的研发成本。

当然，市面上也有一些现成的用户系统解决方案，比如 xx，比如 xx，但是 xx，xx

后端插件化是今天想到的点。
其实如果插件化体系能做好了，可以形成一个用户系统插件市场，类似 npm，那就不是现有的用户系统模块体系可以抗衡的。
比如，后续可以追加用户私信插件、用户工单插件、用户群聊插件、用户关注插件、留言插件、实名认证（KYC）插件、敏感头像审查插件、用户禁言插件、权限系统插件 等等。
这些功能可能是个网站都需要，靠单个公司写一定不能满足所有人需求，
如果有个方便二次开发、分发安装的后端、前端包管理插件系统，加上用户系统这个底座，那么未来写网站将和现在的流程完全不一样了。

## 痛点

注册、登录、重置密码、邮箱验证

开源，可私有化内网部署

体积小 web component 适用于任何框架，灵活可定制，组件可以随意组合

国际化 121 种语言支持

默认的用户协议模板 同样支持多国语言

浏览器推送 [建立 Service Worker Web Push Notification](https://t.cn/A6SJwV6C)

多用户切换

移动端适配

用户登录设备管理

团队组织、分权限享等

[异地登陆邮件报警](https://github.com/orgs/user-tax-dev/projects/1) 以及 输入邮件验证码登录 

otp 验证码

用户行为历史

用户的 api key 管理

用户召回邮件 (支持多语言)，类似

> Hi ,
>
> We noticed you created a Backblaze account, but haven’t started using it yet, and wanted to reach out to see if you needed any help onboarding or had questions the Support team could answer. Your account is free up to 10GB of data, so email b2contact@backblaze.com or contact Support and we’ll help you get set up so you get full advantage of it.
>
> Best,
>
> Backblaze Support Team

更新后的邮件推送

命令行工具登陆

现有的登录系统都有不容易定制化
包括前端样式难以修改（比如，希望优先展示二维码微信扫码登录）
包括后台数据难以修改（比如，希望每个用户可以可以设自己的地址、第二语言、辅助邮箱）
前端样式的定制化问题，user .tax 通过前端组件化来解决，每个模块都是一个小的前端控件，可以自由组合样式
后端的话，（接下来要代码改造），让每个后端模块插件话，可以安装、卸载、升级

## 二期

多点登录免注册（如果用户已经注册过任何 user.tax 的账户，无需注册可以直接登录）

用户实名认证

企业实名认证

头像审核

用户审核

反垃圾注册

## 未来

数字遗产继承权 https://github.com/settings/admin

通过单击下面的“添加继任者”，我承认我是 @usrtax 帐户的所有者，并授权 GitHub 在我死亡的情况下将该帐户中的内容转移到我的 GitHub 继任者（在下面指定）。我明白，对继任者的任命不会凌驾于任何相关司法管辖区的具有法律约束力的近亲规则或遗产法之上，也不会产生具有约束力的遗嘱。 了解有关帐户继任者的更多信息。

## 卖点

1. 给用户打标签、群发邮件、注册之后延时发邮件、定期发召回邮件
1. 支持按国家配置发送短信的渠道（中国大陆短信，国际短信 ...）
1. WebAuthn 实现浏览器无密码登录 : https://t.cn/A6SjcJuF

## 企业版

1. 权限管理
