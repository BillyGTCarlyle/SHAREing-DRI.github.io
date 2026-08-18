---
layout: splash
permalink: /training/external-training-test
classes: wide
---

<section class="page-intro">
    <h1>External Training Catalogue</h1>

    <p>
        Discover external training opportunities in HPC, AI, research software engineering, programming, performance optimisation, and related topics.
    </p>

    <div class="disclaimer">
        <strong>Disclaimer:</strong> This page is a signposting resource created by the SHAREing project. SHAREing support has been used to curate, organise, and present publicly available training opportunities in a searchable format. The courses listed here are provided by third-party organisations and are not funded, delivered, or maintained by SHAREing unless explicitly stated. Course content, availability, schedules, and registration are the responsibility of the individual providers.
    </div>
</section>


<!-- =========================================================
     TRAINING CALENDAR
========================================================= -->



<section class="calendar-section" id="calendar-section">

<div class="calendar-header">

    <div>
        <h2>Training Calendar</h2>

        <div class="calendar-legend">
            <span class="legend-item">
                <span class="legend-colour scheduled-online"></span>
                Scheduled online
            </span>

            <span class="legend-item">
                <span class="legend-colour scheduled-in-person"></span>
                Scheduled in-person
            </span>
            
            <span class="legend-item">
                <span class="legend-colour hybrid"></span>
                Hybrid
            </span>


        </div>
    </div>

    <div class="calendar-controls">
        <button id="prev-month">←</button>
        <span id="calendar-month"></span>
        <button id="next-month">→</button>
    </div>

</div>

    <div id="training-calendar"></div>

</section>

<div class="training-layout">

  <aside id="topic-sidebar">
<div class="sidebar-header">
    <h3>Topics</h3>

    <button id="toggle-topics" class="sidebar-action">
        Collapse all
    </button>
</div>

<ul id="topic-list"></ul>
  </aside>

  <main>

<div class="toolbar">

<input
    id="course-search"
    type="search"
    placeholder="🔍 Search courses..."
    class="search-box"
/>

<div class="training-controls">
    <button id="clear-filters" class="control-button">
        Clear filters
    </button>

    <button id="toggle-calendar" class="control-button">
        📅 Show calendar
    </button>
</div>

</div>

    <div id="training-container">
      Loading courses...
    </div>

  </main>

  <aside id="format-sidebar">
    <h3>Filters</h3>
    <div id="format-filter"></div>
  </aside>

</div>

<button id="back-to-top" aria-label="Back to top">
  ↑
</button>




<style>

/* =========================================================
   CALENDAR LEGEND
========================================================= */

.calendar-legend {
    display: flex;
    align-items: center;
    gap: 1rem;

    margin-top: .5rem;

    font-size: .6rem;
    color: #475569;
}

.legend-item {
    display: flex;
    align-items: center;
    gap: .35rem;
}

.legend-colour {
    width: 12px;
    height: 12px;

    border-radius: 4px;

    display: inline-block;
}

.legend-colour.scheduled-online {
    background: #dcfce7;
    border: 1px solid #86efac;
}

.legend-colour.scheduled-in-person {
    background: #e0f2fe;
    border: 1px solid #7dd3fc;
}

.legend-colour.hybrid {
    background: #fef3c7;
    color: #92400e;
}
/* =========================================================
   TRAINING CALENDAR
========================================================= */

.calendar-toggle-container {
    margin: 1.5rem 0;
}

.calendar-toggle {
    border: 1px solid #d1d5db;
    background: white;

    padding: .7rem 1.2rem;

    border-radius: 999px;

    cursor: pointer;

    font-size: .75rem;
    font-weight: 600;

    color: #0f2a3a;

    transition: .2s ease;
}

.calendar-toggle:hover {
    background: #eef4f8;
    transform: translateY(-1px);
}


/* Calendar hidden by default */

.calendar-section {
    display: none;

    margin: 1.5rem 0 2rem;
    padding: 1.25rem;

    background: #f8fafc;
    border: 1px solid #e5e7eb;
    border-radius: 22px;

    box-shadow: 0 4px 12px rgba(0,0,0,.04);
}

.calendar-section.show {
    display: block;
}


.calendar-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
}

.calendar-header h2 {
    margin: 0;
    color: #0f2a3a;
    font-size: 1rem;
}

.calendar-controls {
    display: flex;
    align-items: center;
    gap: .75rem;
}

.calendar-controls button {
    border: 1px solid #d1d5db;
    background: white;
    width: 34px;
    height: 34px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 1rem;
}

.calendar-controls button:hover {
    background: #eef4f8;
}

#calendar-month {
    min-width: 140px;
    text-align: center;
    font-size: .8rem;
    font-weight: 700;
    color: #0f2a3a;
}

/* =========================================================
   CALENDAR GRID
========================================================= */

.calendar-grid {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    border-top: 1px solid #e5e7eb;
    border-left: 1px solid #e5e7eb;
}

.calendar-day-name {
    padding: .6rem;
    text-align: center;
    font-size: .65rem;
    font-weight: 700;
    color: #475569;
    background: #eef4f8;
    border-right: 1px solid #e5e7eb;
    border-bottom: 1px solid #e5e7eb;
}



.calendar-week {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    grid-column: 1 / -1;
    position: relative;
    min-height: 110px;
}



.calendar-day {
    position: relative;
    min-height: 110px;
    padding: .45rem;
    background: white;
    border-right: 1px solid #e5e7eb;
    border-bottom: 1px solid #e5e7eb;
}

