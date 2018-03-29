---
layout: pages
isCategoryLayout: true
---

<div class="category-articles">
{% for post in site.categories[page.category] %}
    <article class="post-excerpt">
        <header class="post-excerpt-heading">
            <h2>
                <a href="{{ post.url | absolute_url }}">
                    {{ post.title }}
                </a>
            </h2>
            <div class="post-excerpt-metainfo">
                <span class="date-posted">{{ post.date | date_to_string }}
                </span>
                {% for tag in post.tags %}
                    {% capture tag_name %}{{ tag }}{% endcapture %}
                    {% if forloop.last == false %}
                        <span class="post-tag">
                            <a href="/tag/{{ tag_name }}">{{ tag_name }}</a>
                        </span>,
                    {% else %}
                        <span class="post-tag">
                            <a href="/tag/{{ tag_name }}">{{ tag_name }}</a>
                        </span>
                    {% endif %}
                  {% endfor %}
            </div>
        </header>
        <div class="post-excerpt-content">
            {{ post.content | markdownify | strip_html | truncatewords: 20 }}
        </div>
    </article>
    
{% endfor %}
</div>

{% include subscribe.html %}