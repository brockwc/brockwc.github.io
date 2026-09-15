---
layout: default
title: Posts
permalink: /categories/
---
<div class="space-y-12">
  <header>
    <h1 class="text-3xl font-bold tracking-tight text-zinc-900 sm:text-4xl dark:text-zinc-50">Posts</h1>
    <p class="mt-3 text-zinc-600 dark:text-zinc-400">Everything I've written here, grouped by topic.</p>
  </header>

  {% if site.posts.size > 0 %}
    {% assign cats = site.categories | sort %}
    {% for cat in cats %}
      {% assign name = cat[0] %}
      {% if name != 'jekyll' and name != 'update' %}
        <section id="{{ name | slugify }}">
          <h2 class="text-sm font-semibold uppercase tracking-wider text-zinc-600 dark:text-zinc-400">{{ name | capitalize }} <span class="font-normal text-zinc-500 dark:text-zinc-400">({{ cat[1].size }})</span></h2>
          <ul class="mt-2 divide-y divide-zinc-200 dark:divide-zinc-800">
            {% for post in cat[1] %}
              <li>
                <a href="{{ post.url | prepend: site.baseurl }}" class="group flex flex-col gap-0.5 py-4 sm:flex-row sm:items-baseline sm:justify-between sm:gap-6">
                  <span class="font-medium text-zinc-900 transition-colors group-hover:text-orange-700 dark:text-zinc-100 dark:group-hover:text-orange-400">{{ post.title }}</span>
                  <time datetime="{{ post.date | date_to_xmlschema }}" class="shrink-0 text-sm text-zinc-600 dark:text-zinc-400">{{ post.date | date: "%b %-d, %Y" }}</time>
                </a>
              </li>
            {% endfor %}
          </ul>
        </section>
      {% endif %}
    {% endfor %}
  {% else %}
    <p class="text-zinc-500 dark:text-zinc-400">Nothing here yet. First post coming soon.</p>
  {% endif %}
</div>
