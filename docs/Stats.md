---
layout: page
title:
---

{% assign belt_totals = {} %}
{% assign active_members = site.data.members | where_exp: "member", "member.inactive != true" %}

<!-- Initialize the totals for each belt level -->
{% for belt in site.beltLevels %}
  {% assign belt_totals = belt_totals | merge: { belt.value: 0 } %}
{% endfor %}

<!-- Calculate the total belts granted, which includes progression through all belts -->
{% assign belt_total = 0 %}
{% for belt in site.beltLevels %}
  {% assign belt_total = belt_total | plus: belt_totals[belt.value] %}
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
