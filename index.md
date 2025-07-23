---
layout: home
---

./README
--------

Hi, I'm Alejandro de Cora. I didn't expect to be writing on [this repo][1] again, but here we are!  This started as a playful experiment in prompt injecting my resume for a job application at Tinybird.

Now, I'm going to document my interview preparation journey here.  Think of it as a public notebook for tracking my progress and, hopefully, sharing some useful insights along the way.

The face of this repo is cortesy of [jekyll][2], the design is borrowed from [sighingnow][3] which itself is a hevily modified version of [minima][4].

./My Journey
----------

I'll be updating this list with posts detailing the steps I'm taking to prepare.

<ul>
  {% for post in site.posts limit:6 %}
    <li class="alink">
      <a href="{{ post.url }}" class="red-link">
        {{ post.date | date: "%Y-%m-%d" }}&emsp;{{ post.title }}
      </a>
    </li>
  {%- endfor -%}
  <li class="alink"><a href="./blog/" class="red-link">&hellip;&hellip;</a></li>
</ul>

[1]: https://github.com/adecora/tinybird-adventure
[2]: https://jekyllrb.com/
[3]: https://github.com/sighingnow/sighingnow.github.io
[4]: https://jekyll.github.io/minima/