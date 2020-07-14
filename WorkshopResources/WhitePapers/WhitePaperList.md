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
   each `.pdf` file also have a `.md` companion file which contains nothing
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

1. [Anzt, Hartwig and Cojean, Terry: Prioritizing Platform Portability for Scientific Libraries](anzt-cojean-software-portability.pdf)
1. [Bartlett, Roscoe: Restoring productivity through the advanced usage of Git](bartlett-restoring-productivity-git.pdf)
1. [Bartlett, Roscoe, Frye, Joseph, Harvey, Evan: Improved productivity through standardized configurations and testing of Trilinos on advanced platforms](bartlett-frye-harvey-atdm-trilinos-builds.pdf)
1. [Carver, Jeffrey and Eisty, Nasir: Peer Code Review for Scientific Software](carver-eisty-peer-code-review.pdf)
1. [Chandrasekaran, Sunita: Scientific Software Productivity 1. Case studies, Challenges, Opportunities and Potential Solutions](chandrasekaran-studies-challenges-opps-solns.pdf)
1. [Du, C. Fan and Howison, James: An Ecosystem Perspective of Scientific Software Developer Productivity](du-howison-ecosystem-perspective-productivity.pdf)
1. [Dubey, Anshu: When Not to use Agile in Scientific Software Development](dubey-when-not-agile.pdf)
1. [Dyadechko, Vadim: The Art of Serving HPC Products to Business while they are still hot](dyadechko-serving-hpc-products-to-business.pdf)
1. [Eisty, Nasir and Carver, Jeffrey: Testing Scientific Software](eisty-carver-testing-scientific-software.pdf)
1. [Ellingwood, Nathan and Rajamanickam, Sivasankaran: Practices and Challenges of Software Development for a Performance Portable Ecosystem](ellingwood-nathan-software-dev-perf-portable-ecosystem.pdf)
1. [Finkel: The Many Faces of the Productivity Challenge in Scientific Software](finkel-many-faces-of-productivity-challenges.pdf)
1. [Gamblin, Todd: Software Integration Challenges](gamblin-collegeville-2020-integration.pdf)
1. [Gates J., Frye J., Perschbacher B., Vigil D.: Git Productive!](gates-git-productive.pdf)
1. [Gates J., Braun J., Collins D.: One Script to Rule Them All:  Unifying Build Processes Across Platforms](gates-unifying-build-processes.pdf)
1. [Gesing, Sandra: Increasing Developer Productivity by Assigning Well-Defined Roles in Teams](gesing-team-organization.pdf)
1. [Gunter, Dan, and Beattie, Keith: Useful Practices for Software Engineering on Medium-sized Distributed Scientific Projects](gunter-beattie-useful-practices.pdf)
1. [Heroux, M., Willenbring, J., Shende, S., Coti, C., Spear, W., Peyralans, L., Skutnik, J. and Keever, E.  : E4S: Extreme-scale Scientific Software Stack](heroux-willenbring-shende-coti-spear-et-al-E4S.pdf)
1. [Huebl, Axel: Working with Multiple Package Managers](huebl-working-with-multiple-pkg-mgrs.pdf)
1. [Katz, Daniel S., Chard, K., Badia, Rosa M., and Ejarque, Jorge: A common workflow registry of compute endpoints and applications](katz_registry.pdf)
1. [Lehr, JP, Maric, T., Bothe, D. and Bischof, C.: Increasing the quality of (academic) scientific software](lehr-maric-bothe-bischof-increasing-the-quality-of-academic-scientific-software.pdf)
1. [Levine, Aaron and Willenbring, James: Navigating the Rapids: Creating a Continuous Integration System for GitHub and Jenkins](levine-willenbring-ci-systems-github-jenkins.pdf)
1. [Luszczek, Piotr: Productivity, Portability, and Performance: Pick any two in Uncertain Hardware Landscape?](luszczek-p3-pick-two.pdf)
1. [Miller, Mark: SRE+UXDD to Improve Productivity of Customer Support Processes](miller-software-reliability-engineering.md)
1. [Milewicz, Reed: Towards Evidence-Based Practice in Scientific Software Development](milewicz-evidence-based-practice.pdf)
1. [Mundt, M., Levine, A. and Siirola, J.: Overcoming Productivity Plateaus: A Story of Automation Tools and Developer Productivity](mundt-levine-siirola-overcoming-productivity-plateaus.pdf)
1. [Raybourn, Elaine: Why We Need Strategies for Working Remotely](raybourn-why-we-need-strategies-working-remotely.pdf)
1. [Smith, Spencer and Carette, Jacques: Long-term Productivity for Long-term Impact](smith-carette-redefining-productivity.pdf)
1. [Sochat, Vanessa: Developer productivity means developer happiness](sochat-developer-happiness.pdf)
1. [Sochat, Vanessa: Future wants for remote software engineering](sochat-future-remote-rseng.pdf)
1. [Willenbring J., Milewicz R.: Moving Forward Together: How a Software Engineering Department Can Impact Developer Productivity in a Research Organization](willenbring-forward-together.pdf)
1. [Windus, T., Nash, J., and Richard, R.: Scientific Software Developer Productivity Challenges from the Molecular Sciences](windus-nash-richard-productivity-challenges-mol-sci.pdf)
1. [Woods, J., Baker, M., Thavappiragasam, M., Sedova, A., Hernandez, O., Sarkar, V.: Using Python for Improved Productivity in HPC and Data Science Applications: the Time is Now](woods-baker-thavappiragasam-sedova-hernandez-sarkar-python-for-improved-productivity-time-is-now.pdf)

#### [Back to Main Page](../../index.md)
