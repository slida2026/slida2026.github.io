<h2 id="publications" style="margin: 2px 0px -15px;">Selected Publications
  <a href="https://scholar.google.com/citations?user=qlqM-EQAAAAJ&hl=en" style="font-size: 14px; font-weight: normal; color: #666; text-decoration: none; margin-left: 10px;">[View All]</a>
</h2>

<div class="publications">
<ol class="bibliography">

{% for link in site.data.publications.main %}
{% if link.selected %}

<li>
<div class="pub-row">
  <div class="col-sm-3 abbr" style="position: relative;padding-right: 15px;padding-left: 15px;">
    {% if link.conference_short %} 
    <abbr class="badge">{{ link.conference_short }}</abbr>
    {% endif %}
  </div>
  <div class="col-sm-9" style="position: relative;padding-right: 15px;padding-left: 20px;">
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