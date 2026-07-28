---
marp: true
theme: dpdp-theme
paginate: true
header: " "
footer: " "
---

<!-- _class: cover nologo -->

<div class="split-layout" style="align-items: center; justify-content: center; height: 100%;">
  <div class="split-left" style="display: flex; flex-direction: column; justify-content: center;">
    <p class="chapter">DPDP Compliance Series</p>
    <h1>Data Discovery & Consent Management System</h1>
    <h2 style="font-size: 20px; color: var(--dt-gray); font-weight: 500; margin-top: 4px;">DPDP Compliance Dashboard (DDS-CMS)</h2>
    <p style="margin-top: 15px; font-size: 15px; color: var(--dt-gray); font-weight: 400;">Project Overview, Dashboard Workflow & Future Multi-Tenant Architecture</p>
  </div>
  <div class="split-right" style="display: flex; align-items: center; justify-content: center;">
    <img src="images/logo.png" alt="DeepTrustxAI" style="width: 100%; max-width: 320px; border: none; box-shadow: none;" />
  </div>
</div>

<!--
Speaker Notes:
Good morning/afternoon, everyone. Today I am presenting our project: the Data Discovery & Consent Management System, or DDS-CMS. 
This is a comprehensive DPDP Compliance Dashboard designed to bridge the gap between regulatory requirements and technical operations.
During this presentation, I'll walk you through our project overview, the backend workflows, our modules, our analytical capabilities, and finally, our future expansion plans for multi-tenant support.
-->

---

# Project Overview

<hr class="red-line">

<div class="split-layout">
  <div class="split-left">
    <div class="card card-red" style="margin-bottom: 12px; padding: 12px 14px;">
      <h3>Objective</h3>
      <p style="font-size: 14px; margin: 0; line-height: 1.5;">
        Develop a centralized, automated dashboard to assist organizations in monitoring, assessing, and improving compliance under India's Digital Personal Data Protection (DPDP) Act.
      </p>
    </div>
    <div class="card" style="padding: 12px 14px;">
      <h3>Key Features</h3>
      <ul style="margin: 4px 0; padding-left: 20px; font-size: 13px;">
        <li style="margin-bottom: 6px;"><strong>Consent Management</strong>: Centralized consent capture & revocation logs.</li>
        <li style="margin-bottom: 6px;"><strong>DPDP Assessment</strong>: Automated readiness scorecard based on rules.</li>
        <li style="margin-bottom: 6px;"><strong>PII Discovery</strong>: Automated PII detection and classification.</li>
        <li style="margin-bottom: 6px;"><strong>ROPA & DPIA</strong>: Record of processing activities and risk management.</li>
        <li style="margin-bottom: 6px;"><strong>AI Privacy Assistant</strong>: Automated reporting & compliance guidance.</li>
      </ul>
    </div>
  </div>
  <div class="split-right">
    <div class="card" style="background: #fafafa; padding: 12px 14px; margin-bottom: 12px;">
      <h3>Technology Stack</h3>
      <ul style="margin: 4px 0; padding-left: 20px; font-size: 13px;">
        <li style="margin-bottom: 6px;"><strong>Frontend</strong>: React (Interactive Dashboard)</li>
        <li style="margin-bottom: 6px;"><strong>Backend</strong>: Node.js + Express (REST APIs Gateway)</li>
        <li style="margin-bottom: 6px;"><strong>AI Engine</strong>: Groq LLM (Contextual Privacy Intelligence)</li>
        <li style="margin-bottom: 6px;"><strong>Consent Storage</strong>: Consent Manager APIs & Postgres DB</li>
      </ul>
    </div>
    <h3 style="font-size: 15px; margin-top: 10px;">System Architecture</h3>
    <div class="d-flex align-center gap-sm mono xsmall" style="margin-top: 6px; justify-content: center; flex-wrap: wrap;">
      <div class="box" style="padding: 4px 8px; margin: 0; box-shadow: none; background: white; border-left: 3px solid var(--dt-red); font-weight: bold;">User</div>
      <div class="red" style="font-weight: bold; font-size: 12px;">➔</div>
      <div class="box" style="padding: 4px 8px; margin: 0; box-shadow: none; background: white; border-left: 3px solid var(--dt-red); font-weight: bold;">React UI</div>
      <div class="red" style="font-weight: bold; font-size: 12px;">➔</div>
      <div class="box" style="padding: 4px 8px; margin: 0; box-shadow: none; background: white; border-left: 3px solid var(--dt-red); font-weight: bold;">Express API</div>
      <div class="red" style="font-weight: bold; font-size: 12px;">➔</div>
      <div class="box" style="padding: 4px 8px; margin: 0; box-shadow: none; background: white; border-left: 3px solid var(--dt-red); font-weight: bold;">Consent Mgr</div>
      <div class="red" style="font-weight: bold; font-size: 12px;">➔</div>
      <div class="box" style="padding: 4px 8px; margin: 0; box-shadow: none; background: white; border-left: 3px solid var(--dt-red); font-weight: bold;">Consent DB</div>
    </div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
