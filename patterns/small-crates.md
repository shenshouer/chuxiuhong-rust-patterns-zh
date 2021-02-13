# 偏爱更小的库

## 说明

Prefer small crates that do one thing well.

偏向于使用专注于做好一件事的库。

Cargo和crate.io使得使用第三方库更简单，比C和C++在这一点上更强。此外，因为crates.io上的包发布后就不能编辑和撤销，任何发布在未来都要能够工作。我们应该采用这种工具的优点，并且使用更小的，更细粒度的依赖。

## 优点

* 小的库更容易理解，并且鼓励更加模块化代码。
* 库支持在不同项目间重用代码。举例来说，`url`库是作为Servo浏览器引擎的一部分开发的，但是其也被广泛用于这个项目之外。由于Rust的编译单元是Crate，所以讲一个项目拆分为多个Crate可以允许并行编译更多的代码。

## 缺点

* 当一个项目依赖多个有矛盾版本的库时，会导致“依赖地狱”。举例来说，`url`库有0.5和1.0两个版本。由于`Url`在`url:1.0`中和`url:0.5`中是不同的类型，一个使用`url:0.5`的HTTP客户端不能接受使用`url:1.0`的网络爬虫传递的`Url`值。
* 在crates.io上的包时没有策划的。一个库可能写的不好，只有没有帮助的文档，或者是彻头彻尾的恶意代码。
* 两个小库可能比一个大的库的优化要更少，因为编译器默认没有开启链接时优化。

## 示例

`ref_slice`库提供转换`&T`为`&[T]`的函数。

`url`库提供处理URL的工具。

`num_cpus`库提供一个函数来查询机器上的CPU数量。

## See also

* [crates.io: The Rust community crate host](https://crates.io/)