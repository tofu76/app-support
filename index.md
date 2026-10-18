---
title: アプリの一覧
---

# {{ site.title }}

Toshihiro Funamoto が個人で開発しているアプリの、サポート・プライバシーポリシー・お問い合わせの窓口です。

<ul class="apps">
{%- for app in site.data.apps %}
<li>
<h2><a href="{{ '/' | append: app.id | append: '/' | relative_url }}">{{ app.name }}</a></h2>
<p>{{ app.summary }}（{{ app.platforms }}）</p>
<p>{% for p in app.pages %}<a href="{{ '/' | append: app.id | append: '/' | append: p.path | relative_url }}">{{ p.title }}</a>{% unless forloop.last %}　{% endunless %}{% endfor %}</p>
</li>
{%- endfor %}
</ul>