This slide highlights the project overview of DDS-CMS.
The main objective is to provide a single control plane for compliance teams to monitor how customer data is processed.
Our dashboard covers five key functional areas: Consent management, DPDP assessments, PII mapping, ROPA/DPIA, and an AI privacy assistant.
We built this using React for the interface, Node.js and Express for the API, Groq LLM for AI reporting, and a robust Consent Manager system.
The diagram below shows the flow: a user interacts with the React UI, which contacts the Express API, which communicates with the Consent Manager gateway to record or query consent states in the database.
-->

---

# DDS-CMS Workflow

<hr class="red-line">

<div class="split-layout">
  <div class="split-left" style="flex: 1.1;">
    <div style="display: flex; flex-direction: column; align-items: center; gap: 4px; margin-top: 10px;">
      <div class="d-flex align-center gap-sm mono xsmall" style="width: 100%; justify-content: center;">
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; background: #fafafa; font-weight: bold;">User</div>
        <div class="red" style="font-weight: bold;">➔</div>
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; font-weight: bold;">Enter API Key</div>
        <div class="red" style="font-weight: bold;">➔</div>
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; background: #fafafa; font-weight: bold;">Sync Consent</div>
      </div>
      <div class="red" style="font-weight: bold; font-size: 11px; margin: 2px 0;">▼</div>
      <div class="box" style="padding: 6px 12px; margin: 0; text-align: center; font-weight: bold; width: 60%; background: var(--dt-card-bg);">DDS-CMS Core Dashboard</div>
      <div class="red" style="font-weight: bold; font-size: 11px; margin: 2px 0;">▼</div>
      <div class="d-flex align-center gap-xs mono xsmall" style="width: 100%; justify-content: center; flex-wrap: wrap; gap: 6px;">
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; font-weight: bold; background: white;">Consent Analytics</div>
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; font-weight: bold; background: white;">DPDP Compliance</div>
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; font-weight: bold; background: white;">PII Mapping</div>
        <div class="box" style="padding: 5px 8px; margin: 0; text-align: center; font-weight: bold; background: white;">ROPA & DPIA</div>
      </div>
      <div class="red" style="font-weight: bold; font-size: 11px; margin: 2px 0;">▼</div>
      <div class="box" style="padding: 5px 12px; margin: 0; text-align: center; background: #fafafa; font-weight: bold; width: 50%; border-left: 4px solid var(--dt-red);">Export Compliance Reports</div>
    </div>
  </div>
  <div class="split-right" style="flex: 0.9;">
    <div class="card card-red" style="padding: 10px 12px; margin-bottom: 8px;">
      <h3 style="font-size: 15px; margin-bottom: 4px;">Operational Phases</h3>
      <ul style="margin: 2px 0; padding-left: 16px; font-size: 12px; line-height: 1.4;">
        <li style="margin-bottom: 4px;"><strong>API Connection</strong>: Secure client environment pairing.</li>
        <li style="margin-bottom: 4px;"><strong>Data Sync</strong>: Background consent registry synchronization.</li>
        <li style="margin-bottom: 4px;"><strong>Compliance Assessment</strong>: Real-time DPDP score updates.</li>
        <li style="margin-bottom: 0px;"><strong>Continuous Alerts</strong>: Immediate visibility of processing gaps.</li>
      </ul>
    </div>
    <div class="dashboard-gallery" style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 6px; margin-top: 8px;">
      <img src="images/dashboard-overview.png" alt="Overview" style="width: 100%; height: 85px; object-fit: cover; border-radius: 4px; border: 1px solid var(--dt-border);" />
      <img src="images/dpdp-score.png" alt="DPDP Score" style="width: 100%; height: 85px; object-fit: cover; border-radius: 4px; border: 1px solid var(--dt-border);" />
      <img src="images/consent-overview.png" alt="Consent" style="width: 100%; height: 85px; object-fit: cover; border-radius: 4px; border: 1px solid var(--dt-border);" />
      <img src="images/pii-mapping.png" alt="PII Mapping" style="width: 100%; height: 85px; object-fit: cover; border-radius: 4px; border: 1px solid var(--dt-border);" />
      <img src="images/breach-notification.png" alt="ROPA & DPIA" style="width: 100%; height: 85px; object-fit: cover; border-radius: 4px; border: 1px solid var(--dt-border);" />
    </div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
