# P16 软件工程 - Software Engineering

现代软件通常具有庞大的代码量，如Microsoft office系列大致有40,000,000行的代码量，不可能由个人完成，为了完成庞大的软件，程序员动用各种工具和方法进行合作，形成了软件工程学科。

## 面向对象编程

将功能代码打包为函数，将相关的函数打包为对象，对象可层层嵌套打包，相互调用，通过封装组件来隐藏复杂度，这种思想叫做“面向对象编程”(Object Oriented Programming)。

```python
# 对象嵌套
OBJECT Car
    OBJECT Engine
    OBJECT Transmission
    OBJECT Wheels
    ...
    VARIABLE vinNumber
    VARIABLE yearBuilt
    ...
END OBJECT

Car.Engine.CruiseControl.setCruiseSpeed(55)
```

这种将大型软件拆成一个个更小单元的方式，更适合团队合作，为了团队间能够互用协作，除了分工写代码，还需要：

* 文档(Documentation)：帮助理解代码做什么；
* 程序编程接口(Application Programming Interface, API)：可以在不知道具体细节情况下，让其他程序员调用代码。API控制哪些代码可让外部访问(Public)，哪些仅供内部(Private)，

**核心** 面向对象的核心是隐藏复杂度，选择性地发布功能，有利于大型项目的开展。

## 集成开发环境

代码在编译前只是文本，可以用任意文本编辑器编译，但是为了能够在编辑文本过程中更好的展示、管理、编辑和测试代码，通常会使用工具“集成开发环境”(Integrated Development Environments, IDE)。

### Debug

程序员70%-80%的时间是在Debug，而不是写新的代码。

### 写文档

程序员另一重要的工作是给代码写文档，放在Readme文件中，以及代码的注释中。好的文档和注释能够提高代码的复用性(Code Reuse)

## 版本控制

除了IDE这一开发环境，另一重要工具是“源代码管理”(Source Control)，或称“版本控制”(revision control)。

在大型公司中，代码会被集中放在一个服务器上，称为代码仓库(Repository)，当程序员需要修改某部分代码，需要Check It Out，然后在自己的电脑上进行更新测试，测试通过后，可以将代码“提交”(commit)回去，当一部分代码被Check out时，其他程序员不会修改这部分代码，防止重复劳动。

代码的主版本(Master)应该是总可以正常编译的，如果在修改过程中出现问题，可以“回滚”(Rolled Back)旧版本。同时管理器会记录修改人员，以便协调沟通。

## 代码测试

代码测试统称为“质量保证测试”(Quality Assurance, QA)，要模拟软件运行过程中的各种情况，看软件会不会出错，以确保软件可以完成预期效果。
