---
title:  Start Python
date:   2016-1-2 10:00:00
description: Some disturbing things
categories: Python

---

When I was trying to install Scrapy I got this error:

>
Exception:
Traceback (most recent call last):
  File "/Library/Python/2.7/site-packages/pip-7.1.2-py2.7.egg/pip/basecommand.py", line 211, in main
    status = self.run(options, args)
  File "/Library/Python/2.7/site-packages/pip-7.1.2-py2.7.egg/pip/commands/install.py", line 311, in run
    root=options.root_path,
  File "/Library/Python/2.7/site-packages/pip-7.1.2-py2.7.egg/pip/req/req_set.py", line 640, in install
    requirement.uninstall(auto_confirm=True)
  File "/Library/Python/2.7/site-packages/pip-7.1.2-py2.7.egg/pip/req/req_install.py", line 716, in uninstall
    paths_to_remove.remove(auto_confirm)
  File "/Library/Python/2.7/site-packages/pip-7.1.2-py2.7.egg/pip/req/req_uninstall.py", line 125, in remove
    renames(path, new_path)
  File "/Library/Python/2.7/site-packages/pip-7.1.2-py2.7.egg/pip/utils/__init__.py", line 315, in renames
    shutil.move(old, new)
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/shutil.py", line 302, in move
    copy2(src, real_dst)
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/shutil.py", line 131, in copy2
    copystat(src, dst)
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/shutil.py", line 103, in copystat
    os.chflags(dst, st.st_flags)
OSError: [Errno 1] Operation not permitted: '/tmp/pip-WDIurU-uninstall/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/six-1.4.1-py2.7.egg-info'


It seems like it encountered a problem caused by permition. Then I found [this guy](http://stackoverflow.com/questions/31900008/oserror-errno-1-operation-not-permitted-when-installing-scrapy-in-osx-10-11) got this same proble where the most rated answer provided a seemingly not apporiate solution which was disagreed by the comment below. Then I turned to [this](http://stackoverflow.com/questions/32898583/unable-to-install-nltk-on-mac-os-el-capitan/33024464#33024464) and by using

    brew reinstall python

then install Scrapy

    sudo pip install scrapy
    
I got my problem solved. 

In fact when it comes to crawling a website full of ajax, in my case, Agoda.com, I found a better thing than Scrapy, which is, by using PhantomJS via Selenium, refering to [this](http://stackoverflow.com/questions/13287490/is-there-a-way-to-use-phantomjs-in-python).