.calendar-day.empty {
    background: #f8fafc;
}


.calendar-date {
    position: relative;
    z-index: 3;
    font-size: .65rem;
    font-weight: 700;
    color: #64748b;
    margin-bottom: .35rem;
}

.calendar-date.today {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
    border-radius: 50%;
    background: #0f2a3a;
    color: white;
}


.calendar-event {
    position: absolute;
    z-index: 2;
    height: 25px;
    padding: .3rem .45rem;
    border-radius: 7px;
    text-decoration: none;
    font-size: .58rem;
    font-weight: 600;
    line-height: 1.2;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    box-sizing: border-box;
    transition:
        transform .15s ease,
        box-shadow .15s ease;
}

.calendar-event:hover {
    transform: translateY(-1px);
    box-shadow: 0 3px 8px rgba(0,0,0,.12);
    z-index: 5;
}


.calendar-event.scheduled-online {
    background: #dcfce7;
    color: #166534;
}

.calendar-event.scheduled-in-person {
    background: #e0f2fe;
    color: #075985;
}

.calendar-event.hybrid{
    background: #fef3c7;
    color: #92400e;
}



.calendar-event.start {
    border-radius: 7px 0 0 7px;
}

.calendar-event.end {
    border-radius: 0 7px 7px 0;
}

.calendar-event.single-day {
    border-radius: 7px;
}




@media (max-width: 900px) {

    .calendar-day,
    .calendar-week {
        min-height: 80px;}

    .calendar-event {
        font-size: .5rem; }

}


@media (max-width: 600px) {

    .calendar-section {
        overflow-x: auto; }

    .calendar-grid {
        min-width: 700px; }

}

/* =========================================================
   PAGE INTRO
========================================================= */

.page-intro {
    margin: 0.8rem 0;
    padding: 0.8rem;
    background: #f8fafc;
    border-left: 5px solid #421456;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0,0,0,.05);
}

.page-intro h1 {
    margin: 0 0 .5rem;
    color: #0f2a3a;
    font-size: 0.8rem;
}

.page-intro p {
    margin: .1rem 0;
    color: #475569;
    font-size: .6rem;
}

.page-intro .disclaimer {
    margin-top: 0.2rem;
    font-size: .6rem;
    color: #334155;
}


.toolbar {
    display: flex;
    gap: 0.75rem;
    align-items: center;

    margin: 1rem 0;
}

.search-box {
    flex: 1;
    padding: .75rem 1rem;
    border: 1px solid #d1d5db;
    border-radius: 999px;
    font-size: .8rem;
    background: white;
    transition: .2s ease;
}

.search-box:focus {
    outline: none;
    border-color: #245f80;
    box-shadow: 0 0 0 3px rgba(36,95,128,.15);
}

.clear-button {
    width: auto;
    margin: 0;
    white-space: nowrap;
    padding: .75rem 1.25rem;
    border: 1px solid #d1d5db;
    border-radius: 999px;
    background: white;
    font-size: .8rem;
    font-weight: 600;
    cursor: pointer;
    transition: .2s ease;
}



.sidebar-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: .75rem;
}

.sidebar-header h3 {
    margin: 0 0 .75rem;
    color: #0f2a3a;
    font-size:0.6rem;
}

.sidebar-action {
    border: none;
    background: none;
    padding: 0;
    font-size: .65rem;
    font-weight: 600;
    color: #245f80;
    cursor: pointer;
}

.sidebar-action:hover {
    text-decoration: underline;
}




.training-card {
    position: relative;
    
}



.card-header {
    padding: 0.6rem 1.2rem 0.6rem 1rem;
    margin-left: -0.6rem;

    display: flex;
    flex-direction: column;
    gap: .4rem;

    background: #243241;

    border-radius: 20px 20px 0 0;
}



/* =========================================================
   BACK TO TOP BUTTON
========================================================= */

#back-to-top {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    width: 52px;
    height: 52px;
    border: none;
    border-radius: 50%;
    background: #0f2a3a;
    color: white;
    font-size: 1.4rem;
    font-weight: bold;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 6px 16px rgba(0,0,0,.2);
    opacity: 0;
    visibility: hidden;
    transform: translateY(10px);

    transition:
        opacity .25s ease,
        transform .25s ease,
        visibility .25s ease;

    z-index: 1000;
}

#back-to-top:hover {
    background: #173d52;
    transform: translateY(-3px);
}

#back-to-top.show {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
}


#format-filter {
    display: flex;
    flex-direction: column;
    gap: .5rem;
    margin-top:1rem;
    margin-bottom:2rem;
}

.training-controls {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    flex-wrap: wrap;
    margin: 1rem 0;
}

.training-controls button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 0.4rem;
    min-height: 42px;
    padding: 0.6rem 1rem;
    border: 1px solid #d0d5da;
    border-radius: 6px;
    background: #fff;
    color: #002a41;
    font-size: 0.95rem;
    font-weight: 500;
    cursor: pointer;
    transition:
        background-color 0.2s ease,
        border-color 0.2s ease,
        box-shadow 0.2s ease;
}

.training-controls button:hover {
    background: #f5f7f9;
    border-color: #002a41;
}

.training-controls button:focus-visible {
    outline: 2px solid #002a41;
    outline-offset: 2px;
}

@media (max-width: 600px) {
    .training-controls {
        flex-direction: column;
        align-items: stretch;
    }
}

