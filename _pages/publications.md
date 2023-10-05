---
layout: page
permalink: /publications/
title: Publications
description: By categories (preprints; journals and conferences; and thesis and reports) in reversed chronological order. I use [J] and [C] in front of the identification tab to distinguish between conference and journal papers.
sections:
  - bibquery: "@preprint"
    text: "preprint/submission"
  - bibquery: "@article"
    text: "Journal articles"
  - bibquery: "@inproceedings"
    text: "Conference and workshop papers"
  - bibquery: "@misc|@phdthesis|@mastersthesis"
    text: "Thesis"
years: [2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2014, 2013, 2012, 2011]
social: true
nav: true
nav_order: 1
---
Interestingly, [Google Scholar](https://scholar.google.com/citations?hl=en&user=GH4f3-sAAAAJ&view_op=list_works&sortby=pubdate) attaches some whole numbers (yes, zero is included!) to my papers.  

<!-- _pages/publications.md -->
<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <p class="bibtitle">{{section.text}}</p>
  {%- for y in page.years %}

    {%- comment -%}  Count bibliography in actual section and year {%- endcomment -%}
    {%- capture citecount -%}
    {%- bibliography_count -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] -%}
    {%- endcapture -%}

    {%- comment -%} If exist bibliography in actual section and year, print {%- endcomment -%}
    {%- if citecount !="0" %}

      <h2 class="year">{{y}}</h2>
      {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] %}

    {%- endif -%}

  {%- endfor %}

{%- endfor %}

</div>
