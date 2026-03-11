<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Md Ridoan Mahmud Zisan — Full Stack Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"/>
<style>
:root{
  --bg:#05050f;
  --bg2:#0a0a1a;
  --bg3:#0f0f22;
  --accent:#7c3aed;
  --accent2:#22d3ee;
  --accent3:#f472b6;
  --text:#e0d7ff;
  --muted:#8b8baa;
  --card:#0d0d20;
  --border:rgba(124,58,237,0.2);
  --glow:rgba(124,58,237,0.4);
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  background:var(--bg);
  color:var(--text);
  font-family:'DM Sans',sans-serif;
  overflow-x:hidden;
  cursor:none;
}

/* CUSTOM CURSOR */
#cursor{
  width:12px;height:12px;
  background:var(--accent2);
  border-radius:50%;
  position:fixed;top:0;left:0;
  pointer-events:none;z-index:9999;
  transition:transform 0.1s;
  mix-blend-mode:difference;
}
#cursor-trail{
  width:32px;height:32px;
  border:1.5px solid var(--accent);
  border-radius:50%;
  position:fixed;top:0;left:0;
  pointer-events:none;z-index:9998;
  transition:all 0.18s ease;
  opacity:0.6;
}

/* NOISE OVERLAY */
body::before{
  content:'';
  position:fixed;inset:0;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events:none;z-index:0;opacity:0.4;
}

/* GRID BG */
body::after{
  content:'';
  position:fixed;inset:0;
  background-image:linear-gradient(rgba(124,58,237,0.04) 1px,transparent 1px),
    linear-gradient(90deg,rgba(124,58,237,0.04) 1px,transparent 1px);
  background-size:60px 60px;
  pointer-events:none;z-index:0;
}

/* SCROLLBAR */
::-webkit-scrollbar{width:4px;}
::-webkit-scrollbar-track{background:var(--bg);}
::-webkit-scrollbar-thumb{background:var(--accent);border-radius:2px;}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;
  z-index:100;
  padding:18px 40px;
  display:flex;align-items:center;justify-content:space-between;
  background:rgba(5,5,15,0.8);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
}
.nav-logo{
  font-family:'Syne',sans-serif;
  font-weight:800;font-size:1.2rem;
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  letter-spacing:0.05em;
}
.nav-links{display:flex;gap:28px;list-style:none;}
.nav-links a{
  color:var(--muted);font-size:0.85rem;text-decoration:none;
  letter-spacing:0.1em;text-transform:uppercase;
  transition:color 0.2s;position:relative;
}
.nav-links a::after{
  content:'';position:absolute;bottom:-4px;left:0;
  width:0;height:1px;background:var(--accent2);
  transition:width 0.3s;
}
.nav-links a:hover{color:var(--accent2);}
.nav-links a:hover::after{width:100%;}
.nav-cta{
  padding:8px 20px;border:1px solid var(--accent);
  color:var(--accent);font-size:0.82rem;border-radius:4px;
  text-decoration:none;letter-spacing:0.08em;text-transform:uppercase;
  transition:all 0.2s;font-family:'Space Mono',monospace;
}
.nav-cta:hover{background:var(--accent);color:#fff;}

/* HERO */
.hero{
  min-height:100vh;
  display:flex;align-items:center;justify-content:center;
  position:relative;z-index:1;
  padding:120px 40px 80px;
  flex-direction:column;
  text-align:center;
}
.hero-badge{
  display:inline-flex;align-items:center;gap:8px;
  padding:6px 16px;
  border:1px solid rgba(34,211,238,0.3);
  border-radius:100px;
  font-size:0.78rem;letter-spacing:0.15em;text-transform:uppercase;
  color:var(--accent2);margin-bottom:28px;
  background:rgba(34,211,238,0.06);
  animation:fadeDown 0.8s ease both;
}
.hero-badge .dot{
  width:6px;height:6px;border-radius:50%;
  background:var(--accent2);
  animation:pulse 2s infinite;
}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1);}50%{opacity:0.4;transform:scale(0.8);}}