Here is the end-to-end user workflow of the DDS-CMS.
The process starts when a user logs in and securely registers their environment by entering their API key.
This instantly triggers data synchronization, pulling consent log data into the central compliance engine.
Once ingested, the system feeds it into the core modules of our dashboard: Consent Analytics, DPDP Compliance rules, PII discovery, and ROPA/DPIA assessments.
Finally, the compliance officer can download complete reports and audits to prove compliance to regulators.
-->

---

# Compliance Dashboard Modules

<hr class="red-line">

<div class="bento-grid grid-3x2" style="margin-top: 10px; gap: 10px; grid-template-rows: auto auto;">
  <div class="bento-card" style="grid-column: span 2; padding: 12px 14px;">
    <div class="card-header">
      <div class="card-icon"><i class="fa-solid fa-chart-line"></i></div>
      <h3 style="font-size: 14px;">Overview</h3>
    </div>
    <div class="card-body" style="font-size: 13px; margin-top: 4px;">
      Executive summary of compliance readiness. Displays core KPIs, recent data sync metrics, and overall rule coverage.
    </div>
  </div>
  <div class="bento-card" style="padding: 12px 14px;">
    <div class="card-header">
      <div class="card-icon"><i class="fa-solid fa-gauge-high"></i></div>
      <h3 style="font-size: 14px;">DPDP Score</h3>
    </div>
    <div class="card-body" style="font-size: 13px; margin-top: 4px;">
      Real-time compliance rating calculated dynamically based on implemented system controls.
    </div>
  </div>
  <div class="bento-card" style="padding: 12px 14px;">
    <div class="card-header">
      <div class="card-icon"><i class="fa-solid fa-square-check"></i></div>
      <h3 style="font-size: 14px;">Consent</h3>
    </div>
    <div class="card-body" style="font-size: 13px; margin-top: 4px;">
      Monitor active, expired, and revoked consents. View analytics and export raw records to CSV for auditors.
    </div>
  </div>
  <div class="bento-card" style="padding: 12px 14px;">
    <div class="card-header">
      <div class="card-icon"><i class="fa-solid fa-database"></i></div>
      <h3 style="font-size: 14px;">PII Mapping</h3>
    </div>
    <div class="card-body" style="font-size: 13px; margin-top: 4px;">
      Scan database schemas and API payloads to identify and classify sensitive customer data automatically.
    </div>
  </div>
  <div class="bento-card" style="padding: 12px 14px;">
    <div class="card-header">
      <div class="card-icon"><i class="fa-solid fa-shield-halved"></i></div>
      <h3 style="font-size: 14px;">ROPA & DPIA</h3>
    </div>
    <div class="card-body" style="font-size: 13px; margin-top: 4px;">
      Maintain the Record of Processing Activities and perform automated Data Protection Impact Assessments.
    </div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
This slide details the layout of our Compliance Dashboard modules, which we've designed in a standard bento-grid structure.
The five modules are:
1. Overview: The main landing screen summarizing general readiness.
2. DPDP Score: Our calculated index showing where we stand on compliance rules.
3. Consent: The dashboard section tracking granted and revoked permissions.
4. PII Mapping: The classification module that highlights high-risk columns.
5. ROPA & DPIA: The record-keeping and assessment panel.
Let's look at how we calculate these scores in the next slide.
-->

---

# Compliance Analytics

<hr class="red-line">

