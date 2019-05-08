{% comment %}
#
#   This is a nested liquid loop for Jekyll to iterate through YAML data with
#   a depth of three levels. The example loops through a potential table of
#   contents of a book.
#
#   This is the example YAML content'

- chapters: 'Einführung'
  sub_chapters:
    - title: 'Einführung in Jekyll'

- chapters: 'Installation'
  sub_chapters:
    - title: Sub_Subchapter
      sub_sub_chapters:
        - title : 'Mac Installation'
          url   : 'mac-install.adoc'
        - title : 'Window Installation'
          url   : 'window-install.adoc'
        - title : 'Linux Installation'
          url   : 'linux-install.adoc'
    - title : 'Mac Installation'
      url   : 'mac-install.adoc'
    - title : 'Window Installation'
      url   : 'window-install.adoc'
    - title : 'Linux Installation'
      url   : 'linux-install.adoc'

- chapters: 'Aufbau einer Jekyll-Website'
  sub_chapters:
   - title  : '_config.yml'
     url   : 'config.adoc'
   - title  : 'Variablen'
     url   : 'variablen.adoc'
   - title  : 'Programmieren mit Liquid'
     url   : 'liquid.adoc'
   - title  : 'Front Matter & YAML'
     url   : 'front-matter.adoc'

{% endcomment %}


{% for entry in site.data.toc_jekyll %}

<h2>{{ entry.chapters }}</h2>

  {% for subchapter in entry.sub_chapters %}
  	{% if forloop.first %}<ul>{% endif %}
    	<li><h3><a href="{{ subchapter.url }}">{{ subchapter.title }}</a></h3></li>

		  {% for subsubchapter in subchapter.sub_sub_chapters %}
		  	{% if forloop.first %}<ul>{% endif %}
		    	<li><h4><a href="{{ subchapter.url }}">{{ subchapter.title }}</a></h4></li>
		  	{% if forloop.last %}</ul>{% endif %}
		  {% endfor %}

  	{% if forloop.last %}</ul>{% endif %}
  {% endfor %}

{% endfor %}