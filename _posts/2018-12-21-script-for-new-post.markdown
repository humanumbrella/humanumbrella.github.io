---
layout: post
title: Script for New Post in Jekyll
description: Found and then edited a script to set up a new post builder
categories: articles
date: 2018-12-21 09:25:22 -08:00
tags: [automation, bash script]
keywords: [new-post]
image: bg.png
---
OK cool, that seems to work now. Time to write about it and try to better understand it.

So, I was using the basic Terminal in Ubuntu 18.10 as I haven't installed anything extra or fancier. I wanted to add a function to my ~/.bashrc so that I can call it to make a new post instead of copy-pasting the post markdown and changing all of the variables each time, especially the datetime.

I searched for a bit and then found this page:  [How to Implement a Bash Script to Create New Posts in Jekyll](http://joshuasoileau.com/articles/2016/06/08/how-to-implement-a-bash-script-to-create-new-posts-in-jekyll.html)

This has a lot of good info here, except I wanted to tweak it a bit.

---
## Let's work through this

The original script was from [@pibby](https://gist.github.com/pibby/6911493) -- so I set it up in my .bashrc -- this is a hidden file in your home directory.

```shell
$ vim ~/.bashrc
```

If you're not down with vim and can't figure out how to exit, try:

1. hit ESC
2. type :q (you might need :q! if you've made changes and want to discard)
3. hit ENTER

---

> paste in the code (either hers or mine to start and then edit the filepath so it works for you.)

```bash
function new-post() {

    #!/bin/bash
    # Katie Harron - @pibby
    #modified by Justin Moore - @11jmoore

    echo "Post Title: "
    read title
    echo "Post Description: "
    read desc
    echo "Post Tags: "
    read tags

    ptitle=${title// /-}
    plc=`echo "$ptitle" | tr '[:upper:]' '[:lower:]'`
    pdate=`date +%F\ %T\ %z`
    fnamedate=`date +%F`
    filename=~/site/_posts/$fnamedate-$plc.markdown
    touch $filename

    echo "---
layout: post
title: $title
description: $desc
categories: articles
date: $pdate
tags: [$tags]
---
Sample text" > $filename

atom $filename
}
```

> now reload your shell (can use source or .)

```shell
$ source ~/.bashrc
```

[information about the difference](https://superuser.com/a/618442)

---
> and give it a try!

```shell
$ new-post
```

Cheers
--Justin
