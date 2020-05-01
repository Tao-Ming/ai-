```ruby
junit 
如果点击方法名，类名，包名，工程名。分别测试着对应的方法
@Test测试的方法不能是static和不能有形参
如果测试一个方法时候需要准备测试的环境或者清理测试的环境，那么可以@Before @After @BeforeClass @AfterClass

junit使用规范：
1.一个类如果需要测试，那么该类就对应着一个测试类：被测试的类名+Test
2.被测试方法的命名规范：test+被测试的方法
段言
Assert. assertEquals(new String("abc"),"abc")





```
