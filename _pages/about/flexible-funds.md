---
permalink: /about/flexible-funds
title: "Flexible Fund Guidance"
layout: splash
---

<style>


:root {
  --brand-purple: #68246d;
  --brand-purple-light: #faf7fb;
  --text-dark: #333;
  --text-muted: #555;
  --brand-blue-light:  #EBF3F5;
  --brand-blue: #002A41;
}

.parallax-hero {
  width: 100vw;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
  height: 40vh;
  background-image: url('/assets/images/sc-booth.avif');
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
  background-position: 80% 40%;
}

.parallax-overlay {
  width: 100%;
  height: 100%;
background: linear-gradient(to top, #68246D, rgba(104, 36, 109, 0.45));
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



.parallax-overlay p {
  font-size: 0.8rem;
  margin-top: 1rem;
}




.section {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.section-muted {
  background: var(--brand-purple-light);
  width: 100vw;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
 padding: 2.5rem 0; 
  display: flow-root;
  }
  
  .section-muted-blue {
  background: var(--brand-blue-light);
  width: 100vw;
  margin-left: calc(50% - 50vw);
  margin-right: calc(50% - 50vw);
 padding: 2.5rem 0; 
  display: flow-root;
  }
  
  
  .section-muted-blue .card h3 {
  color: var(--brand-blue);
  margin-bottom: 1rem;
  text-align: center;
}
  
.section h2 {
  color: var(--brand-purple);
  font-size: 2.1rem;
  margin-bottom: 1.5rem;
    margin-top: 0;
  margin-bottom: 1.5rem;
}

.section h5 {
  color: var(--brand-blue);
  font-size: 2.1rem;
  margin-bottom: 1.5rem;
    margin-top: 0;
  margin-bottom: 1.5rem;
}

.section.muted h2 {
  color: var(--brand-purple);
  font-size: 2.1rem;
  margin-bottom: 1.5rem;
   margin-top: 0 !important;
}

.section h5 {
  color: var(--brand-blue);
  font-size: 2.1rem;
  margin-bottom: 1.5rem;
    margin-top: 0;
  margin-bottom: 1.5rem;
}

.section p {
  font-size: 1.05rem;
  line-height: 1.75;
  color: var(--text-dark);
  max-width: 900px;
}

.section b {
  font-size: 1.05rem;
  line-height: 1.75;
  color: var(--brand-blue);
  max-width: 900px;
}

.section-lead {
  font-size: 1.2rem;
  color: var(--text-muted);
  margin-bottom: 2rem;
}





.cards-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;

  max-width: 1100px;
  margin: 0 auto;
  padding: 0 1.5rem;
  box-sizing: border-box;
}



.card {
  background: #fff;
  border-radius: 14px;
  padding: 2rem;
  box-shadow: 0 6px 18px rgba(0,0,0,0.06);
}

.card h3 {
  color: var(--brand-purple);
  margin-bottom: 1rem;
}



.card ul {
  padding-left: 1.2rem;
}

.card li {
  margin-bottom: 0.5rem;
  font-size: 0.95rem;
}

.icon-list {
  margin-top: 1.5rem;
  padding-left: 1.2rem;
}

.icon-list li {
  margin-bottom: 0.6rem;
}


.funding-table {
  border-collapse: collapse;
  margin-top: 2rem;
  font-size: 1.1rem;
    border-radius: 12px;
}

.funding-table th,
.funding-table td {
  padding: 1rem;
  text-align: left;
  vertical-align: top;
  border-bottom: 1px solid #e5e5e5;
  color: var(--brand-blue);
  font-weight: 600;

}

.funding-table th {
  color: var(--brand-blue);
  font-weight: 600;
  background: #ffffff;
}

.funding-table tbody tr:last-child td {
  border-bottom: none;
}


@media (max-width: 1024px) {
  .wp-grid {
    grid-template-columns: repeat(2, 1fr);
    padding: 0 2rem;
  }
}

@media (max-width: 640px) {
  .wp-grid {
    grid-template-columns: 1fr;
    padding: 0 1.5rem;
  }
  
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
  
  
  .wp-grid {
 display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.6rem;           
  margin-top: 1rem;
}


.wp-card a {

  font-size: 0.8rem;
}


.section img {
display: none;

}

  
  .cards-grid {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 2rem;
  padding: 0 10rem;
}


  @media (max-width: 1024px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr);
    justify-content: center;
  }
}

@media (max-width: 640px) {
  .cards-grid {
    grid-template-columns: 1fr;
    justify-content: center;
    padding: 0 1.5rem;
  }
}
  
  
  
}



