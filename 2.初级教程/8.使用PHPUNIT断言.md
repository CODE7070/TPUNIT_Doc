在单元测试扩展中，我们除了使用扩展提供给我们的断言语句之外，我们还可以使用PHPUNIT的断言语句。
由于TP自动加载器也会加载composer模块，因此在测试类中，我们直接使用PHPUNIT的类就行。
首先我们跟先前的例子一样，先新建一个控制器：
~~~
<?php
namespace app\index\controller;
use think\Controller;
use think\Response;
class Index
{
	public function index(){
		return 'test';
	}
}
~~~

该控制器的功能就是输出一段字符串,test。我们要做的功能就是对输出的结果进行断言。

PHPUNIT的断言包名比较长，我们首先给报名一个简短的别名。
`use PHPUnit_Framework_Assert as PHPUnit;`
加入上面这一条语句之后，我们就可以在该文件中使用PHPUnit直接访问到PHPUNIT 断言类语句了。然后我们新建一个测试方法，在这个方法里面模拟发送一个请求给TP。
`$this->visit('/index/index/index');`
该语句就是访问上面的操作。接着我们再使用PHPUNIT的断言语句对这次请求的结果进行断言。
`PHPUnit::assertEquals('test',$this->response->getContent());`
assertEquals接受三个参数，第一个参数是期望的值，也就是期望的结果值。第二个是实际值，就是运行之后的实际值。第三个则是一个说明，当断言不成立的时候会回显到终端上面来。
总的测试类为：
~~~
<?php
namespace tests;
use PHPUnit_Framework_Assert as PHPUnit;
//针对Index控制器
class IndexTest extends TestCase
{
	public function testOutput(){
		$this->visit('/index/index/index');
		PHPUnit::assertEquals('test',$this->response->getContent());
	}
}
~~~
更多的PHPUNIT断言语句，可以查看PHPUNIT的相关手册：
[PHPUNIT断言中文手册](http://www.phpunit.cn/manual/current/zh_cn/appendixes.assertions.html#appendixes.assertions.assertEquals)