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
            {% for image in award.preview_images %}
            <img src="{{ image }}" alt="Award Preview" class="img-fluid mb-2">
            {% endfor %}
        </div>
        <div class="col-8">
            <h5>{{ award.title }}</h5>
            <p class="award-description" style="max-height: 100px; overflow: hidden;">{{ award.description }}</p>
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
                <p><a href="{{ award.code }}" target="_blank"><i class="fa-brands fa-square-github"></i> </a></p>
            {% endif %}
            {% if award.embed_post %}
                <div class="mb-3">
                    {{ award.embed_post | safe }}
                </div>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>



<script>
document.addEventListener("DOMContentLoaded", function() {
    var showChar = 100;
    var ellipsestext = "...";
    var moretext = "Read more";
    var lesstext = "Show less";

    var moreButtons = document.querySelectorAll('.read-more');

    moreButtons.forEach(function(button) {
        button.addEventListener('click', function(event) {
            var parent = event.target.parentElement;
            var description = parent.querySelector('.award-description');

            if (description.classList.contains('less')) {
                description.classList.remove('less');
                event.target.textContent = moretext;
            } else {
                description.classList.add('less');
                event.target.textContent = lesstext;
            }
            return false;
        });
    });
});
</script>



