<div class="split-layout">
  <div class="split-left">
    <div class="card card-red" style="padding: 10px 14px; margin-bottom: 12px;">
      <h3><i class="fa-solid fa-chart-simple"></i> Consent KPIs</h3>
      <ul style="margin: 4px 0; padding-left: 20px; font-size: 13px;">
        <li style="margin-bottom: 4px;"><strong>Total Consents</strong>: Aggregated count of registered user preferences.</li>
        <li style="margin-bottom: 4px;"><strong>Granted vs. Revoked</strong>: Real-time status breakdown.</li>
        <li style="margin-bottom: 4px;"><strong>Revocation Rate</strong>: Key indicator of user opt-out trends.</li>
      </ul>
    </div>
    <div class="card" style="padding: 10px 14px; background: #fafafa;">
      <h3><i class="fa-solid fa-scale-balanced"></i> DPDP Readiness</h3>
      <p style="font-size: 13px; margin-bottom: 6px; color: var(--dt-gray);">The compliance engine continuously evaluates the following pillars:</p>
      <div class="two-col" style="gap: 10px; font-size: 12px;">
        <div>
          • Consent Operations<br>
          • Notice & Transparency<br>
          • Data Principal Rights
        </div>
        <div>
          • Security Safeguards<br>
          • Data Minimization<br>
          • Breach Readiness
        </div>
      </div>
    </div>
  </div>
  <div class="split-right">
    <h3>DPDP Score Calculation</h3>
    <p style="font-size: 14px; margin-bottom: 10px;">The system evaluates individual rules and aggregates them via a weighted score model to establish the final DPDP Compliance score.</p>
    <div style="display: flex; flex-direction: column; align-items: center; gap: 5px;">
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 13px; font-weight: bold; background: white;">Compliance Rules</div>
      <div class="red" style="font-weight: bold; font-size: 11px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 13px; font-weight: bold; background: #fafafa;">Individual Scores</div>
      <div class="red" style="font-weight: bold; font-size: 11px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 13px; font-weight: bold; background: white;">Weighted Calculation</div>
      <div class="red" style="font-weight: bold; font-size: 11px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 13px; font-weight: bold; color: var(--dt-red); background: #fff5f5; border-left: 4px solid var(--dt-red);">Final DPDP Score</div>
    </div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
This slide describes our compliance analytics.
We measure compliance status using two methods: Consent KPIs and the DPDP readiness framework.
Consent KPIs include Total Consents, active ratios, and the revocation rate.
DPDP readiness reviews six critical compliance areas, including notice transparency, data principal rights, security safeguards, minimization, and breach response.
Instead of arbitrary ratings, the overall DPDP Score is calculated using a rule engine: individual checklist rules are scored, weighted based on regulatory impact, and aggregated into a single verifiable compliance score.
-->

---

# PII Discovery & Privacy Intelligence

<hr class="red-line">

<div class="split-layout">
  <div class="split-left">
    <div class="card card-red" style="padding: 10px 14px; margin-bottom: 10px;">
      <h3><i class="fa-solid fa-user-lock"></i> Automated Discovery</h3>
      <p style="font-size: 13px; color: var(--dt-gray); margin-bottom: 6px;">Automatically scans database structures and identifies PII fields:</p>
      <div class="d-flex gap-sm mono xsmall" style="flex-wrap: wrap; margin-bottom: 6px;">
        <span style="background:#e0e0e0; padding:2px 6px; border-radius:3px;">Name</span>
        <span style="background:#e0e0e0; padding:2px 6px; border-radius:3px;">Email</span>
        <span style="background:#e0e0e0; padding:2px 6px; border-radius:3px;">Phone</span>
        <span style="background:#e0e0e0; padding:2px 6px; border-radius:3px;">Address</span>
        <span style="background:#e0e0e0; padding:2px 6px; border-radius:3px;">User ID</span>
      </div>
      <p style="font-size: 13px;">Attributes are automatically assigned a Category, Risk Level (High/Med/Low), Owner, and Protection Method (e.g. Encrypted/Masked).</p>
    </div>
    <div class="card" style="padding: 10px 14px; background: #fafafa;">
      <h3><i class="fa-solid fa-robot"></i> AI Privacy Assistant</h3>
      <ul style="margin: 4px 0; padding-left: 18px; font-size: 13px;">
        <li>Leverages discovered schema details to identify compliance gaps.</li>
        <li>Guides developers and compliance teams through automated DPIAs.</li>
        <li>Drafts custom incident response templates and audit documents.</li>
      </ul>
    </div>
  </div>
  <div class="split-right">
    <h3>Privacy Intelligence Pipeline</h3>
    <div style="display: flex; flex-direction: column; align-items: center; gap: 4px; margin-top: 10px;">
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: white;">Consent Data</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: #fafafa;">PII Classification</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: white;">Risk Assessment</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: #fafafa;">AI Assistant Guidance</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; color: var(--dt-red); background: #fff5f5; border-left: 4px solid var(--dt-red);">Compliance Report</div>
    </div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
