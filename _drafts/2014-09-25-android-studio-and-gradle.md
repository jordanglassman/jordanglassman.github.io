---
layout: post
title:  "Android Studio and Gradle"
date:   2014-09-25
categories: android-studio
wiki_link: "http://en.wikipedia.org/wiki/"
---

Gradle, the Gradle wrapper, the Gradle plugin, the Gradle system installation, the local installation, version 0.9, version 2.1, gradle-1.10-all.zip, gradle-2.0-bin.zip.  What does it all mean?  Why aren't the constant error messages a little more (at all) descriptive?  [Where can I find out what in the world Gradle is actually doing](http://stackoverflow.com/questions/24151396/how-can-i-view-android-build-gradle-tasks-from-android-studio)? 

In this post, I'll tackle these questions to buttress my own sanity.

[Google teamed up with Gradleware](http://www.gradleware.com/android/gradle-the-new-android-build-system/), the commercial arm of the Gradle build automation project.  The goal with Gradle seems to have been to improve upon the storied XML-based [Apache Ant]({{ page.wiki }}/Apache_Ant) and the more modern Java-based cousin, [Maven]({{ page.wiki_link }}/Apache_Maven).  More on Gradle later, perhaps.

Gradle is based on...

The Android documentation has with references to the (Eclipse) Gradle plugin and the (Android Studio) Gradle wrapper.  

The wrapper is actually a shell script (`gradlew` or `gradlew.bat`) that Android Studio puts in the root of new projects.  This script does a few things:

- executes the Java class [GradleWrapperMain] (https://github.com/gradle/gradle/blob/master/subprojects/wrapper/src/main/java/org/gradle/wrapper/GradleWrapperMain.java), which is found in `$APP_HOME/gradle/wrapper/gradle-wrapper.jar`.  This class downloads the version of Gradle specified by the filename in `$APP_HOME/gradle/wrapper/gradle-wrapper.properties`.  


You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve --watch`, which launches a web server and auto-regenerates your site when a file is updated.

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

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help

Great blog about Gradle here:  http://mrhaki.blogspot.com/
