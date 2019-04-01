---
layout: home
title: Category theory
---

{%- if site.posts.size > 0 -%}
Notes from the meetings of student research group, mostly focusing on category theory, but also planning to mention some type theory and non-classical logic.

<section class="posts">
    <h2 class="post-list-heading">Posts</h2>
    <ul class="post-list">
        {%- for post in site.posts -%}
            {%- if post.categories contains "category-theory" -%}
                {% include short_post.html %}
            {%- endif -%}
        {%- endfor -%}
    </ul>
</section>
{%- endif -%}
