在TP单元测试扩展中，增加的断言最多便是seeXX断言系列。在快速入门的例子中，我们就使用了see断言函数。在扩展中，还有其他的see函数，他的名字通常是seeXX，比如seeJson。

# see
接收两个参数，用于断言一个正则是否在结果中可以匹配。第二个参数是布尔值，当为假的时候断言第一个参数在结果中匹配。当为真的时候断言第一个参数不在结果中匹配。
# notSee
本方法使用了see，并且设置see的第二个参数为假。
# seeJson
# seeJsonEquals
# seeJsonContains
# seeModule
# seeController
# seeAction
# seeStatusCode
# seeHeader
# seeCookie