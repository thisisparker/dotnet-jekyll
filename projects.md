---
id: 5
title: projects
layout: page
image: /assets/images/computer-music.png
permalink: /projects/
---

<div class="projects">
    {% assign all-projects = site.projects | concat: site.project-pages %}
    {% assign featured_projects = all-projects | where:'featured',true |sort:'year' | reverse %}
    <ul id="featured-project-list">
    {% for project in featured_projects %}
        <li>
        <div class="project-box">
            <div class="project-title">
                <h2><a href="{{ project.link }}">{{ project.title }}</a></h2>
                <span class="year">{{ project.year }}</span>
            </div>
            {% if project.image %}
            <div class="project-image-box">
                <a href="{{ project.link }}"><img class="project-image" src="{{ project.image }}" /></a>
            </div>
            {% endif %}
            <div class="project-description">
                <p>{{ project.excerpt }}</p>
            </div>
        </div>
        </li>
    {% endfor %}
    </ul>
    <ul id="non-featured-project-list">
    {% assign non-featured-projects = all-projects | where_exp:'proj','proj.featured != true' | sort:'year' | reverse %}
    {% for project in non-featured-projects %}
        <li>
        <div class="project-box">
            <div class="project-title">
                <h3><a href="{{ project.link | relative_url}}">{{ project.title }}</a></h3>
                <span class="year">{{ project.year }}</span>
            </div>
            {% if project.image %}
            <div class="project-image-box">
                <a href="{{ project.link }}"><img class="project-image" src="{{ project.image }}" /></a>
            </div>
            {% endif %}
            <div class="project-description">
                <p>{{ project.excerpt }}</p>
            </div>
        </div>
        </li>
    {% endfor %}
    </ul>
</div>
