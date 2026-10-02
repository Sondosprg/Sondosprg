<!DOCTYPE html>
<html lang="en" data-theme="desert">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Soundous | Front-End Developer</title>
<style>
:root{box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);
--text:#fff3d6;--muted:#ead2a0;--accent:#f2c14e;--card:rgba(30,12,4,.52);--line:rgba(242,193,78,.5);
--h1:linear-gradient(100deg,#8a5a12 0%,#f7dc8a 25%,#fff4c4 40%,#d9a233 55%,#8a5a12 75%,#f7dc8a 100%);
--btn:linear-gradient(135deg,#fff0b0,#e0aa3a 50%,#9c6a14);--btntext:#2c1602;--chipbg:rgba(255,225,150,.1);--hi:rgba(255,235,180,.25)}
:root[data-theme="snow"]{--text:#f2f7ff;--muted:#bcd0ee;--accent:#8fd3ff;--card:rgba(8,18,45,.5);--line:rgba(160,210,255,.45);
--h1:linear-gradient(100deg,#6aa9e0 0%,#e8f5ff 28%,#ffffff 42%,#9fd2ff 58%,#6aa9e0 78%,#e8f5ff 100%);
--btn:linear-gradient(135deg,#ffffff,#a9dcff 55%,#5aa7e6);--btntext:#06223f;--chipbg:rgba(170,215,255,.1);--hi:rgba(200,230,255,.25)}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;min-height:100vh;color:var(--text);font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;background:#1a1030;overflow-x:hidden}
svg.i{width:1.1em;height:1.1em;fill:none;stroke:currentColor;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;flex:none}
canvas{position:fixed;inset:0;width:100%;height:100%;pointer-events:none}
#bg{z-index:0}#fx{z-index:1}
.switch{position:fixed;z-index:5;top:calc(env(safe-area-inset-top,0px) + 14px);right:14px;display:flex;padding:4px;gap:4px;border-radius:999px;background:var(--card);border:1px solid var(--line);backdrop-filter:blur(10px)}
.switch button{display:flex;align-items:center;gap:6px;border:0;border-radius:999px;padding:8px 14px;background:transparent;color:var(--text);font:600 .85rem system-ui,sans-serif;cursor:pointer}
.switch button[aria-pressed="true"]{background:var(--btn);color:var(--btntext)}
main{position:relative;z-index:2;max-width:760px;margin:0 auto;padding:84px 20px 180px}
h1{display:flex;align-items:center;gap:12px;flex-wrap:wrap;font-size:clamp(2rem,6vw,3.4rem);margin:0 0 8px;color:var(--accent)}
h1 svg{width:.9em;height:.9em;filter:drop-shadow(0 2px 6px rgba(0,0,0,.5))}
h1 span{background:var(--h1);background-size:250% auto;-webkit-background-clip:text;background-clip:text;color:transparent;animation:shine 6s linear infinite;filter:drop-shadow(0 3px 6px rgba(0,0,0,.55))}
@keyframes shine{to{background-position:250% center}}
.role{color:var(--accent);font-size:1.2rem;margin:0 0 18px;text-shadow:0 2px 6px rgba(0,0,0,.5)}
p.lead{color:var(--muted);line-height:1.7;font-size:1.05rem;text-shadow:0 1px 4px rgba(0,0,0,.5)}
section{margin-top:28px;padding:22px;background:var(--card);border:1px solid var(--line);border-radius:16px;backdrop-filter:blur(10px);box-shadow:0 14px 40px rgba(0,0,0,.4),inset 0 1px 0 var(--hi)}
h2{display:flex;align-items:center;gap:10px;margin:0 0 14px;font-size:1.1rem;color:var(--accent)}
.chips{display:flex;flex-wrap:wrap;gap:10px}
.chip{position:relative;padding:7px 14px 7px 34px;border-radius:10px;font-size:.9rem;background:var(--chipbg);border:1px solid var(--line)}
.chip::before{content:"";position:absolute;left:11px;top:50%;width:12px;height:12px;margin-top:-6px;background:conic-gradient(from 20deg,var(--g),#fff 18%,var(--g) 32%,rgba(0,0,0,.45) 55%,var(--g) 75%,#fff 90%,var(--g));clip-path:polygon(50% 0,100% 35%,50% 100%,0 35%);filter:drop-shadow(0 0 4px var(--g))}
.chip:nth-child(5n+1){--g:#e0245e}.chip:nth-child(5n+2){--g:#1fb97a}.chip:nth-child(5n+3){--g:#2f9bff}.chip:nth-child(5n+4){--g:#a45bff}.chip:nth-child(5n){--g:#f5c84a}
a.btn{display:inline-flex;align-items:center;gap:8px;margin:6px 8px 0 0;padding:10px 18px;border-radius:10px;background:var(--btn);color:var(--btntext);text-decoration:none;font-weight:700;box-shadow:0 4px 14px rgba(0,0,0,.4),inset 0 1px 0 rgba(255,255,255,.7)}
a.btn.alt{background:transparent;color:var(--text);border:1px solid var(--line);box-shadow:none}
</style>
</head>
<body>
<canvas id="bg"></canvas><canvas id="fx"></canvas>
<div class="switch" role="group" aria-label="Theme">
  <button id="bd" aria-pressed="true"><svg class="i" viewBox="0 0 24 24"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M6.34 17.66l-1.41 1.41M19.07 4.93l-1.41 1.41"/></svg>Desert</button>
  <button id="bs" aria-pressed="false"><svg class="i" viewBox="0 0 24 24"><path d="M2 12h20M12 2v20M20 16l-4-4 4-4M4 8l4 4-4 4M16 4l-4 4-4-4M8 20l4-4 4 4"/></svg>Snow</button>
</div>
<main>
  <h1><svg class="i" viewBox="0 0 24 24"><path d="M6 3h12l4 6-10 13L2 9Z"/><path d="M11 3 8 9l4 13 4-13-3-6M2 9h20"/></svg><span>Hi, I'm Soundous</span></h1>
  <p class="role">Front-End Developer</p>
  <p class="lead">I'm a passionate front-end developer who loves creating modern, responsive, and user-friendly web applications.</p>
  <section><h2><svg class="i" viewBox="0 0 24 24"><path d="M16 18l6-6-6-6M8 6l-6 6 6 6"/></svg>Front-End</h2><div class="chips"><span class="chip">HTML5</span><span class="chip">CSS3</span><span class="chip">JavaScript</span><span class="chip">React</span><span class="chip">Tailwind CSS</span><span class="chip">Bootstrap</span></div></section>
  <section><h2><svg class="i" viewBox="0 0 24 24"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94z"/></svg>Tools &amp; Workflow</h2><div class="chips"><span class="chip">Git</span><span class="chip">GitHub</span><span class="chip">VS Code</span><span class="chip">Jupyter</span></div></section>
  <section><h2><svg class="i" viewBox="0 0 24 24"><path d="M12 20V10M18 20V4M6 20v-4"/></svg>Data &amp; Programming</h2><div class="chips"><span class="chip">Python</span><span class="chip">MySQL</span><span class="chip">Pandas</span><span class="chip">NumPy</span><span class="chip">Matplotlib</span><span class="chip">Streamlit</span></div></section>
  <section><h2><svg class="i" viewBox="0 0 24 24"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-10 6L2 7"/></svg>Contact</h2>
    <a class="btn" href="mailto:sondos23cv@gmail.com"><svg class="i" viewBox="0 0 24 24"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-10 6L2 7"/></svg>Email me</a>
    <a class="btn alt" href="https://forms.gle/MHST6q8mviHoMeEs9"><svg class="i" viewBox="0 0 24 24"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>Share your opinion</a></section>
</main>
<script>
const bg=document.getElementById('bg'),b=bg.getContext('2d'),fx=document.getElementById('fx'),x=fx.getContext('2d');
let W,H,P=[],sand=[],seed=7,theme='desert';
try{const t=localStorage.getItem('theme');if(t==='snow'||t==='desert')theme=t}catch(e){}
const rnd=()=>{seed=(seed*16807)%2147483647;return seed/2147483647};
function ridge(px,i,base,amp){return base+Math.sin(px*.004+i*2.1)*amp+Math.sin(px*.011+i*5.3)*amp*.45+Math.sin(px*.027+i)*amp*.12}
function stars(n,maxY){for(let i=0;i<n;i++){b.fillStyle='rgba(255,255,255,'+(rnd()*.7)+')';b.fillRect(rnd()*W,rnd()*H*maxY,1.2,1.2)}}
function dune(L,i,sunX,tone){
  const lg=b.createLinearGradient(0,H*L.base-L.amp,0,H);lg.addColorStop(0,L.c1);lg.addColorStop(.35,L.c2);lg.addColorStop(1,tone.bot);
  const path=()=>{b.beginPath();b.moveTo(0,H);for(let px=0;px<=W;px+=6)b.lineTo(px,ridge(px,i,H*L.base,L.amp));b.lineTo(W,H);b.closePath()};
  path();b.fillStyle=lg;b.fill();
  const sh=b.createLinearGradient(0,0,W,0);
  sh.addColorStop(0,'rgba(20,6,10,.45)');sh.addColorStop(Math.max(.05,sunX/W-.25),'rgba(20,6,10,0)');sh.addColorStop(Math.min(.95,sunX/W+.05),tone.lit);sh.addColorStop(1,'rgba(20,6,10,.35)');
  b.fillStyle=sh;b.fill();
  b.beginPath();for(let px=0;px<=W;px+=6){const y=ridge(px,i,H*L.base,L.amp);px?b.lineTo(px,y):b.moveTo(px,y)}
  b.strokeStyle=tone.edge+(.55-i*.12)+')';b.lineWidth=1.6;b.stroke();
  for(let k=0;k<900;k++){const px=rnd()*W,top=ridge(px,i,H*L.base,L.amp),py=top+rnd()*(H-top)*.6;b.fillStyle=rnd()<.5?tone.g1:tone.g2;b.fillRect(px,py,1.4,1)}
  if(L.haze){const hz=b.createLinearGradient(0,H*L.base-L.amp,0,H*L.base+120);hz.addColorStop(0,tone.haze+L.haze+')');hz.addColorStop(1,tone.haze+'0)');path();b.fillStyle=hz;b.fill()}
}
function vignette(){const vg=b.createRadialGradient(W/2,H/2,H*.35,W/2,H/2,H*.95);vg.addColorStop(0,'rgba(0,0,0,0)');vg.addColorStop(1,'rgba(10,3,6,.55)');b.fillStyle=vg;b.fillRect(0,0,W,H)}
function desertScene(){
  seed=7;const sunX=W*.62,sunY=H*.6;
  let g=b.createLinearGradient(0,0,0,H*.75);
  g.addColorStop(0,'#1d1240');g.addColorStop(.35,'#6a2b55');g.addColorStop(.62,'#d4623a');g.addColorStop(.85,'#f6a64a');g.addColorStop(1,'#fbd78a');
  b.fillStyle=g;b.fillRect(0,0,W,H);stars(110,.38);
  let r=b.createRadialGradient(sunX,sunY,0,sunX,sunY,H*.55);
  r.addColorStop(0,'rgba(255,250,220,1)');r.addColorStop(.04,'rgba(255,236,170,1)');r.addColorStop(.09,'rgba(255,196,100,.55)');r.addColorStop(.3,'rgba(255,140,70,.22)');r.addColorStop(1,'rgba(255,120,60,0)');
  b.fillStyle=r;b.fillRect(0,0,W,H);
  const tone={bot:'#1a0c08',lit:'rgba(255,200,110,.22)',edge:'rgba(255,215,140,',g1:'rgba(255,225,170,.07)',g2:'rgba(40,15,8,.09)',haze:'rgba(255,190,120,'};
  [{base:.66,amp:40,c1:'#e9a15a',c2:'#8a4a2c',haze:.5},{base:.74,amp:55,c1:'#d58a45',c2:'#6f3724',haze:.3},{base:.84,amp:70,c1:'#b8683a',c2:'#4d2418',haze:.14},{base:.95,amp:60,c1:'#8e4a28',c2:'#2c140d',haze:0}].forEach((L,i)=>dune(L,i,sunX,tone));
  vignette();
}
function snowScene(){
  seed=11;const mx=W*.78,my=H*.2;
  let g=b.createLinearGradient(0,0,0,H);
  g.addColorStop(0,'#050b1f');g.addColorStop(.45,'#0d1f4a');g.addColorStop(.75,'#1c3a73');g.addColorStop(1,'#2b5a8f');
  b.fillStyle=g;b.fillRect(0,0,W,H);stars(160,.55);
  let r=b.createRadialGradient(mx,my,0,mx,my,H*.4);
  r.addColorStop(0,'rgba(255,255,255,1)');r.addColorStop(.05,'rgba(230,240,255,1)');r.addColorStop(.1,'rgba(180,210,255,.4)');r.addColorStop(1,'rgba(120,160,255,0)');
  b.fillStyle=r;b.fillRect(0,0,W,H);
  const tone={bot:'#9fb8dc',lit:'rgba(255,255,255,.28)',edge:'rgba(255,255,255,',g1:'rgba(255,255,255,.18)',g2:'rgba(60,90,150,.12)',haze:'rgba(170,200,255,'};
  [{base:.68,amp:36,c1:'#c9dcf5',c2:'#6f8fc2',haze:.5},{base:.78,amp:48,c1:'#e2edfb',c2:'#8fadd8',haze:.3},{base:.9,amp:55,c1:'#f4f9ff',c2:'#b7cdec',haze:0}].forEach((L,i)=>dune(L,i,mx,tone));
  vignette();
}
const cols=[['#ff4d78','#7a0a2a'],['#34e0a0','#05603f'],['#5db8ff','#0a3f8a'],['#b57bff','#4a1a8f'],['#ffe27a','#9a6a05']];
function mk(init){const z=Math.random();
  if(theme==='snow')return{gem:false,z,x:Math.random()*W,y:init?Math.random()*H:-10,r:.8+z*3,s:.4+z*1.1,d:Math.random()*6.28,rot:0,vr:0,c:cols[0]};
  const gem=Math.random()<.28;
  return{gem,z,x:Math.random()*W,y:init?Math.random()*H:-20,r:gem?4+z*9:.6+z*1.8,s:.25+z*.8,d:Math.random()*6.28,rot:Math.random()*6.28,vr:(Math.random()-.5)*.03,c:cols[Math.floor(Math.random()*5)]}}
function build(){scene();P=Array.from({length:Math.min(theme==='snow'?170:90,Math.floor(W/(theme==='snow'?7:11)))},()=>mk(true));
  sand=theme==='snow'?[]:Array.from({length:Math.min(140,Math.floor(W/7))},()=>({x:Math.random()*W,y:H*(.6+Math.random()*.4),v:1+Math.random()*2.5,a:Math.random()*.4+.1}))}
function scene(){theme==='snow'?snowScene():desertScene()}
function size(){W=bg.width=fx.width=innerWidth;H=bg.height=fx.height=innerHeight;build()}
function setTheme(t){theme=t;document.documentElement.dataset.theme=t;
  document.getElementById('bd').setAttribute('aria-pressed',t==='desert');document.getElementById('bs').setAttribute('aria-pressed',t==='snow');
  try{localStorage.setItem('theme',t)}catch(e){}if(W)build()}
document.getElementById('bd').onclick=()=>setTheme('desert');
document.getElementById('bs').onclick=()=>setTheme('snow');
addEventListener('resize',size);
function gem(p,t){
  const r=p.r;x.save();x.translate(p.x,p.y);x.rotate(p.rot);
  const pts=[];for(let i=0;i<8;i++){const a=i/8*6.283;pts.push([Math.cos(a)*r,Math.sin(a)*r*.92])}
  const inner=pts.map(q=>[q[0]*.5,q[1]*.5]);
  x.shadowColor=p.c[0];x.shadowBlur=12*p.z+4;
  for(let i=0;i<8;i++){const j=(i+1)%8,l=.35+.65*Math.abs(Math.sin(i*1.3+p.rot*2));
    x.beginPath();x.moveTo(pts[i][0],pts[i][1]);x.lineTo(pts[j][0],pts[j][1]);x.lineTo(inner[j][0],inner[j][1]);x.lineTo(inner[i][0],inner[i][1]);x.closePath();
    x.fillStyle=i%2?p.c[0]:p.c[1];x.globalAlpha=.55+.4*l;x.fill();
    x.fillStyle='rgba(255,255,255,'+(.5*l*(i%3==0))+')';x.fill()}
  x.shadowBlur=0;x.globalAlpha=.95;
  x.beginPath();inner.forEach((q,i)=>i?x.lineTo(q[0],q[1]):x.moveTo(q[0],q[1]));x.closePath();
  const tg=x.createLinearGradient(-r*.5,-r*.5,r*.5,r*.5);tg.addColorStop(0,'rgba(255,255,255,.95)');tg.addColorStop(.5,p.c[0]);tg.addColorStop(1,p.c[1]);x.fillStyle=tg;x.fill();
  x.strokeStyle='rgba(255,255,255,.55)';x.lineWidth=.6;x.stroke();
  const f=Math.pow(Math.max(0,Math.sin(t*.003+p.d*3)),24);
  if(f>.05){x.globalAlpha=f;x.strokeStyle='#fff';x.lineWidth=1.2;x.beginPath();x.moveTo(-r*1.8,0);x.lineTo(r*1.8,0);x.moveTo(0,-r*1.8);x.lineTo(0,r*1.8);x.stroke()}
  x.restore()}
function loop(t){x.clearRect(0,0,W,H);
  for(const p of sand){p.x+=p.v;p.y+=Math.sin(p.x*.02)*.3;if(p.x>W){p.x=-5;p.y=H*(.6+Math.random()*.4)}x.fillStyle='rgba(255,215,150,'+p.a+')';x.fillRect(p.x,p.y,p.v*1.6,1)}
  for(const p of P){p.d+=.01;p.y+=p.s;p.x+=Math.sin(p.d)*(theme==='snow'?.7:.4)+.15;p.rot+=p.vr;if(p.y>H+20||p.x>W+20)Object.assign(p,mk(false));
    if(p.gem)gem(p,t);
    else if(theme==='snow'){x.globalAlpha=.55+.4*p.z;x.fillStyle='#fff';x.shadowColor='#bfe0ff';x.shadowBlur=p.r*2;x.beginPath();x.arc(p.x,p.y,p.r,0,6.283);x.fill();x.shadowBlur=0;x.globalAlpha=1}
    else{const a=.5+.5*Math.sin(t*.004+p.d*5);x.globalAlpha=a;x.shadowColor='#ffd166';x.shadowBlur=8;x.fillStyle='#ffe08a';x.beginPath();x.arc(p.x,p.y,p.r,0,6.283);x.fill();x.shadowBlur=0;x.globalAlpha=1}}
  requestAnimationFrame(loop)}
setTheme(theme);size();requestAnimationFrame(loop);
</script>
</body>
</html>


