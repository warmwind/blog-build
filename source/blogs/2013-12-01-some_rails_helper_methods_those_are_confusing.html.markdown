---
title: 常用易混的四个Rails View Helper方法
date: 2013-12-01
tags: Rails, View Helper
category: PROGRAMMING
status: publish
---

Rails中有非常多强大的View Helper，今天其实想在这里简单总结其中4个与安全相关的，但是又容易混淆的。

它们分别是: [h](http://api.rubyonrails.org/classes/ERB/Util.html#method-c-h), [html_safe](http://api.rubyonrails.org/classes/String.html#method-i-html_safe), [simple\_format](http://api.rubyonrails.org/classes/ActionView/Helpers/TextHelper.html#method-i-simple_format), [sanitise](http://api.rubyonrails.org/classes/ActionView/Helpers/SanitizeHelper.html#method-i-sanitize)。

READMORE

1\. h

我们经常需要在页面上动态展示文字，这些完全可能来自用户的输入。所以为了防止XSS，在页面渲染时，需要对文字进行转义。在Rails2时，经常见到如下的代码

```erb
<%= h some_text %>
```
其中h方法就是进行转义操作，它的同义方法为html_escape。当然在Rails3之后，h方法已经是默认调用，所以不要再显示出现了。
从源代码可以看出，这里会对四种符号进行转义（&"'><），也就是在Rails的console中可以尝试如下代码

```ruby
include ERB::Util
 => Object
> puts html_escape("is a > 0 & a < 10?")
is a &gt; 0 &amp; a &lt; 10?
```

2\. html_safe


