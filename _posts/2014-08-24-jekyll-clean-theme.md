---
layout: post
title: "222222Jekyll Dark Clean Theme"
date: 2014-08-22 16:25:06 -0700
comments: true
categories:
- code
tags: 
- jekyll
- python
- tornado
description: Here I want to introduce you the dark theme for Jekyll. It was forked from Scotte's jekyll-clean theme and customized.
comments: true
toc: true
---

## Introduction

```cpp
int main()
{
  return 0;
}
```

```html
<html>
   <head>
      <title>{{ title }}</title>
   </head>
   <body>
     <form action="{{ request.path }}" method="post">
       <div>{{ _("你的IP") }} <input type="text" name="username"/></div>
       <!--<div>{{ _("Password") }} <input type="password" name="password"/></div> -->
       <div><input type="submit" value="{{ _("输入") }}"/></div>
       {% module xsrf_form_html() %}
     </form>
   </body>
 </html>
```

```python
import tornado.ioloop
import tornado.web

class MainHandler(tornado.web.RequestHandler):
    def get(self):
        #self.write("Hello, world")
        items = ["Item 1", "Item 2", "Item 3"]
        self.render("temp.html", title="My title", items=items)

# LoginHandler
class LoginHandler(tornado.web.RequestHandler):
    def get(self):
        # template from login.html
        self.render("login.html", title="login")
    def post(self):
        usr=self.get_argument("username", "") 
        #pwd=self.get_argument("password", "") 
        self.write(usr)
        #self.write(pwd)

application = tornado.web.Application([
    (r"/", MainHandler),

    # login时通过LoginHandler处理
    (r"/login", LoginHandler),
])

if __name__ == "__main__":
    application.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```