This slide covers PII Mapping and our AI Assistant.
A major challenge is knowing where sensitive data lives. DDS-CMS automatically runs scanning scripts on connected database tables to detect PII fields.
Once fields like Name, Email, or Phone are discovered, they are classified.
To assist compliance teams, our AI assistant consumes this schema metadata. Instead of legal teams manually reviewing tables, the AI evaluates processing actions, helps complete the Data Protection Impact Assessment (DPIA), and writes the compliance reports automatically.
-->

---

# Backend & API Workflow

<hr class="red-line">

<div class="split-layout">
  <div class="split-left" style="flex: 0.9;">
    <h3>System Communication</h3>
    <div style="display: flex; flex-direction: column; align-items: center; gap: 5px; margin-top: 10px;">
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: white;">React Dashboard</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: #fafafa;">REST APIs Gateway</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: white;">Express Backend</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; background: #fafafa;">Consent Manager Engine</div>
      <div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div>
      <div class="box" style="padding: 5px 10px; margin: 0; width: 85%; text-align: center; font-size: 12px; font-weight: bold; color: var(--dt-red); background: #fff5f5; border-left: 4px solid var(--dt-red);">Consent Database</div>
    </div>
  </div>
  <div class="split-right" style="flex: 1.1;">
    <div class="card card-red" style="padding: 10px 14px; margin-bottom: 8px;">
      <h3>Backend Core Endpoints</h3>
      <ul style="margin: 4px 0; padding-left: 20px; font-size: 13px;">
        <li style="margin-bottom: 6px;"><strong>Consent Retrieval</strong>: Queries and validates user options in real-time.</li>
        <li style="margin-bottom: 6px;"><strong>PII Classification</strong>: Runs classification routines on metadata.</li>
        <li style="margin-bottom: 6px;"><strong>DPDP Score Engine</strong>: Computes compliance stats.</li>
        <li style="margin-bottom: 6px;"><strong>Risk Assessment API</strong>: Evaluates vulnerabilities in data flow.</li>
      </ul>
    </div>
    <div class="card" style="padding: 10px 14px; background: #fafafa;">
      <h3>Architecture Design Goals</h3>
      <ul style="margin: 4px 0; padding-left: 20px; font-size: 13px;">
        <li><strong>Secure API Communication</strong>: Token-based endpoints.</li>
        <li><strong>Modular Infrastructure</strong>: Independent components ensure easy updates.</li>
        <li><strong>Scalable Architecture</strong>: Optimized databases and low latency.</li>
      </ul>
    </div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
This slide explains our backend and API architecture.
The frontend React dashboard communicates with Node.js and Express backend via REST APIs.
The backend handles consent status requests, runs PII classification, executes DPDP score evaluations, and handles risk metrics.
We emphasized three key architectural goals: securing all API communication using tokens, utilizing a modular service layout, and structuring the database for minimal latency.
-->

---

# Future Architecture – Approach A
<div style="max-width: 800px;">
  <h2 style="font-size: 18px; color: var(--dt-gray); font-weight: 500; margin: 0 0 4px 0;">Centralized Multi-Tenant Compliance Portal</h2>
  <p class="muted" style="font-size: 13px; margin: 0 0 6px 0;">Single Compliance Portal for Multiple Organizations</p>
</div>
<hr class="red-line" style="margin-top: 4px; margin-bottom: 12px;">

