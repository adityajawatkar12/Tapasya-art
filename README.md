<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Tapasya arT – Where Art Meets Soul</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@400;700;900&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Noto+Sans+Devanagari:wght@300;400;600;700&display=swap" rel="stylesheet"/>
<style>
  :root{
    --soil:#3d2b1f;
    --bark:#5c3d2e;
    --clay:#a0522d;
    --terracotta:#c1440e;
    --sand:#d4a96a;
    --cream:#f5ead7;
    --parchment:#ede0c4;
    --gold:#c8963c;
    --moss:#556b2f;
    --ash:#8b7355;
    --white:#fdf6ec;
    --text-dark:#2a1a0e;
    --text-mid:#5c3d2e;
    --shadow:rgba(61,43,31,0.35);
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--cream);
    color:var(--text-dark);
    font-family:'Cormorant Garamond',serif;
    overflow-x:hidden;
    cursor:none;
  }
 
  /* ── CUSTOM CURSOR ── */
  #cursor{
    position:fixed;width:14px;height:14px;
    background:var(--terracotta);
    border-radius:50%;pointer-events:none;
    z-index:99999;transform:translate(-50%,-50%);
    transition:transform .12s ease,width .2s,height .2s,background .2s;
    mix-blend-mode:multiply;
  }
  #cursor-ring{
    position:fixed;width:40px;height:40px;
    border:2px solid var(--gold);
    border-radius:50%;pointer-events:none;
    z-index:99998;transform:translate(-50%,-50%);
    transition:transform .35s cubic-bezier(.23,1,.32,1),width .3s,height .3s;
  }
  body:hover #cursor{width:18px;height:18px;}
 
  /* ── LOADER ── */
  #loader{
    position:fixed;inset:0;z-index:9999;
    background:var(--soil);
    display:flex;flex-direction:column;align-items:center;justify-content:center;
    transition:opacity .8s ease,visibility .8s ease;
  }
  #loader.hide{opacity:0;visibility:hidden;}
  .loader-logo{
    font-family:'Cinzel Decorative',serif;
    font-size:2.8rem;color:var(--gold);
    letter-spacing:.15em;
    animation:pulseLogo 1.5s ease-in-out infinite alternate;
  }
  .loader-bar{
    width:280px;height:3px;background:rgba(255,255,255,.15);
    margin-top:2rem;border-radius:2px;overflow:hidden;
  }
  .loader-fill{height:100%;background:var(--gold);animation:loadFill 2s ease forwards;}
  @keyframes pulseLogo{from{opacity:.6;transform:scale(.97)}to{opacity:1;transform:scale(1.03)}}
  @keyframes loadFill{from{width:0}to{width:100%}}
  .loader-sub{font-family:'Noto Sans Devanagari',sans-serif;color:var(--sand);font-size:.9rem;margin-top:1rem;letter-spacing:.2em;}
 
  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar{width:6px;}
  ::-webkit-scrollbar-track{background:var(--cream);}
  ::-webkit-scrollbar-thumb{background:var(--clay);border-radius:3px;}
 
  /* ── NAV ── */
  nav{
    position:fixed;top:0;left:0;right:0;z-index:1000;
    padding:1rem 4%;
    display:flex;align-items:center;justify-content:space-between;
    background:rgba(61,43,31,.92);
    backdrop-filter:blur(14px);
    border-bottom:1px solid rgba(200,150,60,.2);
    transition:all .3s ease;
  }
  nav.scrolled{padding:.7rem 4%;box-shadow:0 4px 30px var(--shadow);}
  .nav-logo{
    font-family:'Cinzel Decorative',serif;
    font-size:1.4rem;color:var(--gold);
    letter-spacing:.1em;text-decoration:none;
    display:flex;align-items:center;gap:.6rem;
  }
  .nav-logo span{color:var(--cream);}
  .nav-links{display:flex;gap:2rem;list-style:none;}
  .nav-links a{
    color:var(--sand);font-size:.95rem;text-decoration:none;
    letter-spacing:.08em;transition:color .3s;
    font-family:'Cormorant Garamond',serif;font-weight:600;
    position:relative;
  }
  .nav-links a::after{
    content:'';position:absolute;bottom:-3px;left:0;width:0;height:1px;
    background:var(--gold);transition:width .3s;
  }
  .nav-links a:hover{color:var(--gold);}
  .nav-links a:hover::after{width:100%;}
  .nav-cta{
    background:var(--terracotta);color:var(--cream);
    padding:.55rem 1.4rem;border-radius:3px;text-decoration:none;
    font-size:.9rem;letter-spacing:.1em;font-family:'Cinzel Decorative',serif;
    transition:all .3s;border:1px solid var(--terracotta);
  }
  .nav-cta:hover{background:transparent;color:var(--terracotta);}
  .hamburger{display:none;flex-direction:column;gap:5px;cursor:pointer;}
  .hamburger span{display:block;width:24px;height:2px;background:var(--gold);}
 
  /* ── HERO ── */
  #hero{
    min-height:100vh;
    background:linear-gradient(135deg,var(--soil) 0%,#2a1506 40%,#4a2510 100%);
    display:flex;align-items:center;justify-content:center;
    position:relative;overflow:hidden;padding:8rem 4% 4rem;
  }
  .hero-canvas{
    position:absolute;inset:0;
    background:url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23c8963c' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }
  .floating-orbs{position:absolute;inset:0;pointer-events:none;}
  .orb{
    position:absolute;border-radius:50%;filter:blur(80px);
    animation:floatOrb 8s ease-in-out infinite alternate;
  }
  .orb1{width:500px;height:500px;background:rgba(193,68,14,.12);top:-10%;right:-10%;}
  .orb2{width:400px;height:400px;background:rgba(200,150,60,.1);bottom:-10%;left:-5%;animation-delay:-3s;}
  .orb3{width:300px;height:300px;background:rgba(85,107,47,.08);top:40%;left:30%;animation-delay:-5s;}
  @keyframes floatOrb{from{transform:translate(0,0) scale(1)}to{transform:translate(30px,20px) scale(1.05)}}
 
  .hero-content{
    text-align:center;z-index:2;max-width:900px;
    animation:heroEnter 1.4s cubic-bezier(.22,1,.36,1) forwards;
    opacity:0;transform:translateY(40px);
  }
  @keyframes heroEnter{to{opacity:1;transform:translateY(0)}}
  .hero-eyebrow{
    font-family:'Noto Sans Devanagari',sans-serif;
    color:var(--gold);font-size:1rem;letter-spacing:.4em;
    text-transform:uppercase;margin-bottom:1.5rem;
    display:flex;align-items:center;justify-content:center;gap:1rem;
  }
  .hero-eyebrow::before,.hero-eyebrow::after{content:'';flex:1;max-width:80px;height:1px;background:var(--gold);opacity:.5;}
  .hero-title{
    font-family:'Cinzel Decorative',serif;
    font-size:clamp(3rem,8vw,7rem);
    color:var(--cream);line-height:1;
    text-shadow:0 0 60px rgba(200,150,60,.3);
  }
  .hero-title .art{color:var(--gold);}
  .hero-tagline{
    font-size:clamp(1.1rem,2.5vw,1.6rem);
    color:var(--sand);font-style:italic;margin-top:1rem;
    font-weight:300;letter-spacing:.05em;
  }
  .hero-marathi{
    font-family:'Noto Sans Devanagari',sans-serif;
    color:var(--sand);font-size:1.1rem;margin-top:.5rem;opacity:.8;
  }
  .hero-btns{display:flex;gap:1.5rem;justify-content:center;flex-wrap:wrap;margin-top:3rem;}
  .btn-primary{
    padding:1rem 2.5rem;background:var(--terracotta);
    color:var(--cream);border:none;border-radius:4px;
    font-family:'Cinzel Decorative',serif;font-size:.9rem;
    letter-spacing:.12em;cursor:pointer;text-decoration:none;
    display:inline-block;transition:all .3s;
    box-shadow:0 8px 30px rgba(193,68,14,.4);
    transform-style:preserve-3d;
  }
  .btn-primary:hover{transform:translateY(-3px) rotateX(5deg);box-shadow:0 14px 40px rgba(193,68,14,.5);}
  .btn-outline{
    padding:1rem 2.5rem;background:transparent;
    color:var(--gold);border:1.5px solid var(--gold);
    border-radius:4px;font-family:'Cinzel Decorative',serif;
    font-size:.9rem;letter-spacing:.12em;cursor:pointer;
    text-decoration:none;display:inline-block;transition:all .3s;
  }
  .btn-outline:hover{background:var(--gold);color:var(--soil);}
  .hero-stats{
    display:flex;gap:4rem;justify-content:center;margin-top:4rem;flex-wrap:wrap;
  }
  .stat{text-align:center;}
  .stat-num{
    font-family:'Cinzel Decorative',serif;font-size:2.2rem;
    color:var(--gold);display:block;line-height:1;
  }
  .stat-label{font-size:.85rem;color:var(--sand);letter-spacing:.15em;margin-top:.3rem;}
  .scroll-hint{
    position:absolute;bottom:2rem;left:50%;transform:translateX(-50%);
    display:flex;flex-direction:column;align-items:center;gap:.5rem;
    color:var(--sand);font-size:.8rem;letter-spacing:.2em;
    animation:bounce 2s ease infinite;
  }
  .scroll-hint::after{
    content:'';width:1px;height:50px;background:linear-gradient(var(--gold),transparent);
  }
  @keyframes bounce{0%,100%{transform:translateX(-50%) translateY(0)}50%{transform:translateX(-50%) translateY(8px)}}
 
  /* ── SECTION BASE ── */
  section{padding:6rem 5%;}
  .section-header{text-align:center;margin-bottom:4rem;}
  .section-eyebrow{
    font-family:'Noto Sans Devanagari',sans-serif;
    color:var(--terracotta);font-size:.85rem;letter-spacing:.4em;
    text-transform:uppercase;margin-bottom:.8rem;
  }
  .section-title{
    font-family:'Cinzel Decorative',serif;
    font-size:clamp(1.8rem,4vw,3rem);color:var(--soil);
  }
  .section-line{
    width:60px;height:3px;background:linear-gradient(var(--terracotta),var(--gold));
    margin:.8rem auto 0;border-radius:2px;
  }
 
  /* ── ABOUT ── */
  #about{background:var(--soil);color:var(--cream);}
  #about .section-title{color:var(--cream);}
  #about .section-eyebrow{color:var(--gold);}
  .about-grid{
    display:grid;grid-template-columns:1fr 1fr;gap:5rem;align-items:center;
    max-width:1100px;margin:0 auto;
  }
  .about-visual{
    position:relative;height:480px;
    perspective:800px;
  }
  .about-card{
    position:absolute;border-radius:12px;overflow:hidden;
    box-shadow:0 20px 60px rgba(0,0,0,.5);
    transition:transform .4s;
  }
  .about-card:hover{transform:rotateY(-8deg) rotateX(4deg) scale(1.03);}
  .about-card-main{
    width:75%;height:380px;top:0;left:0;
    background:linear-gradient(145deg,var(--bark),var(--terracotta));
    display:flex;align-items:center;justify-content:center;
    font-size:6rem;
  }
  .about-card-accent{
    width:55%;height:220px;bottom:0;right:0;
    background:linear-gradient(145deg,var(--clay),var(--gold));
    display:flex;align-items:center;justify-content:center;
    font-size:4rem;
  }
  .about-text h3{
    font-family:'Cinzel Decorative',serif;
    font-size:1.6rem;color:var(--gold);margin-bottom:1.2rem;
  }
  .about-text p{
    color:rgba(245,234,215,.8);line-height:1.9;font-size:1.05rem;margin-bottom:1rem;
  }
  .about-text .marathi-quote{
    font-family:'Noto Sans Devanagari',sans-serif;
    font-size:1.1rem;color:var(--sand);font-style:italic;
    border-left:3px solid var(--gold);padding-left:1rem;margin:1.5rem 0;
  }
  .team-cards{display:flex;gap:1.5rem;margin-top:2rem;flex-wrap:wrap;}
  .team-card{
    flex:1;min-width:180px;
    background:rgba(255,255,255,.06);border:1px solid rgba(200,150,60,.2);
    border-radius:10px;padding:1.2rem;text-align:center;
    transition:all .3s;
  }
  .team-card:hover{background:rgba(200,150,60,.1);transform:translateY(-5px);}
  .team-avatar{
    width:70px;height:70px;background:linear-gradient(var(--terracotta),var(--gold));
    border-radius:50%;margin:0 auto 1rem;display:flex;align-items:center;
    justify-content:center;font-size:1.8rem;
  }
  .team-name{font-family:'Cinzel Decorative',serif;font-size:.85rem;color:var(--cream);}
  .team-phone{font-size:.8rem;color:var(--sand);margin-top:.3rem;}
 
  /* ── SERVICES ── */
  #services{background:var(--parchment);}
  .services-grid{
    display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
    gap:2rem;max-width:1200px;margin:0 auto;
  }
  .service-card{
    background:var(--cream);border-radius:14px;padding:2.2rem;
    position:relative;overflow:hidden;transition:all .4s cubic-bezier(.22,1,.36,1);
    border:1px solid rgba(160,82,45,.12);
    transform-style:preserve-3d;
  }
  .service-card::before{
    content:'';position:absolute;inset:0;
    background:linear-gradient(135deg,transparent,rgba(193,68,14,.06));
    opacity:0;transition:opacity .4s;
  }
  .service-card:hover{
    transform:translateY(-10px) rotateX(3deg);
    box-shadow:0 25px 60px rgba(61,43,31,.2);
    border-color:var(--terracotta);
  }
  .service-card:hover::before{opacity:1;}
  .service-icon{
    width:60px;height:60px;background:linear-gradient(135deg,var(--terracotta),var(--gold));
    border-radius:14px;display:flex;align-items:center;justify-content:center;
    font-size:1.8rem;margin-bottom:1.3rem;
    box-shadow:0 8px 20px rgba(193,68,14,.3);
    transition:transform .3s;
  }
  .service-card:hover .service-icon{transform:rotateY(180deg);}
  .service-name{
    font-family:'Cinzel Decorative',serif;font-size:1rem;
    color:var(--soil);margin-bottom:.6rem;
  }
  .service-desc{font-size:.92rem;color:var(--ash);line-height:1.7;}
  .service-price{
    margin-top:1rem;font-family:'Cinzel Decorative',serif;
    font-size:.85rem;color:var(--terracotta);
  }
  .service-tag{
    position:absolute;top:1rem;right:1rem;
    background:var(--terracotta);color:var(--cream);
    font-size:.7rem;padding:.25rem .6rem;border-radius:20px;letter-spacing:.05em;
  }
 
  /* ── PORTFOLIO ── */
  #portfolio{background:var(--soil);}
  #portfolio .section-title{color:var(--cream);}
  #portfolio .section-eyebrow{color:var(--gold);}
  .portfolio-filter{
    display:flex;gap:1rem;justify-content:center;flex-wrap:wrap;margin-bottom:3rem;
  }
  .filter-btn{
    padding:.5rem 1.3rem;border:1px solid rgba(200,150,60,.3);
    background:transparent;color:var(--sand);border-radius:30px;
    cursor:pointer;font-family:'Cormorant Garamond',serif;font-size:.95rem;
    transition:all .3s;letter-spacing:.05em;
  }
  .filter-btn.active,.filter-btn:hover{background:var(--terracotta);color:var(--cream);border-color:var(--terracotta);}
  .portfolio-grid{
    display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));
    gap:1.5rem;max-width:1200px;margin:0 auto;
  }
  .portfolio-item{
    position:relative;border-radius:12px;overflow:hidden;
    aspect-ratio:4/3;cursor:pointer;
    transform-style:preserve-3d;
    transition:transform .5s cubic-bezier(.22,1,.36,1);
  }
  .portfolio-item:hover{transform:scale(1.03) rotateX(2deg);}
  .portfolio-bg{
    width:100%;height:100%;
    display:flex;align-items:center;justify-content:center;
    font-size:4rem;transition:transform .5s;
  }
  .portfolio-item:hover .portfolio-bg{transform:scale(1.1);}
  .portfolio-overlay{
    position:absolute;inset:0;
    background:linear-gradient(to top,rgba(61,43,31,.95),rgba(61,43,31,.4),transparent);
    opacity:0;transition:opacity .4s;
    display:flex;flex-direction:column;justify-content:flex-end;padding:1.5rem;
  }
  .portfolio-item:hover .portfolio-overlay{opacity:1;}
  .portfolio-title{font-family:'Cinzel Decorative',serif;color:var(--cream);font-size:1rem;margin-bottom:.3rem;}
  .portfolio-cat{color:var(--gold);font-size:.8rem;letter-spacing:.1em;}
  .p1{background:linear-gradient(135deg,#8B4513,#A0522D);}
  .p2{background:linear-gradient(135deg,#556B2F,#8FBC8F);}
  .p3{background:linear-gradient(135deg,#704214,#C8963C);}
  .p4{background:linear-gradient(135deg,#2F4F4F,#5F9EA0);}
  .p5{background:linear-gradient(135deg,#8B0000,#DC143C);}
  .p6{background:linear-gradient(135deg,#191970,#4169E1);}
 
  /* ── SHOP ── */
  #shop{background:var(--parchment);}
  .shop-grid{
    display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));
    gap:2rem;max-width:1200px;margin:0 auto;
  }
  .product-card{
    background:var(--cream);border-radius:16px;overflow:hidden;
    border:1px solid rgba(160,82,45,.12);transition:all .4s;
    transform-style:preserve-3d;
  }
  .product-card:hover{transform:translateY(-8px) rotateX(2deg);box-shadow:0 20px 50px rgba(61,43,31,.18);}
  .product-img{
    width:100%;height:200px;
    display:flex;align-items:center;justify-content:center;
    font-size:5rem;position:relative;overflow:hidden;
  }
  .product-badge{
    position:absolute;top:.8rem;left:.8rem;
    background:var(--terracotta);color:var(--cream);
    font-size:.7rem;padding:.2rem .6rem;border-radius:20px;letter-spacing:.05em;
  }
  .product-info{padding:1.5rem;}
  .product-name{font-family:'Cinzel Decorative',serif;font-size:.95rem;color:var(--soil);margin-bottom:.4rem;}
  .product-desc{font-size:.88rem;color:var(--ash);line-height:1.6;margin-bottom:1rem;}
  .product-price{
    display:flex;align-items:center;justify-content:space-between;
  }
  .price{font-family:'Cinzel Decorative',serif;font-size:1.1rem;color:var(--terracotta);}
  .add-btn{
    padding:.4rem 1rem;background:var(--soil);color:var(--cream);
    border:none;border-radius:6px;cursor:pointer;
    font-size:.8rem;letter-spacing:.08em;transition:all .3s;
  }
  .add-btn:hover{background:var(--terracotta);}
  .shop-note{text-align:center;margin-top:2rem;color:var(--ash);font-style:italic;}
 
  /* ── BOOKING ── */
  #booking{
    background:linear-gradient(135deg,var(--soil) 0%,#2a1506 100%);
    color:var(--cream);
  }
  #booking .section-title{color:var(--cream);}
  #booking .section-eyebrow{color:var(--gold);}
  .booking-wrap{
    display:grid;grid-template-columns:1fr 1fr;gap:4rem;
    max-width:1100px;margin:0 auto;align-items:start;
  }
  .booking-info h3{
    font-family:'Cinzel Decorative',serif;
    font-size:1.5rem;color:var(--gold);margin-bottom:1.2rem;
  }
  .booking-info p{color:rgba(245,234,215,.8);line-height:1.8;margin-bottom:1rem;}
  .booking-steps{margin-top:1.5rem;}
  .step{
    display:flex;align-items:flex-start;gap:1rem;margin-bottom:1.2rem;
    padding:.8rem;background:rgba(255,255,255,.05);border-radius:8px;
    border-left:3px solid var(--gold);transition:all .3s;
  }
  .step:hover{background:rgba(200,150,60,.1);}
  .step-num{
    min-width:36px;height:36px;background:var(--terracotta);
    border-radius:50%;display:flex;align-items:center;justify-content:center;
    font-family:'Cinzel Decorative',serif;font-size:.85rem;color:var(--cream);
  }
  .step-text h4{font-family:'Cinzel Decorative',serif;font-size:.9rem;color:var(--cream);margin-bottom:.2rem;}
  .step-text p{font-size:.82rem;color:var(--sand);}
  .booking-form{
    background:rgba(255,255,255,.06);backdrop-filter:blur(10px);
    border:1px solid rgba(200,150,60,.2);border-radius:16px;padding:2.5rem;
  }
  .form-row{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1rem;}
  .form-group{margin-bottom:1rem;}
  .form-group label{
    display:block;font-size:.82rem;color:var(--sand);
    letter-spacing:.1em;margin-bottom:.4rem;
    font-family:'Cinzel Decorative',serif;
  }
  .form-group input,.form-group select,.form-group textarea{
    width:100%;background:rgba(255,255,255,.07);
    border:1px solid rgba(200,150,60,.25);border-radius:8px;
    padding:.8rem 1rem;color:var(--cream);font-family:'Cormorant Garamond',serif;
    font-size:1rem;transition:all .3s;outline:none;
  }
  .form-group input:focus,.form-group select:focus,.form-group textarea:focus{
    border-color:var(--gold);background:rgba(200,150,60,.08);
    box-shadow:0 0 0 3px rgba(200,150,60,.1);
  }
  .form-group select option{background:var(--soil);}
  .form-group textarea{resize:vertical;min-height:100px;}
  .submit-btn{
    width:100%;padding:1rem;
    background:linear-gradient(135deg,var(--terracotta),var(--clay));
    color:var(--cream);border:none;border-radius:8px;
    font-family:'Cinzel Decorative',serif;font-size:1rem;
    letter-spacing:.12em;cursor:pointer;transition:all .4s;
    box-shadow:0 8px 25px rgba(193,68,14,.4);
  }
  .submit-btn:hover{transform:translateY(-2px);box-shadow:0 12px 35px rgba(193,68,14,.5);}
 
  /* ── TESTIMONIALS ── */
  #testimonials{background:var(--cream);}
  .testimonials-grid{
    display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
    gap:2rem;max-width:1100px;margin:0 auto;
  }
  .testi-card{
    background:var(--parchment);border-radius:14px;padding:2rem;
    border:1px solid rgba(160,82,45,.12);position:relative;
    transition:all .4s;
  }
  .testi-card:hover{transform:translateY(-6px);box-shadow:0 18px 45px rgba(61,43,31,.14);}
  .testi-card::before{
    content:'"';position:absolute;top:-1rem;left:1.5rem;
    font-family:'Cinzel Decorative',serif;font-size:5rem;
    color:var(--terracotta);opacity:.2;line-height:1;
  }
  .testi-text{color:var(--text-mid);font-size:1rem;line-height:1.8;font-style:italic;}
  .testi-author{
    margin-top:1.2rem;display:flex;align-items:center;gap:.8rem;
  }
  .testi-avatar{
    width:45px;height:45px;border-radius:50%;
    background:linear-gradient(135deg,var(--terracotta),var(--gold));
    display:flex;align-items:center;justify-content:center;font-size:1.2rem;
  }
  .testi-name{font-family:'Cinzel Decorative',serif;font-size:.85rem;color:var(--soil);}
  .testi-stars{color:var(--gold);font-size:.85rem;margin-top:.2rem;}
 
  /* ── CONTACT ── */
  #contact{background:var(--soil);color:var(--cream);}
  #contact .section-title{color:var(--cream);}
  #contact .section-eyebrow{color:var(--gold);}
  .contact-grid{
    display:grid;grid-template-columns:1fr 1fr;gap:4rem;
    max-width:1100px;margin:0 auto;align-items:start;
  }
  .contact-info-item{
    display:flex;align-items:flex-start;gap:1.2rem;margin-bottom:2rem;
    padding:1.2rem;background:rgba(255,255,255,.05);border-radius:10px;
    border:1px solid rgba(200,150,60,.12);transition:all .3s;
  }
  .contact-info-item:hover{border-color:var(--gold);background:rgba(200,150,60,.08);}
  .contact-icon{
    min-width:46px;height:46px;background:var(--terracotta);
    border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.2rem;
  }
  .contact-label{font-family:'Cinzel Decorative',serif;color:var(--gold);font-size:.8rem;margin-bottom:.3rem;}
  .contact-val{color:var(--cream);font-size:.95rem;}
  .social-links{display:flex;gap:1rem;margin-top:1.5rem;flex-wrap:wrap;}
  .social-btn{
    display:flex;align-items:center;gap:.5rem;
    padding:.6rem 1.2rem;border:1px solid rgba(200,150,60,.3);
    border-radius:8px;color:var(--sand);text-decoration:none;
    font-size:.85rem;transition:all .3s;
  }
  .social-btn:hover{border-color:var(--gold);color:var(--gold);background:rgba(200,150,60,.1);}
  .contact-map{
    background:rgba(255,255,255,.05);border:1px solid rgba(200,150,60,.2);
    border-radius:12px;height:300px;display:flex;align-items:center;justify-content:center;
    font-size:3rem;color:var(--sand);flex-direction:column;gap:1rem;
    font-family:'Cinzel Decorative',serif;font-size:1rem;
  }
 
  /* ── LOGIN MODAL ── */
  .modal-overlay{
    position:fixed;inset:0;z-index:9000;
    background:rgba(30,15,5,.85);backdrop-filter:blur(10px);
    display:none;align-items:center;justify-content:center;padding:2rem;
  }
  .modal-overlay.open{display:flex;}
  .modal{
    background:var(--cream);border-radius:20px;padding:3rem;
    width:100%;max-width:440px;position:relative;
    box-shadow:0 40px 100px rgba(0,0,0,.5);
    animation:modalIn .4s cubic-bezier(.22,1,.36,1);
  }
  @keyframes modalIn{from{opacity:0;transform:scale(.9) translateY(20px)}to{opacity:1;transform:scale(1) translateY(0)}}
  .modal-close{
    position:absolute;top:1.2rem;right:1.5rem;
    font-size:1.5rem;cursor:pointer;color:var(--ash);transition:color .3s;background:none;border:none;
  }
  .modal-close:hover{color:var(--terracotta);}
  .modal-title{
    font-family:'Cinzel Decorative',serif;font-size:1.6rem;
    color:var(--soil);text-align:center;margin-bottom:.5rem;
  }
  .modal-sub{text-align:center;color:var(--ash);font-size:.9rem;margin-bottom:2rem;}
  .modal-tabs{display:flex;border-radius:8px;overflow:hidden;margin-bottom:2rem;border:1px solid rgba(160,82,45,.2);}
  .modal-tab{
    flex:1;padding:.7rem;text-align:center;cursor:pointer;
    font-family:'Cinzel Decorative',serif;font-size:.8rem;
    color:var(--ash);transition:all .3s;background:transparent;border:none;
  }
  .modal-tab.active{background:var(--terracotta);color:var(--cream);}
  .modal .form-group label{color:var(--ash);}
  .modal .form-group input{
    background:var(--parchment);border:1px solid rgba(160,82,45,.25);
    color:var(--soil);border-radius:8px;padding:.8rem 1rem;
    width:100%;font-family:'Cormorant Garamond',serif;font-size:1rem;
    outline:none;transition:all .3s;
  }
  .modal .form-group input:focus{border-color:var(--terracotta);}
  .modal-btn{
    width:100%;padding:.9rem;background:linear-gradient(135deg,var(--terracotta),var(--clay));
    color:var(--cream);border:none;border-radius:8px;
    font-family:'Cinzel Decorative',serif;font-size:.95rem;
    cursor:pointer;margin-top:1rem;transition:all .3s;letter-spacing:.08em;
  }
  .modal-btn:hover{transform:translateY(-2px);box-shadow:0 8px 25px rgba(193,68,14,.4);}
  .modal-forgot{text-align:center;margin-top:1rem;font-size:.85rem;color:var(--ash);}
  .modal-forgot a{color:var(--terracotta);text-decoration:none;}
 
  /* ── CART SIDEBAR ── */
  #cart-sidebar{
    position:fixed;top:0;right:-420px;width:400px;height:100vh;
    background:var(--cream);z-index:5000;
    box-shadow:-10px 0 40px var(--shadow);
    transition:right .4s cubic-bezier(.22,1,.36,1);
    display:flex;flex-direction:column;padding:2rem;overflow-y:auto;
  }
  #cart-sidebar.open{right:0;}
  .cart-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:2rem;}
  .cart-title{font-family:'Cinzel Decorative',serif;font-size:1.2rem;color:var(--soil);}
  .cart-close{font-size:1.3rem;cursor:pointer;background:none;border:none;color:var(--ash);}
  .cart-item{
    display:flex;gap:1rem;padding:1rem 0;
    border-bottom:1px solid rgba(160,82,45,.12);
  }
  .cart-item-img{
    width:70px;height:70px;border-radius:8px;
    background:linear-gradient(135deg,var(--terracotta),var(--gold));
    display:flex;align-items:center;justify-content:center;font-size:1.8rem;
  }
  .cart-item-name{font-family:'Cinzel Decorative',serif;font-size:.85rem;color:var(--soil);}
  .cart-item-price{color:var(--terracotta);font-size:.9rem;margin-top:.3rem;}
  .cart-total{
    margin-top:auto;padding-top:1.5rem;
    border-top:2px solid var(--terracotta);
  }
  .cart-total-row{display:flex;justify-content:space-between;margin-bottom:.5rem;}
  .cart-total-row.grand{
    font-family:'Cinzel Decorative',serif;font-size:1.1rem;
    color:var(--soil);margin-top:.5rem;
  }
  .checkout-btn{
    width:100%;padding:.9rem;background:var(--terracotta);
    color:var(--cream);border:none;border-radius:8px;
    font-family:'Cinzel Decorative',serif;cursor:pointer;
    margin-top:1rem;font-size:.9rem;letter-spacing:.1em;
    transition:all .3s;
  }
  .checkout-btn:hover{background:var(--soil);}
 
  /* ── FOOTER ── */
  footer{
    background:#1a0d06;color:var(--sand);
    padding:4rem 5% 2rem;
  }
  .footer-grid{
    display:grid;grid-template-columns:2fr 1fr 1fr 1fr;
    gap:3rem;max-width:1200px;margin:0 auto;padding-bottom:3rem;
    border-bottom:1px solid rgba(200,150,60,.15);
  }
  .footer-brand .logo{
    font-family:'Cinzel Decorative',serif;font-size:1.6rem;color:var(--gold);
    margin-bottom:.8rem;
  }
  .footer-brand p{font-size:.9rem;line-height:1.8;color:rgba(212,169,106,.7);max-width:240px;}
  .footer-col h4{font-family:'Cinzel Decorative',serif;color:var(--cream);font-size:.9rem;margin-bottom:1.2rem;}
  .footer-col ul{list-style:none;}
  .footer-col ul li{margin-bottom:.6rem;}
  .footer-col ul li a{color:rgba(212,169,106,.7);text-decoration:none;font-size:.88rem;transition:color .3s;}
  .footer-col ul li a:hover{color:var(--gold);}
  .footer-bottom{
    text-align:center;padding-top:2rem;font-size:.82rem;
    color:rgba(212,169,106,.5);max-width:1200px;margin:0 auto;
  }
  .footer-bottom span{color:var(--terracotta);}
 
  /* ── FLOATING WHATSAPP ── */
  .whatsapp-float{
    position:fixed;bottom:2rem;right:2rem;z-index:4000;
    width:56px;height:56px;background:#25D366;border-radius:50%;
    display:flex;align-items:center;justify-content:center;
    text-decoration:none;font-size:1.8rem;
    box-shadow:0 8px 25px rgba(37,211,102,.4);
    animation:waPulse 2.5s ease infinite;transition:transform .3s;
  }
  .whatsapp-float:hover{transform:scale(1.1);}
  @keyframes waPulse{0%,100%{box-shadow:0 8px 25px rgba(37,211,102,.4)}50%{box-shadow:0 8px 35px rgba(37,211,102,.7)}}
 
  /* ── CART FAB ── */
  .cart-fab{
    position:fixed;bottom:2rem;left:2rem;z-index:4000;
    width:56px;height:56px;background:var(--terracotta);
    border-radius:50%;border:none;cursor:pointer;
    display:flex;align-items:center;justify-content:center;font-size:1.5rem;
    box-shadow:0 8px 25px rgba(193,68,14,.4);transition:transform .3s;
  }
  .cart-fab:hover{transform:scale(1.1);}
  .cart-badge{
    position:absolute;top:-4px;right:-4px;
    background:var(--gold);color:var(--soil);
    width:20px;height:20px;border-radius:50%;
    font-size:.65rem;font-weight:700;
    display:flex;align-items:center;justify-content:center;
    font-family:'Cinzel Decorative',serif;
  }
 
  /* ── SCROLL REVEAL ── */
  .reveal{opacity:0;transform:translateY(30px);transition:all .8s cubic-bezier(.22,1,.36,1);}
  .reveal.visible{opacity:1;transform:translateY(0);}
  .reveal-left{opacity:0;transform:translateX(-40px);transition:all .8s cubic-bezier(.22,1,.36,1);}
  .reveal-left.visible{opacity:1;transform:translateX(0);}
  .reveal-right{opacity:0;transform:translateX(40px);transition:all .8s cubic-bezier(.22,1,.36,1);}
  .reveal-right.visible{opacity:1;transform:translateX(0);}
 
  /* ── 3D TITLE EFFECT ── */
  .title-3d{
    text-shadow:
      1px 1px 0 var(--bark),
      2px 2px 0 var(--clay),
      3px 3px 0 var(--ash),
      4px 4px 0 rgba(61,43,31,.2),
      5px 5px 0 rgba(61,43,31,.1);
  }
 
  /* ── NOTIFICATION ── */
  .notification{
    position:fixed;top:6rem;right:2rem;z-index:9000;
    background:var(--soil);color:var(--cream);
    padding:1rem 1.5rem;border-radius:10px;
    border-left:4px solid var(--gold);
    transform:translateX(200%);transition:transform .4s cubic-bezier(.22,1,.36,1);
    font-family:'Cinzel Decorative',serif;font-size:.85rem;
    max-width:280px;box-shadow:0 8px 30px rgba(0,0,0,.4);
  }
  .notification.show{transform:translateX(0);}
 
  /* ── RESPONSIVE ── */
  @media(max-width:900px){
    .about-grid,.booking-wrap,.contact-grid{grid-template-columns:1fr;}
    .footer-grid{grid-template-columns:1fr 1fr;}
    .nav-links{display:none;}
    .hamburger{display:flex;}
    .about-visual{height:240px;}
    .form-row{grid-template-columns:1fr;}
  }
  @media(max-width:600px){
    .footer-grid{grid-template-columns:1fr;}
    .hero-stats{gap:2rem;}
    #cart-sidebar{width:100%;right:-100%;}
  }
</style>
</head>
<body>
 
<!-- CURSOR -->
<div id="cursor"></div>
<div id="cursor-ring"></div>
 
<!-- LOADER -->
<div id="loader">
  <div class="loader-logo">Tapasya arT</div>
  <div class="loader-sub">कला • सेवा • सर्जनशीलता</div>
  <div class="loader-bar"><div class="loader-fill"></div></div>
</div>
 
<!-- NOTIFICATION -->
<div class="notification" id="notification"></div>
 
<!-- NAV -->
<nav id="navbar">
  <a href="#hero" class="nav-logo">🪷 <span>Tapasya</span> arT</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#portfolio">Portfolio</a></li>
    <li><a href="#shop">Shop</a></li>
    <li><a href="#booking">Book</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div style="display:flex;gap:1rem;align-items:center;">
    <a href="#" class="nav-cta" onclick="openLogin();return false;">🔐 Login</a>
  </div>
  <div class="hamburger" onclick="toggleMobileNav()">
    <span></span><span></span><span></span>
  </div>
</nav>
 
<!-- HERO -->
<section id="hero">
  <div class="hero-canvas"></div>
  <div class="floating-orbs">
    <div class="orb orb1"></div>
    <div class="orb orb2"></div>
    <div class="orb orb3"></div>
  </div>
  <div class="hero-content">
    <div class="hero-eyebrow">कला की दुनिया में आपका स्वागत है</div>
    <h1 class="hero-title title-3d">Tapasya <span class="art">arT</span></h1>
    <p class="hero-tagline">Where Every Surface Becomes a Masterpiece</p>
    <p class="hero-marathi">प्रत्येक भिंत एक कलाकृती बनते</p>
    <div class="hero-btns">
      <a href="#portfolio" class="btn-primary">✦ Explore Gallery</a>
      <a href="#booking" class="btn-outline">Book a Service</a>
    </div>
    <div class="hero-stats">
      <div class="stat"><span class="stat-num" data-count="500">0</span><div class="stat-label">Projects Done</div></div>
      <div class="stat"><span class="stat-num" data-count="8">0</span><div class="stat-label">Years Exp.</div></div>
      <div class="stat"><span class="stat-num" data-count="11">0</span><div class="stat-label">Art Services</div></div>
      <div class="stat"><span class="stat-num" data-count="100">0</span><div class="stat-label">% Handcrafted</div></div>
    </div>
  </div>
  <div class="scroll-hint">SCROLL</div>
</section>
 
<!-- ABOUT -->
<section id="about">
  <div class="section-header">
    <div class="section-eyebrow">आमच्याबद्दल • About Us</div>
    <h2 class="section-title reveal">The Artists Behind the Vision</h2>
    <div class="section-line"></div>
  </div>
  <div class="about-grid">
    <div class="about-visual reveal-left">
      <div class="about-card about-card-main">🎨</div>
      <div class="about-card about-card-accent">🏺</div>
    </div>
    <div class="about-text reveal-right">
      <h3>कला हीच आमची ओळख</h3>
      <p>Tapasya arT is a passionate art studio dedicated to transforming spaces into living stories. Founded by two visionary artists, we blend traditional Indian artistry with modern techniques.</p>
      <div class="marathi-quote">
        "कलेत जीव ओतला तर भिंतीही बोलतात" — जिथे कला आहे, तिथे आत्मा आहे
      </div>
      <p>From grand wall murals to intricate stone carvings, from canvas paintings to precision CNC metal work — every creation carries the mark of dedicated craftsmanship and creative devotion.</p>
      <div class="team-cards">
        <div class="team-card">
          <div class="team-avatar">🎨</div>
          <div class="team-name">Atul Undarkar</div>
          <div class="team-phone">📱 9766654460</div>
        </div>
        <div class="team-card">
          <div class="team-avatar">🖌️</div>
          <div class="team-name">Prashant Hirdekar</div>
          <div class="team-phone">📱 9604316634</div>
        </div>
      </div>
    </div>
  </div>
</section>
 
<!-- SERVICES -->
<section id="services">
  <div class="section-header">
    <div class="section-eyebrow">सेवा • Our Services</div>
    <h2 class="section-title reveal">Crafted with Devotion</h2>
    <div class="section-line"></div>
  </div>
  <div class="services-grid">
    <div class="service-card reveal"><div class="service-tag">Popular</div><div class="service-icon">🏛️</div><div class="service-name">Wall Mural</div><div class="service-desc">Transform your walls into breathtaking artworks. Custom designs from traditional to modern themes.</div><div class="service-price">Starting ₹2,500/sq.ft</div></div>
    <div class="service-card reveal"><div class="service-icon">🪧</div><div class="service-name">Name Plates</div><div class="service-desc">Elegant handcrafted and acrylic name plates — personalized for homes, offices & temples.</div><div class="service-price">Starting ₹500</div></div>
    <div class="service-card reveal"><div class="service-tag">Premium</div><div class="service-icon">🗿</div><div class="service-name">Stone Carving</div><div class="service-desc">Masterful stone sculptures and carvings — Ganesha, temple carvings, decorative panels.</div><div class="service-price">Starting ₹5,000</div></div>
    <div class="service-card reveal"><div class="service-icon">🖼️</div><div class="service-name">Canvas Painting</div><div class="service-desc">Original artwork on canvas — gods, landscapes, abstract, portraits. Made to order.</div><div class="service-price">Starting ₹800</div></div>
    <div class="service-card reveal"><div class="service-icon">🪞</div><div class="service-name">Decorative Frames</div><div class="service-desc">Ornate handcrafted frames — perfect for photos, mirrors & art pieces.</div><div class="service-price">Starting ₹350</div></div>
    <div class="service-card reveal"><div class="service-tag">Specialty</div><div class="service-icon">🕉️</div><div class="service-name">God Murals</div><div class="service-desc">Sacred deity murals with traditional Indian iconography. Ganesh, Lakshmi, Krishna & more.</div><div class="service-price">Starting ₹3,000</div></div>
    <div class="service-card reveal"><div class="service-icon">🚪</div><div class="service-name">Door Mural</div><div class="service-desc">Beautiful paintings on doors — welcome art that creates first impressions.</div><div class="service-price">Starting ₹1,500</div></div>
    <div class="service-card reveal"><div class="service-icon">⚙️</div><div class="service-name">CNC Cutting</div><div class="service-desc">Precision CNC laser cutting for intricate designs in metal, wood & acrylic.</div><div class="service-price">Starting ₹300</div></div>
    <div class="service-card reveal"><div class="service-icon">🔩</div><div class="service-name">Metal Name Plate</div><div class="service-desc">Premium metal name plates with laser engraving — durable & elegant.</div><div class="service-price">Starting ₹800</div></div>
    <div class="service-card reveal"><div class="service-icon">✨</div><div class="service-name">Ceiling Murals</div><div class="service-desc">Spectacular ceiling art — from subtle textures to grand Sistine-style paintings.</div><div class="service-price">Starting ₹3,500/sq.ft</div></div>
    <div class="service-card reveal"><div class="service-icon">💎</div><div class="service-name">Acrylic Name Plate</div><div class="service-desc">Modern acrylic plates with LED backlit options — stylish, sleek and sophisticated.</div><div class="service-price">Starting ₹600</div></div>
  </div>
</section>
 
<!-- PORTFOLIO -->
<section id="portfolio">
  <div class="section-header">
    <div class="section-eyebrow">आमचे काम • Our Work</div>
    <h2 class="section-title reveal" style="color:var(--cream)">Gallery of Masterpieces</h2>
    <div class="section-line"></div>
  </div>
  <div class="portfolio-filter reveal">
    <button class="filter-btn active" onclick="filterPortfolio('all',this)">All Work</button>
    <button class="filter-btn" onclick="filterPortfolio('mural',this)">Murals</button>
    <button class="filter-btn" onclick="filterPortfolio('carving',this)">Carvings</button>
    <button class="filter-btn" onclick="filterPortfolio('canvas',this)">Canvas</button>
    <button class="filter-btn" onclick="filterPortfolio('nameplate',this)">Name Plates</button>
  </div>
  <div class="portfolio-grid" id="portfolioGrid">
    <div class="portfolio-item reveal" data-cat="mural"><div class="portfolio-bg p1">🏛️</div><div class="portfolio-overlay"><div class="portfolio-title">Radha Krishna Wall Mural</div><div class="portfolio-cat">Wall Mural • Nashik</div></div></div>
    <div class="portfolio-item reveal" data-cat="carving"><div class="portfolio-bg p2">🗿</div><div class="portfolio-overlay"><div class="portfolio-title">Lord Ganesha Stone Sculpture</div><div class="portfolio-cat">Stone Carving • Pune</div></div></div>
    <div class="portfolio-item reveal" data-cat="canvas"><div class="portfolio-bg p3">🖼️</div><div class="portfolio-overlay"><div class="portfolio-title">Traditional Warli Canvas</div><div class="portfolio-cat">Canvas Painting • Custom</div></div></div>
    <div class="portfolio-item reveal" data-cat="nameplate"><div class="portfolio-bg p4">🪧</div><div class="portfolio-overlay"><div class="portfolio-title">CNC Brass Name Plate</div><div class="portfolio-cat">Metal Name Plate • Office</div></div></div>
    <div class="portfolio-item reveal" data-cat="mural"><div class="portfolio-bg p5">🕉️</div><div class="portfolio-overlay"><div class="portfolio-title">Temple God Mural</div><div class="portfolio-cat">God Mural • Temple</div></div></div>
    <div class="portfolio-item reveal" data-cat="canvas"><div class="portfolio-bg p6">✨</div><div class="portfolio-overlay"><div class="portfolio-title">Ceiling Art — Hotel Lobby</div><div class="portfolio-cat">Ceiling Mural • Commercial</div></div></div>
    <div class="portfolio-item reveal" data-cat="mural"><div class="portfolio-bg p3">🚪</div><div class="portfolio-overlay"><div class="portfolio-title">Floral Door Mural</div><div class="portfolio-cat">Door Mural • Residence</div></div></div>
    <div class="portfolio-item reveal" data-cat="nameplate"><div class="portfolio-bg p2">💎</div><div class="portfolio-overlay"><div class="portfolio-title">LED Acrylic Name Plate</div><div class="portfolio-cat">Acrylic • Modern Home</div></div></div>
    <div class="portfolio-item reveal" data-cat="carving"><div class="portfolio-bg p1">🏺</div><div class="portfolio-overlay"><div class="portfolio-title">Decorative Stone Panel</div><div class="portfolio-cat">Stone Carving • Villa</div></div></div>
  </div>
</section>
 
<!-- SHOP -->
<section id="shop">
  <div class="section-header">
    <div class="section-eyebrow">खरेदी करा • Shop Online</div>
    <h2 class="section-title reveal">Buy Handcrafted Art</h2>
    <div class="section-line"></div>
  </div>
  <div class="shop-grid">
    <div class="product-card reveal" data-name="Warli Canvas Painting" data-price="1200" data-emoji="🎨">
      <div class="product-img p3" style="background:linear-gradient(135deg,#704214,#C8963C)"><span>🎨</span><div class="product-badge">Handmade</div></div>
      <div class="product-info"><div class="product-name">Warli Canvas Painting</div><div class="product-desc">Traditional Warli art on canvas. 12×16 inches. Ready to hang.</div><div class="product-price"><span class="price">₹1,200</span><button class="add-btn" onclick="addToCart('Warli Canvas Painting','1200','🎨')">Add to Cart</button></div></div>
    </div>
    <div class="product-card reveal" data-name="Ganesha Stone Idol" data-price="3500">
      <div class="product-img" style="background:linear-gradient(135deg,#8B4513,#A0522D)"><span>🗿</span><div class="product-badge">Premium</div></div>
      <div class="product-info"><div class="product-name">Ganesha Stone Idol</div><div class="product-desc">Handcarved Ganesha in natural stone. 8 inch height. Unique piece.</div><div class="product-price"><span class="price">₹3,500</span><button class="add-btn" onclick="addToCart('Ganesha Stone Idol','3500','🗿')">Add to Cart</button></div></div>
    </div>
    <div class="product-card reveal">
      <div class="product-img" style="background:linear-gradient(135deg,#2F4F4F,#5F9EA0)"><span>🪧</span></div>
      <div class="product-info"><div class="product-name">CNC Metal Name Plate</div><div class="product-desc">Laser-cut stainless steel. Custom name engraving. Weather-proof.</div><div class="product-price"><span class="price">₹950</span><button class="add-btn" onclick="addToCart('CNC Metal Name Plate','950','🪧')">Add to Cart</button></div></div>
    </div>
    <div class="product-card reveal">
      <div class="product-img" style="background:linear-gradient(135deg,#556B2F,#8FBC8F)"><span>🪞</span><div class="product-badge">New</div></div>
      <div class="product-info"><div class="product-name">Decorative Wall Frame</div><div class="product-desc">Ornate wooden frame with hand-painted motifs. 18×24 inches.</div><div class="product-price"><span class="price">₹750</span><button class="add-btn" onclick="addToCart('Decorative Wall Frame','750','🪞')">Add to Cart</button></div></div>
    </div>
    <div class="product-card reveal">
      <div class="product-img" style="background:linear-gradient(135deg,#8B0000,#DC143C)"><span>🕉️</span></div>
      <div class="product-info"><div class="product-name">God Canvas Art</div><div class="product-desc">Acrylic on canvas — Lord Shiva, Durga, Krishna. 20×24 inches.</div><div class="product-price"><span class="price">₹1,800</span><button class="add-btn" onclick="addToCart('God Canvas Art','1800','🕉️')">Add to Cart</button></div></div>
    </div>
    <div class="product-card reveal">
      <div class="product-img" style="background:linear-gradient(135deg,#191970,#4169E1)"><span>💎</span></div>
      <div class="product-info"><div class="product-name">LED Acrylic Name Plate</div><div class="product-desc">Modern backlit acrylic plate. Custom text. Perfect for homes & offices.</div><div class="product-price"><span class="price">₹1,100</span><button class="add-btn" onclick="addToCart('LED Acrylic Name Plate','1100','💎')">Add to Cart</button></div></div>
    </div>
  </div>
  <p class="shop-note reveal">🚚 Free delivery above ₹2,000 • Customization available on all products • WhatsApp us for bulk orders</p>
</section>
 
<!-- BOOKING -->
<section id="booking">
  <div class="section-header">
    <div class="section-eyebrow">सेवा बुक करा • Book a Service</div>
    <h2 class="section-title reveal">Commission Your Masterpiece</h2>
    <div class="section-line"></div>
  </div>
  <div class="booking-wrap">
    <div class="booking-info reveal-left">
      <h3>How It Works</h3>
      <p>From concept to creation — we guide you through every step of your art journey.</p>
      <div class="booking-steps">
        <div class="step"><div class="step-num">1</div><div class="step-text"><h4>Share Your Vision</h4><p>Tell us your idea, space dimensions & budget</p></div></div>
        <div class="step"><div class="step-num">2</div><div class="step-text"><h4>Design Consultation</h4><p>We create a detailed design mockup for approval</p></div></div>
        <div class="step"><div class="step-num">3</div><div class="step-text"><h4>Crafting Begins</h4><p>Our artists bring your vision to life with precision</p></div></div>
        <div class="step"><div class="step-num">4</div><div class="step-text"><h4>Delivery & Install</h4><p>Professional installation at your location</p></div></div>
      </div>
    </div>
    <div class="booking-form reveal-right">
      <div class="form-row">
        <div class="form-group"><label>Your Name</label><input type="text" placeholder="Enter full name" id="bName"/></div>
        <div class="form-group"><label>Phone Number</label><input type="tel" placeholder="WhatsApp number" id="bPhone"/></div>
      </div>
      <div class="form-group"><label>Email</label><input type="email" placeholder="your@email.com" id="bEmail"/></div>
      <div class="form-group"><label>Service Required</label>
        <select id="bService">
          <option value="">-- Select Service --</option>
          <option>Wall Mural</option><option>God Mural</option><option>Door Mural</option><option>Ceiling Mural</option>
          <option>Stone Carving</option><option>Canvas Painting</option><option>Decorative Frame</option>
          <option>CNC Cutting</option><option>Metal Name Plate</option><option>Acrylic Name Plate</option><option>Name Plate (Other)</option>
        </select>
      </div>
      <div class="form-row">
        <div class="form-group"><label>Location / City</label><input type="text" placeholder="Your city" id="bCity"/></div>
        <div class="form-group"><label>Preferred Date</label><input type="date" id="bDate"/></div>
      </div>
      <div class="form-group"><label>Your Vision / Message</label><textarea placeholder="Describe your idea, dimensions, theme, colors..." id="bMsg"></textarea></div>
      <button class="submit-btn" onclick="submitBooking()">✦ Submit Booking Request</button>
    </div>
  </div>
</section>
 
<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="section-header">
    <div class="section-eyebrow">ग्राहकांचे मत • Reviews</div>
    <h2 class="section-title reveal">What Our Clients Say</h2>
    <div class="section-line"></div>
  </div>
  <div class="testimonials-grid">
    <div class="testi-card reveal"><div class="testi-text">Tapasya arT transformed our pooja room with an absolutely stunning Radha Krishna mural. The detail and colour work is beyond expectations. Highly recommended!</div><div class="testi-author"><div class="testi-avatar">🙏</div><div><div class="testi-name">Sunita Patil</div><div class="testi-stars">⭐⭐⭐⭐⭐ • Nashik</div></div></div></div>
    <div class="testi-card reveal"><div class="testi-text">Got a custom acrylic name plate for my new office. The LED backlight looks so premium. Prashant ji was very professional and delivered on time. Will order again!</div><div class="testi-author"><div class="testi-avatar">💼</div><div><div class="testi-name">Rajesh Sharma</div><div class="testi-stars">⭐⭐⭐⭐⭐ • Pune</div></div></div></div>
    <div class="testi-card reveal"><div class="testi-text">The stone Ganesha carving they made for our shop is absolutely divine. Atul sir has incredible skill. Our customers keep asking where we got it from!</div><div class="testi-author"><div class="testi-avatar">🕉️</div><div><div class="testi-name">Mangesh Deshmukh</div><div class="testi-stars">⭐⭐⭐⭐⭐ • Aurangabad</div></div></div></div>
  </div>
</section>
 
<!-- CONTACT -->
<section id="contact">
  <div class="section-header">
    <div class="section-eyebrow">संपर्क • Get in Touch</div>
    <h2 class="section-title reveal">Let's Create Together</h2>
    <div class="section-line"></div>
  </div>
  <div class="contact-grid">
    <div class="reveal-left">
      <div class="contact-info-item"><div class="contact-icon">📱</div><div><div class="contact-label">Atul Undarkar</div><div class="contact-val"><a href="tel:9766654460" style="color:var(--cream);text-decoration:none;">+91 9766654460</a></div></div></div>
      <div class="contact-info-item"><div class="contact-icon">📱</div><div><div class="contact-label">Prashant Hirdekar</div><div class="contact-val"><a href="tel:9604316634" style="color:var(--cream);text-decoration:none;">+91 9604316634</a></div></div></div>
      <div class="contact-info-item"><div class="contact-icon">📍</div><div><div class="contact-label">Location</div><div class="contact-val">Maharashtra, India</div></div></div>
      <div class="contact-info-item"><div class="contact-icon">🕐</div><div><div class="contact-label">Working Hours</div><div class="contact-val">Mon–Sat: 9 AM – 7 PM</div></div></div>
      <div class="social-links">
        <a href="#" class="social-btn">📘 Facebook</a>
        <a href="#" class="social-btn">📸 Instagram</a>
        <a href="#" class="social-btn">🔍 Justdial</a>
        <a href="#" class="social-btn">🛒 IndiaMart</a>
      </div>
    </div>
    <div class="reveal-right">
      <div class="contact-map">
        <span style="font-size:3rem">📍</span>
        <span style="font-family:'Cormorant Garamond',serif;color:var(--sand);font-size:1rem">Tapasya arT Studio</span>
        <span style="font-size:.85rem;color:rgba(212,169,106,.6)">Maharashtra, India</span>
        <a href="https://wa.me/919766654460" target="_blank" style="margin-top:1rem;padding:.7rem 1.5rem;background:var(--terracotta);color:var(--cream);text-decoration:none;border-radius:8px;font-family:'Cinzel Decorative',serif;font-size:.85rem;">💬 Chat on WhatsApp</a>
      </div>
    </div>
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <div class="logo">🪷 Tapasya arT</div>
      <p>Handcrafted art that transforms spaces into soulful masterpieces. Based in Maharashtra, serving all of India.</p>
      <p style="margin-top:.8rem;font-family:'Noto Sans Devanagari',sans-serif;font-size:.85rem;color:rgba(212,169,106,.5);">कलेतून जग सुंदर होते</p>
    </div>
    <div class="footer-col"><h4>Services</h4><ul>
      <li><a href="#services">Wall Murals</a></li><li><a href="#services">Stone Carving</a></li>
      <li><a href="#services">Canvas Painting</a></li><li><a href="#services">Name Plates</a></li>
      <li><a href="#services">CNC Cutting</a></li>
    </ul></div>
    <div class="footer-col"><h4>Quick Links</h4><ul>
      <li><a href="#about">About Us</a></li><li><a href="#portfolio">Portfolio</a></li>
      <li><a href="#shop">Shop</a></li><li><a href="#booking">Book Service</a></li>
      <li><a href="#testimonials">Reviews</a></li>
    </ul></div>
    <div class="footer-col"><h4>Contact</h4><ul>
      <li><a href="tel:9766654460">📱 9766654460</a></li>
      <li><a href="tel:9604316634">📱 9604316634</a></li>
      <li><a href="#">📘 Facebook</a></li>
      <li><a href="#">📸 Instagram</a></li>
      <li><a href="#">🔍 Justdial</a></li>
    </ul></div>
  </div>
  <div class="footer-bottom">
    © 2026 Tapasya arT. All Rights Reserved. Crafted with <span>❤️</span> in Maharashtra, India.
  </div>
</footer>
 
<!-- LOGIN MODAL -->
<div class="modal-overlay" id="loginModal">
  <div class="modal">
    <button class="modal-close" onclick="closeLogin()">✕</button>
    <div class="modal-title">🪷 Welcome</div>
    <div class="modal-sub">Login or create your Tapasya arT account</div>
    <div class="modal-tabs">
      <button class="modal-tab active" onclick="switchTab('login')">Login</button>
      <button class="modal-tab" onclick="switchTab('register')">Register</button>
    </div>
    <div id="loginForm">
      <div class="form-group"><label>Phone / Email</label><input type="text" placeholder="Enter your phone or email" id="loginId"/></div>
      <div class="form-group"><label>Password</label><input type="password" placeholder="Enter password" id="loginPwd"/></div>
      <button class="modal-btn" onclick="doLogin()">Login to Account</button>
      <div class="modal-forgot"><a href="#">Forgot password?</a> · <a href="#" onclick="switchTab('register');return false;">New user? Register</a></div>
    </div>
    <div id="registerForm" style="display:none">
      <div class="form-group"><label>Full Name</label><input type="text" placeholder="Your name" id="regName"/></div>
      <div class="form-group"><label>Phone</label><input type="tel" placeholder="+91 XXXXXXXXXX" id="regPhone"/></div>
      <div class="form-group"><label>Email</label><input type="email" placeholder="your@email.com" id="regEmail"/></div>
      <div class="form-group"><label>Create Password</label><input type="password" placeholder="Min 6 characters" id="regPwd"/></div>
      <button class="modal-btn" onclick="doRegister()">Create Account</button>
    </div>
  </div>
</div>
 
<!-- CART SIDEBAR -->
<div id="cart-sidebar">
  <div class="cart-header">
    <span class="cart-title">🛒 Your Cart</span>
    <button class="cart-close" onclick="toggleCart()">✕</button>
  </div>
  <div id="cart-items"></div>
  <div class="cart-total" id="cart-total" style="display:none">
    <div class="cart-total-row"><span>Subtotal</span><span id="cart-sub">₹0</span></div>
    <div class="cart-total-row"><span>Delivery</span><span>₹Free</span></div>
    <div class="cart-total-row grand"><span>Total</span><span id="cart-grand">₹0</span></div>
    <button class="checkout-btn" onclick="checkout()">Proceed to Checkout ✦</button>
  </div>
  <div id="cart-empty" style="text-align:center;padding:3rem 1rem;color:var(--ash)">
    <div style="font-size:3rem">🛒</div>
    <p style="margin-top:1rem;font-family:'Cinzel Decorative',serif;font-size:.85rem">Your cart is empty</p>
    <p style="font-size:.82rem;margin-top:.4rem">Add some beautiful art!</p>
  </div>
</div>
 
<!-- FLOATING BUTTONS -->
<a href="https://wa.me/919766654460?text=Hello%20Tapasya%20arT!%20I%20am%20interested%20in%20your%20services." target="_blank" class="whatsapp-float" title="Chat on WhatsApp">💬</a>
<button class="cart-fab" onclick="toggleCart()" title="View Cart"><span id="cart-icon">🛒</span><div class="cart-badge" id="cart-count">0</div></button>
 
<script>
// ── CURSOR
const cursor=document.getElementById('cursor');
const ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cursor.style.left=mx+'px';cursor.style.top=my+'px';});
function animRing(){rx+=(mx-rx)*.12;ry+=(my-ry)*.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animRing);}animRing();
document.querySelectorAll('a,button,.service-card,.product-card,.portfolio-item,.filter-btn').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cursor.style.width='8px';cursor.style.height='8px';ring.style.width='60px';ring.style.height='60px';});
  el.addEventListener('mouseleave',()=>{cursor.style.width='14px';cursor.style.height='14px';ring.style.width='40px';ring.style.height='40px';});
});
 
// ── LOADER
window.addEventListener('load',()=>{setTimeout(()=>{document.getElementById('loader').classList.add('hide');},2200);});
 
// ── NAV SCROLL
window.addEventListener('scroll',()=>{document.getElementById('navbar').classList.toggle('scrolled',window.scrollY>60);});
 
// ── SCROLL REVEAL
const reveals=document.querySelectorAll('.reveal,.reveal-left,.reveal-right');
const obs=new IntersectionObserver(entries=>{entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('visible');});},{threshold:.12});
reveals.forEach(r=>obs.observe(r));
 
