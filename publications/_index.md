---
title: "Publications"
aliases: /publications/
description: "Preprints and conference articles."
---

# Publications

Here is a list of my publications. For more details, click on the title or use the expandable abstracts.

<div id="full-pub-list-button" onclick="toggleFullPubList()" style="cursor: pointer; margin-bottom: 15px; font-weight: bold;">
🔽 Full Publications
</div>

<div id="full-pub-list">
{% assign sorted_publications = site.publications | sort: 'date' | reverse %}
{% for pub in sorted_publications %}
<div class="publication" style="margin-bottom: 30px; padding-bottom: 20px; border-bottom: 1px solid #eee;">
    <h3 style="margin-bottom: 5px;">
        <a href="{{ pub.url | relative_url }}" style="color: #2c3e50; text-decoration: none;">
            {{ pub.title }}
        </a>
    </h3>
    
    <p style="margin-bottom: 5px; color: #666; font-style: italic;">
        {{ pub.date | date: "%Y" }} • 
        {% if pub.editPost.Text %}
            {{ pub.editPost.Text }}
        {% endif %}
    </p>
    
    <p style="margin-bottom: 10px; color: #333;">
        <strong>{{ pub.author | array_to_sentence_string }}</strong>
    </p>
    
    {% if pub.summary %}
    <p style="margin-bottom: 10px; color: #555; font-size: 0.95em;">
        {{ pub.summary }}
    </p>
    {% endif %}
    
    {% if pub.tags %}
    <p style="margin-bottom: 10px;">
        {% for tag in pub.tags %}
            <span style="background-color: #f0f0f0; padding: 2px 8px; margin-right: 5px; border-radius: 3px; font-size: 0.85em; color: #666;">
                {{ tag }}
            </span>
        {% endfor %}
    </p>
    {% endif %}
    
    <div style="margin-top: 10px;">
        {% if pub.url %}
            <a href="{{ pub.url | relative_url }}" style="margin-right: 10px; color: #3498db; text-decoration: none;">📄 Paper</a>
        {% endif %}
        {% if pub.editPost.URL %}
            <a href="{{ pub.editPost.URL }}" style="margin-right: 10px; color: #3498db; text-decoration: none;" target="_blank">🔗 DOI</a>
        {% endif %}
        <a href="javascript:toggle('#abstract-{{ forloop.index }}')" style="color: #3498db; text-decoration: none;">📖 Abstract</a>
    </div>
    
    <div id="abstract-{{ forloop.index }}" style="display: none; margin-top: 15px; padding: 15px; background-color: #f9f9f9; border-left: 4px solid #3498db;">
        {% if pub.description %}
            <p style="margin-bottom: 0;">{{ pub.description }}</p>
        {% else %}
            <p style="margin-bottom: 0; font-style: italic;">No abstract available.</p>
        {% endif %}
    </div>
</div>
{% endfor %}
</div>