<div class="split-layout">
  <div class="split-left" style="flex: 1.0;">
    <div class="card card-red" style="padding: 10px 12px; margin-bottom: 8px;">
      <h3 style="font-size: 13px; margin-bottom: 4px; display: flex; align-items: center; gap: 6px;"><i class="fa-solid fa-circle-info" style="color: var(--dt-red);"></i> How it Works</h3>
      <div style="display: flex; flex-direction: column; gap: 4px; margin-top: 4px;">
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>A single centralized compliance portal serves multiple organizations.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>The backend registry maintains organization configs and API endpoints.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>Each organization backend secures endpoints via auth mapping.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>Upon user login, the portal gateway retrieves organization API keys.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>Fetches Consent and PII data from the company's remote server.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>The central DPDP compliance engine calculates score and metrics dynamically.</span>
        </div>
      </div>
    </div>
    <div class="two-col" style="gap: 8px;">
      <div class="card" style="padding: 8px 10px; background: #fafafa; border: 1px solid var(--dt-border); border-top: 3px solid var(--dt-green); margin-bottom: 0;">
        <h3 style="font-size: 12px; margin-bottom: 4px; color: var(--dt-green); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-thumbs-up"></i> Advantages</h3>
        <div style="display: flex; flex-direction: column; gap: 3px;">
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Single centralized platform</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Easy onboarding</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Common dashboard</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Centralized administration</span></div>
        </div>
      </div>
      <div class="card" style="padding: 8px 10px; background: #fafafa; border: 1px solid var(--dt-border); border-top: 3px solid var(--dt-red); margin-bottom: 0;">
        <h3 style="font-size: 12px; margin-bottom: 4px; color: var(--dt-red); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-triangle-exclamation"></i> Limitations</h3>
        <div style="display: flex; flex-direction: column; gap: 3px;">
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-xmark" style="color: var(--dt-red); font-size: 10px;"></i> <span>Separate login portal</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-xmark" style="color: var(--dt-red); font-size: 10px;"></i> <span>Registry maintenance</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-xmark" style="color: var(--dt-red); font-size: 10px;"></i> <span>Additional isolation effort</span></div>
        </div>
    </div>
  </div>
</div>
  <div class="split-right" style="flex: 1.0;">
    <h3 style="font-size: 14px; margin-bottom: 8px; text-align: center;"><i class="fa-solid fa-network-wired" style="color: var(--dt-red); margin-right: 4px;"></i> Architecture Flow</h3>
    <div class="flow-container"><div class="flow-col"><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px;">Company Admin</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px;">Login to Portal</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px; border-left-color: var(--dt-red-light);">Express Gateway</div></div><div class="red" style="font-weight: bold; font-size: 14px; width: 20px; text-align: center; flex-shrink: 0;">➔</div><div class="flow-col"><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px;">Registry DB</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px;">Load Config</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px; border-left-color: var(--dt-red-light);">Call Company APIs</div></div><div class="red" style="font-weight: bold; font-size: 14px; width: 20px; text-align: center; flex-shrink: 0;">➔</div><div class="flow-col"><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px;">Fetch Consent/PII</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px;">DPDP Engine</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; color: var(--dt-red); background: #fff5f5; border-left: 4px solid var(--dt-red); box-shadow: none; border-radius: 6px;">Compliance Portal</div></div></div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
Here we present Future Architecture Approach A: the Centralized Multi-Tenant Compliance Portal.
Under this model, a single centralized compliance platform serves multiple distinct tenant organizations. 
When a company administrator logs in, our Express gateway resolves their identity against an Organization Registry database, loads their specific API configuration, and calls their backend to fetch consent and PII data.
The data is then processed by our centralized DPDP compliance engine to render a dashboard within our portal.
While onboarding and administrative control are centralized and straightforward, this model requires a separate login portal for tenants and places the responsibility of data isolation and registry database maintenance entirely on our platform.
-->

---

# Future Architecture – Approach B
<div style="max-width: 800px;">
  <h2 style="font-size: 18px; color: var(--dt-gray); font-weight: 500; margin: 0 0 4px 0;">API-Driven Embedded CMS Architecture (Recommended)</h2>
  <p class="muted" style="font-size: 13px; margin: 0 0 6px 0;">Compliance Dashboard Embedded Inside Company CMS</p>
</div>
<hr class="red-line" style="margin-top: 4px; margin-bottom: 12px;">

