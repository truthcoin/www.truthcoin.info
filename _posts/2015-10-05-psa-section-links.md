---
title: PSA - Linking to a Blog Section
comments: false
---


### Problem

One complaint I get is: "Paul, your blog posts are amazing. You. are, amazing. However, your posts are too long. I feel uncomfortable linking them to my friends because I just want to quote, like, a single section but I don't want to, like, assign them a whole summer reading proj-"

Got it.

So I took 20 minutes and threw this together.

### Solution

Here's what you do.

1. Start at your target Long Blog post.<br>
![LongBlog](/images/long-blog.png) <br><br><br>
2. Find the section you want to link to.<br>
![BlogSection](/images/blog-section.png) <br><br><br>
3. Use right-click (or whatever) to grab **the source**.<br>
![BlogSource](/images/blog-source.png) <br><br><br>
4. Use control+f (or whatever) to find the right part of the source.<br>
![BlogPart](/images/source-part.png) <br><br><br>
5. Find the closest header. They start with an "h".<br>
![SourceHeader](/images/source-header.png) <br><br><br>
6. Grab the header's "id".<br>
![HeaderId](/images/header-id.png) <br><br><br>
7. Paste it into the link with a "#".<br>
![HeaderLink](/images/header-link.png) <br><br><br>
8. The link will now take you to the desired section.<br>
![LinkResult](/images/link-result.png) <br><br><br>


The "header id" is annoying to get, but you can usually just *guess* what it is (they are generated automatically). Look for something big and bold (the header), and modify it a little: [1] remove everything that isn't a letter, [2] make all the letters lowercase, and [3] replace the spaces with dashes.

Happy reading.