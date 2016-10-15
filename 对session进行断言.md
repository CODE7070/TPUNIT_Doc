# 说明
因为HTTP协议是无状态的，因此在网站开发的过程中我们经常使用session保存用户信息。
在ThinkPHP的单元测试扩展中，我们是可以对session做出断言的。
在该测试扩展中，对session断言的涉及到两个方法：
~~~
1. assertSessionHas($key, $value = null)
2. assertSessionHasAll(array $bindings)
~~~
第一个方法是断言session中是否有保存某个key，其值对应value。当只提供一个参数的时候，只判断session是否存在key，而不判断其值。
第二个方法是对key值数组进行判断。

# 例子
下面给出一个例子，用于测试session的两个方法：
