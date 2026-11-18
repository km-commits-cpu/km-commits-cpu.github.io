<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Which Scootizien are you?</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
:root{--y:#FFDD00;--y2:#FFF3A3;--k:#000;--w:#fff;--g:#4a4a4a;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
*,*::before,*::after{box-sizing:inherit}
html{scroll-padding-top:env(safe-area-inset-top,0px);height:100%}
body{margin:0;min-height:100%;background:var(--y);color:var(--k);font-family:"Fredoka",system-ui,-apple-system,"Segoe UI",Arial,sans-serif;font-size:18px;line-height:1.45;display:flex;flex-direction:column}
main{flex:1;width:100%;max-width:680px;margin:0 auto;padding:24px 20px 40px}
.brand{display:flex;align-items:center;gap:10px;font-weight:700;font-size:22px;margin-bottom:28px}
.brand i{display:inline-block;background:var(--k);color:var(--y);border-radius:999px;padding:2px 14px;font-style:normal}
h1{font-size:clamp(40px,11vw,68px);line-height:1;margin:0 0 16px;font-weight:700;letter-spacing:-.02em}
h2{font-size:30px;line-height:1.1;margin:0 0 12px}
p{margin:0 0 16px}
.btn{font:inherit;font-weight:600;font-size:20px;background:var(--k);color:var(--y);border:3px solid var(--k);border-radius:999px;padding:12px 32px;cursor:pointer}
.btn.alt{background:var(--w);color:var(--k)}
.btn:focus-visible,.opt:focus-visible{outline:4px solid var(--w);outline-offset:3px;box-shadow:0 0 0 7px var(--k)}
.btn:hover{transform:translateY(-2px)}
.card{background:var(--w);border:3px solid var(--k);border-radius:28px;padding:22px}
.note{font-size:15px;color:var(--k);background:var(--y2);border:2px dashed var(--k);border-radius:18px;padding:12px 16px;margin-top:24px}
.hero-pill{display:inline-block;background:var(--k);color:var(--y);border-radius:999px;padding:4px 16px;font-weight:600;margin-bottom:16px;font-size:16px}
.bar{height:14px;background:var(--y2);border:2px solid var(--k);border-radius:999px;overflow:hidden;margin-bottom:6px}
.bar>div{height:100%;background:var(--k);width:0;transition:width .3s}
.count{font-size:15px;font-weight:500;margin-bottom:22px}
.q{font-size:clamp(24px,6vw,32px);line-height:1.2;font-weight:600;margin:0 0 22px;min-height:3.6em}
.opts{display:grid;gap:10px}
.opt{font:inherit;font-weight:500;text-align:left;background:var(--w);color:var(--k);border:3px solid var(--k);border-radius:18px;padding:12px 18px;cursor:pointer;display:flex;align-items:center;gap:12px}
.opt:hover{background:var(--y2)}
.opt.on{background:var(--k);color:var(--y)}
.opt b{display:inline-flex;align-items:center;justify-content:center;width:30px;height:30px;border-radius:50%;border:2px solid currentColor;font-size:15px;flex:none}
.nav{display:flex;justify-content:space-between;margin-top:18px}
.link{background:none;border:0;font:inherit;font-weight:600;text-decoration:underline;cursor:pointer;color:var(--k);padding:6px}
.hide{display:none!important}
.result{text-align:center}
.emoji{font-size:64px;line-height:1}
.role{font-size:clamp(34px,9vw,52px);line-height:1.05;margin:8px 0 12px;font-weight:700}
.scores{text-align:left;margin-top:20px}
.scores .row{display:grid;grid-template-columns:minmax(0,1fr) 46px;gap:4px 10px;align-items:center;font-size:16px;margin-bottom:10px}
.scores .row span{font-weight:600}
.scores .row em{font-style:normal;text-align:right;font-weight:600}
.scores .bar{grid-column:1/-1;margin:0;height:12px}
.qr{display:flex;gap:18px;align-items:center;flex-wrap:wrap;justify-content:center;text-align:left;margin-top:28px}
#qrbox{background:#fff;padding:10px;border:3px solid var(--k);border-radius:18px;line-height:0}
#qrbox img,#qrbox canvas{max-width:160px;height:auto}
.qr p{margin:0 0 10px;max-width:300px;font-size:16px}
footer{padding:0 20px 24px;text-align:center;font-size:14px}
.info h3{font-size:22px;margin:0 0 6px}.info ul{margin:0 0 16px;padding-left:22px;font-size:16px}.info li{margin-bottom:4px}.info .p{font-weight:500}.info small{display:block;font-size:13px;margin-top:6px}
@media (prefers-reduced-motion:reduce){*{transition:none!important}}
</style>
</head>
<body>
<main>
<div class="brand">Scoot <i>careers</i></div>

<section id="intro">
  <span class="hero-pill">A quick personality quiz</span>
  <h1>Which Scootizien are you?</h1>
  <p>Rate 12 short statements and find the Scoot role that matches your style best. It takes about 2 minutes.</p>
  <button class="btn" id="start">Start the quiz</button>
  <div class="note"><strong>Please note:</strong> this quiz is just for fun. It helps spread awareness of the different roles at Scoot and is not a tool for deciding whether you qualify for any job.</div>
</section>

<section id="quiz" class="hide">
  <div class="bar" aria-hidden="true"><div id="fill"></div></div>
  <div class="count" id="count"></div>
  <p class="q" id="q" aria-live="polite"></p>
  <div class="opts" id="opts"></div>
  <div class="nav"><button class="link" id="back">Back</button><button class="link" id="restart">Start over</button></div>
</section>

<section id="out" class="hide">
  <div class="card result">
    <div class="emoji" id="emoji"></div>
    <p style="margin:0">You are a</p>
    <div class="role" id="rname"></div>
    <p id="rdesc"></p>
    <div class="scores" id="scores"></div>
  </div>
  <div class="card info" id="info" style="margin-top:20px"></div>
  <div class="note">This quiz is just for fun and spreads awareness of the roles at Scoot. It does not show whether you qualify for any job.</div>
  <div class="qr card" style="margin-top:20px">
    <div id="qrbox2"></div>
    <div>
      <p><strong>Share the quiz with friends.</strong> Scan the code or copy the link.</p>
      <button class="btn alt" id="copy" style="font-size:16px;padding:8px 20px">Copy link</button>
    </div>
  </div>
  <p style="text-align:center;margin-top:24px"><button class="btn" id="again">Take it again</button></p>
</section>

<section id="qrsec" class="qr card" style="margin-top:32px">
  <div id="qrbox"></div>
  <div>
    <p><strong>Scan to take the quiz.</strong> Point your phone camera at the code to open this page.</p>
    <button class="btn alt" id="dl" style="font-size:16px;padding:8px 20px">Download QR code</button>
  </div>
</section>
</main>
<footer>Which Scootizien are you? is a fun awareness quiz about roles at Scoot.</footer>

<script>
var ROLES=[
{n:"Cabin Crew",e:"💛",d:"You light up around people. Warm, calm and quick to notice who needs a hand, you make every journey feel welcoming and look after everyone on board.",q:[
"I enjoy meeting new people and making them feel welcomed.",
"I naturally look out for others and enjoy helping them with their needs.",
"I can remain calm and positive when dealing with difficult or demanding people.",
"I enjoy working closely with others to create a positive experience.",
"I am comfortable speaking to and interacting with people from different backgrounds.",
"I can adapt quickly when plans or situations change unexpectedly.",
"I pay attention to my surroundings and notice when someone might need help.",
"I am willing to take responsibility for the safety and well-being of others.",
"I can maintain a professional and positive attitude even when I feel tired or stressed.",
"I enjoy jobs that allow me to travel, meet people and experience different environments."]},
{n:"Flight Dispatcher",e:"🗺️",d:"You plan ahead, spot problems early and trust the facts. Dispatchers map out the safest and most efficient route for every flight before it leaves the ground.",q:[
"I enjoy analysing information before making important decisions.",
"I like planning ahead and organising tasks before getting started.",
"I am good at spotting potential problems before they happen.",
"I enjoy working with numbers, charts and detailed information.",
"I pay close attention to details to ensure my work is accurate.",
"I enjoy comparing different options to find the safest and most efficient solution.",
"I am interested in understanding how weather conditions can affect plans and decisions.",
"I can follow rules and procedures carefully, even when completing repetitive tasks.",
"I am comfortable making decisions based on facts and available information rather than guesses.",
"I enjoy coordinating with different people to make sure everyone has the information they need."]},
{n:"Operations Controller",e:"⚡",d:"You think fast and keep many things moving at once. Operations Controllers coordinate people and plans, and find solutions when things change.",q:[
"I can think quickly and make decisions when unexpected situations arise.",
"I enjoy coordinating different people and tasks to ensure everything runs smoothly.",
"I am comfortable handling multiple responsibilities at the same time.",
"When things do not go according to plan, I naturally take the initiative to find solutions.",
"I enjoy keeping track of schedules, deadlines and changing situations.",
"I can prioritise tasks when several urgent matters need my attention.",
"I am good at communicating important updates to different people.",
"I enjoy finding ways to make processes more efficient and organised.",
"I can stay focused when working in a fast-paced and high-pressure environment.",
"I enjoy solving problems that require teamwork, quick thinking and careful coordination."]},
{n:"Engineer",e:"🔧",d:"You love knowing how things work and fixing what doesn't. Engineers are patient, hands-on and detail-minded, and keep aircraft safe and ready to fly.",q:[
"I enjoy understanding how machines, equipment and technical systems work.",
"I like figuring out why something is not working and finding ways to fix it.",
"I pay close attention to small details, especially when completing important tasks.",
"I enjoy practical, hands-on activities more than purely theoretical work.",
"I am interested in learning about aircraft systems and how they operate.",
"I can remain patient when troubleshooting a problem that takes time to solve.",
"I understand the importance of following technical instructions and safety procedures carefully.",
"I enjoy organising tools, materials and resources to complete a task efficiently.",
"I can take responsibility and make decisions when a technical issue needs attention.",
"I enjoy working with others to solve technical problems and get things back on track."]},
{n:"Pilot",e:"✈️",d:"You stay composed under pressure and take responsibility. Pilots lead their team, follow procedures with discipline and keep learning every day.",q:[
"I am comfortable taking responsibility and making important decisions.",
"I can stay focused and composed even in high-pressure situations.",
"I enjoy taking the lead while making sure everyone in my team works together.",
"I am passionate about continuously learning new skills and challenging myself.",
"I can assess risks carefully before deciding on a course of action.",
"I am comfortable following strict procedures when safety is involved.",
"I can communicate clearly with others, especially when situations become stressful.",
"I enjoy working towards a shared goal where every team member has an important responsibility.",
"I am able to remain disciplined and focused even during long or demanding tasks.",
"I am willing to take accountability for my decisions and their outcomes."]},
{n:"Revenue Management Analyst",e:"📈",d:"You find the story in the numbers. Revenue Management Analysts study demand and customer behaviour to predict what's next and help the business grow.",q:[
"I enjoy analysing data to identify patterns and trends.",
"I am interested in understanding what influences people’s choices and spending habits.",
"I enjoy working with numbers and using them to solve problems.",
"I like predicting future outcomes based on past information.",
"I enjoy comparing different strategies to find the most effective one.",
"I am interested in understanding how businesses make money and remain profitable.",
"I enjoy finding ways to improve efficiency and achieve better results.",
"I can make decisions based on data rather than personal assumptions.",
"I am comfortable working independently on tasks that require focus and accuracy.",
"I enjoy exploring how changes in demand, seasons and customer behaviour can affect business performance."]}
];
var INFO=[
{p:"Cabin Crew keep passengers safe, comfortable and happy on every flight while representing the Scoot brand.",r:["Follow aviation regulations to keep passengers safe throughout the flight","Assist passengers and keep them comfortable during the journey","Act as a brand ambassador by creating positive customer interactions","Work with fellow cabin crew to deliver consistent service","Respond effectively to situations on board"],g:["Perks include unlimited staff travel for you, family and friends, an annual performance bonus and a vibrant, fun-oriented culture","Rostered shifts, weekend and public holiday duties, frequent travel and a physically demanding environment","Minimum age 18, plus GCE O-Level, N(A)/N(T) or SPM passes in the required subjects including English","Height and grooming standards apply, so check the official job listing for full details"]},
{p:"Flight Dispatchers plan and monitor flights across the Scoot fleet, linking pilots, engineering, ground operations and air traffic control.",r:["Prepare operational flight plans and briefing packages for crews","Plan routes and fuel, and analyse weather and NOTAMs","Assess risks such as tropical storms, volcanic activity and airspace restrictions","File flight plans with Air Traffic Services and keep them up to date","Coordinate with pilots, flight operations, engineering, ground operations and ATC"],g:["Diploma or degree, with a technical or engineering background preferred","Aviation education or operational experience is an advantage","Works in the Operations Control Centre on 24-hour rotating shifts, including weekends and public holidays","Fast-paced, real-time and time-sensitive"]},
{p:"Operations Controllers keep Scoot’s A320, Boeing 787 and Embraer E190 flights safe, punctual and reliable day to day.",r:["Dispatch flights safely and monitor them in real time through flight watch","Plan aircraft utilisation and retime flights when disruptions happen","Make sure flights are crewed within a 72-hour window and duty limits are legal","Manage disruptions such as delays, crew no-shows and medical leave","Keep crews, airports and stations updated on changes","Prepare and verify operational documents such as APIS submissions"],g:["Disruption recovery is a major part of the job","Works with flight crews, airports, stations and operational stakeholders","Uses messaging, ACARS and radio systems to track aircraft"]},
{p:"Engineering operations support keeps Scoot’s B787 and A320 aircraft ready to fly and minimises disruption to the flight schedule.",r:["Monitor aircraft movements and coordinate AOG, return-to-base and air turn-back events","Track deferred defects and critical maintenance tasks so they are completed on time","Coordinate daily maintenance carried out by maintenance repair organisations","Give technical advice and documentation references for the B787 and A320","Arrange AOG spare parts and support aircraft recovery during delays"],g:["Experience in line maintenance and in spare parts or inventory control","A SAR-66 B1.1 licence and B787 and A320 type ratings are preferred","Works in a 24/7, time-sensitive operation with the Duty Manager Engineering, the Operations Control Centre, licensed engineers and logistics teams"]},
{p:"First Officers support the Captain, and Captains command the aircraft. Both keep flights safe, efficient and punctual and bring Scootitude to the flight deck.",r:["First Officer: assist the Captain, follow safety standards and contribute to on-time performance","Captain: command the aircraft, lead cockpit and cabin crew, and mentor teammates","A320 Captains fly short-haul and regional routes, and B787 Captains fly wide-body long-haul","Work closely with cabin crew and operations personnel"],g:["First Officer: 1,500+ fixed-wing hours on aircraft of 5,700 kg MTOM or more","A320 Captain: 3,500+ hours with 1,000+ PIC hours. B787 Captain: 5,000+ hours with 2,000+ PIC hours","CAAS-issued ICAO CPL(A) or ATPL(A) for First Officers, ATPL for Captains, and ICAO English Level 4 or above","Selection has four stages: screening, online assessments, an assessment centre, then a two-day simulator and personality assessment","Type-rating training involves co-payment and a training bond"]},
{p:"Revenue Management Analysts help Scoot sell the right seat, at the right price, to the right customer, at the right time.",r:["Manage seat inventory, fare classes and capacity on assigned routes","Forecast demand from booking patterns, seasons, festival peaks and no-shows","Set overbooking levels to reduce revenue lost to no-shows","Analyse booking, pricing and revenue data to find growth opportunities","Work with commercial, network planning and operations teams"],g:["Bachelor’s degree in business, economics, finance, accounting, maths, statistics or a related field","Microsoft Excel is essential, and revenue management or business intelligence tools are an advantage","Office-based, data-driven and commercially dynamic"]}
];
var LABELS=["Strongly disagree","Disagree","Neutral","Agree","Strongly agree"];
var PER=2,Q=[],ans=[],i=0;
function $(id){return document.getElementById(id)}
function show(id){["intro","quiz","out"].forEach(function(s){$(s).classList.toggle("hide",s!==id)});$("qrsec").classList.toggle("hide",id!=="intro");window.scrollTo(0,0)}
function shuffle(a){for(var j=a.length-1;j>0;j--){var k=Math.floor(Math.random()*(j+1));var t=a[j];a[j]=a[k];a[k]=t}return a}
function begin(){Q=[];ROLES.forEach(function(r,ri){shuffle(r.q.slice()).slice(0,PER).forEach(function(t){Q.push({r:ri,t:t})})});shuffle(Q);ans=[];i=0;show("quiz");render()}
function render(){
  $("q").textContent=Q[i].t;
  $("count").textContent="Statement "+(i+1)+" of "+Q.length;
  $("fill").style.width=(i/Q.length*100)+"%";
  $("back").style.visibility=i?"visible":"hidden";
  var h="";LABELS.forEach(function(l,n){h+='<button class="opt'+(ans[i]===n+1?' on':'')+'" data-v="'+(n+1)+'"><b>'+(n+1)+'</b>'+l+'</button>'});
  $("opts").innerHTML=h;
}
$("opts").addEventListener("click",function(e){
  var b=e.target.closest(".opt");if(!b)return;
  ans[i]=+b.dataset.v;
  b.classList.add("on");
  setTimeout(function(){if(i<Q.length-1){i++;render()}else finish()},160);
});
function finish(){
  var sum=[],cnt=[];ROLES.forEach(function(){sum.push(0);cnt.push(0)});
  Q.forEach(function(q,n){sum[q.r]+=ans[n]||0;cnt[q.r]++});
  var s=sum.map(function(v,n){return cnt[n]?(v/cnt[n]-1)/4*100:-1});
  var order=shuffle(s.map(function(v,n){return n}).filter(function(n){return cnt[n]>0})).sort(function(a,b){return s[b]-s[a]});
  var w=ROLES[order[0]];
  $("emoji").textContent=w.e;$("rname").textContent=w.n;$("rdesc").textContent=w.d;
  var h="";order.forEach(function(n){var p=Math.round(s[n]);h+='<div class="row"><span>'+ROLES[n].n+'</span><em>'+p+'%</em><div class="bar"><div style="width:'+p+'%"></div></div></div>'});
  $("scores").innerHTML='<strong>How you scored across the roles</strong><div style="height:10px"></div>'+h;
  var f=INFO[order[0]];
  $("info").innerHTML='<h3>About the role</h3><p class="p">'+f.p+'</p><h3>What they do</h3><ul>'+f.r.map(function(x){return"<li>"+x+"</li>"}).join("")+'</ul><h3>Good to know</h3><ul>'+f.g.map(function(x){return"<li>"+x+"</li>"}).join("")+'</ul><small>Based on Scoot’s job listings. Requirements can change, so check Scoot’s official careers page for the latest details.</small>';
  show("out");
}
$("start").onclick=begin;$("again").onclick=begin;
$("restart").onclick=function(){show("intro")};
$("back").onclick=function(){if(i>0){i--;render()}};
$("copy").onclick=function(){var u=shareUrl();var b=$("copy");
  function ok(){b.textContent="Link copied"}
  if(navigator.clipboard){navigator.clipboard.writeText(u).then(ok,function(){b.textContent=u})}else b.textContent=u};
var SHARE_URL="";
function shareUrl(){if(SHARE_URL)return SHARE_URL;var u=location.href.split("#")[0];return /^https?:/.test(u)?u:""}
function makeQR(id){
  try{var el=$(id);el.innerHTML="";
    new QRCode(el,{text:shareUrl(),width:200,height:200,colorDark:"#000000",colorLight:"#ffffff",correctLevel:QRCode.CorrectLevel.M});
    el.style.cssText="background:#fff;padding:10px;border:3px solid #000;border-radius:18px;line-height:0";
  }catch(e){$(id).textContent="QR code unavailable"}
}
makeQR("qrbox");makeQR("qrbox2");
$("dl").onclick=function(){
  var c=document.querySelector("#qrbox canvas");if(!c)return;
  var a=document.createElement("a");a.download="scootizien-quiz-qr.png";a.href=c.toDataURL("image/png");a.click();
};
</script>
</body>
</html>
