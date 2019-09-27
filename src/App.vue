<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Edit/>
  </div>
</template>

<script>
import Edit from './components/Edit.vue'

export default {
  name: 'app',
  components: {
    Edit
  }
}
</script>

<style>
html,body,div,span,iframe,h1,h2,h3,h4,h5,h6,p,blockquote,a,address,em,img,ol,ul,li,dl,dt,dd,fieldset,form,label,legend,table,tbody,tfoot,thead,tr,th,td,i,b,s { margin: 0; padding: 0; border: 0; font-weight: normal; font-style: normal; font: 12px/120% Microsoft YaHei,Helvetica Neue,Helvetica,SimSun,PingFang SC,Hiragino Sans GB,sans-serif;color: #666;}
ul,ol{ list-style: none }
a img{ border: none; vertical-align: top }
a{ text-decoration: none }
button{ overflow: visible; padding: 0; margin: 0; border: 0 none; background-color: transparent }
button::-moz-focus-inner { padding: 0 }
textarea,input{ background: none; padding: 0; -webkit-border-radius: 0; -moz-border-radius: 0; border-radius: 0; }
input[type=password]{ -webkit-text-security: disc }
input[type=checkbox]{width: 13px;height: 13px;border: #d3d3d3 1px solid;background: #fff;}
textarea:focus,input:focus,button:focus { outline: none }
table{width: 100%;border-collapse: collapse; border-spacing: 0;}
table tr td{font-family: inherit;}
input, textarea, a {outline: none;font-family: Microsoft YaHei,Helvetica Neue,Helvetica,SimSun,PingFang SC,Hiragino Sans GB,sans-serif;}
td, input, button, select, body {font: inherit;-webkit-font-smoothing: subpixel-antialiased;}
textarea{resize: none;}
.clearfix:before,.clearfix:after { content: ""; display: table }
.clearfix:after { clear: both }
.clearfix{ *zoom:1}

</style>
