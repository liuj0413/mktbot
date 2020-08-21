# mktbot
## 代理商 
|  动作   | API  | 示例  |
|  ----  | ----  | ---- |
| 登入 | mng_login |curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/mng_login?mng=13661234567' -d '{"pwd":"888888"}' ｜
| 改密码 | mng_new_pswd | curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/mng_new_pswd?mng=13661234567' -d '{"pwd":"888888","pwd_new":"12345"}' ｜
| 登出 | mng_logout |curl -b cookie -c cookie 'https://api.media-marketing-server.com/mng_logout'｜
| 新建用户 | usr_new | curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_new?usr=13668888888' ｜
| 注销用户 | usr_del | curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_del?usr=13668888888' ｜
| 新产生许可证 | lcs_new | curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_new?n=5' ｜
| 许可证授予某用户 | lcs_sell | curl -b cookie -c cookie 'https://api.media-marketing-server.com/lcs_sell?usr=13668888888&n=5'｜

## 用户

|  动作   | API  | 示例  |
|  ----  | ----  | ---- |
| 登入 | usr_login |curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/usr_login?mng=13668888888' -d '{"pwd":"888888"}' ｜
| 改密码 | usr_new_pswd | curl -b cookie -c cookie -X POST 'https://api.media-marketing-server.com/usr_new_pswd?mng=13668888888' -d '{"pwd":"888888","pwd_new":"12345"}' ｜
| 登出 | usr_logout |curl -b cookie -c cookie 'https://api.media-marketing-server.com/usr_logout'｜