.hero-name{
  font-family:'Syne',sans-serif;
  font-size:clamp(2.6rem,6vw,5rem);
  font-weight:800;
  line-height:1.05;
  margin-bottom:18px;
  animation:fadeDown 0.8s 0.1s ease both;
}
.hero-name span{
  background:linear-gradient(135deg,#a78bfa,var(--accent2),var(--accent3));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-size:200% 200%;
  animation:gradShift 5s ease infinite;
}
@keyframes gradShift{0%,100%{background-position:0% 50%;}50%{background-position:100% 50%;}}

/* TYPING */
.typing-wrap{
  font-family:'Space Mono',monospace;
  font-size:clamp(0.9rem,2vw,1.15rem);
  color:var(--accent2);
  margin-bottom:24px;
  animation:fadeDown 0.8s 0.2s ease both;
  min-height:1.6em;
}
.typing-cursor{
  display:inline-block;
  width:2px;height:1.1em;
  background:var(--accent2);
  margin-left:2px;vertical-align:middle;
  animation:blink 1s step-end infinite;
}
@keyframes blink{0%,100%{opacity:1;}50%{opacity:0;}}

.hero-desc{
  max-width:560px;
  color:var(--muted);
  line-height:1.75;
  font-size:1rem;
  margin-bottom:40px;
  animation:fadeDown 0.8s 0.3s ease both;
}

.hero-btns{
  display:flex;gap:14px;flex-wrap:wrap;justify-content:center;
  animation:fadeDown 0.8s 0.4s ease both;
  margin-bottom:56px;
}
.btn-primary{
  padding:13px 30px;
  background:linear-gradient(135deg,var(--accent),#5b21b6);
  color:#fff;border:none;border-radius:6px;
  font-size:0.9rem;letter-spacing:0.06em;
  text-decoration:none;cursor:pointer;
  transition:all 0.3s;
  box-shadow:0 0 30px rgba(124,58,237,0.4);
  font-family:'Space Mono',monospace;
}
.btn-primary:hover{transform:translateY(-2px);box-shadow:0 0 50px rgba(124,58,237,0.6);}
.btn-outline{
  padding:13px 30px;
  background:transparent;color:var(--text);
  border:1px solid var(--border);border-radius:6px;
  font-size:0.9rem;letter-spacing:0.06em;
  text-decoration:none;cursor:pointer;
  transition:all 0.3s;
  font-family:'Space Mono',monospace;
}
.btn-outline:hover{border-color:var(--accent2);color:var(--accent2);transform:translateY(-2px);}

/* SOCIAL CIRCLES */
.social-circles{
  display:flex;gap:14px;flex-wrap:wrap;justify-content:center;
  animation:fadeDown 0.8s 0.5s ease both;
}
.s-circle{
  width:46px;height:46px;border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  text-decoration:none;font-size:1rem;
  border:1.5px solid var(--border);
  background:rgba(13,13,32,0.8);
  color:var(--muted);
  transition:all 0.3s;
  position:relative;overflow:hidden;
}
.s-circle::before{
  content:'';position:absolute;inset:0;
  border-radius:50%;opacity:0;
  transition:opacity 0.3s;
}
.s-circle:hover{transform:translateY(-4px) scale(1.1);color:#fff;}
.s-circle.gh{--c:#fff;} .s-circle.gh:hover{border-color:#fff;background:#181717;box-shadow:0 0 20px rgba(255,255,255,0.2);}
.s-circle.li{--c:#0077B5;} .s-circle.li:hover{border-color:#0077B5;background:#0077B5;box-shadow:0 0 20px rgba(0,119,181,0.4);}
.s-circle.fb{--c:#1877F2;} .s-circle.fb:hover{border-color:#1877F2;background:#1877F2;box-shadow:0 0 20px rgba(24,119,242,0.4);}
.s-circle.yt{--c:#FF0000;} .s-circle.yt:hover{border-color:#FF0000;background:#FF0000;box-shadow:0 0 20px rgba(255,0,0,0.4);}
.s-circle.em{--c:#EA4335;} .s-circle.em:hover{border-color:#EA4335;background:#EA4335;box-shadow:0 0 20px rgba(234,67,53,0.4);}
.s-circle.pt{--c:#00C7B7;} .s-circle.pt:hover{border-color:#00C7B7;background:#00C7B7;box-shadow:0 0 20px rgba(0,199,183,0.4);}

/* SCROLL INDICATOR */
.scroll-hint{
  position:absolute;bottom:32px;left:50%;transform:translateX(-50%);
  display:flex;flex-direction:column;align-items:center;gap:8px;
  color:var(--muted);font-size:0.72rem;letter-spacing:0.2em;text-transform:uppercase;
  animation:fadeDown 1s 0.8s ease both;
}
.scroll-line{
  width:1px;height:50px;
  background:linear-gradient(to bottom,var(--accent),transparent);
  animation:scrollPulse 2s ease infinite;
}
@keyframes scrollPulse{0%{transform:scaleY(0);transform-origin:top;}50%{transform:scaleY(1);}100%{transform:scaleY(1);opacity:0;}}

/* SECTIONS */
section{position:relative;z-index:1;padding:100px 40px;}
.section-label{
  font-family:'Space Mono',monospace;
  font-size:0.72rem;letter-spacing:0.25em;text-transform:uppercase;
  color:var(--accent);margin-bottom:12px;
  display:flex;align-items:center;gap:10px;
}
.section-label::before{content:'';width:30px;height:1px;background:var(--accent);}
.section-title{
  font-family:'Syne',sans-serif;
  font-size:clamp(2rem,4vw,3rem);
  font-weight:800;margin-bottom:48px;
}
.section-title em{
  font-style:normal;
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.container{max-width:1100px;margin:0 auto;}

/* STATS STRIP */
.stats-strip{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:16px;padding:36px 48px;
  display:grid;grid-template-columns:repeat(4,1fr);
  gap:24px;margin-bottom:0;
}
.stat-item{text-align:center;}
.stat-num{
  font-family:'Syne',sans-serif;font-size:2.4rem;font-weight:800;
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.stat-label{color:var(--muted);font-size:0.82rem;margin-top:4px;letter-spacing:0.08em;}

/* SKILLS */
.skills-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(120px,1fr));gap:12px;}
.skill-pill{
  padding:12px 14px;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:10px;
  display:flex;flex-direction:column;align-items:center;gap:8px;
  font-size:0.78rem;color:var(--muted);
  transition:all 0.3s;cursor:default;
  text-align:center;
}
.skill-pill i{font-size:1.5rem;color:var(--accent);}
.skill-pill:hover{border-color:var(--accent2);color:var(--accent2);transform:translateY(-3px);}
.skill-pill:hover i{color:var(--accent2);}
.skills-cat-title{
  font-family:'Syne',sans-serif;font-weight:700;
  font-size:0.85rem;letter-spacing:0.1em;text-transform:uppercase;
  color:var(--accent2);margin-bottom:16px;margin-top:36px;
  display:flex;align-items:center;gap:8px;
}
.skills-cat-title::after{content:'';flex:1;height:1px;background:var(--border);}

/* PROJECTS */
.projects-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));
  gap:20px;
}
.project-card{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:14px;overflow:hidden;
  transition:all 0.3s;
  position:relative;
}
.project-card::before{
  content:'';position:absolute;top:0;left:0;right:0;
  height:2px;
  background:linear-gradient(90deg,var(--accent),var(--accent2),var(--accent3));
  opacity:0;transition:opacity 0.3s;
}
.project-card:hover{transform:translateY(-4px);border-color:rgba(124,58,237,0.4);}
.project-card:hover::before{opacity:1;}
.project-img{
  width:100%;height:170px;
  background:linear-gradient(135deg,#1a0533,#0d1b2a);
  display:flex;align-items:center;justify-content:center;
  font-size:3rem;
  position:relative;overflow:hidden;
}
.project-img img{width:100%;height:100%;object-fit:cover;opacity:0.7;}
.project-img .p-icon{position:absolute;font-size:2.5rem;}
.project-body{padding:20px;}
.project-title{
  font-family:'Syne',sans-serif;font-weight:700;
  font-size:1rem;margin-bottom:8px;
}
.project-desc{color:var(--muted);font-size:0.82rem;line-height:1.6;margin-bottom:14px;}
.project-tags{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:14px;}
.tag{
  padding:3px 10px;
  background:rgba(124,58,237,0.15);
  border:1px solid rgba(124,58,237,0.25);
  border-radius:100px;
  font-size:0.7rem;color:var(--accent);
  font-family:'Space Mono',monospace;
}
.project-links{display:flex;gap:10px;}
.p-link{
  display:flex;align-items:center;gap:5px;
  color:var(--muted);font-size:0.78rem;text-decoration:none;
  transition:color 0.2s;
}
.p-link:hover{color:var(--accent2);}

/* CERTS */
.certs-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));
  gap:16px;
}
.cert-card{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:12px;padding:20px;
  display:flex;flex-direction:column;align-items:center;
  gap:10px;text-align:center;
  transition:all 0.3s;
}
.cert-card:hover{border-color:var(--accent);transform:translateY(-3px);}
.cert-icon{
  width:52px;height:52px;border-radius:12px;
  display:flex;align-items:center;justify-content:center;
  font-size:1.5rem;
  background:rgba(124,58,237,0.15);
  color:var(--accent);
}
.cert-name{font-size:0.82rem;font-weight:600;color:var(--text);}
.cert-org{font-size:0.72rem;color:var(--muted);}
.cert-badge{
  display:inline-block;padding:2px 8px;
  background:rgba(34,211,238,0.1);border:1px solid rgba(34,211,238,0.2);
  border-radius:100px;font-size:0.68rem;color:var(--accent2);
}

/* TOOLS */
.tools-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));
  gap:14px;
}
.tool-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:12px;padding:18px 14px;
  display:flex;align-items:center;gap:12px;
  transition:all 0.3s;
}
.tool-card:hover{border-color:var(--accent2);transform:translateX(4px);}
.tool-icon{font-size:1.6rem;}
.tool-name{font-size:0.82rem;font-weight:500;}

