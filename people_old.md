---
title: People
permalink: /people/
---



<img src="{{site.baseurl}}/images/people/group_photo.jpeg" alt="Group Photo" style="width:100%; max-width:1000px;">
<hr>

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|phd|gradstudent|researchstaff|visiting|others|pet|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
  {% if role == 'postdoc' %}
    <h2>Postdoctoral Fellows</h2>
  {% elsif role == 'pi' %}
    <h2>Principal Investigator</h2>
  {% elsif role == 'phd' %}
    <h2>PhD. Students</h2>
  {% elsif role == 'gradstudent' %}
    <h2>Master's Students</h2>
  {% elsif role == 'researchstaff' %}
    <h2>Bachelor's Students</h2>
  {% elsif role == 'visiting' %}
    <h2>Visiting Scholars</h2>
  {% elsif role == 'pet' %}
    <h2>Our Pets</h2>
  {% elsif role == 'others' %}
    <h2>Honorary Members</h2>
  {% elsif role == 'alumni' %}
    <h2>Alumni</h2>
  {% endif %}
</div>

{% if role != 'alumni' %}
  <div class="content list people">
    {% for profile in people_sorted %}
      {% if profile.position contains role %}
        <div class="list-item-people">
          <p class="list-post-title">
            {% if profile.avatar %}
              <a href="{{ profile.personal-url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
            {% else %}
              <a href="{{ profile.personal-url }}"><img class="profile-thumbnail" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
            {% endif %}
            <a class="name" href="{{ profile.personal-url }}">{{ profile.name }}</a>
            <!-- {% if role == 'phd' %}
              <br>
              <span style="color: gray; font-size: 0.9em;">(joining Spring'25)</span>
            {% endif %} -->
          </p>
        </div>
      {% endif %}
    {% endfor %}
  </div>
{% endif %}

<hr> <!-- Line after each section -->

{% endfor %}

<h2>Past Supporters and Collaborators</h2>
<p>Download the PDF <a href="https://drive.google.com/file/d/10a1xLuJ5Q6iOPjchg42H5qcY-SPkOPwd/view?usp=sharing">here</a>.</p>