// ── COUNTER ANIMATION
function countUp(){
  document.querySelectorAll('[data-count]').forEach(el=>{
    const target=+el.dataset.count;let current=0;
    const step=target/60;
    const t=setInterval(()=>{current+=step;if(current>=target){el.textContent=target+'+';clearInterval(t);}else{el.textContent=Math.floor(current);}},30);
  });
}
const heroObs=new IntersectionObserver(e=>{if(e[0].isIntersecting){countUp();heroObs.disconnect();}},{threshold:.3});
heroObs.observe(document.getElementById('hero'));
 
// ── PORTFOLIO FILTER
function filterPortfolio(cat,btn){
  document.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  document.querySelectorAll('.portfolio-item').forEach(item=>{
    if(cat==='all'||item.dataset.cat===cat){item.style.display='block';}else{item.style.display='none';}
  });
}
 
// ── CART
let cart=[];
function addToCart(name,price,emoji){
  const existing=cart.find(i=>i.name===name);
  if(existing){existing.qty++;showNotification('Quantity updated! 🎨');}
  else{cart.push({name,price:+price,emoji,qty:1});showNotification(name+' added to cart! 🛒');}
  updateCart();
}
function updateCart(){
  const count=cart.reduce((s,i)=>s+i.qty,0);
  document.getElementById('cart-count').textContent=count;
  const total=cart.reduce((s,i)=>s+i.price*i.qty,0);
  const itemsEl=document.getElementById('cart-items');
  const emptyEl=document.getElementById('cart-empty');
  const totalEl=document.getElementById('cart-total');
  if(cart.length===0){itemsEl.innerHTML='';emptyEl.style.display='block';totalEl.style.display='none';return;}
  emptyEl.style.display='none';totalEl.style.display='block';
  document.getElementById('cart-sub').textContent='₹'+total.toLocaleString();
  document.getElementById('cart-grand').textContent='₹'+total.toLocaleString();
  itemsEl.innerHTML=cart.map((item,i)=>`
    <div class="cart-item">
      <div class="cart-item-img">${item.emoji}</div>
      <div style="flex:1">
        <div class="cart-item-name">${item.name}</div>
        <div class="cart-item-price">₹${item.price.toLocaleString()} × ${item.qty}</div>
      </div>
      <button onclick="removeFromCart(${i})" style="background:none;border:none;color:#c1440e;cursor:pointer;font-size:1.1rem;">✕</button>
    </div>`).join('');
}
function removeFromCart(i){cart.splice(i,1);updateCart();showNotification('Item removed');}
function toggleCart(){document.getElementById('cart-sidebar').classList.toggle('open');}
function checkout(){alert('Thank you for your order! 🙏\nOur team will contact you on WhatsApp to confirm.');}
 
