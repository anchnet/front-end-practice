# front-end-practice
安畅前端实践

## 开发方式
1. Fork 主项目到个人仓库
2. 本地仓库建立两个远程，分别对应主项目及个人项目。
``` bash
  git remote add upstream git@github.com:anchnet/front-end-practice.git
  git remote add origin git@github.com:xiaoda/front-end-practice.git
```
3. git 操作
``` bash  
  # 拉取主项目最新代码
  git pull upstream master

  # 推到个人项目远程准备发起 pull request
  git push origin master
```
4. hexo 操作
``` bash
  # 启动本地服务器
  hexo server
  # 或
  npm run server

  # 生成静态文件（发布准备）
  hexo generate
  # 或
  npm run build

  # 注意：发布前只需要 generate 不需要 deploy
```