</style>

<section class="parallax-hero">
  <div class="parallax-overlay">
    <h1>Flexible Fund Guidance</h1>
  </div>
</section>
<br>
<section class="section">
  <p class="section-lead">
    SHAREing is a Skills Hub for Accelerated Research Environments, funded through the UKRI 
Digital Research Infrastructure Programme.
  </p>

  <p>
   This Hub will administer flexible funding for identified work across 4 work packages. 
Individual awards will typically be in the range £5,000 - £50,000, with the total fund across the project at £1.6m.
  </p>
  
  <p>
  For each call, the hub will issue a scope of work and eligibility criteria, based on the 
priorities identified during the term of the work. 
</p>

</section>

<section class="section-muted">
  <div class="section">
    <h2>Funding Categories</h2>
The fund is intended to support activities under the three categories below:
<br><br>
    <div class="cards-grid">
      <div class="card">
        <h3>Pioneer</h3>
        <ul>
          <li>National accelerator assessment service</li>
          <li>Accelerator-focused assessment methodology</li>
          <li>Accelerator testbeds landing page</li>
          <li>Acceleration case studies</li>
        </ul>
      </div>

      <div class="card">
        <h3>Realise</h3>
        <ul>
          <li>Training pathways & offer overview</li>
          <li>Knowledge exchange</li>
          <li>Courses & workshop delivery</li>
          <li>Bi-directional pipeline with MSc and Industry</li>
        </ul>
      </div>

      <div class="card">
        <h3>Lead</h3>
        <ul>
          <li>Network with compute centres</li>
          <li>Liaise with vendors, industry and businesses</li>
          <li>Integrate outcomes into University KPIs</li>
          <li>International Collaborations</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<section class="section">
<br>
<br>
  <h5>Funding Available</h5>

  <p>
   The SHAREing hub is able to support activities up to £2million Full Economic Cost (FEC).
  </p>
    <p>
  The funding will be award at 80% FEC in line with UKRI funding rules, meaning that funds of £1.6million are available.
  </p>
    <p>
   For each project awarded, the lead institution must be willing to provide the remaining 20% FEC and will be accountable for the conduct of the research, the use of public funds and for ensuring proper financial management of grants.
  </p>
    <p>
  UKRI funding categories apply, with these exclusions – equipment and research software 
for desktop/institutional compute will not be funded.
  </p>
    <p>
 Proposals must be led by a contributor based in an 
 <a href="https://www.ukri.org/apply-for-funding/before-you-apply/find-out-if-you-can-apply-for-funding/#contents-list" >institution eligible to receive UKRI funding.</a>
  </p>
    <p>
   All applications will be reviewed and assessed by a panel drawn from the SHAREing Team. Outcomes will be shared and an award agreement issued for successful applications, which must be signed and returned prior to commencement of work/commitment of funds.
  </p>

  <p>
Applications will be assessed based on:
  </p>
  <ul class="icon-list">
    <li>Fit to Hub priorities as outlined in the Task description</li>
    <li>Value for money</li>
    <li> Feasibility to deliver</li>
  </ul>
    <p>
    The maximum expected values for each application are outlined in the table below:
  </p>
<section class="section-muted-blue">
  <div class="section">
<table class="funding-table">
  <thead>
    <tr>
      <th>Example Activity Types</th>
      <th>Indicative number of applications to be supported per call</th>
      <th>Indicative/maximum award budget per application (80% values)
