---
layout: home
---

BallCuber is a patented and fast 4x4x4 Rubik's cube solving machine.

<br>
<ul>

{%- assign default_paths = site.pages | map: "path" -%}
{%- assign page_paths = site.header_pages | default: default_paths -%}

{%- for path in page_paths -%}
{%- assign my_page = site.pages | where: "path", path | first -%}
{%- if my_page.title -%}

<li><a href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a></li>

{%- endif -%}
{%- endfor -%}
</ul>