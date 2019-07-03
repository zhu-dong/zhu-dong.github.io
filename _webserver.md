# Do I have a web server running?

___

having a web server turned on doesn't necessarily mean you are serving pages on the world wide web.  its what allows you to load your own static files (`.html`, `.js` etc.) in a browser via `http://`.

if you're not sure whether or not you have a web server running, no problem!  its easy to confirm.

### what happens when you visit [http://localhost/](http://localhost/)?

if you're looking at a webpage, **great**!  
you're done.

# What if i don't?

## Windows

the most popular web server software for microsoft computers is **IIS**.  if its not already running, you can follow the instructions below to get things set up.

https://msdn.microsoft.com/en-us/library/ms181052(v=vs.80).aspx

![iis screenshot](https://www.digicert.com/images/support-images/iis7/iis7-install-4.gif "iis")

afterward, save a `.html` file in `C:/inetpub/wwwroot` and try to access it via http://localhost/[myfile].html. if the page is served up, you're ready to roll.
## Mac

**Apache** comes preinstalled on Apple computers.  If its not running, you can follow the instructions below to get it turned on.

http://osxdaily.com/2012/09/02/start-apache-web-server-mac-os-x/

afterward, save a `.html` file in `~/Users/[yourlogin]/Sites/` and try to access it via http://localhost/~[yourlogin]/myfile.html.  if you can view the content, all is well.
___

:musical_note: interlude :musical_note:
___

# What if I'd rather use something else?

you don't **need** a *why*, but here are a couple:
* you don't have admin priviledges on the computer
* you think Apache `.conf` files are scary, and editing text in VIM is even more frightening
* you want something **lightweight**

### SimpleHTTPServer (a Pythonic approach)

Python comes preinstalled on Macs (and is installed on Windows with ArcGIS Software) so it's [SimpleHTTPServer](https://docs.python.org/2/library/simplehttpserver.html) module is an **excellent** choice.

1. navigate into the folder where  you plan on saving your `.html` files (using terminal/cmd) and execute the following command:
    
    ```python
    python -m SimpleHTTPServer 1337
    ```
    if you're using Python 3.x or higher, you'd use
    ```python
    python -m http.server 1337
    ```
    
2. now you should be able to access your own files via http://localhost:1337/myfile.html in Chrome, Firefox or any other web browser.

```html
<html>
  <body>
    <h1>i'm web serving!</h1>
  </body>
</html>
```

![hello world](https://gist.githubusercontent.com/jgravois/5e73b56fa7756fd00b89/raw/053ea5a0b141e7b53fa14ebce8f6f2d14292ab2a/hello.png "hello world")

### http-server (for Node)

[Node.js](https://nodejs.org) gets more popular by the day, so if you already have it installed (or don't mind taking two minutes to do it now) the npm module [`http-server`](https://www.npmjs.com/package/http-server) is a **really** good choice too.

![using http-server](https://gist.githubusercontent.com/jgravois/5e73b56fa7756fd00b89/raw/1ec60e0e598305b2b5dfe6071c1281431041fb17/node.png "http-server")

1. if you haven't already installed Node.js, visit the site below and lay it down

  https://nodejs.org/en/download/

2. next, open terminal or cmd and install the `http-server` module globally on your machine
  ```
  npm install http-server -g
  ```
3. run it using CLI (specifying the folder you'd like to serve files from)

  ```
  http-server ./[yourfolder] -p 1337
  ```
4. now you should be able to access your files (via something like http://localhost:1337/myfile.html) in a web browser.

# thats it!