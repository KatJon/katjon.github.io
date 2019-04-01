---
layout: home
title: All posts
---

{%- if site.posts.size > 0 -%}
<section class="posts">
    <h2 class="post-list-heading">Posts</h2>
    <ul class="post-list">
        {%- for post in site.posts -%}
            {% include short_post.html %}
        {%- endfor -%}
    </ul>
</section>
{%- endif -%}
