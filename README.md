<html lang="ku" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
/* ══════════════════════════════════════
   RESET & TOKENS
══════════════════════════════════════ */
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --red:#e50914;--red2:#ff2d3a;--gold:#f5c518;
  --bg:#070709;--bg2:#0f0f12;--card:#13131a;--card2:#1a1a24;
  --txt:#f0f0f8;--txt2:#8888aa;--txt3:#44445a;
  --border:rgba(255,255,255,0.06);
  --glass:rgba(255,255,255,0.04);
  --r:14px;
  --nav-h:62px;
}
html{scroll-behavior:smooth}
body{font-family:'Cairo',sans-serif;background:var(--bg);color:var(--txt);overflow-x:hidden;min-height:100vh}

/* scrollbar */
::-webkit-scrollbar{width:4px;height:4px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--red);border-radius:2px}

/* ══════════════════════════════════════
   NAVBAR
══════════════════════════════════════ */
.nav{
  position:fixed;top:0;left:0;right:0;z-index:900;
  height:var(--nav-h);
  display:flex;align-items:center;justify-content:space-between;
  padding:0 20px;
  transition:all .35s;
}
.nav.solid{
  background:rgba(7,7,9,.96);
  backdrop-filter:blur(24px);
  border-bottom:1px solid var(--border);
  box-shadow:0 4px 32px rgba(0,0,0,.5);
}
.nav-brand{
  font-family:'Bebas Neue',sans-serif;
  font-size:1.55em;letter-spacing:4px;
  background:linear-gradient(135deg,#fff 20%,var(--red) 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  cursor:pointer;user-select:none;
  filter:drop-shadow(0 0 18px rgba(229,9,20,.35));
}
.nav-links{display:flex;gap:22px;list-style:none}
.nav-links a{
  color:var(--txt3);font-size:.82em;font-weight:700;
  cursor:pointer;transition:color .2s;text-decoration:none;
  letter-spacing:.5px;
}
.nav-links a:hover{color:var(--txt)}
.nav-right{display:flex;align-items:center;gap:8px}
.nav-btn{
  background:var(--glass);border:1px solid var(--border);
  color:var(--txt2);border-radius:30px;
  padding:6px 14px;font-size:.78em;font-weight:700;
  cursor:pointer;font-family:'Cairo',sans-serif;
  transition:all .2s;display:flex;align-items:center;gap:6px;
}
.nav-btn:hover{background:var(--red);color:#fff;border-color:var(--red)}
@media(max-width:640px){
  .nav-links{display:none}
  .nav{padding:0 14px}
}

/* ══════════════════════════════════════
   HERO — CINEMATIC FULL-SCREEN
══════════════════════════════════════ */
.hero{
  position:relative;
  height:100svh;min-height:600px;
  overflow:hidden;
  display:flex;flex-direction:column;
}

/* bg image with ken burns */
.hero-bg{
  position:absolute;inset:-10px;z-index:0;
  background-size:cover;background-position:center 20%;
  animation:kbZoom 22s ease-in-out infinite alternate;
  filter:brightness(.55) saturate(1.1);
  transition:background-image 1.2s ease;
}
@keyframes kbZoom{
  from{transform:scale(1) translateX(0)}
  to{transform:scale(1.1) translateX(-1%)}
}

/* layered cinematic overlays */
.hero-overlay-left{
  position:absolute;inset:0;z-index:1;
  background:linear-gradient(100deg,
    rgba(7,7,9,.98) 0%,
    rgba(7,7,9,.85) 35%,
    rgba(7,7,9,.3) 65%,
    transparent 100%);
}
.hero-overlay-bottom{
  position:absolute;inset:0;z-index:1;
  background:linear-gradient(to top,
    rgba(7,7,9,1) 0%,
    rgba(7,7,9,.6) 18%,
    transparent 45%);
}
.hero-overlay-top{
  position:absolute;top:0;left:0;right:0;z-index:1;
  height:140px;
  background:linear-gradient(to bottom,rgba(7,7,9,.7) 0%,transparent 100%);
}
/* red glow from left */
.hero-glow{
  position:absolute;z-index:1;
  top:30%;left:-10%;
  width:55%;height:60%;
  background:radial-gradient(ellipse,rgba(229,9,20,.12) 0%,transparent 65%);
  pointer-events:none;
}

/* poster on right */
.hero-poster-wrap{
  position:absolute;
  top:0;right:0;bottom:0;
  width:48%;z-index:2;
  display:flex;align-items:center;justify-content:center;
  padding-top:var(--nav-h);
  pointer-events:none;
}
@media(max-width:700px){.hero-poster-wrap{display:none}}
.hero-poster{
  height:72%;max-height:490px;width:auto;
  border-radius:12px;
  box-shadow:
    0 0 0 1px rgba(255,255,255,.07),
    0 24px 80px rgba(0,0,0,.95),
    0 0 80px rgba(229,9,20,.2),
    -20px 0 60px rgba(7,7,9,.9);
  animation:posterFloat 1.4s cubic-bezier(.22,1,.36,1) .1s both;
  pointer-events:all;cursor:pointer;
  transition:transform .4s,box-shadow .4s;
}
.hero-poster:hover{
  transform:scale(1.03) translateY(-4px);
  box-shadow:0 0 0 1px rgba(229,9,20,.3),0 32px 90px rgba(0,0,0,.95),0 0 100px rgba(229,9,20,.3);
}
@keyframes posterFloat{
  from{opacity:0;transform:translateY(36px) scale(.93)}
  to{opacity:1;transform:translateY(0) scale(1)}
}

/* left content */
.hero-content{
  position:relative;z-index:3;
  flex:1;display:flex;flex-direction:column;justify-content:center;
  padding:var(--nav-h) 24px 0;
  max-width:min(560px, 58%);
}
@media(max-width:700px){.hero-content{max-width:100%;padding:calc(var(--nav-h) + 12px) 18px 0}}

.hero-eyebrow{
  display:flex;align-items:center;gap:10px;
  font-size:.7em;font-weight:800;letter-spacing:3.5px;
  color:var(--red);text-transform:uppercase;
  margin-bottom:14px;
  animation:fadeUp .7s ease both;
}
.hero-eyebrow::before{
  content:'';display:block;
  width:28px;height:2px;border-radius:1px;
  background:var(--red);
  box-shadow:0 0 10px var(--red);
  flex-shrink:0;
}

/* brand */
.hero-brand{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(2.6em,7.5vw,5.2em);
  letter-spacing:5px;line-height:.88;
  color:#fff;
  text-shadow:0 0 60px rgba(229,9,20,.2),0 4px 30px rgba(0,0,0,.9);
  margin-bottom:4px;
  animation:fadeUp .75s ease .05s both;
}
.hero-brand em{
  font-style:normal;
  background:linear-gradient(135deg,var(--red),#ff6b35);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.hero-rule{
  width:0;height:3px;
  background:linear-gradient(90deg,var(--red),transparent);
  border-radius:2px;margin:16px 0;
  box-shadow:0 0 16px rgba(229,9,20,.7);
  animation:ruleGrow .9s ease .2s both;
}
@keyframes ruleGrow{from{width:0;opacity:0}to{width:52px;opacity:1}}
.hero-tagline{
  font-size:.88em;font-weight:400;
  color:rgba(255,255,255,.45);letter-spacing:.08em;
  margin-bottom:30px;
  animation:fadeUp .8s ease .25s both;
}

/* featured film block */
.hero-film-eyebrow{
  font-size:.65em;font-weight:800;letter-spacing:2.5px;
  color:rgba(255,255,255,.35);text-transform:uppercase;
  margin-bottom:5px;
  animation:fadeUp .8s ease .3s both;
}
.hero-film-title{
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(1.7em,4.5vw,2.8em);
  letter-spacing:2px;color:#fff;line-height:1;
  margin-bottom:10px;
  text-shadow:0 2px 20px rgba(0,0,0,.9);
  animation:fadeUp .8s ease .32s both;
}
.hero-chips{
  display:flex;gap:7px;flex-wrap:wrap;
  margin-bottom:26px;
  animation:fadeUp .8s ease .38s both;
}
.chip{
  font-size:.7em;font-weight:700;padding:5px 13px;border-radius:30px;
  border:1px solid rgba(255,255,255,.12);
  background:rgba(255,255,255,.06);
  color:rgba(255,255,255,.7);
  backdrop-filter:blur(6px);
  letter-spacing:.5px;
}
.chip.red{background:rgba(229,9,20,.18);border-color:rgba(229,9,20,.35);color:#ff6b6b}
.chip.gold{background:rgba(245,197,24,.12);border-color:rgba(245,197,24,.3);color:var(--gold)}
.hero-btns{display:flex;gap:10px;flex-wrap:wrap;animation:fadeUp .8s ease .44s both}

/* buttons */
.btn-red{
  display:inline-flex;align-items:center;gap:9px;
  background:var(--red);color:#fff;border:none;
  border-radius:9px;padding:13px 26px;
  font-size:.9em;font-weight:800;cursor:pointer;
  font-family:'Cairo',sans-serif;
  transition:all .22s;letter-spacing:.3px;
  box-shadow:0 4px 22px rgba(229,9,20,.45);
}
.btn-red:hover{background:var(--red2);transform:translateY(-2px);box-shadow:0 8px 32px rgba(229,9,20,.6)}
.btn-glass{
  display:inline-flex;align-items:center;gap:9px;
  background:rgba(255,255,255,.08);
  backdrop-filter:blur(8px);
  color:#fff;border:1px solid rgba(255,255,255,.18);
  border-radius:9px;padding:13px 22px;
  font-size:.9em;font-weight:700;cursor:pointer;
  font-family:'Cairo',sans-serif;transition:all .22s;
  text-decoration:none;
}
.btn-glass:hover{background:rgba(255,255,255,.16)}

/* strip */
.hero-strip{
  position:relative;z-index:3;
  display:grid;grid-template-columns:repeat(4,1fr);
  border-top:1px solid rgba(229,9,20,.25);
  background:rgba(7,7,9,.5);
  backdrop-filter:blur(12px);
}
.strip-card{
  position:relative;height:120px;overflow:hidden;cursor:pointer;
  border-right:1px solid rgba(229,9,20,.15);
}
.strip-card:last-child{border-right:none}
.strip-bg{
  position:absolute;inset:-4px;
  background-size:cover;background-position:center;
  transition:transform .55s,filter .55s;
  filter:brightness(.5) saturate(.9);
}
.strip-card:hover .strip-bg{transform:scale(1.1);filter:brightness(.65) saturate(1.2)}
.strip-veil{
  position:absolute;inset:0;
  background:linear-gradient(to top,rgba(0,0,0,.88) 0%,transparent 55%);
  transition:background .3s;
}
.strip-card:hover .strip-veil{background:linear-gradient(to top,rgba(229,9,20,.65) 0%,rgba(0,0,0,.1) 60%,transparent 100%)}
.strip-info{position:absolute;bottom:9px;left:11px;right:11px;z-index:2}
.strip-title{
  font-family:'Bebas Neue',sans-serif;font-size:.97em;
  letter-spacing:1.5px;color:#fff;line-height:1;
  text-shadow:0 2px 10px rgba(0,0,0,.9);
}
.strip-meta{font-size:.65em;color:rgba(255,255,255,.55);margin-top:2px}
.strip-gold{color:var(--gold);font-weight:700}
@media(max-width:500px){
  .strip-card{height:90px}
  .strip-title{font-size:.8em}
}

@keyframes fadeUp{from{opacity:0;transform:translateY(18px)}to{opacity:1;transform:translateY(0)}}

/* ══════════════════════════════════════
   MAIN CONTAINER
══════════════════════════════════════ */
.main{padding:0 14px 100px;max-width:1240px;margin:0 auto}
@media(min-width:768px){.main{padding:0 28px 100px}}

/* ══════════════════════════════════════
   SEARCH
══════════════════════════════════════ */
.search-wrap{margin:28px 0 0}
.sbox{
  display:flex;align-items:center;
  background:var(--card);
  border:1px solid var(--border);
  border-radius:13px;
  padding:5px 5px 5px 16px;
  transition:border-color .22s,box-shadow .22s;
}
.sbox:focus-within{
  border-color:var(--red);
  box-shadow:0 0 0 3px rgba(229,9,20,.13),0 4px 24px rgba(0,0,0,.4);
}
.sbox i{color:var(--txt3);font-size:.88em;margin-left:8px}
.sinput{
  flex:1;background:transparent;border:none;outline:none;
  color:var(--txt);font-size:.93em;
  font-family:'Cairo',sans-serif;padding:9px 0;
}
.sinput::placeholder{color:var(--txt3)}
.sbtn{
  background:var(--red);border:none;border-radius:10px;
  padding:10px 20px;color:#fff;cursor:pointer;
  font-size:.83em;font-weight:800;
  font-family:'Cairo',sans-serif;transition:background .2s;
  white-space:nowrap;letter-spacing:.3px;
}
.sbtn:hover{background:var(--red2)}

/* ══════════════════════════════════════
   TABS
══════════════════════════════════════ */
.tabs{
  display:flex;gap:5px;margin:20px 0 16px;
  overflow-x:auto;padding-bottom:2px;
}
.tabs::-webkit-scrollbar{height:0}
.tab{
  flex-shrink:0;background:none;
  border:1px solid var(--border);
  color:var(--txt3);font-size:.78em;font-weight:700;
  padding:7px 16px;cursor:pointer;border-radius:30px;
  transition:all .2s;font-family:'Cairo',sans-serif;
  letter-spacing:.4px;
}
.tab.on{background:var(--red);color:#fff;border-color:var(--red);box-shadow:0 3px 16px rgba(229,9,20,.4)}
.tab:hover:not(.on){background:var(--glass);color:var(--txt);border-color:rgba(255,255,255,.12)}

/* ══════════════════════════════════════
   SECTION HEADER
══════════════════════════════════════ */
.sec-hd{
  display:flex;align-items:center;gap:9px;
  font-size:1em;font-weight:800;
  margin-bottom:14px;color:var(--txt);
  letter-spacing:.3px;
}
.sec-hd .cnt{color:var(--red);font-size:.8em}
.sec-hd .line{flex:1;height:1px;background:var(--border)}

/* ══════════════════════════════════════
   FAVORITES
══════════════════════════════════════ */
.fav-sec{margin-bottom:36px}
.fav-empty{
  background:var(--card);border:1px dashed rgba(255,255,255,.06);
  border-radius:var(--r);padding:28px 16px;
  text-align:center;color:var(--txt3);font-size:.84em;
}
.fav-empty i{display:block;font-size:1.8em;margin-bottom:8px;color:var(--red);opacity:.35}
.fav-row{display:flex;gap:10px;overflow-x:auto;padding-bottom:8px}
.fav-row::-webkit-scrollbar{height:3px}
.fav-row::-webkit-scrollbar-thumb{background:var(--red)}
.fav-mini{
  flex-shrink:0;width:100px;border-radius:9px;overflow:hidden;
  background:var(--card);cursor:pointer;position:relative;
  transition:transform .22s;border:1px solid var(--border);
}
.fav-mini:hover{transform:scale(1.06) translateY(-3px)}
.fav-mini img{width:100%;height:138px;object-fit:cover;display:block;background:var(--card2)}
.fav-rm{
  position:absolute;top:5px;left:5px;
  background:rgba(229,9,20,.88);border:none;
  width:22px;height:22px;border-radius:50%;color:#fff;
  font-size:.6em;cursor:pointer;display:flex;align-items:center;justify-content:center;
  transition:transform .2s;
}
.fav-rm:hover{transform:scale(1.15)}
.fav-name{padding:6px 7px;font-size:.68em;font-weight:700;color:var(--txt);line-height:1.2}

/* ══════════════════════════════════════
   MOVIE GRID
══════════════════════════════════════ */
.grid{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:11px;margin-bottom:22px;
}
@media(min-width:460px){.grid{grid-template-columns:repeat(3,1fr)}}
@media(min-width:700px){.grid{grid-template-columns:repeat(4,1fr);gap:14px}}
@media(min-width:1000px){.grid{grid-template-columns:repeat(5,1fr)}}
@media(min-width:1200px){.grid{grid-template-columns:repeat(6,1fr)}}

.mcard{
  background:var(--card);border-radius:var(--r);overflow:hidden;
  cursor:pointer;position:relative;
  border:1px solid var(--border);
  transition:transform .25s cubic-bezier(.22,1,.36,1),box-shadow .25s;
}
.mcard:hover{
  transform:translateY(-6px) scale(1.025);
  box-shadow:0 18px 50px rgba(0,0,0,.7),0 0 0 1px rgba(229,9,20,.22);
  z-index:2;border-color:rgba(229,9,20,.2);
}
.mcard-img{
  width:100%;aspect-ratio:2/3;object-fit:cover;
  display:block;background:var(--card2);
  transition:filter .3s;
}
.mcard:hover .mcard-img{filter:brightness(1.05)}

/* hover glass overlay */
.mcard-veil{
  position:absolute;inset:0;
  background:linear-gradient(to top,rgba(0,0,0,.95) 0%,transparent 55%);
  opacity:0;transition:opacity .25s;
  display:flex;flex-direction:column;justify-content:flex-end;
  padding:13px;
}
.mcard:hover .mcard-veil{opacity:1}
.mcard-play{
  width:36px;height:36px;border-radius:50%;
  background:rgba(229,9,20,.92);
  display:flex;align-items:center;justify-content:center;
  color:#fff;font-size:.78em;margin-bottom:7px;
  box-shadow:0 0 20px rgba(229,9,20,.6);
}
.mcard-ov-ku{font-size:.78em;font-weight:700;color:#fff;line-height:1.25}
.mcard-ov-yr{font-size:.68em;color:rgba(255,255,255,.55);margin-top:2px}

/* fav + age */
.mcard-fav{
  position:absolute;top:7px;left:7px;
  background:rgba(0,0,0,.6);border:none;
  width:28px;height:28px;border-radius:50%;
  color:rgba(255,255,255,.7);font-size:.75em;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  backdrop-filter:blur(4px);transition:all .2s;
  border:1px solid rgba(255,255,255,.1);
}
.mcard-fav:hover,.mcard-fav.on{background:var(--red);color:#fff;border-color:var(--red);box-shadow:0 0 14px rgba(229,9,20,.5)}
.mcard-age{
  position:absolute;top:7px;right:7px;
  background:rgba(0,0,0,.72);color:rgba(255,255,255,.7);
  font-size:.6em;font-weight:800;
  padding:2px 7px;border-radius:4px;
  border:1px solid rgba(255,255,255,.12);letter-spacing:.5px;
}

/* card bottom */
.mcard-info{padding:9px 11px 11px}
.mcard-ku{font-size:.8em;font-weight:700;color:var(--txt);line-height:1.3;margin-bottom:5px}
.mcard-row{display:flex;justify-content:space-between;align-items:center}
.mcard-rat{font-size:.72em;font-weight:700;color:var(--gold)}
.mcard-yr{font-size:.68em;color:var(--txt3)}

/* no results */
.no-res{text-align:center;padding:60px 20px;color:var(--txt3);display:none}
.no-res i{display:block;font-size:2.2em;color:var(--red);opacity:.3;margin-bottom:10px}

/* load more */
.load-more{
  display:block;margin:6px auto 50px;
  padding:11px 40px;
  background:var(--card);border:1px solid var(--border);
  color:var(--txt2);border-radius:30px;
  cursor:pointer;font-size:.85em;font-weight:700;
  font-family:'Cairo',sans-serif;transition:all .22s;
  letter-spacing:.4px;
}
.load-more:hover{background:var(--red);border-color:var(--red);color:#fff;box-shadow:0 4px 22px rgba(229,9,20,.45)}

/* ══════════════════════════════════════
   MODAL — BOTTOM SHEET ON MOBILE
══════════════════════════════════════ */
.modal-wrap{
  position:fixed;inset:0;z-index:2000;
  display:flex;align-items:flex-end;justify-content:center;
  opacity:0;pointer-events:none;transition:opacity .3s;
}
@media(min-width:640px){.modal-wrap{align-items:center;padding:20px}}
.modal-wrap.open{opacity:1;pointer-events:all}
.modal-scrim{position:absolute;inset:0;background:rgba(0,0,0,.85);backdrop-filter:blur(12px)}
.modal-box{
  position:relative;z-index:1;
  background:var(--card);
  width:100%;max-width:720px;max-height:92svh;
  overflow-y:auto;
  border-radius:22px 22px 0 0;
  box-shadow:0 -8px 60px rgba(0,0,0,.9),0 0 0 1px var(--border);
  animation:slideUp .35s cubic-bezier(.22,1,.36,1) both;
}
@media(min-width:640px){
  .modal-box{
    border-radius:20px;
    animation:scaleIn .3s cubic-bezier(.22,1,.36,1) both;
  }
}
@keyframes slideUp{from{transform:translateY(100%)}to{transform:translateY(0)}}
@keyframes scaleIn{from{opacity:0;transform:scale(.93) translateY(16px)}to{opacity:1;transform:scale(1) translateY(0)}}
.modal-box::-webkit-scrollbar{width:3px}
.modal-box::-webkit-scrollbar-thumb{background:var(--red)}

/* drag handle (mobile) */
.modal-handle{
  width:38px;height:4px;border-radius:2px;
  background:rgba(255,255,255,.15);
  margin:12px auto 0;
}

/* modal hero */
.modal-hero{
  position:relative;
  height:210px;
  background-size:cover;background-position:center top;
}
@media(min-width:640px){.modal-hero{height:270px}}
.modal-hero-grad{
  position:absolute;inset:0;
  background:linear-gradient(to top,var(--card) 0%,rgba(19,19,26,.35) 50%,transparent 100%);
}
.modal-close{
  position:absolute;top:12px;left:12px;z-index:2;
  background:rgba(0,0,0,.68);border:none;color:#fff;
  width:33px;height:33px;border-radius:50%;font-size:.85em;
  cursor:pointer;display:flex;align-items:center;justify-content:center;
  backdrop-filter:blur(6px);transition:background .2s;
  border:1px solid rgba(255,255,255,.1);
}
.modal-close:hover{background:var(--red)}
.modal-htitle{position:absolute;bottom:12px;right:16px;left:16px;z-index:2}
.modal-ku{
  font-family:'Bebas Neue',sans-serif;font-size:1.8em;letter-spacing:2px;
  color:#fff;line-height:1;
  text-shadow:0 2px 20px rgba(0,0,0,.9);
}
.modal-en{font-size:.75em;color:rgba(255,255,255,.45);font-family:'Bebas Neue',sans-serif;letter-spacing:2px}

/* modal body */
.modal-body{padding:14px 16px 30px}
@media(min-width:640px){.modal-body{padding:16px 22px 34px}}

.mtags{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:14px}
.mtag{
  font-size:.67em;font-weight:700;padding:4px 12px;border-radius:20px;
  background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);color:var(--txt2);
  letter-spacing:.4px;
}
.mtag.r{background:rgba(229,9,20,.12);border-color:rgba(229,9,20,.25);color:#ff6b6b}
.mtag.g{background:rgba(245,197,24,.08);border-color:rgba(245,197,24,.22);color:var(--gold)}
.mtag.b{background:rgba(100,149,255,.08);border-color:rgba(100,149,255,.2);color:#88aaff}

/* trailer */
.trailer-btn{
  display:flex;align-items:center;justify-content:center;gap:10px;
  background:linear-gradient(135deg,var(--red) 0%,#900 100%);
  color:#fff;border:none;border-radius:11px;
  padding:13px;font-size:.92em;font-weight:800;cursor:pointer;
  font-family:'Cairo',sans-serif;width:100%;margin-bottom:10px;
  box-shadow:0 4px 22px rgba(229,9,20,.45);transition:all .22s;
  letter-spacing:.4px;
}
.trailer-btn:hover{transform:translateY(-2px);box-shadow:0 8px 30px rgba(229,9,20,.6)}
.trailer-player{
  display:none;width:100%;aspect-ratio:16/9;
  border-radius:11px;overflow:hidden;margin-bottom:14px;
  border:1px solid rgba(229,9,20,.25);
  box-shadow:0 8px 32px rgba(0,0,0,.7);
}
.trailer-player.open{display:block;animation:fadeUp .3s ease both}
.trailer-player iframe{width:100%;height:100%;border:none;display:block}

/* fav btn */
.modal-fav{
  display:flex;align-items:center;gap:8px;justify-content:center;
  background:rgba(229,9,20,.08);border:1px solid rgba(229,9,20,.2);
  color:#ff6b6b;border-radius:11px;padding:11px;cursor:pointer;
  font-size:.86em;font-weight:700;font-family:'Cairo',sans-serif;
  transition:all .22s;margin-bottom:14px;width:100%;
}
.modal-fav:hover,.modal-fav.on{background:var(--red);color:#fff;border-color:var(--red);box-shadow:0 4px 20px rgba(229,9,20,.4)}

/* stats */
.modal-stats{
  display:grid;grid-template-columns:repeat(2,1fr);
  gap:8px;margin-bottom:16px;
}
@media(min-width:500px){.modal-stats{grid-template-columns:repeat(4,1fr)}}
.stat{
  background:rgba(255,255,255,.03);border:1px solid var(--border);
  border-radius:9px;padding:9px 12px;
}
.stat-l{font-size:.62em;color:var(--txt3);text-transform:uppercase;letter-spacing:1px;margin-bottom:3px}
.stat-v{font-size:.84em;font-weight:700;color:var(--txt)}
.stat-v.g{color:var(--gold)}

/* sections */
.modal-sec{margin-bottom:16px}
.modal-sec h4{
  font-size:.74em;font-weight:800;color:var(--red);
  letter-spacing:1.5px;text-transform:uppercase;
  margin-bottom:7px;display:flex;align-items:center;gap:7px;
}
.modal-sec p{font-size:.84em;color:var(--txt2);line-height:1.78}

/* awards */
.awards-wrap{display:flex;flex-wrap:wrap;gap:6px}
.award{
  background:rgba(245,197,24,.06);border:1px solid rgba(245,197,24,.18);
  color:#c9a500;font-size:.68em;font-weight:700;padding:4px 11px;border-radius:20px;
}

/* ══════════════════════════════════════
   INSTAGRAM
══════════════════════════════════════ */
.ig-wrap{text-align:center;margin:30px 0}
.ig-btn{
  display:inline-flex;align-items:center;gap:10px;
  background:linear-gradient(45deg,#833ab4,#fd1d1d,#fcb045);
  color:#fff;padding:13px 30px;border-radius:50px;
  text-decoration:none;font-weight:700;font-size:.9em;
  box-shadow:0 4px 22px rgba(131,58,180,.35);
  transition:transform .22s,box-shadow .22s;
}
.ig-btn:hover{transform:translateY(-2px);box-shadow:0 8px 30px rgba(131,58,180,.55)}

/* ══════════════════════════════════════
   COMMENTS
══════════════════════════════════════ */
.csec{border-top:1px solid var(--border);padding-top:34px;margin:20px 0}
.cform{display:flex;flex-direction:column;gap:9px;margin-bottom:22px}
.crow{display:grid;grid-template-columns:1fr 1fr;gap:9px}
@media(max-width:480px){.crow{grid-template-columns:1fr}}
.cinput{
  width:100%;background:var(--card);border:1px solid var(--border);
  border-radius:9px;padding:10px 13px;color:var(--txt);
  font-size:.86em;font-family:'Cairo',sans-serif;
  outline:none;transition:border-color .2s;resize:none;
}
.cinput:focus{border-color:var(--red);box-shadow:0 0 0 2px rgba(229,9,20,.1)}
.cinput::placeholder{color:var(--txt3)}
.csend{
  align-self:flex-end;background:var(--red);color:#fff;border:none;
  border-radius:9px;padding:10px 24px;font-size:.86em;font-weight:800;
  cursor:pointer;font-family:'Cairo',sans-serif;
  transition:background .2s;display:flex;align-items:center;gap:7px;
  box-shadow:0 3px 16px rgba(229,9,20,.4);
}
.csend:hover{background:var(--red2)}
.clist{display:flex;flex-direction:column;gap:9px}
.citem{
  background:var(--card);border:1px solid var(--border);
  border-radius:11px;padding:12px 15px;
  display:flex;gap:11px;align-items:flex-start;
}
.cavatar{
  width:36px;height:36px;border-radius:50%;flex-shrink:0;
  background:linear-gradient(135deg,var(--red),#ff6b35);
  display:flex;align-items:center;justify-content:center;
  font-weight:800;font-size:.9em;
}
.cbody{flex:1}
.cauthor{font-weight:700;font-size:.82em;margin-bottom:2px}
.cmov{color:var(--red);font-size:.75em;font-weight:700}
.ctxt{font-size:.82em;color:var(--txt2);line-height:1.68}
.cbottom{display:flex;align-items:center;gap:10px;margin-top:5px}
.ctime{font-size:.68em;color:var(--txt3);opacity:.6}
.clike{
  background:none;border:none;color:var(--txt3);cursor:pointer;
  font-size:.75em;display:flex;align-items:center;gap:4px;
  font-family:'Cairo',sans-serif;transition:color .2s;
}
.clike:hover,.clike.liked{color:var(--red)}

/* ══════════════════════════════════════
   FOOTER
══════════════════════════════════════ */
footer{
  background:rgba(0,0,0,.5);border-top:1px solid var(--border);
  padding:22px 20px;text-align:center;
}
footer p{color:var(--txt3);font-size:.8em}
footer a{color:var(--red);text-decoration:none}

/* ══════════════════════════════════════
   SCROLL TOP
══════════════════════════════════════ */
.stb{
  position:fixed;bottom:22px;left:18px;z-index:800;
  width:39px;height:39px;background:var(--red);
  border:none;border-radius:50%;color:#fff;
  font-size:.85em;cursor:pointer;
  display:flex;align-items:center;justify-content:center;
  opacity:0;transform:translateY(10px);
  transition:opacity .3s,transform .3s;
  box-shadow:0 4px 18px rgba(229,9,20,.55);
}
.stb.show{opacity:1;transform:translateY(0)}

/* ══════════════════════════════════════
   LIGHT MODE
══════════════════════════════════════ */
body.light{
  --bg:#f0f0f5;--bg2:#e8e8f0;--card:#fff;--card2:#f0f0f8;
  --txt:#111;--txt2:#444;--txt3:#888;
  --border:rgba(0,0,0,.08);--glass:rgba(0,0,0,.04);
}
body.light .hero-overlay-left{background:linear-gradient(100deg,rgba(240,240,245,.98) 0%,rgba(240,240,245,.82) 40%,rgba(240,240,245,.2) 70%,transparent 100%)}
body.light .hero-overlay-bottom{background:linear-gradient(to top,rgba(240,240,245,1) 0%,rgba(240,240,245,.5) 20%,transparent 45%)}
body.light .hero-overlay-top{background:linear-gradient(to bottom,rgba(240,240,245,.7) 0%,transparent 100%)}
body.light .hero-bg{filter:brightness(.7) saturate(.9)}
body.light .nav.solid{background:rgba(240,240,245,.97)}
body.light .strip-veil{background:linear-gradient(to top,rgba(255,255,255,.9) 0%,transparent 55%)}
body.light .strip-title{color:#111}
body.light .strip-meta{color:#555}
body.light .hero-brand{color:#111;text-shadow:none}
body.light .hero-tagline{color:rgba(0,0,0,.45)}
body.light .hero-film-title{color:#111}
</style>
</head>
<body>

<!-- ─── NAVBAR ─── -->
<nav class="nav" id="nav">
  <span class="nav-brand" onclick="scrollTo(0,0)">SRUSHT MOVIES</span>
  <ul class="nav-links">
    <li><a onclick="scrollTo(0,0)">سەرەکی</a></li>
    <li><a onclick="scrollInto('favSec')">دلخوازەکانم</a></li>
    <li><a onclick="scrollInto('gridSec')">فیلمەکان</a></li>
    <li><a onclick="scrollInto('csec')">کۆمینت</a></li>
  </ul>
  <div class="nav-right">
    <button class="nav-btn" id="modeBtn"><i class="fas fa-moon"></i><span>شەو</span></button>
  </div>
</nav>

<!-- ─── HERO ─── -->
<section class="hero">
  <div class="hero-bg" id="heroBg"></div>
  <div class="hero-overlay-left"></div>
  <div class="hero-overlay-bottom"></div>
  <div class="hero-overlay-top"></div>
  <div class="hero-glow"></div>

  <!-- right poster -->
  <div class="hero-poster-wrap">
    <img class="hero-poster" id="heroPoster" src="" alt="">
  </div>

  <!-- left content -->
  <div class="hero-content">
    <div class="hero-eyebrow">SRUSHT MOVIES</div>
    <div class="hero-brand">SRUSHT<br><em>MOVIES</em></div>
    <div class="hero-rule"></div>
    <div class="hero-tagline">یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلم و دراما</div>
    <div class="hero-film-eyebrow">⬤ فیلمی هەفتە</div>
    <div class="hero-film-title" id="heroFT"></div>
    <div class="hero-chips" id="heroChips"></div>
    <div class="hero-btns">
      <button class="btn-red" id="heroInfo"><i class="fas fa-info-circle"></i> زانیاری تەواو</button>
      <a href="https://www.instagram.com/lipri_09" class="btn-glass" target="_blank"><i class="fab fa-instagram"></i> ئینستاگرام</a>
    </div>
  </div>

  <!-- bottom strip -->
  <div class="hero-strip" id="heroStrip"></div>
</section>

<!-- ─── MAIN ─── -->
<main class="main">

  <div class="search-wrap">
    <div class="sbox">
      <i class="fas fa-search"></i>
      <input class="sinput" id="si" placeholder="گەڕان بە ناوی فیلم...">
      <button class="sbtn" onclick="doSearch()">گەڕان</button>
    </div>
  </div>

  <div class="tabs">
    <button class="tab on" data-tab="all">هەموو</button>
    <button class="tab" data-tab="thriller">Thriller</button>
    <button class="tab" data-tab="drama">Drama</button>
    <button class="tab" data-tab="scifi">Sci-Fi</button>
    <button class="tab" data-tab="crime">Crime</button>
    <button class="tab" data-tab="top">⭐ +8.0</button>
  </div>

  <section id="favSec" style="margin-bottom:34px">
    <div class="sec-hd">
      <i class="fas fa-heart" style="color:var(--red)"></i>
      دلخوازەکانم
      <span class="cnt" id="favCnt">(0)</span>
      <div class="line"></div>
    </div>
    <div class="fav-empty" id="favEmpty"><i class="far fa-heart"></i>لەسەر ❤️ کلیک بکە بۆ زیادکردن</div>
    <div class="fav-row" id="favRow" style="display:none"></div>
  </section>

  <section id="gridSec">
    <div class="sec-hd">
      <i class="fas fa-film" style="color:var(--red)"></i>
      فیلمەکان
      <span class="cnt" id="mCnt"></span>
      <div class="line"></div>
    </div>
    <div class="grid" id="grid"></div>
    <div class="no-res" id="noRes"><i class="fas fa-search"></i>هیچ فیلمێک نەدۆزرایەوە</div>
    <button class="load-more" id="loadMore" style="display:none"><i class="fas fa-chevron-down"></i> زیاتر باربکە</button>
  </section>

  <div class="ig-wrap">
    <a href="https://www.instagram.com/lipri_26" class="ig-btn" target="_blank">
      <i class="fab fa-instagram"></i> سەردانی ئینستاگرام بکە
    </a>
  </div>

  <section class="csec" id="csec">
    <div class="sec-hd">
      <i class="fas fa-comments" style="color:var(--red)"></i>
      کۆمینتەکان
      <span class="cnt" id="cCnt">(0)</span>
      <div class="line"></div>
    </div>
    <div class="cform">
      <div class="crow">
        <input class="cinput" id="cN" placeholder="ناوت...">
        <input class="cinput" id="cM" placeholder="ناوی فیلم (ئارەزوومەند)">
      </div>
      <textarea class="cinput" id="cT" rows="3" placeholder="کۆمینتەکەت بنووسە..."></textarea>
      <button class="csend" onclick="addC()"><i class="fas fa-paper-plane"></i> ناردن</button>
    </div>
    <div class="clist" id="clist"></div>
  </section>
</main>

<footer>
  <p>دروستکراوە بە ❤️ بۆ کوردەکان &nbsp;|&nbsp;
  <a href="https://www.instagram.com/lipri_26" target="_blank">@lipri_26</a>
  &nbsp;|&nbsp; Srusht Movies © 2025</p>
</footer>

<button class="stb" id="stb" onclick="scrollTo({top:0,behavior:'smooth'})">
  <i class="fas fa-arrow-up"></i>
</button>

<!-- MODAL -->
<div class="modal-wrap" id="mWrap">
  <div class="modal-scrim" onclick="closeM()"></div>
  <div class="modal-box" id="mBox">
    <div class="modal-handle"></div>
  </div>
</div>

<script>
/* ════════════════════════════
   DATA — 50 REAL MOVIES
════════════════════════════ */
const M=[
{id:0,en:"Fight Club",ku:"فایت کلاب",y:1999,r:8.8,d:"139 خولەک",g:["thriller","drama"],age:"R",dir:"David Fincher",cast:"Brad Pitt, Edward Norton, Helena Bonham Carter",country:"ئەمریکا",lang:"ئینگلیزی",plot:"کارمەندێکی ناڕازی لەگەڵ فرۆشیاری سابونی بازنی سیگار ئەدەن Durden کۆمەڵێکی شەڕی نهێنی دادەمەزرێنن. فیلمەکە کریتیکێکی زیندووی سیستەمی کۆنسومەریزمە. کۆتایی فیلمەکە یەکێک لە شۆکەکەرترین کۆتاییەکانی مێژووی سینەمایە.",awards:["BAFTA: Best Editing","Saturn Award: Best Director"],trivia:"Brad Pitt تەنها 137 خولەک لە فیلمەکەدا دەردەکەوێت.",t:"qtRKdVHc-cE",p:"https://upload.wikimedia.org/wikipedia/en/f/fc/Fight_Club_poster.jpg",tmdb:550},
{id:1,en:"The Sixth Sense",ku:"هەستی شەشەم",y:1999,r:8.1,d:"107 خولەک",g:["thriller","drama"],age:"PG-13",dir:"M. Night Shyamalan",cast:"Bruce Willis, Haley Joel Osment, Toni Collette",country:"ئەمریکا",lang:"ئینگلیزی",plot:"کوڕێکی بچووک قسەی رووحەکان دەکات. دکتۆرێکی مێشک هەوڵی یارمەتیدانی دەدات. ئەو ڕاستییەی لە کۆتاییدا ئاشکرا دەبێت هەموو بینینەکانت دەگۆڕێت.",awards:["Oscar: Best Picture (Nominated)","Oscar: Best Director (Nominated)"],trivia:"فیلمەکە لە باجەتی 40M، 672M بەدەست هێنا.",t:"VG9AGf66tXM",p:"https://upload.wikimedia.org/wikipedia/en/2/28/Sixth_Sense_poster.jpg",tmdb:745},
{id:2,en:"Shutter Island",ku:"شوتەر ئایلەند",y:2010,r:8.2,d:"138 خولەک",g:["thriller","drama"],age:"R",dir:"Martin Scorsese",cast:"Leonardo DiCaprio, Mark Ruffalo, Ben Kingsley",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دوو دیتێکتیڤی فیدرالی لە گیراوەیەکی نهێنی کوشتارچیێک دەبینن. ئەو چیرۆکە زیاتر لەوەیە کە بیری لێ دەکەیتەوە.",awards:["Saturn Award: Best Horror Film","Empire Award: Best Thriller"],trivia:"DiCaprio کتێبی دەروونناسی خوێندەوە بۆ ئامادەکاری.",t:"5iaYLCiq5RM",p:"https://upload.wikimedia.org/wikipedia/en/8/8d/Shutter_Island_poster.jpg",tmdb:11324},
{id:3,en:"Parasite",ku:"پاراسایت",y:2019,r:8.5,d:"132 خولەک",g:["thriller","drama","crime"],age:"R",dir:"Bong Joon-ho",cast:"Song Kang-ho, Lee Sun-kyun, Cho Yeo-jeong",country:"کۆریای باشوور",lang:"کۆری",plot:"خێزانێکی هەژار بە تیشکبازی بۆ خێزانێکی سەروەت خۆیان نیشان دەدەن. نهێنییەکی ژێر خانووەکە هەموو شتێک دەگۆڕێت.",awards:["Oscar: Best Picture","Oscar: Best Director","Palme d'Or - Cannes 2019"],trivia:"یەکەمین فیلمی کۆریایی کە Oscar ی باشترین فیلمی وەرگرت.",t:"5xH0HfJHsaY",p:"https://upload.wikimedia.org/wikipedia/en/5/53/Parasite_%282019%29_BongJoonho.png",tmdb:496243},
{id:4,en:"Inception",ku:"ئینسپشن",y:2010,r:8.8,d:"148 خولەک",g:["scifi","thriller"],age:"PG-13",dir:"Christopher Nolan",cast:"Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دزێکی تایبەتی ئەرکی دانانی ئیدیایەک لە ذیهنی کەسێکدا وەردەگرێت — لە ناو خەونیاندا.",awards:["Oscar: Best Cinematography","Oscar: Best Visual Effects"],trivia:"Nolan 10 ساڵ کارکرد لەسەر سکریپتەکە.",t:"YoHD9XEInc0",p:"https://upload.wikimedia.org/wikipedia/en/2/2e/Inception_%282010%29_theatrical_poster.jpg",tmdb:27205},
{id:5,en:"Memento",ku:"مەمینتۆ",y:2000,r:8.4,d:"113 خولەک",g:["thriller","crime"],age:"R",dir:"Christopher Nolan",cast:"Guy Pearce, Carrie-Anne Moss, Joe Pantoliano",country:"ئەمریکا",lang:"ئینگلیزی",plot:"پیاوێک ناخۆشی بیرنەکردنەوەی بابکار هەیە. بۆ دۆزینەوەی کوژەری ژنی، لەسەر جەستەی خۆیدا تێبینی دەنووسێت.",awards:["Oscar: Best Editing (Nominated)","Writers Guild: Best Screenplay"],trivia:"فیلمەکە لە دوو ئیستراتیژی جیاواز بیناوەتەوە دەکرێت.",t:"0vS0E9bBSL0",p:"https://upload.wikimedia.org/wikipedia/en/3/35/Memento_poster.jpg",tmdb:77},
{id:6,en:"The Prestige",ku:"دەستگیری",y:2006,r:8.5,d:"130 خولەک",g:["thriller","drama"],age:"PG-13",dir:"Christopher Nolan",cast:"Christian Bale, Hugh Jackman, Scarlett Johansson",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دوو سیحربازی دووژمن هەوڵ دەدەن نهێنی تیلسمی یەکی تری بدۆزنەوە. نهێنییەکان بەیەکەوە ئاشکرا دەبن.",awards:["Oscar: Best Cinematography (Nominated)"],trivia:"هەر بازیگەرێک تەنها سکریپتی خۆیانی بینی.",t:"RLtaA9fFNXU",p:"https://upload.wikimedia.org/wikipedia/en/d/df/The_Prestige_poster.jpg",tmdb:1124},
{id:7,en:"Gone Girl",ku:"کچە ونبووە",y:2014,r:8.1,d:"149 خولەک",g:["thriller","drama","crime"],age:"R",dir:"David Fincher",cast:"Ben Affleck, Rosamund Pike, Neil Patrick Harris",country:"ئەمریکا",lang:"ئینگلیزی",plot:"ژنی پیاوێک ناپەیدا دەبێت. میدیا دوژمنایەتی دروست دەکات. بەڵام کیسەکە زیاتر لەوەیە.",awards:["Golden Globe: Best Actress","BAFTA: Best Editing"],trivia:"Fincher 50 دەرفەت هەموو سەحنەیەک دەگرێت.",t:"dcR0WYxzMkA",p:"https://upload.wikimedia.org/wikipedia/en/d/d4/Gone_Girl_Poster.jpg",tmdb:209112},
{id:8,en:"Get Out",ku:"دەرچۆ",y:2017,r:7.7,d:"104 خولەک",g:["thriller","drama"],age:"R",dir:"Jordan Peele",cast:"Daniel Kaluuya, Allison Williams, Bradley Whitford",country:"ئەمریکا",lang:"ئینگلیزی",plot:"کوڕێکی ڕەش بەرەوی خانوودایەی کچی سپیی ئەچێت. نهێنی مالباتەکە لە کۆتایی ئاشکرا دەبێت.",awards:["Oscar: Best Original Screenplay","Sundance: Audience Award"],trivia:"باجەتی 4.5M دۆلاری، 255M بەدەست هێنا.",t:"DzfpyUB60YY",p:"https://upload.wikimedia.org/wikipedia/en/a/a1/Get_Out_poster.png",tmdb:419430},
{id:9,en:"Oldboy",ku:"ئۆڵدبۆی",y:2003,r:8.1,d:"120 خولەک",g:["thriller","drama","crime"],age:"R",dir:"Park Chan-wook",cast:"Choi Min-sik, Yoo Ji-tae, Kang Hye-jung",country:"کۆریای باشوور",lang:"کۆری",plot:"پیاوێک بەبێ هۆکار 15 ساڵ دادەنرێت. 5 ڕۆژی هەیە تا هۆکارەکەی بزانێت. ئەو ڕاستییەیە ئاسمانت بەسەردا دەوەستێت.",awards:["Grand Prix - Cannes 2004"],trivia:"Tarantino ئەمەی خستووەتە لیستی باشترینەکانی.",t:"2uHx1_UZtR4",p:"https://upload.wikimedia.org/wikipedia/en/6/6e/Oldboykoreanposter.jpg",tmdb:670},
{id:10,en:"Se7en",ku:"حەفت",y:1995,r:8.6,d:"127 خولەک",g:["thriller","crime","drama"],age:"R",dir:"David Fincher",cast:"Brad Pitt, Morgan Freeman, Kevin Spacey",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دوو دیتێکتیڤ دواکەوتن کوشتارچیێکن کە تاوانەکانیان بەپێی حەفت گوناهی دین دادەمەزرێنێت.",awards:["BAFTA: Best Editing (Nominated)"],trivia:"Kevin Spacey لە کرێدیتەکانی سەرەوە دانەنراوە.",t:"znmZoVkCjpI",p:"https://upload.wikimedia.org/wikipedia/en/6/68/Seven_%28movie%29_poster.jpg",tmdb:807},
{id:11,en:"The Usual Suspects",ku:"گومانلێکراوەکانی ئاسایی",y:1995,r:8.5,d:"106 خولەک",g:["crime","thriller"],age:"R",dir:"Bryan Singer",cast:"Kevin Spacey, Gabriel Byrne, Benicio del Toro",country:"ئەمریکا",lang:"ئینگلیزی",plot:"پێنج تاوانبار ناچارن پرۆژەیەکی مەزن ئەنجام بدەن. کۆتایی فیلمەکە هەموو بینینەکانت دەگۆڕێت.",awards:["Oscar: Best Supporting Actor - Kevin Spacey","Oscar: Best Original Screenplay"],trivia:"Keyser Söze یەکێک لە باشترین ڤیلانەکانی سینەمایە.",t:"oiXdPolca5w",p:"https://upload.wikimedia.org/wikipedia/en/6/6e/The_Usual_Suspects.jpg",tmdb:629},
{id:12,en:"Interstellar",ku:"ئینتەرستێلار",y:2014,r:8.6,d:"169 خولەک",g:["scifi","drama"],age:"PG-13",dir:"Christopher Nolan",cast:"Matthew McConaughey, Anne Hathaway, Jessica Chastain",country:"ئەمریکا",lang:"ئینگلیزی",plot:"شوێندۆزان بۆ دۆزینەوەی گەردووی نوێ کڕمچاڵێک تێدەپەڕن.",awards:["Oscar: Best Visual Effects"],trivia:"فیزیکدانی نۆبێل Kip Thorne وێنەی گرانکێشی دروست کرد.",t:"zSWdZVtXT7E",p:"https://upload.wikimedia.org/wikipedia/en/b/bc/Interstellar_film_poster.jpg",tmdb:157336},
{id:13,en:"Joker",ku:"جۆکەر",y:2019,r:8.4,d:"122 خولەک",g:["thriller","drama","crime"],age:"R",dir:"Todd Phillips",cast:"Joaquin Phoenix, Robert De Niro, Zazie Beetz",country:"ئەمریکا",lang:"ئینگلیزی",plot:"Arthur Fleck بەرەو بوونە Joker ی نامداری دەگرێت. چیرۆکی کۆمەڵایەتی و دەروونی.",awards:["Oscar: Best Actor - Joaquin Phoenix","Venice: Golden Lion"],trivia:"Phoenix 52 پاوند وزەی لادا. باجەتی 60M، 1B+ بەدەست هێنا.",t:"zAGVQLHvwOY",p:"https://upload.wikimedia.org/wikipedia/en/e/e1/Joker_%282019_film%29_poster.jpg",tmdb:475557},
{id:14,en:"Prisoners",ku:"بندیەکان",y:2013,r:8.1,d:"153 خولەک",g:["thriller","crime","drama"],age:"R",dir:"Denis Villeneuve",cast:"Hugh Jackman, Jake Gyllenhaal, Viola Davis",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دوو کچی بچووک ناپەیدا دەبن. باوکێک بەبێ بەڵگە دەستی دەکات. دیتێکتیڤێک کیسەکەی پەیوەندی دەکات.",awards:["Oscar: Best Cinematography (Nominated)"],trivia:"Villeneuve 153 خولەک دانا.",t:"oWf9B4sBSYQ",p:"https://upload.wikimedia.org/wikipedia/en/0/0c/Prisoners_Poster.jpg",tmdb:146233},
{id:15,en:"The Departed",ku:"دچووەتەوە",y:2006,r:8.5,d:"151 خولەک",g:["crime","thriller","drama"],age:"R",dir:"Martin Scorsese",cast:"Leonardo DiCaprio, Matt Damon, Jack Nicholson",country:"ئەمریکا",lang:"ئینگلیزی",plot:"پۆلیسێک لە نێو کۆمەڵی جینایی دانراوە کاتێک کۆمەڵی جینایی ئاگانامەیەکی لە نێو پۆلیسدا هەیە.",awards:["Oscar: Best Picture","Oscar: Best Director","Oscar: Best Editing","Oscar: Best Adapted Screenplay"],trivia:"Scorsese ئەمجارەیە Oscar ی باشترین دەرکەوتنی وەرگرت.",t:"iqdyRSzLKkM",p:"https://upload.wikimedia.org/wikipedia/en/5/50/The_Departed_Poster.jpg",tmdb:1422},
{id:16,en:"Black Swan",ku:"قوتاببازی تاریک",y:2010,r:8.0,d:"108 خولەک",g:["thriller","drama"],age:"R",dir:"Darren Aronofsky",cast:"Natalie Portman, Mila Kunis, Vincent Cassel",country:"ئەمریکا",lang:"ئینگلیزی",plot:"ڕاقیسەیەک بۆ Swan Lake هەڵدەبژێردرێت. بۆ کامل بوون پێویستی بە گۆڕینی کەسایەتی هەیە.",awards:["Oscar: Best Actress - Natalie Portman","Golden Globe: Best Actress"],trivia:"Portman 11 مانگ ئامادەکاری کرد.",t:"9PeNHFdS0Ys",p:"https://upload.wikimedia.org/wikipedia/en/d/dc/Black_Swan_poster.jpg",tmdb:45269},
{id:17,en:"Hereditary",ku:"میراتبەری",y:2018,r:7.3,d:"127 خولەک",g:["thriller","drama"],age:"R",dir:"Ari Aster",cast:"Toni Collette, Alex Wolff, Gabriel Byrne",country:"ئەمریکا",lang:"ئینگلیزی",plot:"خێزانێک لەدوای مردنی دایکبووکەی گورپانی دروست دەکەن. نهێنییەکی خانەدانی هەموو چیرۆکەکە دەگۆڕێت.",awards:["Critics Choice: Best Horror Film"],trivia:"Aster ئەمەی وەک 'بەدترین دایکی تاریخ' ناوی بردووە.",t:"V6wWKNij_1M",p:"https://upload.wikimedia.org/wikipedia/en/8/8e/Hereditary_poster.png",tmdb:493922},
{id:18,en:"Mulholland Drive",ku:"مۆڵهۆلاند درایڤ",y:2001,r:7.9,d:"147 خولەک",g:["thriller","drama"],age:"R",dir:"David Lynch",cast:"Naomi Watts, Laura Harring, Justin Theroux",country:"ئەمریکا",lang:"ئینگلیزی",plot:"ئەکتەرەیەکی تازە لە LA دەگاتە بانەیەک. خیاڵ و ڕاستی لێک دەدرێت.",awards:["Cannes: Best Director - David Lynch"],trivia:"Lynch فیلمەکەی سەرەتا بۆ تەلەفزیۆن نووسی.",t:"nlPJbEp6Y2s",p:"https://upload.wikimedia.org/wikipedia/en/5/50/Mulholland_Drive_poster.jpg",tmdb:1018},
{id:19,en:"A Beautiful Mind",ku:"ذیهنێکی ئوقلومەند",y:2001,r:8.2,d:"135 خولەک",g:["drama"],age:"PG-13",dir:"Ron Howard",cast:"Russell Crowe, Ed Harris, Jennifer Connelly",country:"ئەمریکا",lang:"ئینگلیزی",plot:"ماتماتیکزانێکی بەرز دووچاری شیزۆفرینیا دەبێت. تێکەڵبوونی خیاڵ و ڕاستی لەیەکتری جیا دەکاتەوە.",awards:["Oscar: Best Picture","Oscar: Best Director","Oscar: Best Adapted Screenplay","Oscar: Best Supporting Actress"],trivia:"John Nash ی ڕاستەقینە لە 2015 لە تاکسییەکدا کوژرا.",t:"oaQ01GfFny4",p:"https://upload.wikimedia.org/wikipedia/en/5/54/A_Beautiful_Mind_Poster.jpg",tmdb:453},
{id:20,en:"The Truman Show",ku:"شۆوی ترومان",y:1998,r:8.1,d:"103 خولەک",g:["drama","scifi"],age:"PG",dir:"Peter Weir",cast:"Jim Carrey, Laura Linney, Ed Harris",country:"ئەمریکا",lang:"ئینگلیزی",plot:"پیاوێک هەموو ژیانی لە شۆوی تەلەفزیۆنی ژیاوە بەبێ ئەوەی بزانێت.",awards:["Golden Globe: Best Actor - Jim Carrey","Golden Globe: Best Director"],trivia:"فیلمەکە پێشبینی کردی ئاینده ڕیالیتی شۆ و ئینستاگرام.",t:"loTIzXAS7s4",p:"https://upload.wikimedia.org/wikipedia/en/9/9d/The_Truman_Show.jpg",tmdb:37165},
{id:21,en:"1917",ku:"١٩١٧",y:2019,r:8.3,d:"119 خولەک",g:["drama"],age:"R",dir:"Sam Mendes",cast:"George MacKay, Dean-Charles Chapman, Mark Strong",country:"UK",lang:"ئینگلیزی",plot:"دوو سەربازی بریتانی ئەرکی گواستنی ئیشارەیەکی مەترسیدار وەردەگرن. تەنها یەک شەو هەیانە.",awards:["Oscar: Best Cinematography","Oscar: Best Sound Mixing","Golden Globe: Best Drama"],trivia:"بەشێوەی 'یەک شۆت' فیلمبراوە — لە ڕاستیدا 61 دوور بەیەکەوە.",t:"YqNYrYUiMfg",p:"https://upload.wikimedia.org/wikipedia/en/8/8e/1917_Film_poster.jpg",tmdb:530915},
{id:22,en:"The Shining",ku:"درەوشانەوە",y:1980,r:8.4,d:"146 خولەک",g:["thriller","drama"],age:"R",dir:"Stanley Kubrick",cast:"Jack Nicholson, Shelley Duvall, Danny Lloyd",country:"UK",lang:"ئینگلیزی",plot:"نووسەرێک لەگەڵ خێزانەکەی مێمانخانەیەکی زستان چاودێری دەکات. تاریکی مەکانەکە لەسەری کاری دەکات.",awards:["Hugo Award: Best Dramatic Presentation"],trivia:"Kubrick زیاتر لە 100 دەرفەت ئەو سەحنەی گرییەکەی Duvall دووباره گرتەوە.",t:"S014oGZiSdI",p:"https://upload.wikimedia.org/wikipedia/en/b/b6/The_Shining_poster.jpg",tmdb:694},
{id:23,en:"Arrival",ku:"گەیشتن",y:2016,r:7.9,d:"116 خولەک",g:["scifi","thriller","drama"],age:"PG-13",dir:"Denis Villeneuve",cast:"Amy Adams, Jeremy Renner, Forest Whitaker",country:"ئەمریکا",lang:"ئینگلیزی",plot:"12 کەشتیی بیگانە لە جیاجیاکانی زەوی دادەنرێن. ژیانگەیاندەکارێک ئەرکداری دەبێت زمانیان فێربێت.",awards:["Oscar: Best Cinematography (Nominated)","Oscar: Best Director (Nominated)"],trivia:"Villeneuve فیلمەکە لە ٦ ژینگەی جیاواز فیلمکرا.",t:"tFMo3UJ4B4g",p:"https://upload.wikimedia.org/wikipedia/en/d/d6/Arrival_film_poster.jpg",tmdb:329865},
{id:24,en:"Eternal Sunshine",ku:"ڕووناکی هەمیشەیی ذیهنی پاک",y:2004,r:8.3,d:"108 خولەک",g:["drama","scifi"],age:"R",dir:"Michel Gondry",cast:"Jim Carrey, Kate Winslet, Tom Wilkinson",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دوو خۆشەویست بڕیاری دەدەن یادی یەکیتریان بسڕنەوە. بەڵام لەناو پرۆسەدا دووبارە خۆشویستی دروست دەبێت.",awards:["Oscar: Best Original Screenplay","BAFTA: Best Original Screenplay"],trivia:"Charlie Kaufman شێوازی نووسینی گۆرا بۆ لایەکی لادراو.",t:"hvDDD2rPaFQ",p:"https://upload.wikimedia.org/wikipedia/en/4/4d/Eternal_Sunshine_of_the_Spotless_Mind.png",tmdb:38},
{id:25,en:"A Ghost Story",ku:"چیرۆکی روح",y:2017,r:6.9,d:"92 خولەک",g:["drama","thriller"],age:"R",dir:"David Lowery",cast:"Casey Affleck, Rooney Mara",country:"ئەمریکا",lang:"ئینگلیزی",plot:"لەدوای مردنی پیاوێک روحەکەی دەمێنێتەوە بۆ ئەوەی مامۆستایی خۆی بباینێت.",awards:["Critics Choice: Most Innovative Film"],trivia:"باجەتی 100K دۆلاری. Affleck دووساعەت ژێر ملاپۆشەکەی مایەوە.",t:"bnCsAA6FvqA",p:"https://upload.wikimedia.org/wikipedia/en/a/a9/A_Ghost_Story_poster.jpg",tmdb:401981},
{id:26,en:"Annihilation",ku:"لەناوبردن",y:2018,r:6.8,d:"115 خولەک",g:["scifi","thriller"],age:"R",dir:"Alex Garland",cast:"Natalie Portman, Jennifer Jason Leigh, Oscar Isaac",country:"UK",lang:"ئینگلیزی",plot:"ژیانزانەیەک بۆ ناو 'X-Area' دەچێت. گواستنەوەی سەرسوڕهێنەر دەبینن.",awards:["BAFTA: Best Special Effects (Nominated)"],trivia:"Garland سکریپتەکەی نووسی بەبێ ئەوەی کتێبەکەی بخوێنێتەوە.",t:"89OP6Okdm08",p:"https://upload.wikimedia.org/wikipedia/en/a/a1/Annihilation_%282018%29_poster.png",tmdb:300668},
{id:27,en:"Zodiac",ku:"زۆدیاک",y:2007,r:7.7,d:"157 خولەک",g:["thriller","crime","drama"],age:"R",dir:"David Fincher",cast:"Jake Gyllenhaal, Mark Ruffalo, Robert Downey Jr.",country:"ئەمریکا",lang:"ئینگلیزی",plot:"کوژرانێکی ڕاستەقینەی کە هەرگیز نەدۆزرایەوە. کارتوونیستێک تەرخانی ژیانی دەکات.",awards:["New York Film Critics: Best Editing"],trivia:"Fincher زیاتر لە 65 ساعات فیلم گرت.",t:"YQESwXNL6KY",p:"https://upload.wikimedia.org/wikipedia/en/8/8d/Zodiac-2007-poster.jpg",tmdb:10443},
{id:28,en:"Whiplash",ku:"وویپلاش",y:2014,r:8.5,d:"106 خولەک",g:["drama"],age:"R",dir:"Damien Chazelle",cast:"Miles Teller, J.K. Simmons, Melissa Benoist",country:"ئەمریکا",lang:"ئینگلیزی",plot:"تیلمیزانی دریمزی بە مامۆستاوێکی داواکارترین ئامادەدەبێت. 'باشترین' بە چ بهایەک دێت؟",awards:["Oscar: Best Supporting Actor - J.K. Simmons","Oscar: Best Editing","Sundance: Grand Jury Prize"],trivia:"Chazelle سەرەتا کورتە فیلمی دروست کرد.",t:"7d65HCMEQls",p:"https://upload.wikimedia.org/wikipedia/en/6/68/Whiplash_%282014%29_poster.jpg",tmdb:244786},
{id:29,en:"La La Land",ku:"لالالاند",y:2016,r:8.0,d:"128 خولەک",g:["drama"],age:"PG-13",dir:"Damien Chazelle",cast:"Ryan Gosling, Emma Stone, John Legend",country:"ئەمریکا",lang:"ئینگلیزی",plot:"پیانیستێک و ئەکتەرەیەک لە LA خۆشویستی دەکەن. خەونەکانیان و خۆشویستییانیان ناگون.",awards:["Oscar: Best Actress - Emma Stone","Oscar: Best Director","Golden Globe: 7 خەڵات"],trivia:"لە شەوی Oscar دا خەڵاتی باشترین فیلمی بە ئەشتباه بەڵاو کرایەوە.",t:"0pdqf4P9MB8",p:"https://upload.wikimedia.org/wikipedia/en/a/ab/La_La_Land_%28film%29.png",tmdb:313369},
{id:30,en:"No Country for Old Men",ku:"وڵاتێک بۆ پیرەمێرد نییە",y:2007,r:8.2,d:"122 خولەک",g:["crime","thriller","drama"],age:"R",dir:"Joel & Ethan Coen",cast:"Tommy Lee Jones, Javier Bardem, Josh Brolin",country:"ئەمریکا",lang:"ئینگلیزی",plot:"ڕووبار پەی ئیش دوو ملیۆن دۆلار دروکی دروست دەکات. کوژرانێکی ئاجیزکار بەدواید دەکەوێت.",awards:["Oscar: Best Picture","Oscar: Best Director","Oscar: Best Supporting Actor - Javier Bardem"],trivia:"Anton Chigurh یەکێک لە ترسناکترین ڤیلانەکانی سینەمایە.",t:"38A__WT3-o0",p:"https://upload.wikimedia.org/wikipedia/en/4/4b/No_Country_for_Old_Men_poster.jpg",tmdb:6966},
{id:31,en:"Blade Runner 2049",ku:"بلەید ڕەنەر ٢٠٤٩",y:2017,r:8.0,d:"164 خولەک",g:["scifi","thriller","drama"],age:"R",dir:"Denis Villeneuve",cast:"Ryan Gosling, Harrison Ford, Ana de Armas",country:"ئەمریکا",lang:"ئینگلیزی",plot:"بلەید ڕەنەرێکی نوێ نهێنییەکی دروست دەکات کە شکاندنی هەموو جیهانەکەی دەکات.",awards:["Oscar: Best Cinematography","Oscar: Best Visual Effects"],trivia:"Roger Deakins Oscar وەرگرت لەدوای 13 نومزەتی.",t:"gCcx85zbxz4",p:"https://upload.wikimedia.org/wikipedia/en/9/9d/Blade_Runner_2049_poster.png",tmdb:335984},
{id:32,en:"Moon",ku:"مانگ",y:2009,r:7.9,d:"97 خولەک",g:["scifi","drama"],age:"R",dir:"Duncan Jones",cast:"Sam Rockwell, Kevin Spacey",country:"UK",lang:"ئینگلیزی",plot:"کارمەندێک تەنها لەسەر مانگ ئیشدەکات. دۆزینەوەیەکی سەرسوڕهێنەری دەکات.",awards:["BAFTA: Best British Film (Nominated)"],trivia:"باجەتی تەنها 5M دۆلاری.",t:"oY7eFiJKJRc",p:"https://upload.wikimedia.org/wikipedia/en/a/a5/Moon_2009_film.jpg",tmdb:37686},
{id:33,en:"Ex Machina",ku:"ئێکس ماکینا",y:2014,r:7.7,d:"108 خولەک",g:["scifi","thriller","drama"],age:"R",dir:"Alex Garland",cast:"Domhnall Gleeson, Alicia Vikander, Oscar Isaac",country:"UK",lang:"ئینگلیزی",plot:"پرۆگرامەرێک ئەرکی تاقیکردنەوەی ئینتەلیجەنسی دەستکردی ڕۆبۆتێک وەردەگرێت.",awards:["Oscar: Best Visual Effects"],trivia:"Vikander بازیکەری Ava کرد — CGI لەسەر جەستەکەی بوو.",t:"XYGzRJ4KWEM",p:"https://upload.wikimedia.org/wikipedia/en/1/1f/Ex_Machina_%28film%29_poster.jpg",tmdb:264660},
{id:34,en:"The Lighthouse",ku:"مناره",y:2019,r:7.4,d:"109 خولەک",g:["thriller","drama"],age:"R",dir:"Robert Eggers",cast:"Willem Dafoe, Robert Pattinson",country:"ئەمریکا",lang:"ئینگلیزی",plot:"دوو چاودێری مناره لەسەر گیراوەیەک کۆدەبنەوە. خیاڵ و ئیشتیها لەیەکتری جیا ناکەوێت.",awards:["Oscar: Best Cinematography (Nominated)"],trivia:"بە ئاسپێکت ڕیشیۆی 4:3 و سپی-ڕەش فیلمکرا.",t:"a9_IjB6LXQU",p:"https://upload.wikimedia.org/wikipedia/en/0/05/The-lighthouse-poster.jpg",tmdb:519765},
{id:35,en:"Midsommar",ku:"نیوەی ئەستا",y:2019,r:7.1,d:"148 خولەک",g:["thriller","drama"],age:"R",dir:"Ari Aster",cast:"Florence Pugh, Jack Reynor, William Jackson Harper",country:"ئەمریکا / سوید",lang:"ئینگلیزی",plot:"گروپێک بۆ جەژنی سوید دەچن. ترسناکەکانیش لە رووناکیدان.",awards:["Saturn Award: Best Horror Film (Nominated)"],trivia:"Aster وتی ئەمەیە باسی جیابوونەوەی خۆشویستی دەکات.",t:"1Bud7YH-Tc8",p:"https://upload.wikimedia.org/wikipedia/en/6/65/Midsommar_poster.jpg",tmdb:530385},
{id:36,en:"The Others",ku:"ئەوانی تر",y:2001,r:7.6,d:"101 خولەک",g:["thriller","drama"],age:"PG-13",dir:"Alejandro Amenábar",cast:"Nicole Kidman, Fionnula Flanagan, Christopher Eccleston",country:"ئیسپانیا",lang:"ئینگلیزی",plot:"ئافرەتێک لەگەڵ دوو منداڵی خۆیدا لە مالێکی تاریکدا دەژین. کۆتایی هەموو بینینەکانت دەگۆڕێت.",awards:["Goya Award: Best Film","Goya Award: Best Director"],trivia:"Amenábar سکریپت، دەرکەوتن و موزیک هەموویانی خۆی ئەنجام دا.",t:"T6U4pFsEI-s",p:"https://upload.wikimedia.org/wikipedia/en/3/35/The_Others_poster.jpg",tmdb:1428},
{id:37,en:"Nightcrawler",ku:"شەوگەرد",y:2014,r:7.9,d:"117 خولەک",g:["thriller","crime","drama"],age:"R",dir:"Dan Gilroy",cast:"Jake Gyllenhaal, Rene Russo, Bill Paxton",country:"ئەمریکا",lang:"ئینگلیزی",plot:"کەسێک جینایەت فیلمی دەگرێت و بۆ تەلەفزیۆن دەفرۆشێت. بەتەدریج بەرەو کرداری جینایی دەڕوات.",awards:["Oscar: Best Original Screenplay (Nominated)"],trivia:"Gyllenhaal 20 پاوند لادا. وتی پیاوەکەی وەک coyote بینی.",t:"X8kYDQan0dE",p:"https://upload.wikimedia.org/wikipedia/en/9/95/Nightcrawler_%282014_film%29.png",tmdb:242582},
{id:38,en:"Requiem for a Dream",ku:"ئاهەنگی خەونێک",y:2000,r:8.3,d:"102 خولەک",g:["drama","thriller"],age:"R",dir:"Darren Aronofsky",cast:"Jared Leto, Jennifer Connelly, Ellen Burstyn",country:"ئەمریکا",lang:"ئینگلیزی",plot:"چوار کەس، چوار ئیدیا، یەک کۆتایی. ترسناکترین وێنەی مەترسی مادەی تاریک.",awards:["Oscar: Best Actress (Nominated - Ellen Burstyn)"],trivia:"Aronofsky تەکنیکی Hip-Hop Montage بەکارهێنا.",t:"1Rcbh7-hm9c",p:"https://upload.wikimedia.org/wikipedia/en/e/e9/Requiem_for_a_Dream_poster.jpg",tmdb:4517},
{id:39,en:"Pan's Labyrinth",ku:"ئەستوری ئەفوون",y:2006,r:8.2,d:"118 خولەک",g:["thriller","drama"],age:"R",dir:"Guillermo del Toro",cast:"Ivana Baquero, Sergi López, Maribel Verdú",country:"ئیسپانیا",lang:"ئیسپانی",plot:"دوای جەنگی شاری ئیسپانیا کچێکی بچووک لە جیهانی خەیاڵی ئەرکانی وەردەگرێت. جیهانی ڕاستی ترسناکتری.",awards:["Oscar: Best Cinematography","Oscar: Best Art Direction","Oscar: Best Makeup"],trivia:"del Toro سکریپتەکەی لە 16 مانگدا نووسی.",t:"lG7DGMgfB9Q",p:"https://upload.wikimedia.org/wikipedia/en/b/b0/PansLabyrinthPoster.jpg",tmdb:1408},
{id:40,en:"Donnie Darko",ku:"دۆنی دارکۆ",y:2001,r:8.0,d:"113 خولەک",g:["scifi","thriller","drama"],age:"R",dir:"Richard Kelly",cast:"Jake Gyllenhaal, Jena Malone, Drew Barrymore",country:"ئەمریکا",lang:"ئینگلیزی",plot:"خورتێکی ناکۆک ئاگای دەبێت کە ئەو جیهانە 28 ڕۆژ دواتر لەناو دەچێت.",awards:["Sundance: Nominated for Grand Jury Prize"],trivia:"لەسەر پەردە شکستی هێنا بەڵام DVD ی کەلتی دروست کرد.",t:"ZZyBhhKxhZA",p:"https://upload.wikimedia.org/wikipedia/en/d/d4/Donnie_Darko_poster.jpg",tmdb:141},
{id:41,en:"Her",ku:"ئەو",y:2013,r:8.0,d:"126 خولەک",g:["drama","scifi"],age:"R",dir:"Spike Jonze",cast:"Joaquin Phoenix, Scarlett Johansson, Amy Adams",country:"ئەمریکا",lang:"ئینگلیزی",plot:"نووسەرێک دلدادەی سیستەمی ئۆپەریتینگی خۆی دەبێت. ئەو خۆشویستییە باسی تەنهایی مرۆڤی ئەمڕۆ دەکات.",awards:["Oscar: Best Original Screenplay","Golden Globe: Best Screenplay"],trivia:"Johansson تەنها دەنگی یاری کرد.",t:"WzV6mXIOVl4",p:"https://upload.wikimedia.org/wikipedia/en/4/43/Her2013Poster.jpg",tmdb:152601},
{id:42,en:"The Road",ku:"ڕێگا",y:2009,r:7.3,d:"111 خولەک",g:["drama","thriller"],age:"R",dir:"John Hillcoat",cast:"Viggo Mortensen, Kodi Smit-McPhee, Charlize Theron",country:"ئەمریکا",lang:"ئینگلیزی",plot:"لەدوای ئەفلاکی نادیار، باوک و کوڕ بەرەو باشووری کەناری بەحر دەڕۆن.",awards:["AFI: Top 10 Films of 2009"],trivia:"لەسەر رۆمانی Cormac McCarthy کرا کە Pulitzer وەریگرت.",t:"W0-EXwmGPFc",p:"https://upload.wikimedia.org/wikipedia/en/9/9e/The_Road_film_poster.jpg",tmdb:13610},
{id:43,en:"Children of Men",ku:"منداڵانی مرۆڤ",y:2006,r:7.9,d:"109 خولەک",g:["scifi","thriller","drama"],age:"R",dir:"Alfonso Cuarón",cast:"Clive Owen, Julianne Moore, Michael Caine",country:"UK",lang:"ئینگلیزی",plot:"لە 2027، هیچ منداڵێک 18 ساڵە لادایە. ئافرەتێک دووگیانەی. پیاوێکی ئاسایی ئەرکی گواستنی وەردەگرێت.",awards:["Oscar: Best Cinematography (Nominated)","BAFTA: Best Cinematography"],trivia:"سەحنەی ڕواڵەتی شەر 4 ڕۆژ بۆ فیلمکردن خایەناند.",t:"ZOC-h5Lkj60",p:"https://upload.wikimedia.org/wikipedia/en/d/df/Children_of_Men.jpg",tmdb:1984},
{id:44,en:"Uncut Gems",ku:"گەوهەرە بەئێسک نەکراوەکان",y:2019,r:7.4,d:"135 خولەک",g:["thriller","crime","drama"],age:"R",dir:"Safdie Brothers",cast:"Adam Sandler, Julia Fox, Kevin Garnett",country:"ئەمریکا",lang:"ئینگلیزی",plot:"فرۆشیاری گەوهەرفرۆشی نیویۆرک بەردەوام لەسەر گرتن ئەحوالی خراپ دەنرێت.",awards:["National Society: Best Film"],trivia:"Sandler وتی ئەگەر Oscar نەگرت دەگەڕێتەوە بۆ کۆمیدی خراپتر.",t:"xEQQkq6DixQ",p:"https://upload.wikimedia.org/wikipedia/en/b/b6/Uncut_Gems_poster.jpeg",tmdb:640146},
{id:45,en:"The Platform",ku:"پلاتفۆرم",y:2019,r:7.0,d:"94 خولەک",g:["thriller","scifi","drama"],age:"R",dir:"Galder Gaztelu-Urrutia",cast:"Ivan Massagué, Zorion Eguileor",country:"ئیسپانیا",lang:"ئیسپانی",plot:"زیندانێکی ستراندراو کە خواردن لە سەرەوە دادەنرێت. کەسانی خوارەوە تەنها ئەوەی دەخوەن کە دەماوە.",awards:["Toronto: People's Choice Award"],trivia:"ساڵی COVID-19 باوەڕەکەی گەیشتەوە بەحەد نورمال.",t:"p_YmHBMXhiQ",p:"https://upload.wikimedia.org/wikipedia/en/a/a5/The_Platform_%282019_film%29.jpg",tmdb:717728},
{id:46,en:"I Saw the Devil",ku:"شەیتانی بینیم",y:2010,r:7.8,d:"141 خولەک",g:["thriller","crime"],age:"R",dir:"Kim Jee-woon",cast:"Lee Byung-hun, Choi Min-sik",country:"کۆریای باشوور",lang:"کۆری",plot:"دیتێکتیڤێک ئەوی کوشتاری نامزێتی دەگرێت بەڵام نەیکوژێت — بەردەوام ئازاری دەدات.",awards:["Grand Bell: Best Director"],trivia:"لە کۆریا بکراویەوە چونکە زۆر توندوتیژ بوو.",t:"MxiEkNmQlDc",p:"https://upload.wikimedia.org/wikipedia/en/5/5e/I_Saw_the_Devil.jpg",tmdb:49491},
{id:47,en:"Burning",ku:"سووتان",y:2018,r:7.5,d:"148 خولەک",g:["thriller","drama","crime"],age:"R",dir:"Lee Chang-dong",cast:"Yoo Ah-in, Steven Yeun, Jeon Jong-seo",country:"کۆریای باشوور",lang:"کۆری",plot:"کورتچیرۆکنووسێکی تازەکار کچێک دەناسێت. ئەو کچەیش هاوڕێیەکی تازەی لا دەکاتەوە. ئینجا کچەکە ناپەیدا دەبێت.",awards:["Cannes: FIPRESCI Prize"],trivia:"لەسەر کورتچیرۆکی Haruki Murakami کراوە.",t:"XsuhJsclRp0",p:"https://upload.wikimedia.org/wikipedia/en/3/35/Burning_2018_film.png",tmdb:519771},
{id:48,en:"The Wailing",ku:"هاواری",y:2016,r:7.4,d:"156 خولەک",g:["thriller","drama"],age:"R",dir:"Na Hong-jin",cast:"Kwak Do-won, Hwang Jung-min, Chun Woo-hee",country:"کۆریای باشوور",lang:"کۆری",plot:"لە گوندێکی ئاشتییدا کوژرانی سەرسوڕهێنەر دەستپێدەکات. بیگانەیەک لەم گوندەدا دانیشتووە.",awards:["Grand Bell: Best Director","Blue Dragon: Best Film"],trivia:"Na Hong-jin 3 ساڵ وەختی گرت.",t:"8DxRNxDgBJE",p:"https://upload.wikimedia.org/wikipedia/en/3/3c/The_Wailing_film.jpg",tmdb:376867},
{id:49,en:"Coherence",ku:"کۆهیرینس",y:2013,r:7.2,d:"89 خولەک",g:["scifi","thriller"],age:"R",dir:"James Ward Byrkit",cast:"Emily Baldoni, Maury Sterling, Nicholas Brendon",country:"ئەمریکا",lang:"ئینگلیزی",plot:"هەشت دۆست لە شەوی تێپەڕبوونی ستێرەیەکدا کۆدەبنەوە. جیهانی پاراڵێل دەستپێدەکات.",awards:["Tribeca: Audience Award (Nominated)"],trivia:"بەبێ سکریپت فیلمکرا — بازیگەران ئیمپرۆڤایز بوون.",t:"iz9PX2-O3q0",p:"https://upload.wikimedia.org/wikipedia/en/5/58/Coherence_2013_film_poster.jpg",tmdb:220289}
];

/* ════════════════════════════
   STATE
════════════════════════════ */
const TMDB_KEY='df3194b0b76a3ac936ceb1b11c3e63d3';
const TMDB_IMG='https://image.tmdb.org/t/p/';
async function loadTMDBImages(){
  const batches=[];
  for(let i=0;i<M.length;i+=5)batches.push(M.slice(i,i+5));
  for(const batch of batches){
    await Promise.all(batch.map(async m=>{
      if(!m.tmdb)return;
      try{
        const res=await fetch(`https://api.themoviedb.org/3/movie/${m.tmdb}?api_key=${TMDB_KEY}`);
        if(!res.ok)return;
        const d=await res.json();
        if(d.poster_path)m.p=TMDB_IMG+'w500'+d.poster_path;
        if(d.backdrop_path)m.backdrop=TMDB_IMG+'w1280'+d.backdrop_path;
      }catch(e){}
    }));
    await new Promise(r=>setTimeout(r,120));
  }
  renderMovies(true);renderFavs();
  const hf=M[4];
  if(hf.backdrop)document.getElementById('heroBg').style.backgroundImage=`url('${hf.backdrop}')`;
  if(hf.p)document.getElementById('heroPoster').src=hf.p;
  [M[0],M[3],M[13],M[15]].forEach((m,i)=>{
    const el=document.querySelectorAll('.hsc-bg')[i];
    if(el&&m.backdrop)el.style.backgroundImage=`url('${m.backdrop}')`;
    else if(el&&m.p)el.style.backgroundImage=`url('${m.p}')`;
  });
}
let favs=JSON.parse(localStorage.getItem('sm_favs')||'[]');
let comments=JSON.parse(localStorage.getItem('sm_c')||'[]');
let page=1,perPage=16,tab='all',q='';

/* ════════════════════════════
   UTILS
════════════════════════════ */
function scrollInto(id){document.getElementById(id).scrollIntoView({behavior:'smooth'})}

/* ════════════════════════════
   HERO SETUP
════════════════════════════ */
const hf=M[4]; // Inception as featured
document.getElementById('heroBg').style.backgroundImage=`url('${hf.p}')`;
const hp=document.getElementById('heroPoster');
hp.src=hf.p; hp.alt=hf.en;
hp.onerror=()=>hp.style.display='none';
hp.onclick=()=>openM(hf.id);
document.getElementById('heroFT').textContent=hf.en;
document.getElementById('heroInfo').onclick=()=>openM(hf.id);
document.getElementById('heroChips').innerHTML=
  `<span class="chip gold">⭐ ${hf.r}</span><span class="chip">${hf.y}</span><span class="chip">${hf.d}</span><span class="chip red">${hf.age}</span>`;

// strip
const strip=document.getElementById('heroStrip');
[M[0],M[3],M[13],M[15]].forEach(m=>{
  const c=document.createElement('div');c.className='strip-card';
  c.innerHTML=`<div class="strip-bg" style="background-image:url('${m.p}')"></div><div class="strip-veil"></div><div class="strip-info"><div class="strip-title">${m.en}</div><div class="strip-meta"><span class="strip-gold">⭐${m.r}</span> · ${m.y} · ${m.age}</div></div>`;
  c.onclick=()=>openM(m.id);
  strip.appendChild(c);
});

/* ════════════════════════════
   FILTER
════════════════════════════ */
function filtered(){
  let l=[...M];
  if(tab==='thriller')l=l.filter(m=>m.g.includes('thriller'));
  else if(tab==='drama')l=l.filter(m=>m.g.includes('drama'));
  else if(tab==='scifi')l=l.filter(m=>m.g.includes('scifi'));
  else if(tab==='crime')l=l.filter(m=>m.g.includes('crime'));
  else if(tab==='top')l=l.filter(m=>m.r>=8.0);
  if(q)l=l.filter(m=>m.ku.includes(q)||m.en.toLowerCase().includes(q.toLowerCase()));
  return l;
}

/* ════════════════════════════
   RENDER MOVIES
════════════════════════════ */
function renderMovies(reset=false){
  const g=document.getElementById('grid');
  if(reset){g.innerHTML='';page=1;}
  const list=filtered();
  const s=(page-1)*perPage,e=s+perPage,show=list.slice(s,e);
  document.getElementById('mCnt').textContent=`(${list.length})`;
  document.getElementById('noRes').style.display=list.length===0?'block':'none';
  show.forEach((m,i)=>{
    const on=favs.includes(m.id);
    const fb=`https://placehold.co/300x450/13131a/e50914?text=${encodeURIComponent(m.en.slice(0,10))}`;
    const c=document.createElement('div');c.className='mcard';
    c.style.animationDelay=`${i*.035}s`;
    c.innerHTML=`
      <img class="mcard-img" src="${m.p}" alt="${m.ku}" loading="lazy" onerror="this.onerror=null;this.src='${fb}'">
      <div class="mcard-veil">
        <div class="mcard-play"><i class="fas fa-info-circle"></i></div>
        <div class="mcard-ov-ku">${m.ku}</div>
        <div class="mcard-ov-yr">${m.y} · ${m.d}</div>
      </div>
      <button class="mcard-fav ${on?'on':''}" data-id="${m.id}"><i class="${on?'fas':'far'} fa-heart"></i></button>
      <span class="mcard-age">${m.age}</span>
      <div class="mcard-info">
        <div class="mcard-ku">${m.ku}</div>
        <div class="mcard-row">
          <span class="mcard-rat">⭐ ${m.r}</span>
          <span class="mcard-yr">${m.y}</span>
        </div>
      </div>`;
    c.querySelector('.mcard-fav').addEventListener('click',ev=>{ev.stopPropagation();toggleFav(m.id)});
    c.addEventListener('click',()=>openM(m.id));
    g.appendChild(c);
  });
  document.getElementById('loadMore').style.display=e<list.length?'block':'none';
}

/* ════════════════════════════
   FAVORITES
════════════════════════════ */
function toggleFav(id){
  const i=favs.indexOf(id);
  if(i===-1)favs.push(id);else favs.splice(i,1);
  localStorage.setItem('sm_f',JSON.stringify(favs));
  renderFavs();
  document.querySelectorAll(`.mcard-fav[data-id="${id}"]`).forEach(b=>{
    const on=favs.includes(id);
    b.classList.toggle('on',on);
    b.querySelector('i').className=on?'fas fa-heart':'far fa-heart';
  });
}
function renderFavs(){
  const row=document.getElementById('favRow'),em=document.getElementById('favEmpty');
  document.getElementById('favCnt').textContent=`(${favs.length})`;
  if(!favs.length){row.style.display='none';em.style.display='block';return}
  em.style.display='none';row.style.display='flex';row.innerHTML='';
  favs.forEach(id=>{
    const m=M.find(x=>x.id===id);if(!m)return;
    const c=document.createElement('div');c.className='fav-mini';
    c.innerHTML=`<img src="${m.p}" alt="${m.ku}" loading="lazy" onerror="this.src='https://placehold.co/100x138/13131a/e50914'"><button class="fav-rm" data-id="${m.id}"><i class="fas fa-times"></i></button><div class="fav-name">${m.ku}</div>`;
    c.querySelector('.fav-rm').addEventListener('click',ev=>{ev.stopPropagation();toggleFav(m.id)});
    c.addEventListener('click',()=>openM(m.id));
    row.appendChild(c);
  });
}

/* ════════════════════════════
   MODAL
════════════════════════════ */
function openM(id){
  const m=M.find(x=>x.id===id);if(!m)return;
  const on=favs.includes(m.id);
  const genres=m.g.map(g=>`<span class="mtag">${g.toUpperCase()}</span>`).join('');
  const awards=m.awards.map(a=>`<div class="award">🏆 ${a}</div>`).join('');
  document.getElementById('mBox').innerHTML=`
    <div class="modal-handle"></div>
    <div class="modal-hero" style="background-image:url('${m.p}')">
      <div class="modal-hero-grad"></div>
      <button class="modal-close" onclick="closeM()"><i class="fas fa-times"></i></button>
      <div class="modal-htitle">
        <div class="modal-ku">${m.ku}</div>
        <div class="modal-en">${m.en}</div>
      </div>
    </div>
    <div class="modal-body">
      <div class="mtags">${genres}<span class="mtag g">⭐ ${m.r}</span><span class="mtag b">${m.age}</span><span class="mtag">${m.y}</span><span class="mtag">${m.d}</span></div>
      ${m.t?`<button class="trailer-btn" onclick="toggleT('${m.t}',this)"><i class="fas fa-play"></i><span id="tTxt">▶ تریلەری فیلم ببینە</span></button><div class="trailer-player" id="tPlayer"></div>`:''}
      <button class="modal-fav ${on?'on':''}" onclick="toggleFav(${m.id});this.classList.toggle('on')">
        <i class="${on?'fas':'far'} fa-heart"></i> ${on?'لە دلخوازەکانم':'زیادکردن بۆ دلخواز'}
      </button>
      <div class="modal-stats">
        <div class="stat"><div class="stat-l">دەرکەوتن</div><div class="stat-v">${m.dir}</div></div>
        <div class="stat"><div class="stat-l">وڵات</div><div class="stat-v">${m.country}</div></div>
        <div class="stat"><div class="stat-l">زمان</div><div class="stat-v">${m.lang}</div></div>
        <div class="stat"><div class="stat-l">ڕیتینگ IMDB</div><div class="stat-v g">⭐ ${m.r}</div></div>
      </div>
      <div class="modal-sec"><h4><i class="fas fa-film"></i> باسی فیلم</h4><p>${m.plot}</p></div>
      <div class="modal-sec"><h4><i class="fas fa-users"></i> بازیگەران</h4><p>${m.cast}</p></div>
      <div class="modal-sec"><h4><i class="fas fa-trophy"></i> خەڵاتەکان</h4><div class="awards-wrap">${awards}</div></div>
      <div class="modal-sec"><h4><i class="fas fa-lightbulb"></i> زانیاری سەرسوڕهێنەر</h4><p>${m.trivia}</p></div>
    </div>`;
  document.getElementById('mWrap').classList.add('open');
  document.body.style.overflow='hidden';
}
function closeM(){
  const p=document.getElementById('tPlayer');if(p)p.innerHTML='';
  document.getElementById('mWrap').classList.remove('open');
  document.body.style.overflow='';
}
function toggleT(ytId,btn){
  const p=document.getElementById('tPlayer'),t=document.getElementById('tTxt');
  if(!p)return;
  if(p.classList.contains('open')){
    p.classList.remove('open');p.innerHTML='';
    t.textContent='▶ تریلەری فیلم ببینە';
    btn.style.background='linear-gradient(135deg,var(--red) 0%,#900 100%)';
  }else{
    p.classList.add('open');
    p.innerHTML=`<iframe src="https://www.youtube.com/embed/${ytId}?autoplay=1&rel=0" allowfullscreen allow="autoplay;encrypted-media"></iframe>`;
    t.textContent='✕ داخستنی تریلەر';
    btn.style.background='linear-gradient(135deg,#2a2a2a,#111)';
    p.scrollIntoView({behavior:'smooth',block:'center'});
  }
}

/* ════════════════════════════
   COMMENTS
════════════════════════════ */
function renderC(){
  const l=document.getElementById('clist');
  document.getElementById('cCnt').textContent=`(${comments.length})`;
  l.innerHTML='';
  [...comments].reverse().forEach((c,i)=>{
    const d=document.createElement('div');d.className='citem';
    d.innerHTML=`
      <div class="cavatar">${c.n.charAt(0).toUpperCase()}</div>
      <div class="cbody">
        <div class="cauthor">${c.n}${c.m?` · <span class="cmov">${c.m}</span>`:''}</div>
        <div class="ctxt">${c.t}</div>
        <div class="cbottom">
          <span class="ctime">${c.time}</span>
          <button class="clike ${c.liked?'liked':''}" data-i="${comments.length-1-i}">
            <i class="${c.liked?'fas':'far'} fa-heart"></i> ${c.likes||0}
          </button>
        </div>
      </div>`;
    d.querySelector('.clike').addEventListener('click',function(){
      const idx=+this.dataset.i;
      comments[idx].liked=!comments[idx].liked;
      comments[idx].likes=(comments[idx].likes||0)+(comments[idx].liked?1:-1);
      localStorage.setItem('sm_c',JSON.stringify(comments));
      renderC();
    });
    l.appendChild(d);
  });
}
function addC(){
  const n=document.getElementById('cN').value.trim();
  const t=document.getElementById('cT').value.trim();
  const mv=document.getElementById('cM').value.trim();
  if(!n||!t)return;
  const now=new Date();
  comments.push({n,t,m:mv,likes:0,liked:false,
    time:now.toLocaleDateString('ku')+' · '+now.toLocaleTimeString('ku',{hour:'2-digit',minute:'2-digit'})});
  localStorage.setItem('sm_c',JSON.stringify(comments));
  document.getElementById('cN').value='';
  document.getElementById('cT').value='';
  document.getElementById('cM').value='';
  renderC();
}

/* ════════════════════════════
   TABS
════════════════════════════ */
document.querySelectorAll('.tab').forEach(b=>{
  b.addEventListener('click',function(){
    document.querySelectorAll('.tab').forEach(x=>x.classList.remove('on'));
    this.classList.add('on');
    tab=this.dataset.tab;
    renderMovies(true);
  });
});

/* ════════════════════════════
   SEARCH
════════════════════════════ */
function doSearch(){q=document.getElementById('si').value.trim();renderMovies(true)}
document.getElementById('si').addEventListener('keydown',e=>{if(e.key==='Enter')doSearch()});
document.getElementById('si').addEventListener('input',function(){if(!this.value){q='';renderMovies(true)}});
document.querySelector('.sbtn').addEventListener('click',doSearch);

/* ════════════════════════════
   LOAD MORE + SCROLL
════════════════════════════ */
document.getElementById('loadMore').addEventListener('click',()=>{page++;renderMovies()});
window.addEventListener('scroll',()=>{
  document.getElementById('nav').classList.toggle('solid',scrollY>60);
  document.getElementById('stb').classList.toggle('show',scrollY>400);
},{passive:true});
document.addEventListener('keydown',e=>{if(e.key==='Escape')closeM()});

/* ════════════════════════════
   MODE TOGGLE
════════════════════════════ */
const mb=document.getElementById('modeBtn');
if(localStorage.getItem('sm_mode')==='light'){
  document.body.classList.add('light');
  mb.querySelector('i').className='fas fa-sun';
  mb.querySelector('span').textContent='ڕۆژ';
}
mb.addEventListener('click',()=>{
  document.body.classList.toggle('light');
  const L=document.body.classList.contains('light');
  mb.querySelector('i').className=L?'fas fa-sun':'fas fa-moon';
  mb.querySelector('span').textContent=L?'ڕۆژ':'شەو';
  localStorage.setItem('sm_mode',L?'light':'dark');
});

/* ════════════════════════════
   INIT
════════════════════════════ */
renderMovies();
renderFavs();
renderC();
// load real TMDB images in background
loadTMDBImages();
</script>
</body><div style="text-align: center; margin: 50px 0; padding-bottom: 50px;">
    <h2 style="color: #fff; margin-bottom: 20px; font-family: 'Cairo', sans-serif;">بەشەکانی تری فیلم</h2>
    
    <a href="movies2.html" class="sbtn" style="text-decoration: none; display: inline-flex; align-items: center; gap: 10px; background: var(--red); color: white; padding: 12px 30px; border-radius: 50px; font-weight: bold; transition: 0.3s; border: 2px solid transparent;">
        <i class="fas fa-arrow-right"></i>
        بچۆ بۆ بەشی دووەم (50 فیلمی نوێ)
    </a>

    <br><br>

    <a href="player.html?v=U2Qp5pL38RE&title=Dune Part Two" style="color: var(--txt2); text-decoration: none; font-size: 14px;">
        <i class="fas fa-play-circle"></i> تاقیکردنەوەی پەخشکەری ڤیدیۆ
    </a>
</div>

</html>
