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
//前端跨域解决方案:浏览器请求必须遵循同源策略:同域名、同端口、同协议
/**
 * CROS跨域
 * JSONP跨域
 * 代理跨域
 */
//CROS跨域-服务端设置,前端直接调用
//说明:后台允许前端某个站点进行访问
//CROS跨域浏览器的Response Header 的Access-COntrol-Allow-Credentials会设置为true
//对于简单请求，浏览器直接发出CORS请求。具体来说，就是在头信息之中，增加一个Origin字段
//如果Origin指定的域名在许可范围内,服务器返回的响应,会多出几个头信息字段
/**
 * Access-Control-Allow-Origin: http://api.bob.com
   Access-Control-Allow-Credentials: true
   Access-Control-Expose-Headers: FooBar
   Content-Type: text/html; charset=utf-8

   CORS请求默认不发送Cookie和HTTP认证信息。如果要把Cookie发到服务器，
   一方面要服务器同意，指定Access-Control-Allow-Credentials字段。
   Access-Control-Allow-Credentials: true
   另一方面，开发者必须在AJAX请求中打开withCredentials属性。
   var xhr = new XMLHttpRequest();
   xhr.withCredentials = true;
   否则，即使服务器同意发送Cookie，浏览器也不会发送。或者，服务器要求设置Cookie，浏览器也不会处理。
   但是，如果省略withCredentials设置，有的浏览器还是会一起发送Cookie。这时，可以显式关闭withCredentials。
   xhr.withCredentials = false;
 */
export default {
  data() {
    return {};
  },
  mounted(){
    let url = "https://api-hmugo-web.itheima.net/api/public/v1/my/orders/all";
    axios.get(url).then(()=>{

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