/* ABOUT YAML */
.about-yaml{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:14px;overflow:hidden;
}
.yaml-bar{
  background:#1a1a2e;
  padding:12px 20px;
  display:flex;align-items:center;gap:8px;
  border-bottom:1px solid var(--border);
  font-family:'Space Mono',monospace;
  font-size:0.78rem;color:var(--muted);
}
.yaml-dot{width:10px;height:10px;border-radius:50%;}
.yaml-body{
  padding:28px;
  font-family:'Space Mono',monospace;
  font-size:0.85rem;line-height:2;
}
.y-key{color:#f472b6;}
.y-colon{color:var(--muted);}
.y-val{color:#86efac;}
.y-str{color:var(--accent2);}
.y-line{display:block;}

/* GITHUB STATS */
.gh-stats{
  display:grid;grid-template-columns:1fr 1fr;
  gap:16px;
}
.gh-stat-img{
  border-radius:12px;overflow:hidden;
  border:1px solid var(--border);
  background:var(--card);
  width:100%;
}
.gh-stat-img img{width:100%;display:block;}

/* CONTACT */
.contact-grid{
  display:grid;grid-template-columns:1fr 1fr;
  gap:24px;align-items:start;
}
.contact-info{
  display:flex;flex-direction:column;gap:16px;
}
.contact-item{
  display:flex;align-items:center;gap:14px;
  padding:16px 20px;
  background:var(--card);border:1px solid var(--border);
  border-radius:12px;text-decoration:none;
  transition:all 0.3s;
}
.contact-item:hover{border-color:var(--accent);transform:translateX(6px);}
.ci-icon{
  width:40px;height:40px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:1.1rem;flex-shrink:0;
}
.ci-text small{display:block;font-size:0.72rem;color:var(--muted);margin-bottom:2px;}
.ci-text span{font-size:0.88rem;color:var(--text);}

/* FOOTER */
footer{
  border-top:1px solid var(--border);
  padding:40px;
  text-align:center;
  position:relative;z-index:1;
}
.footer-logo{
  font-family:'Syne',sans-serif;font-weight:800;font-size:1.5rem;
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  margin-bottom:16px;
}
.footer-links{
  display:flex;gap:20px;justify-content:center;
  list-style:none;margin-bottom:24px;
  flex-wrap:wrap;
}
.footer-links a{color:var(--muted);text-decoration:none;font-size:0.82rem;transition:color 0.2s;}
.footer-links a:hover{color:var(--accent2);}
.footer-copy{color:var(--muted);font-size:0.78rem;}
.footer-social{
  display:flex;gap:12px;justify-content:center;margin-bottom:20px;
}
.fs-icon{
  width:38px;height:38px;border-radius:50%;
  border:1px solid var(--border);
  display:flex;align-items:center;justify-content:center;
  color:var(--muted);text-decoration:none;font-size:0.9rem;
  transition:all 0.3s;
}
.fs-icon:hover{border-color:var(--accent);color:var(--accent);transform:translateY(-3px);}

/* PROGRESS BAR */
.skill-bar-wrap{margin-bottom:14px;}
.sb-head{display:flex;justify-content:space-between;margin-bottom:6px;font-size:0.82rem;}
.sb-head span:first-child{color:var(--text);}
.sb-head span:last-child{color:var(--muted);}
.sb-track{
  height:5px;background:rgba(255,255,255,0.06);
  border-radius:100px;overflow:hidden;
}
.sb-fill{
  height:100%;border-radius:100px;
  background:linear-gradient(90deg,var(--accent),var(--accent2));
  width:0%;
  transition:width 1.2s cubic-bezier(0.4,0,0.2,1);
}

/* CURRENT STATUS */
.status-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:14px;padding:24px;
  display:flex;align-items:center;gap:16px;
  margin-bottom:32px;
}
.status-dot{
  width:10px;height:10px;border-radius:50%;
  background:#22c55e;flex-shrink:0;
  box-shadow:0 0 8px #22c55e;
  animation:pulse 2s infinite;
}
.status-text{font-size:0.88rem;}
.status-text strong{color:var(--accent2);}
.status-text span{color:var(--muted);}

/* TABS */
.tabs{display:flex;gap:8px;margin-bottom:28px;flex-wrap:wrap;}
.tab-btn{
  padding:8px 20px;border-radius:100px;
  border:1px solid var(--border);
  background:transparent;color:var(--muted);
  font-size:0.82rem;cursor:pointer;
  transition:all 0.2s;
  font-family:'Space Mono',monospace;
}
.tab-btn.active,.tab-btn:hover{
  background:var(--accent);border-color:var(--accent);
  color:#fff;
}
.tab-content{display:none;}
.tab-content.active{display:block;}

/* TIMELINE */
.timeline{position:relative;padding-left:30px;}
.timeline::before{
  content:'';position:absolute;left:0;top:0;bottom:0;
  width:1px;background:var(--border);
}
.tl-item{
  position:relative;margin-bottom:28px;
  padding-left:20px;
}
.tl-item::before{
  content:'';position:absolute;left:-34px;top:6px;
  width:10px;height:10px;border-radius:50%;
  background:var(--accent);
  box-shadow:0 0 8px var(--accent);
}
.tl-date{font-family:'Space Mono',monospace;font-size:0.72rem;color:var(--accent2);margin-bottom:4px;}
.tl-title{font-weight:600;margin-bottom:4px;}
.tl-desc{font-size:0.83rem;color:var(--muted);}

/* ANIMATIONS */
@keyframes fadeDown{from{opacity:0;transform:translateY(-20px);}to{opacity:1;transform:translateY(0);}}
@keyframes fadeUp{from{opacity:0;transform:translateY(30px);}to{opacity:1;transform:translateY(0);}}
.reveal{opacity:0;transform:translateY(30px);transition:all 0.7s cubic-bezier(0.4,0,0.2,1);}
.reveal.visible{opacity:1;transform:translateY(0);}

/* GLOWING ORB BG */
.orb{
  position:fixed;border-radius:50%;filter:blur(80px);
  pointer-events:none;z-index:0;opacity:0.18;
}
.orb1{width:500px;height:500px;background:var(--accent);top:-100px;right:-100px;}
.orb2{width:400px;height:400px;background:var(--accent2);bottom:-100px;left:-100px;}
.orb3{width:300px;height:300px;background:var(--accent3);top:50%;left:50%;transform:translate(-50%,-50%);}

/* RESPONSIVE */
@media(max-width:768px){
  nav{padding:16px 20px;}
  .nav-links{display:none;}
  section{padding:70px 20px;}
  .stats-strip{grid-template-columns:repeat(2,1fr);}
  .gh-stats{grid-template-columns:1fr;}
  .contact-grid{grid-template-columns:1fr;}
}
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-trail"></div>
<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">RMZ.</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#certs">Certs</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="mailto:ridoan.zisan@gmail.com" class="nav-cta">Hire Me</a>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-badge"><span class="dot"></span> Available for freelance & collaboration</div>
  <h1 class="hero-name">Md Ridoan<br/><span>Mahmud Zisan</span></h1>
  <div class="typing-wrap">
    <span id="typed-text"></span><span class="typing-cursor"></span>
  </div>
  <p class="hero-desc">
    Full Stack Developer from Bogura, Bangladesh 🇧🇩. Building scalable web apps, EdTech platforms,
    and tools that empower the next generation. Open source enthusiast & social change maker.
  </p>
  <div class="hero-btns">
    <a href="https://ridoan-zisan.netlify.app" class="btn-primary"><i class="fas fa-rocket"></i> &nbsp;View Portfolio</a>
    <a href="#contact" class="btn-outline"><i class="fas fa-paper-plane"></i> &nbsp;Get In Touch</a>
  </div>
  <div class="social-circles">
    <a href="https://github.com/RidoanDev" class="s-circle gh" title="GitHub"><i class="fab fa-github"></i></a>
    <a href="https://linkedin.com/in/ridoan-zisan" class="s-circle li" title="LinkedIn"><i class="fab fa-linkedin-in"></i></a>
    <a href="https://facebook.com/rid0anzisan" class="s-circle fb" title="Facebook"><i class="fab fa-facebook-f"></i></a>
    <a href="https://youtube.com/@ridoan-zisan" class="s-circle yt" title="YouTube"><i class="fab fa-youtube"></i></a>
    <a href="mailto:ridoan.zisan@gmail.com" class="s-circle em" title="Gmail"><i class="fab fa-google"></i></a>
    <a href="https://ridoan-zisan.netlify.app" class="s-circle pt" title="Portfolio"><i class="fas fa-globe"></i></a>
  </div>
  <div class="scroll-hint"><span>scroll</span><div class="scroll-line"></div></div>
</div>

<!-- STATS -->
<section style="padding-top:0;">
  <div class="container">
    <div class="stats-strip reveal">
      <div class="stat-item"><div class="stat-num" data-target="50">0</div><div class="stat-label">Projects Built</div></div>
      <div class="stat-item"><div class="stat-num" data-target="20">0</div><div class="stat-label">Certifications</div></div>
      <div class="stat-item"><div class="stat-num" data-target="3">0</div><div class="stat-label">Years Experience</div></div>
      <div class="stat-item"><div class="stat-num" data-target="5">0</div><div class="stat-label">Open Source Repos</div></div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <div class="section-label"><i class="fas fa-user-astronaut"></i> Who I Am</div>
    <h2 class="section-title">About <em>Me</em></h2>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:32px;" class="reveal">
      <div>
        <div class="status-card">
          <div class="status-dot"></div>
          <div class="status-text">
            <strong>Open to Work</strong><br/>
            <span>Available for freelance & full-time opportunities</span>
          </div>
        </div>
        <div class="about-yaml">
          <div class="yaml-bar">
            <div class="yaml-dot" style="background:#ff5f57"></div>
            <div class="yaml-dot" style="background:#febc2e"></div>
            <div class="yaml-dot" style="background:#28c840"></div>
            <span style="margin-left:8px;">profile.yaml</span>
          </div>
          <div class="yaml-body">
            <span class="y-line"><span class="y-key">name</span><span class="y-colon">: </span><span class="y-str">"Md Ridoan Mahmud Zisan"</span></span>
            <span class="y-line"><span class="y-key">location</span><span class="y-colon">: </span><span class="y-str">"Bogura, Bangladesh 🇧🇩"</span></span>
            <span class="y-line"><span class="y-key">role</span><span class="y-colon">: </span><span class="y-str">"Full Stack Developer"</span></span>
            <span class="y-line"><span class="y-key">focus</span><span class="y-colon">:</span></span>
            <span class="y-line" style="padding-left:16px"><span class="y-val">- Scalable Web Apps</span></span>
            <span class="y-line" style="padding-left:16px"><span class="y-val">- EdTech Platforms</span></span>
            <span class="y-line" style="padding-left:16px"><span class="y-val">- Open Source Projects</span></span>
            <span class="y-line"><span class="y-key">learning</span><span class="y-colon">: </span><span class="y-str">"Cloud Native · DevOps · AI/ML"</span></span>
            <span class="y-line"><span class="y-key">mission</span><span class="y-colon">: </span><span class="y-str">"Empower youth via technology"</span></span>
            <span class="y-line"><span class="y-key">available</span><span class="y-colon">: </span><span class="y-val">true</span></span>
          </div>
        </div>
      </div>
      <div>
        <h3 style="font-family:'Syne',sans-serif;font-size:1.3rem;margin-bottom:20px;">Core Skills Proficiency</h3>
        <div class="skill-bar-wrap"><div class="sb-head"><span>React / Next.js</span><span>92%</span></div><div class="sb-track"><div class="sb-fill" data-w="92"></div></div></div>
        <div class="skill-bar-wrap"><div class="sb-head"><span>Node.js / Express</span><span>87%</span></div><div class="sb-track"><div class="sb-fill" data-w="87"></div></div></div>
        <div class="skill-bar-wrap"><div class="sb-head"><span>JavaScript / TypeScript</span><span>90%</span></div><div class="sb-track"><div class="sb-fill" data-w="90"></div></div></div>
        <div class="skill-bar-wrap"><div class="sb-head"><span>Python</span><span>75%</span></div><div class="sb-track"><div class="sb-fill" data-w="75"></div></div></div>
        <div class="skill-bar-wrap"><div class="sb-head"><span>MongoDB / MySQL</span><span>82%</span></div><div class="sb-track"><div class="sb-fill" data-w="82"></div></div></div>
        <div class="skill-bar-wrap"><div class="sb-head"><span>UI/UX & Tailwind CSS</span><span>88%</span></div><div class="sb-track"><div class="sb-fill" data-w="88"></div></div></div>
        <div style="margin-top:28px;">
          <div class="timeline">
            <div class="tl-item"><div class="tl-date">2025 — Present</div><div class="tl-title">Full Stack Developer & Freelancer</div><div class="tl-desc">Building web apps, EdTech platforms, and social impact tools.</div></div>
            <div class="tl-item"><div class="tl-date">2024</div><div class="tl-title">Founded BOBDO & YouthHopeBD</div><div class="tl-desc">Blood donation organization and youth empowerment NGO.</div></div>
            <div class="tl-item"><div class="tl-date">2023</div><div class="tl-title">Started Open Source Journey</div><div class="tl-desc">Contributed to community tools, launched 50+ personal projects.</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" style="background:var(--bg2);">
  <div class="container">
    <div class="section-label"><i class="fas fa-bolt"></i> Arsenal</div>
    <h2 class="section-title reveal">Tech Stack <em>Arsenal</em></h2>
    <div class="reveal">
      <div class="skills-cat-title"><i class="fas fa-palette"></i> Frontend</div>
      <div class="skills-grid">
        <div class="skill-pill"><i class="fab fa-js-square" style="color:#F7DF1E"></i>JavaScript</div>
        <div class="skill-pill"><i class="fab fa-react" style="color:#61DAFB"></i>React</div>
        <div class="skill-pill"><i class="fas fa-n" style="color:#fff"></i>Next.js</div>
        <div class="skill-pill"><i class="fab fa-html5" style="color:#E34F26"></i>HTML5</div>
        <div class="skill-pill"><i class="fab fa-css3-alt" style="color:#1572B6"></i>CSS3</div>
        <div class="skill-pill"><i class="fas fa-wind" style="color:#06B6D4"></i>Tailwind</div>
        <div class="skill-pill"><i class="fab fa-bootstrap" style="color:#7952B3"></i>Bootstrap</div>
        <div class="skill-pill"><i class="fas fa-code" style="color:#3178C6"></i>TypeScript</div>
      </div>
      <div class="skills-cat-title"><i class="fas fa-server"></i> Backend & Database</div>
      <div class="skills-grid">
        <div class="skill-pill"><i class="fab fa-node-js" style="color:#339933"></i>Node.js</div>
        <div class="skill-pill"><i class="fas fa-layer-group" style="color:#888"></i>Express.js</div>
        <div class="skill-pill"><i class="fab fa-python" style="color:#3776AB"></i>Python</div>
        <div class="skill-pill"><i class="fas fa-leaf" style="color:#47A248"></i>MongoDB</div>
        <div class="skill-pill"><i class="fas fa-database" style="color:#4479A1"></i>MySQL</div>
        <div class="skill-pill"><i class="fas fa-fire" style="color:#FFCA28"></i>Firebase</div>
      </div>
      <div class="skills-cat-title"><i class="fas fa-tools"></i> Tools & Platforms</div>
      <div class="skills-grid">
        <div class="skill-pill"><i class="fab fa-git-alt" style="color:#F05032"></i>Git</div>
        <div class="skill-pill"><i class="fab fa-github"></i>GitHub</div>
        <div class="skill-pill"><i class="fab fa-linux" style="color:#FCC624"></i>Linux</div>
        <div class="skill-pill"><i class="fas fa-code" style="color:#007ACC"></i>VS Code</div>
        <div class="skill-pill"><i class="fab fa-figma" style="color:#F24E1E"></i>Figma</div>
        <div class="skill-pill"><i class="fas fa-flask" style="color:#FF6C37"></i>Postman</div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="container">
    <div class="section-label"><i class="fas fa-rocket"></i> Work</div>
    <h2 class="section-title reveal">Featured <em>Projects</em></h2>

    <div class="tabs reveal">
      <button class="tab-btn active" onclick="showTab('all',this)">All</button>
      <button class="tab-btn" onclick="showTab('edtech',this)">EdTech</button>
      <button class="tab-btn" onclick="showTab('ecommerce',this)">eCommerce</button>
      <button class="tab-btn" onclick="showTab('social',this)">Social Impact</button>
      <button class="tab-btn" onclick="showTab('tools',this)">Dev Tools</button>
    </div>

    <div id="tab-all" class="tab-content active reveal">
      <div class="projects-grid">

        <div class="project-card" data-cat="social">
          <div class="project-img" style="background:linear-gradient(135deg,#1a0533,#0d2340);">
            <span class="p-icon">🏙️</span>
          </div>
          <div class="project-body">
            <div class="project-title">DhunatHub</div>
            <div class="project-desc">A local community platform connecting people in Dhunat, Bangladesh. Real-time updates, local news & events.</div>
            <div class="project-tags"><span class="tag">React</span><span class="tag">Node.js</span><span class="tag">Firebase</span></div>
            <div class="project-links">
              <a href="https://dhunat.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="social">
          <div class="project-img" style="background:linear-gradient(135deg,#1a0010,#2a0010);">
            <span class="p-icon">🩸</span>
          </div>
          <div class="project-body">
            <div class="project-title">BOBDO</div>
            <div class="project-desc">Blood donation organization connecting donors with patients in need. Life-saving social impact platform.</div>
            <div class="project-tags"><span class="tag">React</span><span class="tag">MongoDB</span><span class="tag">Express</span></div>
            <div class="project-links">
              <a href="https://bobdo.vercel.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="edtech">
          <div class="project-img" style="background:linear-gradient(135deg,#0a1a33,#0a2a1a);">
            <span class="p-icon">🎓</span>
          </div>
          <div class="project-body">
            <div class="project-title">HSCian</div>
            <div class="project-desc">EdTech platform built for HSC students. Study materials, quizzes, and exam prep resources.</div>
            <div class="project-tags"><span class="tag">Next.js</span><span class="tag">Tailwind</span><span class="tag">Firebase</span></div>
            <div class="project-links">
              <a href="https://hscian.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="ecommerce">
          <div class="project-img" style="background:linear-gradient(135deg,#1a1000,#2a1a00);">
            <span class="p-icon">🛍️</span>
          </div>
          <div class="project-body">
            <div class="project-title">Netlistore</div>
            <div class="project-desc">Full-featured e-commerce platform with cart, checkout, payment integration, and admin dashboard.</div>
            <div class="project-tags"><span class="tag">React</span><span class="tag">Node.js</span><span class="tag">MongoDB</span></div>
            <div class="project-links">
              <a href="https://netlistore.vercel.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="ecommerce">
          <div class="project-img" style="background:linear-gradient(135deg,#001a1a,#001a0a);">
            <span class="p-icon">🛒</span>
          </div>
          <div class="project-body">
            <div class="project-title">ZupraMart</div>
            <div class="project-desc">Online marketplace with multi-vendor support, product discovery, and seamless user experience.</div>
            <div class="project-tags"><span class="tag">React</span><span class="tag">Express</span><span class="tag">MySQL</span></div>
            <div class="project-links">
              <a href="https://zupramart.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="tools">
          <div class="project-img" style="background:linear-gradient(135deg,#0a0a2a,#1a0a2a);">
            <span class="p-icon">🛠️</span>
          </div>
          <div class="project-body">
            <div class="project-title">ToolHub</div>
            <div class="project-desc">Developer utilities suite — color picker, JSON formatter, regex tester, code minifier and more.</div>
            <div class="project-tags"><span class="tag">JavaScript</span><span class="tag">CSS3</span><span class="tag">HTML5</span></div>
            <div class="project-links">
              <a href="https://toolhub-i.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="social">
          <div class="project-img" style="background:linear-gradient(135deg,#002a0a,#0a2a0a);">
            <span class="p-icon">🤝</span>
          </div>
          <div class="project-body">
            <div class="project-title">YouthHopeBD</div>
            <div class="project-desc">Youth empowerment NGO platform supporting social change through education and skill development.</div>
            <div class="project-tags"><span class="tag">React</span><span class="tag">Tailwind</span><span class="tag">Firebase</span></div>
            <div class="project-links">
              <a href="https://youthhope-bd.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="tools">
          <div class="project-img" style="background:linear-gradient(135deg,#1a0a00,#2a1500);">
            <span class="p-icon">📝</span>
          </div>
          <div class="project-body">
            <div class="project-title">Zpad</div>
            <div class="project-desc">Minimal online notepad with markdown support, auto-save, and distraction-free writing mode.</div>
            <div class="project-tags"><span class="tag">JavaScript</span><span class="tag">LocalStorage</span></div>
            <div class="project-links">
              <a href="https://zpad.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

        <div class="project-card" data-cat="tools">
          <div class="project-img" style="background:linear-gradient(135deg,#0a1a0a,#001a1a);">
            <span class="p-icon">🔄</span>
          </div>
          <div class="project-body">
            <div class="project-title">UniConverter</div>
            <div class="project-desc">Universal file converter supporting image, document, and media format conversions in the browser.</div>
            <div class="project-tags"><span class="tag">JavaScript</span><span class="tag">WebAPI</span><span class="tag">CSS3</span></div>
            <div class="project-links">
              <a href="https://uniconverter.netlify.app" class="p-link" target="_blank"><i class="fas fa-external-link-alt"></i> Live Demo</a>
            </div>
          </div>
        </div>

      </div>
    </div>
    <div style="text-align:center;margin-top:36px;" class="reveal">
      <a href="https://ridoan-zisan.netlify.app/blog" class="btn-outline" target="_blank"><i class="fas fa-th-large"></i> &nbsp;View All 50+ Projects</a>
    </div>
  </div>
</section>

<!-- GITHUB STATS -->
<section style="background:var(--bg2);">
  <div class="container">
    <div class="section-label"><i class="fab fa-github"></i> GitHub</div>
    <h2 class="section-title reveal">Contribution <em>Stats</em></h2>
    <div class="gh-stats reveal">
      <div class="gh-stat-img">
        <img src="https://github-readme-stats.vercel.app/api?username=RidoanDev&show_icons=true&theme=tokyonight&rank_icon=github&hide_border=true&bg_color=0D1117&title_color=A78BFA&icon_color=22D3EE&text_color=e0d7ff&border_radius=12" alt="GitHub Stats"/>
      </div>
      <div class="gh-stat-img">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=RidoanDev&theme=tokyonight&hide_border=true&background=0D1117&ring=7c3aed&fire=22d3ee&currStreakLabel=A78BFA&sideLabels=A78BFA&border_radius=12" alt="GitHub Streak"/>
      </div>
    </div>
    <div style="margin-top:16px;" class="reveal">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=RidoanDev&bg_color=0D1117&color=A78BFA&line=22D3EE&point=ffffff&hide_border=true&area=true&area_color=7c3aed&radius=12" width="100%" alt="Activity Graph" style="border-radius:12px;border:1px solid var(--border);"/>
    </div>
  </div>
</section>

<!-- CERTIFICATIONS -->
<section id="certs">
  <div class="container">
    <div class="section-label"><i class="fas fa-medal"></i> Achievements</div>
    <h2 class="section-title reveal">Certifications & <em>Achievements</em></h2>
    <div class="reveal">
      <div style="font-family:'Syne',sans-serif;font-size:0.82rem;letter-spacing:0.15em;text-transform:uppercase;color:var(--accent2);margin-bottom:16px;display:flex;align-items:center;gap:8px;"><i class="fas fa-laptop-code"></i> Technology & Development <span style="flex:1;height:1px;background:var(--border);display:inline-block;margin-left:10px;"></span></div>
      <div class="certs-grid">
        <div class="cert-card"><div class="cert-icon"><i class="fab fa-google"></i></div><div class="cert-name">Google IT Support</div><div class="cert-org">Google · Coursera</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fas fa-shield-alt"></i></div><div class="cert-name">Cyber Security Foundations</div><div class="cert-org">Google · Coursera</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fas fa-code"></i></div><div class="cert-name">Complete Web Development</div><div class="cert-org">Udemy</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fab fa-python"></i></div><div class="cert-name">Introduction to Python</div><div class="cert-org">IBM · Coursera</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fas fa-chart-bar"></i></div><div class="cert-name">Data Science & AI</div><div class="cert-org">IBM · Coursera</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fas fa-robot"></i></div><div class="cert-name">Intro to Artificial Intelligence</div><div class="cert-org">IBM</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fas fa-brain"></i></div><div class="cert-name">Machine Learning</div><div class="cert-org">Stanford · Coursera</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon"><i class="fas fa-bullhorn"></i></div><div class="cert-name">Digital Marketing</div><div class="cert-org">Google</div><div class="cert-badge">✓ Verified</div></div>
      </div>

      <div style="font-family:'Syne',sans-serif;font-size:0.82rem;letter-spacing:0.15em;text-transform:uppercase;color:#4ade80;margin-bottom:16px;margin-top:36px;display:flex;align-items:center;gap:8px;"><i class="fas fa-leaf"></i> Sustainability & Climate <span style="flex:1;height:1px;background:var(--border);display:inline-block;margin-left:10px;"></span></div>
      <div class="certs-grid">
        <div class="cert-card"><div class="cert-icon" style="background:rgba(74,222,128,0.1);color:#4ade80;"><i class="fas fa-venus-mars"></i></div><div class="cert-name">Gender & Climate Action</div><div class="cert-org">IRENA</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon" style="background:rgba(74,222,128,0.1);color:#4ade80;"><i class="fas fa-seedling"></i></div><div class="cert-name">Net Zero 101</div><div class="cert-org">UNFCC</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon" style="background:rgba(74,222,128,0.1);color:#4ade80;"><i class="fas fa-globe-americas"></i></div><div class="cert-name">Sustainable Development</div><div class="cert-org">SDG Academy</div><div class="cert-badge">✓ Verified</div></div>
        <div class="cert-card"><div class="cert-icon" style="background:rgba(74,222,128,0.1);color:#4ade80;"><i class="fas fa-cloud-sun"></i></div><div class="cert-name">UN Climate Process</div><div class="cert-org">UNFCC</div><div class="cert-badge">✓ Verified</div></div>
      </div>

      <div style="font-family:'Syne',sans-serif;font-size:0.82rem;letter-spacing:0.15em;text-transform:uppercase;color:#fbbf24;margin-bottom:16px;margin-top:36px;display:flex;align-items:center;gap:8px;"><i class="fas fa-trophy"></i> Competitions & Leadership <span style="flex:1;height:1px;background:var(--border);display:inline-block;margin-left:10px;"></span></div>
      <div class="certs-grid">
        <div class="cert-card"><div class="cert-icon" style="background:rgba(251,191,36,0.1);color:#fbbf24;"><i class="fas fa-heartbeat"></i></div><div class="cert-name">BOBDO Founder</div><div class="cert-org">Social Leadership</div><div class="cert-badge">🏆 Award</div></div>
        <div class="cert-card"><div class="cert-icon" style="background:rgba(251,191,36,0.1);color:#fbbf24;"><i class="fas fa-infinity"></i></div><div class="cert-name">Math Olympiad</div><div class="cert-org">Bangladesh</div><div class="cert-badge">🥇 Participant</div></div>
        <div class="cert-card"><div class="cert-icon" style="background:rgba(251,191,36,0.1);color:#fbbf24;"><i class="fas fa-microchip"></i></div><div class="cert-name">ICT Olympiad</div><div class="cert-org">Bangladesh</div><div class="cert-badge">🥇 Participant</div></div>
        <div class="cert-card"><div class="cert-icon" style="background:rgba(251,191,36,0.1);color:#fbbf24;"><i class="fas fa-book"></i></div><div class="cert-name">GK Olympiad</div><div class="cert-org">National</div><div class="cert-badge">🥇 Participant</div></div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact" style="background:var(--bg2);">
  <div class="container">
    <div class="section-label"><i class="fas fa-paper-plane"></i> Get In Touch</div>
    <h2 class="section-title reveal">Let's <em>Connect</em></h2>
    <div class="contact-grid reveal">
      <div>
        <p style="color:var(--muted);line-height:1.75;margin-bottom:28px;">
          Whether you have a project in mind, want to collaborate on open source, 
          or just want to say hello — my inbox is always open. I'll get back to you within 24 hours!
        </p>
        <div class="contact-info">
          <a href="mailto:ridoan.zisan@gmail.com" class="contact-item" style="color:inherit;text-decoration:none;">
            <div class="ci-icon" style="background:rgba(234,67,53,0.15);color:#EA4335;"><i class="fab fa-google"></i></div>
            <div class="ci-text"><small>Email</small><span>ridoan.zisan@gmail.com</span></div>
          </a>
          <a href="https://linkedin.com/in/ridoan-zisan" class="contact-item" target="_blank" style="color:inherit;text-decoration:none;">
            <div class="ci-icon" style="background:rgba(0,119,181,0.15);color:#0077B5;"><i class="fab fa-linkedin-in"></i></div>
            <div class="ci-text"><small>LinkedIn</small><span>ridoan-zisan</span></div>
          </a>
          <a href="https://github.com/RidoanDev" class="contact-item" target="_blank" style="color:inherit;text-decoration:none;">
            <div class="ci-icon" style="background:rgba(255,255,255,0.08);color:#fff;"><i class="fab fa-github"></i></div>
            <div class="ci-text"><small>GitHub</small><span>RidoanDev</span></div>
          </a>
          <a href="https://facebook.com/rid0anzisan" class="contact-item" target="_blank" style="color:inherit;text-decoration:none;">
            <div class="ci-icon" style="background:rgba(24,119,242,0.15);color:#1877F2;"><i class="fab fa-facebook-f"></i></div>
            <div class="ci-text"><small>Facebook</small><span>rid0anzisan</span></div>
          </a>
          <a href="https://youtube.com/@ridoan-zisan" class="contact-item" target="_blank" style="color:inherit;text-decoration:none;">
            <div class="ci-icon" style="background:rgba(255,0,0,0.15);color:#FF0000;"><i class="fab fa-youtube"></i></div>
            <div class="ci-text"><small>YouTube</small><span>@ridoan-zisan</span></div>
          </a>
        </div>
      </div>
      <div>
        <div style="background:var(--card);border:1px solid var(--border);border-radius:14px;overflow:hidden;">
          <div style="background:#1a1a2e;padding:12px 20px;border-bottom:1px solid var(--border);font-family:'Space Mono',monospace;font-size:0.78rem;color:var(--muted);display:flex;align-items:center;gap:8px;">
            <div style="width:10px;height:10px;border-radius:50%;background:#ff5f57;"></div>
            <div style="width:10px;height:10px;border-radius:50%;background:#febc2e;"></div>
            <div style="width:10px;height:10px;border-radius:50%;background:#28c840;"></div>
            <span style="margin-left:8px;">message.js</span>
          </div>
          <div style="padding:24px;font-family:'Space Mono',monospace;font-size:0.82rem;line-height:1.9;">
            <span style="color:#f472b6;">const</span> <span style="color:#22d3ee;">message</span> <span style="color:#94a3b8;">= {</span><br/>
            &nbsp;&nbsp;<span style="color:#a78bfa;">to</span><span style="color:#94a3b8;">:</span> <span style="color:#86efac;">"ridoan.zisan@gmail.com"</span><span style="color:#94a3b8;">,</span><br/>
            &nbsp;&nbsp;<span style="color:#a78bfa;">from</span><span style="color:#94a3b8;">:</span> <span style="color:#86efac;">"you@example.com"</span><span style="color:#94a3b8;">,</span><br/>
            &nbsp;&nbsp;<span style="color:#a78bfa;">subject</span><span style="color:#94a3b8;">:</span> <span style="color:#86efac;">"Let's work together!"</span><span style="color:#94a3b8;">,</span><br/>
            &nbsp;&nbsp;<span style="color:#a78bfa;">body</span><span style="color:#94a3b8;">:</span> <span style="color:#86efac;">"Hey Ridoan, I have a project..."</span><br/>
            <span style="color:#94a3b8;">};</span><br/><br/>
            <span style="color:#f472b6;">await</span> <span style="color:#22d3ee;">send</span><span style="color:#94a3b8;">(</span>message<span style="color:#94a3b8;">);</span><br/>
            <span style="color:#94a3b8;">// ✅ Response within 24 hours!</span>
          </div>
        </div>
        <a href="mailto:ridoan.zisan@gmail.com" class="btn-primary" style="display:block;text-align:center;margin-top:16px;">
          <i class="fas fa-envelope"></i> &nbsp;Send Me a Message
        </a>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">RMZ.</div>
  <ul class="footer-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#certs">Certifications</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="https://ridoan-zisan.netlify.app" target="_blank">Portfolio</a></li>
  </ul>
  <div class="footer-social">
    <a href="https://github.com/RidoanDev" class="fs-icon" target="_blank"><i class="fab fa-github"></i></a>
    <a href="https://linkedin.com/in/ridoan-zisan" class="fs-icon" target="_blank"><i class="fab fa-linkedin-in"></i></a>
    <a href="https://facebook.com/rid0anzisan" class="fs-icon" target="_blank"><i class="fab fa-facebook-f"></i></a>
    <a href="https://youtube.com/@ridoan-zisan" class="fs-icon" target="_blank"><i class="fab fa-youtube"></i></a>
    <a href="mailto:ridoan.zisan@gmail.com" class="fs-icon"><i class="fab fa-google"></i></a>
    <a href="https://ridoan-zisan.netlify.app" class="fs-icon" target="_blank"><i class="fas fa-globe"></i></a>
  </div>
  <div class="footer-copy">⚡ Crafted with passion by <strong>Md Ridoan Mahmud Zisan</strong> · Bogura, Bangladesh 🇧🇩 · © 2025</div>
</footer>

<script>
// CURSOR
const cursor = document.getElementById('cursor');
const trail = document.getElementById('cursor-trail');
let mx=0,my=0,tx=0,ty=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  cursor.style.left=(mx-6)+'px';cursor.style.top=(my-6)+'px';
});
function animTrail(){
  tx+=(mx-tx)*0.15;ty+=(my-ty)*0.15;
  trail.style.left=(tx-16)+'px';trail.style.top=(ty-16)+'px';
  requestAnimationFrame(animTrail);
}
animTrail();
document.querySelectorAll('a,button').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cursor.style.transform='scale(2)';trail.style.transform='scale(1.5)';});
  el.addEventListener('mouseleave',()=>{cursor.style.transform='scale(1)';trail.style.transform='scale(1)';});
});