.filter-button {

    border:none;
    background:white;
    border:1px solid #e5e7eb;
    padding:.55rem 1rem;
    border-radius:999px;
    cursor:pointer;
    font-size:0.6rem;
    font-weight:600;
    color:#374151;
    transition:.25s ease;
    margint-top: 2rem;

}


.filter-button:hover {

    background:#eef4f8;
    transform:translateY(-2px);

}


.filter-button.active {

    background:#0f2a3a;
    color:white;
    border-color:#0f2a3a;

}

/* =========================================================
   PAGE LAYOUT
========================================================= */

.training-layout {
    display: grid;
    grid-template-columns: 260px minmax(0, 1fr) 220px;
    gap: 1rem;
    align-items: start;
}

.card-content {
    padding: 1rem;
    display: flex;
    flex-direction: column;
    flex: 1;
}

/* =========================================================
   SIDEBAR
========================================================= */
#format-sidebar {
    position: sticky;
    top: 2rem;
    background: #fff;
    border: 1px solid #e5e7eb;
    border-radius: 18px;
    padding: 1.25rem;
    margin-top: 1rem;
    box-shadow: 0 4px 12px rgba(0,0,0,.05);
}

#format-sidebar h3 {
    margin: 0 0 .75rem;
    color: #0f2a3a;
    font-size:0.6rem;
}

#topic-sidebar {

    position: sticky;
    top: 2rem;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 18px;
    padding: 1.25rem;
    margin-top: 1rem;
    box-shadow:
        0 4px 12px rgba(0,0,0,.05);

    max-height: calc(100vh - 4rem);
    display: flex;
    flex-direction: column;
}


#topic-sidebar h3 {

    margin-top:0;
    margin-bottom:0.5rem;
    color:#0f2a3a;
    font-size:0.6rem;

}


#topic-list {

    list-style: none;
    padding: 0;
    margin: 0;
    overflow-y: auto;
    flex: 1;
    min-height: 0;
    padding-right: .3rem;
}

#topic-list::-webkit-scrollbar {
    width: 8px;
}

#topic-list::-webkit-scrollbar-track {
    background: transparent;
}

#topic-list::-webkit-scrollbar-thumb {
    background: #cbd5e1;
    border-radius: 999px;
}

#topic-list::-webkit-scrollbar-thumb:hover {
    background: #94a3b8;
}

#topic-list li {

    margin-bottom:0.05rem;

}


#topic-sidebar details {
    margin-bottom: .4rem;
}

#topic-sidebar summary {
    cursor: pointer;
    font-weight: 700;
    color: #0f2a3a;
    padding: 0.1rem;
    list-style: none;
    font-size: 0.8rem;
}

#topic-sidebar summary::-webkit-details-marker {
    display: none;
}

#topic-sidebar summary::before {
    content: "▸";
    margin-right: .5rem;
    transition: .2s;
}

#topic-sidebar details[open] summary::before {
    content: "▾";
}

.topic-sublist {
    list-style: none;
    padding-left: 1rem;
    margin-top: .3rem;
}


.topic-sublist {
    list-style: none;
    margin: .3rem 0 0;
    padding-left: 1rem;
}

.topic-sublist li {
    margin: .2rem 0;
}

.topic-link {
    display: inline-block;
    padding: .15rem 0;
    color: #4b5563;
    text-decoration: none;
    font-size: .8rem;
    font-weight: 500;
    transition: color .2s ease;
}

.topic-link:hover {
    color: #0f2a3a;
    text-decoration: underline;
    
}

.topic-link.active {
    color: #245f80;
    font-weight: 700;
}

/* =========================================================
   TOPIC SECTIONS
========================================================= */

.training-topic {

    margin-bottom:1rem;
    padding:1rem;
    border-radius:22px;
    background:#f8fafc;
    border:1px solid #e5e7eb;
    scroll-margin-top:2rem;

}


.training-topic h2 {

    margin-top:0;
    margin-bottom:0.3rem;
    color:#0f2a3a;
        border-bottom: none;
    font-size:1rem;

}



/* =========================================================
   COURSE GRID
========================================================= */

.training-grid {

    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: .5rem;
    align-items: stretch;
}


@media (max-width: 900px) {
    .training-grid {
        grid-template-columns: 1fr;
    }
}

.training-group {
    margin-bottom: 2.5rem;
}

.training-group > h1 {
    font-size: 1.5rem;
    color: #0f2a3a;
    margin-bottom: 1rem;
    border-bottom: 2px solid #dbe5ec;
    padding-bottom: .4rem;
}





/* =========================================================
   COURSE CARDS
========================================================= */

.course-dates {
    margin-top: -.5rem;
    margin-bottom: .8rem;
    color: #475569;
    font-size: .65rem;
    font-weight: 600;
    line-height: 1.4;
}

.course-location {
    margin-top: -.5rem;
    margin-bottom: .8rem;
    color: #475569;
    font-size: .65rem;
    font-weight: 600;
    line-height: 1.4;
}


/* =========================================================
   MODERN COURSE CARDS
========================================================= */

.training-card {
    position: relative;
    display: flex;
    flex-direction: column;
    min-height: 250px;
    overflow: hidden;
    background: #ffffff;
    border: 1px solid #e2e8f0;
    border-radius: 18px;
    box-shadow:
        0 2px 4px rgba(15, 42, 58, .03),
        0 8px 20px rgba(15, 42, 58, .05);

    transition:
        transform .2s ease,
        box-shadow .2s ease,
        border-color .2s ease;
}

