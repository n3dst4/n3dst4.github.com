---
layout: post
title: "Idea: Lighthouse Comments"
tags:
---

Nearly all text editor and IDE syntax colouring themes render comments in a muted, unobtrusive style. Because if you've commented something out, it's not important, right? "Commented out" code is dead, pointless code. There's even a groundswell of folks who say [you shouldn't even commit commented-out code][pdccoc].

But "comment" a funny word for something unimportant. *Commentary* is usually interesting and important. We have commentary on sports, art, and current affairs to help us interpret what we're seeing. Why shouldn't code be the same? As much as you might want all code to be self-documenting, sometimes it just isn't. And even when it is, maybe there are side-effects or corner cases that might not be apparent to someone else. So you add a comment.

(As a side-note: if you ask someone why they don't comment their code, and they reply, "good code is self-documenting", you should answer: "sure, but I asked why *you* don't comment your code".)

Then this weird thing happens: your text editor will nearly always make that comment appear dull, greyed out, or hard to read. Look, here's some source code from React, in Atom, using Atom's default UI and syntax themes:

![Source code with grey comments barely visible on grey background][cbvoagb]

Wait... those notes should bemore visible than everything around them! Most text editor syntax thems do this to some extent. Comments are dark, washed out, muted, second-class citizens on the page of code.

**But comments are important, and should be visible. If the comments in your code are noise, then fix that problem. If you have commented-out code in your codebase, then it should be deleted (to make sure it never gets accidentally un-commented) or it should be visible.**

Here's what I've done to my Atom (same bit of source as above):

![Source code comments glowing brightly][lighthouse]

I'm calling this "lighthouse comments". Good comments should act like lighthouses, shining to warn you about rocky corner cases and stormy side-effects.

Here's the LESS I added to my user stylesheet to get the effect you see above. The glow may be hard to reproduce in other text editors but at least you should be able to pick a bright, visible colour.

```css
////////////////////////////////////////////////////////////////////////////////
// re-color comments
atom-text-editor::shadow {
  @comment-color: #acf;
  .comment {
    color: @comment-color;
    &.end, &.begin {
      color: @comment-color;
    }
  }
  .punctuation.definition.comment {
    color: @comment-color;
  }
}

////////////////////////////////////////////////////////////////////////////////
// comments glow
atom-text-editor::shadow {
  .comment {
    @offset: 0em;
    @radius: .6em;
    text-shadow: @offset @offset @radius;
  }
}
```



[pdccoc]: https://medium.com/@kentcdodds/please-don-t-commit-commented-out-code-53d0b5b26d5f#.u8vghjurj
[cbvoagb]: https://dl.dropboxusercontent.com/u/555629/codepen-blog/2015-12-02%2014_59_18-untitled%20-%20C__git_modeng-wiki%20-%20Atom.png
[lighthouse]: https://dl.dropboxusercontent.com/u/555629/codepen-blog/2015-12-02%2015_03_26-Lighthouse%20comments-%20CodePen.png
