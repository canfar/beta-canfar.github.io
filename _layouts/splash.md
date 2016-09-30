---
layout: default
---

{% include _page_header.html %}

<div class="container">
  <div class="row">

    <section id="main_content">
      <div id="canfar-carousel" class="carousel slide"
           data-ride="carousel" data-keyboard="true">
        <!-- Indicators -->
        <ol class="carousel-indicators">
          {% for showcase in site.data.showcases %}
          {% assign idx = forloop.index | minus: 1 %}
          <li data-target="#canfar-carousel" data-slide-to="{{ idx }}" {% if idx == 0 %}class="active"{% endif %}></li>
          {% endfor %}
        </ol>

        <!-- Wrapper for slides -->
        <div class="carousel-inner" role="listbox">
          {% for showcase in site.data.showcases %}
          {% assign tagindex = forloop.index | minus: 1 %}
          <div class="item {% if forloop.index == 1 %}active{% endif %}" style="background-image: url('{{ showcase.img | prepend: site.baseurl }}');">
            <div class="carousel-caption">
              <h3>{{ showcase.title }}</h3>
              <p>{{ t.showcase_taglines[tagindex] }}</p>
            </div>
          </div>
          {% endfor %}
        </div>

        <!-- Controls -->
        <a class="left carousel-control" href="#canfar-carousel"
           role="button" data-slide="prev">
          <span class="glyphicon glyphicon-chevron-left"
                aria-hidden="true"></span>
          <span class="sr-only">{{ t.previous }}</span>
        </a>
        <a class="right carousel-control" href="#canfar-carousel"
           role="button" data-slide="next">
          <span class="glyphicon glyphicon-chevron-right"
                aria-hidden="true"></span>
          <span class="sr-only">{{ t.next }}</span>
        </a>
      </div>

    </section>

    <section id="information_section">
      <div class="row">
        <div class="col-md-4">
          <h3 class="text-info information_section_capture">Providing research cyberinfrastructure services
            to the Canadian astronomical community</h3>

          <p>The Canadian Advanced Network for Astronomy Research is a national platform
            for data-intensive scientific computing.</p>

          <p>CANFAR is a consortium of Canadian university astronomers, Compute Canada,
            and the National Research Council Canada’s Canadian Astronomy Data Centre
            with support from CANARIE and the Canadian Space Agency.</p>

          <p>CANFAR services include:</p>
          <ul>
            <li>Archival data storage for major Canadian and international observatories
              and projects
            </li>
            <li>Cloud processing</li>
            <li>Infrastructure for visualization and analytics on massive datasets</li>
            <li>User-managed storage for research teams</li>
            <li>Innovative development to keep Canadian science at the leading edge</li>
          </ul>

        </div>
        <div id="information_content" class="col-md-8">
          <div class="col-md-4">
            <div class="panel panel-default">
              <div class="panel-heading">
                <h3 class="panel-title">{{ t['news'].name }} </h3>
              </div>
              <div class="panel-body">
                {% assign news_posts = (site.posts | where: 'category', 'news') %}
                {% for post in news_posts %}
                <div class="media">
                  <div class="media-body">
                    <h4 class="media-heading"><span class="glyphicon glyphicon-chevron-right"></span><a href="{{ post.url }}">{{ post.date | date: '%B %d, %Y' }}</a></h4>
                    {{ post.excerpt | strip_html | truncatewords:10 }}
                  </div>
                </div>
                {% endfor %}
              </div>
            </div>
          </div>
          <div class="col-md-4">
            <div class="panel panel-default">
              <div class="panel-heading">
                <h3 class="panel-title">{{ t['events'].name }} </h3>
              </div>
              <div class="panel-body">
                {% assign events_posts = (site.posts | where: 'category', 'events') %}
                {% for post in events_posts %}
                <div class="media">
                  <div class="media-body">
                    <h4 class="media-heading"><span class="glyphicon glyphicon-chevron-right"></span><a href="{{ post.url }}">{{ post.date | date: '%B %d, %Y' }}</a></h4>
                    {{ post.excerpt | strip_html | truncatewords:10 }}
                  </div>
                </div>
                {% endfor %}
              </div>
            </div>
          </div>
          <div class="col-md-4">
            <div class="panel panel-default">
              <div class="panel-heading">
                <h3 class="panel-title">{{ t['featured'].name }} </h3>
              </div>
              <div class="panel-body">
                {% assign featured_posts = (site.posts | where: 'category', 'featured') %}
                {% for post in featured_posts | limit: 1 %}
                <div class="media">
                  <div class="media-body">
                    <h4 class="media-heading"><span class="glyphicon glyphicon-chevron-right"></span><a href="{{ post.url }}">{{ post.title }}{% if post.author %} by {{ post.author }}{% endif %}</a> </h4>
                    {{ post.excerpt | strip_html | truncatewords:50 }}
                  </div>
                </div>
              {% endfor %}
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    {% include _page_footer.html %}

  </div>
</div>