#  营销小精灵 MktBot
## 客户端
0. 与代理商接洽，由代理商在系统内登记您的手机号，为您开户
1. 在您的 Android 手机上打开 MktBot
2. 在 MktBot 内的用户号输入框，输入您的手机号
3. 点击"重新登录"按钮，等待10秒，如许可证字段显示证书，说明本手机已经连上服务器
4. 点击"无障碍服务"，开启"营销小精灵 APK"，开启后点击设置可以回到客户端主界面
5. 点击"开始工作"

## 超级用户
|  动作   | API  | 示例  |
|  ----  | ----  | ---- |
| 创建代理商 | mng_new |curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/mng_new?mng=13661234567' -d '{"root_key":"XXXX-XXXX-XXXX-XXXX"}'

## 代理商 
|  动作   | API  | 示例  |
|  ----  | ----  | ---- |
| 登入 | mng_login |curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/mng_login?mng=13661234567' -d '{"pwd":"888888"}' 
| 改密码 | mng_new_pswd | curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/mng_new_pswd?mng=13661234567' -d '{"pwd":"888888","pwd_new":"12345"}' 
| 登出 | mng_logout |curl -b cookie -c cookie 'https://api.media-marketing-server.com/mng_logout'
| 新建用户 | usr_new | curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_new?usr=13668888888' 
| 注销用户 | usr_del | curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_del?usr=13668888888' 
| 新产生许可证 | lcs_new | curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_new?n=5' 
| 许可证授予某用户 | lcs_sell | curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_sell?usr=13668888888&n=5'

## 用户

|  动作   | API  | 示例  |
|  ----  | ----  | ---- |
| 登入 | usr_login |curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/usr_login?usr=13668888888' -d '{"pwd":"888888"}' 
| 改密码 | usr_new_pswd | curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/usr_new_pswd?usr=13668888888' -d '{"pwd":"888888","pwd_new":"12345"}' 
| 登出 | usr_logout |curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_logout'
| 创建组 | lcs_grp__new |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__new?grp=XX'
| 注销组 | lcs_grp__del |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__del?grp=XX'
| 许可证加入组 | lcs_grp__in |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__in?grp=XX&lcs=293E-D82C-6005-625D'
| 许可证移出组 | lcs_grp__out |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__out?grp=XX&lcs=293E-D82C-6005-625D'
| 列出组内许可证 | lcs_grp__list |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__list?grp=XX'
| 许可证解绑 | lcs_reset |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_reset?lcs=293E-D82C-6005-625D'

## 任务列表

### 字段一览
|  字段名 | 说明 |
|  ----   | ---- |
| go_first | 1:本任务放入任务池顶，相关设备结束当前任务后立即执行此任务 0:本任务放入任务池底 |
| reset | 是否清空任务池 |
| q | 搜索关键词 |
| search_mode | 搜索模式:视频(视频) |
|CNT:video_view_total | 看多少个视频 |
| dur:avg | 观看时长的平均值 |
| dur:std | 观看时长的"方差/均值"比率，0表示一样长，0.5表示方差为均值一半 |
| pr_digg | 点赞概率|
| pr_talk2 | 触发私信概率 |
| talk2_triggerwords | 评论含有哪些关键词将触发私信 |
| talk2_texts | 私信内容，随机选择 |
| pr_forward | 转发概率|
| pr_comment | 进入评论区的概率|
| comment_texts | 评论文本，随机选择|

### 任务: 搜索用户评论区关注私信
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSPLQGZSX" \
  -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1", "pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"] }'
```
### 任务: 搜索转发视频
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSZFSP" \
  -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_forward":"1" }'
```
### 任务: 搜索转发指定视频
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSZFZDSP" \
  -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_forward":"1" }'
```
### 任务: 搜索视频点赞
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSSPDZ" \
 -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1" }'
```

### 任务: 搜索视频点赞_plus
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSSPDZ_plus" \
 -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1" }'
```

### 任务: 搜索指定用户点赞评论
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSZDYHDZPL" \
 -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1","pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 搜索指定用户点赞评论_plus
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSZDYHDZPL_plus" \
 -d '{ "go_first":"1", "reset":"0", "q":"玩具", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1","pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 关注点赞评论
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_GZDZPL" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1","pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 关注私信Plus
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_GZSX_plus" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1","pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"] }'
```

### 任务: 多条视频点赞
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_GZDZ" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1"}'
```

### 任务: 推荐评论
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJPL" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 推荐私信
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJSX" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5","pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"] }'
```

### 任务: 推荐评论点赞 
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJPLDZ" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5","pr_digg":"1", "pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 推荐概率点赞
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJGLDZ" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10","dur:std":"0.5","pr_digg":"1"}'
```

### 任务: 推荐点赞
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJDZ" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10","dur:std":"0.5"}'
```

### 任务: 推荐浏览
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJLL" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10","dur:std":"0.5"}'
```
### 任务: 推荐回复
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TJHF" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10","dur:std":"0.5", "pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"]}'
```

### 任务: 同城私信
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TCSX" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5","pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"] }'
```

### 任务: 同城点赞
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TCDZ" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10","dur:std":"0.5"}'
```

### 任务: 同城评论点赞
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TCPLDZ" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5","pr_digg":"1", "pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 同城评论
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TCPL" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_comment":"1", "comment_texts":["真棒","666","我喜欢"] }'
```

### 任务: 同城回复
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_TCHF" \
 -d '{ "go_first":"1", "reset":"0", "CNT:video_view_total":"20", "dur:avg":"10","dur:std":"0.5", "pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"]}'
```


## FAQ
Q1: 如何快速调出MktBot客户端
ANS: 在手机上进入"设置/更多设置/无障碍/更多已下载的服务/营销小精灵 APK"，点开启服务后，点击页面底部的"设置"，即可。
