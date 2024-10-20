---
layout: page
title:
---

<!-- Debugging: Output the full belts structure for each member -->
{% for member in site.data.members %}
  <p>Member {{ member.name }} belts: {{ member.belts | inspect }}</p>
{% endfor %}


<!-- Step 1: Initialize variables for each belt level -->
{% assign white_total = 0 %}
{% assign yellow_total = 0 %}
{% assign green_total = 0 %}
{% assign blue_total = 0 %}
{% assign purple_total = 0 %}
{% assign brown_total = 0 %}
{% assign red_total = 0 %}
{% assign black_total = 0 %}

<!-- Step 2: Loop through members and access the mindset belt -->
{% for member in site.data.members %}
  {% if member.belts.mindset %}
    <!-- Check the mindset belt value and increment the correct total -->
    {% case member.belts.mindset %}
      {% when "white" %}
        {% assign white_total = white_total | plus: 1 %}
      {% when "yellow" %}
        {% assign yellow_total = yellow_total | plus: 1 %}
      {% when "green" %}
        {% assign green_total = green_total | plus: 1 %}
      {% when "blue" %}
        {% assign blue_total = blue_total | plus: 1 %}
      {% when "purple" %}
        {% assign purple_total = purple_total | plus: 1 %}
      {% when "brown" %}
        {% assign brown_total = brown_total | plus: 1 %}
      {% when "red" %}
        {% assign red_total = red_total | plus: 1 %}
      {% when "black" %}
        {% assign black_total = black_total | plus: 1 %}
    {% endcase %}
  {% else %}
    <p>Member {{ member.name }} does not have a mindset belt assigned.</p>
  {% endif %}
{% endfor %}

<!-- Step 3: Output the final totals for each belt -->
<p>White belts: {{ white_total }}</p>
<p>Yellow belts: {{ yellow_total }}</p>
<p>Green belts: {{ green_total }}</p>
<p>Blue belts: {{ blue_total }}</p>
<p>Purple belts: {{ purple_total }}</p>
<p>Brown belts: {{ brown_total }}</p>
<p>Red belts: {{ red_total }}</p>
<p>Black belts: {{ black_total }}</p>




<!-- Step 1: Initialize each belt level total explicitly in a more Liquid-friendly way -->
{% assign belt_totals = "" %}

{% for belt in site.beltLevels %}
  {% capture belt_key %}{{ belt.value }}{% endcapture %}
  {% assign belt_totals = belt_totals | append: belt_key | append: ":0;" %}
{% endfor %}

<!-- Step 2: Parse belt_totals into key-value pairs -->
{% assign belt_totals_array = belt_totals | split: ";" %}
{% assign belt_dict = {} %}

{% for item in belt_totals_array %}
  {% assign key_value = item | split: ":" %}
  {% if key_value[0] and key_value[1] %}
    {% assign belt_dict = belt_dict | merge: { key_value[0]: key_value[1] | plus: 0 } %}
  {% endif %}
{% endfor %}

<!-- Debugging: Output the structure of the belt_dict dictionary -->
<p>{{ belt_dict | inspect }}</p>

<!-- Step 3: Modify belt_dict based on actual belt ownership -->
{% for member in site.data.members %}
  {% for belt in member.belts %}
    {% if belt_dict[belt] %}
      {% assign current_value = belt_dict[belt] | plus: 1 %}
      {% assign belt_dict = belt_dict | merge: { belt: current_value } %}
    {% endif %}
  {% endfor %}
{% endfor %}

<!-- Step 4: Output the final belt totals -->
{% for belt in site.beltLevels %}
  <p>{{ belt.value | capitalize }}: {{ belt_dict[belt.value] }}</p>
{% endfor %}



{% assign active_members = site.data.members | where_exp: "member", "member.inactive != true" %}

<!-- Manually initialize each belt level total -->
{% for belt in site.beltLevels %}
  {% assign belt_totals = belt_totals | append: belt.value | append: ":0;" %}
{% endfor %}

<!-- Now split the belt_totals string back into usable parts -->
{% assign belt_totals_array = belt_totals | split: ";" %}
{% assign belt_totals = {} %}

<!-- Loop through the split array and set each belt's value -->
{% for pair in belt_totals_array %}
  {% assign key_value = pair | split: ":" %}
  {% if key_value[0] and key_value[1] %}
    {% assign belt_totals = belt_totals | merge: { key_value[0]: key_value[1] } %}
  {% endif %}
{% endfor %}

<!-- Inactive Members -->
{% assign inactiveArr = site.data.members | where_exp: "member", "member.inactive == true" %}

{% for belt in site.beltLevels %}
  {{ belt_totals | debug }}
  <p>{{ belt.value }}: {{ belt_totals[belt.value] }}</p>
{% endfor %}

<div class="jumbotron p-5">
    <h1 class="display-4">Dojo Progression</h1>
    <p class="lead">Active summary of the community's competence claims</p>
    <hr class="my-4">
    <div class="row">
        <div class="col-md-6 text-center my-4">
            <h1 class="display-4">{{site.data.members | size}}</h1>
            <img class="m-2" src="images/285989_AdvisoryCouncil_R_orange.png" height="150">
            <h3>Members with Belts</h3>
            <span>Active Members: {{active_members | size}}</span>
        </div>
        <div class="col-md-6 text-center my-4">
            <h1 class="display-4">{{belt_total}}</h1>
            <img class="m-2" src="images/286568_Badge_R_orange.png" height="150">
            <h3>Total Belts Granted</h3>
            <span>All-time Belt Count</span>
        </div>
    </div>
    <hr class="my-5">

    <!-- Dynamically Render Belt Levels and Totals -->
    <div class="row">
        {% for belt in site.beltLevels %}
          <div class="col-md-6 text-center my-6">
            <h1 class="display-5">{{ belt_totals[belt.value] }}</h1>
            <img src="images/belt-{{ belt.value }}.png" height="60">
            <h3>{{ belt.value | capitalize }} Belts</h3>
          </div>
        {% endfor %}
    </div>

</div>
<div class="row">
    {% for domain in site.domains %}
        {%- include domain-stats.html -%}
    {% endfor %}
</div>
<hr class="my-4">
<p><em>* Stats are based on those who have submitted for belts. Rank totals show how many actively hold that belt. Higher belts are not included in lower belt totals, but are reflected in the Total Belts Granted.</em></p>
<p><em>** Inactive Members: {{inactiveArr | size}}</em></p>
