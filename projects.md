---
id: 5
title: projects
author: 'Parker Higgins'
layout: page
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
                <a href="{{ project.link }}"><h2>{{ project.title }}</h2></a>
                <span class="year">{{ project.year }}</span>
            </div>
            {% if project.image %}
            <div class="project-image-box">
                <img class="project-image" src="{{ project.image | prepend: '/assets/images/' | relative_url }}" />
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
                 <a href="{{ project.link | relative_url}}"><h3>{{ project.title }}</h3></a>
                <span class="year">{{ project.year }}</span>
            </div>
            {% if project.image %}
            <div class="project-image-box">
                <img class="project-image" src="{{ project.image | prepend: '/assets/images/' | relative_url }}" />
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
