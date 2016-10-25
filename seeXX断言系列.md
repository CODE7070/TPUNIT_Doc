在TP单元测试扩展中，增加的断言最多便是seeXX断言系列。在快速入门的例子中，我们就使用了see断言函数。在扩展中，还有其他的see函数，他的名字通常是seeXX，比如seeJson。

# see
接收两个参数，用于断言一个正则是否在结果中可以匹配。第二个参数是布尔值，当为假的时候断言第一个参数在结果中匹配。当为真的时候断言第一个参数不在结果中匹配。
# notSee
本方法使用了see，并且设置see的第二个参数为真。

# seeJson
内部使用seeJsonContains，用于断言某个json是否在结果中

@param array $data 期望的json
@param boolean $negate 非操作，为真时是期望$data不在结果中

# seeJsonEquals
断言json是否跟结果相等。
@param array $data 传入一个数组，排序再转换成json

其内部会将实际值转回成数组进行排序后再跟$data排序后转换成的json进行断言。

# seeJsonContains
断言某个json是否在结果中。

@param array $data 期望的与断言的json数据
@param boolean $negate 非操作

# seeModule
用于断言请求中的模块。

@param string @module 欲断言的模块名字
`$this->visit('/index/index/index')->seeModule('index');`

# seeController
用于断言请求中的控制器。

@param string @controller 欲断言的控制器名字
`$this->visit('/index/index/index')->seeController('Index');`
>注意，控制器首字母是需要大写的。

# seeAction
用于断言请求中的操作。

@param string @action 欲断言的操作名字
`$this->visit('/index/index/index')->seeAction('index');`

# seeStatusCode
用于断言response的状态码。

# seeHeader
用于断言response的head部。

# seeCookie
用于断言Cookie中是否存在某个值。