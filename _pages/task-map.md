---
permalink: /task-map/
title: "Task Map"
layout: default
sidebar: false
---

<style>
.shareing-diagram {
  font-family: system-ui, sans-serif;
  background: #f8fafc;
  border: 1px solid #dbe4ee;
  border-radius: 24px;
  padding: 0.9rem;

  max-width: 1200px;
  margin: auto auto;

  color: #17365d;
}

.shareing-diagram h2 {
  text-align: center;
  font-size: 2.2rem;
  margin-bottom: 0.75rem;
}

.shareing-diagram .intro {
  text-align: center;
  max-width: 1200px;
  color: #475569;
  line-height: 1.7;
  font-size: 0.7rem;
}

.diagram-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  position: relative;
}

.diagram-column {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.column-title {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 1.25rem;
  border-radius: 16px;
  font-weight: 700;
  font-size: 0.9rem;
    min-height: 110px;
}

.column-title.blue {
  background: #D9F1FF;
  border: 2px solid #002A41;
  color: #002A41;
}

.column-title.green {
  background: #FEE8FE;
  border: 2px solid #740574;
  color: #740574;
}

.icon-circle {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  color: white;
  font-size: 1.4rem;
  flex-shrink: 0;
}

.blue .icon-circle {
  background: #002A41;
}

.green .icon-circle {
  background: #740574;
}

.flow-card {
  background: white;
  border-radius: 18px;
  padding: 1rem;
  border: 1px solid #dbe4ee;
  position: relative;
}

.flow-card::after {
  content: "↓";
  position: absolute;
  bottom: -1.3rem;
  left: 50%;
  transform: translateX(-50%);
  color: #94a3b8;
  font-size: 1rem;
}

.flow-card:last-child::after {
  display: none;
}

.flow-card h4 {
  margin: 0 0 0.5rem 0;
  font-size: 0.8rem;
}

.flow-card p, a {
  margin: 0;
  color: #475569;
  line-height: 1.6;
  font-size: 0.8rem;
}

.flow-card a:hover {
  margin: 0;
  color: #740574;
  transition: none;
}


.blue-card {
  border-left: 5px solid #002A41;
}

.green-card {
  border-left: 5px solid #740574;
}

.meeting-boxes {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.75rem;
  margin-top: 1rem;
}




.meeting-box strong {
  display: block;
  margin-bottom: 0.25rem;
  color: #17365d;
}

.deadline-card {
  background: linear-gradient(135deg, #17365d, #1d4ed8);
  color: white;
  border-radius: 18px;
  padding: 1rem;
  text-align: center;
  margin-top: 1rem;
}

.deadline-card h3 {
  margin: 0 0 0.5rem 0;
  font-size: 0.9rem;
}

.deadline-card p {
  margin: 0;
  font-size: 0.9rem;
  font-weight: 700;
}

.connector {
  position: absolute;
  left: 50%;
  top: 67%;
  width: 180px;
  transform: translateX(-50%);
  z-index: 5;
}

.connector-line {
  border-top: 3px dashed #2f9e44;
  position: relative;
}

.connector-line::after {
  content: "➜";
  position: absolute;
  right: -12px;
  top: -14px;
  color: #1d4ed8;
  font-size: 1.5rem;
}

.connector-text {
  background: white;
  border: 1px solid #dbe4ee;
  border-radius: 12px;
  padding: 0.75rem;
  margin-top: 0.75rem;
  font-size: 0.85rem;
  text-align: center;
  color: #475569;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}

.review-section {
  margin-top: 2.5rem;
  background: #f3f0ff;
  border: 1px solid #ddd6fe;
  border-radius: 18px;
  padding: 0.8rem;
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 2rem;
}

.review-section h4 {
  margin-top: 0;
  margin-bottom: 0.5rem;
   font-size: 0.8rem;
}

.review-section p {
  margin: 0;
  line-height: 1.7;
  color: #475569;
  font-size: 0.8rem;
}

.footer-note {
  margin-top: 2rem;
  border: 2px dashed #c4b5fd;
  border-radius: 14px;
  padding: 1rem;
  text-align: center;
  color: #6d28d9;
  font-weight: 500;
}

@media (max-width: 900px) {

  .diagram-grid {
    grid-template-columns: 1fr;
  }

  .meeting-boxes {
    grid-template-columns: 1fr;
  }

  .review-section {
    grid-template-columns: 1fr;
  }

  .connector {
    position: static;
    transform: none;
    width: 100%;
    margin: 0.5rem 0 1rem 0;
  }

  .connector-line {
    display: none;
  }
}

.wp-columns {
  display: grid;
grid-template-columns: repeat(4, minmax(100px, 1fr));
  gap: 18px;             
  width: 100%;
  max-width: 1500px;      
  margin: 0 auto;
  padding: 8px;
  transform-origin: top center;
  align-items: stretch;
}

@media (max-width: 600px) {
  .wp-columns {
    grid-template-columns: repeat(4, 1fr);
  }
  
  
  .expand-collapse-btn{
  display:none;
  }
}


@media (max-width: 1100px) {
  .wp-columns {
    grid-template-columns: 1fr;
  }
}


@media (max-width: 1100px) {
  .wp-columns {
    grid-template-columns: 1fr;
  }
}


.wp-column {
  background: #ffffff;
  border-radius: 14px;
  padding: 10px 8px 14px;  
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
  border-top: 4px solid #68246d;
    display: flex;
   flex-direction: column;
    height: 100%;
}




.wp-column-title {
  font-size: 0.9rem;
  font-weight: 700;
  text-align: center;
  padding-bottom: 10px;
  margin-bottom: 20px;
  color: #003d66;
    font-size: 1.15rem;
  margin-bottom: 18px;
   min-height: 60px; 
}

.wp-main-number {
  font-size: 1.55rem;
  font-weight: 700;
  color: #003d66;
 
}

.wp-main-subtitle {
  font-size: 0.7rem;
  font-weight: 500;
  color: #555;
  margin-top: 5px;
  
    line-height: 1.4;
  min-height: calc(1.4em * 2);

  display: -webkit-box;
  -webkit-line-clamp: 2;     
  -webkit-box-orient: vertical;
  overflow: hidden;
}



.wp-subblock {
  border-radius: 8px;
  padding: 10px;
  margin: 14px 0;
  background: #ffffff;
  border: 3px solid #002A41;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}




.wp-subblock-header {
  display: flex;
  gap: 10px;
  align-items: flex-start;
  margin-bottom: 12px;
}

.wp-lead-photo {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  object-fit: cover;
  background-color: #f0f0f0;
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
}

.wp-subblock-text {
  display: flex;
  flex-direction: column;
  
}

.wp-subblocks-wrapper {
  display: grid;
  grid-template-columns: 1fr;
  row-gap: 12px;

  align-items: stretch;
}

.wp-header-wrapper {
  display: grid;
  grid-template-rows: auto 1fr;
  row-gap: 8px;
}


.wp-subtitle {
  font-size: 0.5rem;
  font-weight: 600;
  color: #003d66;
  text-align: center;
    line-height: 1.4;
  min-height: calc(1.4em * 4);

  display: -webkit-box;
  -webkit-line-clamp: 4;      
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.wp-lead {
  font-size: 0.8rem;
  color: #555;
  font-style: italic;
  margin-top: 3px;
}

.wp-content {
  font-size: 0.4rem;
  color: #555;
  font-style: italic;
  margin-top: 3px;
}


.wp-subblocks-wrapper {
  display: grid;
  grid-template-columns: 1fr;
  row-gap: 12px;
}


.kanban {
  display: flex;         
  gap: 12px;              
  margin-top: 8px;
  flex-wrap: wrap;      
    min-height: 110px; /
}

.column {
  background: #ffffff;
  padding: 8px;
  border-radius: 8px;
  flex: 1 1 200px;     
  display: flex;
  flex-direction: column; 
 display: flex;
  flex-direction: column;
  justify-content: flex-start;
}


.column h3 {
  font-size: 0.7rem;
  text-transform: uppercase;
  color: white;
  padding: 5px;
  border-radius: 6px;
  text-align: center;
  margin-bottom: 8px;
}

.open-col h3 { background:#B906B9; }
.progress-col h3 { background:#940594; }
.completed-col h3 { background:#490349; }


.tasks-wrapper {
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex-grow: 1; 
    position: relative;
  display: flex;
  flex-direction: column;
  gap: 6px;
  flex-grow: 1;
  min-height: calc((1.3em * 2 + 14px) * 2); 
}



.extra-task {
  display: none; 
}

.tasks-wrapper.expanded .extra-task {
  display: block; 
}


.empty-task {
  visibility: hidden;
}


.task {
  background:#ffffff;
  border-radius: 6px;
  padding: 7px;
  font-size: 0.7rem;
  margin-bottom: 6px;
  border: 2px solid #EAEAEA;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
  font-weight: 700;
  
}

.task a {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;   
  overflow: hidden;

  line-height: 1.3;
  min-height: calc(1.3em * 2);

  text-decoration: none;
  color: #003d66;
  font-size: 0.6rem;
}

.propose-task {
  margin-top: 10px;
  text-align: center;
  padding: 10px 0;
  color: #ffffff;
}

.propose-task-link {
  display: block;
  padding: 5px;
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: 5px;
  background: #003d66;
  color: #ffffff !important;
  text-decoration: none;
  transition: all 0.2s ease;
}

.propose-task-link:hover {
  background: #CDA3CD !important;
  border-color: #CDA3CD !important;
}



.toggle-tasks {
  margin-top: auto; 
  padding: 4px 8px;
  font-size: 0.7rem;
  cursor: pointer;
  border-radius: 6px;
  background: #003d66;
  color: #fff;
  border: none;
    min-height: 26px;
}
.toggle-tasks:hover {
  background: #68246d;
}





.open-col .task:hover {
  box-shadow: 0 0 10px rgba(185, 6, 185, 0.45);
  border-color: #B906B9;
  background: rgba(185, 6, 185, 0.08);
  transform: translateY(-2px);
}

.open-col .task {

  background: #FDDFFD;
  transform: translateY(-2px);
}

.progress-col .task:hover {
  box-shadow: 0 0 10px rgba(148, 5, 148, 0.45);
  border-color: #940594;
  background: rgba(148, 5, 148, 0.08);
  transform: translateY(-2px);
}

.progress-col .task {
  background: #E9C9E9;
  transform: translateY(-2px);
}


.completed-col .task{
  background: #DED0DE;
  transform: translateY(-2px);
}


.completed-col .task:hover {
  box-shadow: 0 0 10px rgba(73, 3, 73, 0.45);
  border-color: #490349;
  background: rgba(73, 3, 73, 0.08);
  transform: translateY(-2px);
}


.task-filter {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  max-width: 1500px;
  margin: 1.2rem auto;
}


.filter-group {
  display: flex;
  gap: 12px;
}



.wp-btn {
  background: #f8fafc;
  border: 1px solid #dbe4ee;
  border-radius: 12px;
  padding: 0.5rem;
  text-align: center;
  font-size: 0.8rem;
}

.wp-btn:hover {
  background: #f8fafc;
  border: 1px solid #740574;
  color: #740574;
  box-shadow: 0 4px 12px rgba(0,0,0,0.05);
}

.wp-btn.active {
  background: #003d66;
  color: white;
}





.filter-btn {
  padding: 6px 14px;
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: 20px;
  border: 2px solid #003d66;
  background: white;
  color: #003d66;
  cursor: pointer;
  transition: all 0.2s ease;
}

.filter-btn:hover {
  background: #003d66;
  color: white;
}

.filter-btn.active {
  background: #003d66;
  color: white;
}


.expand-collapse-btn {

  padding: 6px 14px;
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: 20px;
  border: 2px solid #68246d;
  background: white;
  color: #68246d;
  cursor: pointer;
  transition: all 0.2s ease;
    position: absolute;
  left: 0.5rem;
}



.expand-collapse-btn:hover {
  background: #68246d;
  color: white;
}

.expand-collapse-btn.active {
  background: #68246d;
  color: white;
}



.no-tasks-message {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  width: 90%;
  font-size: 0.6rem;
  color: #666;
  font-style: italic;
  text-align: center;
  line-height: 1.4;
  pointer-events: none; 
}


.wp-suggest-task {
  text-align: center;
  margin-bottom: 12px;
}

.wp-suggest-task a {
  display: inline-block;
  padding: 5px 12px;
  font-size: 0.65rem;
  font-weight: 600;
  border-radius: 14px;
  border: 2px dashed #68246d;
  color: #68246d;
  text-decoration: none;
  transition: all 0.2s ease;
  background: #faf5fb;
}

.wp-suggest-task a:hover {
  background: #68246d;
  color: white;
  border-color: #68246d;
}


.eligibility-box {
  max-width: 1400px;
  margin: 2rem auto 1rem;
  padding: 16px 18px;
  border-radius: 14px;

  background: linear-gradient(135deg, #FDF6FF, #f7f9fc);
  border: 2px solid #F0DEF5;
  box-shadow: 0 6px 18px rgba(0,0,0,0.05);

  display: grid;
  grid-template-columns: auto 1fr;
  gap: 14px;

  font-size: 0.75rem;
  color: #002A41;
  line-height: 1.45;
}

.eligibility-icon {
  font-size: 1.6rem;
  line-height: 1;
  margin-top: 2px;
}

.eligibility-box strong {
  font-weight: 700;
}

.eligibility-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  margin-top: 10px;
 align-items: stretch;
}

.eligibility-pill {
  padding: 4px 10px;
  border: 1px solid #68246d;
  border-radius: 999px;
  font-size: 0.65rem;
  font-weight: 600;
  background: #faf5fb;
  border: 1px solid #003d66;
  color: #940594;
}

.eligibility-pill:hover {
  border-color: #490349;
  background: #FEECFE;
  transform: translateY(-2px);
}

.eligibility-pill a{
  color: #940594;
}

.collapsible-diagram {
  margin: 2rem 0;

}

.collapsible-diagram summary {
  padding: 6px 14px;
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: 20px;
  border: 2px solid #003d66;
  background: white;
  color: #003d66;
  cursor: pointer;
  transition: all 0.2s ease;
  max-width: 400px;
    margin: auto auto;
    text-align: center;
}

.collapsible-diagram summary:hover {
  background: #1d4ed8;
  color: #ffffff;
}

.collapsible-diagram summary::-webkit-details-marker {
  display: none;
}

.collapsible-content {
  margin-top: 1.5rem;
}



.funding-banner {
  background: linear-gradient(90deg, #68246d, #940594);
  color: white;
  text-align: center;
  padding: 12px 18px;
  font-size: 0.95rem;
  font-weight: 500;
  position: relative;
  z-index: 20;
   width: 100vw;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
  margin-top: 0rem !important;
}

.funding-banner a {
  color: white;
  font-weight: 700;
  margin-left: 10px;
  text-decoration: underline;
}

.funding-banner a:hover {
  opacity: 0.85;
}

@keyframes scroll-banner {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}



body.filter-open .progress-col,
body.filter-open .completed-col {
  display: none;
}

body.filter-progress .open-col,
body.filter-progress .completed-col {
  display: none;
}

body.filter-completed .open-col,
body.filter-completed .progress-col {
  display: none;
}

</style>

<!---
<div class="funding-banner">
  📢 The call to <strong>Suggest New Tasks</strong> for the next Flexible Fund round is now open until  <strong>22 September</strong>.
</div>
!-->
<details class="collapsible-diagram">

  <summary>
    How SHAREing Flexible Funds Work
  </summary>

<div class="collapsible-content">
  <div class="shareing-diagram">

  <p class="intro">
    SHAREing funds people to carry out solutions to important challenges.
    You can get involved in two ways: <strong> propose a solution </strong> to an existing open task or <strong> suggest a new task</strong>. <br>
  </p>

<div class="diagram-grid">

  <!-- LEFT: SUGGEST A NEW TASK -->
  <div class="diagram-column">

    <div class="column-title green">
      <div class="icon-circle">💡</div>
      SUGGEST A NEW TASK – Call currently open
    </div>

    <div class="flow-card green-card">
      <h4>Suggest a new task</h4>
      <p>
        <a href="https://shareing-dri.github.io/about/suggest-a-task">
          Submit your idea for a new task
        </a>
        that matches one of the Work Package themes <strong> by 22 September </strong>
      </p>
    </div>

    <div class="flow-card green-card">
      <h4>Discussed at open Working Package meetings</h4>
      <p>
        Your suggestion will be discussed at the next open meeting for the relevant Working Package.
      </p>

      <div class="meeting-boxes">

        <a class="wp-btn" href="https://shareing-dri.github.io/events/202609-WP1-webinar/">
          <strong>WP1</strong><br>3pm, 24 Sept 2026
        </a>

        <a class="wp-btn" href="https://shareing-dri.github.io/events/202609-WP2-webinar/">
          <strong>WP2</strong><br>3pm, 25 Sept 2026
        </a>

        <a class="wp-btn" href="https://shareing-dri.github.io/events/202609-WP3-webinar/">
          <strong>WP3</strong><br>3pm, 23 Sept 2026
        </a>

      </div>
    </div>

    <div class="flow-card green-card">
      <h4>Approved?</h4>
      <p>
        If approved, the new task will be added to the map of open tasks on this website.
        You are then welcome to propose a solution to the task.
      </p>
    </div>

  </div>


  <!-- RIGHT: PROPOSE A SOLUTION -->
  <div class="diagram-column">

    <div class="column-title blue">
      <div class="icon-circle">📋</div>
      PROPOSE A SOLUTION TO AN EXISTING OPEN TASK – Will open on 2 October
    </div>

    <div class="flow-card blue-card">
      <p>
        Explore the open tasks across our Working Packages (WP1, WP2, WP3, WP4).
      </p>
    </div>

    <div class="flow-card blue-card">

      <a href="https://shareing-dri.github.io/about/flexible-funds">
        Check our Flexible Fund Guidance
      </a>

    </div>

    <div class="flow-card blue-card">
      <h4>Submit your proposal</h4>
      <p>
        Propose your solution to an existing open task.
      </p>
    </div>

    <div class="deadline-card">
      <h3>Proposal deadline</h3>
      <p>
        This call will open on 2 October and close on 20 November 2026.
      </p>
    </div>

  </div>

</div>


  <!-- REVIEW SECTION -->
  <div class="review-section">

    <div>
      <h4>Review and decision</h4>

      <p>
        All task suggestions and proposals are reviewed through SHAREing’s open governance process and assessed for alignment with SHAREing priorities and UKRI eligibility requirements.
      </p>
    </div>

    <div>
      <h4>Successful proposals</h4>

      <p>
        Approved proposals may be supported and funded through SHAREing Flexible Funds.
      </p>
    </div>

  </div>


 </div>

 </div>
</details>



<div class="task-filter">
  <button class="expand-collapse-btn" id="expandCollapseBtn">
    Collapse all
  </button>

  <div class="filter-group">
    <button class="filter-btn active" data-status="open">Open</button>
    <button class="filter-btn" data-status="progress">In progress</button>
    <button class="filter-btn" data-status="completed">Completed</button>
  </div>
</div>





<div class="wp-columns">

{% assign wp_groups =
  "wp1:wp1.1,wp1.2,wp1.3|
   wp2:wp2.3,wp2.4|
   wp3:wp3.3,wp3.4|
   wp4:wp4.1,wp4.3" | split:"|" %}

{% for group in wp_groups %}

  {% assign parts = group | split:":" %}
  {% assign wp_main = parts[0] | strip %}
  {% assign wp_list = parts[1] | split:"," %}
  {% assign wp_number = wp_main | replace:"wp","" %}


  {% assign wp_filename = "WP" | append: wp_number | append: ".md" %}
  {% assign wp_page = site.workpackages | where:"path", wp_filename | first %}


  {% if wp_page == nil %}
    {% assign wp_page = site.workpackages | where_exp:"p","p.path contains wp_filename" | first %}
  {% endif %}

  {% assign wp_target = "/workpackages/workpackage-" | append: wp_number | append:"/" %}

  <div class="wp-column">


<div class="wp-column-title">
  <a href="{{ wp_target }}">
    <div class="wp-main-number">Work Package {{ wp_number }}</div>
    <div class="wp-main-subtitle">{{ wp_page.title }}</div>
  </a>
</div>

<div class="wp-suggest-task">
  <a href="/about/suggest-a-task">
    + Suggest a new task for this WP
  </a>
</div>




{% assign wp_file = "workpackages-" | append: wp_number | append: "-team-lead" %}
{% assign wp_lead_data = site.data[wp_file] %}

<div class="wp-lead-block" style="display:flex; align-items:center; font-size:0.8rem; gap:12px; background:#FDF6FF; padding:8px 12px; border-radius:10px; border:1px solid #F0DEF5; margin-bottom:12px;">
  <img src="{{ wp_lead_data.lead_photo }}" alt="{{ wp_lead_data.lead-wp }}" style="width:50px; height:50px; border-radius:50%; object-fit:cover;">
  <div style="display:flex; flex-direction:column;">
    <div style="font-weight:600; color:#003d66;">{{ wp_lead_data.lead-wp }}</div>
  </div>
</div>

    

    {% assign wp_file = "workpackages-" | append: wp_number | append: "-team-lead" %}

    {% for wp in wp_list %}

      {% assign meta = site.data[wp_file][wp] %}
      {% assign open = site.tasks | where:"workpackage",wp | where:"status","open" %}
      {% assign progress = site.tasks | where:"workpackage",wp | where:"status","progress" %}
      {% assign completed = site.tasks | where:"workpackage",wp | where:"status","completed" %}


      <div class="wp-subblock">


        <div class="wp-subblock-header">
             <div class="wp-subblock-text">
            <div class="wp-subtitle">{{ meta.title }}</div>
          </div>
        </div>

        <div class="kanban">
        
        
        
        
<div class="column open-col">



<div class="tasks-wrapper">
  {% assign num_to_show = 2 %}

  {% if open.size == 0 %}
    <div class="no-tasks-message">
      There are no current open tasks for this subgroup.
    </div>

    {% for i in (1..num_to_show) %}
      <div class="task empty-task">&nbsp;</div>
    {% endfor %}

  {% else %}

    {% for task in open limit:num_to_show %}
      <div class="task">
        <a href="{{ task.url }}">{{ task.title }}</a>
      </div>
    {% endfor %}

    {% assign extra_tasks = open | slice: num_to_show, open.size %}
    {% for task in extra_tasks %}
      <div class="task extra-task">
        <a href="{{ task.url }}">{{ task.title }}</a>
      </div>
    {% endfor %}

    {% if open.size < num_to_show %}
      {% assign empty_slots = num_to_show | minus: open.size %}
      {% for i in (1..empty_slots) %}
        <div class="task empty-task">&nbsp;</div>
      {% endfor %}
    {% endif %}

  {% endif %}
</div>

  
  
  

{% if open.size > num_to_show %}
  <button class="toggle-tasks">Show more</button>
{% else %}
  <div class="toggle-tasks" style="visibility:hidden;">Show more</div>
{% endif %}

</div>







<div class="column progress-col">
 
 
 
 
<div class="tasks-wrapper">
  {% assign num_to_show = 2 %}

  {% if progress.size == 0 %}
    <div class="no-tasks-message">
      There are no current tasks in progress for this subgroup.
    </div>

    {% for i in (1..num_to_show) %}
      <div class="task empty-task">&nbsp;</div>
    {% endfor %}

  {% else %}

    {% for task in progress limit:num_to_show %}
      <div class="task">
        <a href="{{ task.url }}">{{ task.title }}</a>
      </div>
    {% endfor %}

    {% assign extra_tasks = progress | slice: num_to_show, progress.size %}
    {% for task in extra_tasks %}
      <div class="task extra-task">
        <a href="{{ task.url }}">{{ task.title }}</a>
      </div>
    {% endfor %}

    {% if progress.size < num_to_show %}
      {% assign empty_slots = num_to_show | minus: progress.size %}
      {% for i in (1..empty_slots) %}
        <div class="task empty-task">&nbsp;</div>
      {% endfor %}
    {% endif %}

  {% endif %}
</div>

  
  





  {% if progress.size > num_to_show %}
    <button class="toggle-tasks">Show more</button>
  {% else %}
    <div class="toggle-tasks" style="visibility:hidden;">Show more</div>
  {% endif %}
</div>






<div class="column completed-col">





<div class="tasks-wrapper">
  {% assign num_to_show = 2 %}

  {% if completed.size == 0 %}
    <div class="no-tasks-message">
      There are no current completed tasks for this subgroup.
    </div>

    {% for i in (1..num_to_show) %}
      <div class="task empty-task">&nbsp;</div>
    {% endfor %}

  {% else %}

    {% for task in completed limit:num_to_show %}
      <div class="task">
        <a href="{{ task.url }}">{{ task.title }}</a>
      </div>
    {% endfor %}

    {% assign extra_tasks = completed | slice: num_to_show, completed.size %}
    {% for task in extra_tasks %}
      <div class="task extra-task">
        <a href="{{ task.url }}">{{ task.title }}</a>
      </div>
    {% endfor %}

    {% if completed.size < num_to_show %}
      {% assign empty_slots = num_to_show | minus: completed.size %}
      {% for i in (1..empty_slots) %}
        <div class="task empty-task">&nbsp;</div>
      {% endfor %}
    {% endif %}

  {% endif %}
</div>

  
  
  
  
  
  
  

  {% if completed.size > num_to_show %}
    <button class="toggle-tasks">Show more</button>
  {% else %}
    <div class="toggle-tasks" style="visibility:hidden;">Show more</div>
  {% endif %}
</div>




  </div>

</div>

    {% endfor %}

  </div>

{% endfor %}

</div>






<script>
document.addEventListener("DOMContentLoaded", function() {

  // EXPAND ALL ON FIRST LOAD
  document.querySelectorAll(".tasks-wrapper").forEach(wrapper => {
    wrapper.classList.add("expanded");
  });

  // Update all toggle buttons to "Show less"
  document.querySelectorAll(".toggle-tasks").forEach(button => {
    button.textContent = "Show less";

    button.addEventListener("click", function() {
      const wrapper = this.previousElementSibling;
      wrapper.classList.toggle("expanded");
      this.textContent = wrapper.classList.contains("expanded") 
        ? "Show less" 
        : "Show more";
    });
  });

});
</script>


<script>
document.addEventListener("DOMContentLoaded", function () {

  document.body.classList.add("filter-open");

  document.querySelectorAll(".filter-btn").forEach(btn => {
    btn.addEventListener("click", function () {
      const status = this.dataset.status;


      document.body.classList.remove(
        "filter-open",
        "filter-progress",
        "filter-completed"
      );


      document.body.classList.add(`filter-${status}`);

      document.querySelectorAll(".filter-btn").forEach(b =>
        b.classList.remove("active")
      );
      this.classList.add("active");
    });
  });

});
</script>


<script>
document.addEventListener("DOMContentLoaded", function () {

  const expandBtn = document.getElementById("expandCollapseBtn");

  function getVisibleWrappers() {
    return Array.from(document.querySelectorAll(".tasks-wrapper"))
      .filter(wrapper => {
        const column = wrapper.closest(".column");
        return column && window.getComputedStyle(column).display !== "none";
      });
  }

  function getVisibleToggleButtons() {
    return Array.from(document.querySelectorAll(".toggle-tasks"))
      .filter(btn => {
        const column = btn.closest(".column");
        return column && window.getComputedStyle(column).display !== "none";
      });
  }

  expandBtn.addEventListener("click", function () {

    const wrappers = getVisibleWrappers();
    const toggles = getVisibleToggleButtons();

    if (wrappers.length === 0) return;

    const allExpanded = wrappers.every(wrapper =>
      wrapper.classList.contains("expanded")
    );

    wrappers.forEach(wrapper => {
      wrapper.classList.toggle("expanded", !allExpanded);
    });

    toggles.forEach(btn => {
      btn.textContent = !allExpanded ? "Show less" : "Show more";
    });

    expandBtn.textContent = !allExpanded
      ? "Collapse all"
      : "Expand all";
  });

});
</script>
