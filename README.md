**本项目源于：[https://github.com/jirengu-inc/animating-resume](https://github.com/jirengu-inc/animating-resume "https://github.com/jirengu-inc/animating-resume")。向作者表示深深的敬意。**

# 一个会动的简历模板
- 功能还很少，欢迎各位给我提意见和建议~

## 线上预览

> **This is my resume ➡️ [https://joeybling.github.io/anires/index.html](https://joeybling.github.io/anires/index.html)**

## 项目截图

[![試毅-思伟的个人简历](./screenshots/all_mini.png "試毅-思伟的个人简历")](https://joeybling.github.io/anires/index.html "試毅-思伟的个人简历")

## 使用方法
```bash
git clone https://github.com/JoeyBling/anires.git
cd anires
npm install
npm run dev
```

## 部署方法

1. 编辑 **config/index.js**，修改第 10 行的 `assetsPublicPath`，值为 `项目名/public`。如果你没有修改项目名 `anires`，则可跳过此步骤。

2. 编译、上传
```bash
npm run build
git add .
git commit -m "update"
git push
```
3. 开启 **GitHub Pages** 功能，把生成的目标文件`public/*`放在你的web服务器上。

4. 访问地址：[https://your-github-username.github.io/anires/public](https://joeybling.github.io/anires/index.html "https://joeybling.github.io/anires/index.html")

# 关于我
- [个人博客](https://zhousiwei.gitee.io/)
- [技术笔记](https://zhousiwei.gitee.io/ibooks/)
- [GitHub](https://github.com/JoeyBling)
- [码云](https://gitee.com/zhousiwei)
- [简书](https://www.jianshu.com/u/02cbf31a043a)
- [CSDN](https://blog.csdn.net/qq_30930805)
- [知乎](https://www.zhihu.com/people/joeybling)
- [微博](http://weibo.com/jayinfo)
- **主要涉及技术：`Java后端开发`、`聚合支付`、`公众号开发`、`开源爱好者`、`Linux`**

## License

[Apache License](./LICENSE)