// ── BOOKING
function submitBooking(){
  const name=document.getElementById('bName').value;
  const phone=document.getElementById('bPhone').value;
  const service=document.getElementById('bService').value;
  if(!name||!phone||!service){showNotification('Please fill all required fields');return;}
  showNotification('Booking submitted! We\'ll contact you soon 🙏');
  ['bName','bPhone','bEmail','bCity','bDate','bMsg'].forEach(id=>document.getElementById(id).value='');
  document.getElementById('bService').selectedIndex=0;
}
 
// ── LOGIN
function openLogin(){document.getElementById('loginModal').classList.add('open');}
function closeLogin(){document.getElementById('loginModal').classList.remove('open');}
function switchTab(tab){
  document.querySelectorAll('.modal-tab').forEach((t,i)=>{t.classList.toggle('active',(i===0&&tab==='login')||(i===1&&tab==='register'));});
  document.getElementById('loginForm').style.display=tab==='login'?'block':'none';
  document.getElementById('registerForm').style.display=tab==='register'?'block':'none';
}
function doLogin(){
  const id=document.getElementById('loginId').value;
  if(!id){showNotification('Please enter your phone or email');return;}
  showNotification('Welcome back to Tapasya arT! 🎨');closeLogin();
}
function doRegister(){
  const name=document.getElementById('regName').value;
  const phone=document.getElementById('regPhone').value;
  if(!name||!phone){showNotification('Please fill all fields');return;}
  showNotification('Account created! Welcome '+name+' 🙏');closeLogin();
}
document.getElementById('loginModal').addEventListener('click',function(e){if(e.target===this)closeLogin();});
 
