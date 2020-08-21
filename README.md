#  营销小精灵 MktBot
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
| 登入 | usr_login |curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/usr_login?mng=13668888888' -d '{"pwd":"888888"}' 
| 改密码 | usr_new_pswd | curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/usr_new_pswd?mng=13668888888' -d '{"pwd":"888888","pwd_new":"12345"}' 
| 登出 | usr_logout |curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_logout'
| 创建组 | lcs_grp__new |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__new?grp=XX'
| 注销组 | lcs_grp__del |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__del?grp=XX'
| 许可证加入组 | lcs_grp__in |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__in?grp=XX&lcs=293E-D82C-6005-625D'
| 许可证移出组 | lcs_grp__out |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__out?grp=XX&lcs=293E-D82C-6005-625D'
| 列出组内许可证 | lcs_grp__list |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_grp__list?grp=XX'
| 许可证解绑 | lcs_reset |curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_reset?lcs=293E-D82C-6005-625D'

## 任务列表

### 搜索用户评论区关注私信
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSPLQGZSX" \
  -d '{ "go_first":"1", "reset":"0", "q":"玩具", "search_mode":"video", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_digg":"1", "pr_talk2":"1", "talk2_triggerwords":["买","多少钱"], "talk2_texts":["我有货，更便宜","真棒!"] }'
```
### 搜索转发视频
```shell
$ curl -b cookie -c cookie -X POST "https://api.media-marketing-server.com/order_new?grp=XX&func=DOUYIN_SSZFSP" \
  -d '{ "go_first":"1", "reset":"0", "q":"玩具", "search_mode":"video", "CNT:video_view_total":"20", "dur:avg":"10", "dur:std":"0.5", "pr_forward":"1" }'
```

