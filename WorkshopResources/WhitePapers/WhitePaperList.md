---
# Some frontmatter is required
permalink: /WorkshopResources/WhitePapers/
---
# 2020 Collegeville Workshop on Scientific Software Whitepapers

Add the PDF or Markdown of your white paper to the this folder and
name it like so...

  ```
  CamelCaseShortTitle-AuthorLastName-AuthorOtherName1_AuthorOtherName2.{md,pdf}
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
        {%- if str != substrs[1] -%}
           ,&nbsp;
        {%- endif -%}
        {% assign rstr = str | replace: "_", " " %}
        {{-rstr-}}
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

### Notes to Mike

1. Changes to `_config.yml`

   ```
   defaults:
     - scope:
         path: "WorkshopResources/WhitePapers"
       values:
         white_paper: true
   ```

   This has the effect of adding the member `white_paper` to all files
   at the specified path with value `true`. We us that here to filter
   `site.static_files` to restrict to those in this folder.

1. Supporting Markdown and PDF introduces an issue

   If we allowed only markdown files here, we can capture all the
   information about a paper (e.g. author, title, category tags if
   we want, etc.) as YML frontmatter. However, because we also want
   to allow `.pdf` files here, which are essentially binary, we
   have no place to store YML front matter. We could require that
   each `.pdf` file also have a `.md` friend which contains nothing
   but frontmatter and references the `.pdf` file but that would
   mean authors who contribute `.pdf` files then need to also create
   this `.md` friend. Its actually easy and would honestly be a bit
   better design but since the current site isn't designed this way
   I opted not to go that route. This means the only remaining way
   to encode information like author and article title is in the
   actual file name string itself. And, that is what we do.

1. File name convention

   This allows us to use the filename to store the author's name and
   article title.

1. Liquid code here

   The liquid code in this file loops over `site.static_files` filtering
   for attribute `white_paper`. Each file name is broken into the
   author info and the article title. An HTML table is constructed with
   two columns for author and article title.   

1. The `Gemfile` at the top dir was added so that `bundle exec jekyll ...`
   commands will produce *something* locally. These won't produce properly
   themed site but are sufficient to do most testing locally before committing.

#### [Back to Main Page](../../index.md)
