---
title: Cocoa Conferences
description: List of cocoa conferences for iOS & macOS developers
---


## All-English conferences for **Cocoa** developers.

<div id="upcoming"></div>

## Past Conferences

<div id="past"></div>

### More

* A [Twitter list](https://twitter.com/NeoNacho/lists/cocoaconferences) with all the conferences made by [Boris Bügling](https://twitter.com/NeoNacho)

If you want to add a conference to this list or edit the info, send a **pull request**, [ping me on twitter](https://twitter.com/lascorbe) or get in touch at [luis@nsspain.com](mailto:luis@nsspain.com). Thank you!


<script type="text/javascript"> 
const conferences = [
{% for conference in site.data.conferences %}
  {
    name: "{{ conference.name }}",
    link: {% if conference.link %} "{{ conference.link }}" {% else %} null {% endif %},
    location: {% if conference.location %} "{{ conference.location }}" {% else %} "TBA" {% endif %},
    cocoa: {% if conference.cocoa-only %} true {% else %} false {% endif %},
    {% if conference.start %}
		{% assign start = conference.start | split: "-" %}
    	start: { year: {{ start[0] }}, month: {{ start[1] }}, day: {{ start[2] }} },
    	{% if conference.end %}
			{% assign end = conference.end | split: "-" %}
		    end: { year: {{ end[0] }}, month: {{ end[1] }}, day: {{ end[2] }} },
    	{% else %}
	    end: { year: {{ start[0] }}, month: {{ start[1] }}, day: {{ start[2] }} },
    	{% endif %}
    {% else %}
	    start: null,
	    end: null,
    {% endif %}
    cfp: {
      {% if conference.cfp.link %}
     	 link: "{{ conference.cfp.link }}",
      {% else %}
   	   link: null,
      {% endif %}
      {% if conference.cfp.deadline %}
        {% assign dead = conference.cfp.deadline | split: "-" %}
    	  deadline: { year: {{ dead[0] }}, month: {{ dead[1] }}, day: {{ dead[2] }} }
      {% else %}
    	  deadline: null
      {% endif %}
    }
  },
{% endfor %}
];

{% include helpers.js %} 

buildSections(conferences);

</script>
