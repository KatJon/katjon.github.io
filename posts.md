---
layout: home
title: All posts
---

{%- if site.posts.size > 0 -%}
<section class="posts">
    <h2 class="post-list-heading">Posts</h2>
    <ul class="post-list">
        {%- for post in site.posts -%}
            {%- unless post.categories contains "news" -%}
                {% include short_post.html %}
            {%- endunless -%}
        {%- endfor -%}
    </ul>
</section>
{%- endif -%}
