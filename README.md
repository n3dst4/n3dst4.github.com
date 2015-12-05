
This is a Jekyll website. Installing Jekyll in Windows requires some hoop-jumping, documented at [Run Jekyll On Windows][rjow]. We're also using foundation installed via npm, so you'll want to run `npm install` from the root folder too.

The whole process is summarised below:

1. Install [Ruby for Windows][ruby]
2. Download the [Ruby Dev Kit][rdk] (same page as before, slightly further down)
  1. Extract the RDK into C:\\RubyDevKit
  2. Open a command prompt in C:\\RubyDevKit
  3. `ruby dk.rb init`
  4. Open `config.yml` and ensure it's found the path to your Ruby installation
  5. `ruby dk.rb install`
3. `gem install jekyll`
4. `gem install rouge`
5. `gem install sass`
6. `npm install`
7. `jekyll build`
  or
  `jekyll serve`
```

Build stylesheets with:

```
sass
```

https://help.github.com/articles/using-jekyll-with-pages

http://jekyllrb.com/docs/quickstart/

[ruby]: http://rubyinstaller.org/downloads/
[rdk]: http://rubyinstaller.org/downloads/
[rjow]: http://jekyll-windows.juthilo.com/
