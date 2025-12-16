---
layout: page
title: About
description: About 
keywords: Elisha Teng, elishateng
comments: false
menu: 关于
permalink: /about/
---

Hello! I am Elisha. Nice to meet you~

Hyvää päivää! Minun nimeni on Elisa. Hauska tutustua~

Staff Engineer with over 11 years of experience building UI frameworks and turning design documents into runnable code.

I work mainly with C/C++, C#, TypeScript, and Python. 

I know Linux well and have solid knowledge of data structures, algorithms, and common design patterns.

My experience covers both low-level work (C++ Dali library) and higher-level UI frameworks (Tizen.NUI, Xamarin, Web).

I am comfortable with Agile, Git, and modern AI coding tools (Cursor/Cline).

I also have a dual degree in Software Engineer and Finance.

## Contact

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}