// TYPING
const phrases=['Full Stack Developer','Social Change Maker','Open Source Contributor','EdTech Builder','Problem Solver'];
let pi=0,ci=0,del=false;
const el=document.getElementById('typed-text');
function typeLoop(){
  const phrase=phrases[pi];
  if(!del){
    el.textContent=phrase.slice(0,++ci);
    if(ci===phrase.length){del=true;setTimeout(typeLoop,2000);return;}
  } else {
    el.textContent=phrase.slice(0,--ci);
    if(ci===0){del=false;pi=(pi+1)%phrases.length;setTimeout(typeLoop,400);return;}
  }
  setTimeout(typeLoop,del?60:90);
}
typeLoop();

// REVEAL
const observer=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.classList.add('visible');
      // SKILL BARS
      e.target.querySelectorAll('.sb-fill').forEach(bar=>{
        bar.style.width=bar.dataset.w+'%';
      });
      // COUNTERS
      e.target.querySelectorAll('[data-target]').forEach(el=>{
        const target=+el.dataset.target;
        let current=0;
        const step=target/60;
        const timer=setInterval(()=>{
          current+=step;
          if(current>=target){current=target;clearInterval(timer);}
          el.textContent=Math.floor(current)+(target>=50?'+':target>=5?'+':'');
        },20);
      });
    }
  });
},{threshold:0.15});
document.querySelectorAll('.reveal').forEach(el=>observer.observe(el));

// TABS
function showTab(cat,btn){
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const grid=document.querySelector('#tab-all .projects-grid');
  grid.querySelectorAll('.project-card').forEach(card=>{
    if(cat==='all'||card.dataset.cat===cat){
      card.style.display='';
    } else {
      card.style.display='none';
    }
  });
}
</script>
</body>
</html>
