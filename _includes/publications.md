<h2 id="publications" style="margin: 2px 0px -15px;">Selected Publications
  <a href="https://scholar.google.com/citations?user=qlqM-EQAAAAJ&hl=en" style="font-size: 14px; font-weight: normal; color: #666; text-decoration: none; margin-left: 10px;">[Google Scholar]</a>
</h2>

<div class="publications">
<ol class="bibliography">

{% for link in site.data.publications.main %}
{% if link.selected %}

<li>
<div class="pub-row">
  <div class="abbr">
    {% if link.conference_short %} 
    <abbr class="badge">{{ link.conference_short }}</abbr>
    {% endif %}
  </div>
  <div class="publication-content">
      <div class="title"><a href="{{ link.source }}">{{ link.title }}</a></div>
      <div class="author">{{ link.authors }}</div>
      <div class="periodical"><em>{{ link.conference }}</em>
      </div>
  </div>
</div>
</li>

<br>

{% endif %}
{% endfor %}

</ol>
</div>_includes/publications.md