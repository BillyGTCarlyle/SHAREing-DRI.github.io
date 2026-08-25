---
permalink: /tasks-in-progress/
title: "Tasks in progress"
layout: splash
classes: wide
---

<style>

.parallax-hero {
  width: 100vw;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
  height: 50vh;
  background-image: url('/assets/images/sc-booth.jpg');
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
}

.parallax-overlay {
  width: 100%;
  height: 100%;
  background: linear-gradient(to top, rgba(0,42,65,0.9), rgba(0,42,65,0.45));
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: #fff;
}

.parallax-overlay h1 {
  font-size: 3rem;
  margin-bottom: 0.5rem;
}



/* GRID */
.tasks-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}


.task-card {
  background: #ffffff;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 28px rgba(0,0,0,0.07);
  border-top: 4px solid #68246d;
  text-decoration: none;
  color: inherit;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  display: flex;
  flex-direction: column;
}

.task-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 18px 40px rgba(0,0,0,0.12);
}

.task-card {
  position: relative;
}

.task-new-badge {
  position: absolute;
  top: 1rem;
  right: 1rem;
  z-index: 5;

  background: #B906B9;
  color: #fff;

  padding: 0.45rem 0.85rem;
  border-radius: 999px;

  font-size: 0.75rem;
  font-weight: 800;
  letter-spacing: 0.08em;
  text-transform: uppercase;

  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}


.task-main-image {
  width: 100%;
  height: 220px;
  object-fit: cover;
  display: block;
}

.task-content {
  padding: 1.4rem;
}


.task-card .wp {
 display: inline-flex;
  align-items: center;

  padding: 0.45rem 1rem;
  margin-bottom: 1rem;

  border-radius: 999px;


background: rgba(255,255,255,0.9);

  border: 1px solid rgba(255,255,255,0.18);


  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;

  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}


.task-card h3 {
  font-size: 1.15rem;
  margin-bottom: 1rem;
  color: #68246d;
  line-height: 1.4;
}


.task-person {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  margin-top: auto;
}


.task-profile-pic {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  object-fit: cover;
  flex-shrink: 0;
  border: 2px solid #f0f0f0;
}


.task-person-info {
  display: flex;
  flex-direction: column;
}

.task-person-info .name {
  font-size: 0.92rem;
  font-weight: 600;
  color: #333;
}

.task-person-info .institution {
  font-size: 0.8rem;
  color: #777;
}


.assessment-header {
  text-align: center;
  margin: 1.5rem 0 2rem 0;
}

.assessment-header h1 {
  font-size: 2.1rem;
  margin-bottom: 0.3rem;
    margin-top: 0.3rem;
}

.assessment-header p {
  color: #555;
  font-size: 0.8rem;
  max-width: 1200px;
  margin: 1rem auto;
}
v

@media (max-width: 768px) {
  .parallax-hero {
    background-attachment: scroll;
    height: 30vh;
  }
  
    .parallax-overlay {
    padding: 1.5rem;
  }

  .parallax-overlay h1 {
    font-size: 2rem;
  }
   
}



</style>


<div class="assessment-header">
  <h1>Tasks in Progress</h1>
  <p>

This page showcases the current work taking place within SHAREing. These activities were proposed as solutions to open tasks across the different work packages. Browse the mini-projects currently in progress and <a href='https://shareing-dri.github.io/contact/'>get in touch</a> if you would like to get involved.

If you are interested in contributing similar work, please explore our current <a href='https://shareing-dri.github.io/task-map/'>open tasks and propose your own solution</a>.


</p>
</div>


<section class="section-wide">
 <div class="tasks-grid">

  {%- comment -%}
    First show tasks marked as "new"
  {%- endcomment -%}

  {% for task in site.tasks %}
    {% if task.status == "progress" and task.added == "new" %}

      <a href="{{ task.url }}" class="task-card">

        <span class="task-new-badge">Just funded!</span>

        {% if task.image %}
          <img
            src="{{ task.image }}"
            loading="lazy"
            class="task-main-image"
          >
        {% endif %}

        <div class="task-content">

          <p class="wp">{{ task.workpackage }}</p>

          <h3>{{ task.title }}</h3>

          {% if task.person.name %}
            <div class="task-person">

              {% if task.person.image %}
                <img
                  src="{{ task.person.image }}"
                  loading="lazy"
                  alt="{{ task.person.name }}"
                  class="task-profile-pic"
                >
              {% endif %}

              <div class="task-person-info">

                <div class="name">
                  {{ task.person.name }}
                </div>

                {% if task.person.institution %}
                  <div class="institution">
                    {{ task.person.institution }}
                  </div>
                {% endif %}

              </div>

            </div>
          {% endif %}

        </div>

      </a>

    {% endif %}
  {% endfor %}


  {%- comment -%}
    Then show all other tasks
  {%- endcomment -%}

  {% for task in site.tasks %}
    {% if task.status == "progress" and task.added != "new" %}

      <a href="{{ task.url }}" class="task-card">

        {% if task.image %}
          <img
            src="{{ task.image }}"
            loading="lazy"
            class="task-main-image"
          >
        {% endif %}

        <div class="task-content">

          <p class="wp">{{ task.workpackage }}</p>

          <h3>{{ task.title }}</h3>

          {% if task.person.name %}
            <div class="task-person">

              {% if task.person.image %}
                <img
                  src="{{ task.person.image }}"
                  loading="lazy"
                  alt="{{ task.person.name }}"
                  class="task-profile-pic"
                >
              {% endif %}

              <div class="task-person-info">

                <div class="name">
                  {{ task.person.name }}
                </div>

                {% if task.person.institution %}
                  <div class="institution">
                    {{ task.person.institution }}
                  </div>
                {% endif %}

              </div>

            </div>
          {% endif %}

        </div>

      </a>

    {% endif %}
  {% endfor %}

</div>
</section>
