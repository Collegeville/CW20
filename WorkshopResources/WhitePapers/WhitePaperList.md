# 2020 Collegeville Workshop on Scientific Software Whitepapers

To edit this page, make a pull request for the [page source on GitHub](https://github.com/Collegeville/CW20/blob/master/WorkshopResources/WhitePapers/WhitePaperList.md).  Add the PDF of your white paper to the same folder.

[**All White Papers: WhitePapersBundle.zip**](../WhitePapersBundle.zip)

## List of papers:

- [Sochat, Vanessa: Developer productivity means developer happiness](developer-happiness-whitepaper-vsochat.pdf)
- [Sochat, Vanessa: Future wants for remote software engineering](future-remote-rseng-whitepaper-vsochat.pdf)

<<<<<<< Updated upstream
- [Lastname, Firstname: Title](file.pdf)
=======
{% comment %}
{% assign myfiles = site.static_files | where: "white_paper", true %}
{% endcomment %}
{% assign myfiles = site.static_files %}
{% for file in myfiles %}
<h3>{{file.name}}</h3>
<a href="{{file.path}}">{{file.path}}</a>
{% endfor %}
>>>>>>> Stashed changes

#### [Back to Main Page](../../index.md)
