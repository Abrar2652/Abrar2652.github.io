---
layout: page
permalink: /awards/
title: Awards
description: Noteworthy honors and awards Md Abrar Jahin received.
nav: true
nav_order: 3
---

<div class="container">
    {% assign awards = site.data.awards | sort: 'year' | sort: 'month' | reverse %}
    {% for award in awards %}
    <div class="row mb-4">
        <div class="col-2">
            <p class="text-muted">{{ award.year }} - {{ award.month }}</p>
            <img src="{{ award.preview_image }}" alt="Award Preview" class="img-fluid">
        </div>
        <div class="col-8">
            <h5>{{ award.title }}</h5>
            <p>{{ award.description }}</p>
            <p><a href="{{ award.certificate_pdf }}" target="_blank"><i class="fa-solid fa-award"></i> Certificate (PDF)</a></p>
            <p><a href="{{ award.shared_post_link }}" target="_blank"><i class="fab fa-facebook-square"></i> Shared Post</a></p>
            {% if award.facebook %}
                <a href="{{ award.facebook }}" target="_blank"><i class="fab fa-facebook-square"></i></a>
            {% endif %}
            {% if award.linkedin %}
                <a href="{{ award.linkedin }}" target="_blank"><i class="fa-brands fa-linkedin"></i></a>
            {% endif %}
            {% if award.twitter %}
                <a href="{{ award.twitter }}" target="_blank"><i class="fab fa-twitter"></i></a>
            {% endif %}
            {% if award.youtube %}
                <a href="{{ award.youtube }}" target="_blank"><i class="fab fa-youtube"></i></a>
            {% endif %}
            {% if award.external_link %}
                <a href="{{ award.external_link }}" target="_blank"><i class="fa-regular fa-link"></i></a>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>
