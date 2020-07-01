---
# Some frontmatter is required
permalink: /WorkshopResources/WhitePapers/
---
# Collegeville Workshop on Scientific Software Whitepapers

{% comment %}
  White paper file names should be of the form...
    CamelCaseTitle-AuthorLastName-AuthorOtherName(s).{md,pdf}
{% endcomment %}

{% assign white_papers = site.static_files | where: "white_paper", true %}

<table>
  <tr>
    <th>Author</th>
    <th>Title</th>
  </tr>
{%- for wp in white_papers -%}
  {%- assign substrs = wp.basename | split: "-" -%}
  <tr>
    <td>{{substrs[1]}}, {{substrs[2]}}</td>
    <td><a href="{{wp.name}}">{{substrs[0]}}</a></td>
  </tr>
{%- endfor -%}
</table>
