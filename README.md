# front-end-practice
安畅前端实践

## 贡献方法
1. Fork 主项目到个人仓库
2. 本地仓库建立两个远程，分别对应主项目及个人项目。
``` bash
  git remote add upstream git@github.com:anchnet/front-end-practice.git
  git remote add origin git@github.com:<my_name>/front-end-practice.git
```
3. 开发流程
``` bash  
  # 拉取主项目最新代码
  git pull upstream master

  # 启动本地服务器
  hexo server
  # 或
  npm run server
```

4. 发布流程
``` bash
  # 生成静态文件（注意：发布前只需要 generate 不需要 deploy）
  hexo generate
  # 或
  npm run build

  # 推到个人项目远程
  git push origin master
```

5. 向主项目发起 pull request