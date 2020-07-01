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
{% for wp in white_papers %}
  {% assign substrs = wp.basename | split: "-" %}
  <tr>
    <td>
    {% for str in substrs offset:1 %}
        {% if str != substrs[1] %}
           ,&nbsp;
        {% endif %}
        {{str}}
    {% endfor %}
    </td>
    {% assign title = "" %}
    {% assign nchars = wp.basename | size %}
    {% for i in (0..nchars) %}
      {% assign char = wp.basename | slice: i %}
      {% if char == "-" %}
        {% break %}
      {% endif %}
      {% assign upchar = char | upcase %}
      {% if char == upchar %}
         {% assign title = title | append: " " %}
      {% endif %}
      {% assign title = title | append: char %}
    {% endfor %}
    <td><a href="{{wp.name}}">{{title}}</a></td>
  </tr>
{% endfor %}
</table>
