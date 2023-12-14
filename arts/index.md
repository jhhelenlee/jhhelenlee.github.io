---
layout: single
title: Arts
page_categories: ["concert", "museum"]
---

This is some sample text.

This is some more sample text.

This is a long paragraph. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Elementum nibh tellus molestie nunc non. Nunc sed id semper risus. Nunc scelerisque viverra mauris in aliquam. Nam at lectus urna duis convallis convallis tellus. Volutpat est velit egestas dui. Amet venenatis urna cursus eget nunc scelerisque viverra mauris. Ut tristique et egestas quis ipsum. Tristique senectus et netus et malesuada fames ac turpis. In tellus integer feugiat scelerisque. Pellentesque habitant morbi tristique senectus et netus et malesuada fames.

---
### Concerts

This lists my concert outings.

{% assign tag1 = page.page_categories[0] %}
{% assign concert_posts = site.posts | where_exp: "post", "post.categories contains tag1" %}
{% for post in concert_posts %}
    {% include archive-single.html type=page.entries_layout %}
{% endfor %}

### Museums

This lists my museum visits.

{% assign tag2 = page.page_categories[1] %}
{% assign museum_posts = site.posts | where_exp: "post", "post.categories contains tag2" %}
{% for post in museum_posts %}
    {% include archive-single.html type=page.entries_layout %}
{% endfor %}

### Other

This lists other artistic adventures.

{% for post in site.posts %}
    {% assign tagListLength = post.categories | size %}
    {% assign additionalTagsLength = page.page_categories | size %}
    {% assign totalLength = tagListLength | plus: additionalTagsLength %}

    {% assign combinedTags = post.categories | concat: page.page_categories | uniq %}
    {% assign unionLength = combinedTags | size %}

    {% if unionLength == totalLength and post.categories contains 'arts' %}
        {% include archive-single.html type=page.entries_layout %}
    {% endif %}

{% endfor %}

