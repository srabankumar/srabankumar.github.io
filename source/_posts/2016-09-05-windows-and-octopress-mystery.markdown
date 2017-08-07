---
layout: post
title: "Windows and octopress Mystery"
date: 2016-09-05 19:27:23 +0530
comments: true
categories: octopress, windows
---
Hi Folks,
  
  Octopress is one of the favourite tool for those( specially for Programmers)  who loves to write and post something in a blog  . If you are using linux system , then octopress installation and setup will be easier than those who are using windows. I am using windows8 and tried to setup octopress in my machine. Believe me , it took nearly 2 days to  setup octopress because of some errors which I am going to explain in this Article. So let's start.
  
  If you want to install octopress then you can go through this [Article](https://github.com/imathis/octopress/wiki/Installation-Instructions-2.0-on-Windows). After completing every step in above article ,When I run the command ```bundle install``` , I got the following error

    Fetching gem metadata from https://rubygems.org/
    Fetching version metadata from https://rubygems.org/
    Fetching dependency metadata from https://rubygems.org/
    Resolving dependencies...
    Using rake 10.5.0
    Using RedCloth 4.2.9
    Using addressable 2.4.0
    Using blankslate 2.1.2.4
    Using chunky_png 1.3.6
    Installing fast-stemmer 1.0.2 with native extensions

    Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

        C:/Ruby193/bin/ruby.exe extconf.rb
    Invalid argument - C:/Ruby193/bin/ruby.exe extconf.rb 2>&1

    Gem files will remain installed in C:/Ruby193/lib/ruby/gems/1.9.1/gems/fast-stem
    mer-1.0.2 for inspection.
    Results logged to C:/Ruby193/lib/ruby/gems/1.9.1/extensions/x86-mingw32/1.9.1/fa
    st-stemmer-1.0.2/gem_make.out
    Using coffee-script-source 1.10.0
    Using execjs 2.7.0
    Using colorator 0.1
    Using multi_json 1.12.1
    Using sass 3.4.22
    Using rb-fsevent 0.9.7
    Using ffi 1.9.14
    Using multipart-post 2.0.0
    Using tilt 2.0.5
    Using jekyll-paginate 1.1.0
    Using kramdown 1.12.0
    Using liquid 2.6.3
    Using mercenary 0.3.6
    Installing posix-spawn 0.3.11 with native extensions

    Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

        C:/Ruby193/bin/ruby.exe extconf.rb
    Invalid argument - C:/Ruby193/bin/ruby.exe extconf.rb 2>&1

    Gem files will remain installed in C:/Ruby193/lib/ruby/gems/1.9.1/gems/posix-spa
    wn-0.3.11 for inspection.
    Results logged to C:/Ruby193/lib/ruby/gems/1.9.1/extensions/x86-mingw32/1.9.1/po
    six-spawn-0.3.11/gem_make.out
    Installing yajl-ruby 1.2.1 with native extensions

    Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

        C:/Ruby193/bin/ruby.exe extconf.rb
    Invalid argument - C:/Ruby193/bin/ruby.exe extconf.rb 2>&1

    Gem files will remain installed in C:/Ruby193/lib/ruby/gems/1.9.1/gems/yajl-ruby
    -1.2.1 for inspection.
    Results logged to C:/Ruby193/lib/ruby/gems/1.9.1/extensions/x86-mingw32/1.9.1/ya
    jl-ruby-1.2.1/gem_make.out
    Installing redcarpet 3.3.4 with native extensions

    Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

        C:/Ruby193/bin/ruby.exe extconf.rb
    Invalid argument - C:/Ruby193/bin/ruby.exe extconf.rb 2>&1

    Gem files will remain installed in C:/Ruby193/lib/ruby/gems/1.9.1/gems/redcarpet
    -3.3.4 for inspection.
    Results logged to C:/Ruby193/lib/ruby/gems/1.9.1/extensions/x86-mingw32/1.9.1/re
    dcarpet-3.3.4/gem_make.out
    Using safe_yaml 1.0.4
    Using rack 1.6.4
    Installing rdiscount 2.2.0.1 with native extensions

    Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

        C:/Ruby193/bin/ruby.exe extconf.rb
    Invalid argument - C:/Ruby193/bin/ruby.exe extconf.rb 2>&1

    Gem files will remain installed in C:/Ruby193/lib/ruby/gems/1.9.1/gems/rdiscount
    -2.2.0.1 for inspection.
    Results logged to C:/Ruby193/lib/ruby/gems/1.9.1/extensions/x86-mingw32/1.9.1/rd
    iscount-2.2.0.1/gem_make.out
    Using stringex 1.4.0
    Using bundler 1.12.5
    Installing jekyll-sitemap 0.11.0

    Errno::EINVAL: Invalid argument - C:/Ruby193/lib/ruby/gems/1.9.1/gems/jekyll-sit
    emap-0.11.0/spec/fixtures/_posts/2016-04-01-i¶↓h
    Using parslet 1.5.0
    An error occurred while installing fast-stemmer (1.0.2), and Bundler cannot
    continue.
    Make sure that `gem install fast-stemmer -v '1.0.2'` succeeds before bundling.
If you are finding this error then try to run the following command ```SET COMSPEC``` and see the result . The output should be like 
    
    ComSpec=C:\Windows\system32\cmd.exe
If you find any other result other than above (In my case I got ```ComSpec=C:\Windows\system32\cmd.exe;C:\Ruby21-x64```) then change it to ```ComSpec=C:\Windows\system32\cmd.exe``` by changing the ```ComSpec``` variable .

How to change ComSpec in windows.
  
  1. Right click on Computer
  2. Goto Properties -> Advanced System Settings
  3. Click on Environment Variables
  4. Goto System Variables -> ComSpec
  5. Click on Edit and remove the Extra text(in my case it was ```C:\Ruby21-x64```) and don't forget to remove ";"
  6. After Edit it should be like ```ComSpec=C:\Windows\system32\cmd.exe```
  7. Click on OK
  

Now run the command ```bundle install``` .If you are getting the some error like

    'make' is not recognized as an internal or external command, operable program or batch file.

 It may be due to the  following reason.

  ```The Ruby Development Kit has a component called MinGW which is used to run Unix command on Windows and Ruby Development Kit not added to the system path variable```
  
So try the following solution to resolve the problem.
 
 1. Goto your devKit location and run the following command in terminal
 2. ```ruby dk.rb init```
 3. ```ruby dk.rb install```
 4. ```devkitvars.bat```  --> This command I had missed while installation

Now setup octopress and start your blog.
 
 Happy Coding. :)

Some reference link:

 https://github.com/imathis/octopress/wiki/Installation-Instructions-2.0-on-Windows
 https://github.com/oneclick/rubyinstaller/wiki/Troubleshooting
 http://stackoverflow.com/questions/27239491/cannot-install-gem-make-is-not-recognized-as-an-internal-or-external-command-o/33442847#33442847
  


  