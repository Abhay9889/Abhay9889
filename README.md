<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Abhay Singh Yadav — Software Engineer & AI Architect</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;900&family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Exo+2:wght@300;400;600;800&display=swap" rel="stylesheet">
<style>
:root{
  --c:  #00f5ff;
  --p:  #9b30ff;
  --k:  #ff00aa;
  --g:  #ffd700;
  --dk: #020915;
  --bg: rgba(0,18,40,.75);
  --cg: 0 0 12px rgba(0,245,255,.45),0 0 35px rgba(0,245,255,.18);
  --pg: 0 0 12px rgba(155,48,255,.45),0 0 35px rgba(155,48,255,.18);
  --kg: 0 0 12px rgba(255,0,170,.45),0 0 35px rgba(255,0,170,.18);
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{background:var(--dk);color:#c0e0ff;font-family:'Exo 2',sans-serif;overflow-x:hidden;cursor:none}

/* cursor */
#cur{width:10px;height:10px;background:var(--c);border-radius:50%;position:fixed;pointer-events:none;z-index:9999;box-shadow:var(--cg);transform:translate(-50%,-50%)}
#cur-r{width:34px;height:34px;border:1px solid rgba(0,245,255,.45);border-radius:50%;position:fixed;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:all .12s ease}

/* canvas */
#bg-c{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0}
.noise{position:fixed;inset:0;z-index:1;pointer-events:none;opacity:.3;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.05'/%3E%3C/svg%3E")}
.scan{position:fixed;left:0;width:100%;height:2px;background:linear-gradient(90deg,transparent,rgba(0,245,255,.55),transparent);animation:scan 8s linear infinite;z-index:3;pointer-events:none}
@keyframes scan{from{top:-4px}to{top:100vh}}

.wrap{position:relative;z-index:2}

/* ───── NAV ───── */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:1.1rem 3rem;display:flex;justify-content:space-between;align-items:center;backdrop-filter:blur(14px);transition:all .3s}
nav.on{background:rgba(2,9,21,.96);border-bottom:1px solid rgba(0,245,255,.08)}
.logo{font-family:'Orbitron',sans-serif;font-size:1.05rem;font-weight:900;background:linear-gradient(135deg,var(--c),var(--p));-webkit-background-clip:text;-webkit-text-fill-color:transparent;letter-spacing:2px}
.nav-links{display:flex;gap:2rem;list-style:none}
.nav-links a{text-decoration:none;font-family:'Space Mono',monospace;font-size:.68rem;letter-spacing:2px;color:rgba(192,224,255,.55);text-transform:uppercase;transition:color .3s;position:relative}
.nav-links a::after{content:'';position:absolute;bottom:-3px;left:0;right:0;height:1px;background:var(--c);box-shadow:0 0 5px var(--c);transform:scaleX(0);transition:transform .3s}
.nav-links a:hover{color:var(--c)}
.nav-links a:hover::after{transform:scaleX(1)}

/* ───── HERO ───── */
#hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:2rem;position:relative}
.rings{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;pointer-events:none}
.ring{position:absolute;border-radius:50%;border:1px solid rgba(0,245,255,.1)}
.ring:nth-child(1){width:520px;height:520px;animation:spin 22s linear infinite}
.ring:nth-child(2){width:360px;height:360px;border-color:rgba(255,0,170,.08);animation:spin 15s linear infinite reverse}
.ring:nth-child(3){width:210px;height:210px;border-color:rgba(155,48,255,.12);animation:spin 9s linear infinite}
.ring:nth-child(4){width:640px;height:640px;border-color:rgba(0,245,255,.04);animation:spin 35s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}

.avatar{width:130px;height:130px;border-radius:50%;padding:3px;background:linear-gradient(135deg,var(--c),var(--p),var(--k));position:relative;z-index:3;margin-bottom:1.8rem;box-shadow:var(--cg);animation:av 4s ease-in-out infinite}
@keyframes av{0%,100%{box-shadow:var(--cg)}50%{box-shadow:0 0 60px rgba(0,245,255,.7),0 0 120px rgba(155,48,255,.5)}}
.avatar-in{width:100%;height:100%;border-radius:50%;background:#020a1a;display:flex;align-items:center;justify-content:center;font-family:'Orbitron',sans-serif;font-size:2.5rem;font-weight:900;background:linear-gradient(135deg,var(--c),var(--p));-webkit-background-clip:text;-webkit-text-fill-color:transparent}

.h-tag{font-family:'Space Mono',monospace;font-size:.72rem;color:var(--c);letter-spacing:5px;text-transform:uppercase;margin-bottom:.8rem;opacity:.7;position:relative;z-index:3}
.h-name{font-family:'Orbitron',sans-serif;font-size:clamp(2rem,5.5vw,4.8rem);font-weight:900;line-height:1.05;background:linear-gradient(135deg,#fff 15%,var(--c) 50%,var(--p) 85%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;filter:drop-shadow(0 0 22px rgba(0,245,255,.4));position:relative;z-index:3}
.glitch{position:relative}
.glitch::before,.glitch::after{content:attr(data-t);position:absolute;top:0;left:0;width:100%;background:linear-gradient(135deg,#fff 15%,var(--c) 50%,var(--p) 85%);-webkit-background-clip:text;-webkit-text-fill-color:transparent}
.glitch::before{animation:g1 5s infinite;clip-path:polygon(0 0,100% 0,100% 38%,0 38%)}
.glitch::after{animation:g2 5s infinite;clip-path:polygon(0 62%,100% 62%,100% 100%,0 100%)}
@keyframes g1{0%,88%,100%{transform:translate(0,0);opacity:0}90%{transform:translate(-4px,1px);opacity:.6}92%{transform:translate(4px,-1px);opacity:.6}94%{transform:translate(0,0);opacity:0}}
@keyframes g2{0%,90%,100%{transform:translate(0,0);opacity:0}92%{transform:translate(4px,2px);opacity:.6}94%{transform:translate(-4px,-2px);opacity:.6}96%{transform:translate(0,0);opacity:0}}

.h-sub{font-size:1.05rem;font-weight:300;color:rgba(192,224,255,.65);margin:.9rem 0 1.8rem;letter-spacing:2px;position:relative;z-index:3}
.h-sub em{font-style:normal;color:var(--c);font-weight:600}
#typed::after{content:'|';animation:blink 1s infinite;color:var(--c)}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

.btns{display:flex;gap:1rem;flex-wrap:wrap;justify-content:center;position:relative;z-index:3;margin-bottom:2.5rem}
.btn{padding:.72rem 1.8rem;font-family:'Orbitron',sans-serif;font-size:.7rem;font-weight:600;letter-spacing:2px;text-transform:uppercase;border:none;cursor:pointer;border-radius:3px;position:relative;overflow:hidden;transition:all .3s;text-decoration:none;display:inline-block}
.bp{background:linear-gradient(135deg,var(--c),var(--p));color:#020915;box-shadow:0 0 20px rgba(0,245,255,.3)}
.bp:hover{box-shadow:0 0 40px rgba(0,245,255,.7),0 0 80px rgba(0,245,255,.25);transform:translateY(-2px)}
.bg{background:transparent;color:var(--c);border:1px solid rgba(0,245,255,.4)}
.bg:hover{background:rgba(0,245,255,.1);border-color:var(--c);box-shadow:0 0 20px rgba(0,245,255,.3);transform:translateY(-2px)}

/* social badges */
.social-row{display:flex;gap:.6rem;flex-wrap:wrap;justify-content:center;position:relative;z-index:3;margin-bottom:2.5rem}
.soc{display:inline-flex;align-items:center;gap:.4rem;padding:.35rem .9rem;border-radius:3px;font-family:'Space Mono',monospace;font-size:.65rem;text-decoration:none;transition:all .3s;border:1px solid transparent}
.soc:hover{transform:translateY(-2px);filter:brightness(1.2)}
.s-gh {background:#161b22;color:#c0c0c0;border-color:rgba(192,192,192,.3)}
.s-li {background:#0a3250;color:#0077b5;border-color:rgba(0,119,181,.4)}
.s-ig {background:#2d0a18;color:#e4405f;border-color:rgba(228,64,95,.4)}
.s-tw {background:#0d0d0d;color:#aaa;border-color:rgba(180,180,180,.3)}
.s-fb {background:#0a1e36;color:#1877f2;border-color:rgba(24,119,242,.4)}
.s-em {background:#2d0b07;color:#d14836;border-color:rgba(209,72,54,.4)}

.scroll-ind{position:absolute;bottom:2rem;display:flex;flex-direction:column;align-items:center;gap:.4rem;color:rgba(0,245,255,.35);font-size:.65rem;letter-spacing:3px;animation:float 2.5s ease-in-out infinite}
.s-line{width:1px;height:45px;background:linear-gradient(to bottom,var(--c),transparent)}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-6px)}}

/* ───── SECTIONS ───── */
section{padding:5.5rem 2rem;max-width:1200px;margin:0 auto}
.slbl{font-family:'Space Mono',monospace;font-size:.68rem;letter-spacing:5px;color:var(--c);text-transform:uppercase;margin-bottom:.4rem;opacity:.65}
.stitle{font-family:'Orbitron',sans-serif;font-size:clamp(1.7rem,3.8vw,2.8rem);font-weight:900;color:#fff;margin-bottom:2.8rem;position:relative}
.stitle::after{content:'';display:block;width:55px;height:3px;background:linear-gradient(to right,var(--c),var(--p));margin-top:.8rem;border-radius:2px;box-shadow:var(--cg)}

/* reveal */
.rv{opacity:0;transform:translateY(28px);transition:opacity .8s ease,transform .8s ease}
.rv.in{opacity:1;transform:translateY(0)}

/* ───── ABOUT ───── */
.a-grid{display:grid;grid-template-columns:1fr 1fr;gap:3rem;align-items:start}
@media(max-width:768px){.a-grid,.c-grid,.sk-grid{grid-template-columns:1fr}}

.code{background:rgba(0,12,28,.85);border:1px solid rgba(0,245,255,.14);border-radius:8px;padding:1.5rem;font-family:'Space Mono',monospace;font-size:.74rem;line-height:1.9;position:relative;overflow:hidden}
.code::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(to right,var(--c),var(--p),var(--k));box-shadow:0 0 10px var(--c)}
.dots{display:flex;gap:6px;margin-bottom:1rem}
.dots span{width:11px;height:11px;border-radius:50%}
.dots span:nth-child(1){background:#ff5f56}
.dots span:nth-child(2){background:#ffbd2e}
.dots span:nth-child(3){background:#27c93f}
.kw{color:var(--p)}.fn{color:var(--c)}.str{color:#98c379}.cm{color:rgba(192,224,255,.28)}.num{color:var(--g)}.ty{color:#e5c07b}

.about-p{font-size:.95rem;line-height:1.85;color:rgba(192,224,255,.72);margin-bottom:1.4rem}
.about-p strong{color:var(--c)}

.stat-g{display:grid;grid-template-columns:1fr 1fr;gap:.85rem;margin-top:1.8rem}
.sc{background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:8px;padding:1.1rem;text-align:center;position:relative;overflow:hidden;transition:all .3s}
.sc:hover{border-color:rgba(0,245,255,.38);box-shadow:0 0 20px rgba(0,245,255,.12);transform:translateY(-3px)}
.sc::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(to right,transparent,var(--c),transparent)}
.sn{font-family:'Orbitron',sans-serif;font-size:1.7rem;font-weight:900;background:linear-gradient(135deg,var(--c),var(--p));-webkit-background-clip:text;-webkit-text-fill-color:transparent}
.sl{font-size:.65rem;letter-spacing:2px;color:rgba(192,224,255,.45);text-transform:uppercase;margin-top:.2rem}

/* ───── SKILLS ───── */
.sk-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(290px,1fr));gap:1.4rem}
.scat{background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:10px;padding:1.5rem;position:relative;overflow:hidden;transition:transform .35s ease,border-color .3s,box-shadow .3s}
.scat:hover{border-color:rgba(0,245,255,.3);box-shadow:0 10px 40px rgba(0,245,255,.08)}
.scat::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--bar-top,linear-gradient(to right,var(--c),var(--p)));box-shadow:0 0 7px var(--bar-glow,var(--c))}
.scat-name{font-family:'Orbitron',sans-serif;font-size:.72rem;letter-spacing:2px;color:var(--c);margin-bottom:1rem;text-transform:uppercase;display:flex;align-items:center;gap:.5rem}
.bw{margin-bottom:.7rem}
.bl{display:flex;justify-content:space-between;font-size:.78rem;color:rgba(192,224,255,.65);margin-bottom:.28rem}
.bl span:last-child{color:var(--c);font-family:'Space Mono',monospace;font-size:.68rem}
.bt{height:4px;background:rgba(0,245,255,.07);border-radius:2px;overflow:hidden}
.bf{height:100%;border-radius:2px;width:0;transition:width 1.6s cubic-bezier(.25,.46,.45,.94);position:relative}
.bf::after{content:'';position:absolute;right:0;top:-3px;width:9px;height:9px;border-radius:50%;background:inherit;box-shadow:0 0 10px currentColor}

/* tech pills */
.tp-wrap{display:flex;flex-wrap:wrap;gap:.6rem;margin-top:2.5rem}
.tp{padding:.35rem .9rem;background:rgba(0,245,255,.04);border:1px solid rgba(0,245,255,.13);border-radius:20px;font-size:.75rem;color:rgba(192,224,255,.75);font-family:'Space Mono',monospace;transition:all .3s;cursor:default}
.tp:hover{background:rgba(0,245,255,.1);border-color:var(--c);color:var(--c);box-shadow:0 0 12px rgba(0,245,255,.18);transform:translateY(-2px)}

/* ───── WHAT I DO ───── */
.do-grid{display:grid;grid-template-columns:1fr 1fr;gap:1.5rem}
@media(max-width:768px){.do-grid{grid-template-columns:1fr}}
.do-card{background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:10px;padding:1.5rem;position:relative;overflow:hidden;transition:all .35s}
.do-card:hover{border-color:rgba(0,245,255,.28);box-shadow:0 8px 35px rgba(0,245,255,.07);transform:translateY(-3px)}
.do-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--bar-top,linear-gradient(to right,var(--c),var(--p)))}
.do-title{font-family:'Orbitron',sans-serif;font-size:.8rem;color:var(--c);letter-spacing:2px;margin-bottom:1rem;text-transform:uppercase}

/* ───── DSA ───── */
.dsa-g{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:1rem;margin-bottom:2.5rem}
.dc{background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:10px;padding:1.4rem;text-align:center;transition:all .3s;position:relative;overflow:hidden}
.dc:hover{transform:translateY(-4px) scale(1.02);border-color:rgba(0,245,255,.3);box-shadow:0 10px 30px rgba(0,245,255,.1)}
.dc::before{content:'';position:absolute;inset:0;border-radius:10px;background:radial-gradient(circle at 50% 0%,var(--dc-glow,rgba(0,245,255,.04)),transparent 70%)}
.dp{font-family:'Orbitron',sans-serif;font-size:.72rem;letter-spacing:2px;text-transform:uppercase;margin-bottom:.45rem}
.dr{font-family:'Orbitron',sans-serif;font-size:1.7rem;font-weight:900;margin-bottom:.25rem}
.ds{font-size:.65rem;letter-spacing:2px;color:rgba(192,224,255,.4);text-transform:uppercase}

/* ───── PROJECTS ───── */
.proj-g{display:grid;grid-template-columns:repeat(auto-fit,minmax(310px,1fr));gap:1.4rem}
.pc{background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:12px;padding:1.75rem;position:relative;overflow:hidden;transition:all .4s}
.pc:hover{transform:translateY(-6px);border-color:rgba(0,245,255,.33);box-shadow:0 18px 55px rgba(0,245,255,.1)}
.pnum{font-family:'Orbitron',sans-serif;font-size:2.8rem;font-weight:900;color:rgba(0,245,255,.05);position:absolute;top:.8rem;right:1.3rem}
.ptag{font-size:.62rem;letter-spacing:3px;text-transform:uppercase;padding:.22rem .7rem;border-radius:20px;background:rgba(0,245,255,.07);color:var(--c);border:1px solid rgba(0,245,255,.18);display:inline-block;margin-bottom:.9rem}
.pname{font-family:'Orbitron',sans-serif;font-size:1.05rem;font-weight:700;color:#fff;margin-bottom:.65rem}
.pdesc{font-size:.82rem;line-height:1.75;color:rgba(192,224,255,.58);margin-bottom:1.1rem}
.ps{display:flex;flex-wrap:wrap;gap:.35rem}
.st{font-size:.62rem;padding:.18rem .48rem;background:rgba(155,48,255,.08);border:1px solid rgba(155,48,255,.2);border-radius:3px;color:rgba(155,48,255,.88);font-family:'Space Mono',monospace}

/* ───── ACHIEVEMENTS ───── */
.ach-table{width:100%;border-collapse:collapse}
.ach-table th{font-family:'Orbitron',sans-serif;font-size:.65rem;letter-spacing:2px;color:var(--c);text-transform:uppercase;padding:.8rem 1rem;border-bottom:1px solid rgba(0,245,255,.15);text-align:left}
.ach-table td{padding:.85rem 1rem;font-size:.85rem;color:rgba(192,224,255,.75);border-bottom:1px solid rgba(0,245,255,.06);transition:all .3s;vertical-align:middle}
.ach-table tr:hover td{color:#fff;background:rgba(0,245,255,.03)}
.ach-table td:first-child{font-weight:600;color:#fff}
.badge{display:inline-flex;gap:2px;font-size:.9rem}

/* ───── TIMELINE ───── */
.tl{position:relative;padding-left:2rem}
.tl::before{content:'';position:absolute;left:0;top:0;bottom:0;width:1px;background:linear-gradient(to bottom,var(--c),var(--p),transparent);box-shadow:0 0 8px rgba(0,245,255,.3)}
.ti{position:relative;margin-bottom:2rem;padding:1.4rem;background:var(--bg);border:1px solid rgba(0,245,255,.08);border-radius:8px;transition:all .3s}
.ti:hover{border-color:rgba(0,245,255,.25);box-shadow:0 0 20px rgba(0,245,255,.06);transform:translateX(4px)}
.ti::before{content:'';position:absolute;left:-2.5rem;top:1.4rem;width:9px;height:9px;border-radius:50%;background:var(--c);box-shadow:var(--cg)}
.ty{font-family:'Space Mono',monospace;font-size:.67rem;color:var(--c);letter-spacing:2px;margin-bottom:.28rem}
.tt{font-family:'Orbitron',sans-serif;font-size:.95rem;font-weight:700;color:#fff;margin-bottom:.4rem}
.td{font-size:.82rem;line-height:1.7;color:rgba(192,224,255,.58)}

/* ───── CONTACT ───── */
.c-grid{display:grid;grid-template-columns:1fr 1fr;gap:2rem;align-items:start}
.cl-wrap{display:flex;flex-direction:column;gap:.65rem}
.cl{display:flex;align-items:center;gap:1rem;padding:.95rem 1.2rem;background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:8px;text-decoration:none;color:rgba(192,224,255,.8);font-size:.83rem;transition:all .3s;position:relative;overflow:hidden}
.cl::before{content:'';position:absolute;left:0;top:0;bottom:0;width:2px;background:var(--lc,var(--c));box-shadow:0 0 8px var(--lc,var(--c))}
.cl:hover{border-color:rgba(0,245,255,.3);color:var(--c);transform:translateX(5px);box-shadow:0 0 18px rgba(0,245,255,.07)}
.ci{width:34px;height:34px;border-radius:7px;display:flex;align-items:center;justify-content:center;font-size:1rem;background:rgba(0,245,255,.07);flex-shrink:0}
.cln{font-weight:600;color:#fff;font-size:.88rem;margin-bottom:.15rem}
.cls{font-size:.72rem;color:rgba(192,224,255,.42);font-family:'Space Mono',monospace}

.avail-box{background:var(--bg);border:1px solid rgba(0,245,255,.12);border-radius:10px;padding:1.8rem;position:relative;overflow:hidden}
.avail-box::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(to right,transparent,var(--c),transparent)}
.av-head{font-family:'Orbitron',sans-serif;font-size:.9rem;color:var(--c);margin-bottom:1rem;display:flex;align-items:center;gap:.6rem}
.dot{width:8px;height:8px;border-radius:50%;background:#27c93f;box-shadow:0 0 8px #27c93f;animation:pdot 2s ease-in-out infinite;flex-shrink:0}
@keyframes pdot{0%,100%{box-shadow:0 0 4px #27c93f}50%{box-shadow:0 0 14px #27c93f,0 0 4px #27c93f}}
.av-txt{font-size:.84rem;line-height:1.85;color:rgba(192,224,255,.62);margin-bottom:1.3rem}
.ct-wrap{display:flex;flex-wrap:wrap;gap:.45rem}
.ct{padding:.3rem .72rem;background:rgba(155,48,255,.07);border:1px solid rgba(155,48,255,.2);border-radius:4px;font-size:.7rem;color:rgba(155,48,255,.9);font-family:'Space Mono',monospace}

/* footer */
footer{text-align:center;padding:2.8rem 2rem;border-top:1px solid rgba(0,245,255,.07);position:relative}
footer::before{content:'';position:absolute;top:0;left:50%;transform:translateX(-50%);width:180px;height:1px;background:linear-gradient(to right,transparent,var(--c),transparent);box-shadow:0 0 10px var(--c)}
.ft-n{font-family:'Orbitron',sans-serif;font-size:.75rem;letter-spacing:4px;color:rgba(192,224,255,.35);text-transform:uppercase}
.ft-q{font-size:.72rem;color:rgba(0,245,255,.3);margin-top:.5rem;font-family:'Space Mono',monospace}
</style>
</head>
<body>

<div id="cur"></div>
<div id="cur-r"></div>
<canvas id="bg-c"></canvas>
<div class="noise"></div>
<div class="scan"></div>

<nav id="nav">
  <div class="logo">ASY</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#whatido">What I Do</a></li>
    <li><a href="#dsa">DSA</a></li>
    <li><a href="#achievements">Wins</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<div class="wrap">

<!-- ═══ HERO ═══ -->
<section id="hero">
  <div class="rings">
    <div class="ring"></div><div class="ring"></div>
    <div class="ring"></div><div class="ring"></div>
  </div>

  <div class="avatar"><div class="avatar-in">ASY</div></div>

  <p class="h-tag">// Software Engineer &bull; AI Architect &bull; Problem Solver</p>
  <h1 class="h-name glitch" data-t="ABHAY SINGH YADAV">ABHAY SINGH YADAV</h1>
  <p class="h-sub"><em>India 🇮🇳</em> &nbsp;·&nbsp; <span id="typed"></span></p>

  <div class="social-row">
    <a href="https://github.com/Abhay9889" target="_blank" class="soc s-gh">⌥ GitHub</a>
    <a href="https://linkedin.com" target="_blank" class="soc s-li">in LinkedIn</a>
    <a href="https://instagram.com/aditya_50" target="_blank" class="soc s-ig">◈ @aditya_50</a>
    <a href="https://twitter.com" target="_blank" class="soc s-tw">𝕏 Twitter</a>
    <a href="https://facebook.com" target="_blank" class="soc s-fb">f Facebook</a>
    <a href="mailto:your.email@example.com" class="soc s-em">✉ Email</a>
  </div>

  <div class="btns">
    <a href="#whatido" class="btn bp">Explore Work</a>
    <a href="#contact" class="btn bg">Get In Touch</a>
  </div>

  <div class="scroll-ind"><span>SCROLL</span><div class="s-line"></div></div>
</section>

<!-- ═══ ABOUT ═══ -->
<section id="about">
  <div class="rv"><p class="slbl">// 01 — init_sequence</p><h2 class="stitle">About Me</h2></div>
  <div class="a-grid">
    <div class="rv">
      <div class="code">
        <div class="dots"><span></span><span></span><span></span></div>
<pre><span class="kw">public class</span> <span class="fn">AbhaySinghYadav</span> <span class="kw">extends</span> <span class="ty">Developer</span>
    <span class="kw">implements</span> <span class="ty">AI_Engineer</span> {

  <span class="kw">private</span> <span class="ty">String</span> name     = <span class="str">"Abhay Singh Yadav"</span>;
  <span class="kw">private</span> <span class="ty">String</span> location = <span class="str">"India 🇮🇳"</span>;
  <span class="kw">private</span> <span class="ty">String</span> role     = <span class="str">"Software Engineer"</span>
                          + <span class="str">" & AI Researcher"</span>;

  <span class="kw">private</span> <span class="ty">String</span>[] currentFocus = {
    <span class="str">"Building scalable backend systems"</span>,
    <span class="str">"Training cutting-edge neural networks"</span>,
    <span class="str">"Solving complex algorithmic challenges"</span>,
    <span class="str">"Creating intelligent mobile applications"</span>
  };

  <span class="cm">// Languages & Stacks</span>
  Map.of(
    <span class="str">"Languages"</span>, [<span class="str">"Java"</span>,<span class="str">"Python"</span>,<span class="str">"C++"</span>,<span class="str">"Kotlin"</span>,<span class="str">"JS"</span>],
    <span class="str">"Backend"</span>,   [<span class="str">"Spring Boot"</span>,<span class="str">"REST"</span>,<span class="str">"MySQL"</span>],
    <span class="str">"Mobile"</span>,    [<span class="str">"Android"</span>,<span class="str">"MVVM"</span>,<span class="str">"Room DB"</span>],
    <span class="str">"AI/ML"</span>,     [<span class="str">"TensorFlow"</span>,<span class="str">"CNN"</span>,<span class="str">"NLP"</span>]
  )

  <span class="cm">// Mission</span>
  <span class="kw">boolean</span> available = <span class="num">true</span>;
  <span class="kw">boolean</span> learning  = <span class="num">true</span>;
}</pre>
      </div>
    </div>
    <div>
      <div class="rv">
        <p class="about-p">I'm a <strong>passionate Computer Science student</strong> and software engineer from India, dedicated to crafting intelligent, scalable solutions that make a meaningful impact.</p>
        <p class="about-p">My expertise spans <strong>full-stack development</strong>, <strong>artificial intelligence</strong>, and <strong>competitive programming</strong> — bridging traditional software engineering with cutting-edge AI.</p>
        <p class="about-p">With a <strong>strong foundation in Java</strong>, expertise in <strong>Data Structures & Algorithms</strong>, and hands-on experience in <strong>Deep Learning & Computer Vision</strong>, I turn complex problems into elegant, production-ready code.</p>
        <p style="font-family:'Space Mono',monospace;font-size:.78rem;color:rgba(0,245,255,.5);border-left:2px solid var(--c);padding-left:1rem;margin-top:1rem;line-height:1.7">"The best way to predict the future is to invent it."<br><span style="color:rgba(192,224,255,.35);font-size:.7rem">— Alan Kay</span></p>
      </div>
      <div class="stat-g rv">
        <div class="sc"><div class="sn">3+</div><div class="sl">Years Java / Backend</div></div>
        <div class="sc"><div class="sn">2+</div><div class="sl">Years Deep Learning</div></div>
        <div class="sc"><div class="sn">500+</div><div class="sl">DSA Problems Solved</div></div>
        <div class="sc"><div class="sn">5★</div><div class="sl">HackerRank Java</div></div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ SKILLS ═══ -->
<section id="skills">
  <div class="rv"><p class="slbl">// 02 — skill_matrix</p><h2 class="stitle">Tech Stack & Expertise</h2></div>

  <div class="sk-grid">
    <!-- Languages -->
    <div class="scat rv" style="--bar-top:linear-gradient(to right,var(--c),var(--p));--bar-glow:var(--c)">
      <div class="scat-name">💻 Programming Languages</div>
      <div class="bw"><div class="bl"><span>Java</span><span>95%</span></div><div class="bt"><div class="bf" data-w="95" style="background:linear-gradient(to right,var(--c),var(--p))"></div></div></div>
      <div class="bw"><div class="bl"><span>Python</span><span>88%</span></div><div class="bt"><div class="bf" data-w="88" style="background:linear-gradient(to right,var(--c),var(--p))"></div></div></div>
      <div class="bw"><div class="bl"><span>Kotlin</span><span>85%</span></div><div class="bt"><div class="bf" data-w="85" style="background:linear-gradient(to right,var(--c),var(--p))"></div></div></div>
      <div class="bw"><div class="bl"><span>C++ / C</span><span>82%</span></div><div class="bt"><div class="bf" data-w="82" style="background:linear-gradient(to right,var(--c),var(--p))"></div></div></div>
      <div class="bw"><div class="bl"><span>JavaScript</span><span>75%</span></div><div class="bt"><div class="bf" data-w="75" style="background:linear-gradient(to right,var(--c),var(--p))"></div></div></div>
    </div>

    <!-- AI/ML -->
    <div class="scat rv" style="--bar-top:linear-gradient(to right,var(--p),var(--k));--bar-glow:var(--p)">
      <div class="scat-name">🤖 AI / ML & Deep Learning</div>
      <div class="bw"><div class="bl"><span>TensorFlow / Keras</span><span>88%</span></div><div class="bt"><div class="bf" data-w="88" style="background:linear-gradient(to right,var(--p),var(--k))"></div></div></div>
      <div class="bw"><div class="bl"><span>OpenCV (Computer Vision)</span><span>85%</span></div><div class="bt"><div class="bf" data-w="85" style="background:linear-gradient(to right,var(--p),var(--k))"></div></div></div>
      <div class="bw"><div class="bl"><span>CNN / RNN / LSTM</span><span>84%</span></div><div class="bt"><div class="bf" data-w="84" style="background:linear-gradient(to right,var(--p),var(--k))"></div></div></div>
      <div class="bw"><div class="bl"><span>NLP / Transformers</span><span>78%</span></div><div class="bt"><div class="bf" data-w="78" style="background:linear-gradient(to right,var(--p),var(--k))"></div></div></div>
      <div class="bw"><div class="bl"><span>PyTorch</span><span>72%</span></div><div class="bt"><div class="bf" data-w="72" style="background:linear-gradient(to right,var(--p),var(--k))"></div></div></div>
    </div>

    <!-- Backend & Mobile -->
    <div class="scat rv" style="--bar-top:linear-gradient(to right,#ff9500,var(--g));--bar-glow:var(--g)">
      <div class="scat-name">🔧 Backend & Mobile</div>
      <div class="bw"><div class="bl"><span>Spring Boot / REST APIs</span><span>93%</span></div><div class="bt"><div class="bf" data-w="93" style="background:linear-gradient(to right,#ff9500,var(--g))"></div></div></div>
      <div class="bw"><div class="bl"><span>Android (Kotlin / Java)</span><span>88%</span></div><div class="bt"><div class="bf" data-w="88" style="background:linear-gradient(to right,#ff9500,var(--g))"></div></div></div>
      <div class="bw"><div class="bl"><span>MySQL / PostgreSQL</span><span>86%</span></div><div class="bt"><div class="bf" data-w="86" style="background:linear-gradient(to right,#ff9500,var(--g))"></div></div></div>
      <div class="bw"><div class="bl"><span>Microservices / Docker</span><span>80%</span></div><div class="bt"><div class="bf" data-w="80" style="background:linear-gradient(to right,#ff9500,var(--g))"></div></div></div>
      <div class="bw"><div class="bl"><span>MVVM / Clean Architecture</span><span>87%</span></div><div class="bt"><div class="bf" data-w="87" style="background:linear-gradient(to right,#ff9500,var(--g))"></div></div></div>
    </div>
  </div>

  <!-- Full tech cloud from README -->
  <div class="tp-wrap rv">
    <span class="tp">Java</span><span class="tp">Python</span><span class="tp">C++</span><span class="tp">C</span><span class="tp">Kotlin</span><span class="tp">JavaScript</span><span class="tp">HTML</span><span class="tp">CSS</span>
    <span class="tp">TensorFlow</span><span class="tp">PyTorch</span><span class="tp">OpenCV</span><span class="tp">Pandas</span><span class="tp">NumPy</span><span class="tp">Jupyter</span>
    <span class="tp">Spring Boot</span><span class="tp">Hibernate</span><span class="tp">MySQL</span><span class="tp">Redis</span>
    <span class="tp">Android</span><span class="tp">React</span><span class="tp">Node.js</span>
    <span class="tp">Git</span><span class="tp">Docker</span><span class="tp">Linux</span><span class="tp">AWS</span><span class="tp">VS Code</span><span class="tp">IntelliJ IDEA</span><span class="tp">Android Studio</span><span class="tp">Google Colab</span>
  </div>
</section>

<!-- ═══ WHAT I DO ═══ -->
<section id="whatido">
  <div class="rv"><p class="slbl">// 03 — role_spec</p><h2 class="stitle">What I Do</h2></div>
  <div class="do-grid">
    <div class="do-card rv" style="--bar-top:linear-gradient(to right,var(--c),var(--p))">
      <div class="do-title">🎯 Software Engineering</div>
      <div class="code" style="font-size:.7rem">
<pre><span class="cm">Backend Development:</span>
  ├─ <span class="str">Spring Boot microservices</span>
  ├─ <span class="str">RESTful API design</span>
  ├─ <span class="str">MySQL, PostgreSQL</span>
  ├─ <span class="str">JWT, OAuth auth</span>
  └─ <span class="str">Performance optimisation</span>

<span class="cm">Mobile Development:</span>
  ├─ <span class="str">Native Android (Kotlin/Java)</span>
  ├─ <span class="str">Material Design & UI/UX</span>
  ├─ <span class="str">MVVM & Clean Architecture</span>
  ├─ <span class="str">RxJava / Coroutines</span>
  └─ <span class="str">Offline-first apps</span></pre>
      </div>
    </div>
    <div class="do-card rv" style="--bar-top:linear-gradient(to right,var(--p),var(--k))">
      <div class="do-title">🧠 Artificial Intelligence</div>
      <div class="code" style="font-size:.7rem">
<pre><span class="cm">Deep Learning:</span>
  ├─ <span class="str">CNN, RNN, LSTM, GAN</span>
  ├─ <span class="str">Computer Vision & imaging</span>
  ├─ <span class="str">NLP (BERT, Transformers)</span>
  ├─ <span class="str">Transfer learning</span>
  └─ <span class="str">Model deployment (TFLite)</span>

<span class="cm">Machine Learning:</span>
  ├─ <span class="str">Supervised & unsupervised</span>
  ├─ <span class="str">Feature engineering</span>
  ├─ <span class="str">Hyperparameter tuning</span>
  ├─ <span class="str">Model eval & validation</span>
  └─ <span class="str">EDA & data analysis</span></pre>
      </div>
    </div>
  </div>
</section>

<!-- ═══ DSA ═══ -->
<section id="dsa">
  <div class="rv"><p class="slbl">// 04 — algo_bench</p><h2 class="stitle">Competitive Programming</h2></div>

  <div class="dsa-g rv">
    <div class="dc" style="--dc-glow:rgba(255,215,0,.06)">
      <div class="dp" style="color:var(--g)">LeetCode</div>
      <div class="dr" style="color:var(--g)">300+</div>
      <div class="ds">Problems · Guardian ⭐⭐⭐</div>
    </div>
    <div class="dc" style="--dc-glow:rgba(0,245,255,.06)">
      <div class="dp" style="color:var(--c)">HackerRank</div>
      <div class="dr" style="color:var(--c)">5★</div>
      <div class="ds">Java · Gold ⚡</div>
    </div>
    <div class="dc" style="--dc-glow:rgba(255,0,170,.06)">
      <div class="dp" style="color:var(--k)">CodeChef</div>
      <div class="dr" style="color:var(--k)">3★</div>
      <div class="ds">150+ Problems 🏆</div>
    </div>
    <div class="dc" style="--dc-glow:rgba(155,48,255,.06)">
      <div class="dp" style="color:var(--p)">Codeforces</div>
      <div class="dr" style="color:var(--p)">Spec.</div>
      <div class="ds">Specialist 100+ 🎯</div>
    </div>
  </div>

  <!-- DSA proficiency from README table -->
  <div class="sk-grid rv">
    <div class="scat" style="--bar-top:linear-gradient(to right,var(--g),#ff9500);--bar-glow:var(--g)">
      <div class="scat-name">🏗️ DSA Proficiency</div>
      <div class="bw"><div class="bl"><span>Arrays &amp; Strings</span><span>95%</span></div><div class="bt"><div class="bf" data-w="95" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Stacks &amp; Queues</span><span>93%</span></div><div class="bt"><div class="bf" data-w="93" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Sorting &amp; Searching</span><span>92%</span></div><div class="bt"><div class="bf" data-w="92" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Linked Lists</span><span>90%</span></div><div class="bt"><div class="bf" data-w="90" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Trees &amp; Graphs</span><span>88%</span></div><div class="bt"><div class="bf" data-w="88" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Recursion &amp; Backtracking</span><span>87%</span></div><div class="bt"><div class="bf" data-w="87" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Dynamic Programming</span><span>85%</span></div><div class="bt"><div class="bf" data-w="85" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
      <div class="bw"><div class="bl"><span>Bit Manipulation</span><span>80%</span></div><div class="bt"><div class="bf" data-w="80" style="background:linear-gradient(to right,var(--g),#ff9500)"></div></div></div>
    </div>

    <div class="scat" style="--bar-top:linear-gradient(to right,var(--p),var(--k));--bar-glow:var(--p)">
      <div class="scat-name">🔬 AI Research Areas</div>
      <div class="code" style="font-size:.7rem;margin-top:.5rem">
<pre><span class="cm">Computer Vision:</span>
  <span class="str">CNN · YOLO · ResNet · MobileNet</span>
  <span class="kw">→</span> Image classification
  <span class="kw">→</span> Object detection
  <span class="kw">→</span> Face recognition

<span class="cm">NLP:</span>
  <span class="str">RNN · LSTM · BERT · Transformers</span>
  <span class="kw">→</span> Text classification
  <span class="kw">→</span> Sentiment analysis
  <span class="kw">→</span> Named entity recognition

<span class="cm">Deployment:</span>
  <span class="str">TFLite · ONNX · Docker · Flask</span></pre>
      </div>
    </div>
  </div>
</section>

<!-- ═══ ACHIEVEMENTS ═══ -->
<section id="achievements">
  <div class="rv"><p class="slbl">// 05 — achievement_log</p><h2 class="stitle">Achievements & Certifications</h2></div>

  <div style="background:var(--bg);border:1px solid rgba(0,245,255,.1);border-radius:10px;overflow:hidden" class="rv">
    <table class="ach-table">
      <thead>
        <tr>
          <th>Achievement</th>
          <th>Year</th>
          <th>Badge</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>5★ Java — HackerRank</td><td style="font-family:'Space Mono',monospace;font-size:.75rem;color:var(--c)">2024</td><td><span class="badge">⭐⭐⭐⭐⭐</span></td></tr>
        <tr><td>3★ Rating — CodeChef</td><td style="font-family:'Space Mono',monospace;font-size:.75rem;color:var(--c)">2024</td><td><span class="badge">🏆</span></td></tr>
        <tr><td>Top Contributor — Open Source</td><td style="font-family:'Space Mono',monospace;font-size:.75rem;color:var(--c)">2024</td><td><span class="badge">🌟</span></td></tr>
        <tr><td>300+ Problems — LeetCode</td><td style="font-family:'Space Mono',monospace;font-size:.75rem;color:var(--c)">2024</td><td><span class="badge">💻</span></td></tr>
        <tr><td>Deep Learning Specialization</td><td style="font-family:'Space Mono',monospace;font-size:.75rem;color:var(--c)">2023</td><td><span class="badge">🎓</span></td></tr>
        <tr><td>Android Developer Certification</td><td style="font-family:'Space Mono',monospace;font-size:.75rem;color:var(--c)">2023</td><td><span class="badge">📱</span></td></tr>
      </tbody>
    </table>
  </div>

  <!-- Quick Stats from README -->
  <div style="margin-top:3rem">
    <div class="rv">
      <div class="code">
        <div class="dots"><span></span><span></span><span></span></div>
<pre><span class="kw">const</span> <span class="fn">abhayStats</span> = {
  name:     <span class="str">"Abhay Singh Yadav"</span>,
  role:     <span class="str">"Software Engineer & AI Researcher"</span>,
  location: <span class="str">"India 🇮🇳"</span>,
  experience: {
    backend: <span class="str">"3+ years with Java & Spring Boot"</span>,
    mobile:  <span class="str">"2+ years Android development"</span>,
    ai_ml:   <span class="str">"2+ years Deep Learning & CV"</span>,
    dsa:     <span class="str">"500+ problems across platforms"</span>
  },
  currentlyLearning: [
    <span class="str">"Advanced System Design"</span>,
    <span class="str">"Distributed Systems"</span>,
    <span class="str">"Large Language Models (LLMs)"</span>,
    <span class="str">"Cloud Architecture (AWS/Azure)"</span>
  ],
  hobbies: [<span class="str">"☕ Coffee"</span>, <span class="str">"📚 Tech blogs"</span>,
            <span class="str">"♟ Chess"</span>, <span class="str">"🏃 Fitness"</span>],
  funFact: <span class="str">"I debug code faster with good coffee ☕"</span>,
  motto:   <span class="str">"Code with passion, build with purpose 🚀"</span>
};</pre>
      </div>
    </div>
  </div>
</section>

<!-- ═══ CONTACT ═══ -->
<section id="contact">
  <div class="rv"><p class="slbl">// 06 — handshake</p><h2 class="stitle">Let's Connect</h2></div>
  <div class="c-grid">
    <div class="cl-wrap rv">
      <a href="https://github.com/Abhay9889" target="_blank" class="cl" style="--lc:#c0c0c0">
        <div class="ci">⌥</div>
        <div><div class="cln">GitHub</div><div class="cls">github.com/Abhay9889</div></div>
      </a>
      <a href="https://linkedin.com" target="_blank" class="cl" style="--lc:#0077b5">
        <div class="ci" style="color:#0077b5">in</div>
        <div><div class="cln">LinkedIn</div><div class="cls">Connect professionally</div></div>
      </a>
      <a href="https://instagram.com/aditya_50" target="_blank" class="cl" style="--lc:#e4405f">
        <div class="ci" style="color:#e4405f">◈</div>
        <div><div class="cln">Instagram</div><div class="cls">@aditya_50</div></div>
      </a>
      <a href="https://twitter.com" target="_blank" class="cl" style="--lc:#888">
        <div class="ci">𝕏</div>
        <div><div class="cln">Twitter / X</div><div class="cls">Follow for updates</div></div>
      </a>
      <a href="https://facebook.com" target="_blank" class="cl" style="--lc:#1877f2">
        <div class="ci" style="color:#1877f2">f</div>
        <div><div class="cln">Facebook</div><div class="cls">Connect on Facebook</div></div>
      </a>
      <a href="mailto:your.email@example.com" class="cl" style="--lc:var(--c)">
        <div class="ci">✉</div>
        <div><div class="cln">Email</div><div class="cls">your.email@example.com</div></div>
      </a>
    </div>

    <div class="avail-box rv">
      <div class="av-head"><div class="dot"></div>Open for Collaboration</div>
      <p class="av-txt">Currently open to collaborations on AI/ML projects, open source contributions, backend systems, mobile applications, and research papers. Always excited about challenging engineering problems.</p>
      <div class="ct-wrap">
        <span class="ct">AI/ML Projects</span>
        <span class="ct">Open Source</span>
        <span class="ct">Backend Systems</span>
        <span class="ct">Mobile Apps</span>
        <span class="ct">Research Papers</span>
        <span class="ct">System Design</span>
        <span class="ct">LLM Engineering</span>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="ft-n">Abhay Singh Yadav &nbsp;·&nbsp; India 🇮🇳</div>
  <p class="ft-q">// Code with passion, build with purpose 🚀</p>
</footer>

</div><!-- .wrap -->

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script>
// ── CUSTOM CURSOR ──
const cur = document.getElementById('cur');
const curR = document.getElementById('cur-r');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX; my=e.clientY;
  cur.style.left=mx+'px'; cur.style.top=my+'px';
});
(function animR(){
  rx+=(mx-rx)*.11; ry+=(my-ry)*.11;
  curR.style.left=rx+'px'; curR.style.top=ry+'px';
  requestAnimationFrame(animR);
})();
document.querySelectorAll('a,button,.tp,.sc,.dc,.pc').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cur.style.transform='translate(-50%,-50%) scale(2.5)';curR.style.transform='translate(-50%,-50%) scale(1.6)'});
  el.addEventListener('mouseleave',()=>{cur.style.transform='translate(-50%,-50%) scale(1)';curR.style.transform='translate(-50%,-50%) scale(1)'});
});

// ── THREE.JS BACKGROUND ──
const canvas=document.getElementById('bg-c');
const renderer=new THREE.WebGLRenderer({canvas,antialias:true,alpha:false});
renderer.setSize(window.innerWidth,window.innerHeight);
renderer.setClearColor(0x020915,1);
renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));

const scene=new THREE.Scene();
const cam=new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,.1,1000);
cam.position.z=30;

// Particle field
const N=5000;
const geo=new THREE.BufferGeometry();
const pos=new Float32Array(N*3),col=new Float32Array(N*3);
for(let i=0;i<N;i++){
  pos[i*3]=(Math.random()-.5)*130;
  pos[i*3+1]=(Math.random()-.5)*90;
  pos[i*3+2]=(Math.random()-.5)*90;
  const t=Math.random();
  if(t<.45){col[i*3]=0;col[i*3+1]=.96;col[i*3+2]=1}
  else if(t<.75){col[i*3]=.61;col[i*3+1]=.19;col[i*3+2]=1}
  else if(t<.9){col[i*3]=1;col[i*3+1]=0;col[i*3+2]=.67}
  else{col[i*3]=1;col[i*3+1]=.84;col[i*3+2]=0}
}
geo.setAttribute('position',new THREE.BufferAttribute(pos,3));
geo.setAttribute('color',new THREE.BufferAttribute(col,3));
const mat=new THREE.PointsMaterial({size:.14,vertexColors:true,transparent:true,opacity:.7,sizeAttenuation:true,blending:THREE.AdditiveBlending});
const pts=new THREE.Points(geo,mat);
scene.add(pts);

// Grid
const gv=[];const gs=70,st=6,gn=gs/st;
for(let i=-gn;i<=gn;i++){
  gv.push(-gs,0,i*st,gs,0,i*st);
  gv.push(i*st,0,-gs,i*st,0,gs);
}
const gg=new THREE.BufferGeometry();
gg.setAttribute('position',new THREE.Float32BufferAttribute(gv,3));
const gm=new THREE.LineBasicMaterial({color:0x001a33,transparent:true,opacity:.25});
const grid=new THREE.LineSegments(gg,gm);
grid.position.y=-22; grid.rotation.x=Math.PI/14;
scene.add(grid);

// Wireframe shapes
function wf(g,x,y,z,c=0x00f5ff){
  const m=new THREE.Mesh(g,new THREE.MeshBasicMaterial({color:c,wireframe:true,transparent:true,opacity:.07}));
  m.position.set(x,y,z); scene.add(m); return m;
}
const shapes=[
  {m:wf(new THREE.IcosahedronGeometry(4,0),-16,6,-12),rx:.003,ry:.005},
  {m:wf(new THREE.OctahedronGeometry(3,0),19,-4,-16,0x9b30ff),rx:-.004,ry:.003},
  {m:wf(new THREE.TetrahedronGeometry(2.5,0),6,9,-22,0xff00aa),rx:.005,ry:-.004},
  {m:wf(new THREE.TorusGeometry(3,.8,8,16),-21,-9,-14,0xffd700),rx:.002,ry:.006},
  {m:wf(new THREE.DodecahedronGeometry(2.5,0),12,10,-18),rx:.004,ry:.003},
];

let pmx=0,pmy=0;
document.addEventListener('mousemove',e=>{pmx=(e.clientX/window.innerWidth-.5)*2;pmy=(e.clientY/window.innerHeight-.5)*2});

let t=0;
(function anim(){
  requestAnimationFrame(anim);
  t+=.004;
  pts.rotation.y=t*.035; pts.rotation.x=t*.012;
  cam.position.x+=(pmx*3-cam.position.x)*.018;
  cam.position.y+=(-pmy*2-cam.position.y)*.018;
  cam.lookAt(0,0,0);
  shapes.forEach(s=>{s.m.rotation.x+=s.rx;s.m.rotation.y+=s.ry});
  grid.position.y=-22+Math.sin(t)*.4;
  renderer.render(scene,cam);
})();

window.addEventListener('resize',()=>{
  renderer.setSize(window.innerWidth,window.innerHeight);
  cam.aspect=window.innerWidth/window.innerHeight;
  cam.updateProjectionMatrix();
});

// ── TYPING ANIMATION ──
const phrases=['Full Stack Developer 🚀','Deep Learning Engineer 🧠','Competitive Programmer 🏆','Android Developer 📱','AI Researcher 🤖','Building Intelligent Systems ⚡'];
let pi=0,ci=0,del=false;
const tEl=document.getElementById('typed');
function typeLoop(){
  const c=phrases[pi];
  if(!del){tEl.textContent=c.slice(0,ci++);if(ci>c.length){del=true;setTimeout(typeLoop,1900);return}}
  else{tEl.textContent=c.slice(0,ci--);if(ci<0){del=false;pi=(pi+1)%phrases.length;ci=0}}
  setTimeout(typeLoop,del?55:85);
}
typeLoop();

// ── SCROLL REVEAL ──
const rvEls=document.querySelectorAll('.rv');
const ro=new IntersectionObserver(entries=>{
  entries.forEach((e,i)=>{if(e.isIntersecting)setTimeout(()=>e.target.classList.add('in'),i*80)});
},{threshold:.1,rootMargin:'0px 0px -40px 0px'});
rvEls.forEach(el=>ro.observe(el));

// ── SKILL BARS ──
const bo=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting)e.target.querySelectorAll('.bf').forEach(b=>{b.style.width=b.dataset.w+'%'});
  });
},{threshold:.25});
document.querySelectorAll('.scat').forEach(el=>bo.observe(el));

// ── NAV ──
window.addEventListener('scroll',()=>document.getElementById('nav').classList.toggle('on',scrollY>50));

// ── 3D CARD TILT ──
document.querySelectorAll('.pc,.scat,.do-card,.dc').forEach(c=>{
  c.addEventListener('mousemove',e=>{
    const r=c.getBoundingClientRect();
    const x=e.clientX-r.left,y=e.clientY-r.top;
    const cx=r.width/2,cy=r.height/2;
    c.style.transform=`perspective(700px) rotateX(${((y-cy)/cy)*-7}deg) rotateY(${((x-cx)/cx)*7}deg) translateY(-4px)`;
    c.style.transition='transform .1s ease';
  });
  c.addEventListener('mouseleave',()=>{c.style.transform='';c.style.transition='all .4s ease'});
});
</script>
</body>
</html>
