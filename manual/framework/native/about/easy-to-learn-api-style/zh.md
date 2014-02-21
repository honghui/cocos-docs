# 易学易用——API类型

## 两阶段构造器及静态create()函数

在cocos2d-x引擎中，我们使用了两阶段构造器，这不仅指Objective-C实现文件（implementation），也与Symbian SDK及Bada SDK相似。我认为这一举措在C++编程中很不错。

```
MyClass::MyClass()  // c++ class constructor
```

我们之所以不应在这里编写任何逻辑，是因为C++默认构造器不能返回表明我们逻辑正确与否的bool 值。

bool MyClass::initWithFilename(const char* filename)

MyClass* obj = new MyClass;

在cocos2d-x引擎中，我们已对这一两阶段构造器进行包装，并在静态函数create()中自动释放引用计数。除了单例模式，每一个cocos2d类都有自己的static CCClass* CCClass::create(...)方法。极力推荐这一方法。代码样本：

```


## doSomething()

这是最常见的函数名，在cocos2d-x/-html5引擎中处处都有应用到。第一个字是一个动词，第二个字是一个名词。比如： **replaceScene(CCScene*)** 和 **getTexture()**。

## doWithResource()


class CCLayer
因为历史原因，这类函数还没有应用到所有回调方法中。我们需要与旧版本保持兼容性。典型的反例就是**CCTouchDelegate**，其回调函数名仍为**bool ccTouchBegan(…)**, **bool ccTouchMoved(…)** 等。在未来的版本中，我们将对其进行修改。


因为在C++ 和 C++11中没有"property" （“属性”）这个概念，所以我们在Cocos2d-x引擎中使用了许多“getter/setters”。


改变属性的值。这通常会影响到对象的行为。比如 **_sprite->setPosition(ccp(0,0))** 会将精灵移动到左下角。


```

