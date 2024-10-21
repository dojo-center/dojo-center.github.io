---
layout: page
title: Members
datatable: true
---

<hr/>
<span class="text-info">Hold down shift to sort on multiple columns (secondary, tertiary, etc)</span>
<div>
    <table id="members-table" class="table table-bordered table-hover table-active display" data-page-length='25'>
        <thead>
            <tr>
                <th class="text-center" scope="col"></th>
                {% for program in site.programs -%}
                <th class="text-center" scope="col">{{program}}</th>
                {% endfor %}
            </tr>
        </thead>
        <tbody>
            {% for member_record in site.data.members %}
                {% assign member_id = member_record[0] %}
                {% assign member = member_record[1] %}
                {% if member.inactive == true %}
                    {% continue %}
                {% endif %}

                <tr>
                    <td class="text-left" scope="row">
                        <div class="text-primary"><a href="{{member.url}}">{{ member.name }}</a></div>
                    </td>
                    {% for program in site.programs %}
                        {% assign beltColor = "" %}
                        {% assign programLower = program | downcase %}
                        {% for item in member.belts %}
                            {% if item[0] == programLower %}
                            {% assign beltColor = item[1] %}
                            {% endif %}
                        {% endfor %}
                        
                        {% assign belt = site.beltLevels | where: "value", beltColor | first %}
                        {% if belt %}
                            {% assign beltSort = belt.sort %}
                        {% else %}
                            {% assign beltSort = -9999 %}
                        {% endif %}

                        <td class="text-center" data-search="{{ beltColor }}" data-sort="{{ beltSort }}"><img class="mx-auto d-block" src="images/belt-{{ beltColor }}.png" height="30" /></td>
                    {% endfor %}
                </tr>
            {% endfor %}
        </tbody>
    </table>
</div>

<script>
    $(document).ready(function() {
        $('#members-table').DataTable({
        });
    } );
</script>
