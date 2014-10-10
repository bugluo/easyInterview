#web安全是web最重要的环节，最重要的还是码农的代码通不过安全测试就发不出去。。。

##XSS
###攻击
XSS的核心是在攻击者提交数据，使其它用户访问页面，页面渲染时执行本不该执行的代码，获得本不应该有的执行权限
XSS分类
1 反射型
通过URL访问执行的脚本
	访问
	http://fovweb.com/xss/message.php?send=<script>alert(‘xss’)</script>
	页面输出
	<script>alert('xss')</script>
2 存储型
通过存储数据到后端，再由前端展示到前端
	例如百度百科，提交XSS到页面
	<span><script>alert('xss')</script></span>
	页面也同样输出存储在后端的同样代码，此时就会执行存储的内容
3 DOM型
	通过innerHTML替换文本内容，如果让用户自己贴图
	<img src="" onerror="alert('xss')"></img>
	此时给img一个错误的src，就会触发xss
###防护
原则：不相信客户输入的任何数据
将重要的cookie标记为http only, 这样的话Javascript 中的document.cookie语句就不能获取到cookie。

##CSRF

##SQL注入

##URL跳转

##权限绕过

##逻辑漏洞

##任意文件读取

##敏感信息泄露

##安全配置错误

