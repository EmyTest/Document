# Dicument
# https://www.cnblogs.com/JHblogs/p/6418802.html
postman 获取上一个接口里面的header值作为下一个接口的参数

tests：
var data = postman.getResponseHeader("A-Token-Header")
postman.setEnvironmentVariable("token",data)

在下一个接口的header里面填入  key： A-Token-Header     value：{{token}}

postman 获取上一个接口里面的body值作为下一个接口的参数
var jsonData =JSON.parse(responseBody);//获取body中返回的所有参数
postman.setEnvironmentVariable("appKey",jsonData.data.appKey);//把返回参数中的keys设置为环境变量