.training-card:hover {
    transform: translateY(-4px);
    border-color: #cbd5e1;
    box-shadow:
        0 6px 12px rgba(15, 42, 58, .06),
        0 14px 30px rgba(15, 42, 58, .09);
}


/* =========================================================
   CARD HEADER
========================================================= */

.card-header {
    position: relative;
    padding: 1rem 1rem .7rem;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #ffffff;
    border-radius: 18px 18px 0 0;
}


/* Organisation */
/* =========================================================
   CARD HEADER
========================================================= */

.card-header {
    padding: 1rem 1rem .7rem;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    gap: .45rem;
    background: #ffffff;
    border-radius: 18px 18px 0 0;
}


/* =========================================================
   ORGANISATION BADGE
========================================================= */

.card-badge {
    display: inline-flex;
    align-items: center;
    width: fit-content;
    padding: .3rem .6rem;
    border-radius: 999px;
    background: #f3e8f5;
    color: #67136d;
    font-size: .58rem;
    font-weight: 700;
    line-height: 1.2;
}



/* =========================================================
   CARD CONTENT
========================================================= */

.card-content {
    padding: .5rem 1rem 1rem;
    display: flex;
    flex-direction: column;
    flex: 1;
}


/* Course title */

.training-card h4 {
    margin: .2rem 0 1rem;
    color: #0f2a3a;
    font-size: .78rem;
    line-height: 1.45;
    font-weight: 700;
}


/* =========================================================
   COURSE INFORMATION
========================================================= */

.course-dates,
.course-location {
    display: flex;
    align-items: flex-start;
    margin: 0 0 .45rem;
    color: #64748b;
    font-size: .62rem;
    font-weight: 600;
    line-height: 1.45;
}


/* =========================================================
   CARD FOOTER
========================================================= */

.card-footer {
    margin-top: auto;
    padding: 0;
    background: transparent;
    border-radius: 0;
    display: flex;
    justify-content: stretch;
}

.card-footer:hover {
    background: transparent;
}


/* View course button */

.card-button {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: .75rem 1rem;
    color: #ffffff;
    background: #0f2a3a;
    text-decoration: none;
    text-align: left;
    font-size: .65rem;
    font-weight: 700;
    border-radius: 0 0 17px 17px;
    transition:
        background .2s ease,
        padding .2s ease;
}

.card-button::after {
    content: "→";
    font-size: .85rem;
    transition: transform .2s ease;
}

.card-button:hover {
    color: #ffffff;
    background: #245f80;
    padding-left: 1.15rem;
}

.card-button:hover::after {
    transform: translateX(3px);
}


/* =========================================================
   ORGANISATION BADGE
========================================================= */

.card-badge {
    display: inline-flex;
    width: fit-content;
    padding: .25rem .6rem;
    border-radius: 8px;
    background: #f3e8f5;
    color: #67136d;
    font-size: .65rem;
    font-weight: 700;
}

/* =========================================================
   FORMAT PILLS
========================================================= */

.format-pill {
    display: inline-flex;
    align-items: center;
    gap: .3rem;
    width: fit-content;
    padding: .25rem .65rem;
    border-radius: 999px;
    font-size: .65rem;
    font-weight: 700;
    line-height: 1.2;
}


/* self-paced */

.format-on-demand {
    background: #e0f2fe;
    color: #075985;
}


/* fixed date courses */

.format-scheduled-online {
    background: #dcfce7;
    color: #166534;
}

.format-scheduled-in-person {
    background: #dcfce7;
    color: #166534;
}


/* dates unknown */

.format-upcoming {
    background: #fef3c7;
    color: #92400e;
}



/* =========================================================
   COURSE TITLE
========================================================= */

.training-card h4 {

    margin:0 0 1rem 0;
    color:#0f2a3a;
    font-size:0.7rem;
    line-height:1.4;
    font-weight:700;

}

/* =========================================================
   RESPONSIVE
========================================================= */

@media(max-width:900px){

    .training-layout {
        grid-template-columns:1fr;
    }

    #topic-sidebar {
        position:relative;
        top:0;
    }

}



</style>


<script>

const courses = {{ site.data["external-training"] | jsonify }};


// =============================================================================
// CONFIGURATION
// =============================================================================

const formatInfo = {
    "Online (self-service)": {
        label: "On-demand",
        icon: "📚",
        class: "format-on-demand"
    },

    "Scheduled (online)": {
        label: "Scheduled (online)",
        icon: "📅",
        class: "format-scheduled-online"
    },

    "Scheduled (hybrid)": {
        label: "Hybrid",
        icon: "📅",
        class: "format-scheduled-hybrid"
    },

    "Scheduled (in-person)": {
        label: "Scheduled (in-person)",
        icon: "📅",
        class: "format-scheduled-in-person"
    },

    "Upcoming": {
        label: "Upcoming",
        icon: "⏳",
        class: "format-upcoming"
    },

    "Other": {
        label: "Other",
        icon: "🎉",
        class: "format-other"
    }
};