<div class="split-layout">
  <div class="split-left" style="flex: 1.0;">
    <div class="card card-red" style="padding: 10px 12px; margin-bottom: 8px;">
      <h3 style="font-size: 13px; margin-bottom: 4px; display: flex; align-items: center; gap: 6px;"><i class="fa-solid fa-circle-info" style="color: var(--dt-red);"></i> How it Works</h3>
      <div style="display: flex; flex-direction: column; gap: 4px; margin-top: 4px;">
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>Each company manages its own API key from its CMS settings directly.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>The compliance dashboard is embedded directly into the company's CMS.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>The CMS sends compliance data and API key to our Express backend.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>Our backend performs all DPDP calculations (score, PII, risk).</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>The backend returns standardized JSON compliance datasets.</span>
        </div>
        <div style="font-size: 11px; line-height: 1.3; color: var(--dt-dark); display: flex; align-items: flex-start; gap: 5px;">
          <i class="fa-solid fa-chevron-right" style="font-size: 8px; color: var(--dt-red); margin-top: 4px; flex-shrink: 0;"></i>
          <span>The CMS renders the dashboard interface inside its own native interface.</span>
        </div>
      </div>
    </div>
    <div class="two-col" style="gap: 8px;">
      <div class="card" style="padding: 8px 10px; background: #fafafa; border: 1px solid var(--dt-border); border-top: 3px solid var(--dt-green); margin-bottom: 0;">
        <h3 style="font-size: 12px; margin-bottom: 4px; color: var(--dt-green); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-thumbs-up"></i> Advantages</h3>
        <div style="display: flex; flex-direction: column; gap: 3px;">
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Single Sign-On (SSO)</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Better user experience</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Better data isolation</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Stateless backend</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-check" style="color: var(--dt-green); font-size: 10px;"></i> <span>Easy horizontal scaling</span></div>
        </div>
      </div>
      <div class="card" style="padding: 8px 10px; background: #fafafa; border: 1px solid var(--dt-border); border-top: 3px solid var(--dt-red); margin-bottom: 0;">
        <h3 style="font-size: 12px; margin-bottom: 4px; color: var(--dt-red); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-triangle-exclamation"></i> Limitations</h3>
        <div style="display: flex; flex-direction: column; gap: 3px;">
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-xmark" style="color: var(--dt-red); font-size: 10px;"></i> <span>Requires CMS integration</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-xmark" style="color: var(--dt-red); font-size: 10px;"></i> <span>Frontend embed effort</span></div>
          <div style="font-size: 10px; line-height: 1.25; color: var(--dt-dark); display: flex; align-items: center; gap: 4px;"><i class="fa-solid fa-xmark" style="color: var(--dt-red); font-size: 10px;"></i> <span>CMS must integrate API</span></div>
        </div>
      </div>
    </div>
  </div>
  <div class="split-right" style="flex: 1.0;">
    <h3 style="font-size: 14px; margin-bottom: 8px; text-align: center;"><i class="fa-solid fa-network-wired" style="color: var(--dt-red); margin-right: 4px;"></i> Embedded Flow</h3>
    <div class="flow-container"><div class="flow-col"><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px;">Company Admin</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px;">Company CMS</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px; border-left-color: var(--dt-red-light);">Compliance Module</div></div><div class="red" style="font-weight: bold; font-size: 14px; width: 20px; text-align: center; flex-shrink: 0;">➔</div><div class="flow-col"><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px;">Generate API Key</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px;">Call /api/compliance/...</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px; border-left-color: var(--dt-red-light);">Express Engine</div></div><div class="red" style="font-weight: bold; font-size: 14px; width: 20px; text-align: center; flex-shrink: 0;">➔</div><div class="flow-col"><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 10px; font-weight: bold; background: white; box-shadow: none; border-radius: 6px; line-height: 1.2;">DPDP Score / PII / Risk</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; background: #fafafa; box-shadow: none; border-radius: 6px;">Return Std JSON</div><div class="red" style="font-weight: bold; font-size: 10px; line-height: 1;">▼</div><div class="box" style="padding: 6px 8px; margin: 0; width: 100%; text-align: center; font-size: 11px; font-weight: bold; color: var(--dt-red); background: #fff5f5; border-left: 4px solid var(--dt-red); box-shadow: none; border-radius: 6px;">Embedded Dashboard</div></div></div>
  </div>
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
Approach B represents an API-driven embedded CMS architecture.
Instead of sending users to our centralized portal, the compliance dashboard is embedded directly into the company's own CMS.
Each company manages their own compliance module settings and API keys inside their local CMS.
The CMS then sends consent and PII compliance data to our backend, which performs calculations statelessly and returns standardized JSON.
The CMS renders the dashboard locally within its own interface.
This provides a superior user experience with single sign-on, ensures natural data isolation, simplifies our backend to be stateless, and allows easy horizontal scaling. However, it requires frontend embedding effort and custom integration by each CMS.
-->

