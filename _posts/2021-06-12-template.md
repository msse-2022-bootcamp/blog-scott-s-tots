---
layout: post
title: "2021 MSSE Bootcamp Instructions"
author: Jessica Nash
---

This is a template to create a blog post.

## Introduction

We ask that a member of your team write a summary for the class and group work each day. You should have a rotation schedule for this. The length and depth of the blog post is up to you, but you should aim to write at least 250 words each day.

On the first day, everyone should make a post and make a pull request. You should use your post to introduce yourself to your team. Make sure you include your name as author at the top of the page!

To create a post, you should clone this repository to your computer. Create a branch as discussed in class 

```
$ git switch -c YOUR_NAME
```

Next, create a post about you. Create a file in the `_posts` directory with the format

```
YEAR-MONTH-DATE-YOUR-NAME.md
```

Add the following at the top of the page, but change the title and author

```
---
layout: post
title: "YOUR TITLE"
author: YOUR NAME
---
```

Now, you are ready to type your blog entry! You can just use text for this (you create headers by starting a line with a hashtag `#`).

When you are done, commit your page and push to the repository. Open a pull request and have a teammate review it to have it incorporated into the blog!

## Blog Features

The blog posts support many features, should you choose to use them.

You can include equations using Latex Syntax:

$$ \vec{F} = - \nabla U $$

$$ \vec{F} = m \cdot \vec{a} = m \cdot \frac{d\vec{v}}{dt} = m \cdot \frac{d^{2}\vec{r}}{dt^{2}}$$

The Latex for this equation is:

```
$$ \vec{F} = - \nabla U $$

$$ \vec{F} = m \cdot \vec{a} = m \cdot \frac{d\vec{v}}{dt} = m \cdot \frac{d^{2}\vec{r}}{dt^{2}}$$
```

Your instructors have the Latex for most of the equations we will be using, so if you would like to include them in your blog, just ask!

You can include images:

<center>

<img src = '{{ "/images/msse-logo-bg.svg" | relative_url }}'>  

***Figure 1**: The logo of the UC Berkeley MSSE program.*
</center>

and you can include code:

{% highlight python %}
def hello_world():
    print("hello world")
{% endhighlight %}

{% highlight C++ %}
#include <iostream>

int main() {
    std::cout << "Hello World!";
    return 0;
}
{% endhighlight %}

On the first day, everyone should make a post and make a pull request. You should use your post to introduce yourself to your team. Make sure you include your name as author at the top of the page!

To create a post, you should clone this repository to your computer. Create a branch as discussed in class 

```
$ git switch -c YOUR_NAME
```

Next, create a post about you. Create a file in the `_posts` directory with the format

```
YEAR-MONTH-DATE-YOUR-NAME.md
```

Add the following at the top of the page, but change the title and author

```
---
layout: post
title: "YOUR TITLE"
author: YOUR NAME
---
```

Now, you are ready to type your blog entry! You can just use text for this (you create headers by starting a line with a hashtag `#`).

When you are done, commit your page and push to the repository. Open a pull request and have a teammate review it to have it incorporated into the blog!