<template>
  <div id="app">
    <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
    <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
  </div>
</template>

<script>
import StyleEditor from "./components/StyleEditor";
import ResumeEditor from "./components/ResumeEditor";
import "./assets/reset.css";
export default {
  name: "app",
  components: {
    StyleEditor,
    ResumeEditor
  },
  data() {
    return {
      interval: 3,
      currentStyle: "",
      enableHtml: false,
      fullStyle: [
        `/*
* Inspired by http://strml.net/
* 源码地址 https://gitee.com/zhousiwei/anires
* 大家好，我是試毅-思伟。
* 我来写一份简历！
*/

/* 首先给所有元素加上过渡效果 */
* {
  transition: all .1s;
}
/* 白色背景太单调了，我们来点背景 */
html {
  color: rgb(222,222,222);
  background: rgb(0,43,54);
}
/* 文字离边框太近了 */
.styleEditor {
  padding: .5em;
  border: 1px solid;
  overflow: auto;
  width: 90vw;
  margin: 2.5vh 5vw;
  height: 90vh;
}
/* 太高了 */
.styleEditor {
  height: 45vh;
}
/* 代码高亮 */
.token.selector{
  color: rgb(133,153,0);
}
.token.property{
  color: rgb(187,137,0);
}
.token.punctuation{
  color: yellow;
}
.token.function{
  color: rgb(42,161,152);
}
/* 加点 3D 效果呗 */
html{
  perspective: 1000px;
}
.styleEditor {
  position: fixed; left: 0; top: 0;
  transform: rotateX(-10deg) translateZ(-50px) ;
}
/* 接下来我给自己准备一个编辑器 */
.resumeEditor{
  position: fixed;
  top: 50%; left: 0;
  padding: .5em;  margin: 2.5vh;
  width: 95vw; height: 45vh;
  border: 1px solid;
  background: white; color: #222;
  overflow: auto;
}
/* 开始写简历 */
`,
        `
.resumeEditor{
  padding: 2em;
}
.resumeEditor h2{
  display: inline-block;
  border-bottom: 1px solid;
  margin: 1em 0 .5em;
}
.resumeEditor ul,.resumeEditor ol{
  list-style: none;
}
.resumeEditor ul> li::before{
  content: '•';
  margin-right: .5em;
}
.resumeEditor ol {
  counter-reset: section;
}
.resumeEditor ol li::before {
  counter-increment: section;
  content: counters(section, ".") " ";
  margin-right: .5em;
}
.resumeEditor blockquote {
  margin: 1em;
  padding: .5em;
  background: #ddd;
}
`
      ],
      currentMarkdown: "",
      fullMarkdown: `
周思伟
----
23岁，Java软件工程师，三年Java EE 从业经验，目前在杭州工作。
有良好的文档编写和代码书写规范，能独立解决问题、百折不挠、细节控
<br/>

- [中英文简历](https://zhousiwei.gitee.io/cv/)

技能
----
* 后端开发
* 聚合支付
* 单点登录
* 权限管理
* 公众号/小程序开发
* API接口开发
* Linux
* 开源爱好者
* 博客系统

技术及语言
----
  - **Java**: SpringBoot、SpringCloud、SpringMVC、MyBatis、Shiro、Freemarker
  - **前端**: VueJs、Bootstrap、LayUI、jQuery UI
  - **数据库**: MySQL/MariaDB、SQLServer、Oracle、MongoDB、redis、memcached
  - **web 服务器**: Nginx、Tomcat、Apache、Jetty
  - **OS**: Linux、Windows
  - **Others**: Git、Svn、Maven、XMind、Visio、IDEA

工作经历
----
1. [杭州特扬网络科技有限公司](http://www.hztywl.cn/)
2. [江西三叉数信息科技有限公司](http://www.3xdata.cn/)
3. [江西益强微盈信息科技有限公司](http://jxyq123.51sole.com/)

开源项目
----
1. [基于SpringBoot + Shiro + MyBatisPlus的权限管理框架](https://gitee.com/zhousiwei/bootplus)
2. [SpringBoot集成MyBatisPlus集成Shiro可以快速开发](https://gitee.com/zhousiwei/springboot_mybatisplus)
3. [自制spring boot starter for fastjson](https://gitee.com/zhousiwei/fastjson-spring-boot-starter)
4. [基于web版kettle开发的一套分布式综合调度,管理,ETL开发的用户专业版B/S架构工具](https://github.com/JoeyBling/webkettle)
5. [一个会动的简历](https://gitee.com/zhousiwei/anires)
6. [VuePress记录技术开发笔记](https://gitee.com/zhousiwei/ibooks)
7. [使用GitBook记录开发笔记](https://zhousiwei.gitee.io/myBook/)
8. [試毅-思伟的技术博客网站](https://gitee.com/zhousiwei/zhousiwei)

链接
----
* [技术博客](https://zhousiwei.gitee.io/)
* [GitHub](https://github.com/JoeyBling)
* [简书](https://www.jianshu.com/u/02cbf31a043a)
* [开发笔记](https://zhousiwei.gitee.io/ibooks)

[归档文章](https://zhousiwei.gitee.io/)
----
1. [Java](https://zhousiwei.gitee.io/tags/Java/)
2. [Linux](https://zhousiwei.gitee.io/tags/Linux/)
3. [ELK日志分析](https://zhousiwei.gitee.io/tags/ELK%E6%97%A5%E5%BF%97%E5%88%86%E6%9E%90/)
4. [MySQL](https://zhousiwei.gitee.io/tags/MySQL)
5. [Hexo](https://zhousiwei.gitee.io/tags/Hexo)
6. [日记本](https://zhousiwei.gitee.io/tags/%E6%97%A5%E8%AE%B0%E6%9C%AC/)

联系我
----
* 联系QQ：**2434387555** | 微信：**13647910412**
* 主要涉及技术：**Java后端开发**、**聚合支付**、**公众号开发**、**开源爱好者**、**Linux**

> 如果你喜欢这个效果，Fork [我的项目](https://gitee.com/zhousiwei/anires)，打造你自己的简历！
`
    };
  },
  created() {
    this.makeResume();
  },
  methods: {
    makeResume: async function() {
      await this.progressivelyShowStyle(0);
      await this.progressivelyShowResume();
      await this.progressivelyShowStyle(1);
      await this.showHtml();
      await this.progressivelyShowStyle(2);
    },
    showHtml: function() {
      return new Promise((resolve, reject) => {
        this.enableHtml = true;
        this.$nextTick(() => {
          this.$refs.resumeEditor.goTop();
        });
        resolve();
      });
    },
    progressivelyShowStyle(n) {
      return new Promise((resolve, reject) => {
        let interval = this.interval;
        let showStyle = async function() {
          let style = this.fullStyle[n];
          if (!style) {
            return;
          }
          // 计算前 n 个 style 的字符总数
          let length = this.fullStyle
            .filter((_, index) => index <= n)
            .map(item => item.length)
            .reduce((p, c) => p + c, 0);
          let prefixLength = length - style.length;
          if (this.currentStyle.length < length) {
            let l = this.currentStyle.length - prefixLength;
            let char = style.substring(l, l + 1) || " ";
            this.currentStyle += char;
            if (style.substring(l - 1, l) === "\n" && this.$refs.styleEditor) {
              this.$nextTick(() => {
                this.$refs.styleEditor.goBottom();
              });
            }
            setTimeout(showStyle, interval);
          } else {
            resolve();
          }
        }.bind(this);
        showStyle();
      });
    },
    progressivelyShowResume() {
      return new Promise((resolve, reject) => {
        let length = this.fullMarkdown.length;
        let interval = this.interval;
        let showResume = () => {
          if (this.currentMarkdown.length < length) {
            this.currentMarkdown = this.fullMarkdown.substring(
              0,
              this.currentMarkdown.length + 1
            );
            let lastChar = this.currentMarkdown[
              this.currentMarkdown.length - 1
            ];
            let prevChar = this.currentMarkdown[
              this.currentMarkdown.length - 2
            ];
            if (prevChar === "\n" && this.$refs.resumeEditor) {
              this.$nextTick(() => this.$refs.resumeEditor.goBottom());
            }
            setTimeout(showResume, interval);
          } else {
            resolve();
          }
        };
        showResume();
      });
    }
  }
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
  position: relative;
}
html {
  min-height: 100vh;
}
* {
  box-sizing: border-box;
}
</style>