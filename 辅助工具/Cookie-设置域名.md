### 设置域名

正常情况下，同一个一级域名下的两个二级域名也不能交互使用Cookie，需要设置Cookie的domain参数为(**.主域名**)就能访问同一个cookie

实战：axio设置请求拦截器，取cookie内的token，设置请求头授权Authorization带上token