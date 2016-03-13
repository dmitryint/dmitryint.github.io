---
layout: page
title: Судебное делопроизводство
tagline: Белый Город vs Сабидом
---
{% assign active = site.data.sabidom_case_data.first %}

{% for sud in site.data.sabidom_case_data %}
<script>
$('#{{ sud.name }} a').click(function (e) {
  e.preventDefault()
  $(this).tab('show')
})
</script>
{% endfor %}

<ul class="nav nav-tabs">
  {% for sud in site.data.sabidom_case_data %}
  	<li {% if sud == active %}class="active"{% endif %}><a href="#{{ sud.name }}" data-toggle="tab">{{ sud.name }}</a></li>
  {% endfor %}
</ul>

<div class="tab-content">
{% for sud in site.data.sabidom_case_data %}
  <div class="tab-pane {% if sud == active %}active{% endif %}" id="{{ sud.name }}" id="{{ sud.name }}">
  {% for case in sud.data %}
  	<div class="row">
  		<div class="col-md-9">
    		<a href="{{ case.link }}">{{ case.case_number }}</a>
    	</div>
    </div>
    <div class="row">
    	<div class="col-md-9">
    		{% for event in case.events %}
    		<span class="glyphicon {{ event.icon }}" data-toggle="tooltip" data-placement="top" title="{{event.date}} {{event.time}}: {{event.event}}"></span> 
    		{% endfor %}
    	</div>
    </div>
  {% endfor %}
  </div>
{% endfor %}
</div>