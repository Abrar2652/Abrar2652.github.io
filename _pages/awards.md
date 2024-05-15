---
layout: page
permalink: /awards/
title: Awards
description: Noteworthy honors and awards Md Abrar Jahin received.
nav: true
nav_order: 3
---

<div class="container">
    {% assign month_map = "January,1|February,2|March,3|April,4|May,5|June,6|July,7|August,8|September,9|October,10|November,11|December,12" | split: "|" %}
    
    {% assign awards = site.data.awards %}
    {% for award in awards %}
        {% assign month_number = 0 %}
        {% for map in month_map %}
            {% assign key_value = map | split: "," %}
            {% if award.month == key_value[0] %}
                {% assign month_number = key_value[1] %}
            {% endif %}
        {% endfor %}
        {% assign timestamp = award.year | append: "-" | append: month_number | append: "-01" | date: "%s" %}
        {% assign award.timestamp = timestamp %}
    {% endfor %}
    
    {% assign sorted_awards = awards | sort: "timestamp" %}

    {% for award in sorted_awards %}
    <div class="row mb-4">
        <div class="col-2">
            <p class="text-muted">{{ award.year }} - {{ award.month }}</p>
            {% for image in award.preview_images %}
            <img src="{{ image }}" alt="Award Preview" class="img-fluid mb-2">
            {% endfor %}
        </div>
        <div class="col-8">
            <h5>{{ award.title }}</h5>
            <p class="award-description">
                {{ award.description | truncatewords: 30 }}...
                <span class="more-content" style="display: none;">{{ award.description | remove_first: award.description | truncatewords: 30 }}</span>
                <a href="#" class="read-more">Read more</a>
            </p>
            {% if award.certificate %}
                <p><a href="{{ award.certificate }}" target="_blank"><i class="fa-solid fa-award"></i> Certificate</a></p>
            {% endif %}
            {% if award.pdf %}
                <p><a href="{{ award.pdf }}" target="_blank"><i class="fa-solid fa-file-pdf"></i> PDF</a></p>
            {% endif %}
            {% if award.facebook %}
                <p><a href="{{ award.facebook }}" target="_blank"><i class="fab fa-facebook-square"></i> Facebook reference</a></p>
            {% endif %}
            {% if award.linkedin %}
                <p><a href="{{ award.linkedin }}" target="_blank"><i class="fa-brands fa-linkedin"></i> LinkedIn reference</a></p>
            {% endif %}
            {% if award.twitter %}
                <p><a href="{{ award.twitter }}" target="_blank"><i class="fab fa-twitter"></i> Twitter reference</a></p>
            {% endif %}
            {% if award.youtube %}
                <p><a href="{{ award.youtube }}" target="_blank"><i class="fab fa-youtube"></i> YouTube video</a></p>
            {% endif %}
            {% if award.external_link %}
                <p><a href="{{ award.external_link }}" target="_blank"><i class="fa-regular fa-link"></i> Link</a></p>
            {% endif %}
            {% if award.website %}
                <p><a href="{{ award.website }}" target="_blank"><i class="fa-solid fa-globe"></i> Website</a></p>
            {% endif %}
            {% if award.code %}
                <p><a href="{{ award.code }}" target="_blank"><i class="fa-brands fa-square-github"></i> Code</a></p>
            {% endif %}
            {% if award.embed_post %}
                <div class="mb-3">
                    {{ award.embed_post | safe }}
                </div>
            {% endif %}
            {% if award.video %}
                <div class="mb-3">
                    <video width="300" height="240" controls>
                      <source src="{{ site.baseurl }}/assets/videos/{{ award.video }}" type="video/mp4">
                      Your browser does not support the video tag.
                    </video>
                </div>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>
<style>
    .more-content {
        display: none;
    }

    .read-more:after {
        content: 'Read more';
        color: blue;
        cursor: pointer;
    }

    .read-more.expanded:after {
        content: 'Show less';
    }

    .read-more.expanded + .more-content {
        display: inline;
    }
</style>