const topicGroups = {
    "Languages 💬": [
        "Fortran",
        "C++",
        "Julia",
        "Python"
    ],

    "Parallelism 🔀": [
        "OpenMP",
        "MPI"
    ],

    "GPU 🎮": [
        "OpenMP offload",
        "OpenACC",
        "CUDA",
        "HIP"
    ],

    "Performance 📊": [
        "Performance Engineering",
        "Performance Analysis",
        "Tools"
    ],

    "Other 📦": [
        "Containers",
        "Professional Skills"
    ],

    "Community 🎉": [
        "Seminar",
        "Community"
    ]
};


// =============================================================================
// DOM ELEMENTS
// =============================================================================

const sidebar = document.getElementById("topic-list");
const container = document.getElementById("training-container");
const filterContainer = document.getElementById("format-filter");

const searchBox = document.getElementById("course-search");
const clearButton = document.getElementById("clear-filters");

const toggleButton = document.getElementById("toggle-topics");
const backToTop = document.getElementById("back-to-top");


// Calendar elements
const calendarContainer = document.getElementById("training-calendar");
const calendarMonth = document.getElementById("calendar-month");
const prevMonthButton = document.getElementById("prev-month");
const nextMonthButton = document.getElementById("next-month");
const calendarSection = document.getElementById("calendar-section");
const toggleCalendarButton = document.getElementById("toggle-calendar");


// =============================================================================
// STATE
// =============================================================================

let activeFormatFilter = "all";
let searchTerm = "";
let calendarDate = new Date();


// =============================================================================
// TOPIC GROUPS
// =============================================================================

// Find all topics already assigned to a group.
const knownTopics = new Set(
    Object.values(topicGroups).flat()
);


// Find tags that are not currently assigned to a group.
const extraTopics = new Set();

courses.forEach(course => {

    if (!course.tags) {
        return;
    }

    course.tags
        .split(",")
        .map(tag => tag.trim())
        .filter(Boolean)
        .forEach(tag => {

            if (!knownTopics.has(tag)) {
                extraTopics.add(tag);
            }

        });

});


// Add previously unknown topics to Other.
topicGroups["Other 📦"].push(
    ...Array.from(extraTopics).sort()
);


// =============================================================================
// GROUP COURSES BY TOPIC
// =============================================================================

const groupedCourses = {};

courses.forEach(course => {

    const topics = course.tags
        ? course.tags
            .split(",")
            .map(tag => tag.trim())
            .filter(Boolean)
        : [];

    topics.forEach(topic => {

        if (!groupedCourses[topic]) {
            groupedCourses[topic] = [];
        }

        groupedCourses[topic].push(course);

    });

});


// =============================================================================
// BUILD SIDEBAR
// =============================================================================

function buildSidebar() {

    sidebar.innerHTML = "";

    Object.entries(topicGroups).forEach(([groupName, topics]) => {

        const availableTopics = topics.filter(
            topic => groupedCourses[topic]
        );

        if (!availableTopics.length) {
            return;
        }


        const details = document.createElement("details");

        details.open = true;

        details.innerHTML = `
            <summary>${groupName}</summary>
            <ul class="topic-sublist"></ul>
        `;


        const sublist = details.querySelector(".topic-sublist");


        availableTopics.forEach(topic => {

            const id = topicToId(topic);

            const li = document.createElement("li");

            li.dataset.topic = id;

            li.innerHTML = `
                <a
                    class="topic-link"
                    href="#${id}"
                    data-topic="${id}"
                >
                    <span>${topic}</span>
                </a>
            `;

            sublist.appendChild(li);

        });


        sidebar.appendChild(details);

    });

}


// =============================================================================
// TOPIC ID HELPER
// =============================================================================

function topicToId(topic) {

    return topic
        .trim()
        .toLowerCase()
        .replace(/\s+/g, "-")
        .replace(/[^\w-]/g, "");

}


// =============================================================================
// BUILD TRAINING SECTIONS
// =============================================================================

function buildTrainingSections() {

    container.innerHTML = "";


    Object.keys(groupedCourses)
        .sort()
        .forEach(topic => {

            const id = topicToId(topic);

            const section = document.createElement("section");

            section.className = "training-topic";
            section.id = id;


            section.innerHTML = `
                <h2>${topic}</h2>
                <div class="training-grid"></div>
            `;


            const grid =
                section.querySelector(".training-grid");


            groupedCourses[topic].forEach(course => {

                const card =
                    document.createElement("div");

                card.className = "training-card";


                const format =
                    formatInfo[course.format] || {
                        label: course.format || "Other",
                        icon: "📚",
                        class: ""
                    };


                card.dataset.format = course.format || "";
                card.dataset.title =
                    (course.title || "").toLowerCase();


                let courseDetails = "";


                // -------------------------------------------------------------
                // Scheduled online
                // -------------------------------------------------------------

                if (
                    course.format === "Scheduled (online)" &&
                    course.dates
                ) {

                    courseDetails = `
                        <div class="course-dates">
                            📅 ${course.dates}
                        </div>

                        <div class="course-location">
                            📍 Online
                        </div>
                    `;

                }


                // -------------------------------------------------------------
                // Scheduled hybrid
                // -------------------------------------------------------------

                else if (
                    course.format === "Scheduled (hybrid)" &&
                    course.dates
                ) {

                    courseDetails = `
                        <div class="course-dates">
                            📅 ${course.dates}
                        </div>

                        <div class="course-location">
                            📍 ${
                                course.location
                                    ? `Online/${course.location}`
                                    : "Online"
                            }
                        </div>
                    `;

                }


                // -------------------------------------------------------------
                // Scheduled in-person
                // -------------------------------------------------------------

                else if (
                    course.format === "Scheduled (in-person)" &&
                    course.dates
                ) {

                    courseDetails = `
                        <div class="course-dates">
                            📅 ${course.dates}
                        </div>

                        ${
                            course.location
                                ? `
                                    <div class="course-location">
                                        📍 ${course.location}
                                    </div>
                                  `
                                : ""
                        }
                    `;

                }


                // -------------------------------------------------------------
                // On-demand
                // -------------------------------------------------------------

                else if (
                    course.format === "Online (self-service)"
                ) {

                    courseDetails = `
                        <div class="course-dates">
                            📚 On-demand
                        </div>
                    `;

                }


                // -------------------------------------------------------------
                // Upcoming
                // -------------------------------------------------------------

                else if (
                    course.format === "Upcoming"
                ) {

                    courseDetails = `
                        <div class="course-dates">
                            ⏳ Upcoming, yet to be scheduled
                        </div>
                    `;

                }


                // -------------------------------------------------------------
                // Card HTML
                // -------------------------------------------------------------

                card.innerHTML = `

                    <div class="card-header">

                        <span class="card-badge">
                            ${course.organisation || ""}
                        </span>

                    </div>


                    <div class="card-content">

                        <h4>
                            ${course.title || ""}
                        </h4>

                        ${courseDetails}

                    </div>


                    <div class="card-footer">

                        <a
                            href="${course.url || "#"}"
                            class="card-button"
                            target="_blank"
                            rel="noopener"
                        >
                            View course
                        </a>

                    </div>

                `;


                grid.appendChild(card);

            });


            container.appendChild(section);

        });

}


