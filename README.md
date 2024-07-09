# Bloom'Docs

一个简约的博客/笔记网站模板，基于 markdown + vitepress


## 使用
需要 Nodejs / pnpm

```bash
pnpm install # 安装
pnpm docs:dev # dev模式,本地查看文档
pnpm docs:build # 构建网站发布所需要的资源, build之后在 .vitepress/dist 下, 保证在本地能构建成功后再发布比较好
```

需要修改的内容：
- 可以修改 metadata/index.ts 配置一下自己的网站信息
- 再修改一下 index.md 配置一下首页
- 修改 `.vitepress/creators.ts`, 添加你的 github 地址，这样的话，在每个文章下面的贡献者那里就能够链接到你的 github 首页（否则只是一个名字，无法点击）。

## 部署
### vercel 部署
vercel 部署很简单, 在 vercel 中选择项目后, 修改构建的 output directory 为 .vitepress/dist 就行了（默认是 ./dist）

如果你选择了用 vercel 部署，可以关闭 netflify 的 workflow.

在 github仓库页面 -> Actions -> netlify 对应 workflow -> 右上角3个点 -> disable workflow

<img width="204" alt="image" src="https://github.com/Jackiexiao/nolebase-template/assets/18050469/aa83c0f4-9ff6-4fc2-b5df-eb45f81f6773">




## 开启 giscus 评论功能
giscus 利用了 [GitHub Discussions](https://docs.github.com/en/discussions) 实现的评论系统，让访客借助 GitHub 在你的网站上留下评论！（你的github仓库必须是公开的才能使用 giscus）

具体配置方法
- 第1步，访问 [Giscus](https://giscus.app/zh-CN) 网站， 参考网站上的说明，一步步操作，最后得到一个配置代码
- 第2步，在 `./vitepress/theme/index.ts` 中修改 giscus 相关配置，在该文件中搜索 `giscusTalk`, 参考说明，修改配置即可



