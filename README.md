<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>TechKr — Nigeria's Talent, Unlocked</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;0,500;0,600;0,700;0,800;0,900;1,400;1,700&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
:root {
  --bg: #f5f1ea;
  --ink: #0d0c0a;
  --rust: #c04820;
  --gold: #d4921a;
  --green: #17422a;
  --lightgreen: #e4ede7;
  --sand: #c0aa8a;
  --muted: #72685c;
  --white: #fefcf8;
  --border: rgba(13,12,10,0.1);
  --cardano: #0033ad;
  --r: 10px;
  --rsm: 6px;
}
*{box-sizing:border-box;margin:0;padding:0;}
html,body{height:100%;overflow:hidden;}
body{font-family:'Inter',sans-serif;background:var(--bg);color:var(--ink);overflow:hidden;-webkit-font-smoothing:antialiased;}

/* SCREENS */
.screen{position:absolute;inset:0;opacity:0;pointer-events:none;transition:opacity .35s ease,transform .35s ease;transform:translateY(14px);overflow-y:auto;}
.screen.active{opacity:1;pointer-events:all;transform:translateY(0);}

/* NAV */
.nav{position:sticky;top:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:0 3rem;height:68px;background:rgba(13,12,10,0.97);backdrop-filter:blur(12px);border-bottom:1px solid rgba(255,255,255,0.07);gap:1rem;}
.nav-logo{font-family:'Poppins',sans-serif;font-size:1.55rem;font-weight:800;letter-spacing:-0.02em;color:var(--gold);cursor:pointer;flex-shrink:0;display:flex;align-items:center;gap:0.2rem;}
.nav-logo .kr{color:var(--rust);}
.nav-logo .dot{width:6px;height:6px;background:var(--rust);border-radius:50%;margin-bottom:6px;animation:pdot 2s ease-in-out infinite;}
@keyframes pdot{0%,100%{transform:scale(1);opacity:1}50%{transform:scale(1.6);opacity:.6}}
.nav-links{display:flex;align-items:center;gap:0.25rem;}
.nav-link{font-size:0.76rem;font-weight:500;color:rgba(255,255,255,.55);background:none;border:none;cursor:pointer;padding:0.45rem 0.85rem;border-radius:var(--rsm);transition:all .2s;white-space:nowrap;letter-spacing:0.01em;}
.nav-link:hover{color:var(--white);background:rgba(255,255,255,.07);}
.nav-link.active-link{color:var(--gold);}
.nav-right{display:flex;align-items:center;gap:0.65rem;}
.nav-btn{font-family:'Inter',sans-serif;font-size:0.75rem;font-weight:600;letter-spacing:0.03em;padding:0.5rem 1.15rem;cursor:pointer;border:none;border-radius:var(--rsm);transition:all .2s;white-space:nowrap;}
.nav-btn-ghost{background:transparent;color:rgba(255,255,255,.7);border:1px solid rgba(255,255,255,.18);}
.nav-btn-ghost:hover{border-color:var(--gold);color:var(--gold);}
.nav-btn-cta{background:var(--rust);color:#fff;}
.nav-btn-cta:hover{background:#a83d1b;}
.nav-ham{display:none;flex-direction:column;gap:5px;cursor:pointer;background:none;border:none;padding:4px;}
.nav-ham span{display:block;width:22px;height:2px;background:rgba(255,255,255,.75);border-radius:2px;transition:all .2s;}
.mob-menu{display:none;position:fixed;top:68px;left:0;right:0;background:rgba(13,12,10,.98);border-bottom:1px solid rgba(255,255,255,.08);z-index:99;padding:1rem 1.5rem;flex-direction:column;gap:.4rem;}
.mob-menu.open{display:flex;}
.mob-item{font-size:.85rem;font-weight:500;color:rgba(255,255,255,.6);background:none;border:none;cursor:pointer;padding:.8rem 1rem;text-align:left;border-radius:var(--rsm);transition:all .15s;}
.mob-item:hover{background:rgba(255,255,255,.06);color:var(--gold);}

/* BUTTONS */
.btn{font-family:'Inter',sans-serif;font-size:.78rem;font-weight:600;letter-spacing:.03em;padding:.75rem 1.75rem;cursor:pointer;border:none;transition:all .18s;display:inline-flex;align-items:center;gap:.5rem;border-radius:var(--rsm);}
.btn-gold{background:var(--gold);color:var(--ink);}
.btn-gold:hover{background:#c0821a;transform:translateY(-1px);}
.btn-rust{background:var(--rust);color:#fff;}
.btn-rust:hover{background:#a33d13;transform:translateY(-1px);}
.btn-dark{background:var(--ink);color:#fff;}
.btn-dark:hover{background:#242220;transform:translateY(-1px);}
.btn-outline{background:transparent;color:var(--ink);border:1.5px solid var(--border);}
.btn-outline:hover{border-color:rgba(13,12,10,.35);}
.btn-ghost-white{background:rgba(255,255,255,.08);color:#fff;border:1px solid rgba(255,255,255,.15);}
.btn-ghost-white:hover{background:rgba(255,255,255,.14);}
.btn-green{background:var(--green);color:#fff;}
.btn-green:hover{background:#1c5234;}

/* CHIPS */
.chip{display:inline-flex;align-items:center;gap:.3rem;font-size:.6rem;font-weight:600;letter-spacing:.07em;text-transform:uppercase;padding:.25rem .65rem;border-radius:4px;}
.chip-gold{background:rgba(212,147,26,.12);color:#b07a10;border:1px solid rgba(212,147,26,.3);}
.chip-rust{background:rgba(192,72,32,.1);color:var(--rust);border:1px solid rgba(192,72,32,.25);}
.chip-green{background:var(--lightgreen);color:#145c2e;border:1px solid rgba(23,66,42,.2);}
.chip-blue{background:rgba(0,51,173,.08);color:var(--cardano);border:1px solid rgba(0,51,173,.2);}
.chip-muted{background:rgba(0,0,0,.04);color:var(--muted);border:1px solid var(--border);}

/* INPUTS */
.input-wrap{display:flex;flex-direction:column;gap:.4rem;}
.input-label{font-size:.67rem;font-weight:600;letter-spacing:.07em;text-transform:uppercase;color:var(--muted);}
.input-field{font-family:'Inter',sans-serif;font-size:.92rem;padding:.75rem 1rem;background:var(--white);border:1.5px solid var(--border);color:var(--ink);outline:none;transition:border-color .2s,box-shadow .2s;border-radius:var(--rsm);width:100%;}
.input-field:focus{border-color:var(--gold);box-shadow:0 0 0 3px rgba(212,147,26,.1);}
.input-field::placeholder{color:var(--sand);}
select.input-field{cursor:pointer;}
textarea.input-field{resize:vertical;min-height:100px;}

/* ═══════════════════════════════════════════════════════════
   SCREEN 1: LANDING — MODERN FREELANCE REDESIGN
═══════════════════════════════════════════════════════════ */
#s-landing{background:var(--ink);}

/* — TOP NAV BAR — */
.landing-nav{position:sticky;top:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:0 3rem;height:68px;background:rgba(13,12,10,.97);backdrop-filter:blur(12px);border-bottom:1px solid rgba(255,255,255,.07);gap:1rem;}

/* — HERO — */
.hero{min-height:calc(100vh - 68px);display:grid;grid-template-columns:1fr 1fr;position:relative;overflow:hidden;}
.hero-noise{position:absolute;inset:0;opacity:.018;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");background-size:200px;}
.hero-grid-lines{position:absolute;inset:0;opacity:.03;background-image:repeating-linear-gradient(0deg,transparent,transparent 72px,rgba(212,147,26,.8) 72px,rgba(212,147,26,.8) 73px),repeating-linear-gradient(90deg,transparent,transparent 72px,rgba(212,147,26,.8) 72px,rgba(212,147,26,.8) 73px);}

/* Hero left */
.hero-left{padding:5rem 4rem 5rem 6rem;display:flex;flex-direction:column;justify-content:center;position:relative;z-index:2;}
.hero-badge{display:inline-flex;align-items:center;gap:.6rem;background:rgba(212,147,26,.1);border:1px solid rgba(212,147,26,.25);border-radius:100px;padding:.4rem 1rem .4rem .65rem;margin-bottom:2.25rem;width:fit-content;}
.hero-badge-dot{width:6px;height:6px;background:var(--rust);border-radius:50%;animation:pdot 2s ease-in-out infinite;}
.hero-badge-text{font-size:.68rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--gold);}
.hero-h1{font-family:'Poppins',sans-serif;font-size:clamp(3.2rem,5.5vw,5.8rem);font-weight:900;line-height:.93;letter-spacing:-.04em;color:#fff;margin-bottom:1.5rem;}
.hero-h1 .gold{color:var(--gold);}
.hero-h1 .rust{color:var(--rust);}
.hero-h1 .outline{-webkit-text-stroke:2px rgba(255,255,255,.35);color:transparent;}
.hero-sub{font-size:1.02rem;line-height:1.72;color:rgba(255,255,255,.5);max-width:430px;margin-bottom:2.5rem;}

/* Hero search bar */
.hero-search{display:flex;align-items:center;background:var(--white);border-radius:var(--r);overflow:hidden;margin-bottom:1.25rem;border:2px solid rgba(255,255,255,.12);box-shadow:0 8px 40px rgba(0,0,0,.35);}
.hero-search-input{flex:1;font-family:'Inter',sans-serif;font-size:.95rem;padding:1rem 1.25rem;background:none;border:none;color:var(--ink);outline:none;}
.hero-search-input::placeholder{color:var(--sand);}
.hero-search-btn{background:var(--rust);color:#fff;border:none;padding:0 1.5rem;height:52px;font-family:'Inter',sans-serif;font-size:.8rem;font-weight:700;letter-spacing:.04em;text-transform:uppercase;cursor:pointer;transition:background .2s;white-space:nowrap;display:flex;align-items:center;gap:.5rem;}
.hero-search-btn:hover{background:#a83d1b;}
.hero-search-btn svg{width:16px;height:16px;}
.hero-cats{display:flex;gap:.5rem;flex-wrap:wrap;margin-bottom:2.75rem;}
.hero-cat{font-size:.72rem;font-weight:500;color:rgba(255,255,255,.45);background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.1);border-radius:100px;padding:.3rem .85rem;cursor:pointer;transition:all .2s;white-space:nowrap;}
.hero-cat:hover,.hero-cat.active{background:rgba(212,147,26,.15);border-color:rgba(212,147,26,.4);color:var(--gold);}
.hero-proof{display:flex;gap:2.5rem;padding-top:2.25rem;border-top:1px solid rgba(255,255,255,.07);flex-wrap:wrap;}
.proof-num{font-family:'Poppins',sans-serif;font-size:2rem;font-weight:800;color:var(--gold);line-height:1;display:block;letter-spacing:-.03em;}
.proof-label{font-size:.62rem;font-weight:600;letter-spacing:.09em;text-transform:uppercase;color:rgba(255,255,255,.3);}

/* Hero right — talent mosaic + live feed */
.hero-right{display:flex;flex-direction:column;justify-content:center;padding:4rem 5rem 4rem 2rem;position:relative;z-index:2;gap:1.5rem;}

/* Talent mosaic — visual representation of the platform */
.talent-mosaic{display:grid;grid-template-columns:1fr 1fr 1fr;grid-template-rows:auto auto auto;gap:.75rem;}
.t-card{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.09);border-radius:var(--r);padding:1rem;display:flex;flex-direction:column;gap:.6rem;cursor:pointer;transition:all .25s;position:relative;overflow:hidden;}
.t-card::before{content:'';position:absolute;inset:0;opacity:0;background:linear-gradient(135deg,rgba(212,147,26,.08),transparent);transition:opacity .3s;}
.t-card:hover{border-color:rgba(212,147,26,.3);background:rgba(255,255,255,.08);transform:translateY(-2px);}
.t-card:hover::before{opacity:1;}
.t-card.lg{grid-column:span 2;}
.t-card.gold-accent{border-color:rgba(212,147,26,.25);background:rgba(212,147,26,.06);}
.t-card.rust-accent{border-color:rgba(192,72,32,.25);background:rgba(192,72,32,.05);}
.t-card.green-accent{border-color:rgba(23,66,42,.5);background:rgba(23,66,42,.15);}
.t-avatar-row{display:flex;align-items:center;gap:.6rem;}
.t-avatar{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Poppins',sans-serif;font-size:.75rem;font-weight:700;flex-shrink:0;}
.t-name{font-size:.82rem;font-weight:600;color:#fff;line-height:1.2;}
.t-role{font-size:.7rem;color:rgba(255,255,255,.4);}
.t-rating{display:flex;align-items:center;gap:.3rem;font-size:.72rem;font-weight:600;color:var(--gold);margin-left:auto;flex-shrink:0;}
.t-rate{font-family:'Inter',sans-serif;font-size:.78rem;font-weight:700;color:#5cba6e;}
.t-skill-row{display:flex;gap:.35rem;flex-wrap:wrap;}
.t-skill{font-size:.58rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;color:rgba(255,255,255,.4);background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.08);border-radius:4px;padding:.18rem .5rem;}
.t-verified{font-size:.6rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;color:#5cba6e;display:flex;align-items:center;gap:.3rem;}
.t-img-placeholder{width:100%;height:90px;border-radius:var(--rsm);overflow:hidden;position:relative;}
.img-craft{width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:2.5rem;position:relative;}

/* Live activity feed */
.activity-panel{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.08);border-radius:var(--r);padding:1rem;}
.act-header{display:flex;align-items:center;gap:.5rem;margin-bottom:.85rem;}
.act-live-dot{width:7px;height:7px;background:#5cba6e;border-radius:50%;animation:pdot 1.5s ease-in-out infinite;}
.act-title{font-size:.63rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:rgba(255,255,255,.3);}
.act-count{font-size:.63rem;font-weight:600;color:rgba(255,255,255,.2);margin-left:auto;}
.act-list{display:flex;flex-direction:column;gap:.6rem;}
.act-item{display:flex;align-items:center;gap:.7rem;}
.act-av{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.65rem;font-weight:700;font-family:'Poppins',sans-serif;flex-shrink:0;}
.act-body{flex:1;min-width:0;}
.act-name{font-size:.78rem;font-weight:600;color:#fff;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.act-detail{font-size:.68rem;color:rgba(255,255,255,.35);}
.act-val{font-size:.72rem;font-weight:700;white-space:nowrap;margin-left:auto;}
.act-val.green{color:#5cba6e;}
.act-val.gold{color:var(--gold);}
.act-val.blue{color:#4a9eff;}
.act-val.muted{color:rgba(255,255,255,.25);}

/* — MARQUEE — */
.marquee-wrap{background:var(--rust);padding:.6rem 0;border-top:2px solid var(--gold);border-bottom:2px solid var(--gold);overflow:hidden;}
.marquee-inner{display:flex;gap:2.5rem;white-space:nowrap;animation:mq 24s linear infinite;}
@keyframes mq{from{transform:translateX(0)}to{transform:translateX(-50%)}}
.mq-item{font-size:.68rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:#fff;flex-shrink:0;display:flex;align-items:center;gap:2rem;}
.mq-item::after{content:'⬡';color:rgba(255,255,255,.3);font-size:.5rem;}

/* — CATEGORY SECTION — */
.cats-section{background:var(--white);padding:4.5rem 6rem;}
.section-label{font-size:.67rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--rust);display:flex;align-items:center;gap:.6rem;margin-bottom:.75rem;}
.section-label::before{content:'';width:20px;height:1.5px;background:var(--rust);}
.section-h2{font-family:'Poppins',sans-serif;font-size:clamp(1.8rem,3.5vw,3rem);font-weight:900;letter-spacing:-.03em;line-height:1.05;color:var(--ink);margin-bottom:.75rem;}
.section-h2 em{color:var(--rust);font-style:normal;}
.section-intro{font-size:.95rem;color:var(--muted);line-height:1.7;max-width:520px;margin-bottom:2.75rem;}
.cats-grid{display:grid;grid-template-columns:repeat(6,1fr);gap:1rem;}
.cat-card{background:var(--bg);border:1px solid var(--border);border-radius:var(--r);padding:1.5rem 1rem;text-align:center;cursor:pointer;transition:all .2s;position:relative;overflow:hidden;}
.cat-card::after{content:'';position:absolute;bottom:0;left:0;right:0;height:3px;background:var(--rust);transform:scaleX(0);transform-origin:left;transition:transform .25s;}
.cat-card:hover{border-color:rgba(192,72,32,.3);background:var(--white);transform:translateY(-3px);box-shadow:0 8px 24px rgba(0,0,0,.08);}
.cat-card:hover::after{transform:scaleX(1);}
.cat-icon{font-size:1.8rem;margin-bottom:.75rem;display:block;}
.cat-name{font-family:'Poppins',sans-serif;font-size:.85rem;font-weight:700;color:var(--ink);margin-bottom:.2rem;}
.cat-count{font-size:.67rem;font-weight:500;color:var(--muted);}

/* — HOW IT WORKS — */
.how-section{background:var(--bg);padding:5rem 6rem;}
.how-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1.5px;background:var(--border);border-radius:var(--r);overflow:hidden;}
.how-card{background:var(--white);padding:2.25rem 1.75rem;position:relative;transition:background .2s;}
.how-card:hover{background:var(--bg);}
.how-num{font-family:'Poppins',sans-serif;font-size:3.5rem;font-weight:900;letter-spacing:-.04em;color:rgba(192,72,32,.07);line-height:1;margin-bottom:.75rem;display:block;}
.how-icon{font-size:1.6rem;margin-bottom:.75rem;display:block;}
.how-card h3{font-family:'Poppins',sans-serif;font-size:.97rem;font-weight:700;margin-bottom:.5rem;letter-spacing:-.01em;}
.how-card p{font-size:.83rem;color:var(--muted);line-height:1.65;}
.how-arrow{position:absolute;top:2rem;right:-1px;width:22px;height:22px;background:var(--bg);display:flex;align-items:center;justify-content:center;font-size:.7rem;color:var(--rust);border:1px solid var(--border);border-radius:50%;z-index:1;}

/* — FEATURED TALENT — */
.talent-section{background:var(--white);padding:5rem 6rem;}
.talent-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1.25rem;margin-top:2.75rem;}
.talent-card{border:1px solid var(--border);border-radius:var(--r);overflow:hidden;cursor:pointer;transition:all .2s;background:var(--white);}
.talent-card:hover{box-shadow:0 12px 40px rgba(0,0,0,.1);transform:translateY(-4px);border-color:rgba(13,12,10,.18);}
.talent-card-top{height:90px;display:flex;align-items:center;justify-content:center;position:relative;}
.talent-card-av{width:64px;height:64px;border-radius:50%;border:3px solid var(--white);display:flex;align-items:center;justify-content:center;font-family:'Poppins',sans-serif;font-size:1.25rem;font-weight:700;position:absolute;bottom:-28px;}
.talent-card-body{padding:2rem 1.25rem 1.25rem;}
.talent-card-name{font-family:'Poppins',sans-serif;font-size:.97rem;font-weight:700;margin-bottom:.2rem;text-align:center;}
.talent-card-role{font-size:.78rem;color:var(--muted);text-align:center;margin-bottom:.85rem;}
.talent-card-skills{display:flex;gap:.35rem;flex-wrap:wrap;justify-content:center;margin-bottom:.9rem;}
.talent-card-footer{display:flex;align-items:center;justify-content:space-between;border-top:1px solid var(--border);padding-top:.85rem;}
.tc-rate{font-size:.85rem;font-weight:700;color:var(--green);}
.tc-rating{font-size:.8rem;font-weight:600;color:var(--gold);display:flex;align-items:center;gap:.25rem;}

/* — TRUST / ESCROW SECTION — */
.trust-section{background:var(--ink);padding:5rem 6rem;display:grid;grid-template-columns:1fr 1fr;gap:5rem;align-items:center;}
.trust-left{}
.trust-eyebrow{font-size:.67rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--gold);display:flex;align-items:center;gap:.6rem;margin-bottom:.75rem;}
.trust-eyebrow::before{content:'';width:20px;height:1.5px;background:var(--gold);}
.trust-h2{font-family:'Poppins',sans-serif;font-size:clamp(2rem,3.5vw,3.2rem);font-weight:900;letter-spacing:-.04em;color:#fff;line-height:1.05;margin-bottom:1.25rem;}
.trust-h2 em{color:var(--gold);font-style:normal;}
.trust-p{font-size:.92rem;color:rgba(255,255,255,.5);line-height:1.75;margin-bottom:2rem;}
.trust-feats{display:flex;flex-direction:column;gap:.85rem;}
.trust-feat{display:flex;align-items:flex-start;gap:.85rem;padding:.9rem 1rem;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);border-radius:var(--r);}
.trust-feat-icon{font-size:1.2rem;flex-shrink:0;margin-top:.05rem;}
.trust-feat-text strong{color:#fff;font-weight:600;display:block;margin-bottom:.15rem;font-size:.88rem;}
.trust-feat-text span{font-size:.8rem;color:rgba(255,255,255,.45);line-height:1.5;}
.trust-right{}
.escrow-diagram{background:rgba(255,255,255,.03);border:1px solid rgba(255,255,255,.08);border-radius:var(--r);padding:2rem;}
.escrow-title{font-size:.65rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--gold);margin-bottom:1.5rem;display:flex;align-items:center;gap:.5rem;}
.escrow-steps{display:flex;flex-direction:column;gap:0;}
.escrow-step{display:flex;align-items:flex-start;gap:1rem;padding:.9rem 0;border-bottom:1px solid rgba(255,255,255,.06);}
.escrow-step:last-child{border-bottom:none;}
.escrow-step-num{width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Poppins',sans-serif;font-size:.72rem;font-weight:700;flex-shrink:0;}
.escrow-step-text strong{color:#fff;font-size:.84rem;font-weight:600;display:block;margin-bottom:.1rem;}
.escrow-step-text span{font-size:.75rem;color:rgba(255,255,255,.4);}
.escrow-stat-row{display:grid;grid-template-columns:1fr 1fr 1fr;gap:1px;background:rgba(255,255,255,.07);margin-top:1.5rem;border-radius:var(--rsm);overflow:hidden;}
.escrow-stat{background:rgba(255,255,255,.04);padding:1rem;text-align:center;}
.escrow-stat-num{font-family:'Poppins',sans-serif;font-size:1.5rem;font-weight:800;color:var(--gold);display:block;letter-spacing:-.02em;}
.escrow-stat-label{font-size:.6rem;font-weight:600;letter-spacing:.07em;text-transform:uppercase;color:rgba(255,255,255,.3);}

/* — BOTTOM CTA — */
.cta-section{background:var(--green);padding:5.5rem 6rem;display:flex;align-items:center;justify-content:space-between;gap:3rem;flex-wrap:wrap;}
.cta-h2{font-family:'Poppins',sans-serif;font-size:clamp(2.2rem,4vw,4rem);font-weight:900;letter-spacing:-.04em;line-height:1.05;color:#fff;max-width:480px;}
.cta-h2 em{color:var(--gold);font-style:normal;}
.cta-right{display:flex;flex-direction:column;gap:.85rem;align-items:flex-start;}
.cta-right p{font-size:.9rem;color:rgba(255,255,255,.58);line-height:1.65;max-width:340px;}
.cta-btns{display:flex;gap:.75rem;flex-wrap:wrap;}

/* ═══════════════════════════════════════════════════════════
   SCREEN 2: AUTH
═══════════════════════════════════════════════════════════ */
#s-auth{background:var(--ink);display:flex;align-items:stretch;min-height:100vh;}
.auth-left{width:44%;background:var(--green);padding:4rem;display:flex;flex-direction:column;justify-content:space-between;position:relative;overflow:hidden;}
.auth-left::before{content:'TECHKR';position:absolute;bottom:-2rem;left:-1rem;font-family:'Poppins',sans-serif;font-size:12rem;font-weight:900;color:rgba(255,255,255,.03);line-height:1;pointer-events:none;white-space:nowrap;letter-spacing:-.05em;}
.auth-logo{font-family:'Poppins',sans-serif;font-size:1.45rem;font-weight:800;letter-spacing:-.02em;color:var(--gold);margin-bottom:2.5rem;cursor:pointer;}
.auth-logo .kr{color:var(--rust);}
.auth-tagline{font-family:'Poppins',sans-serif;font-size:3rem;font-weight:900;line-height:1.02;letter-spacing:-.04em;color:#fff;}
.auth-tagline em{color:var(--gold);font-style:normal;display:block;}
.auth-sub{color:rgba(255,255,255,.5);font-size:.88rem;line-height:1.7;margin-top:1.25rem;max-width:310px;}
.auth-feats{display:flex;flex-direction:column;gap:.85rem;}
.auth-feat{display:flex;align-items:flex-start;gap:.75rem;padding:.9rem 1rem;background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.08);border-radius:var(--r);}
.auth-feat-icon{font-size:1.1rem;flex-shrink:0;}
.auth-feat-text strong{color:#fff;font-size:.84rem;font-weight:600;display:block;margin-bottom:.1rem;}
.auth-feat-text span{font-size:.78rem;color:rgba(255,255,255,.45);line-height:1.5;}
.auth-right{flex:1;padding:4rem;display:flex;align-items:center;justify-content:center;}
.auth-box{width:100%;max-width:420px;}
.auth-heading{font-family:'Poppins',sans-serif;font-size:1.7rem;font-weight:800;letter-spacing:-.03em;color:#fff;margin-bottom:.35rem;}
.auth-subheading{font-size:.85rem;color:rgba(255,255,255,.4);margin-bottom:2rem;}
.auth-tabs{display:flex;background:rgba(255,255,255,.06);border-radius:var(--r);padding:.35rem;gap:.35rem;margin-bottom:2rem;}
.auth-tab{flex:1;font-size:.75rem;font-weight:600;letter-spacing:.04em;text-transform:uppercase;color:rgba(255,255,255,.4);padding:.65rem;cursor:pointer;border:none;background:none;border-radius:var(--rsm);transition:all .2s;}
.auth-tab.active{background:var(--gold);color:var(--ink);}
.auth-form{display:flex;flex-direction:column;gap:1.1rem;}
.auth-form .input-field{background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;border-radius:var(--rsm);}
.auth-form .input-field:focus{border-color:var(--gold);box-shadow:0 0 0 3px rgba(212,147,26,.15);}
.auth-form .input-field::placeholder{color:rgba(255,255,255,.2);}
.auth-form .input-label{color:rgba(255,255,255,.4);}
.role-pick{display:grid;grid-template-columns:1fr 1fr;gap:.75rem;}
.role-card{padding:1rem;border:1.5px solid rgba(255,255,255,.1);cursor:pointer;transition:all .2s;background:rgba(255,255,255,.04);text-align:center;border-radius:var(--r);}
.role-card.selected{border-color:var(--gold);background:rgba(212,147,26,.1);}
.role-card-icon{font-size:1.5rem;margin-bottom:.4rem;}
.role-card-label{font-size:.63rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:rgba(255,255,255,.5);}
.role-card.selected .role-card-label{color:var(--gold);}
.auth-divider{display:flex;align-items:center;gap:1rem;font-size:.62rem;font-weight:600;color:rgba(255,255,255,.2);text-transform:uppercase;letter-spacing:.1em;}
.auth-divider::before,.auth-divider::after{content:'';flex:1;height:1px;background:rgba(255,255,255,.1);}
.wallet-btn{width:100%;padding:.85rem;background:rgba(0,51,173,.15);border:1.5px solid rgba(0,51,173,.4);color:rgba(255,255,255,.8);font-size:.72rem;font-weight:600;letter-spacing:.06em;text-transform:uppercase;cursor:pointer;display:flex;align-items:center;justify-content:center;gap:.6rem;transition:all .2s;border-radius:var(--rsm);}
.wallet-btn:hover{background:rgba(0,51,173,.28);border-color:rgba(0,51,173,.6);}
.auth-note{font-size:.76rem;color:rgba(255,255,255,.25);text-align:center;margin-top:1.25rem;}
.auth-note a{color:var(--gold);cursor:pointer;text-decoration:underline;}

/* ═══════════════════════════════════════════════════════════
   DASH NAV (shared across screens 3–7)
═══════════════════════════════════════════════════════════ */
.dash-nav{position:sticky;top:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:0 2rem;height:62px;background:var(--white);border-bottom:1px solid var(--border);gap:.5rem;}
.dash-logo{font-family:'Poppins',sans-serif;font-size:1.3rem;font-weight:800;letter-spacing:-.02em;color:var(--gold);cursor:pointer;flex-shrink:0;}
.dash-logo .kr{color:var(--rust);}
.dash-tabs{display:flex;height:100%;overflow-x:auto;}
.dash-tab{font-size:.67rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;color:var(--muted);padding:0 1rem;border-bottom:2.5px solid transparent;cursor:pointer;background:none;border-top:none;border-left:none;border-right:none;transition:all .2s;display:flex;align-items:center;gap:.4rem;white-space:nowrap;}
.dash-tab.active{color:var(--rust);border-bottom-color:var(--rust);}
.dash-tab:hover{color:var(--ink);}
.dash-user{display:flex;align-items:center;gap:.65rem;cursor:pointer;flex-shrink:0;}
.dash-avatar{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Poppins',sans-serif;font-size:.75rem;font-weight:700;}
.dash-uname{font-size:.82rem;font-weight:600;}
.dash-badge{font-size:.55rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;background:rgba(212,147,26,.12);color:#a07010;border:1px solid rgba(212,147,26,.3);padding:.2rem .5rem;border-radius:4px;}

/* ═══════════════════════════════════════════════════════════
   SCREEN 3: DASHBOARD
═══════════════════════════════════════════════════════════ */
#s-dashboard{background:var(--bg);display:flex;flex-direction:column;}
.dash-body{flex:1;overflow-y:auto;}
.dash-content{display:none;}
.dash-content.active{display:block;}
.dash-home{padding:2rem;}
.dash-welcome{background:var(--ink);padding:2rem 2.5rem;display:flex;align-items:center;justify-content:space-between;margin-bottom:1.5rem;border-left:4px solid var(--gold);border-radius:var(--r);gap:1rem;flex-wrap:wrap;}
.dash-welcome h2{font-family:'Poppins',sans-serif;font-size:1.7rem;font-weight:800;letter-spacing:-.03em;color:#fff;}
.dash-welcome h2 span{color:var(--gold);}
.dash-welcome p{color:rgba(255,255,255,.4);font-size:.83rem;margin-top:.25rem;}
.dash-stats{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem;margin-bottom:1.5rem;}
.stat-card{background:var(--white);padding:1.4rem;border:1px solid var(--border);border-radius:var(--r);}
.stat-card-num{font-family:'Poppins',sans-serif;font-size:2.1rem;font-weight:800;letter-spacing:-.03em;line-height:1;color:var(--ink);display:block;margin-bottom:.25rem;}
.stat-card-label{font-size:.61rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--muted);}
.stat-card-sub{font-size:.76rem;color:var(--rust);margin-top:.35rem;font-weight:500;}
.dash-two-col{display:grid;grid-template-columns:1fr 1fr;gap:1.25rem;}
.dash-panel{background:var(--white);border:1px solid var(--border);border-radius:var(--r);overflow:hidden;}
.panel-header{padding:1.1rem 1.4rem;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.panel-title{font-size:.67rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);}
.panel-action{font-size:.65rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;color:var(--rust);cursor:pointer;background:none;border:none;}
.panel-action:hover{text-decoration:underline;}
.mini-job{padding:1rem 1.4rem;border-bottom:1px solid var(--border);display:flex;gap:.75rem;align-items:flex-start;}
.mini-job:last-child{border-bottom:none;}
.mini-job-ico{width:34px;height:34px;background:var(--lightgreen);display:flex;align-items:center;justify-content:center;font-size:.95rem;flex-shrink:0;border-radius:var(--rsm);}
.mini-job-title{font-size:.86rem;font-weight:600;margin-bottom:.15rem;}
.mini-job-meta{font-size:.75rem;color:var(--muted);display:flex;gap:.6rem;flex-wrap:wrap;}
.mini-job-rate{font-size:.76rem;font-weight:700;color:var(--green);margin-left:auto;white-space:nowrap;}

/* ═══════════════════════════════════════════════════════════
   SCREEN 4: JOBS
═══════════════════════════════════════════════════════════ */
#s-jobs{background:var(--bg);}
.jobs-layout{display:grid;grid-template-columns:268px 1fr;min-height:calc(100vh - 62px);}
.jobs-sidebar{background:var(--white);border-right:1px solid var(--border);padding:1.4rem;overflow-y:auto;}
.filter-section{margin-bottom:1.75rem;}
.filter-title{font-size:.63rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:.7rem;}
.filter-options{display:flex;flex-direction:column;gap:.3rem;}
.filter-opt{display:flex;align-items:center;gap:.55rem;cursor:pointer;padding:.32rem 0;}
.filter-opt input{accent-color:var(--rust);cursor:pointer;}
.filter-opt label{font-size:.84rem;cursor:pointer;color:var(--ink);}
.filter-opt-count{font-size:.61rem;font-weight:500;color:var(--sand);margin-left:auto;}
.search-bar{display:flex;gap:0;margin-bottom:1.4rem;}
.search-input{flex:1;font-family:'Inter',sans-serif;font-size:.87rem;padding:.72rem 1rem;background:var(--white);border:1.5px solid var(--border);border-right:none;color:var(--ink);outline:none;border-radius:var(--rsm) 0 0 var(--rsm);}
.search-input:focus{border-color:var(--gold);}
.search-btn{padding:0 1.1rem;background:var(--rust);border:none;color:#fff;font-size:1rem;cursor:pointer;transition:background .2s;border-radius:0 var(--rsm) var(--rsm) 0;}
.search-btn:hover{background:#a33d13;}
.jobs-main{padding:1.5rem 2rem;overflow-y:auto;}
.jobs-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.2rem;flex-wrap:wrap;gap:.75rem;}
.jobs-count{font-size:.68rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--muted);}
.job-cards{display:flex;flex-direction:column;gap:1px;background:var(--border);border-radius:var(--r);overflow:hidden;}
.job-card{background:var(--white);padding:1.35rem 1.6rem;display:grid;grid-template-columns:1fr auto;gap:1rem;cursor:pointer;transition:background .15s;border-left:3px solid transparent;}
.job-card:hover{background:#fdf9f4;border-left-color:var(--gold);}
.job-card.featured{border-left-color:var(--rust);background:#fffbf7;}
.job-card-top{display:flex;align-items:center;gap:.65rem;margin-bottom:.4rem;flex-wrap:wrap;}
.job-title{font-size:.95rem;font-weight:700;color:var(--ink);}
.job-company{font-size:.81rem;color:var(--muted);margin-bottom:.42rem;}
.job-desc{font-size:.81rem;color:var(--muted);line-height:1.55;margin-bottom:.65rem;max-width:600px;}
.job-tags{display:flex;gap:.4rem;flex-wrap:wrap;}
.job-card-right{text-align:right;display:flex;flex-direction:column;justify-content:space-between;align-items:flex-end;}
.job-rate{font-size:.9rem;font-weight:700;color:var(--green);white-space:nowrap;}
.job-type{font-size:.6rem;font-weight:500;letter-spacing:.07em;text-transform:uppercase;color:var(--muted);}
.job-apply{margin-top:.5rem;}

/* ═══════════════════════════════════════════════════════════
   SCREEN 5: POST A JOB
═══════════════════════════════════════════════════════════ */
#s-post{background:var(--bg);}
.post-layout{display:grid;grid-template-columns:1fr 360px;min-height:calc(100vh - 62px);}
.post-form-area{padding:2.5rem 3rem;overflow-y:auto;}
.post-preview-area{padding:2rem;background:var(--white);border-left:1px solid var(--border);overflow-y:auto;max-height:calc(100vh - 62px);}
.post-title-main{font-family:'Poppins',sans-serif;font-size:2rem;font-weight:900;letter-spacing:-.04em;color:var(--ink);margin-bottom:.4rem;}
.post-sub{color:var(--muted);font-size:.87rem;margin-bottom:2.25rem;}
.form-section{margin-bottom:2.25rem;}
.form-section-title{font-size:.66rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--rust);margin-bottom:1.1rem;padding-bottom:.55rem;border-bottom:1px solid var(--border);}
.form-row{display:grid;gap:1.15rem;margin-bottom:1.15rem;}
.form-row-2{grid-template-columns:1fr 1fr;}
.form-row-3{grid-template-columns:1fr 1fr 1fr;}
.escrow-visual{background:var(--ink);padding:1.4rem;margin-top:1rem;border-left:4px solid var(--gold);border-radius:0 var(--r) var(--r) 0;}
.escrow-visual-title{font-size:.63rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--gold);margin-bottom:1rem;}
.escrow-flow-row{display:flex;align-items:center;gap:0;margin-bottom:.5rem;flex-wrap:wrap;gap:.25rem;}
.escrow-node{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.1);padding:.45rem .7rem;font-size:.62rem;font-weight:500;letter-spacing:.04em;text-transform:uppercase;color:rgba(255,255,255,.6);white-space:nowrap;border-radius:4px;}
.escrow-arrow{font-size:.7rem;color:var(--gold);padding:0 .35rem;}
.escrow-node.active{background:rgba(212,147,26,.15);border-color:rgba(212,147,26,.4);color:var(--gold);}
.preview-label{font-size:.63rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:1rem;}
.preview-job-card{border:1.5px solid var(--border);padding:1.4rem;background:var(--bg);border-radius:var(--r);}
.preview-job-title{font-size:1.02rem;font-weight:700;margin-bottom:.3rem;}
.preview-job-company{font-size:.81rem;color:var(--muted);margin-bottom:.7rem;}
.preview-job-tags{display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.9rem;}
.preview-escrow-box{background:var(--ink);padding:1rem;border-radius:var(--rsm);}
.preview-escrow-row{display:flex;justify-content:space-between;align-items:center;}
.preview-escrow-label{font-size:.61rem;font-weight:500;letter-spacing:.07em;text-transform:uppercase;color:rgba(255,255,255,.4);}
.preview-escrow-val{font-size:.9rem;font-weight:700;color:var(--gold);}
.preview-escrow-status{font-size:.58rem;font-weight:600;letter-spacing:.07em;text-transform:uppercase;color:#5cba6e;margin-top:.5rem;display:flex;align-items:center;gap:.35rem;}
.preview-escrow-status::before{content:'●';font-size:.4rem;}

/* ═══════════════════════════════════════════════════════════
   SCREEN 6: BOUNTIES
═══════════════════════════════════════════════════════════ */
#s-bounties{background:var(--bg);}
.bounties-hero{background:var(--cardano);padding:3rem;position:relative;overflow:hidden;border-bottom:3px solid var(--gold);}
.bounties-hero::before{content:'⬡';position:absolute;right:3rem;top:50%;transform:translateY(-50%);font-size:14rem;color:rgba(255,255,255,.03);line-height:1;pointer-events:none;}
.bounties-eyebrow{font-size:.67rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:rgba(255,255,255,.5);margin-bottom:.75rem;display:flex;align-items:center;gap:.5rem;}
.bounties-hero h2{font-family:'Poppins',sans-serif;font-size:3rem;font-weight:900;letter-spacing:-.04em;color:#fff;line-height:1.02;margin-bottom:.75rem;}
.bounties-hero h2 em{color:var(--gold);font-style:normal;}
.bounties-hero p{color:rgba(255,255,255,.58);font-size:.9rem;line-height:1.65;max-width:540px;}
.bounties-stats{display:flex;gap:2.5rem;margin-top:1.75rem;flex-wrap:wrap;}
.b-stat-num{font-family:'Poppins',sans-serif;font-size:1.8rem;font-weight:800;color:var(--gold);display:block;line-height:1;letter-spacing:-.03em;}
.b-stat-label{font-size:.59rem;font-weight:600;letter-spacing:.09em;text-transform:uppercase;color:rgba(255,255,255,.3);}
.bounties-main{padding:2rem;}
.bounties-filter-row{display:flex;gap:.5rem;flex-wrap:wrap;margin-bottom:1.5rem;}
.filter-pill{font-size:.63rem;font-weight:600;letter-spacing:.06em;text-transform:uppercase;padding:.38rem .9rem;cursor:pointer;border:1.5px solid var(--border);background:var(--white);color:var(--muted);transition:all .15s;border-radius:100px;}
.filter-pill.active{background:var(--ink);color:#fff;border-color:var(--ink);}
.filter-pill:hover:not(.active){border-color:rgba(13,12,10,.35);color:var(--ink);}
.bounties-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--border);border-radius:var(--r);overflow:hidden;}
.bounty-card{background:var(--white);padding:1.6rem;cursor:pointer;transition:background .15s;border-top:3px solid transparent;}
.bounty-card:hover{background:#fdf9f4;border-top-color:var(--gold);}
.bounty-card.featured{border-top-color:var(--cardano);}
.bounty-sponsor{display:flex;align-items:center;gap:.6rem;margin-bottom:.85rem;}
.bounty-sponsor-ico{width:30px;height:30px;background:rgba(0,51,173,.1);display:flex;align-items:center;justify-content:center;font-size:.95rem;border-radius:var(--rsm);}
.bounty-sponsor-name{font-size:.67rem;font-weight:600;letter-spacing:.07em;text-transform:uppercase;color:var(--cardano);}
.bounty-title{font-size:.95rem;font-weight:700;margin-bottom:.42rem;}
.bounty-desc{font-size:.79rem;color:var(--muted);line-height:1.55;margin-bottom:.85rem;}
.bounty-footer{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:.5rem;}
.bounty-reward{font-size:.88rem;font-weight:700;color:var(--green);}
.bounty-deadline{font-size:.6rem;font-weight:500;letter-spacing:.06em;text-transform:uppercase;color:var(--muted);}

/* ═══════════════════════════════════════════════════════════
   SCREEN 7: PROFILE PAGE (NEW)
═══════════════════════════════════════════════════════════ */
#s-profile{background:var(--bg);}
.profile-layout{display:grid;grid-template-columns:300px 1fr;min-height:calc(100vh - 62px);gap:0;}
.profile-sidebar{background:var(--white);border-right:1px solid var(--border);padding:0;overflow-y:auto;}
.profile-sidebar-inner{padding:2rem;}
.profile-cover{height:100px;background:linear-gradient(135deg,var(--ink) 0%,#1a3a1a 100%);position:relative;overflow:hidden;}
.profile-cover::after{content:'';position:absolute;inset:0;background-image:repeating-linear-gradient(45deg,transparent,transparent 10px,rgba(212,147,26,.08) 10px,rgba(212,147,26,.08) 11px);}
.profile-av-wrap{position:relative;margin-top:-28px;margin-bottom:1rem;display:flex;align-items:flex-end;justify-content:space-between;}
.profile-av{width:64px;height:64px;border-radius:50%;border:3px solid var(--white);display:flex;align-items:center;justify-content:center;font-family:'Poppins',sans-serif;font-size:1.3rem;font-weight:700;background:var(--green);color:var(--gold);flex-shrink:0;}
.profile-online{position:absolute;bottom:3px;right:3px;width:14px;height:14px;background:#5cba6e;border:2px solid var(--white);border-radius:50%;}
.profile-edit-btn{font-size:.65rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;background:none;border:1.5px solid var(--border);color:var(--muted);padding:.35rem .75rem;cursor:pointer;border-radius:var(--rsm);transition:all .2s;}
.profile-edit-btn:hover{border-color:var(--ink);color:var(--ink);}
.profile-name{font-family:'Poppins',sans-serif;font-size:1.25rem;font-weight:800;letter-spacing:-.02em;color:var(--ink);margin-bottom:.2rem;}
.profile-title{font-size:.85rem;color:var(--muted);margin-bottom:.6rem;}
.profile-meta{display:flex;flex-direction:column;gap:.4rem;margin-bottom:1.25rem;}
.profile-meta-item{display:flex;align-items:center;gap:.5rem;font-size:.78rem;color:var(--muted);}
.profile-meta-item span{font-weight:500;color:var(--ink);}
.profile-bio{font-size:.82rem;color:var(--muted);line-height:1.65;padding:1rem;background:var(--bg);border-radius:var(--rsm);margin-bottom:1.25rem;}
.profile-section-title{font-size:.63rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:.75rem;padding-bottom:.5rem;border-bottom:1px solid var(--border);}
.profile-skills{display:flex;flex-wrap:wrap;gap:.4rem;margin-bottom:1.5rem;}
.profile-skill{font-size:.67rem;font-weight:600;letter-spacing:.04em;background:var(--lightgreen);color:#145c2e;border:1px solid rgba(23,66,42,.2);padding:.28rem .7rem;border-radius:var(--rsm);}
.profile-badges{display:flex;flex-direction:column;gap:.5rem;margin-bottom:1.5rem;}
.profile-badge-item{display:flex;align-items:center;gap:.65rem;padding:.65rem .8rem;background:var(--bg);border:1px solid var(--border);border-radius:var(--rsm);}
.profile-badge-icon{font-size:1rem;flex-shrink:0;}
.profile-badge-text{font-size:.78rem;color:var(--ink);font-weight:500;}
.profile-badge-text small{display:block;font-size:.68rem;color:var(--muted);font-weight:400;}
.profile-stats-grid{display:grid;grid-template-columns:1fr 1fr;gap:.75rem;margin-bottom:1.5rem;}
.profile-stat{text-align:center;padding:.85rem;background:var(--bg);border-radius:var(--rsm);border:1px solid var(--border);}
.profile-stat-num{font-family:'Poppins',sans-serif;font-size:1.4rem;font-weight:800;letter-spacing:-.03em;display:block;margin-bottom:.15rem;}
.profile-stat-label{font-size:.62rem;font-weight:600;letter-spacing:.07em;text-transform:uppercase;color:var(--muted);}

/* Profile main */
.profile-main{overflow-y:auto;padding:2rem;}
.profile-main-tabs{display:flex;border-bottom:1px solid var(--border);margin-bottom:2rem;gap:0;}
.profile-main-tab{font-size:.73rem;font-weight:600;letter-spacing:.04em;text-transform:uppercase;color:var(--muted);padding:.85rem 1.2rem;cursor:pointer;border-bottom:2.5px solid transparent;margin-bottom:-1px;background:none;border-top:none;border-left:none;border-right:none;transition:all .2s;}
.profile-main-tab.active{color:var(--rust);border-bottom-color:var(--rust);}
.profile-tab-content{display:none;}
.profile-tab-content.active{display:block;}

/* Portfolio grid */
.portfolio-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-bottom:2rem;}
.portfolio-item{border-radius:var(--r);overflow:hidden;cursor:pointer;transition:all .2s;border:1px solid var(--border);}
.portfolio-item:hover{transform:translateY(-3px);box-shadow:0 8px 24px rgba(0,0,0,.1);}
.portfolio-thumb{height:120px;display:flex;align-items:center;justify-content:center;font-size:2.5rem;position:relative;}
.portfolio-info{background:var(--white);padding:.85rem 1rem;}
.portfolio-info-title{font-size:.85rem;font-weight:700;margin-bottom:.2rem;}
.portfolio-info-cat{font-size:.7rem;color:var(--muted);}

/* Reviews */
.review-list{display:flex;flex-direction:column;gap:1rem;}
.review-card{background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.5rem;}
.review-header{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:.85rem;gap:1rem;}
.review-user{display:flex;align-items:center;gap:.75rem;}
.review-av{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-family:'Poppins',sans-serif;font-size:.75rem;font-weight:700;flex-shrink:0;}
.review-username{font-size:.88rem;font-weight:600;}
.review-meta{font-size:.73rem;color:var(--muted);}
.review-stars{display:flex;gap:.18rem;font-size:.9rem;}
.review-text{font-size:.84rem;color:var(--muted);line-height:1.65;}
.review-job-tag{display:inline-flex;margin-top:.85rem;font-size:.65rem;font-weight:600;letter-spacing:.04em;text-transform:uppercase;background:var(--lightgreen);color:#145c2e;padding:.28rem .7rem;border-radius:var(--rsm);}

/* Earnings chart (simple CSS bar chart) */
.earnings-section{margin-bottom:2rem;}
.earnings-header{display:flex;align-items:baseline;gap:1rem;margin-bottom:1.5rem;}
.earnings-total{font-family:'Poppins',sans-serif;font-size:2.5rem;font-weight:800;letter-spacing:-.04em;color:var(--ink);}
.earnings-change{font-size:.8rem;font-weight:600;color:#5cba6e;background:rgba(92,186,110,.1);padding:.2rem .6rem;border-radius:4px;}
.chart-bars{display:flex;gap:.5rem;align-items:flex-end;height:120px;margin-bottom:.5rem;}
.chart-bar-wrap{flex:1;display:flex;flex-direction:column;align-items:center;gap:.4rem;height:100%;}
.chart-bar{width:100%;background:var(--lightgreen);border-radius:4px 4px 0 0;transition:background .2s;cursor:pointer;min-height:4px;position:relative;margin-top:auto;}
.chart-bar:hover{background:var(--green);}
.chart-bar.current{background:var(--rust);}
.chart-label{font-size:.62rem;font-weight:500;color:var(--muted);text-align:center;}
.chart-months{display:flex;gap:.5rem;}
.chart-month{flex:1;text-align:center;font-size:.62rem;font-weight:500;color:var(--muted);}

/* ═══════════════════════════════════════════════════════════
   SCREEN 8: PAYOUT
═══════════════════════════════════════════════════════════ */
#s-payout{background:var(--ink);}
#s-payout .auth-left{background:#1a3a14;}

/* ═══════════════════════════════════════════════════════════
   TOAST
═══════════════════════════════════════════════════════════ */
.toast{position:fixed;bottom:1.5rem;right:1.5rem;z-index:9999;background:var(--ink);color:#fff;padding:.9rem 1.4rem;border-left:4px solid var(--gold);font-size:.86rem;font-weight:500;animation:toastIn .3s ease,toastOut .3s ease 2.7s forwards;max-width:320px;border-radius:0 var(--r) var(--r) 0;}
@keyframes toastIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
@keyframes toastOut{from{opacity:1}to{opacity:0;transform:translateY(6px)}}
@keyframes slideIn{from{opacity:0;transform:translateX(14px)}to{opacity:1;transform:translateX(0)}}

/* ═══════════════════════════════════════════════════════════
   RESPONSIVE
═══════════════════════════════════════════════════════════ */
@media(max-width:1024px){
  .hero{grid-template-columns:1fr;}
  .hero-left{padding:3.5rem 3rem 3.5rem 3.5rem;}
  .talent-mosaic{display:none;}
  .activity-panel{display:block;}
  .hero-right{padding:0 3.5rem 3.5rem;padding-top:0;}
  .cats-grid{grid-template-columns:repeat(3,1fr);}
  .cats-section,.how-section,.talent-section,.trust-section,.cta-section{padding:4rem 3.5rem;}
  .how-grid{grid-template-columns:repeat(2,1fr);}
  .talent-grid{grid-template-columns:repeat(2,1fr);}
  .trust-section{grid-template-columns:1fr;gap:2.5rem;}
  .auth-left{width:40%;padding:3rem;}
  .auth-right{padding:3rem;}
  .dash-stats{grid-template-columns:repeat(2,1fr);}
  .dash-two-col{grid-template-columns:1fr;}
  .bounties-grid{grid-template-columns:repeat(2,1fr);}
  .portfolio-grid{grid-template-columns:repeat(2,1fr);}
  .profile-layout{grid-template-columns:260px 1fr;}
  .post-layout{grid-template-columns:1fr 300px;}
}
@media(max-width:767px){
  .nav,.landing-nav{padding:0 1.2rem;height:60px;}
  .nav-links,.nav-right{display:none;}
  .nav-ham{display:flex;}
  .hero{grid-template-columns:1fr;min-height:auto;}
  .hero-left{padding:2.5rem 1.5rem 2rem;}
  .hero-h1{font-size:clamp(2.8rem,12vw,4rem);}
  .hero-sub{font-size:.9rem;max-width:100%;}
  .hero-cats{display:none;}
  .hero-right{padding:0 1.5rem 2.5rem;}
  .talent-mosaic{display:none;}
  .hero-proof{gap:1.5rem;}
  .cats-section,.how-section,.talent-section,.trust-section,.cta-section{padding:3rem 1.5rem;}
  .cats-grid{grid-template-columns:repeat(2,1fr);gap:.75rem;}
  .how-grid{grid-template-columns:1fr;}
  .how-arrow{display:none;}
  .talent-grid{grid-template-columns:repeat(2,1fr);}
  .cta-section{flex-direction:column;align-items:flex-start;}
  .cta-h2{font-size:2rem;}
  .auth-left{display:none;}
  .auth-right{width:100%;padding:2rem 1.5rem;}
  #s-auth{min-height:100vh;}
  .dash-nav{padding:0 1rem;height:56px;}
  .dash-tabs{display:none;}
  .dash-user .dash-uname,.dash-badge{display:none;}
  .dash-home{padding:1rem;}
  .dash-welcome{padding:1.25rem;flex-direction:column;align-items:flex-start;}
  .dash-welcome h2{font-size:1.3rem;}
  .dash-stats{grid-template-columns:1fr 1fr;gap:.75rem;}
  .stat-card{padding:1rem;}
  .stat-card-num{font-size:1.7rem;}
  .dash-two-col{grid-template-columns:1fr;gap:.75rem;}
  .jobs-layout{grid-template-columns:1fr;}
  .jobs-sidebar{display:none;}
  .jobs-main{padding:1rem 1.2rem;}
  .post-layout{grid-template-columns:1fr;}
  .post-preview-area{display:none;}
  .post-form-area{padding:1.5rem;}
  .form-row-2,.form-row-3{grid-template-columns:1fr;}
  .post-title-main{font-size:1.6rem;}
  .bounties-hero{padding:2rem 1.5rem;}
  .bounties-hero h2{font-size:2rem;}
  .bounties-main{padding:1.2rem;}
  .bounties-grid{grid-template-columns:1fr;}
  .profile-layout{grid-template-columns:1fr;}
  .profile-sidebar{border-right:none;border-bottom:1px solid var(--border);}
  .profile-main{padding:1.2rem;}
  .portfolio-grid{grid-template-columns:1fr 1fr;}
  .toast{bottom:1rem;right:1rem;left:1rem;max-width:none;}
}
</style>
</head>
<body>

<!-- ═══════════════ SCREEN 1: LANDING ═══════════════ -->
<div id="s-landing" class="screen active">
  <!-- NAV -->
  <nav class="nav">
    <div class="nav-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span><span class="dot"></span></div>
    <div class="nav-links">
      <button class="nav-link" onclick="goTo('s-jobs')">Find Work</button>
      <button class="nav-link" onclick="goTo('s-jobs')">Find Talent</button>
      <button class="nav-link" onclick="goTo('s-bounties')">⬡ Bounties</button>
      <button class="nav-link">How it Works</button>
    </div>
    <div class="nav-right">
      <button class="nav-btn nav-btn-ghost" onclick="goTo('s-auth')">Log In</button>
      <button class="nav-btn nav-btn-cta" onclick="goTo('s-auth')">Get Started Free</button>
    </div>
    <button class="nav-ham" onclick="toggleMob()" aria-label="Menu"><span></span><span></span><span></span></button>
  </nav>
  <div class="mob-menu" id="mob-menu">
    <button class="mob-item" onclick="goTo('s-jobs');toggleMob()">Find Work</button>
    <button class="mob-item" onclick="goTo('s-jobs');toggleMob()">Find Talent</button>
    <button class="mob-item" onclick="goTo('s-bounties');toggleMob()">⬡ Bounties</button>
    <hr style="border:none;border-top:1px solid rgba(255,255,255,.08);margin:.25rem 0;">
    <button class="mob-item" onclick="goTo('s-auth');toggleMob()">Log In</button>
    <button class="mob-item" style="color:var(--gold);" onclick="goTo('s-auth');toggleMob()">Get Started Free →</button>
  </div>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-noise"></div>
    <div class="hero-grid-lines"></div>

    <!-- Left -->
    <div class="hero-left">
      <div class="hero-badge">
        <div class="hero-badge-dot"></div>
        <span class="hero-badge-text">Nigeria's #1 Verified Talent Platform</span>
      </div>
      <h1 class="hero-h1">
        Real Work.<br/>
        <span class="gold">Real Pay.</span><br/>
        <span class="outline">Verified.</span>
      </h1>
      <p class="hero-sub">Connect with skilled Nigerian professionals — software developers, carpenters, designers, welders and more — through blockchain-secured escrow and on-chain reputation.</p>

      <!-- Search -->
      <div class="hero-search">
        <svg style="margin-left:1.1rem;flex-shrink:0;" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--sand)" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>
        <input class="hero-search-input" placeholder="Search for a skill, trade, or service…" type="text"/>
        <button class="hero-search-btn" onclick="goTo('s-jobs')">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>
          Search
        </button>
      </div>
      <div class="hero-cats">
        <span class="hero-cat active">All</span>
        <span class="hero-cat">💻 Software Dev</span>
        <span class="hero-cat">🎨 Design</span>
        <span class="hero-cat">🔨 Artisan</span>
        <span class="hero-cat">📝 Writing</span>
        <span class="hero-cat">📱 Virtual Assist</span>
        <span class="hero-cat">⬡ Blockchain</span>
      </div>
      <div class="hero-proof">
        <div class="proof-item"><span class="proof-num">12K+</span><span class="proof-label">Verified Talents</span></div>
        <div class="proof-item"><span class="proof-num">$54M+</span><span class="proof-label">Paid Out</span></div>
        <div class="proof-item"><span class="proof-num">99%</span><span class="proof-label">Dispute-Free</span></div>
        <div class="proof-item"><span class="proof-num">580+</span><span class="proof-label">Active Jobs</span></div>
      </div>
    </div>

    <!-- Right: Talent Mosaic + Live Activity -->
    <div class="hero-right">
      <!-- Talent mosaic — visual representation of platform diversity -->
      <div class="talent-mosaic">
        <!-- Card 1 — large, software dev -->
        <div class="t-card lg gold-accent" onclick="goTo('s-profile')">
          <div class="t-avatar-row">
            <div class="t-avatar" style="background:#1a3a1a;color:#e8a020;">FN</div>
            <div>
              <div class="t-name">Fatima Nuhu</div>
              <div class="t-role">UI/UX Designer · Lagos</div>
            </div>
            <div class="t-rating">★ 4.9</div>
          </div>
          <div class="t-img-placeholder" style="background:linear-gradient(135deg,#1a2a4a,#2a1a3a);">
            <div class="img-craft" style="font-size:2.8rem;">🖥️</div>
            <div style="position:absolute;bottom:.6rem;right:.6rem;background:rgba(212,147,26,.9);color:var(--ink);font-size:.58rem;font-weight:700;padding:.2rem .55rem;border-radius:3px;letter-spacing:.04em;text-transform:uppercase;">Pro</div>
          </div>
          <div class="t-skill-row"><span class="t-skill">Figma</span><span class="t-skill">UI Systems</span><span class="t-skill">Prototyping</span></div>
          <div style="display:flex;align-items:center;justify-content:space-between;">
            <div class="t-verified">✓ On-chain Verified · 47 reviews</div>
            <div class="t-rate">$22/hr</div>
          </div>
        </div>
        <!-- Card 2 — carpenter -->
        <div class="t-card rust-accent">
          <div class="t-avatar-row">
            <div class="t-avatar" style="background:#2a1a08;color:#e8a020;">KA</div>
            <div>
              <div class="t-name">Kola Adeyemi</div>
              <div class="t-role">Carpenter · Ibadan</div>
            </div>
          </div>
          <div class="t-img-placeholder" style="background:linear-gradient(135deg,#2a1508,#3a2010);">
            <div class="img-craft">🪵</div>
          </div>
          <div class="t-rating" style="margin-left:0;">★ 4.8 <span style="color:rgba(255,255,255,.35);font-weight:400;">· 32 jobs</span></div>
          <div class="t-rate">$480/project</div>
        </div>
        <!-- Card 3 — blockchain dev -->
        <div class="t-card" style="background:rgba(0,51,173,.12);border-color:rgba(0,51,173,.3);">
          <div class="t-avatar-row">
            <div class="t-avatar" style="background:#0033ad;color:#fff;">⬡</div>
            <div>
              <div class="t-name">Emeka Obi</div>
              <div class="t-role">Blockchain Dev</div>
            </div>
          </div>
          <div class="t-skill-row"><span class="t-skill" style="background:rgba(0,51,173,.2);color:#4a9eff;">Plutus</span><span class="t-skill" style="background:rgba(0,51,173,.2);color:#4a9eff;">Aiken</span></div>
          <div class="t-rate" style="color:#4a9eff;">$2,800/contract</div>
        </div>
        <!-- Card 4 — VA -->
        <div class="t-card green-accent">
          <div class="t-avatar-row">
            <div class="t-avatar" style="background:#17422a;color:#5cba6e;">AU</div>
            <div>
              <div class="t-name">Amara Uche</div>
              <div class="t-role">Virtual Assist · Abuja</div>
            </div>
          </div>
          <div class="t-rating" style="margin-left:0;color:#5cba6e;">★ 5.0 · 28 reviews</div>
          <div class="t-rate" style="color:#5cba6e;">$15/hr</div>
        </div>
        <!-- Card 5 — welder -->
        <div class="t-card">
          <div class="t-avatar-row">
            <div class="t-avatar" style="background:#1a1a2a;color:#8888ff;">SI</div>
            <div>
              <div class="t-name">Sunday Ike</div>
              <div class="t-role">Welder · Port Harcourt</div>
            </div>
          </div>
          <div class="t-img-placeholder" style="background:linear-gradient(135deg,#1a1a1a,#2a1a0a);height:60px;">
            <div class="img-craft" style="font-size:1.8rem;">⚙️</div>
          </div>
          <div class="t-rate">$320/project</div>
        </div>
        <!-- Card 6 — content writer -->
        <div class="t-card" style="background:rgba(212,147,26,.08);border-color:rgba(212,147,26,.2);">
          <div class="t-avatar-row">
            <div class="t-avatar" style="background:#2a1a08;color:var(--gold);">CH</div>
            <div>
              <div class="t-name">Chioma Hassan</div>
              <div class="t-role">Content Writer</div>
            </div>
          </div>
          <div class="t-skill-row"><span class="t-skill">SEO</span><span class="t-skill">Copywriting</span></div>
          <div class="t-rate">$18/hr</div>
        </div>
      </div>

      <!-- Live Activity Panel -->
      <div class="activity-panel">
        <div class="act-header">
          <div class="act-live-dot"></div>
          <div class="act-title">Live Platform Activity</div>
          <div class="act-count">Updated now</div>
        </div>
        <div class="act-list">
          <div class="act-item" style="animation:slideIn .5s ease both;">
            <div class="act-av" style="background:#1a4a2e;color:#e8a020;">FN</div>
            <div class="act-body">
              <div class="act-name">Fatima Nuhu <span style="font-weight:400;color:rgba(255,255,255,.3);font-size:.68rem;">earned Pro Badge</span></div>
              <div class="act-detail">UI/UX Designer · Lagos · 47 reviews</div>
            </div>
            <div class="act-val gold">⬡ PRO</div>
          </div>
          <div class="act-item" style="animation:slideIn .5s .1s ease both;">
            <div class="act-av" style="background:#1a3a5c;color:#fff;">KA</div>
            <div class="act-body">
              <div class="act-name">Kola Adeyemi <span style="font-weight:400;color:rgba(255,255,255,.3);font-size:.68rem;">completed job</span></div>
              <div class="act-detail">Master Carpenter · Ibadan</div>
            </div>
            <div class="act-val green">+$269</div>
          </div>
          <div class="act-item" style="animation:slideIn .5s .2s ease both;">
            <div class="act-av" style="background:#2a1a08;color:var(--gold);">OA</div>
            <div class="act-body">
              <div class="act-name">Orji & Associates <span style="font-weight:400;color:rgba(255,255,255,.3);font-size:.68rem;">locked escrow</span></div>
              <div class="act-detail">React Developer needed · Remote</div>
            </div>
            <div class="act-val gold">$1,155</div>
          </div>
          <div class="act-item" style="animation:slideIn .5s .3s ease both;">
            <div class="act-av" style="background:#0033ad;color:#fff;">⬡</div>
            <div class="act-body">
              <div class="act-name">MinswapDEX <span style="font-weight:400;color:rgba(255,255,255,.3);font-size:.68rem;">posted bounty</span></div>
              <div class="act-detail">Community Management · 30 days</div>
            </div>
            <div class="act-val blue">₳ 650</div>
          </div>
          <div class="act-item" style="animation:slideIn .5s .4s ease both;">
            <div class="act-av" style="background:#3a1a2e;color:var(--gold);">AU</div>
            <div class="act-body">
              <div class="act-name">Amara Uche <span style="font-weight:400;color:rgba(255,255,255,.3);font-size:.68rem;">joined platform</span></div>
              <div class="act-detail">Virtual Assistant · Abuja</div>
            </div>
            <div class="act-val muted">NEW</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- MARQUEE -->
  <div class="marquee-wrap">
    <div class="marquee-inner">
      <span class="mq-item">Software Developers</span><span class="mq-item">Carpenters</span><span class="mq-item">UI/UX Designers</span><span class="mq-item">Vulcanizers</span><span class="mq-item">Virtual Assistants</span><span class="mq-item">Welders</span><span class="mq-item">Data Analysts</span><span class="mq-item">Hairdressers</span><span class="mq-item">Content Writers</span><span class="mq-item">Electricians</span><span class="mq-item">Blockchain Devs</span><span class="mq-item">Mechanics</span><span class="mq-item">Tailors</span><span class="mq-item">Plumbers</span>
      <span class="mq-item">Software Developers</span><span class="mq-item">Carpenters</span><span class="mq-item">UI/UX Designers</span><span class="mq-item">Vulcanizers</span><span class="mq-item">Virtual Assistants</span><span class="mq-item">Welders</span><span class="mq-item">Data Analysts</span><span class="mq-item">Hairdressers</span><span class="mq-item">Content Writers</span><span class="mq-item">Electricians</span><span class="mq-item">Blockchain Devs</span><span class="mq-item">Mechanics</span><span class="mq-item">Tailors</span><span class="mq-item">Plumbers</span>
    </div>
  </div>

  <!-- BROWSE CATEGORIES -->
  <section class="cats-section">
    <div class="section-label">What are you looking for?</div>
    <h2 class="section-h2">Browse by <em>Category</em></h2>
    <p class="section-intro">From code to craft — TechKr is the only platform where your local carpenter and a global blockchain dev live on the same verified marketplace.</p>
    <div class="cats-grid">
      <div class="cat-card" onclick="goTo('s-jobs')"><span class="cat-icon">💻</span><div class="cat-name">Software Dev</div><div class="cat-count">248 jobs</div></div>
      <div class="cat-card" onclick="goTo('s-jobs')"><span class="cat-icon">🎨</span><div class="cat-name">Design</div><div class="cat-count">91 jobs</div></div>
      <div class="cat-card" onclick="goTo('s-jobs')"><span class="cat-icon">🔨</span><div class="cat-name">Artisan & Trade</div><div class="cat-count">130 jobs</div></div>
      <div class="cat-card" onclick="goTo('s-jobs')"><span class="cat-icon">📝</span><div class="cat-name">Writing</div><div class="cat-count">64 jobs</div></div>
      <div class="cat-card" onclick="goTo('s-jobs')"><span class="cat-icon">📱</span><div class="cat-name">Virtual Assist</div><div class="cat-count">47 jobs</div></div>
      <div class="cat-card" onclick="goTo('s-bounties')"><span class="cat-icon">⬡</span><div class="cat-name">Blockchain</div><div class="cat-count">38 bounties</div></div>
    </div>
  </section>

  <!-- HOW IT WORKS -->
  <section class="how-section">
    <div style="margin-bottom:2.75rem;">
      <div class="section-label">How it works</div>
      <h2 class="section-h2">Simple. Secure. <em>Verified.</em></h2>
    </div>
    <div class="how-grid">
      <div class="how-card">
        <span class="how-num">01</span>
        <span class="how-icon">🪪</span>
        <h3>Create Your Profile</h3>
        <p>Sign up as a Talent or Client. Connect your Cardano wallet — it becomes your payment rail and on-chain identity.</p>
        <div class="how-arrow">→</div>
      </div>
      <div class="how-card">
        <span class="how-num">02</span>
        <span class="how-icon">🔍</span>
        <h3>Post or Find a Job</h3>
        <p>Clients post with budgets; talents browse by skill, location, and rate. Digital gigs and artisan work both supported.</p>
        <div class="how-arrow">→</div>
      </div>
      <div class="how-card">
        <span class="how-num">03</span>
        <span class="how-icon">🔐</span>
        <h3>Escrow Funds Safely</h3>
        <p>Client locks funds into a smart contract. Talent sees confirmed escrow before starting. No "trust me" — ever.</p>
        <div class="how-arrow">→</div>
      </div>
      <div class="how-card">
        <span class="how-num">04</span>
        <span class="how-icon">💰</span>
        <h3>Complete & Get Paid</h3>
        <p>Client approves delivery. Funds release instantly. On-chain review builds your permanent reputation. Receive in USD or Naira.</p>
      </div>
    </div>
  </section>

  <!-- FEATURED TALENT -->
  <section class="talent-section">
    <div class="section-label">Featured Talent</div>
    <h2 class="section-h2" style="display:inline;">Meet Nigeria's <em>Best.</em></h2>
    <button class="btn btn-outline" style="margin-left:1.5rem;vertical-align:middle;font-size:.72rem;" onclick="goTo('s-jobs')">Browse All Talent →</button>
    <div class="talent-grid">
      <div class="talent-card" onclick="goTo('s-profile')">
        <div class="talent-card-top" style="background:linear-gradient(135deg,#1a2a4a,#2a1a3a);">
          <div class="talent-card-av" style="background:#1a4a2e;color:#e8a020;">FN</div>
        </div>
        <div class="talent-card-body">
          <div class="talent-card-name">Fatima Nuhu</div>
          <div class="talent-card-role">UI/UX Designer · Lagos</div>
          <div class="talent-card-skills"><span class="chip chip-muted">Figma</span><span class="chip chip-muted">Design Sys</span><span class="chip chip-green">Pro ✓</span></div>
          <div class="talent-card-footer"><div class="tc-rate">$22/hr</div><div class="tc-rating">★ 4.9 <span style="color:var(--muted);font-weight:400;">(47)</span></div></div>
        </div>
      </div>
      <div class="talent-card" onclick="goTo('s-profile')">
        <div class="talent-card-top" style="background:linear-gradient(135deg,#2a1508,#3a2010);">
          <div class="talent-card-av" style="background:#2a1a08;color:#e8a020;">KA</div>
        </div>
        <div class="talent-card-body">
          <div class="talent-card-name">Kola Adeyemi</div>
          <div class="talent-card-role">Master Carpenter · Ibadan</div>
          <div class="talent-card-skills"><span class="chip chip-muted">Furniture</span><span class="chip chip-muted">Cabinets</span><span class="chip chip-green">Verified ✓</span></div>
          <div class="talent-card-footer"><div class="tc-rate">$480/job</div><div class="tc-rating">★ 4.8 <span style="color:var(--muted);font-weight:400;">(32)</span></div></div>
        </div>
      </div>
      <div class="talent-card" onclick="goTo('s-profile')">
        <div class="talent-card-top" style="background:linear-gradient(135deg,#0a1a3a,#0033ad22);">
          <div class="talent-card-av" style="background:#0033ad;color:#fff;">EO</div>
        </div>
        <div class="talent-card-body">
          <div class="talent-card-name">Emeka Obi</div>
          <div class="talent-card-role">Blockchain Dev · Remote</div>
          <div class="talent-card-skills"><span class="chip chip-blue">Plutus</span><span class="chip chip-blue">Aiken</span><span class="chip chip-green">Pro ✓</span></div>
          <div class="talent-card-footer"><div class="tc-rate">$2.8k/contract</div><div class="tc-rating">★ 5.0 <span style="color:var(--muted);font-weight:400;">(18)</span></div></div>
        </div>
      </div>
      <div class="talent-card" onclick="goTo('s-profile')">
        <div class="talent-card-top" style="background:linear-gradient(135deg,#0f2a1a,#17422a);">
          <div class="talent-card-av" style="background:#17422a;color:#5cba6e;">AU</div>
        </div>
        <div class="talent-card-body">
          <div class="talent-card-name">Amara Uche</div>
          <div class="talent-card-role">Virtual Assistant · Abuja</div>
          <div class="talent-card-skills"><span class="chip chip-muted">Admin</span><span class="chip chip-muted">Research</span><span class="chip chip-green">Verified ✓</span></div>
          <div class="talent-card-footer"><div class="tc-rate">$15/hr</div><div class="tc-rating">★ 5.0 <span style="color:var(--muted);font-weight:400;">(28)</span></div></div>
        </div>
      </div>
    </div>
  </section>

  <!-- TRUST / ESCROW -->
  <section class="trust-section">
    <div class="trust-left">
      <div class="trust-eyebrow">Why TechKr is Different</div>
      <h2 class="trust-h2">Built on <em>Trust.</em><br/>Secured by Code.</h2>
      <p class="trust-p">Every payment on TechKr flows through a smart contract. No more chasing clients, no more abandoned projects. The blockchain holds the money — and releases it only when you're satisfied.</p>
      <div class="trust-feats">
        <div class="trust-feat"><div class="trust-feat-icon">🔐</div><div class="trust-feat-text"><strong>Smart Contract Escrow</strong><span>Funds locked before work begins. Released only on your approval. Zero risk, zero drama.</span></div></div>
        <div class="trust-feat"><div class="trust-feat-icon">⬡</div><div class="trust-feat-text"><strong>On-Chain Reputation</strong><span>Every review is permanent and immutable. Your track record can't be faked or deleted.</span></div></div>
        <div class="trust-feat"><div class="trust-feat-icon">💵</div><div class="trust-feat-text"><strong>USD or Naira Payouts</strong><span>Choose your currency. Receive to dollar account or local Nigerian bank — no friction.</span></div></div>
      </div>
    </div>
    <div class="trust-right">
      <div class="escrow-diagram">
        <div class="escrow-title">⬡ Smart Contract Escrow Flow</div>
        <div class="escrow-steps">
          <div class="escrow-step">
            <div class="escrow-step-num" style="background:rgba(212,147,26,.15);color:var(--gold);">1</div>
            <div class="escrow-step-text"><strong>Client Posts & Funds</strong><span>Budget locked into smart contract. Talent sees confirmed funds before starting.</span></div>
          </div>
          <div class="escrow-step">
            <div class="escrow-step-num" style="background:rgba(192,72,32,.15);color:var(--rust);">2</div>
            <div class="escrow-step-text"><strong>Talent Works Safely</strong><span>Work begins with confidence — funds are already secured on-chain.</span></div>
          </div>
          <div class="escrow-step">
            <div class="escrow-step-num" style="background:rgba(92,186,110,.15);color:#5cba6e;">3</div>
            <div class="escrow-step-text"><strong>Delivery & Approval</strong><span>Client reviews and approves. Funds release instantly to talent's account.</span></div>
          </div>
          <div class="escrow-step">
            <div class="escrow-step-num" style="background:rgba(0,51,173,.15);color:#4a9eff;">4</div>
            <div class="escrow-step-text"><strong>On-Chain Review Added</strong><span>Immutable reputation point recorded. Both parties build verified track records.</span></div>
          </div>
        </div>
        <div class="escrow-stat-row">
          <div class="escrow-stat"><span class="escrow-stat-num">$54M+</span><span class="escrow-stat-label">Paid Out</span></div>
          <div class="escrow-stat"><span class="escrow-stat-num">99%</span><span class="escrow-stat-label">Dispute-Free</span></div>
          <div class="escrow-stat"><span class="escrow-stat-num">0</span><span class="escrow-stat-label">Failed Payments</span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- BOTTOM CTA -->
  <section class="cta-section">
    <h2 class="cta-h2">Your Skill.<br/>Your <em>Proof.</em><br/>Your Future.</h2>
    <div class="cta-right">
      <p>Join thousands of Nigerian professionals building verified reputations and earning fairly — whether you write code, build furniture, or manage executives.</p>
      <div class="cta-btns">
        <button class="btn btn-gold" onclick="goTo('s-auth')">Start as Talent →</button>
        <button class="btn btn-ghost-white" onclick="goTo('s-auth')">Hire on TechKr</button>
      </div>
    </div>
  </section>
</div>

<!-- ═══════════════ SCREEN 2: AUTH ═══════════════ -->
<div id="s-auth" class="screen">
  <div style="display:flex;align-items:stretch;min-height:100vh;">
    <div class="auth-left">
      <div>
        <div class="auth-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
        <div class="auth-tagline">Your Work.<br/><em>Paid Fairly.</em></div>
        <p class="auth-sub">Nigeria's first blockchain-powered talent marketplace. Build your reputation. Get paid securely. No middlemen.</p>
      </div>
      <div class="auth-feats">
        <div class="auth-feat"><div class="auth-feat-icon">🔐</div><div class="auth-feat-text"><strong>100% Secure Escrow</strong><span>Funds locked and released only on your approval.</span></div></div>
        <div class="auth-feat"><div class="auth-feat-icon">⬡</div><div class="auth-feat-text"><strong>On-Chain Reputation</strong><span>Verified reviews that can't be deleted or faked — ever.</span></div></div>
        <div class="auth-feat"><div class="auth-feat-icon">💵</div><div class="auth-feat-text"><strong>USD or Naira Payouts</strong><span>Dollar account or any Nigerian bank — your choice.</span></div></div>
      </div>
    </div>
    <div class="auth-right">
      <div class="auth-box">
        <div class="auth-heading">Welcome to TechKr</div>
        <div class="auth-subheading">Join 12,000+ verified professionals</div>
        <div class="auth-tabs">
          <button class="auth-tab active" id="tab-login" onclick="switchAuthTab('login')">Log In</button>
          <button class="auth-tab" id="tab-signup" onclick="switchAuthTab('signup')">Sign Up</button>
        </div>
        <div id="auth-login">
          <div class="auth-form">
            <div class="input-wrap"><div class="input-label">Email address</div><input type="email" class="input-field" placeholder="you@example.com"/></div>
            <div class="input-wrap"><div class="input-label">Password</div><input type="password" class="input-field" placeholder="••••••••"/></div>
            <button class="btn btn-gold" style="width:100%;justify-content:center;" onclick="doLogin()">Continue →</button>
            <div class="auth-divider">or</div>
            <button class="wallet-btn" onclick="doLogin()">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none"><path d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z" fill="#4285F4"/><path d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z" fill="#34A853"/><path d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l3.66-2.84z" fill="#FBBC05"/><path d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z" fill="#EA4335"/></svg>
              Continue with Google
            </button>
          </div>
          <div class="auth-note">Don't have an account? <a onclick="switchAuthTab('signup')">Sign up free</a></div>
        </div>
        <div id="auth-signup" style="display:none;">
          <div class="auth-form">
            <div style="margin-bottom:.25rem;">
              <div class="input-label" style="color:rgba(255,255,255,.4);margin-bottom:.65rem;">I am joining as a...</div>
              <div class="role-pick">
                <div class="role-card selected" id="role-talent" onclick="pickRole('talent')"><div class="role-card-icon">👷</div><div class="role-card-label">Talent</div></div>
                <div class="role-card" id="role-client" onclick="pickRole('client')"><div class="role-card-icon">🏢</div><div class="role-card-label">Client</div></div>
              </div>
            </div>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:.75rem;">
              <div class="input-wrap"><div class="input-label">First name</div><input type="text" class="input-field" placeholder="Fatima"/></div>
              <div class="input-wrap"><div class="input-label">Last name</div><input type="text" class="input-field" placeholder="Nuhu"/></div>
            </div>
            <div class="input-wrap"><div class="input-label">Email address</div><input type="email" class="input-field" placeholder="you@example.com"/></div>
            <div class="input-wrap"><div class="input-label">Password</div><input type="password" class="input-field" placeholder="Min 8 characters"/></div>
            <button class="btn btn-gold" style="width:100%;justify-content:center;" onclick="doSignup()">Create Account →</button>
            <div class="auth-divider">or</div>
            <button class="wallet-btn" onclick="doSignup()">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none"><path d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z" fill="#4285F4"/><path d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z" fill="#34A853"/><path d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l3.66-2.84z" fill="#FBBC05"/><path d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z" fill="#EA4335"/></svg>
              Sign up with Google
            </button>
          </div>
          <div class="auth-note">Already have an account? <a onclick="switchAuthTab('login')">Log in</a></div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ SCREEN 3: DASHBOARD ═══════════════ -->
<div id="s-dashboard" class="screen">
  <nav class="dash-nav">
    <div class="dash-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
    <div class="dash-tabs">
      <button class="dash-tab active" onclick="goTo('s-dashboard')">Home</button>
      <button class="dash-tab" onclick="goTo('s-jobs')">Find Jobs</button>
      <button class="dash-tab" onclick="goTo('s-post')">Post a Job</button>
      <button class="dash-tab" onclick="goTo('s-bounties')">⬡ Bounties</button>
    </div>
    <div class="dash-user" onclick="goTo('s-profile')">
      <div class="dash-avatar" style="background:var(--green);color:var(--gold);">FN</div>
      <div><div class="dash-uname">Fatima Nuhu</div><div class="dash-badge">⬡ Anchor Tier</div></div>
    </div>
  </nav>
  <div class="dash-body">
    <div class="dash-content active" id="dash-home">
      <div class="dash-home">
        <div class="dash-welcome">
          <div><h2>Welcome back, <span>Fatima</span> 👋</h2><p>You have 3 new job matches and 1 pending escrow release.</p></div>
          <div style="display:flex;gap:.75rem;flex-wrap:wrap;">
            <button class="btn btn-gold" onclick="goTo('s-jobs')">Browse Jobs</button>
            <button class="btn btn-ghost-white" onclick="goTo('s-bounties')">⬡ Bounties</button>
          </div>
        </div>
        <div class="dash-stats">
          <div class="stat-card"><span class="stat-card-num">$1,820</span><div class="stat-card-label">Total Earned</div><div class="stat-card-sub">+$269 this week</div></div>
          <div class="stat-card"><span class="stat-card-num">12</span><div class="stat-card-label">Jobs Completed</div><div class="stat-card-sub">3 in progress</div></div>
          <div class="stat-card"><span class="stat-card-num">4.9</span><div class="stat-card-label">Avg. Rating</div><div class="stat-card-sub">On-chain verified</div></div>
          <div class="stat-card"><span class="stat-card-num">78%</span><div class="stat-card-label">To Pro Badge</div><div class="stat-card-sub">22% remaining</div></div>
        </div>
        <div class="dash-two-col">
          <div class="dash-panel">
            <div class="panel-header"><div class="panel-title">Recommended Jobs</div><button class="panel-action" onclick="goTo('s-jobs')">View All →</button></div>
            <div class="mini-job"><div class="mini-job-ico">💻</div><div><div class="mini-job-title">React Frontend Developer</div><div class="mini-job-meta"><span>Remote</span><span>·</span><span>Full-time contract</span></div></div><div class="mini-job-rate">$15/hr</div></div>
            <div class="mini-job"><div class="mini-job-ico">🎨</div><div><div class="mini-job-title">Brand Identity Design</div><div class="mini-job-meta"><span>Lagos</span><span>·</span><span>Fixed price</span></div></div><div class="mini-job-rate">$512</div></div>
            <div class="mini-job"><div class="mini-job-ico">📱</div><div><div class="mini-job-title">Mobile App UI Redesign</div><div class="mini-job-meta"><span>Remote</span><span>·</span><span>Project-based</span></div></div><div class="mini-job-rate">$15/hr</div></div>
          </div>
          <div class="dash-panel">
            <div class="panel-header"><div class="panel-title">Active Escrows</div><button class="panel-action">Manage →</button></div>
            <div class="mini-job"><div class="mini-job-ico" style="background:#fff3cd;">🔐</div><div><div class="mini-job-title">Dashboard UI Kit</div><div class="mini-job-meta"><span>Client: TechStart NG</span><span>·</span><span>Due: 3 days</span></div></div><div class="mini-job-rate" style="color:var(--gold);">$384 locked</div></div>
            <div class="mini-job"><div class="mini-job-ico" style="background:#d4edda;">✅</div><div><div class="mini-job-title">Logo Package</div><div class="mini-job-meta"><span>Client: Adebayo & Sons</span><span>·</span><span>Approved</span></div></div><div class="mini-job-rate" style="color:#5cba6e;">$128 ready</div></div>
          </div>
        </div>
        <div style="margin-top:1.25rem;">
          <div class="dash-panel">
            <div class="panel-header"><div class="panel-title">⬡ Open Cardano Bounties</div><button class="panel-action" onclick="goTo('s-bounties')">All Bounties →</button></div>
            <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--border);">
              <div class="mini-job" style="flex-direction:column;gap:.5rem;"><div style="display:flex;align-items:center;gap:.5rem;"><span>⬡</span><span style="font-size:.62rem;font-weight:600;color:var(--cardano);text-transform:uppercase;letter-spacing:.07em;">MinswapDEX</span></div><div class="mini-job-title" style="font-size:.86rem;">Community Discord Moderator</div><div style="display:flex;gap:.5rem;justify-content:space-between;align-items:center;"><span class="chip chip-blue">30 days</span><span style="font-size:.77rem;font-weight:700;color:var(--green);">₳ 650</span></div></div>
              <div class="mini-job" style="flex-direction:column;gap:.5rem;"><div style="display:flex;align-items:center;gap:.5rem;"><span>⬡</span><span style="font-size:.62rem;font-weight:600;color:var(--cardano);text-transform:uppercase;letter-spacing:.07em;">WingRiders</span></div><div class="mini-job-title" style="font-size:.86rem;">Video Tutorial Creation</div><div style="display:flex;gap:.5rem;justify-content:space-between;align-items:center;"><span class="chip chip-blue">14 days</span><span style="font-size:.77rem;font-weight:700;color:var(--green);">₳ 400</span></div></div>
              <div class="mini-job" style="flex-direction:column;gap:.5rem;"><div style="display:flex;align-items:center;gap:.5rem;"><span>⬡</span><span style="font-size:.62rem;font-weight:600;color:var(--cardano);text-transform:uppercase;letter-spacing:.07em;">IOHK</span></div><div class="mini-job-title" style="font-size:.86rem;">dApp Beta Testing & Feedback</div><div style="display:flex;gap:.5rem;justify-content:space-between;align-items:center;"><span class="chip chip-blue">7 days</span><span style="font-size:.77rem;font-weight:700;color:var(--green);">₳ 180</span></div></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ SCREEN 4: JOBS ═══════════════ -->
<div id="s-jobs" class="screen">
  <nav class="dash-nav">
    <div class="dash-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
    <div class="dash-tabs">
      <button class="dash-tab" onclick="goTo('s-dashboard')">Home</button>
      <button class="dash-tab active">Find Jobs</button>
      <button class="dash-tab" onclick="goTo('s-post')">Post a Job</button>
      <button class="dash-tab" onclick="goTo('s-bounties')">⬡ Bounties</button>
    </div>
    <div class="dash-user" onclick="goTo('s-profile')"><div class="dash-avatar" style="background:var(--green);color:var(--gold);">FN</div><div><div class="dash-uname">Fatima Nuhu</div><div class="dash-badge">⬡ Anchor Tier</div></div></div>
  </nav>
  <div class="jobs-layout">
    <div class="jobs-sidebar">
      <div class="filter-section">
        <div class="search-bar"><input type="text" class="search-input" placeholder="Search jobs…"/><button class="search-btn">⌕</button></div>
      </div>
      <div class="filter-section">
        <div class="filter-title">Category</div>
        <div class="filter-options">
          <div class="filter-opt"><input type="checkbox" id="f1" checked/><label for="f1">Digital / Tech</label><span class="filter-opt-count">248</span></div>
          <div class="filter-opt"><input type="checkbox" id="f2"/><label for="f2">Design / Creative</label><span class="filter-opt-count">91</span></div>
          <div class="filter-opt"><input type="checkbox" id="f3"/><label for="f3">Writing / Content</label><span class="filter-opt-count">64</span></div>
          <div class="filter-opt"><input type="checkbox" id="f4"/><label for="f4">Artisan / Trade</label><span class="filter-opt-count">130</span></div>
          <div class="filter-opt"><input type="checkbox" id="f5"/><label for="f5">Virtual Assistant</label><span class="filter-opt-count">47</span></div>
        </div>
      </div>
      <div class="filter-section">
        <div class="filter-title">Job Type</div>
        <div class="filter-options">
          <div class="filter-opt"><input type="checkbox" id="ft1" checked/><label for="ft1">Remote</label><span class="filter-opt-count">312</span></div>
          <div class="filter-opt"><input type="checkbox" id="ft2" checked/><label for="ft2">On-site</label><span class="filter-opt-count">168</span></div>
          <div class="filter-opt"><input type="checkbox" id="ft3"/><label for="ft3">Hybrid</label><span class="filter-opt-count">54</span></div>
        </div>
      </div>
      <div class="filter-section">
        <div class="filter-title">Rate Range</div>
        <div class="filter-options">
          <div class="filter-opt"><input type="checkbox" id="fr1" checked/><label for="fr1">$10–$20/hr</label></div>
          <div class="filter-opt"><input type="checkbox" id="fr2" checked/><label for="fr2">$20–$50/hr</label></div>
          <div class="filter-opt"><input type="checkbox" id="fr3"/><label for="fr3">$50+/hr</label></div>
          <div class="filter-opt"><input type="checkbox" id="fr4" checked/><label for="fr4">Fixed Price</label></div>
        </div>
      </div>
    </div>
    <div class="jobs-main">
      <div class="jobs-header">
        <div class="jobs-count">580 jobs found</div>
        <button class="btn btn-gold" style="padding:.5rem 1.1rem;font-size:.7rem;" onclick="goTo('s-post')">+ Post a Job</button>
      </div>
      <div class="job-cards">
        <div class="job-card featured" onclick="showJobToast()">
          <div>
            <div class="job-card-top"><span class="job-title">Senior React / Next.js Developer</span><span class="chip chip-rust">Featured</span><span class="chip chip-green">Escrow ✓</span></div>
            <div class="job-company">Orji & Associates · Lagos, Nigeria</div>
            <div class="job-desc">We need an experienced React developer to rebuild our customer portal. Responsive design, API integration, 4–6 week timeline. Must be comfortable with Agile sprints.</div>
            <div class="job-tags"><span class="chip chip-muted">React</span><span class="chip chip-muted">Next.js</span><span class="chip chip-muted">TypeScript</span><span class="chip chip-muted">Remote</span></div>
          </div>
          <div class="job-card-right"><div><div class="job-rate">$15/hr</div><div class="job-type">Hourly · Remote</div></div><button class="btn btn-dark job-apply" style="padding:.5rem .95rem;font-size:.67rem;">Apply →</button></div>
        </div>
        <div class="job-card" onclick="showJobToast()">
          <div>
            <div class="job-card-top"><span class="job-title">UI/UX Designer — Brand Refresh</span><span class="chip chip-green">Escrow ✓</span></div>
            <div class="job-company">NaijaFintech Ltd · Remote</div>
            <div class="job-desc">Complete brand identity refresh including new design system, component library, and onboarding flows. Portfolio of fintech work required.</div>
            <div class="job-tags"><span class="chip chip-muted">Figma</span><span class="chip chip-muted">Design Systems</span><span class="chip chip-muted">Fintech</span></div>
          </div>
          <div class="job-card-right"><div><div class="job-rate">$580</div><div class="job-type">Fixed · Remote</div></div><button class="btn btn-dark job-apply" style="padding:.5rem .95rem;font-size:.67rem;">Apply →</button></div>
        </div>
        <div class="job-card" onclick="showJobToast()">
          <div>
            <div class="job-card-top"><span class="job-title">Master Carpenter — Kitchen Refit</span><span class="chip chip-green">Escrow ✓</span><span class="chip chip-muted">Artisan</span></div>
            <div class="job-company">Private Client · Ibadan, Oyo State</div>
            <div class="job-desc">Full kitchen cabinet installation and custom shelving. Materials partially covered by 50% milestone release. Must provide past work photos and references.</div>
            <div class="job-tags"><span class="chip chip-muted">Carpentry</span><span class="chip chip-muted">Ibadan</span><span class="chip chip-muted">Milestone Pay</span></div>
          </div>
          <div class="job-card-right"><div><div class="job-rate">$770</div><div class="job-type">Milestone · On-site</div></div><button class="btn btn-dark job-apply" style="padding:.5rem .95rem;font-size:.67rem;">Apply →</button></div>
        </div>
        <div class="job-card" onclick="showJobToast()">
          <div>
            <div class="job-card-top"><span class="job-title">Virtual Assistant — Executive Support</span><span class="chip chip-green">Escrow ✓</span></div>
            <div class="job-company">GlobalOps Remote · UK Client</div>
            <div class="job-desc">Calendar management, email handling, research tasks, and client communication for a London-based startup. Fluent English required, 20hrs/week.</div>
            <div class="job-tags"><span class="chip chip-muted">Admin</span><span class="chip chip-muted">Remote</span><span class="chip chip-muted">Long-term</span></div>
          </div>
          <div class="job-card-right"><div><div class="job-rate">$15/hr</div><div class="job-type">Hourly · Remote</div></div><button class="btn btn-dark job-apply" style="padding:.5rem .95rem;font-size:.67rem;">Apply →</button></div>
        </div>
        <div class="job-card" onclick="showJobToast()">
          <div>
            <div class="job-card-top"><span class="job-title">Blockchain Developer — dApp Project</span><span class="chip chip-blue">Blockchain</span><span class="chip chip-green">Escrow ✓</span></div>
            <div class="job-company">DeFi Nigeria · Remote</div>
            <div class="job-desc">Build a staking contract in Plutus/Aiken. Must have prior smart contract experience. 3-week sprint with clear milestone deliverables.</div>
            <div class="job-tags"><span class="chip chip-muted">Plutus</span><span class="chip chip-muted">Aiken</span><span class="chip chip-muted">Haskell</span><span class="chip chip-muted">Remote</span></div>
          </div>
          <div class="job-card-right"><div><div class="job-rate">$2,240</div><div class="job-type">Fixed · Remote</div></div><button class="btn btn-dark job-apply" style="padding:.5rem .95rem;font-size:.67rem;">Apply →</button></div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ SCREEN 5: POST A JOB ═══════════════ -->
<div id="s-post" class="screen">
  <nav class="dash-nav">
    <div class="dash-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
    <div class="dash-tabs">
      <button class="dash-tab" onclick="goTo('s-dashboard')">Home</button>
      <button class="dash-tab" onclick="goTo('s-jobs')">Find Jobs</button>
      <button class="dash-tab active">Post a Job</button>
      <button class="dash-tab" onclick="goTo('s-bounties')">⬡ Bounties</button>
    </div>
    <div class="dash-user" onclick="goTo('s-profile')"><div class="dash-avatar" style="background:var(--green);color:var(--gold);">FN</div><div><div class="dash-uname">Fatima Nuhu</div><div class="dash-badge">⬡ Anchor Tier</div></div></div>
  </nav>
  <div class="post-layout">
    <div class="post-form-area">
      <div class="post-title-main">Post a Job</div>
      <p class="post-sub">Fill in the details. Escrow will be set up automatically when a talent accepts.</p>
      <div class="form-section">
        <div class="form-section-title">Job Details</div>
        <div class="form-row"><div class="input-wrap"><div class="input-label">Job Title</div><input type="text" class="input-field" placeholder="e.g. React Developer for Web App" id="post-title" oninput="updatePreview()"/></div></div>
        <div class="form-row form-row-2">
          <div class="input-wrap"><div class="input-label">Category</div><select class="input-field" id="post-cat" onchange="updatePreview()"><option>Digital / Tech</option><option>Design / Creative</option><option>Writing / Content</option><option>Artisan / Trade</option><option>Virtual Assistant</option><option>Other</option></select></div>
          <div class="input-wrap"><div class="input-label">Job Type</div><select class="input-field" id="post-type" onchange="updatePreview()"><option>Remote</option><option>On-site</option><option>Hybrid</option></select></div>
        </div>
        <div class="form-row"><div class="input-wrap"><div class="input-label">Job Description</div><textarea class="input-field" rows="5" placeholder="Describe the scope of work, requirements, and expectations…"></textarea></div></div>
        <div class="form-row form-row-3">
          <div class="input-wrap"><div class="input-label">Location</div><input type="text" class="input-field" placeholder="Lagos / Remote"/></div>
          <div class="input-wrap"><div class="input-label">Duration</div><select class="input-field"><option>1–2 weeks</option><option>2–4 weeks</option><option>1–3 months</option><option>Ongoing</option></select></div>
          <div class="input-wrap"><div class="input-label">Skills (comma-sep.)</div><input type="text" class="input-field" placeholder="React, Node.js, Figma"/></div>
        </div>
      </div>
      <div class="form-section">
        <div class="form-section-title">Payment & Escrow Setup</div>
        <div class="form-row form-row-2">
          <div class="input-wrap"><div class="input-label">Payment Type</div><select class="input-field" id="post-paytype" onchange="updateEscrow()"><option value="fixed">Fixed Price</option><option value="hourly">Hourly Rate</option><option value="milestone">Milestone (Artisan)</option></select></div>
          <div class="input-wrap"><div class="input-label">Budget (USD $)</div><input type="number" class="input-field" placeholder="e.g. 500" id="post-budget" oninput="updateEscrow()"/></div>
        </div>
        <div class="escrow-visual" id="escrow-visual">
          <div class="escrow-visual-title">⬡ Smart Contract Escrow Flow</div>
          <div class="escrow-flow-row" id="escrow-flow-digital">
            <div class="escrow-node active">You Lock Funds</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">Contract Secured</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">Talent Works</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">You Approve</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">Funds Released</div>
          </div>
          <div class="escrow-flow-row" id="escrow-flow-milestone" style="display:none;">
            <div class="escrow-node active">50% Released</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">Materials Bought</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">Work Done</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">You Approve</div><div class="escrow-arrow">→</div>
            <div class="escrow-node">50% Released</div>
          </div>
          <p style="color:rgba(255,255,255,.32);font-size:.77rem;margin-top:1rem;line-height:1.5;">Funds are held securely in escrow. Talent starts only after seeing confirmed funds. You release payment only when satisfied.</p>
        </div>
      </div>
      <div style="display:flex;gap:.85rem;padding-bottom:3rem;">
        <button class="btn btn-gold" onclick="doPostJob()">Fund Escrow & Publish →</button>
        <button class="btn btn-outline">Save Draft</button>
      </div>
    </div>
    <div class="post-preview-area">
      <div class="preview-label">Live Preview</div>
      <div class="preview-job-card">
        <div class="preview-job-title" id="preview-title">Job Title</div>
        <div class="preview-job-company">Your Company · <span id="preview-type">Remote</span></div>
        <div class="preview-job-tags"><span class="chip chip-green">Escrow Verified ✓</span><span class="chip chip-muted" id="preview-cat">Digital / Tech</span></div>
        <div style="font-size:.8rem;color:var(--muted);line-height:1.55;margin-bottom:1rem;">Job description will appear here once you start typing…</div>
        <div class="preview-escrow-box">
          <div class="preview-escrow-row"><span class="preview-escrow-label">Escrow Budget</span><span class="preview-escrow-val" id="preview-budget">$ —</span></div>
          <div class="preview-escrow-status" id="preview-status">Awaiting fund lock</div>
        </div>
      </div>
      <div style="margin-top:1.25rem;padding:1.1rem;background:var(--lightgreen);border:1px solid rgba(23,66,42,.15);border-radius:var(--r);">
        <div style="font-size:.62rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--green);margin-bottom:.5rem;">Why Escrow?</div>
        <p style="font-size:.8rem;color:var(--green);line-height:1.6;">Talents won't start until funds are secured. You won't lose money to abandoned projects. Every release builds an on-chain trust record.</p>
      </div>
      <div style="margin-top:.85rem;padding:1.1rem;background:rgba(0,51,173,.05);border:1px solid rgba(0,51,173,.15);border-radius:var(--r);">
        <div style="font-size:.62rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--cardano);margin-bottom:.5rem;">⬡ Or post a Cardano Bounty?</div>
        <p style="font-size:.8rem;color:var(--muted);line-height:1.6;margin-bottom:.7rem;">For community tasks, giveaways, or ecosystem work. Wallet required only for bounty claims.</p>
        <button class="btn" style="background:rgba(0,51,173,.1);color:var(--cardano);border:1px solid rgba(0,51,173,.25);padding:.45rem .9rem;font-size:.63rem;" onclick="goTo('s-bounties')">Go to Bounties →</button>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ SCREEN 6: BOUNTIES ═══════════════ -->
<div id="s-bounties" class="screen">
  <nav class="dash-nav">
    <div class="dash-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
    <div class="dash-tabs">
      <button class="dash-tab" onclick="goTo('s-dashboard')">Home</button>
      <button class="dash-tab" onclick="goTo('s-jobs')">Find Jobs</button>
      <button class="dash-tab" onclick="goTo('s-post')">Post a Job</button>
      <button class="dash-tab active">⬡ Bounties</button>
    </div>
    <div class="dash-user" onclick="goTo('s-profile')"><div class="dash-avatar" style="background:var(--green);color:var(--gold);">FN</div><div><div class="dash-uname">Fatima Nuhu</div><div class="dash-badge">⬡ Anchor Tier</div></div></div>
  </nav>
  <div class="bounties-hero">
    <div class="bounties-eyebrow">⬡ Cardano Ecosystem · Powered by TechKr</div>
    <h2>Cardano <em>Bounties</em></h2>
    <p>Cardano projects tap into Nigeria's talent pool for community management, content creation, testing, and micro-tasks. Earn ₳ while learning the ecosystem.</p>
    <div class="bounties-stats">
      <div><span class="b-stat-num">38</span><span class="b-stat-label">Open Bounties</span></div>
      <div><span class="b-stat-num">₳ 12,400</span><span class="b-stat-label">Total Pool</span></div>
      <div><span class="b-stat-num">8</span><span class="b-stat-label">Partner Projects</span></div>
      <div><span class="b-stat-num">$2.1M</span><span class="b-stat-label">Claimed to Date</span></div>
    </div>
  </div>
  <div class="bounties-main">
    <div class="bounties-filter-row">
      <button class="filter-pill active" onclick="activePill(this)">All</button>
      <button class="filter-pill" onclick="activePill(this)">Community</button>
      <button class="filter-pill" onclick="activePill(this)">Development</button>
      <button class="filter-pill" onclick="activePill(this)">Content</button>
      <button class="filter-pill" onclick="activePill(this)">Giveaway</button>
      <button class="filter-pill" onclick="activePill(this)">Beginner</button>
    </div>
    <div class="bounties-grid">
      <div class="bounty-card featured" onclick="showBountyWallet('Community Discord Moderator','₳ 650')">
        <div class="bounty-sponsor"><div class="bounty-sponsor-ico">⬡</div><div class="bounty-sponsor-name">MinswapDEX</div></div>
        <div class="bounty-title">Community Discord Moderator</div>
        <div class="bounty-desc">Moderate the MinswapDEX Discord. Fluent English, active community member, 4hrs/day commitment for 30 days. Nigerian users especially encouraged to apply.</div>
        <div style="display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.7rem;"><span class="chip chip-blue">Community</span><span class="chip chip-muted">30 days</span><span class="chip chip-gold">Featured</span></div>
        <div class="bounty-footer"><span class="bounty-reward">₳ 650</span><span class="bounty-deadline">Closes: 15 Jun</span></div>
      </div>
      <div class="bounty-card featured" onclick="showBountyWallet('DeFi Tutorial Video Series','₳ 1,200')">
        <div class="bounty-sponsor"><div class="bounty-sponsor-ico">⬡</div><div class="bounty-sponsor-name">WingRiders</div></div>
        <div class="bounty-title">DeFi Tutorial Video Series</div>
        <div class="bounty-desc">Create a 5-part YouTube tutorial series on using WingRiders DEX. Must have existing YouTube presence and knowledge of Cardano DeFi basics.</div>
        <div style="display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.7rem;"><span class="chip chip-blue">Content</span><span class="chip chip-muted">14 days</span></div>
        <div class="bounty-footer"><span class="bounty-reward">₳ 1,200</span><span class="bounty-deadline">Closes: 20 Jun</span></div>
      </div>
      <div class="bounty-card" onclick="showBountyWallet('Cardano Node Setup Tutorial','₳ 400')">
        <div class="bounty-sponsor"><div class="bounty-sponsor-ico">⬡</div><div class="bounty-sponsor-name">IOHK</div></div>
        <div class="bounty-title">Cardano Node Setup Tutorial</div>
        <div class="bounty-desc">Write a step-by-step guide on setting up a Cardano node for beginners. Technical writing experience required. Submit PR to official docs repo.</div>
        <div style="display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.7rem;"><span class="chip chip-blue">Development</span><span class="chip chip-muted">7 days</span></div>
        <div class="bounty-footer"><span class="bounty-reward">₳ 400</span><span class="bounty-deadline">Closes: 25 Jun</span></div>
      </div>
      <div class="bounty-card" onclick="showBountyWallet('Yoruba Language Translation','₳ 120')">
        <div class="bounty-sponsor"><div class="bounty-sponsor-ico">⬡</div><div class="bounty-sponsor-name">Cardano Foundation</div></div>
        <div class="bounty-title">Yoruba Language Translation Pack</div>
        <div class="bounty-desc">Translate the Cardano Foundation's 2024 annual report and key docs into Yoruba. Native Yoruba speakers only. Estimated 6,000 words.</div>
        <div style="display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.7rem;"><span class="chip chip-blue">Community</span><span class="chip chip-muted">5 days</span></div>
        <div class="bounty-footer"><span class="bounty-reward">₳ 120</span><span class="bounty-deadline">Closes: 10 Jun</span></div>
      </div>
      <div class="bounty-card" onclick="showBountyWallet('Smart Contract Audit Assistant','$770')">
        <div class="bounty-sponsor"><div class="bounty-sponsor-ico">⬡</div><div class="bounty-sponsor-name">MLabs</div></div>
        <div class="bounty-title">Smart Contract Audit Assistant</div>
        <div class="bounty-desc">Assist senior auditors in reviewing Plutus smart contracts. Must have Haskell and Cardano development experience. 2-week internship format.</div>
        <div style="display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.7rem;"><span class="chip chip-blue">Internship</span><span class="chip chip-muted">Development</span><span class="chip chip-muted">14 days</span></div>
        <div class="bounty-footer"><span class="bounty-reward">$770</span><span class="bounty-deadline">Closes: 1 Jul</span></div>
      </div>
      <div class="bounty-card" onclick="showBountyWallet('Giveaway: First Wallet Setup','₳ 25')">
        <div class="bounty-sponsor"><div class="bounty-sponsor-ico">⬡</div><div class="bounty-sponsor-name">Eternl Wallet</div></div>
        <div class="bounty-title">Giveaway: First Wallet Setup</div>
        <div class="bounty-desc">New to Cardano? Set up an Eternl wallet, stake to a Nigerian pool, and share your staking address. First 50 participants rewarded instantly.</div>
        <div style="display:flex;gap:.4rem;flex-wrap:wrap;margin-bottom:.7rem;"><span class="chip chip-blue">Giveaway</span><span class="chip chip-muted">Beginner</span></div>
        <div class="bounty-footer"><span class="bounty-reward">₳ 25</span><span class="bounty-deadline">50 spots left</span></div>
      </div>
    </div>
    <div style="margin-top:2rem;padding:2.25rem;background:var(--cardano);display:flex;align-items:center;justify-content:space-between;gap:2rem;border-radius:var(--r);flex-wrap:wrap;">
      <div>
        <div style="font-size:.65rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:rgba(255,255,255,.5);margin-bottom:.5rem;">Are you a Cardano project?</div>
        <h3 style="font-family:'Poppins',sans-serif;font-weight:900;font-size:1.85rem;letter-spacing:-.03em;color:#fff;line-height:1.05;">Post a Bounty. <span style="color:var(--gold);">Tap Nigeria.</span></h3>
        <p style="color:rgba(255,255,255,.55);font-size:.87rem;line-height:1.6;max-width:480px;margin-top:.5rem;">List your tasks on TechKr and reach Nigeria's growing talent pool for community work, testing, content, and development tasks.</p>
      </div>
      <button class="btn btn-gold" style="white-space:nowrap;flex-shrink:0;" onclick="showToast('Bounty posting coming soon! 🚀')">Post a Bounty →</button>
    </div>
  </div>
</div>

<!-- ═══════════════ SCREEN 7: PROFILE (NEW) ═══════════════ -->
<div id="s-profile" class="screen">
  <nav class="dash-nav">
    <div class="dash-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
    <div class="dash-tabs">
      <button class="dash-tab" onclick="goTo('s-dashboard')">Home</button>
      <button class="dash-tab" onclick="goTo('s-jobs')">Find Jobs</button>
      <button class="dash-tab" onclick="goTo('s-post')">Post a Job</button>
      <button class="dash-tab" onclick="goTo('s-bounties')">⬡ Bounties</button>
    </div>
    <div class="dash-user" style="color:var(--rust);font-size:.67rem;font-weight:600;letter-spacing:.05em;text-transform:uppercase;cursor:default;">My Profile</div>
  </nav>

  <div class="profile-layout">
    <!-- Sidebar -->
    <div class="profile-sidebar">
      <div class="profile-cover"></div>
      <div class="profile-sidebar-inner">
        <div class="profile-av-wrap">
          <div style="position:relative;">
            <div class="profile-av">FN</div>
            <div class="profile-online"></div>
          </div>
          <button class="profile-edit-btn" onclick="showToast('Edit profile coming soon!')">Edit Profile</button>
        </div>
        <div class="profile-name">Fatima Nuhu</div>
        <div class="profile-title">UI/UX Designer · Product Strategist</div>
        <div class="profile-meta">
          <div class="profile-meta-item">📍 <span>Lagos, Nigeria</span></div>
          <div class="profile-meta-item">🕐 <span>Responds within 2 hours</span></div>
          <div class="profile-meta-item">🌐 <span>English · Hausa · Pidgin</span></div>
          <div class="profile-meta-item">✅ <span>Identity Verified</span></div>
        </div>

        <!-- Badges -->
        <div class="profile-section-title">Badges & Tier</div>
        <div class="profile-badges">
          <div class="profile-badge-item"><div class="profile-badge-icon">⬡</div><div class="profile-badge-text">Anchor Tier<small>Joined platform · 8 months ago</small></div></div>
          <div class="profile-badge-item" style="background:rgba(212,147,26,.07);border-color:rgba(212,147,26,.25);"><div class="profile-badge-icon">🏅</div><div class="profile-badge-text" style="color:#a07010;">78% to Pro Badge<small style="color:var(--muted);">Complete 4 more jobs to unlock</small></div></div>
          <div class="profile-badge-item"><div class="profile-badge-icon">✅</div><div class="profile-badge-text">On-Chain Verified<small>47 reviews · Zero disputes</small></div></div>
        </div>

        <!-- Stats -->
        <div class="profile-section-title">Quick Stats</div>
        <div class="profile-stats-grid">
          <div class="profile-stat"><span class="profile-stat-num" style="color:var(--ink);">$1,820</span><span class="profile-stat-label">Earned</span></div>
          <div class="profile-stat"><span class="profile-stat-num" style="color:var(--rust);">12</span><span class="profile-stat-label">Jobs Done</span></div>
          <div class="profile-stat"><span class="profile-stat-num" style="color:var(--gold);">4.9★</span><span class="profile-stat-label">Rating</span></div>
          <div class="profile-stat"><span class="profile-stat-num" style="color:#5cba6e;">98%</span><span class="profile-stat-label">Job Success</span></div>
        </div>

        <!-- Skills -->
        <div class="profile-section-title">Skills</div>
        <div class="profile-skills">
          <span class="profile-skill">Figma</span><span class="profile-skill">UI Design</span><span class="profile-skill">Prototyping</span><span class="profile-skill">User Research</span><span class="profile-skill">Design Systems</span><span class="profile-skill">Wireframing</span><span class="profile-skill">Mobile UI</span><span class="profile-skill">Usability Testing</span>
        </div>

        <!-- Actions -->
        <button class="btn btn-gold" style="width:100%;justify-content:center;margin-bottom:.65rem;" onclick="goTo('s-jobs')">Browse Jobs</button>
        <button class="btn btn-outline" style="width:100%;justify-content:center;" onclick="goTo('s-payout')">Payout Settings</button>
      </div>
    </div>

    <!-- Main -->
    <div class="profile-main">
      <!-- Tab nav -->
      <div class="profile-main-tabs">
        <button class="profile-main-tab active" onclick="switchProfileTab('overview',this)">Overview</button>
        <button class="profile-main-tab" onclick="switchProfileTab('portfolio',this)">Portfolio</button>
        <button class="profile-main-tab" onclick="switchProfileTab('reviews',this)">Reviews (47)</button>
        <button class="profile-main-tab" onclick="switchProfileTab('earnings',this)">Earnings</button>
      </div>

      <!-- OVERVIEW TAB -->
      <div class="profile-tab-content active" id="tab-overview">
        <!-- Bio -->
        <div style="background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.75rem;margin-bottom:1.5rem;">
          <div style="font-size:.63rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:.9rem;">About Me</div>
          <p style="font-size:.88rem;line-height:1.75;color:var(--ink);">UI/UX Designer with 4+ years of experience creating clean, user-centred digital products for fintech, e-commerce, and SaaS companies. I specialise in taking ideas from concept to high-fidelity prototype, with a particular focus on Nigerian market needs and mobile-first design.</p>
          <p style="font-size:.88rem;line-height:1.75;color:var(--ink);margin-top:.85rem;">When I'm not designing, I'm contributing to open-source design systems and mentoring junior designers in the Lagos tech community.</p>
        </div>

        <!-- Active job -->
        <div style="background:var(--white);border:1px solid var(--border);border-radius:var(--r);overflow:hidden;margin-bottom:1.5rem;">
          <div class="panel-header"><div class="panel-title">Active Contracts</div><span class="chip chip-green">3 In Progress</span></div>
          <div class="mini-job">
            <div class="mini-job-ico" style="background:#fff3cd;">🔐</div>
            <div style="flex:1;min-width:0;">
              <div class="mini-job-title">Dashboard UI Kit — TechStart NG</div>
              <div class="mini-job-meta"><span>Escrow: $384 locked</span><span>·</span><span>Due in 3 days</span></div>
            </div>
            <button class="btn btn-outline" style="padding:.4rem .85rem;font-size:.65rem;flex-shrink:0;" onclick="showToast('Opening contract details...')">View →</button>
          </div>
          <div class="mini-job">
            <div class="mini-job-ico" style="background:#d4edda;">✅</div>
            <div style="flex:1;min-width:0;">
              <div class="mini-job-title">Logo Package — Adebayo & Sons</div>
              <div class="mini-job-meta"><span style="color:#5cba6e;font-weight:600;">$128 ready to release</span><span>·</span><span>Awaiting client approval</span></div>
            </div>
            <button class="btn btn-gold" style="padding:.4rem .85rem;font-size:.65rem;flex-shrink:0;" onclick="showToast('Approval requested!')">Request →</button>
          </div>
          <div class="mini-job">
            <div class="mini-job-ico">📱</div>
            <div style="flex:1;min-width:0;">
              <div class="mini-job-title">Mobile App Redesign — NaijaFintech</div>
              <div class="mini-job-meta"><span>Escrow: $15/hr · 6hrs billed</span><span>·</span><span>Ongoing</span></div>
            </div>
            <button class="btn btn-outline" style="padding:.4rem .85rem;font-size:.65rem;flex-shrink:0;" onclick="showToast('Opening timesheet...')">Log Time →</button>
          </div>
        </div>

        <!-- Quick portfolio preview -->
        <div style="background:var(--white);border:1px solid var(--border);border-radius:var(--r);overflow:hidden;">
          <div class="panel-header"><div class="panel-title">Recent Work</div><button class="panel-action" onclick="switchProfileTab('portfolio',document.querySelector('.profile-main-tab:nth-child(2))'))">View All →</button></div>
          <div style="padding:1.25rem;display:grid;grid-template-columns:repeat(3,1fr);gap:.85rem;">
            <div style="border-radius:var(--rsm);overflow:hidden;cursor:pointer;" onclick="showToast('Opening case study...')">
              <div style="height:80px;background:linear-gradient(135deg,#1a2a4a,#2a1a3a);display:flex;align-items:center;justify-content:center;font-size:1.8rem;">🏦</div>
              <div style="padding:.65rem;background:var(--bg);"><div style="font-size:.8rem;font-weight:600;margin-bottom:.15rem;">Fintech Onboarding</div><div style="font-size:.68rem;color:var(--muted);">UI/UX Design</div></div>
            </div>
            <div style="border-radius:var(--rsm);overflow:hidden;cursor:pointer;" onclick="showToast('Opening case study...')">
              <div style="height:80px;background:linear-gradient(135deg,#0f3020,#1a4a2e);display:flex;align-items:center;justify-content:center;font-size:1.8rem;">🛒</div>
              <div style="padding:.65rem;background:var(--bg);"><div style="font-size:.8rem;font-weight:600;margin-bottom:.15rem;">E-commerce App</div><div style="font-size:.68rem;color:var(--muted);">Mobile Design</div></div>
            </div>
            <div style="border-radius:var(--rsm);overflow:hidden;cursor:pointer;" onclick="showToast('Opening case study...')">
              <div style="height:80px;background:linear-gradient(135deg,#2a1508,#3a2010);display:flex;align-items:center;justify-content:center;font-size:1.8rem;">📊</div>
              <div style="padding:.65rem;background:var(--bg);"><div style="font-size:.8rem;font-weight:600;margin-bottom:.15rem;">SaaS Dashboard</div><div style="font-size:.68rem;color:var(--muted);">Design System</div></div>
            </div>
          </div>
        </div>
      </div>

      <!-- PORTFOLIO TAB -->
      <div class="profile-tab-content" id="tab-portfolio">
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:1.5rem;">
          <div style="font-size:.88rem;color:var(--muted);">12 projects · 4 categories</div>
          <button class="btn btn-outline" style="padding:.45rem 1rem;font-size:.68rem;" onclick="showToast('Portfolio upload coming soon!')">+ Add Work</button>
        </div>
        <div class="portfolio-grid">
          <div class="portfolio-item" onclick="showToast('Opening case study...')"><div class="portfolio-thumb" style="background:linear-gradient(135deg,#1a2a4a,#2a1a3a);">🏦</div><div class="portfolio-info"><div class="portfolio-info-title">Fintech Onboarding Flow</div><div class="portfolio-info-cat">UI/UX · 2024</div></div></div>
          <div class="portfolio-item" onclick="showToast('Opening case study...')"><div class="portfolio-thumb" style="background:linear-gradient(135deg,#0f3020,#1a4a2e);">🛒</div><div class="portfolio-info"><div class="portfolio-info-title">E-commerce Mobile App</div><div class="portfolio-info-cat">Mobile Design · 2024</div></div></div>
          <div class="portfolio-item" onclick="showToast('Opening case study...')"><div class="portfolio-thumb" style="background:linear-gradient(135deg,#2a1508,#3a2010);">📊</div><div class="portfolio-info"><div class="portfolio-info-title">SaaS Analytics Dashboard</div><div class="portfolio-info-cat">Design System · 2023</div></div></div>
          <div class="portfolio-item" onclick="showToast('Opening case study...')"><div class="portfolio-thumb" style="background:linear-gradient(135deg,#1a1040,#2a0a5a);">🎨</div><div class="portfolio-info"><div class="portfolio-info-title">Brand Identity — Startup</div><div class="portfolio-info-cat">Brand Design · 2023</div></div></div>
          <div class="portfolio-item" onclick="showToast('Opening case study...')"><div class="portfolio-thumb" style="background:linear-gradient(135deg,#0a2a3a,#0033ad22);">📱</div><div class="portfolio-info"><div class="portfolio-info-title">Crypto Wallet UI</div><div class="portfolio-info-cat">Mobile UI · 2023</div></div></div>
          <div class="portfolio-item" onclick="showToast('Opening case study...')"><div class="portfolio-thumb" style="background:linear-gradient(135deg,#1a3010,#2a5020);">🏥</div><div class="portfolio-info"><div class="portfolio-info-title">Health App Redesign</div><div class="portfolio-info-cat">UX Research · 2023</div></div></div>
        </div>
      </div>

      <!-- REVIEWS TAB -->
      <div class="profile-tab-content" id="tab-reviews">
        <div style="display:flex;align-items:center;gap:2rem;margin-bottom:2rem;padding:1.5rem;background:var(--white);border:1px solid var(--border);border-radius:var(--r);">
          <div style="text-align:center;flex-shrink:0;">
            <div style="font-family:'Poppins',sans-serif;font-size:3.5rem;font-weight:900;color:var(--ink);letter-spacing:-.04em;line-height:1;">4.9</div>
            <div style="color:var(--gold);font-size:1.2rem;margin:.25rem 0;">★★★★★</div>
            <div style="font-size:.7rem;font-weight:500;color:var(--muted);">47 reviews</div>
          </div>
          <div style="flex:1;">
            <div style="display:flex;flex-direction:column;gap:.4rem;">
              <div style="display:flex;align-items:center;gap:.75rem;"><span style="font-size:.72rem;color:var(--muted);width:20px;">5★</span><div style="flex:1;height:6px;background:var(--border);border-radius:3px;"><div style="width:87%;height:100%;background:var(--gold);border-radius:3px;"></div></div><span style="font-size:.72rem;color:var(--muted);width:30px;">41</span></div>
              <div style="display:flex;align-items:center;gap:.75rem;"><span style="font-size:.72rem;color:var(--muted);width:20px;">4★</span><div style="flex:1;height:6px;background:var(--border);border-radius:3px;"><div style="width:10%;height:100%;background:var(--sand);border-radius:3px;"></div></div><span style="font-size:.72rem;color:var(--muted);width:30px;">5</span></div>
              <div style="display:flex;align-items:center;gap:.75rem;"><span style="font-size:.72rem;color:var(--muted);width:20px;">3★</span><div style="flex:1;height:6px;background:var(--border);border-radius:3px;"><div style="width:2%;height:100%;background:var(--sand);border-radius:3px;"></div></div><span style="font-size:.72rem;color:var(--muted);width:30px;">1</span></div>
            </div>
          </div>
        </div>
        <div class="review-list">
          <div class="review-card">
            <div class="review-header">
              <div class="review-user"><div class="review-av" style="background:#1a3a5c;color:#fff;">TO</div><div><div class="review-username">TechStart NG</div><div class="review-meta">Feb 2024 · 3-week project</div></div></div>
              <div class="review-stars">★★★★★</div>
            </div>
            <div class="review-text">Fatima absolutely delivered beyond expectations. The dashboard UI kit was stunning, well-documented, and she communicated every step of the way. Will definitely hire again for our next sprint.</div>
            <span class="review-job-tag">Dashboard UI Kit</span>
          </div>
          <div class="review-card">
            <div class="review-header">
              <div class="review-user"><div class="review-av" style="background:#2a1508;color:#e8a020;">AB</div><div><div class="review-username">Adebayo & Sons</div><div class="review-meta">Jan 2024 · Fixed price</div></div></div>
              <div class="review-stars">★★★★★</div>
            </div>
            <div class="review-text">She understood exactly what our brand needed. Professional, fast, and her design sensibility is world-class. The logo package she delivered has gotten us so many compliments. Highly recommend.</div>
            <span class="review-job-tag">Logo Package</span>
          </div>
          <div class="review-card">
            <div class="review-header">
              <div class="review-user"><div class="review-av" style="background:#0f3020;color:#5cba6e;">GO</div><div><div class="review-username">GlobalOps Remote</div><div class="review-meta">Dec 2023 · Long-term</div></div></div>
              <div class="review-stars">★★★★☆</div>
            </div>
            <div class="review-text">Great work on the mobile app redesign. Fatima is thorough and detail-oriented. Took a little time getting familiar with our codebase constraints, but once she did, the output was excellent.</div>
            <span class="review-job-tag">Mobile App UI Redesign</span>
          </div>
        </div>
      </div>

      <!-- EARNINGS TAB -->
      <div class="profile-tab-content" id="tab-earnings">
        <div class="earnings-section">
          <div style="background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.75rem;margin-bottom:1.25rem;">
            <div class="earnings-header">
              <div class="earnings-total">$1,820</div>
              <div class="earnings-change">+$269 this week</div>
            </div>
            <div style="font-size:.8rem;color:var(--muted);margin-bottom:1.5rem;">Total earnings since joining TechKr · Aug 2023</div>
            <div class="chart-bars">
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:30%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:45%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:25%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:60%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:40%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:75%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar" style="height:55%;"></div></div>
              <div class="chart-bar-wrap"><div class="chart-bar current" style="height:85%;"></div></div>
            </div>
            <div class="chart-months">
              <div class="chart-month">Sep</div><div class="chart-month">Oct</div><div class="chart-month">Nov</div><div class="chart-month">Dec</div><div class="chart-month">Jan</div><div class="chart-month">Feb</div><div class="chart-month">Mar</div><div class="chart-month">Apr</div>
            </div>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1.25rem;">
            <div style="background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.25rem;">
              <div style="font-size:.63rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--muted);margin-bottom:.5rem;">Pending Release</div>
              <div style="font-family:'Poppins',sans-serif;font-size:1.8rem;font-weight:800;color:var(--gold);letter-spacing:-.03em;">$512</div>
              <div style="font-size:.78rem;color:var(--muted);margin-top:.3rem;">2 contracts in escrow</div>
            </div>
            <div style="background:var(--white);border:1px solid var(--border);border-radius:var(--r);padding:1.25rem;">
              <div style="font-size:.63rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;color:var(--muted);margin-bottom:.5rem;">Available to Withdraw</div>
              <div style="font-family:'Poppins',sans-serif;font-size:1.8rem;font-weight:800;color:#5cba6e;letter-spacing:-.03em;">$128</div>
              <div style="font-size:.78rem;color:var(--muted);margin-top:.3rem;">Logo Package — approved</div>
            </div>
          </div>
          <button class="btn btn-gold" style="width:100%;justify-content:center;" onclick="goTo('s-payout')">Withdraw Earnings →</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ SCREEN 8: PAYOUT ═══════════════ -->
<div id="s-payout" class="screen">
  <div style="display:flex;align-items:stretch;min-height:100vh;background:var(--ink);">
    <div class="auth-left" style="background:#1a3a14;">
      <div>
        <div class="auth-logo" onclick="goTo('s-landing')">Tech<span class="kr">Kr</span></div>
        <div class="auth-tagline">Choose How<br/><em>You Get Paid.</em></div>
        <p class="auth-sub">All jobs on TechKr are priced in USD. You decide how to receive your earnings — straight to your dollar account or converted to Naira.</p>
      </div>
      <div class="auth-feats">
        <div class="auth-feat"><div class="auth-feat-icon">💵</div><div class="auth-feat-text"><strong>Dollar Account</strong><span>Receive USD directly to your domiciliary account. Great for building FX savings.</span></div></div>
        <div class="auth-feat"><div class="auth-feat-icon">🏦</div><div class="auth-feat-text"><strong>Naira — Local Bank</strong><span>We convert at the day's rate and send to any Nigerian bank account.</span></div></div>
        <div class="auth-feat"><div class="auth-feat-icon">🔄</div><div class="auth-feat-text"><strong>Change Anytime</strong><span>Update your payout preference from profile settings at any time.</span></div></div>
      </div>
    </div>
    <div class="auth-right">
      <div class="auth-box" style="max-width:460px;">
        <div style="margin-bottom:2rem;">
          <div style="font-size:.67rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:rgba(255,255,255,.3);margin-bottom:.55rem;">Step 2 of 2 — Payout Setup</div>
          <div style="font-family:'Poppins',sans-serif;font-weight:900;font-size:1.9rem;letter-spacing:-.04em;color:#fff;line-height:1.1;">How do you want to receive your earnings?</div>
        </div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:2rem;">
          <div class="role-card selected" id="pay-usd" onclick="pickPayout('usd')" style="padding:1.4rem;text-align:left;">
            <div style="font-size:1.7rem;margin-bottom:.55rem;">💵</div>
            <div class="role-card-label" style="color:var(--gold);">USD Dollar</div>
            <div style="font-size:.78rem;color:rgba(255,255,255,.4);line-height:1.5;margin-top:.3rem;">Domiciliary or international account</div>
          </div>
          <div class="role-card" id="pay-ngn" onclick="pickPayout('ngn')" style="padding:1.4rem;text-align:left;">
            <div style="font-size:1.7rem;margin-bottom:.55rem;">🏦</div>
            <div class="role-card-label">Nigerian Naira</div>
            <div style="font-size:.78rem;color:rgba(255,255,255,.4);line-height:1.5;margin-top:.3rem;">Any local Nigerian bank account</div>
          </div>
        </div>
        <div id="fields-usd" style="display:flex;flex-direction:column;gap:1rem;margin-bottom:1.4rem;">
          <div class="input-wrap"><div class="input-label">Bank Name</div><input type="text" class="input-field" placeholder="e.g. GTBank, Access, Zenith" style="background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;"/></div>
          <div class="input-wrap"><div class="input-label">Dollar Account Number</div><input type="text" class="input-field" placeholder="IBAN or Domiciliary number" style="background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;"/></div>
          <div class="input-wrap"><div class="input-label">Account Name</div><input type="text" class="input-field" placeholder="As it appears on the account" style="background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;"/></div>
        </div>
        <div id="fields-ngn" style="display:none;flex-direction:column;gap:1rem;margin-bottom:1.4rem;">
          <div style="padding:.85rem 1rem;background:rgba(212,147,26,.08);border:1px solid rgba(212,147,26,.2);font-size:.8rem;color:rgba(255,255,255,.5);line-height:1.6;border-radius:var(--rsm);">💡 Your USD earnings will be converted to Naira at the <strong style="color:var(--gold);">current official exchange rate</strong> on the day of release and sent within 1–2 business days.</div>
          <div class="input-wrap"><div class="input-label">Bank Name</div><select class="input-field" style="background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;"><option style="background:#0d0c0a;">Select your bank</option><option style="background:#0d0c0a;">Access Bank</option><option style="background:#0d0c0a;">First Bank Nigeria</option><option style="background:#0d0c0a;">GTBank</option><option style="background:#0d0c0a;">UBA</option><option style="background:#0d0c0a;">Zenith Bank</option><option style="background:#0d0c0a;">Opay</option><option style="background:#0d0c0a;">Palmpay</option><option style="background:#0d0c0a;">Kuda Bank</option><option style="background:#0d0c0a;">Other</option></select></div>
          <div class="input-wrap"><div class="input-label">Account Number</div><input type="text" class="input-field" placeholder="10-digit NUBAN number" maxlength="10" style="background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;"/></div>
          <div class="input-wrap"><div class="input-label">Account Name</div><input type="text" class="input-field" placeholder="Auto-filled after account number" style="background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.12);color:#fff;"/></div>
        </div>
        <button class="btn btn-gold" style="width:100%;justify-content:center;" onclick="doPayoutSave()">Save & Go to Dashboard →</button>
        <div class="auth-note" style="margin-top:.85rem;">You can update payout details anytime in <a onclick="goTo('s-profile')">Profile Settings</a></div>
      </div>
    </div>
  </div>
</div>

<script>
// NAVIGATION
function goTo(id){
  document.querySelectorAll('.screen').forEach(s=>{
    s.classList.remove('active');
    s.style.transform='translateY(14px)';
  });
  const el=document.getElementById(id);
  if(el){
    setTimeout(()=>{el.style.transform='';el.classList.add('active');el.scrollTop=0;},10);
  }
  // close mobile menu
  document.getElementById('mob-menu').classList.remove('open');
}

// MOBILE NAV
function toggleMob(){document.getElementById('mob-menu').classList.toggle('open');}

// AUTH
function switchAuthTab(tab){
  document.getElementById('auth-login').style.display=tab==='login'?'block':'none';
  document.getElementById('auth-signup').style.display=tab==='signup'?'block':'none';
  document.getElementById('tab-login').classList.toggle('active',tab==='login');
  document.getElementById('tab-signup').classList.toggle('active',tab==='signup');
}
function pickRole(role){
  document.getElementById('role-talent').classList.toggle('selected',role==='talent');
  document.getElementById('role-client').classList.toggle('selected',role==='client');
}
function doLogin(){showToast('Welcome back, Fatima! 👋');setTimeout(()=>goTo('s-dashboard'),800);}
function doSignup(){showToast('Account created! Setting up payout details. 💵');setTimeout(()=>goTo('s-payout'),800);}

// PROFILE TABS
function switchProfileTab(tab,btn){
  document.querySelectorAll('.profile-main-tab').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.profile-tab-content').forEach(c=>c.classList.remove('active'));
  if(btn) btn.classList.add('active');
  const el=document.getElementById('tab-'+tab);
  if(el) el.classList.add('active');
}

// POST JOB PREVIEW
function updatePreview(){
  const title=document.getElementById('post-title')?.value||'Job Title';
  const cat=document.getElementById('post-cat')?.value||'Digital / Tech';
  const type=document.getElementById('post-type')?.value||'Remote';
  if(document.getElementById('preview-title')){
    document.getElementById('preview-title').textContent=title||'Job Title';
    document.getElementById('preview-cat').textContent=cat;
    document.getElementById('preview-type').textContent=type;
  }
}
function updateEscrow(){
  const paytype=document.getElementById('post-paytype')?.value;
  const budget=document.getElementById('post-budget')?.value;
  const digital=document.getElementById('escrow-flow-digital');
  const milestone=document.getElementById('escrow-flow-milestone');
  if(paytype==='milestone'){digital.style.display='none';milestone.style.display='flex';}
  else{digital.style.display='flex';milestone.style.display='none';}
  if(document.getElementById('preview-budget')){
    document.getElementById('preview-budget').textContent=budget?'$'+Number(budget).toLocaleString():'$ —';
    document.getElementById('preview-status').textContent=budget?'Ready to lock escrow':'Awaiting fund lock';
  }
}
function doPostJob(){
  const title=document.getElementById('post-title')?.value;
  if(!title){showToast('Please enter a job title first!');return;}
  showToast('Job posted & escrow funded! Talent can now see your listing. 🎉');
  setTimeout(()=>goTo('s-jobs'),1000);
}

// BOUNTIES
function activePill(btn){document.querySelectorAll('.filter-pill').forEach(p=>p.classList.remove('active'));btn.classList.add('active');}
function showBountyWallet(name,reward){
  const existing=document.getElementById('bounty-modal');
  if(existing)existing.remove();
  const modal=document.createElement('div');
  modal.id='bounty-modal';
  modal.style.cssText='position:fixed;inset:0;background:rgba(0,0,0,.78);z-index:9998;display:flex;align-items:center;justify-content:center;padding:2rem;';
  modal.innerHTML=`
    <div style="background:#0d0c0a;border:1px solid rgba(255,255,255,.1);border-top:4px solid #0033ad;max-width:440px;width:100%;padding:2.5rem;position:relative;border-radius:0 0 10px 10px;">
      <button onclick="document.getElementById('bounty-modal').remove()" style="position:absolute;top:1rem;right:1rem;background:none;border:none;color:rgba(255,255,255,.3);font-size:1.2rem;cursor:pointer;">✕</button>
      <div style="font-size:.62rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:#0033ad;margin-bottom:1.2rem;display:flex;align-items:center;gap:.5rem;"><span>⬡</span> Cardano Bounty Application</div>
      <div style="font-family:'Poppins',sans-serif;font-weight:800;font-size:1.45rem;letter-spacing:-.03em;color:#fff;line-height:1.15;margin-bottom:.45rem;">${name}</div>
      <div style="font-size:.78rem;font-weight:600;color:var(--gold);margin-bottom:1.4rem;">Reward: ${reward}</div>
      <div style="background:rgba(0,51,173,.08);border:1px solid rgba(0,51,173,.2);padding:1rem;margin-bottom:1.4rem;border-radius:6px;">
        <div style="font-size:.62rem;font-weight:600;letter-spacing:.09em;text-transform:uppercase;color:rgba(255,255,255,.35);margin-bottom:.45rem;">Why connect a wallet?</div>
        <p style="font-size:.8rem;color:rgba(255,255,255,.48);line-height:1.6;">Cardano bounty rewards are paid in ₳ ADA directly to your Cardano wallet. A wallet is only required for bounty claims — not for regular TechKr jobs.</p>
      </div>
      <button onclick="connectWallet('${name}')" style="width:100%;padding:.9rem;background:#0033ad;color:#fff;border:none;font-size:.73rem;font-weight:600;letter-spacing:.06em;text-transform:uppercase;cursor:pointer;display:flex;align-items:center;justify-content:center;gap:.6rem;margin-bottom:.7rem;border-radius:6px;">⬡ Connect Cardano Wallet & Apply</button>
      <div style="font-size:.61rem;font-weight:500;letter-spacing:.06em;text-transform:uppercase;color:rgba(255,255,255,.2);text-align:center;">Supports: Nami · Eternl · Flint · Typhon</div>
    </div>`;
  document.body.appendChild(modal);
  modal.addEventListener('click',e=>{if(e.target===modal)modal.remove();});
}
function connectWallet(name){document.getElementById('bounty-modal')?.remove();showToast(`Wallet connected! Application submitted for "${name}" ⬡`);}
function showJobToast(){showToast('Opening job details... Apply with one click! 🚀');}

// PAYOUT
function pickPayout(type){
  document.getElementById('pay-usd').classList.toggle('selected',type==='usd');
  document.getElementById('pay-ngn').classList.toggle('selected',type==='ngn');
  document.getElementById('fields-usd').style.display=type==='usd'?'flex':'none';
  document.getElementById('fields-ngn').style.display=type==='ngn'?'flex':'none';
  if(type==='ngn')document.getElementById('fields-ngn').style.flexDirection='column';
}
function doPayoutSave(){showToast('Payout details saved! Welcome to TechKr 🎉');setTimeout(()=>goTo('s-dashboard'),900);}

// TOAST
function showToast(msg){
  const ex=document.querySelector('.toast');if(ex)ex.remove();
  const t=document.createElement('div');t.className='toast';t.textContent=msg;
  document.body.appendChild(t);setTimeout(()=>t.remove(),3200);
}

// Hero cat click
document.querySelectorAll('.hero-cat').forEach(c=>{c.addEventListener('click',()=>{document.querySelectorAll('.hero-cat').forEach(x=>x.classList.remove('active'));c.classList.add('active');});});
</script>
</body>
</html>