// =============================================================================
// FORMAT FILTERS
// =============================================================================

const formatFilters = [
    {
        id: "all",
        label: "🌐 All"
    },
    {
        id: "Online (self-service)",
        label: "📚 On-demand"
    },
    {
        id: "Scheduled (online)",
        label: "📅 Scheduled (Online)"
    },
    {
        id: "Scheduled (hybrid)",
        label: "📅 Scheduled (Hybrid)"
    },
    {
        id: "Scheduled (in-person)",
        label: "📅 Scheduled (In-person)"
    },
    {
        id: "Upcoming",
        label: "⏳ Upcoming"
    },
    {
        id: "Other",
        label: "🎉 Other"
    }
];


function buildFormatFilters() {

    filterContainer.innerHTML = "";


    formatFilters.forEach(filter => {

        const button =
            document.createElement("button");

        button.type = "button";

        button.className = "filter-button";

        button.textContent = filter.label;

        button.dataset.filter = filter.id;


        if (filter.id === "all") {
            button.classList.add("active");
        }


        button.addEventListener("click", () => {

            activeFormatFilter = filter.id;


            document
                .querySelectorAll(".filter-button")
                .forEach(btn => {
                    btn.classList.toggle(
                        "active",
                        btn.dataset.filter === activeFormatFilter
                    );
                });


            applyFilters();

        });


        filterContainer.appendChild(button);

    });

}


// =============================================================================
// APPLY FILTERS
// =============================================================================

function applyFilters() {

    document
        .querySelectorAll(".training-card")
        .forEach(card => {

            const cardFormat =
                card.dataset.format;

            const cardTitle =
                card.dataset.title;


            const matchesFormat =
                activeFormatFilter === "all" ||
                cardFormat === activeFormatFilter;


            const matchesSearch =
                cardTitle.includes(searchTerm);


            card.style.display =
                matchesFormat && matchesSearch
                    ? "flex"
                    : "none";

        });


    // -------------------------------------------------------------------------
    // Show/hide topic sections
    // -------------------------------------------------------------------------

    document
        .querySelectorAll(".training-topic")
        .forEach(section => {

            const visibleCards =
                section.querySelectorAll(
                    ".training-card:not([style*='display: none'])"
                );


            section.style.display =
                visibleCards.length
                    ? ""
                    : "none";

        });


    // -------------------------------------------------------------------------
    // Show/hide sidebar topics
    // -------------------------------------------------------------------------

    document
        .querySelectorAll("#topic-list li")
        .forEach(li => {

            const section =
                document.getElementById(li.dataset.topic);


            li.style.display =
                section && section.style.display !== "none"
                    ? ""
                    : "none";

        });


    // -------------------------------------------------------------------------
    // Show/hide empty sidebar groups
    // -------------------------------------------------------------------------

    document
        .querySelectorAll("#topic-list details")
        .forEach(details => {

            const visibleTopics =
                details.querySelectorAll(
                    "li:not([style*='display: none'])"
                );


            details.style.display =
                visibleTopics.length
                    ? ""
                    : "none";

        });

}


// =============================================================================
// TOPIC SCROLL SPY
// =============================================================================

function initialiseTopicObserver() {

    const observer =
        new IntersectionObserver(
            entries => {

                entries.forEach(entry => {

                    if (!entry.isIntersecting) {
                        return;
                    }


                    const currentId =
                        entry.target.id;


                    document
                        .querySelectorAll(".topic-link")
                        .forEach(link => {

                            link.classList.toggle(
                                "active",
                                link.dataset.topic === currentId
                            );

                        });

                });

            },
            {
                root: null,
                rootMargin: "-30% 0px -60% 0px",
                threshold: 0
            }
        );


    document
        .querySelectorAll(".training-topic")
        .forEach(section => {

            observer.observe(section);

        });


    const firstLink =
        document.querySelector(".topic-link");


    if (firstLink) {
        firstLink.classList.add("active");
    }

}


