# OpenManusUnnatural
深度赋智的OpenManus hackathon比赛提交项目

# 队伍
不自然委员会：小熊，乘鳞真人
# 联系方式
微信xuyuhang243269  （小熊）
# 项目描述
本项目基于[OpenManus项目](https://github.com/mannaandpoem/OpenManus) 的first_hackathon分支进行测试，没有增加任何新功能，无需修改任何代码。
## 功能
本项目是用提示词实现<一个适用于主题热门视频的分析工作流>。

需要指定主题，指定网站搜索页面，关键指标。并且要明确中间信息的存储文件名。

# LLM配置
```
# Global LLM configuration
[llm]
model = "deepseek-chat"        # 必须用官方DeepSeek v3
base_url = "https://api.deepseek.com/v1/"  # 必须用DeepSeek v3
api_key = "sk-xxx"                    # 省略api key ， 可以在官网进行申请
max_tokens = 8192                           # Maximum number of tokens in the response
temperature = 0.0                           # Controls randomness
```
# 提示词和运行方式
直接启动项目下的main.py即可,输入如下提示词，会生成0403intro.txt,各个视频的json文件和最后的html网页文件
```
请完成以下任务，完成一个任务要在分析的时候重复一下当前任务编号。：1、打开https://www.aigc.cn/manus总结manus的介绍用中文记录，并存到0403intro.txt , 2、去到https://search.bilibili.com/all?keyword=Manus，这个网址是b站搜索页，会 搜索b站上面Manus相关的爆款视频，要对应好每个视频和对应url网址，先把各个视频标题和网址存为list0403.txt，每一行是视频标题 和对应网址，用逗号隔开， 视频网址是http://www.bilibili.com/video开头，其他开头的网址不是视频；3、然后再从list0403.txt依次不重复的读取每一个标题和对应网址（至少读取6个网址），每次打开一个网址 ，记录当前视频播放 收藏数，点赞数，投币数，转发数，标签列表，和评论情况,记录视频下面的前十个评论，存为json格式为{“title”:xx,“coin_number”:0，”play_number”:n1,”collection_number”:n2,”top_10_hot_remark”:[‘remark1’,’remark2’],”tags”:[]}，文件名为    0403_<视频标题>.json；4、打开0403intro.txt，理解manus是什么，然后，打开每个名为0403_<视频标题>.json的文件，读取json后分析视频视频属于什么类型，为什么会火，输出一个html报告，注意文字内容为中文
```
