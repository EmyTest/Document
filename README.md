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

【一定要注意“jsonData.data.appKey”  即 定位返回值的位置，可点击左侧小三角形，折叠报文！！！！！！！！！！！！ 】



######################################################################################################################


1.设置环境变量
postman.setEnvironmentVariable("key", "value");

2.设置全局变量
postman.setGlobalVariable("key", "value");

pm.globals.set("variable_key", "variable_value");

3.检查response body中是否包含某个string
tests["Body matches string"] = responseBody.has("string_you_want_to_search");

4.检测JSON中的某个值是否等于预期的值

var data = JSON.parse(responseBody);
tests["Your test name"] = data.value === 100;
JSON.parse()方法，把json字符串转化为对象。parse()会进行json格式的检查是一个安全的函数。 

如：检查json中某个数组元素的个数(这里检测programs的长度)

var data = JSON.parse(responseBody);
tests["program's lenght"] = data.programs.length === 5;
5.转换XML body为JSON对象
var jsonObject = xml2Json(responseBody);

tests["Body is correct"] = responseBody === "response_body_string";

6.检查response body是否与某个string相等

7.测试response Headers中的某个元素是否存在(如:Content-Type)

tests["Content-Type is present"] = postman.getResponseHeader("Content-Type"); 
//getResponseHeader()方法会返回header的值，如果该值存在
或者： 

tests["Content-Type is present"] = responseHeaders.hasOwnProperty("Content-Type");
上面的方法，不区分大小写。下面的方法，要区分大小写。 


![日喔](https:////wx2.sinaimg.cn/orj360/b278a87fly1fqc5a3qy49j20xc1n9402.jpg) 