// ── NOTIFICATION
function showNotification(msg){
  const n=document.getElementById('notification');
  n.textContent=msg;n.classList.add('show');
  setTimeout(()=>n.classList.remove('show'),3000);
}
 
// ── MOBILE NAV
function toggleMobileNav(){
  const links=document.querySelector('.nav-links');
  if(links.style.display==='flex'){links.style.display='none';}
  else{links.style.display='flex';links.style.flexDirection='column';links.style.position='fixed';links.style.top='70px';links.style.left='0';links.style.right='0';links.style.background='rgba(61,43,31,.97)';links.style.padding='2rem';links.style.gap='1.5rem';links.style.zIndex='999';}
}
 
// ── 3D TILT ON CARDS
document.querySelectorAll('.service-card,.product-card').forEach(card=>{
  card.addEventListener('mousemove',e=>{
    const r=card.getBoundingClientRect();
    const x=(e.clientX-r.left)/r.width-.5;
    const y=(e.clientY-r.top)/r.height-.5;
    card.style.transform=`perspective(600px) rotateY(${x*10}deg) rotateX(${-y*10}deg) translateY(-6px)`;
  });
  card.addEventListener('mouseleave',()=>{card.style.transform='';});
});
 
// Init cart
updateCart();
</script>
</body>
</html>
