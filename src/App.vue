<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
  </div>
</template>
<script>
import axios from "axios";
import jsonp from 'jsonp'
//前端跨域解决方案:浏览器请求必须遵循同源策略:同域名、同端口、同协议
/**
 * CROS跨域
 * JSONP跨域
 * 代理跨域
 */
//JSONP跨域-前端适配,后台配合
//说明:前后台同时改造
/**
 * jsonp不是一个xhr,而是一段脚本js,只是访问了一个脚本带了一个接口
 * jsonp(url地址,option配置(可省略),回调函数(错误信息,返回信息))
 * jsonp只是一段Js脚本,在访问的时候传了一个callback=_jp0
 *
 *
 *
 */
export default {
  data() {
    return {
      data:''
    };
  },
  mounted(){
    // let url = "https://api-hmugo-web.itheima.net/api/public/v1/my/orders/all";浏览器:https://api-hmugo-web.itheima.net/api/public/v1/my/orders/all?callback=__jp0
    let url = "https://www.imooc.com/activity/servicetime";//https://www.imooc.com/activity/servicetime?callback=__jp0
    // axios.get(url).then(()=>{})
    //jsonp请求
    jsonp(url,(err,res)=>{
      let result=res
      this.data=result
      //data的信息就是返回的_jp0的信息
    })
  }
};
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
