---
layout: post
title:  "What is a Context, anyway?"
date:   2014-09-24 23:40
categories: 
-android 
-context
---

{% include _links_library.markdown %}

The `Context` class lies at the root of the `Activity` hierarchy

Importing projects seamlessly into Android Studio can be non-trivial, presumably because the tool is in such a state of flux these days.  For a developer trying to follow along using the hopelessly out of date documentation and scattered samples, this can be an annoying, if edifying process.  

This post will try to document the various scenarios I've come up against while trying to RTFM.

### No IDE metadata at all

Example: [CustomViews.zip](http://developer.android.com/shareables/training/CustomView.zip)

In this scenario, no IDE was used to create the project or maybe IDE-specific metadata has been removed.  

Using Android Studio (as of 0.8.9), one can first File -> Import Project.  This gives the option to `Create project from existing sources` or `Import project from existing model`.  Here, "model" means "IDE model" or "build tool model".  I think it probably tells IntelliJ what directory structure and metadata to look for.  In the case of no metadata, select `Create project from existing sources`.

Use the default (directory name) or change the project name.

The import wizard then looks for source files and gives you the opportunity to select the project roots.  In Java terms, these are the directories housing the default package, as well as all user-defined packages in the normal hierarchical fashion.  

Next, the wizard looks for external libraries.  Perhaps it's looking for JAR files?  A `lib/` directory?  `import`s from unrecnognized packages?  The example I've selected here doesn't have any.  Updates as events warrant.

Now the wizard tries to guess an appropriate module structure for this project.   A "module" is an IntelliJ abstraction.  From their [docs](http://www.jetbrains.com/idea/webhelp/module.html), a "module is a discrete unit of functionality which you can compile, run, test and debug independently...Modules contain everything that is required for their specific tasks: source code, build scripts, unit tests, deployment descriptors, and documentation. However, modules exist and are functional only in the context of a project...Configuration information for a module is stored in a .iml module file...Development teams, normally, share the .iml module files through version control.

Next comes an opporunity to "select project SDK".  This wizard presumably looks in default installation locations for Android and Java SDKs.  


We then just have to include our library to use links like this :

[context]({{ androidRef }}/content/Context.html)

ContextImpl???

