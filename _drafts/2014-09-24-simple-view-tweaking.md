---
layout: post
title:  "Simple View Tweaking"
date:   2014-09-24 17:17:20
categories: android view
---

Subclassing [View][view] is the first step for making any kind of changes to the UI widgets that ship with Android.  

Google's Android [training][custom_view_training] and [API][custom_view_api_guide] [guides][drawing_api_guide] contain several helpful pages.  This post will demonstrate...

Starting [here][custom_view_training], you might want to take a look at the [sample project](http://developer.android.com/shareables/training/CustomView.zip) before starting.  Sadly, importing this project into Android Studio (0.8.9), is non-trivial and is covered....

ToggleButton

I'l




To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[view]: http://developer.android.com/reference/android/view/View.html
[custom_view_training]: http://developer.android.com/training/custom-views/index.html
[custom_view_api_guide]: http://developer.android.com/guide/topics/ui/custom-components.html
[drawing_api_guide]: http://developer.android.com/guide/topics/graphics/2d-graphics.html