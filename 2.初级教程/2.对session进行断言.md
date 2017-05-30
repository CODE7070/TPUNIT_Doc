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
~~~
<?php
namespace app\index\controller;
use think\Session;//注意引入Session
class Index
{
	//添加一个值
	public function addOneValue(){
		Session::clear();
		Session::set('value1',1);
	}
	//添加多个值
	public function addTwoValue(){
		Session::clear();
		Session::set('value2',2);
		Session::set('value3',3);
	}
}
~~~

针对上面的这段代码，我们可以在tests目录下增加一个IndexTest.php对其进行测试:
~~~

<?php
namespace tests;
//针对Index控制器
class IndexTest extends TestCase
{
	public function testAddOneValue(){
		$response=$this->visit('/index/index/addOneValue');
		$response->assertSessionHas('value1');
		$response->assertSessionHas('value1',1);
	}
	
	public function testAddTwoValue(){
		$sessData=array(
		'value2'=>2,
		'value3'=>3
		);
		$response=$this->visit('/index/index/addTwoValue');
		$response->assertSessionHas($sessData);
	}
}
~~~
