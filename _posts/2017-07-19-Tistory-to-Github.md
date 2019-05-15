---
title: Tistory to Github
date: 2013-12-24 23:29:08
categories:
 - Test
 - Guide
description: Code Guide
tags: 
- Test
- Guide
---
기존 Tistory<https://sophia2730.tistory.com/>에서 Github 이전 작업 중입니다.

# Normal block

```
alert('Hello World!');
```

    print 'helloworld'

# Highlight block

```javascript
alert( 'Hello, world!' );
```

```python
print 'helloworld'
```

```ruby
def foo
  puts 'foo'
end
```

{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}

{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}

```c++
#include <iostream>

using namespace std;

void foo(int arg1, int arg2)
{

}

int main()
{
  string str;
  foo(1, 2);
  cout << "Hello World" << endl;
  return 0;
}
```

Image Test
![Image](/assets/images/searchicon.png){: width="auto"}

Local
cd /Users/sophia/Desktop/Github/cs-Devlog
bundle exec jekyll server