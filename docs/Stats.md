---
layout: page
title:
---

<!-- Step 1: Initialize an empty string to hold our belt totals -->
{% assign belt_totals = "" %}

<!-- Step 2: Dynamically add each belt key with an initial value of 0 -->
{% for belt in site.beltLevels %}
  {% capture belt_key %}{{ belt.value }}{% endcapture %}
  {% assign belt_totals = belt_totals | append: belt_key | append: ":0;" %}
{% endfor %}

<!-- Debugging: Output the belt_totals string to verify it's being created correctly -->
<p>{{ belt_totals }}</p>

<!-- Step 3: Convert the belt_totals string into an array of key-value pairs -->
{% assign belt_totals_array = belt_totals | split: ";" %}

<!-- Step 4: Create a dictionary from this array of key-value pairs -->
{% assign belt_totals_dict = {} %}
{% for pair in belt_totals_array %}
  {% assign key_value = pair | split: ":" %}
  {% if key_value[0] and key_value[1] %}
    {% assign belt_totals_dict = belt_totals_dict | merge: { key_value[0]: key_value[1] | plus: 0 } %}
  {% endif %}
{% endfor %}

<!-- Debugging: Output the dictionary to see its structure -->
{{ belt_totals_dict | debug }}

<!-- Step 5: Modify the values dynamically (this example shows how you can increase totals) -->
{% for member in site.data.members %}
  {% for belt in member.belts %}
    {% assign current_total = belt_totals_dict[belt] | plus: 1 %}
    {% assign belt_totals_dict = belt_totals_dict | merge: { belt: current_total } %}
  {% endfor %}
{% endfor %}

<!-- Step 6: Output the final belt totals -->
{% for belt in site.beltLevels %}
  <p>{{ belt.value | capitalize }}: {{ belt_totals_dict[belt.value] }}</p>
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
