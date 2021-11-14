---
layout: archive
title: "Python Note"
permalink: /PythonNote/
author_profiles: true
---

{% assign posts = site.categories.PythonNote %}
{% for post in posts %} 
  {% include archive-single.html type=page.entries_layout %} 
{% endfor %}
<a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>