---
layout: post
title: Sass undefined method '[]'
---

Working on Rails upgrade to versions 4.2 recently, I came across the following error message:

`NoMethodError undefined method '[]' for "image":Sass::Script::Value::String`

Backtrace pointed at nonrelevant line, so I had no idea where to start searching. Fortunately I found the solution at <https://github.com/rails/sprockets-rails/issues/279>.

It seems like the issue was my `asset-url` method using old two-argument call:

{% highlight ruby %}
asset-url('payments/cards_new.png', image)
{% endhighlight %}

I removed the last argument according to <http://guides.rubyonrails.org/upgrading_ruby_on_rails.html> depreciation notice and it worked like charm.

