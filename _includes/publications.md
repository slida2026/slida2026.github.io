<h2 id="publications" style="margin: 2px 0px -15px;">Selected Publications 
  <a href="#" id="view-all-link" style="font-size: 14px; font-weight: normal; color: #666; text-decoration: none; margin-left: 10px;">[View All]</a>
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
</div>

<!-- All Publications Section (Hidden by default) -->
<div id="all-publications" style="display: none;">
<div class="publications">
<ol class="bibliography">

<!-- Main Publications -->
{% for link in site.data.publications.main %}

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

{% endfor %}


</ol>
</div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const viewAllLink = document.getElementById('view-all-link');
    const selectedPublications = document.querySelector('.publications');
    const allPublications = document.getElementById('all-publications');
    const publicationsTitle = document.querySelector('#publications');
    
    // Store original display states and title
    const originalStates = new Map();
    const originalTitle = publicationsTitle.innerHTML;
    let isShowingAll = false; // Track current state
    
    viewAllLink.addEventListener('click', function(e) {
        e.preventDefault();
        
        if (!isShowingAll) {
            // Show all publications and hide other sections
            allPublications.style.display = 'block';
            selectedPublications.style.display = 'none';
            
            // Change the main title and update the link text
            // Update the h2 text content (everything except the link)
            const h2Element = publicationsTitle;
            const linkElement = h2Element.querySelector('#view-all-link');
            const textNode = h2Element.childNodes[0]; // The text node before the link
            textNode.textContent = 'All Publications ';
            linkElement.textContent = '[Show Homepage]';
            
            // Update state
            isShowingAll = true;
            
            // Scroll to the top of the page
            window.scrollTo({ top: 0, behavior: 'smooth' });
            
            // Hide all h2 elements except publications and their content
            const allH2s = document.querySelectorAll('h2');
            allH2s.forEach(h2 => {
                if (h2.id !== 'publications') {
                    // Store original state
                    originalStates.set(h2, h2.style.display);
                    h2.style.display = 'none';
                    
                    // Hide all following elements until next h2
                    let nextElement = h2.nextElementSibling;
                    while (nextElement && nextElement.tagName !== 'H2') {
                        originalStates.set(nextElement, nextElement.style.display);
                        nextElement.style.display = 'none';
                        nextElement = nextElement.nextElementSibling;
                    }
                }
            });
        } else {
            // Show selected publications and restore all sections
            allPublications.style.display = 'none';
            selectedPublications.style.display = 'block';
            
            // Restore the original title and link text
            const h2Element = publicationsTitle;
            const linkElement = h2Element.querySelector('#view-all-link');
            const textNode = h2Element.childNodes[0]; // The text node before the link
            textNode.textContent = 'Selected Publications ';
            linkElement.textContent = '[View All]';
            
            // Update state
            isShowingAll = false;
            
            // Restore all original states
            originalStates.forEach((originalDisplay, element) => {
                element.style.display = originalDisplay;
            });
            originalStates.clear();
        }
    });
});
</script>
