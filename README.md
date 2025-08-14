<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>MindBodyMom</title>
  <meta name="description" content="Perinatal mental health and wellbeing: fast, guided access to therapists, dietitians, pelvic floor PTs, and psychiatric care." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Playfair+Display:wght@600&display=swap" rel="stylesheet">
  <style>
    :root {
      --teal: #0c998e;
      --sage: #9bb8a6;
      --blush: #f7e6ea;
      --gold: #d7b36a;
      --ink: #1f2a34;
      --muted: #5c6b76;
      --bg: #fff;
    }
    *{box-sizing:border-box}
    html,body{margin:0;padding:0}
    body{font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;color:var(--ink);background:var(--bg);line-height:1.6}
    a{text-decoration:none;color:inherit}
    .container{max-width:1200px;margin:0 auto;padding:0 20px}
    header{position:sticky;top:0;background:#fff9;backdrop-filter:saturate(180%) blur(10px);border-bottom:1px solid #eee;z-index:40}
    .nav{display:flex;align-items:center;justify-content:space-between;height:64px}
    .brand{display:flex;align-items:center;gap:10px}
    .logo{width:36px;height:36px;border-radius:10px;background:linear-gradient(135deg,var(--teal),var(--sage));display:grid;place-items:center;color:white;font-weight:700}
    .brand span{font-family:"Playfair Display",serif;font-weight:600;font-size:22px}
    .navlinks{display:flex;gap:14px;align-items:center;flex-wrap:wrap}
    .navlinks a.active{color:var(--teal);font-weight:700}
    .btn{display:inline-flex;align-items:center;justify-content:center;padding:10px 16px;border-radius:999px;border:1px solid transparent;font-weight:600;transition:transform .05s ease, box-shadow .2s}
    .btn:active{transform:translateY(1px)}
    .btn-primary{background:var(--teal);color:#fff;box-shadow:0 6px 20px rgba(12,153,142,.25)}
    .btn-outline{border-color:var(--teal);color:var(--teal);background:#fff}
    .btn-gold{background:var(--gold);color:#1d1d1d}

    main > section{display:none}
    main > section.active{display:block}

    .hero{display:grid;grid-template-columns:1.1fr .9fr;gap:40px;align-items:center;padding:64px 0}
    .chip{display:inline-block;background:var(--blush);color:#7a4c58;padding:6px 12px;border-radius:999px;font-size:12px;font-weight:600}
    h1{font-family:"Playfair Display",serif;font-weight:600;line-height:1.1;margin:14px 0;font-size:44px}
    .sub{color:var(--muted);font-size:18px}
    .hero-cta{display:flex;gap:12px;margin-top:18px;flex-wrap:wrap}
    .card{background:#fff;border:1px solid #eee;border-radius:18px;padding:20px;box-shadow:0 8px 30px rgba(0,0,0,.06)}
    .illus{aspect-ratio:4/3;border-radius:16px;background:linear-gradient(135deg,var(--blush),#fff 40%, var(--sage));position:relative;overflow:hidden}
    .badge{position:absolute;right:16px;top:16px;background:#fff;border:1px solid #eee;border-radius:999px;padding:8px 12px;font-weight:700;color:var(--teal)}

    .trust{background:linear-gradient(180deg,#fff, #fafbfc)}
    .trust .row{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;padding:28px 0}
    .stat{border-radius:16px;padding:18px;text-align:center;background:#fff;border:1px dashed #e9eef2}
    .stat strong{display:block;font-size:28px;color:var(--teal)}

    .how{padding:56px 0}
    .how h2, .dir h2, .partners h2, .faq h2, .cal h2, .epic h2, .inbox h2{font-family:"Playfair Display",serif;font-size:32px;margin:0 0 8px}
    .lead{color:var(--muted)}
    .steps{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:20px}
    .step{position:relative;padding-left:14px}
    .step::before{content:"";position:absolute;left:0;top:10px;width:6px;height:6px;background:var(--gold);border-radius:50%}

    .dir{padding:56px 0;background:linear-gradient(180deg,#fbf9f9,#fff)}
    .grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:18px}
    .clin{display:flex;gap:12px}
    .avatar{width:54px;height:54px;border-radius:14px;background:linear-gradient(135deg,var(--sage),var(--teal));flex:0 0 54px}
    .clin h4{margin:0 0 4px}
    .pill{display:inline-block;background:#f1f5f9;border:1px solid #e5e7eb;border-radius:999px;padding:4px 8px;font-size:12px;margin-right:6px;margin-top:6px}

    /* Calendar */
    .cal{padding:56px 0}
    .cal-wrap{overflow:auto}
    .cal-grid{display:grid;grid-template-columns:120px repeat(5,1fr);border:1px solid #e5e7eb;border-radius:12px}
    .cal-grid .head{background:#f8fafc;font-weight:700;text-align:center;padding:10px;border-bottom:1px solid #e5e7eb}
    .cal-grid .time{padding:10px;border-right:1px solid #eef2f6;color:#64748b;white-space:nowrap}
    .slot{min-height:54px;border-left:1px solid #eef2f6;border-top:1px solid #eef2f6;position:relative;cursor:pointer}
    .slot.booked{background:rgba(12,153,142,.12)}
    .slot.booked::after{content:"Booked";position:absolute;right:6px;top:6px;font-size:11px;color:var(--teal);font-weight:700}

    /* EPIC-like */
    .epic{padding:56px 0}
    .epic-wrap{display:grid;grid-template-columns:260px 1fr;gap:16px}
    .epic-sidebar{background:#0f172a;color:#e2e8f0;border-radius:14px;padding:12px}
    .epic-sidebar h4{margin:8px 0 4px;font-size:14px;color:#cbd5e1}
    .epic-patient{background:#fff;border:1px solid #e5e7eb;border-radius:14px;padding:18px}
    .chart-head{display:flex;justify-content:space-between;align-items:center}
    .chart-meta{display:flex;gap:12px;color:#475569;font-size:14px}
    .epic-toolbar{display:flex;gap:8px;flex-wrap:wrap}
    .epic-toolbar .btn{padding:6px 10px}

    /* Inbox */
    .inbox{padding:56px 0}
    .inbox-list{display:grid;grid-template-columns:1fr 1fr;gap:14px}

    .partners{padding:56px 0}
    .cols{display:grid;grid-template-columns:1.2fr .8fr;gap:24px}
    .check{display:flex;align-items:flex-start;gap:10px;margin:10px 0}
    .check svg{flex:0 0 20px}

    .testimonials{padding:40px 0;background:linear-gradient(180deg,#fff,#f9fbfb)}
    .marquee{display:flex;gap:16px;overflow:auto;scroll-snap-type:x mandatory;padding-bottom:6px}
    .marquee .card{min-width:320px;scroll-snap-align:start}

    .faq{padding:56px 0}
    details{border:1px solid #eaecef;border-radius:14px;padding:14px;background:#fff;box-shadow:0 6px 18px rgba(0,0,0,.04)}
    details+details{margin-top:10px}
    summary{cursor:pointer;font-weight:600}

    footer{padding:36px 0;border-top:1px solid #eee;color:#4a5a64}

    /* Modal */
    .modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,.36);z-index:50}
    .modal[aria-hidden="false"]{display:flex}
    .modal-card{background:#fff;border-radius:18px;max-width:640px;width:92%;padding:20px;border:1px solid #eee;box-shadow:0 18px 60px rgba(0,0,0,.25)}
    .modal-header{display:flex;align-items:center;justify-content:space-between}
    .close{background:transparent;border:none;font-size:22px;cursor:pointer}
    .form{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:10px}
    .form .full{grid-column:1 / -1}
    label{font-size:12px;font-weight:600;color:#4a5a64}
    input,select,textarea{width:100%;padding:10px;border-radius:10px;border:1px solid #e1e6ea;font:inherit}
    textarea{min-height:84px}
    .inline{display:flex;gap:8px;align-items:center;margin-top:6px}

    .toast{position:fixed;right:16px;bottom:16px;background:#0b6e66;color:#fff;padding:12px 16px;border-radius:12px;box-shadow:0 8px 24px rgba(0,0,0,.2);opacity:0;transform:translateY(10px);transition:.25s;z-index:60}
    .toast.show{opacity:1;transform:translateY(0)}

    @media (max-width: 1100px){
      .hero{grid-template-columns:1fr}
      .grid{grid-template-columns:1fr 1fr}
      .steps{grid-template-columns:1fr}
      .cols{grid-template-columns:1fr}
      .epic-wrap{grid-template-columns:1fr}
      .inbox-list{grid-template-columns:1fr}
    }
    @media (max-width: 640px){
      .grid{grid-template-columns:1fr}
      .navlinks{display:none}
      h1{font-size:36px}
    }
  </style>
</head>
<body>
  <header>
    <div class="container nav" role="navigation" aria-label="Main">
      <div class="brand">
        <div class="logo" aria-hidden="true">MB</div>
        <span>MindBodyMom</span>
      </div>
      <nav class="navlinks" id="mainNav">
        <a href="#home" data-route>Home</a>
        <a href="#directory" data-route>Directory</a>
        <a href="#calendar" data-route>Calendar</a>
        <a href="#epic" data-route>EPIC Mock</a>
        <a href="#inbox" data-route>Hand‑off Inbox</a>
        <a href="#partners" data-route>For OB/GYNs</a>
        <a href="#faq" data-route>FAQ</a>
        <button class="btn btn-outline" id="openReferral">Refer a patient</button>
        <a class="btn btn-primary" href="#directory" data-route>Get care</a>
      </nav>
    </div>
  </header>

  <main>
    <!-- HOME -->
    <section class="hero container active" id="home">
      <div>
        <span class="chip">Perinatal mental health & wellbeing</span>
        <h1>Warm hand‑offs to care in 0–48 hours, thoughtfully guided from referral to recovery.</h1>
        <p class="sub">We connect pregnant and postpartum parents to licensed therapists, pelvic floor PTs, dietitians, and psychiatric care—while supporting clinicians and OB/GYN teams with a simple, secure referral flow.</p>
        <div class="hero-cta">
          <button class="btn btn-primary" id="openSelf">I’m seeking care</button>
          <button class="btn btn-gold" id="openReferral2">I’m a clinician → Refer</button>
          <a class="btn btn-outline" href="#partners" data-route>For OB/GYN & partners</a>
        </div>
      </div>
      <div>
        <div class="illus card" aria-hidden="true">
          <div class="badge">Up to 48h</div>
          <div class="card" style="position:absolute;left:20px;bottom:20px;right:20px">
            <div style="display:flex;align-items:center;justify-content:space-between">
              <div>
                <strong>Next available</strong>
                <div style="color:var(--muted);font-size:14px">Video consult • Therapy</div>
              </div>
              <button class="btn btn-primary" id="openSchedule">Schedule</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- DIRECTORY -->
    <section class="dir" id="directory">
      <div class="container">
        <h2>Browse clinicians</h2>
        <p class="lead">Licensed providers with perinatal expertise. Choose by specialty, insurance, language, and availability.</p>
        <div class="grid" role="list">
          <!-- Clinician Card 1 -->
          <article class="card" role="listitem">
            <div class="clin">
              <div class="avatar" aria-hidden="true"></div>
              <div>
                <h4>J. Rivera, LPCC</h4>
                <div style="color:var(--muted);font-size:14px">Therapist • Perinatal mood & anxiety • Telehealth (NM)</div>
                <div>
                  <span class="pill">Accepting new</span>
                  <span class="pill">BCBS, Medicaid</span>
                  <span class="pill">Spanish</span>
                </div>
              </div>
            </div>
            <div style="display:flex;gap:8px;margin-top:12px">
              <button class="btn btn-outline" data-profile="rivera">View profile</button>
              <button class="btn btn-primary" data-sched>Schedule</button>
            </div>
          </article>
          <!-- Clinician Card 2 -->
          <article class="card" role="listitem">
            <div class="clin">
              <div class="avatar" aria-hidden="true"></div>
              <div>
                <h4>S. Patel, RD</h4>
                <div style="color:var(--muted);font-size:14px">Dietitian • Gestational diabetes & lactation nutrition</div>
                <div>
                  <span class="pill">Self‑pay & PPO</span>
                  <span class="pill">Weekend slots</span>
                </div>
              </div>
            </div>
            <div style="display:flex;gap:8px;margin-top:12px">
              <button class="btn btn-outline" data-profile="patel">View profile</button>
              <button class="btn btn-primary" data-sched>Schedule</button>
            </div>
          </article>
          <!-- Clinician Card 3 -->
          <article class="card" role="listitem">
            <div class="clin">
              <div class="avatar" aria-hidden="true"></div>
              <div>
                <h4>A. Nguyen, DPT</h4>
                <div style="color:var(--muted);font-size:14px">Pelvic Floor PT • Postpartum recovery & pain</div>
                <div>
                  <span class="pill">Hybrid care</span>
                  <span class="pill">Albuquerque</span>
                </div>
              </div>
            </div>
            <div style="display:flex;gap:8px;margin-top:12px">
              <button class="btn btn-outline" data-profile="nguyen">View profile</button>
              <button class="btn btn-primary" data-sched>Schedule</button>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- CALENDAR -->
    <section class="cal container" id="calendar">
      <h2>Clinician Calendar</h2>
      <p class="lead">Click slots to toggle availability. (Demo only — saved to your browser.)</p>
      <div class="cal-wrap">
        <div class="cal-grid" id="calGrid">
          <!-- Head row -->
          <div></div>
          <div class="head">Mon</div>
          <div class="head">Tue</div>
          <div class="head">Wed</div>
          <div class="head">Thu</div>
          <div class="head">Fri</div>
          <!-- Rows will be generated by JS -->
        </div>
      </div>
      <div style="margin-top:12px;display:flex;gap:8px">
        <button class="btn btn-outline" id="clearCal">Clear</button>
        <button class="btn btn-primary" id="mockFill">Mock fill</button>
      </div>
    </section>

    <!-- EPIC MOCK -->
    <section class="epic container" id="epic">
      <h2>EPIC‑style Chart (Mock)</h2>
      <div class="epic-wrap">
        <aside class="epic-sidebar">
          <h4>Patients</h4>
          <div class="card" style="background:#111827;color:#e5e7eb;border-color:#1f2937">
            <strong>Mari G.</strong>
            <div style="font-size:12px;color:#94a3b8">20w pregnant • Anxiety</div>
          </div>
          <div class="card" style="background:#111827;color:#e5e7eb;border-color:#1f2937;margin-top:8px;opacity:.7">
            <strong>Jess R.</strong>
            <div style="font-size:12px;color:#94a3b8">PP 3 mo • Sleep</div>
          </div>
        </aside>
        <div class="epic-patient">
          <div class="chart-head">
            <div>
              <h3 style="margin:0">Mari G. <span style="font-size:14px;color:#64748b">(DOB 1997)</span></h3>
              <div class="chart-meta">
                <span>Pregnancy: 20 weeks</span>
                <span>PHQ‑9: 13</span>
                <span>GAD‑7: 12</span>
              </div>
            </div>
            <div class="epic-toolbar">
              <button class="btn btn-outline" id="openReferral4">Refer to MindBodyMom</button>
              <button class="btn btn-primary" id="openSchedule2">Schedule Therapy</button>
            </div>
          </div>
          <hr style="margin:16px 0;border:none;border-top:1px solid #e5e7eb" />
          <div class="grid" style="grid-template-columns:1fr 1fr">
            <div>
              <h4 style="margin:0 0 6px">Summary</h4>
              <div class="card">
                <p><strong>Chief concern:</strong> Anxiety interfering with sleep and appetite. Denies current SI. No substance use. Supportive partner.</p>
                <p><strong>Plan:</strong> Behavioral therapy; consider SSRI with psych consult if symptoms persist.</p>
              </div>
            </div>
            <div>
              <h4 style="margin:0 0 6px">Medications</h4>
              <div class="card">
                <ul>
                  <li>Prenatal vitamin</li>
                  <li>Iron supplement (every other day)</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- HAND-OFF INBOX -->
    <section class="inbox container" id="inbox">
      <h2>Warm Hand‑off Inbox</h2>
      <p class="lead">Clinicians are notified here when a referral is ready to schedule.</p>
      <div class="inbox-list" id="inboxList">
        <!-- items populated by JS -->
      </div>
    </section>

    <!-- PARTNERS -->
    <section class="partners container" id="partners">
      <h2>For OB/GYN & partners</h2>
      <p class="lead">Purpose‑built for clinics that want real‑time access to behavioral, nutrition, PT, and psychiatric care—without adding burden to staff.</p>
      <div class="cols">
        <div class="card">
          <div class="check"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 6L9 17l-5-5" stroke="var(--teal)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg><div><strong>Warm hand‑off</strong><div class="lead">Start a referral during the visit; we handle outreach and follow‑up.</div></div></div>
          <div class="check"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 6L9 17l-5-5" stroke="var(--teal)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg><div><strong>Guided onboarding</strong><div class="lead">We gather safety, history, and preferences in a secure pre‑visit.</div></div></div>
          <div class="check"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 6L9 17l-5-5" stroke="var(--teal)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg><div><strong>0–48h access</strong><div class="lead">First appointment within 0–48 hours whenever possible.</div></div></div>
          <div class="check"><svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 6L9 17l-5-5" stroke="var(--teal)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg><div><strong>Status updates</strong><div class="lead">Consent‑based feedback loop to the referring provider.</div></div></div>
          <div style="margin-top:16px;display:flex;gap:10px"><button class="btn btn-primary" id="openReferral3">Start a referral</button><button class="btn btn-outline" id="openDemo">See demo</button></div>
        </div>
        <div class="card">
          <h3 style="margin-top:0">At‑a‑glance</h3>
          <ul>
            <li>Contractor‑friendly marketplace for licensed clinicians</li>
            <li>Telehealth‑ready; hybrid care optional</li>
            <li>Insurance & self‑pay supported (mockup)</li>
            <li>Simple Netlify‑deployable prototype</li>
          </ul>
          <div class="card" style="background:var(--blush);border-color:#f3dbe2;margin-top:10px">
            <strong style="display:block">Demo login (mock)</strong>
            <div style="font-family:monospace">provider@mindbodymom.com / demo1234</div>
          </div>
        </div>
      </div>
    </section>

    <!-- TESTIMONIALS -->
    <section class="testimonials" id="stories">
      <div class="container">
        <div class="marquee" aria-label="Stories">
          <div class="card">
            <strong>Mari (first‑time mom)</strong>
            <p>“My OB clicked ‘refer’ and I had a video session the next day. The follow‑ups kept me on track.”</p>
          </div>
          <div class="card">
            <strong>OB Clinic Admin</strong>
            <p>“It takes 60 seconds to start a warm hand‑off—then our staff can move to the next patient.”</p>
          </div>
          <div class="card">
            <strong>Therapist, LPCC</strong>
            <p>“I keep my private practice and meet perinatal clients who truly match my scope.”</p>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ -->
    <section class="faq container" id="faq">
      <h2>FAQs</h2>
      <details>
        <summary>Is this a real scheduling system?</summary>
        <p>This prototype is clickable for user testing. Buttons simulate scheduling and referrals; data isn’t stored on a server.</p>
      </details>
      <details>
        <summary>What does “warm hand‑off” mean here?</summary>
        <p>A referring clinician initiates the process during the medical visit, and we guide the patient into the first appointment within 0–48 hours when possible.</p>
      </details>
      <details>
        <summary>Do clinicians work as contractors?</summary>
        <p>Yes—providers keep their practice while serving perinatal clients through MindBodyMom.</p>
      </details>
    </section>
  </main>

  <footer>
    <div class="container" style="display:flex;justify-content:space-between;gap:16px;flex-wrap:wrap">
      <div>© <span id="year"></span> MindBodyMom</div>
      <div style="display:flex;gap:12px">
        <a href="#" id="openContact">Contact</a>
        <a href="#partners" data-route>For OB/GYN</a>
        <a href="#directory" data-route>Directory</a>
      </div>
    </div>
  </footer>

  <!-- Referral / Self‑init Modal (shared) -->
  <div class="modal" id="refModal" aria-hidden="true" role="dialog" aria-modal="true" aria-labelledby="refTitle">
    <div class="modal-card" role="document">
      <div class="modal-header">
        <h3 id="refTitle" style="margin:0">Start a referral</h3>
        <button class="close" aria-label="Close" id="closeModal">×</button>
      </div>
      <form class="form" id="refForm" onsubmit="return false;">
        <div>
          <label>Patient first name</label>
          <input required placeholder="Mari" />
        </div>
        <div>
          <label>Patient last name</label>
          <input required placeholder="G." />
        </div>
        <div>
          <label>Relationship</label>
          <select>
            <option>OB/Midwife</option>
            <option>Self</option>
            <option>Pediatrician</option>
            <option>Partner</option>
          </select>
        </div>
        <div>
          <label>Insurance</label>
          <select>
            <option>Medicaid</option>
            <option>BCBS</option>
            <option>PPO</option>
            <option>Self‑pay</option>
          </select>
        </div>
        <div class="full">
          <label>Primary concern</label>
          <textarea placeholder="Briefly describe symptoms, timing, safety concerns..."></textarea>
        </div>
        <div class="full inline">
          <input type="checkbox" id="consent" />
          <label for="consent">I have consent to share this information for care coordination.</label>
        </div>
        <div class="full" style="display:flex;gap:8px;justify-content:flex-end;margin-top:6px">
          <button class="btn btn-outline" id="modalCancel" type="button">Cancel</button>
          <button class="btn btn-primary" id="submitRef" type="submit">Find first available</button>
        </div>
      </form>
    </div>
  </div>

  <!-- Profile Modal -->
  <div class="modal" id="profileModal" aria-hidden="true" role="dialog" aria-modal="true" aria-labelledby="profileTitle">
    <div class="modal-card" role="document">
      <div class="modal-header">
        <h3 id="profileTitle" style="margin:0">Clinician profile</h3>
        <button class="close" aria-label="Close" id="closeProfile">×</button>
      </div>
      <div id="profileBody">
        <!-- populated by JS -->
      </div>
      <div style="display:flex;gap:8px;justify-content:flex-end;margin-top:10px">
        <button class="btn btn-outline" id="profileSchedule">Schedule</button>
      </div>
    </div>
  </div>

  <!-- Toast -->
  <div class="toast" id="toast" role="status" aria-live="polite">Referral received. We’ll guide the next steps (demo).</div>

  <script>
    const $ = (s,scope=document)=>scope.querySelector(s);
    const $$ = (s,scope=document)=>Array.from(scope.querySelectorAll(s));

    const refModal = $('#refModal');
    const refTitle = $('#refTitle');
    const openReferral = $('#openReferral');
    const openReferral2 = $('#openReferral2');
    const openReferral3 = $('#openReferral3');
    const openReferral4 = $('#openReferral4');
    const openSelf = $('#openSelf');
    const openSchedule = $('#openSchedule');
    const openSchedule2 = $('#openSchedule2');
    const closeModal = $('#closeModal');
    const modalCancel = $('#modalCancel');
    const refForm = $('#refForm');
    const toast = $('#toast');
    const year = $('#year');
    const profileModal = $('#profileModal');
    const closeProfile = $('#closeProfile');
    const profileBody = $('#profileBody');
    const profileSchedule = $('#profileSchedule');

    year.textContent = new Date().getFullYear();

    /* Router */
    const routes = ['home','directory','calendar','epic','inbox','partners','faq'];
    function showRoute(hash){
      const id = (hash||'#home').replace('#','');
      routes.forEach(r=>{
        const el = document.getElementById(r);
        if(!el) return;
        el.classList.toggle('active', r===id);
      });
      // nav state
      $$('#mainNav a[data-route]').forEach(a=> a.classList.toggle('active', a.getAttribute('href') === '#'+id));
    }
    window.addEventListener('hashchange',()=> showRoute(location.hash));
    showRoute(location.hash);

    /* Modal helpers */
    function showModal(title){
      refTitle.textContent = title || 'Start a referral';
      refModal.setAttribute('aria-hidden','false');
      setTimeout(()=>{ const first = refForm.querySelector('input,select,textarea,button'); first && first.focus(); }, 0);
    }
    function hideModal(){ refModal.setAttribute('aria-hidden','true'); }
    function showToast(msg){
      toast.textContent = msg; toast.classList.add('show');
      setTimeout(()=> toast.classList.remove('show'), 2400);
    }

    [openReferral,openReferral2,openReferral3,openReferral4].forEach(btn=> btn && btn.addEventListener('click',()=> showModal('Start a referral')));
    openSelf && openSelf.addEventListener('click',()=> showModal("I'd like to get care"));
    ;[openSchedule,openSchedule2].forEach(b=> b && b.addEventListener('click',()=> showModal('Schedule first visit')));

    closeModal.addEventListener('click', hideModal);
    modalCancel.addEventListener('click', hideModal);
    refModal.addEventListener('click', (e)=>{ if(e.target===refModal) hideModal(); });

    // Fake submit
    refForm.addEventListener('submit', ()=>{
      hideModal();
      showToast('Referral received. Next available shown (demo).');
      // Push to inbox (demo)
      addInboxItem({name:'Mari G.', concern:'Anxiety in pregnancy', requested:'Therapy', urgency:'Within 48h'});
      location.hash = '#inbox';
    });

    // Directory: schedule/profile actions
    $$('[data-sched]').forEach(b=> b.addEventListener('click', ()=> showModal('Schedule with this clinician')));

    const profiles = {
      rivera: {
        name:'J. Rivera, LPCC',
        bio:'Licensed Professional Clinical Counselor with 8+ years supporting perinatal mood & anxiety disorders. Trauma‑informed, CBT, IPT.',
        details:'Telehealth across NM • Spanish/English • BCBS, Medicaid',
        tags:['Perinatal Anxiety','CBT','Spanish']
      },
      patel: {
        name:'S. Patel, RD',
        bio:'Registered Dietitian focusing on gestational diabetes, nausea management, and lactation nutrition. Practical plans for busy families.',
        details:'Self‑pay & PPO • Weekend availability',
        tags:['Gestational Diabetes','Lactation','Meal Planning']
      },
      nguyen: {
        name:'A. Nguyen, DPT',
        bio:'Pelvic floor PT helping postpartum recovery, prolapse support, and pain reduction. Hybrid care in Albuquerque.',
        details:'Hybrid • Albuquerque',
        tags:['Postpartum Recovery','Pelvic Pain','Hybrid']
      }
    };

    $$('[data-profile]').forEach(btn=>{
      btn.addEventListener('click',()=>{
        const id = btn.getAttribute('data-profile');
        const p = profiles[id];
        if(!p) return;
        $('#profileTitle').textContent = p.name;
        profileBody.innerHTML = `
          <div class="card">
            <p>${p.bio}</p>
            <p style="color:#64748b">${p.details}</p>
            <div>${p.tags.map(t=>`<span class="pill">${t}</span>`).join('')}</div>
          </div>
          <div class="card" style="margin-top:10px">
            <strong>Reviews (mock)</strong>
            <ul>
              <li>“Compassionate and evidence‑based.”</li>
              <li>“Helped me feel like myself again postpartum.”</li>
            </ul>
          </div>
        `;
        profileModal.setAttribute('aria-hidden','false');
      })
    });
    closeProfile.addEventListener('click',()=> profileModal.setAttribute('aria-hidden','true'));
    profileModal.addEventListener('click',(e)=>{ if(e.target===profileModal) profileModal.setAttribute('aria-hidden','true'); });
    profileSchedule.addEventListener('click',()=>{ profileModal.setAttribute('aria-hidden','true'); showModal('Schedule with this clinician'); });

    // Calendar build
    const calGrid = $('#calGrid');
    const hours = Array.from({length:9}, (_,i)=> 9+i); // 9..17
    const days = ['Mon','Tue','Wed','Thu','Fri'];
    const calKey = 'mbm_calendar_v1';
    let state = JSON.parse(localStorage.getItem(calKey) || '{}');

    function buildCalendar(){
      // remove old rows
      $$('.time', calGrid).forEach(el=> el.remove());
      $$('.slot', calGrid).forEach(el=> el.remove());
      hours.forEach(h=>{
        const label = document.createElement('div');
        label.className = 'time';
        label.textContent = `${String(h).padStart(2,'0')}:00`;
        calGrid.appendChild(label);
        days.forEach((d,di)=>{
          const key = `${d}-${h}`;
          const div = document.createElement('div');
          div.className = 'slot' + (state[key]?' booked':'');
          div.dataset.key = key;
          div.addEventListener('click',()=>{
            state[key] = !state[key];
            div.classList.toggle('booked', !!state[key]);
            localStorage.setItem(calKey, JSON.stringify(state));
          });
          calGrid.appendChild(div);
        });
      });
    }
    buildCalendar();
    $('#clearCal').addEventListener('click',()=>{ state={}; localStorage.removeItem(calKey); buildCalendar(); });
    $('#mockFill').addEventListener('click',()=>{
      // Quick-fill a few booked slots
      ['Mon-10','Mon-11','Tue-13','Wed-9','Thu-15','Fri-11'].forEach(k=> state[k]=true);
      localStorage.setItem(calKey, JSON.stringify(state));
      buildCalendar();
    });

    // Inbox demo
    const inboxList = $('#inboxList');
    let inbox = [];
    function renderInbox(){
      inboxList.innerHTML = '';
      if(inbox.length===0){
        inboxList.innerHTML = '<div class="card">No warm hand‑offs yet. Referrals you create will appear here.</div>';
        return;
      }
      inbox.forEach((item,i)=>{
        const el = document.createElement('div');
        el.className = 'card';
        el.innerHTML = `
          <div style="display:flex;justify-content:space-between;gap:10px;align-items:flex-start">
            <div>
              <strong>${item.name}</strong>
              <div class="lead">${item.concern} • Requested: ${item.requested}</div>
              <div style="font-size:12px;color:#64748b">Urgency: ${item.urgency}</div>
            </div>
            <div style="display:flex;gap:8px;flex-wrap:wrap">
              <button class="btn btn-outline" data-accept="${i}">Accept</button>
              <button class="btn btn-primary" data-schedule="${i}">Schedule</button>
            </div>
          </div>`;
        inboxList.appendChild(el);
      });
      // attach handlers
      $$('[data-accept]', inboxList).forEach(btn=> btn.addEventListener('click',()=>{
        showToast('Hand‑off accepted (demo)');
      }));
      $$('[data-schedule]', inboxList).forEach(btn=> btn.addEventListener('click',()=>{
        showModal('Schedule from warm hand‑off');
      }));
    }
    function addInboxItem(item){ inbox.unshift(item); renderInbox(); }
    renderInbox();

    // Simple demo link
    const openDemo = $('#openDemo');
    openDemo && openDemo.addEventListener('click', ()=>{
      window.scrollTo({top:0,behavior:'smooth'});
      showToast('Demo started — use any Schedule/Refer button.');
    });
  </script>
</body>
</html>
