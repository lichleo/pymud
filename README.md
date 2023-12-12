# PyMUD - Python原生MUD客户端
## 简介

### 帮助文件见北侠WIKI：  https://www.pkuxkx.net/wiki/tools/pymud
### 源代码地址: https://github.com/crapex/pymud
### 使用流QQ群：554672580


### 北大侠客行Mud (www.pkuxkx.net)，最好的中文Mud游戏！
### PyMUD是我为了更好的玩北大侠客行，特意自行开发的MUD客户端。PyMUD具有以下特点：
+ 原生Python开发，除prompt-toolkit及其依赖库（wcwidth, pygment, pyperclip)外，不需要其他第三方库支持
+ 基于控制台的全屏UI界面设计，支持鼠标操作（Android上支持触摸屏操作）
+ 支持分屏显示，在数据快速滚动的时候，上半屏保持不动，以确保不错过信息
+ 解决了99%情况下，北大侠客行中文对不齐，也就是看不清字符画的问题（因为我没有走遍所有地方，不敢保证100%）
+ 真正的支持多session会话，支持命令或鼠标切换会话
+ 原生支持多种服务器端编码方式，不论是GBK、BIG5、还是UTF-8
+ 支持NWAS、MTTS协商，支持GMCP、MSDP、MSSP协议
+ 一次脚本开发，多平台运行。只要能在该平台上运行python，就可以运行PyMUD客户端
+ 脚本所有语法均采用Python原生语法，因此你只要会用Python，就可以自己写脚本，免去了再去学习lua、熟悉各类APP的使用的难处
+ Python拥有极为强大的文字处理能力，用于处理文本的MUD最为合适
+ Python拥有极为丰富的第三方库，能支持的第三方库，就能在PyMud中支持
+ 我自己还在玩，所以本客户端会持续进行更新:)

## 版本更新信息
### 0.15.8 (2023-12-05)
发布到pip，增加模块使用

### 0.16.1 (2023-12-11)
+ 问题修复：修复__init__.py中的__all__变量为字符串
+ 功能增加：可以加载自定义Settings。在执行python -m pymud时，会自动从当前目录读取pymud.cfg文件。使用json格式将配置信息写在该文件中即可。支持模块中settings.py里的sessions, client, server, styles, text字段内容。
+ 功能增加：增加全局变量集，可以使用session.setGlobal和session.getGlobal进行访问，以便于跨session通信。也可以使用#global在命令行访问
+ 功能增加：增加变量的持久化，持久化文件保存于当前目录，文件名为session名称.mud，该文件在会话初始化时自动读取，会话断开时自动保存，其他时候使用#save保存。
+ 功能增加：在extras.py中增加DotDict，用于支持字典的.访问方式
+ 功能增加：使用DotDict增加了session有关对象的点访问方式（.）的快捷访问，包括变量vars，全局变量globals，触发器tris，别名alis，命令cmds，定时器timers，gmcp。例如：session.vars.charname，相当于session.getVariable('charname')
+ 功能增加：增加#all命令，可以向当前所有活动会话发送同一消息，例如#all xixi，可以使所有连接的会话都发送emote
+ 功能增加：增加%copy系统变量，当复制后，会将复制内容赋值给%copy变量
+ 功能增加：增加Trigger测试功能，使用#test {msg}在命令行输入后，会如同接收到服务端数据一样引发触发反应，并且会使用[PYMUD TRIGGER TEST]进行信息显示。
+ 功能增加：匹配#test命令和%copy变量使用如下：窗体中复制有关行，然后命令行中输入#test %copy可使用复制的行来测试触发器
+ 功能修改：将原CodeBlock修改为CodeBlock和CodeLine组成，以适应新的#test命令
+ 功能修改：session对命令的输入异步处理函数handle_input_async进行微小调整，以适应#test命令使用
+ 功能修改：退出时未断开session时的提示窗口文字改为红色（原黄色对比度问题，看不清楚）
+ 功能修改：恢复了#help功能，可以在任意会话中使用#help列出所有帮助主题，#help topic可以查看主题详情
+ 功能修改：在#reload重新加载脚本时，保留变量数据

### 0.16.1.post1 (2023-12-12)
+ 问题修复：修复版本显示，更正问为0.16.1（原0.16.0）
+ 问题修复：发布日期标志修改为当前时间
+ 功能修改：CodeLine的执行运行处理修改为不删除中间的多余空白

### 0.16.1.post2 (2023-12-12)
+ 问题修复：修改github项目地址为原pymud地址