---

# Architecture Comparison & Recommendation
<hr class="red-line" style="margin-top: 4px; margin-bottom: 8px;">

<table style="width: 100%; border-collapse: collapse; font-size: 10px; margin: 4px 0;">
  <thead>
    <tr style="background: var(--dt-red); color: white;">
      <th style="padding: 5px 8px; font-weight: 700; text-align: left; text-transform: uppercase; letter-spacing: 0.5px;">Criteria</th>
      <th style="padding: 5px 8px; font-weight: 700; text-align: left; text-transform: uppercase; letter-spacing: 0.5px;">Approach A: Centralized Portal</th>
      <th style="padding: 5px 8px; font-weight: 700; text-align: left; text-transform: uppercase; letter-spacing: 0.5px; background: var(--dt-red-light);">Approach B: Embedded CMS (Recommended)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Portal Location</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Centralized SaaS Portal</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Embedded inside Company CMS</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Dashboard</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Central Common Dashboard</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Native Embedded CMS Interface</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Authentication</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Separate Portal Login</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Single Sign-On (SSO) via CMS</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">API Key Management</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Central Registry Database</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Managed in local CMS settings</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Backend Storage</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Persistent Registry Config DB</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Stateless (No Tenant Registry DB)</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Data Isolation</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Logical Isolation on Platform</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Strict Natural Tenant Isolation</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Scalability</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Moderate (Central Routing Overhead)</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">High (Stateless Backend Scaling)</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">User Experience</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Separate Dashboard Login</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Seamless Integrated CMS Experience</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Backend Responsibility</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">High (Gateway, Routing & Mappings)</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; background: #fff8f8;">Low (Stateless Calculation APIs)</td>
    </tr>
    <tr>
      <td style="padding: 3px 8px; font-weight: 600; border-bottom: 1px solid var(--dt-border);">Recommendation</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border);">Centralized SaaS Platform Deployments</td>
      <td style="padding: 3px 8px; border-bottom: 1px solid var(--dt-border); font-weight: 600; color: var(--dt-green); background: #fff8f8;"><strong>Recommended Approach (SSO & Isolation)</strong></td>
    </tr>
  </tbody>
</table>

<div style="margin: 6px 0 0 0; padding: 6px 12px; font-size: 10px; border-left: 4px solid var(--dt-red); background: #fff5f5; color: var(--dt-red); font-style: italic; font-weight: 600; line-height: 1.4;">
  Both architectures achieve the same compliance goals using different deployment models. Approach A is suitable for a centralized SaaS compliance platform where organizations access a common portal. Approach B integrates directly into an organization's existing CMS, providing a seamless single-login experience, natural tenant isolation, and a lightweight stateless backend. Both approaches will be presented to stakeholders, and the final architecture will be selected based on project requirements.
</div>

<div style="position: absolute; bottom: 18px; left: 60px; font-size: 11px; color: #bbb; font-family: 'Inter', sans-serif;">DDS-CMS | DPDP Compliance Dashboard</div>

<!--
Speaker Notes:
To compare both approaches, we evaluate them across key architectural criteria.
Approach A provides a centralized, SaaS-like portal that is quick to onboard if companies do not want to modify their CMS. However, it introduces separate login flows and database registry overhead.
Approach B offers a seamless native CMS experience, uses single sign-on, and ensures strict data isolation by keeping data on the client side, while keeping our backend stateless and highly scalable.
Both approaches achieve our compliance goals. We will present both to stakeholders to make a final selection based on the specific deployment requirements of our customers.
-->
ke a final selection based on the specific deployment requirements of our customers.
-->

