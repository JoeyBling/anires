<template>
  <div class="resumeEditor" :class="{htmlMode:enableHtml}" ref="container">
    <div v-if="enableHtml" v-html="result"></div>
    <pre v-else>{{result}}</pre>
  </div>
</template>

<script>
import marked from "marked";
export default {
  props: ["markdown", "enableHtml"],
  name: "ResumeEditor",
  computed: {
    result: function() {
      var rendererMD = new marked.Renderer();
      //基本设置
      marked.setOptions({
        renderer: rendererMD,
        gfm: true, //允许 Git Hub标准的markdown.
        tables: true, //允许支持表格语法（该选项要求 gfm 为true）
        breaks: true, //允许回车换行（该选项要求 gfm 为true）
        pedantic: false, //不纠正原始模型任何的不良行为和错误（默认为false）
        sanitize: false, //对输出进行过滤（清理），将忽略任何已经输入的html代码（标签）
        smartLists: true, //使用比原生markdown更时髦的列表
        smartypants: false //使用更为时髦的标点
      });
      //https://github.com/markedjs/marked/issues/655#issuecomment-383226346
      const linkRenderer = rendererMD.link;
      rendererMD.link = (href, title, text) => {
        const html = linkRenderer.call(rendererMD, href, title, text);
        return html.replace(/^<a /, '<a target="_blank" rel="nofollow" ');
      };
      return this.enableHtml
        ? marked(this.markdown, { rendererMD })
        : this.markdown;
    }
  },
  methods: {
    goBottom: function() {
      this.$refs.container.scrollTop = 100000;
    },
    goTop: function() {
      this.$refs.container.scrollTop = 0;
    }
  }
};
</script>

<style scoped>
@media (max-width: 500px) {
  .resumeEditor {
  }
}
.htmlMode {
  animation: flip 2s;
}

@keyframes flip {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