</th>
    </tr>
  </thead>
  
  
  <tbody>
    <tr>
      <td>Workshops, Hackathons, Bootcamps</td>
      <td>4–6</td>
      <td>£5,000</td>
    </tr>
    <tr>
      <td>In-depth assessments of research codes</td>
      <td>Up to 10 case studies</td>
      <td>£25,000</td>
    </tr>
    <tr>
      <td>
       Creation of learning material (preferred e-learning) and development of methodologies/workflows
      </td>
      <td>6–10</td>
      <td>£50,000</td>
    </tr>
  </tbody>
</table>
 </div> 
 </section>
<br>
 
  
    <p>
    Typically work is expected to commence within 2 months of confirmation of funding and 
complete within 5 months of confirmation. This schedule is subject to change due to 
changing project requirement.
  </p>
  
      <p>
Project dates and reporting will be stated in the award agreement, but in all cases, projects awarded under this scheme must be completed and fully invoiced by 28th February 2028.
  </p>
  
  
  
  
</section>

<section class="section-muted">
  <div class="section">
    <h2>Eligibility and Scope</h2>

    <p>
     Eligibility criteria and the scope of work will be announced via our website, which include our standard EDI principles.
    </p>

    <p>
     Bids must be closely aligned to the tasks as outlined in the call specific guidance.
    </p>
    
     <p>
     A long-term vision for SHAREing is that we want tasks to use a consistent methodology and appearance. Performance assessments should use similar methodological building 
blocks, training material similar didactic concepts, machine descriptions provide similar 
content. As we are just about to start, these methodologies are not written down anywhere 
yet - they might not even exist - and guidelines are not available. We hence would like bids in the future to make it clearer what methodology they plan to use, so the write-up of the 
methods itself can benefit from the work done.
    </p>
    
         <p>
For SHAREing, it is absolutely key that all mini projects contribute towards a joint, public body of work, i.e. webpages, public training material, success stories. Some bids could 
have pointed out more clearly how their deliverables will be made public and how they 
contribute towards SHAREing public-facing webpages, for example.
    </p>
    
<p>
If a bid is about knowledge exchange comprising meetings, workshops, etc travel money is 
reasonable and important. Otherwise, SHAREing mini projects cannot fund it. As an 
example, requests for "conference attendance and outreach" is not fundable unless 
explicitly within the scope of the mini project. SHAREing will make explicit support funds 
for such activities available later.
    </p>
    
    
<p>
Events and workshops will always be higher prioritised than individual travel: If a mini 
project has to conduct interviews or brainstorming sessions, we strongly encourage bids to 
think if these could culminate in official SHAREing events hosted at one of the partner 
sites, as these events help to increase SHAREing's visibility. In such a case, travel money 
obviously is available.
 </p>
    
       
  </div>
</section>

<section class="section">
<br>
<br>
  <h5>EDI Principles</h5>

  <p>
Projects should encourage and support inclusive research practices and seek to engage 
underrepresented groups or communities. Following the recommendations of the <a href="https://n8cir.org.uk/documents/140/2022_05_09_recrtuitment_checklist_K3EWMHP.pdf" >N8 CIR EDI Recruitment Checklist.</a>
  </p>

  <ul class="icon-list">
    <li>All work has a generous latest delivery time, but it is up to the project team how this deadline is best met (part-time, full-time, ...)</li>
    <li>Events and meetings organised as part of a Task are to be scheduled on workdays 
only, preferably in the mornings, such that school runs and childcare arrangements 
are not affected.</li>
    <li> All meetings shall be recorded and saved for a brief period of time so people can 
study the content later.</li>
    <li>Work is designed to be completed by RTPs without any micromanagement by senior 
management and academics.</li>
    <li>Constructive feedback on any unsuccessful project bid will be made available and 
project rankings will be published.</li>
    <li> The executive team will work towards short turnaround times to give colleagues 
freedom and security to plan.</li>
    <li> The assessment panel will consist of members from a range of role types and career 
seniority.</li>
  </ul>
</section>



