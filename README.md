<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sainik School</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:Georgia,serif;color:#1a1a2e;background:#f4f1e8;display:flex;min-height:100vh;}
#sidebar{width:220px;background:#0a1628;min-height:100vh;position:fixed;top:0;left:0;z-index:200;display:flex;flex-direction:column;transition:transform 0.3s;}
.sb-logo{padding:20px 18px 14px;border-bottom:1px solid rgba(212,175,55,0.2);}
.sb-logo-title{color:#d4af37;font-size:15px;font-weight:bold;letter-spacing:1px;}
.sb-logo-sub{color:#5a7a9a;font-size:11px;margin-top:3px;}
.sb-nav{padding:12px 0;flex:1;overflow-y:auto;}
.sb-section{padding:8px 18px 4px;font-size:10px;letter-spacing:2px;color:#4a6a8a;text-transform:uppercase;font-family:Arial,sans-serif;}
.sb-link{display:flex;align-items:center;gap:10px;padding:10px 18px;cursor:pointer;transition:all 0.2s;border-left:3px solid transparent;font-family:Arial,sans-serif;}
.sb-link:hover{background:rgba(212,175,55,0.08);border-left-color:rgba(212,175,55,0.4);}
.sb-link.active{background:rgba(212,175,55,0.12);border-left-color:#d4af37;}
.sb-link .sb-icon{font-size:15px;width:20px;text-align:center;}
.sb-link .sb-label{font-size:13px;color:#b0c8e0;}
.sb-link.active .sb-label{color:#d4af37;font-weight:bold;}
.sb-link:hover .sb-label{color:#d4af37;}
.sb-footer{padding:14px 18px;border-top:1px solid rgba(212,175,55,0.15);}
.sb-footer p{font-size:11px;color:#3a5a7a;line-height:1.5;}
#main{margin-left:220px;flex:1;min-height:100vh;}
.topbar{background:#0d1e35;padding:12px 32px;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid rgba(212,175,55,0.15);position:sticky;top:0;z-index:100;}
.topbar-title{color:#d4af37;font-size:16px;font-weight:bold;}
.topbar-right{display:flex;gap:12px;align-items:center;}
.topbar-badge{background:rgba(212,175,55,0.15);border:1px solid rgba(212,175,55,0.3);color:#d4af37;font-size:11px;padding:4px 12px;border-radius:20px;font-family:Arial,sans-serif;}
.page{display:none;padding:36px 40px;max-width:1000px;}
.page.active{display:block;}
.page-hero{background:linear-gradient(135deg,#0a1628,#1a3a5c);border-radius:10px;padding:44px;margin-bottom:32px;position:relative;overflow:hidden;}
.page-hero::after{content:'';position:absolute;right:-20px;top:-20px;width:180px;height:180px;background:rgba(212,175,55,0.05);border-radius:50%;}
.page-hero-tag{font-size:11px;letter-spacing:2px;color:#d4af37;text-transform:uppercase;font-family:Arial,sans-serif;margin-bottom:10px;}
.page-hero h1{font-size:32px;color:#fff;margin-bottom:12px;line-height:1.3;}
.page-hero p{font-size:15px;color:#7a9bbf;line-height:1.8;max-width:680px;}
.card{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:26px;margin-bottom:20px;}
.card h3{font-size:18px;color:#0a1628;margin-bottom:12px;display:flex;align-items:center;gap:10px;}
.card p{font-size:14px;color:#555;line-height:1.9;}
.card ul{padding-left:18px;margin-top:10px;}
.card ul li{font-size:14px;color:#444;padding:4px 0;line-height:1.7;}
.card-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:20px;}
.card-grid .card{margin:0;}
.card-accent{border-left:4px solid #d4af37;}
.card-dark{background:#0a1628;border-color:#0a1628;}
.card-dark h3{color:#d4af37;}
.card-dark p{color:#aac4e0;}
.card-dark ul li{color:#aac4e0;}
.stat-row{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:28px;}
.stat-box{background:#0a1628;border-radius:8px;padding:20px;text-align:center;}
.stat-box .num{font-size:28px;font-weight:bold;color:#d4af37;}
.stat-box .lbl{font-size:11px;color:#5a7a9a;letter-spacing:1px;margin-top:4px;font-family:Arial,sans-serif;}
.why-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-bottom:20px;}
.why-c{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:22px;border-top:3px solid #d4af37;}
.why-c .wi{font-size:28px;margin-bottom:10px;}
.why-c h4{font-size:14px;color:#0a1628;margin-bottom:8px;font-weight:bold;}
.why-c p{font-size:13px;color:#555;line-height:1.7;}
.step-list{display:flex;flex-direction:column;gap:0;}
.step-row{display:flex;gap:20px;align-items:flex-start;padding:20px 0;border-bottom:1px solid #e8e2d4;}
.step-row:last-child{border:none;}
.step-n{width:44px;height:44px;background:#0a1628;color:#d4af37;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:bold;font-size:18px;flex-shrink:0;}
.step-body h4{font-size:15px;color:#0a1628;margin-bottom:6px;font-weight:bold;}
.step-body p{font-size:14px;color:#555;line-height:1.7;}
.elig-grid{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:20px;}
.elig-box{background:#0a1628;border-radius:8px;padding:22px;}
.elig-box h4{color:#d4af37;font-size:13px;letter-spacing:1px;text-transform:uppercase;margin-bottom:12px;font-family:Arial,sans-serif;}
.elig-box li{color:#aac4e0;font-size:13px;padding:5px 0;border-bottom:1px solid rgba(255,255,255,0.05);list-style:none;}
.elig-box li::before{content:'✓ ';color:#d4af37;}
.subject-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:24px;}
.subj{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:22px;border-left:4px solid #0a1628;}
.subj h4{font-size:15px;color:#0a1628;margin-bottom:12px;}
.subj li{font-size:13px;color:#444;padding:4px 0;list-style:none;line-height:1.6;}
.subj li::before{content:'▸ ';color:#d4af37;}
.tips-dark{background:#0a1628;border-radius:10px;padding:28px;margin-top:4px;}
.tips-dark h3{color:#d4af37;font-size:18px;margin-bottom:20px;}
.tips-dark-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
.tip-row{display:flex;gap:12px;align-items:flex-start;}
.tip-n{width:26px;height:26px;background:#d4af37;color:#0a1628;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:bold;font-size:12px;flex-shrink:0;}
.tip-row p{font-size:13px;color:#aac4e0;line-height:1.6;}
.schools-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
.school-card{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:18px;transition:all 0.2s;}
.school-card:hover{border-color:#d4af37;box-shadow:0 4px 16px rgba(212,175,55,0.1);}
.sc-state{font-size:11px;letter-spacing:1px;text-transform:uppercase;color:#d4af37;margin-bottom:5px;font-family:Arial,sans-serif;}
.school-card h4{font-size:14px;color:#0a1628;margin-bottom:5px;font-weight:bold;}
.school-card p{font-size:12px;color:#666;line-height:1.6;}
.schedule{border-radius:10px;overflow:hidden;border:1px solid #e0d9c8;margin-bottom:24px;}
.sch-row{display:flex;border-bottom:1px solid #e8e2d4;}
.sch-row:last-child{border:none;}
.sch-time{padding:13px 16px;min-width:110px;background:#0a1628;color:#d4af37;font-size:12px;font-weight:bold;font-family:Arial,sans-serif;}
.sch-act{padding:13px 16px;color:#333;font-size:14px;background:#fff;}
.extra-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-top:16px;}
.extra-pill{background:#fff;border-radius:8px;border:1px solid #e0d9c8;padding:16px;text-align:center;}
.extra-pill .ei{font-size:22px;margin-bottom:8px;}
.extra-pill p{font-size:12px;color:#444;font-family:Arial,sans-serif;font-weight:bold;margin-bottom:4px;}
.extra-pill span{font-size:11px;color:#888;line-height:1.4;display:block;}
.faq-item{background:#fff;border-radius:8px;margin-bottom:10px;overflow:hidden;border:1px solid #e0d9c8;}
.faq-q{padding:16px 20px;cursor:pointer;font-size:14px;color:#0a1628;font-weight:bold;display:flex;justify-content:space-between;align-items:center;font-family:Arial,sans-serif;}
.faq-q:hover{background:#f9f7f1;}
.faq-a{padding:0 20px 16px;font-size:14px;color:#555;line-height:1.9;display:none;}
.faq-a.open{display:block;}
.faq-tog{color:#d4af37;font-size:18px;}
.alumni-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
.al-card{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:20px;position:relative;}
.al-card::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:linear-gradient(90deg,#d4af37,#0a1628);border-radius:10px 10px 0 0;}
.al-av{width:52px;height:52px;background:#0a1628;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:20px;margin-bottom:14px;}
.al-card h4{font-size:15px;color:#0a1628;margin-bottom:3px;}
.al-role{font-size:11px;color:#d4af37;font-weight:bold;letter-spacing:0.5px;margin-bottom:10px;text-transform:uppercase;font-family:Arial,sans-serif;}
.al-card p{font-size:13px;color:#555;line-height:1.7;}
.cta-banner{background:linear-gradient(135deg,#d4af37,#b8932a);border-radius:10px;padding:36px;text-align:center;margin-top:24px;}
.cta-banner h3{font-size:22px;color:#0a1628;margin-bottom:10px;}
.cta-banner p{font-size:14px;color:#3a2800;margin-bottom:20px;line-height:1.7;}
.btn-dark{background:#0a1628;color:#d4af37;padding:12px 32px;border-radius:4px;font-weight:bold;font-size:14px;display:inline-block;cursor:pointer;font-family:Arial,sans-serif;}
.btn-dark:hover{background:#0d2137;}
.info-strip{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-bottom:20px;}
.info-box{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:20px;text-align:center;}
.info-box .ib-icon{font-size:30px;margin-bottom:10px;}
.info-box h4{font-size:14px;color:#0a1628;margin-bottom:6px;font-weight:bold;}
.info-box p{font-size:13px;color:#666;line-height:1.6;}
.timeline{position:relative;padding-left:32px;margin:16px 0;}
.timeline::before{content:'';position:absolute;left:8px;top:0;bottom:0;width:2px;background:#d4af37;}
.tl-item{position:relative;margin-bottom:24px;}
.tl-dot{position:absolute;left:-28px;top:4px;width:14px;height:14px;background:#d4af37;border-radius:50%;border:2px solid #fff;}
.tl-year{font-size:11px;color:#d4af37;font-weight:bold;font-family:Arial,sans-serif;letter-spacing:1px;margin-bottom:4px;}
.tl-item h4{font-size:14px;color:#0a1628;margin-bottom:4px;font-weight:bold;}
.tl-item p{font-size:13px;color:#555;line-height:1.7;}
.subject-detail{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:22px;margin-bottom:16px;border-left:4px solid #d4af37;}
.subject-detail h4{font-size:16px;color:#0a1628;margin-bottom:6px;}
.subject-detail .sd-meta{font-size:12px;color:#d4af37;font-family:Arial,sans-serif;margin-bottom:12px;font-weight:bold;}
.subject-detail p{font-size:14px;color:#555;line-height:1.8;margin-bottom:10px;}
.subject-detail ul{padding-left:16px;}
.subject-detail ul li{font-size:13px;color:#444;padding:3px 0;line-height:1.6;}
.book-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:16px;}
.book-card{background:#0a1628;border-radius:8px;padding:14px;text-align:center;}
.book-card .bc-icon{font-size:24px;margin-bottom:8px;}
.book-card h5{font-size:13px;color:#d4af37;margin-bottom:4px;}
.book-card p{font-size:11px;color:#5a7a9a;line-height:1.5;}
.pillar-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:16px;margin-bottom:20px;}
.pillar{background:#fff;border-radius:10px;border:1px solid #e0d9c8;padding:22px;}
.pillar h4{font-size:15px;color:#0a1628;margin-bottom:10px;display:flex;align-items:center;gap:8px;}
.pillar p{font-size:14px;color:#555;line-height:1.8;margin-bottom:8px;}
.pillar ul{padding-left:16px;}
.pillar ul li{font-size:13px;color:#444;padding:3px 0;}
.menu-btn{display:none;background:none;border:none;color:#d4af37;font-size:22px;cursor:pointer;padding:4px;}
.tag-row{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;}
.tag{background:#f4f1e8;border:1px solid #d4af37;color:#0a1628;font-size:12px;padding:4px 12px;border-radius:20px;font-family:Arial,sans-serif;}
.quote-box{background:#f9f7f1;border-left:4px solid #d4af37;border-radius:0 8px 8px 0;padding:18px 22px;margin:16px 0;font-style:italic;color:#333;font-size:14px;line-height:1.8;}
.quote-box span{display:block;margin-top:8px;font-size:12px;color:#888;font-style:normal;}
@media(max-width:768px){
  #sidebar{transform:translateX(-220px);}
  #sidebar.open{transform:translateX(0);}
  #main{margin-left:0;}
  .menu-btn{display:block;}
  .card-grid,.subject-grid,.why-grid,.alumni-grid,.schools-grid,.tips-dark-grid,.elig-grid,.stat-row,.pillar-grid,.info-strip{grid-template-columns:1fr 1fr;}
  .extra-grid{grid-template-columns:1fr 1fr;}
  .page{padding:20px;}
}
</style>
</head>
<body>

<div id="sidebar">
  <div class="sb-logo">
    <div class="sb-logo-title">⚔ SAINIK SCHOOL</div>
    <div class="sb-logo-sub">Shaping Leaders for the Nation</div>
  </div>
  <nav class="sb-nav">
    <div class="sb-section">Main</div>
    <div class="sb-link active" onclick="goTo('home')"><span class="sb-icon">🏠</span><span class="sb-label">Home</span></div>
    <div class="sb-link" onclick="goTo('about')"><span class="sb-icon">🛡️</span><span class="sb-label">About Sainik Schools</span></div>
    <div class="sb-link" onclick="goTo('why')"><span class="sb-icon">🌟</span><span class="sb-label">Why Join?</span></div>
    <div class="sb-link" onclick="goTo('alumni')"><span class="sb-icon">🎖️</span><span class="sb-label">Alumni & Careers</span></div>
    <div class="sb-section">Admission</div>
    <div class="sb-link" onclick="goTo('admission')"><span class="sb-icon">📋</span><span class="sb-label">Admission Process</span></div>
    <div class="sb-link" onclick="goTo('prep')"><span class="sb-icon">📚</span><span class="sb-label">Exam Preparation</span></div>
    <div class="sb-section">Schools & Life</div>
    <div class="sb-link" onclick="goTo('schools')"><span class="sb-icon">🗺️</span><span class="sb-label">Schools Across India</span></div>
    <div class="sb-link" onclick="goTo('life')"><span class="sb-icon">⏰</span><span class="sb-label">Life at Sainik School</span></div>
    <div class="sb-section">Help</div>
    <div class="sb-link" onclick="goTo('faq')"><span class="sb-icon">❓</span><span class="sb-label">FAQ</span></div>
    <div class="sb-link" onclick="window.open('https://sainikschool.sarv.net','_blank')"><span class="sb-icon">🔗</span><span class="sb-label">Official Portal ↗</span></div>
  </nav>
  <div class="sb-footer"><p>Info sourced from Sainik Schools Society & NTA. Always verify on the official portal.</p></div>
</div>

<div id="main">
  <div class="topbar">
    <div style="display:flex;align-items:center;gap:14px;">
      <button class="menu-btn" onclick="toggleSidebar()">☰</button>
      <div class="topbar-title" id="topbar-title">Home</div>
    </div>
    <div class="topbar-right">
      <div class="topbar-badge">Est. 1961</div>
      <div class="topbar-badge">33+ Schools</div>
    </div>
  </div>

  <!-- HOME -->
  <div class="page active" id="page-home">
    <div class="page-hero">
      <div class="page-hero-tag">Welcome to Sainik School</div>
      <h1>Where Boys Become<br/>Leaders of the Nation</h1>
      <p>Sainik Schools are India's most prestigious residential institutions — forging discipline, academic brilliance, and physical excellence in young minds since 1961. They are the gateway to the National Defence Academy and a lifetime of national service.</p>
    </div>
    <div class="stat-row">
      <div class="stat-box"><div class="num">33+</div><div class="lbl">Schools in India</div></div>
      <div class="stat-box"><div class="num">60+</div><div class="lbl">Years of Excellence</div></div>
      <div class="stat-box"><div class="num">1000s</div><div class="lbl">Officers Produced</div></div>
      <div class="stat-box"><div class="num">NDA</div><div class="lbl">Top Feeder</div></div>
    </div>
    <div class="card card-accent">
      <h3>🇮🇳 A Legacy of National Service</h3>
      <p>Sainik Schools have been shaping the leaders of tomorrow for over six decades. Established by the Ministry of Defence in 1961, these schools were designed with a singular, powerful purpose: to prepare India's youth — mentally, physically, and academically — to serve the nation through its most prestigious defence academies. Today, Sainik School alumni can be found commanding battalions, piloting fighter jets, navigating submarines, leading civil services, and breaking records in sports. The Sainik School network is not just a group of schools — it is a movement that has transformed hundreds of thousands of young lives and produced some of India's most distinguished leaders.</p>
    </div>
    <div class="card-grid">
      <div class="card card-accent" style="cursor:pointer" onclick="goTo('about')"><h3>🛡️ About Sainik Schools</h3><p>Learn about the rich history, governing structure, and national mission of India's premier defence-oriented residential school network, established in 1961.</p></div>
      <div class="card card-accent" style="cursor:pointer" onclick="goTo('why')"><h3>🌟 Why Join?</h3><p>Discover the compelling reasons why thousands of families across India choose Sainik Schools — from NDA pathways to lifelong brotherhood and career success.</p></div>
      <div class="card card-accent" style="cursor:pointer" onclick="goTo('admission')"><h3>📋 Admission Process</h3><p>A complete step-by-step guide to the AISSEE entrance exam, eligibility criteria, important dates, required documents, and what to expect at each stage.</p></div>
      <div class="card card-accent" style="cursor:pointer" onclick="goTo('prep')"><h3>📚 Exam Preparation</h3><p>Detailed subject-wise preparation strategies, recommended books, study timetables, mock test advice, and the top 8 expert tips to crack the AISSEE.</p></div>
      <div class="card card-accent" style="cursor:pointer" onclick="goTo('schools')"><h3>🗺️ Schools Across India</h3><p>Browse all major Sainik Schools by state, learn about each school's unique character, and find the right institution for your child's future.</p></div>
      <div class="card card-accent" style="cursor:pointer" onclick="goTo('life')"><h3>⏰ Life at Sainik School</h3><p>A detailed look at the daily routine, sports culture, extracurricular activities, hostel life, and the full cadet experience inside the campus.</p></div>
    </div>
    <div class="quote-box">"A Sainik School education is the greatest gift a parent can give their child — not just knowledge, but character, discipline, and an unshakeable sense of purpose in service of the nation."<span>— Sentiment shared by thousands of Sainik School parents and alumni across India</span></div>
    <div class="cta-banner">
      <h3>Ready to Begin the Journey?</h3>
      <p>Apply for admission through the official Sainik Schools portal. Registrations open every year — do not miss the window for your child's future.</p>
      <div class="btn-dark" onclick="window.open('https://sainikschool.sarv.net','_blank')">Apply on Official Portal ↗</div>
    </div>
  </div>

  <!-- ABOUT -->
  <div class="page" id="page-about">
    <div class="page-hero">
      <div class="page-hero-tag">Our Legacy</div>
      <h1>About Sainik Schools</h1>
      <p>India's premier residential institutions — blending military values with academic excellence to shape the next generation of national leaders since 1961.</p>
    </div>
    <div class="card card-accent">
      <h3>🏛️ History & Origin</h3>
      <p>The Sainik School concept was born from a vision to strengthen India's defence forces by preparing young men for entry into the National Defence Academy (NDA) and the Naval Academy (NA). The first Sainik School was established at Satara, Maharashtra in 1961, under the stewardship of the Ministry of Defence. The founding principle was simple but transformative: if India could identify talented young boys and provide them with world-class residential education combining academics, physical training, and character-building, the country would produce a steady supply of outstanding officers for the armed forces.</p>
      <p>Over the decades, the network expanded dramatically. By the 1980s, every major state had at least one Sainik School. In 2021, the Government of India announced a major expansion — new-pattern Sainik Schools set up in partnership with state governments and private educational institutions, further democratising access to this prestigious education.</p>
    </div>
    <div class="card"><h3>📅 Timeline of Growth</h3>
      <div class="timeline">
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-year">1961</div><h4>Sainik School Satara — The First</h4><p>India's first Sainik School opens in Maharashtra, setting the gold standard for military-oriented residential education across the country.</p></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-year">1960s–70s</div><h4>Rapid National Expansion</h4><p>Sainik Schools established across multiple states including Rajasthan, Kerala, Punjab, Haryana, and Odisha, building a truly national network of excellence.</p></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-year">1980s–2000s</div><h4>Consolidation & Excellence</h4><p>The schools mature into world-class institutions with strong NDA selection records, modern infrastructure, and a growing alumni legacy in all three armed forces.</p></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-year">2021</div><h4>Girls Admitted & New Schools</h4><p>A landmark year — girls allowed to apply to Sainik Schools for the first time. Government announces major expansion with 100 new-pattern Sainik Schools across India.</p></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-year">Today</div><h4>33+ Schools, Thousands of Leaders</h4><p>The Sainik School network continues to grow, with over 33 traditional schools and a rapidly expanding new-pattern network producing India's finest leaders every year.</p></div>
      </div>
    </div>
    <div class="card-grid">
      <div class="card"><h3>🎯 Mission & Vision</h3><p>To prepare students academically, physically, and mentally for careers in the Indian Armed Forces while instilling values of discipline, integrity, patriotism, and national pride. The vision extends beyond the military — Sainik Schools aim to produce well-rounded citizens who contribute meaningfully to every sphere of national life.</p></div>
      <div class="card"><h3>🏫 Affiliation & Board</h3><p>All Sainik Schools are affiliated with the Central Board of Secondary Education (CBSE) and managed under the Sainik Schools Society — an autonomous body under the Ministry of Defence. Admissions are conducted centrally by the National Testing Agency (NTA) through the AISSEE examination each year.</p></div>
      <div class="card"><h3>⚖️ Governing Structure</h3><p>The Sainik Schools Society is chaired by the Raksha Mantri (Defence Minister) of India. Each school has its own Board of Governors with representation from the state government, Ministry of Defence, and the Army. This dual oversight ensures both national standards and local relevance are maintained.</p></div>
      <div class="card"><h3>💰 Financial Support</h3><p>The central government substantially subsidises Sainik School education, making it far more affordable than comparable private boarding schools. Additional scholarships and fee waivers are available for students from SC/ST backgrounds and economically weaker sections, ensuring that merit — not money — determines who gets this education.</p></div>
    </div>
    <div class="cta-banner">
      <h3>Want to Know More?</h3>
      <p>Visit the official Sainik Schools Society website for complete institutional details, policies, and updates.</p>
      <div class="btn-dark" onclick="window.open('https://sainikschool.sarv.net','_blank')">Visit Official Site ↗</div>
    </div>
  </div>

  <!-- WHY JOIN -->
  <div class="page" id="page-why">
    <div class="page-hero">
      <div class="page-hero-tag">Compelling Reasons</div>
      <h1>Why Choose Sainik School?</h1>
      <p>A Sainik School education is not just schooling — it is a complete transformation of your child into a confident, disciplined, and purposeful leader ready to serve the nation and excel in any field of life.</p>
    </div>
    <div class="card card-accent">
      <h3>🌟 The Sainik School Difference</h3>
      <p>Most schools teach subjects. Sainik Schools build people. The combination of rigorous academics, daily physical training, leadership responsibilities, and a strong value system creates graduates who are fundamentally different from their peers — more focused, more resilient, more capable, and more purposeful. This is not marketing language. It is the lived experience of thousands of Sainik School alumni who credit their school with shaping everything good about their adult lives.</p>
    </div>
    <div class="why-grid">
      <div class="why-c"><div class="wi">🎖️</div><h4>Gateway to the NDA</h4><p>Sainik Schools are the single largest feeder institutions for the National Defence Academy. The training, preparation, and culture of these schools align perfectly with NDA requirements — giving Sainik School students a massive advantage in the entrance exam and interview process.</p></div>
      <div class="why-c"><div class="wi">🧠</div><h4>Holistic Education</h4><p>Beyond textbooks, students develop critical thinking, situational awareness, emotional intelligence, and a deep sense of national purpose. These are qualities that serve them not just in the military, but in every career and life situation they encounter.</p></div>
      <div class="why-c"><div class="wi">💪</div><h4>Physical Excellence</h4><p>Daily PT, swimming, obstacle courses, drill, and mandatory sports build a level of physical fitness unmatched in conventional schools. Students graduate not just fit, but with healthy habits, discipline, and a warrior's mindset towards challenges.</p></div>
      <div class="why-c"><div class="wi">🤝</div><h4>Lifelong Brotherhood</h4><p>The bonds formed at Sainik School — living together, training together, facing challenges together — are unlike any other friendship. Alumni networks are incredibly strong, providing support, mentorship, and opportunity across every field and every decade of life.</p></div>
      <div class="why-c"><div class="wi">🏅</div><h4>Prestigious Alumni Network</h4><p>From decorated war heroes to IAS officers, IIT graduates, Olympians, and successful entrepreneurs — Sainik School alumni occupy positions of leadership and influence across every sector of Indian society. This network opens doors throughout your child's career.</p></div>
      <div class="why-c"><div class="wi">🇮🇳</div><h4>Patriotism & Purpose</h4><p>Students graduate with a deep, genuine love for their country and a clarity of purpose that most young people never find. Whether they serve in uniform or in civilian life, this sense of purpose drives extraordinary achievement and meaningful contribution.</p></div>
      <div class="why-c"><div class="wi">📚</div><h4>CBSE Academic Excellence</h4><p>High academic standards, experienced and dedicated faculty, well-equipped science and computer labs, and a structured learning environment produce students who excel in board exams, competitive exams, and university education alike.</p></div>
      <div class="why-c"><div class="wi">🏆</div><h4>Diverse Career Paths</h4><p>While the military is the primary focus, the discipline, education, and leadership skills from Sainik Schools prepare alumni for extraordinary success in the IITs, IIMs, UPSC civil services, professional sports, medicine, law, and entrepreneurship.</p></div>
      <div class="why-c"><div class="wi">🌟</div><h4>Scholarships & Affordability</h4><p>Government subsidies, merit scholarships, and fee concessions for EWS, SC/ST students ensure that a Sainik School education — worth lakhs in private boarding schools — is accessible to every deserving child, regardless of their family's financial background.</p></div>
    </div>
    <div class="pillar-grid">
      <div class="pillar"><h4>🧭 Character Building</h4><p>The Sainik School environment is carefully designed to build character qualities that last a lifetime:</p><ul><li>Honesty and integrity in all situations</li><li>Responsibility and accountability for actions</li><li>Respect for elders, peers, and subordinates</li><li>Courage to face adversity and challenge</li><li>Compassion and empathy towards others</li></ul></div>
      <div class="pillar"><h4>🏋️ Physical Development</h4><p>Physical fitness is not optional at Sainik School — it is a core pillar of education:</p><ul><li>Daily morning PT and drill sessions</li><li>Swimming as a mandatory activity</li><li>Obstacle and confidence courses</li><li>At least one sport compulsory for every student</li><li>Annual fitness assessments and tracking</li></ul></div>
    </div>
  </div>

  <!-- ALUMNI -->
  <div class="page" id="page-alumni">
    <div class="page-hero">
      <div class="page-hero-tag">Hall of Fame</div>
      <h1>Alumni & Careers</h1>
      <p>Sainik School graduates are found at the very pinnacle of India's armed forces, civil services, sciences, sports, and industry — a testament to the power of this extraordinary education.</p>
    </div>
    <div class="card card-accent">
      <h3>🌍 Where Alumni Serve</h3>
      <p>The impact of a Sainik School education radiates far beyond the armed forces. While the NDA and military remain the primary career destination, Sainik School alumni have made their mark in virtually every field of national life. This breadth of achievement is a direct result of the holistic education these schools provide — an education that does not just prepare students for one career, but for life itself.</p>
    </div>
    <div class="alumni-grid">
      <div class="al-card"><div class="al-av">🎖</div><h4>Indian Army</h4><div class="al-role">Generals & Chiefs of Army Staff</div><p>Multiple Chiefs of Army Staff and hundreds of serving Generals commanding India's mightiest land force began their journey at a Sainik School. The Army's officer corps counts thousands of Sainik School alumni in its ranks at every level of command.</p></div>
      <div class="al-card"><div class="al-av">✈️</div><h4>Indian Air Force</h4><div class="al-role">Air Marshals & Fighter Pilots</div><p>From supersonic fighter pilots to test pilots and Air Marshals, Sainik School alumni have taken to India's skies with distinction. The IAF's officer cadre has a strong and proud Sainik School contingent at its core.</p></div>
      <div class="al-card"><div class="al-av">⚓</div><h4>Indian Navy</h4><div class="al-role">Admirals & Naval Commanders</div><p>Submarine commanders, Fleet Admirals, and naval aviation officers — Sainik School graduates have led the Indian Navy with exceptional skill and valour across decades of service to the nation.</p></div>
      <div class="al-card"><div class="al-av">🏛</div><h4>Civil Services</h4><div class="al-role">IAS, IPS & IFS Officers</div><p>The analytical rigor, discipline, and broad education of Sainik Schools have produced numerous IAS, IPS, and IFS officers who now serve as District Collectors, Commissioners, Ambassadors, and senior administrators across every state of India.</p></div>
      <div class="al-card"><div class="al-av">🚀</div><h4>Science & Technology</h4><div class="al-role">ISRO, DRDO & IIT Alumni</div><p>Sainik Schools' strong STEM foundation and disciplined study habits have produced leading scientists at ISRO, weapons researchers at DRDO, and professors at India's top IITs and research institutions contributing to national development.</p></div>
      <div class="al-card"><div class="al-av">🏅</div><h4>Sports Champions</h4><div class="al-role">Olympians & National Players</div><p>The intense sports culture at Sainik Schools has produced national-level athletes and Olympians across disciplines including shooting, boxing, athletics, wrestling, and equestrian sports — making India proud on the world stage.</p></div>
    </div>
    <div class="card card-dark" style="margin-top:20px;">
      <h3>💼 Career Pathways After Sainik School</h3>
      <p>After completing Class XII from a Sainik School, students are exceptionally well-positioned for multiple prestigious career pathways:</p>
      <ul>
        <li>National Defence Academy (NDA) — the primary and most prestigious pathway for Sainik School graduates</li>
        <li>Naval Academy (NA) — direct entry to the Indian Navy officer training programme</li>
        <li>Joint Entrance Exam (JEE) — IITs, NITs, and top engineering colleges across India</li>
        <li>UPSC Civil Services Examination — IAS, IPS, IFS, and other central services</li>
        <li>Medical entrance (NEET) — AIIMS, JIPMER, and top medical colleges</li>
        <li>State police and paramilitary services — CRPF, BSF, CISF officer programmes</li>
        <li>Sports quota — national and international representation in multiple disciplines</li>
      </ul>
    </div>
    <div class="quote-box">"When I walk into any room — whether it is a boardroom, a battlefield, or a courtroom — I carry Sainik School with me. It gave me the confidence to face anything."<span>— Sentiment shared by alumni across professions and generations</span></div>
  </div>

  <!-- ADMISSION -->
  <div class="page" id="page-admission">
    <div class="page-hero">
      <div class="page-hero-tag">Admission Guide</div>
      <h1>Admission Process</h1>
      <p>Admission to Sainik Schools is through the All India Sainik Schools Entrance Examination (AISSEE), conducted by the National Testing Agency (NTA) every year. Here is everything you need to know.</p>
    </div>
    <div class="info-strip">
      <div class="info-box"><div class="ib-icon">📅</div><h4>When to Apply</h4><p>Registration typically opens October–November. The exam is held in January. Check the NTA portal for current year dates.</p></div>
      <div class="info-box"><div class="ib-icon">📝</div><h4>Exam Format</h4><p>Objective MCQ paper. Class VI: Maths, Language, GK, Intelligence. Class IX: Maths, English, GK, Science, Social Studies.</p></div>
      <div class="info-box"><div class="ib-icon">💰</div><h4>Application Fee</h4><p>Approximately ₹400 for general category. Reduced fees for SC/ST applicants. Payment made online through the NTA portal.</p></div>
    </div>
    <div class="card">
      <h3>📝 Step-by-Step Admission Process</h3>
      <div class="step-list">
        <div class="step-row"><div class="step-n">1</div><div class="step-body"><h4>Check Eligibility</h4><p>Verify your child's age and educational eligibility for Class VI or Class IX entry. Ensure they meet the age bracket as of 31 March of the admission year and have passed the required class from a recognised school. Medical fitness standards should also be reviewed early — the official AISSEE notification publishes detailed medical requirements each year.</p></div></div>
        <div class="step-row"><div class="step-n">2</div><div class="step-body"><h4>Register Online</h4><p>Visit the official NTA portal during the registration window (typically October–November). Fill the application form carefully with accurate personal, academic, and category details. Upload scanned copies of required documents including birth certificate, recent passport photo, and class mark sheet. Pay the application fee online and download the confirmation page.</p></div></div>
        <div class="step-row"><div class="step-n">3</div><div class="step-body"><h4>Download Admit Card</h4><p>Admit cards are released approximately 2–3 weeks before the examination date. Download and print the admit card from the NTA portal. Verify all details on the admit card carefully. The admit card is mandatory for entry to the examination hall — no candidate will be admitted without it.</p></div></div>
        <div class="step-row"><div class="step-n">4</div><div class="step-body"><h4>Appear for AISSEE</h4><p>The All India Sainik Schools Entrance Examination is conducted at designated centres across India, usually in January. The exam is an objective MCQ paper. Class VI students are tested on Mathematics, Language, General Knowledge, and Intelligence/Reasoning. Class IX students additionally face Science and Social Studies sections. Arrive at the exam centre well in advance with your admit card and a valid photo ID.</p></div></div>
        <div class="step-row"><div class="step-n">5</div><div class="step-body"><h4>Results & Shortlisting</h4><p>Results are published on the NTA portal within 4–6 weeks of the examination. Shortlisted students are identified based on merit rank and school-wise cut-offs. Each school has separate merit lists for general, SC/ST, and defence quota categories. Students who clear the written exam are called for the next stage.</p></div></div>
        <div class="step-row"><div class="step-n">6</div><div class="step-body"><h4>Medical Examination</h4><p>Shortlisted candidates must undergo a detailed medical fitness examination conducted by a designated government medical board. The exam checks vision, hearing, height, weight, general health, and the absence of any disqualifying physical conditions. Students are advised to maintain good health and fitness well before the examination.</p></div></div>
        <div class="step-row"><div class="step-n">7</div><div class="step-body"><h4>Document Verification</h4><p>Candidates who clear the medical examination are called for document verification. Original documents must be presented including birth certificate, class mark sheets, category certificate (if applicable), domicile certificate, and the school's recommendation. Ensure all documents are authentic and in order well before this stage.</p></div></div>
        <div class="step-row"><div class="step-n">8</div><div class="step-body"><h4>Admission & Joining</h4><p>Final selection is based on overall merit from the written examination, with medical fitness as a mandatory qualifier. Selected students receive an official admission offer letter. Fee payment, document submission, and joining formalities must be completed within the deadline specified in the offer letter.</p></div></div>
      </div>
    </div>
    <div class="elig-grid">
      <div class="elig-box"><h4>Class VI Entry</h4><ul><li>Age: 10–12 years as of 31 March of admission year</li><li>Must have passed Class V from a recognised school</li><li>Boys and girls eligible (varies by school)</li><li>Indian nationality required</li><li>Medical fitness is mandatory</li><li>Defence quota available for wards of serving/retired personnel</li></ul></div>
      <div class="elig-box"><h4>Class IX Entry</h4><ul><li>Age: 13–15 years as of 31 March of admission year</li><li>Must have passed Class VIII from a recognised school</li><li>Subject to seat availability at each school</li><li>Indian nationality required</li><li>Medical fitness is mandatory</li><li>Exam syllabus includes Science and Social Studies additionally</li></ul></div>
    </div>
    <div class="card" style="margin-top:20px;">
      <h3>📄 Documents Required</h3>
      <p>Keep these documents ready well before the application window opens:</p>
      <div class="tag-row">
        <span class="tag">Birth Certificate</span><span class="tag">Class Mark Sheet</span><span class="tag">Passport Photo</span><span class="tag">Domicile Certificate</span><span class="tag">Caste Certificate (if applicable)</span><span class="tag">Defence ID (if applicable)</span><span class="tag">School Leaving Certificate</span><span class="tag">Aadhar Card</span>
      </div>
    </div>
    <div class="cta-banner">
      <h3>Apply Now on the Official Portal</h3>
      <p>Registrations open annually in October–November. Do not miss the window — seats are limited and competition is high. Start preparing your child today.</p>
      <div class="btn-dark" onclick="window.open('https://sainikschool.sarv.net','_blank')">Go to Admission Portal ↗</div>
    </div>
  </div>

  <!-- EXAM PREP -->
  <div class="page" id="page-prep">
    <div class="page-hero">
      <div class="page-hero-tag">AISSEE Preparation</div>
      <h1>How to Crack the AISSEE</h1>
      <p>The All India Sainik Schools Entrance Exam is competitive but very achievable with the right strategy, the right resources, and consistent hard work. This is your complete preparation guide.</p>
    </div>
    <div class="card card-accent">
      <h3>📊 Exam Pattern Overview</h3>
      <p>The AISSEE is a multiple-choice objective examination conducted by NTA. Understanding the pattern is the first step to cracking it:</p>
      <ul>
        <li>Class VI exam: 4 sections — Mathematics (50 marks), Language/GK (25 marks each), Intelligence (25 marks) — Total 125 marks</li>
        <li>Class IX exam: 5 sections — Mathematics, English, GK, Science, Social Studies — Total 300 marks</li>
        <li>Duration: approximately 2.5 hours for Class VI, 3 hours for Class IX</li>
        <li>No negative marking — attempt every question</li>
        <li>Medium of exam: English and Hindi</li>
      </ul>
    </div>
    <div class="subject-detail">
      <h4>📐 Mathematics</h4>
      <div class="sd-meta">Highest Weightage — 50 marks (Class VI) | Focus: Speed & Accuracy</div>
      <p>Mathematics is the most heavily weighted section and the key differentiator between candidates. The syllabus covers the Class V (for Class VI entry) or Class VIII (for Class IX entry) NCERT curriculum. Focus on building both conceptual understanding and calculation speed.</p>
      <ul>
        <li>Number system: LCM, HCF, prime numbers, divisibility rules</li>
        <li>Arithmetic: percentages, profit/loss, simple interest, ratio and proportion</li>
        <li>Geometry: triangles, circles, quadrilaterals, angles, area and perimeter</li>
        <li>Measurement: time, distance, speed, units of measurement</li>
        <li>Data handling: basic graphs, averages, and tables</li>
        <li>Practice strategy: solve minimum 50 problems daily from NCERT + practice books</li>
      </ul>
    </div>
    <div class="subject-detail">
      <h4>🔤 Language (English & Hindi)</h4>
      <div class="sd-meta">25 marks each | Focus: Vocabulary, Grammar & Comprehension</div>
      <p>The language sections test reading comprehension, vocabulary, grammar, and writing skills. Both English and Hindi are tested separately. Regular reading is the single most effective preparation strategy for this section.</p>
      <ul>
        <li>Reading comprehension: understand unseen passages and answer questions accurately</li>
        <li>Vocabulary: synonyms, antonyms, one-word substitution, idioms and phrases</li>
        <li>Grammar: tenses, articles, prepositions, subject-verb agreement, active/passive voice</li>
        <li>Sentence correction: identify and correct grammatical errors in sentences</li>
        <li>Daily habit: read an English newspaper and a Hindi newspaper every morning</li>
        <li>Practice previous years' language papers to understand question format</li>
      </ul>
    </div>
    <div class="subject-detail">
      <h4>🌍 General Knowledge</h4>
      <div class="sd-meta">25 marks | Focus: India-Centric Knowledge + Current Affairs</div>
      <p>The GK section covers a broad range of topics with a strong focus on India — its geography, history, culture, and current events. Consistent reading over months is more effective than last-minute cramming for this section.</p>
      <ul>
        <li>Indian geography: rivers, mountains, states, capitals, national parks, climate zones</li>
        <li>Indian history: ancient civilisations, medieval period, freedom movement, independence</li>
        <li>Indian polity: Constitution, fundamental rights and duties, Parliament, judiciary</li>
        <li>Science GK: human body, plants, animals, space, environment and ecology</li>
        <li>Sports: Indian sports achievements, Olympic medals, current sports personalities</li>
        <li>Current affairs: national news, defence news, awards, appointments — last 6 months</li>
        <li>Recommended resources: Lucent's GK, monthly current affairs magazine, GK Today</li>
      </ul>
    </div>
    <div class="subject-detail">
      <h4>🧩 Intelligence & Reasoning</h4>
      <div class="sd-meta">25 marks | Focus: Logical Thinking & Pattern Recognition</div>
      <p>The intelligence section tests logical reasoning, spatial awareness, and pattern recognition. This section can be significantly improved with regular practice — it rewards systematic effort more than any other section.</p>
      <ul>
        <li>Series: number series, letter series, mixed series — find the next term</li>
        <li>Analogies: word analogies, number analogies, letter analogies</li>
        <li>Coding-decoding: decipher codes based on given rules and patterns</li>
        <li>Direction sense: north/south/east/west problem solving with multiple turns</li>
        <li>Figure matrices and pattern completion for visual-spatial reasoning</li>
        <li>Blood relations: family relationship problems with multiple members</li>
        <li>Venn diagrams: logical set-based problems with overlapping categories</li>
      </ul>
    </div>
    <div class="book-grid">
      <div class="book-card"><div class="bc-icon">📘</div><h5>NCERT Textbooks</h5><p>Class V/VIII Maths, Science, Social Studies — the foundation of the entire exam</p></div>
      <div class="book-card"><div class="bc-icon">📗</div><h5>Lucent's GK</h5><p>The definitive GK reference for all competitive exams — a must-have for AISSEE prep</p></div>
      <div class="book-card"><div class="bc-icon">📙</div><h5>R.S. Aggarwal</h5><p>Quantitative Aptitude and Verbal/Non-Verbal Reasoning — the gold standard for practice</p></div>
      <div class="book-card"><div class="bc-icon">📕</div><h5>AISSEE Previous Papers</h5><p>Last 5–7 years of actual exam papers — essential for understanding real exam difficulty</p></div>
      <div class="book-card"><div class="bc-icon">📓</div><h5>Monthly Current Affairs</h5><p>Any reputable monthly current affairs magazine or app for GK section preparation</p></div>
      <div class="book-card"><div class="bc-icon">📒</div><h5>Target AISSEE Guide</h5><p>Purpose-built AISSEE preparation books available from major educational publishers</p></div>
    </div>
    <div class="tips-dark" style="margin-top:20px;">
      <h3>🎯 Expert Tips to Crack the AISSEE</h3>
      <div class="tips-dark-grid">
        <div class="tip-row"><div class="tip-n">1</div><p>Begin preparation at least 6 months before the exam. Create a weekly study plan covering all four sections every week without fail.</p></div>
        <div class="tip-row"><div class="tip-n">2</div><p>Solve the last 5–7 years of AISSEE papers under real exam conditions — timed, no distractions. Analyse every mistake carefully and correct misunderstandings.</p></div>
        <div class="tip-row"><div class="tip-n">3</div><p>Daily schedule: 90 mins Maths, 60 mins Language, 45 mins GK, 30 mins Reasoning. Consistency over six months beats intensive last-minute preparation every time.</p></div>
        <div class="tip-row"><div class="tip-n">4</div><p>Take one full-length mock test every weekend under exam conditions — same timing, same environment. Review every answer, especially the ones you got right by guessing.</p></div>
        <div class="tip-row"><div class="tip-n">5</div><p>Since there is no negative marking, attempt every single question in the exam. Never leave any question blank — an educated guess is always better than no attempt.</p></div>
        <div class="tip-row"><div class="tip-n">6</div><p>Physical fitness matters too. The medical exam requires good health standards. Maintain regular exercise, eat well, and sleep adequately throughout the preparation period.</p></div>
        <div class="tip-row"><div class="tip-n">7</div><p>In the final month, shift to revision mode only. Revisit weak areas, solve short practice sets, and do not introduce any new study material after this point.</p></div>
        <div class="tip-row"><div class="tip-n">8</div><p>Mental strength is as important as academic preparation. Stay calm, maintain a positive mindset, and remember: thousands of students have cracked this exam with consistent hard work.</p></div>
      </div>
    </div>
  </div>

  <!-- SCHOOLS -->
  <div class="page" id="page-schools">
    <div class="page-hero">
      <div class="page-hero-tag">Across the Nation</div>
      <h1>Sainik Schools in India</h1>
      <p>Over 33 traditional Sainik Schools spread across every region of India, each carrying the same proud legacy of discipline, excellence, and national service — with a rapidly growing new-pattern network expanding access further.</p>
    </div>
    <div class="card card-accent">
      <h3>🗺️ A Truly National Network</h3>
      <p>The geographic spread of Sainik Schools ensures that no region of India is left without access to this prestigious education. From the Himalayan foothills of Jammu & Kashmir to the tropical landscapes of Kerala, from the deserts of Rajasthan to the coastlines of Odisha — every part of India has a Sainik School with its own character, its own traditions, and its own proud record of producing national leaders. In 2021, the network was further expanded with new-pattern Sainik Schools in partnership with state governments and private educational institutions, bringing the total number of Sainik Schools across India to well over 100 when both categories are counted.</p>
    </div>
    <div class="schools-grid">
      <div class="school-card"><div class="sc-state">Maharashtra</div><h4>Sainik School Satara</h4><p>India's very first Sainik School, established in 1961. A pioneering institution with over six decades of tradition and an outstanding NDA selection record.</p></div>
      <div class="school-card"><div class="sc-state">Rajasthan</div><h4>Sainik School Chittorgarh</h4><p>Located near the legendary Chittorgarh Fort, this school carries the warrior spirit of the Rajputs in every cadet and has produced numerous distinguished officers.</p></div>
      <div class="school-card"><div class="sc-state">Kerala</div><h4>Sainik School Kazhakootam</h4><p>Situated in the beautiful hills near Thiruvananthapuram, this school is known for its academic excellence and consistently strong performance in competitive exams.</p></div>
      <div class="school-card"><div class="sc-state">Uttar Pradesh</div><h4>Sainik School Lucknow</h4><p>Set in the historic city of nawabs, blending the rich cultural heritage of Lucknow with the rigour of military education to produce well-rounded leaders.</p></div>
      <div class="school-card"><div class="sc-state">Haryana</div><h4>Sainik School Kunjpura</h4><p>One of the most highly regarded Sainik Schools in India, consistently producing top rankers in the NDA entrance examination year after year.</p></div>
      <div class="school-card"><div class="sc-state">Punjab</div><h4>Sainik School Kapurthala</h4><p>Located in the fertile land of five rivers, this school produces warriors with the legendary courage, resilience, and community spirit of Punjab.</p></div>
      <div class="school-card"><div class="sc-state">Odisha</div><h4>Sainik School Bhubaneswar</h4><p>A top-performing institution in eastern India with a proud legacy of producing outstanding Army, Navy, and Air Force officers across decades.</p></div>
      <div class="school-card"><div class="sc-state">Tamil Nadu</div><h4>Sainik School Amaravathinagar</h4><p>Nestled in the breathtaking Nilgiris foothills, this school combines stunning natural surroundings with demanding academic and physical training.</p></div>
      <div class="school-card"><div class="sc-state">Karnataka</div><h4>Sainik School Bijapur</h4><p>Set in the historically rich city of Bijapur, building cadets with the strength, resilience, and pride of Karnataka's deep warrior heritage.</p></div>
      <div class="school-card"><div class="sc-state">Jammu & Kashmir</div><h4>Sainik School Nagrota</h4><p>Located at the strategically important foothills of the Himalayas, training cadets in one of India's most vital and beautiful border regions.</p></div>
      <div class="school-card"><div class="sc-state">Madhya Pradesh</div><h4>Sainik School Rewa</h4><p>Situated in the culturally rich Vindhya region, producing leaders who carry both the intellectual heritage of MP and the warrior values of Sainik Schools.</p></div>
      <div class="school-card"><div class="sc-state">Gujarat</div><h4>Sainik School Balachadi</h4><p>Overlooking the Arabian Sea on the Saurashtra coast, this school produces cadets with the enterprise, boldness, and maritime spirit of Gujarat.</p></div>
    </div>
    <div class="card" style="margin-top:20px;">
      <h3>ℹ️ Choosing the Right School</h3>
      <p>With over 33 traditional Sainik Schools across India, choosing the right one requires some research. Most parents prefer schools in their home state for ease of family visits and because many schools reserve a portion of seats for state domicile candidates. However, any Indian student can apply to any Sainik School in the country. Key factors to consider include the school's historical NDA selection rate, its infrastructure and facilities, the extracurricular opportunities available, its academic board results, and the nature of the surrounding environment. Visit the official Sainik Schools Society website for a complete and up-to-date list of all schools, including newly established new-pattern institutions.</p>
    </div>
  </div>

  <!-- LIFE -->
  <div class="page" id="page-life">
    <div class="page-hero">
      <div class="page-hero-tag">Inside the Campus</div>
      <h1>Life at a Sainik School</h1>
      <p>Every single day at a Sainik School is purposefully structured to build a better human being — sharper, stronger, more disciplined, more compassionate, and more ready to lead. Here is what that life truly looks like.</p>
    </div>
    <div class="card card-accent">
      <h3>🌅 A Day in the Life of a Cadet</h3>
      <p>Life at a Sainik School follows a structured daily schedule that leaves no time idle — every hour is purposefully spent on either academic growth, physical development, or personal enrichment. The routine may seem demanding at first, but cadets quickly discover that it builds an extraordinary capacity for productivity, self-discipline, and resilience that stays with them for life.</p>
    </div>
    <div class="schedule">
      <div class="sch-row"><div class="sch-time">05:30 AM</div><div class="sch-act">🌅 Reveille — Wake up bugle sounds. Personal hygiene, bed-making, and room tidying to military standard.</div></div>
      <div class="sch-row"><div class="sch-time">05:45 AM</div><div class="sch-act">🏃 Physical Training — Mandatory PT, parade drills, running, and morning exercise for all cadets on the grounds.</div></div>
      <div class="sch-row"><div class="sch-time">07:00 AM</div><div class="sch-act">🚿 Bath, personal time, morning prayers, and house assembly with the housemaster.</div></div>
      <div class="sch-row"><div class="sch-time">07:45 AM</div><div class="sch-act">🍳 Breakfast at the common dining hall — nutritionally balanced meals served in a structured, disciplined environment.</div></div>
      <div class="sch-row"><div class="sch-time">08:15 AM</div><div class="sch-act">📚 Academic Classes — 6 periods of rigorous CBSE classroom instruction with experienced subject teachers.</div></div>
      <div class="sch-row"><div class="sch-time">01:30 PM</div><div class="sch-act">🍱 Lunch at the dining hall followed by a supervised rest period — vital for afternoon energy and focus.</div></div>
      <div class="sch-row"><div class="sch-time">03:00 PM</div><div class="sch-act">⚽ Compulsory Sports & Games — every cadet participates in at least one sport. Coaching by qualified instructors.</div></div>
      <div class="sch-row"><div class="sch-time">05:00 PM</div><div class="sch-act">🎭 Extracurricular Activities — NCC, music, drama, art, science clubs, debates, and hobby circles.</div></div>
      <div class="sch-row"><div class="sch-time">06:30 PM</div><div class="sch-act">🍽 Dinner & free time — cadets can relax, read, socialise, or participate in house activities and meetings.</div></div>
      <div class="sch-row"><div class="sch-time">07:30 PM</div><div class="sch-act">📝 Prep Time — supervised self-study in classrooms under the guidance of duty teachers. No exceptions.</div></div>
      <div class="sch-row"><div class="sch-time">09:30 PM</div><div class="sch-act">🌙 Lights Out — mandatory rest for all cadets. Physical recovery is treated as seriously as physical training.</div></div>
    </div>
    <div class="pillar-grid">
      <div class="pillar"><h4>🏠 House System</h4><p>Like the great public schools of the world, Sainik Schools are organised around a House System. Each cadet belongs to a house — named after Indian war heroes, virtues, or natural features. The house becomes a cadet's second family:</p><ul><li>Houses compete in academics, sports, and extracurriculars</li><li>House captains are senior cadets who lead and mentor</li><li>House spirit builds loyalty, teamwork, and pride</li><li>Annual inter-house competitions are the highlight of the school calendar</li></ul></div>
      <div class="pillar"><h4>🏆 Sports Culture</h4><p>Sport is not optional at a Sainik School — it is a compulsory, central pillar of daily life. The breadth of sports on offer ensures every cadet finds their discipline:</p><ul><li>Cricket, football, hockey, basketball, volleyball</li><li>Swimming — mandatory for all cadets</li><li>Athletics: running, jumping, throwing events</li><li>Combat sports: boxing, wrestling, judo</li><li>Precision sports: shooting, archery</li><li>Equestrian sports at select schools</li></ul></div>
    </div>
    <div class="card"><h3>🎯 Extracurricular Life</h3><p>Beyond the parade ground and the classroom, Sainik School campus life is rich with opportunities for creativity, exploration, and personal growth. Every cadet is encouraged to discover new interests and develop a well-rounded personality.</p></div>
    <div class="extra-grid">
      <div class="extra-pill"><div class="ei">🏊</div><p>Swimming</p><span>Mandatory for all cadets. Advanced coaching available at most schools.</span></div>
      <div class="extra-pill"><div class="ei">🎸</div><p>Music & Band</p><span>Military band, classical music, and contemporary music programmes.</span></div>
      <div class="extra-pill"><div class="ei">🎨</div><p>Arts & Crafts</p><span>Painting, pottery, and visual arts — cultivating creativity alongside discipline.</span></div>
      <div class="extra-pill"><div class="ei">📣</div><p>Debates</p><span>Inter-house and inter-school debates building confidence and communication skills.</span></div>
      <div class="extra-pill"><div class="ei">🔭</div><p>Science Club</p><span>Experiments, projects, and science fairs inspiring future researchers and engineers.</span></div>
      <div class="extra-pill"><div class="ei">🎭</div><p>Drama & Theatre</p><span>Annual school plays and skit competitions building expression and confidence.</span></div>
      <div class="extra-pill"><div class="ei">⛺</div><p>Trekking</p><span>Annual treks, outdoor camps, and adventure activities building resilience.</span></div>
      <div class="extra-pill"><div class="ei">🎯</div><p>Shooting</p><span>Rifle and pistol shooting under qualified instructors — a signature Sainik School activity.</span></div>
    </div>
    <div class="quote-box" style="margin-top:20px;">"I learned more about life in the first month at Sainik School than I had in the previous ten years. The routine, the sport, the friendships — it all came together to make me who I am."<span>— Common sentiment among Sainik School alumni</span></div>
  </div>

  <!-- FAQ -->
  <div class="page" id="page-faq">
    <div class="page-hero">
      <div class="page-hero-tag">Common Questions</div>
      <h1>Frequently Asked Questions</h1>
      <p>Detailed answers to the most important questions every parent asks before applying to a Sainik School — from fees and eligibility to daily life and career prospects.</p>
    </div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">Are girls allowed in Sainik Schools? <span class="faq-tog">+</span></div><div class="faq-a">Yes! In a landmark policy change in 2021, girls were allowed to apply to Sainik Schools for the first time. This began as a pilot programme across select schools and has been progressively expanded. Girls compete through the same AISSEE examination as boys. Some schools have separate girl cadet wings while others integrate girl cadets into the existing house system. Check the specific school's annual notification for the current year's eligibility and seat availability for girl candidates.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">What is the fee structure at Sainik Schools? <span class="faq-tog">+</span></div><div class="faq-a">Fees vary by school and state but are substantially lower than comparable private boarding schools thanks to government subsidies. Annual fees typically range from approximately ₹80,000 to ₹1,50,000, covering tuition, boarding, meals, laundry, and basic amenities. The government also provides merit scholarships and full fee waivers for students from SC/ST backgrounds and economically weaker sections. Defence quota candidates (wards of serving/retired armed forces personnel) also receive fee concessions. The exact fee structure for each school is published in the annual AISSEE notification.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">How difficult is the AISSEE exam? <span class="faq-tog">+</span></div><div class="faq-a">The AISSEE is competitive — thousands of students across India apply for a relatively limited number of seats — but it is far from impossible. The exam tests Class V level knowledge (for Class VI entry) or Class VIII level knowledge (for Class IX entry) across Maths, Language, GK, and Reasoning/Intelligence. The difficulty level is moderate. A student who has studied their NCERT textbooks thoroughly and practised regularly for 4–6 months is very well-placed to score high marks. The key differentiators are accuracy in Maths, strong GK preparation, and speed in the Reasoning section.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">Is it mandatory to join the Army after completing Sainik School? <span class="faq-tog">+</span></div><div class="faq-a">Absolutely not. While Sainik Schools are designed primarily to prepare students for the NDA and a career in the Indian Armed Forces, there is no obligation whatsoever for alumni to join the military. Many Sainik School graduates go on to crack IIT-JEE and study engineering, appear for UPSC and serve as IAS officers, pursue medicine, law, or business, or represent India in international sports. The school's education — its discipline, analytical training, and character development — is equally powerful preparation for any career path. In fact, many top civilian leaders proudly credit their Sainik School education as the foundation of their success.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">Can students visit home during the school year? <span class="faq-tog">+</span></div><div class="faq-a">Sainik Schools are fully residential institutions and students live on campus throughout the academic year. Students do not go home on weekends — this is a key part of the residential experience that builds independence, self-reliance, and the deep bonds of camaraderie among cadets. However, there are several structured leave periods throughout the year: summer vacation (typically May–June), a mid-term break around Dussehra/Diwali, and a winter break. Parents can also visit during designated visiting days as published by each school.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">What medical fitness standards are required? <span class="faq-tog">+</span></div><div class="faq-a">Medical fitness is a mandatory requirement for admission to Sainik Schools. The standards are broadly similar to military medical standards but are age-appropriate for school children. Key requirements include: good general health with no major illness, vision within acceptable limits (correctable vision may be acceptable in some categories), normal hearing, height and weight within the standard range for the candidate's age, and no disqualifying physical conditions. Candidates are examined by a designated government medical board. The detailed and specific medical standards are published in the official AISSEE notification each year and should be reviewed carefully before applying.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">How do I choose which Sainik School to apply to? <span class="faq-tog">+</span></div><div class="faq-a">Most parents choose their home state's Sainik School for practical reasons: ease of family visits during leave periods, familiarity with the local environment, and state-level domicile reservations that give home-state candidates a slight advantage in seat allocation. However, any Indian student can apply to any Sainik School across the country. When evaluating schools, consider: the school's historical NDA selection rate (publicly available), its CBSE board result performance, infrastructure and facilities, sports and extracurricular opportunities, and the surrounding geographic environment. Speaking to alumni of different schools through online forums is also a very useful step.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">What happens if my child does not get into the NDA after Sainik School? <span class="faq-tog">+</span></div><div class="faq-a">This is a question every parent should consider — and the answer is reassuring. Sainik School graduates who do not make it to the NDA are still exceptionally well-prepared for life. The rigorous academic training prepares them for JEE, NEET, and other competitive exams. The discipline, communication skills, and leadership abilities they develop make them outstanding candidates for top universities and employers. Many Sainik School graduates who did not join the military have gone on to build distinguished careers in engineering, medicine, civil services, business, and sports. The Sainik School brand is widely respected and recognised across Indian society.</div></div>
    <div class="faq-item"><div class="faq-q" onclick="tFaq(this)">When does AISSEE registration open and what is the exam date? <span class="faq-tog">+</span></div><div class="faq-a">The AISSEE registration window typically opens in October or November each year on the official NTA portal. The examination itself is usually conducted in January of the following year. Results are published within 4–6 weeks of the exam. The exact dates vary slightly from year to year, so it is essential to regularly check the official Sainik Schools Society website and the NTA portal (nta.ac.in) for the most current notifications. Set a reminder for October each year to ensure you do not miss the application window.</div></div>
    <div class="cta-banner">
      <h3>Still Have Questions?</h3>
      <p>Visit the official Sainik Schools Society portal for the most comprehensive and up-to-date information, including school-specific contacts, fee structures, and annual notifications.</p>
      <div class="btn-dark" onclick="window.open('https://sainikschool.sarv.net','_blank')">Visit Official Portal ↗</div>
    </div>
  </div>

</div>

<script>
var pages={home:{id:'page-home',title:'Home'},about:{id:'page-about',title:'About Sainik Schools'},why:{id:'page-why',title:'Why Join?'},alumni:{id:'page-alumni',title:'Alumni & Careers'},admission:{id:'page-admission',title:'Admission Process'},prep:{id:'page-prep',title:'Exam Preparation'},schools:{id:'page-schools',title:'Schools Across India'},life:{id:'page-life',title:'Life at Sainik School'},faq:{id:'page-faq',title:'FAQ'}};
function goTo(k){
  document.querySelectorAll('.page').forEach(function(p){p.classList.remove('active');});
  document.querySelectorAll('.sb-link').forEach(function(l){l.classList.remove('active');});
  var pg=document.getElementById(pages[k].id);
  if(pg){pg.classList.add('active');}
  document.getElementById('topbar-title').textContent=pages[k].title;
  document.querySelectorAll('.sb-link').forEach(function(l){if(l.getAttribute('onclick')&&l.getAttribute('onclick').indexOf("'"+k+"'")>-1)l.classList.add('active');});
  document.getElementById('main').scrollTop=0;
  if(window.innerWidth<=768){document.getElementById('sidebar').classList.remove('open');}
}
function toggleSidebar(){document.getElementById('sidebar').classList.toggle('open');}
function tFaq(el){
  var a=el.nextElementSibling,t=el.querySelector('.faq-tog'),open=a.classList.contains('open');
  document.querySelectorAll('.faq-a.open').forEach(function(x){x.classList.remove('open');});
  document.querySelectorAll('.faq-tog').forEach(function(x){x.textContent='+';});
  if(!open){a.classList.add('open');t.textContent='−';}
}
</script>
</body>
</html>