// =============================================================================
// CALENDAR — DATE PARSING
// =============================================================================

function parseCourseDate(dateString) {

    if (!dateString) {
        return null;
    }


    const match = dateString.match(
        /(\d{1,2})(?:[–-](\d{1,2}))?\s+([A-Za-z]+)\s+(\d{4})/
    );


    if (!match) {
        return null;
    }


    const startDay =
        parseInt(match[1], 10);

    const endDay =
        match[2]
            ? parseInt(match[2], 10)
            : startDay;

    const monthName =
        match[3];

    const year =
        parseInt(match[4], 10);


    const monthIndex =
        new Date(
            `${monthName} 1, ${year}`
        ).getMonth();


    if (Number.isNaN(monthIndex)) {
        return null;
    }


    const start =
        new Date(
            year,
            monthIndex,
            startDay
        );


    const end =
        new Date(
            year,
            monthIndex,
            endDay
        );


    start.setHours(0, 0, 0, 0);

    end.setHours(23, 59, 59, 999);


    return {
        start,
        end
    };

}


// =============================================================================
// CALENDAR — DATE HELPERS
// =============================================================================

function dateKey(date) {

    return [
        date.getFullYear(),
        date.getMonth(),
        date.getDate()
    ].join("-");

}


function isSameDay(date1, date2) {

    return (
        date1.getFullYear() === date2.getFullYear() &&
        date1.getMonth() === date2.getMonth() &&
        date1.getDate() === date2.getDate()
    );

}


// Monday = 0, Sunday = 6
function getWeekday(date) {

    return (date.getDay() + 6) % 7;

}


// =============================================================================
// CALENDAR — GET SCHEDULED COURSES
// =============================================================================

function getScheduledCourses() {

    return courses
        .filter(course => {

            return (
                course.dates &&
                [
                    "Scheduled (online)",
                    "Hybrid",
                    "Scheduled (in-person)"
                ].includes(course.format)
            );

        })
        .map(course => {

            const parsed =
                parseCourseDate(course.dates);


            if (!parsed) {
                return null;
            }


            return {
                ...course,
                start: parsed.start,
                end: parsed.end
            };

        })
        .filter(Boolean);

}


// =============================================================================
// CALENDAR — EVENT CLASS
// =============================================================================

function getCalendarEventClass(course) {

    switch (course.format) {

        case "Scheduled (in-person)":
            return "scheduled-in-person";

        case "Hybrid":
            return "hybrid";

        default:
            return "scheduled-online";

    }

}


// =============================================================================
// CALENDAR — RENDER
// =============================================================================

function renderCalendar() {

    if (!calendarContainer) {
        return;
    }


    const year =
        calendarDate.getFullYear();

    const month =
        calendarDate.getMonth();


    calendarMonth.textContent =
        new Intl.DateTimeFormat(
            "en-GB",
            {
                month: "long",
                year: "numeric"
            }
        ).format(calendarDate);


    const firstDay =
        new Date(year, month, 1);

    const lastDay =
        new Date(year, month + 1, 0);


    const firstWeekday =
        getWeekday(firstDay);

    const daysInMonth =
        lastDay.getDate();


    const numberOfWeeks =
        Math.ceil(
            (firstWeekday + daysInMonth) / 7
        );


    const scheduledCourses =
        getScheduledCourses();


    const today =
        new Date();

    today.setHours(0, 0, 0, 0);


    let html = `

        <div class="calendar-grid">

            <div class="calendar-day-name">Mon</div>
            <div class="calendar-day-name">Tue</div>
            <div class="calendar-day-name">Wed</div>
            <div class="calendar-day-name">Thu</div>
            <div class="calendar-day-name">Fri</div>
            <div class="calendar-day-name">Sat</div>
            <div class="calendar-day-name">Sun</div>

    `;


    // =========================================================================
    // WEEKS
    // =========================================================================

    for (
        let week = 0;
        week < numberOfWeeks;
        week++
    ) {

        const weekStart =
            new Date(
                year,
                month,
                1 - firstWeekday + week * 7
            );


        weekStart.setHours(0, 0, 0, 0);


        const weekEnd =
            new Date(weekStart);


        weekEnd.setDate(
            weekEnd.getDate() + 6
        );


        weekEnd.setHours(
            23,
            59,
            59,
            999
        );


        const weekCourses =
            scheduledCourses
                .filter(course =>
                    course.end >= weekStart &&
                    course.start <= weekEnd
                )
                .sort((a, b) =>
                    a.start - b.start
                );


        // ---------------------------------------------------------------------
        // Assign overlap lanes
        // ---------------------------------------------------------------------

        const lanes = [];


        weekCourses.forEach(course => {

            let lane = 0;


            while (
                lanes[lane] &&
                lanes[lane].end >= course.start
            ) {

                lane++;

            }


            course._calendarLane = lane;

            lanes[lane] = course;

        });


        // ---------------------------------------------------------------------
        // Week height
        // ---------------------------------------------------------------------

        const eventHeight = 25;
        const eventGap = 4;
        const eventTop = 38;


        const weekHeight =
            Math.max(
                110,
                eventTop +
                lanes.length *
                (eventHeight + eventGap) +
                10
            );


        html += `
            <div
                class="calendar-week"
                style="min-height: ${weekHeight}px;"
            >
        `;


        // =====================================================================
        // DAY CELLS
        // =====================================================================

        for (
            let weekday = 0;
            weekday < 7;
            weekday++
        ) {

            const dayNumber =
                week * 7 +
                weekday -
                firstWeekday +
                1;


            if (
                dayNumber < 1 ||
                dayNumber > daysInMonth
            ) {

                html += `
                    <div class="calendar-day empty"></div>
                `;

                continue;

            }


            const currentDate =
                new Date(
                    year,
                    month,
                    dayNumber
                );


            currentDate.setHours(
                0,
                0,
                0,
                0
            );


            const todayClass =
                isSameDay(
                    currentDate,
                    today
                )
                    ? "today"
                    : "";


            html += `
                <div
                    class="calendar-day"
                    data-date="${dateKey(currentDate)}"
                >

                    <div class="calendar-date ${todayClass}">
                        ${dayNumber}
                    </div>

                </div>
            `;

        }


        // =====================================================================
        // COURSE EVENTS
        // =====================================================================

        weekCourses.forEach(course => {

            const eventStart =
                course.start > weekStart
                    ? course.start
                    : weekStart;


            const eventEnd =
                course.end < weekEnd
                    ? course.end
                    : weekEnd;


            let startColumn =
                getWeekday(eventStart);

            let endColumn =
                getWeekday(eventEnd);


            if (course.start < weekStart) {
                startColumn = 0;
            }


            if (course.end > weekEnd) {
                endColumn = 6;
            }


            const span =
                endColumn - startColumn + 1;


            const startsHere =
                isSameDay(
                    course.start,
                    eventStart
                );


            const endsHere =
                isSameDay(
                    course.end,
                    eventEnd
                );


            let eventClass =
                getCalendarEventClass(course);


            if (startsHere && endsHere) {

                eventClass += " single-day";

            } else {

                if (startsHere) {
                    eventClass += " start";
                }

                if (endsHere) {
                    eventClass += " end";
                }

            }


            const left =
                (startColumn / 7) * 100;


            const width =
                (span / 7) * 100;


            const top =
                eventTop +
                course._calendarLane *
                (eventHeight + eventGap);


            html += `
                <a
                    href="${course.url || "#"}"
                    target="_blank"
                    rel="noopener"
                    class="calendar-event ${eventClass}"
                    title="${course.title} — ${course.dates}"
                    style="
                        left: calc(${left}% + .2rem);
                        width: calc(${width}% - .4rem);
                        top: ${top}px;
                    "
                >
                    ${course.title}
                </a>
            `;

        });


        html += `
            </div>
        `;

    }


    html += `
        </div>
    `;


    calendarContainer.innerHTML = html;

}


