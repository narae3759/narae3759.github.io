---
layout: archive
title: "CodingTest"
permalink: /codingtest/
author_profiles: true
---
<!-- 
<div>
  <div>※ Coding Test 주의사항<div>
  <ul>
    <li>시간 복잡도, 메모리 등 조건들을 가장 먼저 파악하자.(제한시간이 짧다면 문제의 유형과 관련한 함수를 먼저 떠올려라.)</li>
    <li><code>sys.stdin.readline</code>을 사용할 때에는 공백을 주의하라. (<code>strip()</code> 사용하기)</li>
    <li>출력 형식(list인지 string인지)을 잘 지키자.</li>
  </ul>
</div> -->


{% assign posts = site.categories.codingtest %}
{% for post in posts %} 
  {% include archive-single-custom.html type=page.entries_layout %} 
{% endfor %}
<a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>