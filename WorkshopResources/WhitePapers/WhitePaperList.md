---
# Some frontmatter is required
permalink: /WorkshopResources/WhitePapers/
---
# 2020 Collegeville Workshop on Scientific Software Whitepapers

Add the PDF or Markdown of your white paper to the this folder and
name it like so...

  ```
  CamelCaseShortTitle-AuthorLastName-AuthorOtherNames.{md,pdf}
  ```

For example...

  ```
  MyCoolSoftwareProductivityArticle-Miller-Mark_C.md
  ```

[**All White Papers: WhitePapersBundle.zip**](../WhitePapersBundle.zip)

{% comment %}
  White paper file names should be of the form...
    CamelCaseTitle-AuthorLastName-AuthorOtherName(s).{md,pdf}
{% endcomment %}

{% assign white_papers = site.static_files | where: "white_paper", true %}

<table>
  <caption>Papers currently available here</caption>
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
        {% assign rstr = str | replace: "_", " " %}
        {{rstr}}
    {% endfor %}
    </td>
    {% assign title = "" %}
    {% assign nchars = wp.basename | size %}
    {% for i in (0..nchars) %}
      {% assign char = wp.basename | slice: i %}
      {% assign inx = i | plus: 1 %}
      {% assign nxchar = wp.basename | slice: inx %}
      {% if char == "-" %}
        {% break %}
      {% endif %}
      {% assign upchar = char | upcase %}
      {% assign nxupchar = nxchar | upcase %}
      {% if char == upchar %}
        {% if nxchar != nxupchar %}
          {% assign title = title | append: " " %}
        {% endif %}
      {% endif %}
      {% assign title = title | append: char %}
    {% endfor %}
    {% if wp.extname == ".md" %}
        <td><a href="{{wp.basename}}.html">{{title}}</a></td>
    {% else %}
        <td><a href="{{wp.name}}">{{title}}</a></td>
    {% endif %}
  </tr>
{% endfor %}
</table>

#### [Back to Main Page](../../index.md)