// =============================================================================
// CALENDAR — CONTROLS
// =============================================================================

if (toggleCalendarButton && calendarSection) {

    toggleCalendarButton.addEventListener(
        "click",
        () => {

            const isVisible =
                calendarSection.classList.toggle("show");


            toggleCalendarButton.textContent =
                isVisible
                    ? "📅 Hide calendar"
                    : "📅 Show calendar";

        }
    );

}


if (prevMonthButton) {

    prevMonthButton.addEventListener(
        "click",
        () => {

            calendarDate.setMonth(
                calendarDate.getMonth() - 1
            );

            renderCalendar();

        }
    );

}


if (nextMonthButton) {

    nextMonthButton.addEventListener(
        "click",
        () => {

            calendarDate.setMonth(
                calendarDate.getMonth() + 1
            );

            renderCalendar();

        }
    );

}


// =============================================================================
// TOPIC CONTROLS
// =============================================================================

if (toggleButton) {

    toggleButton.addEventListener(
        "click",
        () => {

            const details =
                document.querySelectorAll(
                    "#topic-list details"
                );


            const expand =
                [...details].some(
                    details => !details.open
                );


            details.forEach(
                details => {
                    details.open = expand;
                }
            );


            toggleButton.textContent =
                expand
                    ? "Collapse all"
                    : "Expand all";

        }
    );

}


// =============================================================================
// SEARCH
// =============================================================================

if (searchBox) {

    searchBox.addEventListener(
        "input",
        () => {

            searchTerm =
                searchBox.value
                    .trim()
                    .toLowerCase();


            applyFilters();

        }
    );

}


// =============================================================================
// CLEAR FILTERS
// =============================================================================

if (clearButton) {

    clearButton.addEventListener(
        "click",
        () => {

            activeFormatFilter = "all";
            searchTerm = "";


            if (searchBox) {
                searchBox.value = "";
            }


            document
                .querySelectorAll(".filter-button")
                .forEach(button => {

                    button.classList.toggle(
                        "active",
                        button.dataset.filter === "all"
                    );

                });


            applyFilters();


            window.scrollTo({
                top: 0,
                behavior: "smooth"
            });

        }
    );

}


// =============================================================================
// BACK TO TOP
// =============================================================================

if (backToTop) {

    window.addEventListener(
        "scroll",
        () => {

            backToTop.classList.toggle(
                "show",
                window.scrollY > 300
            );

        }
    );


    backToTop.addEventListener(
        "click",
        () => {

            window.scrollTo({
                top: 0,
                behavior: "smooth"
            });

        }
    );

}


// =============================================================================
// INITIALISE
// =============================================================================

buildSidebar();
buildTrainingSections();
buildFormatFilters();
applyFilters();
initialiseTopicObserver();
renderCalendar();

</script>