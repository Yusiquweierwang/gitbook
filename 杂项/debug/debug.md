# UE5

### 使用 vs 生成 cmake 编译好的工程时报错：无法启动程序......拒绝访问。

https://blog.csdn.net/weixin_44120025/article/details/115270215?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-115270215-blog-78053055.235%5Ev43%5Epc_blog_bottom_relevance_base8&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-115270215-blog-78053055.235%5Ev43%5Epc_blog_bottom_relevance_base8&utm_relevant_index=5

### 项目启动时报错-`UnrealBuildTool failed with exit code 0xe0434352`

- 先把 Binaries / intermediate / saved 文件夹删除，右键 Uproject ： generate vs project files。
- 打开.sln，解决方案配置设置为 developer editor，调试。
- 失败，则右键 games /
- 有可能是中文原因，再重新生成调试，查看错误报告
- 用 tortoiseGit
- 在项目“testE/AgentSim/AgentSim”下面右键 git commit > 'main'
- 重新调试

### 另一个 MSB307 问题

![1721097987730](image/debug/1721097987730.png)

![1721098026521](image/debug/1721098026521.png)

![1721098061617](image/debug/1721098061617.png)
提交 git

### 材质问题

- 找到材质文件 - 父项 - c4dreference
- datasmith 文件夹的问题 ，拷贝好的替换文件夹。

## git 问题

### 令牌问题 access denied

设置 - 版本控制 - gitlab - 登录 - 登录失败时获取令牌 - selected scopes 全选 -create - 上面即 your new personal access token
![1720513255437](image/debug/1720513255437.png)

## UE5

### 运行时有的物体在完成时消失了

在大纲搜该物体
在细节中找到已空间加载，打勾再关闭

![1721808647970](image/debug/1721808647970.png)
把这个叉掉

2.如果有重复命名，需要更改名称。

### 在全局中寻找某变量

![1722413336088](image/debug/1722413336088.png)

### 批量修改资产

在大纲中找到该资产，浏览至资产。
批量选择所有资产 ctrl + A
右键->
资产操作->
通过属性矩阵编辑->
在右框中搜索要编辑的属性，如碰撞
修改后 ctrl + s 保存所有对资产的操作

### 解决子弹穿墙问题

![1723515096943](image/debug/1723515096943.png)

### hint

### 查看蓝图更改历史

### git 解决方案冲突

一个个勾选接受您的，接受他们的

### error C2511 没有找到重载的成员函数

![1725428847034](image/debug/1725428847034.png)
使参数名，参数数量，参数顺序保持一致。

### 上传代码之前先 package 一下

### crash 之后的解决

**搜 log 日志，在 saved/log**

### 行人具有初始身高 196

在 BP_citizen 中 childcharacter ， 右侧细节面板 子 actor template 中 设置 default param。

### 在 不同关卡出现问题

1.考虑是否没有把 BP 拖入场景；

### 蓝图冲突合并

- 将本地资产更改与当前版本控制修订版进行对比
  diff against depot.
- 将本地资产更改与特定版本控制修订版本进行对比
  diff against workspace file.
- 将资产的早期修订版本与其上一修订版进行对比
  diff against previous revision.

| 颜色  | 说明                           |
| ----- | ------------------------------ |
| red   | 左侧内容在右侧缺失（内容减少） |
| green | 内容增加                       |
| blue  | 内容变化                       |
| gray  | 移动了节点 / 注释              |

**参考文档**：[虚幻引擎中的 UE 对比工具 | 虚幻引擎 5.5 文档 | Epic Developer Community | Epic Developer Community](https://dev.epicgames.com/documentation/zh-cn/unreal-engine/ue-diff-tool-in-unreal-engine)

### 蓝图 ： 设置输入模式游戏和 UI

### 编译报错流程

重新 generate

打开.sln

右键 Games/AgentSim，设为启动项目，选 developer editor ， win64, 启动，

如果还不行，删掉临时文件 saved / intermediate /
