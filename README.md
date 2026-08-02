# Mikmagic
It’s about consultancy services
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mikmagic✨ | Mohit Harsh Vardhan — Digital Architecture</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Jost:wght@200;300;400;500&family=Cinzel:wght@400;500&display=swap" rel="stylesheet"/>
<style>
/* ─── DESIGN TOKENS ─── */
:root {
  --cream:       #F5F0E8;
  --ivory:       #FAF7F2;
  --linen:       #EDE8DE;
  --gold:        #D4AF37;
  --gold-light:  #E8D06A;
  --gold-dark:   #A8891E;
  --charcoal:    #2C2A26;
  --bronze:      #4A3F2F;
  --slate:       #6B6560;
  --glass-bg:    rgba(245,240,232,0.72);
  --glass-border:rgba(212,175,55,0.25);
  --shadow-gold: 0 4px 40px rgba(212,175,55,0.12);
  --transition:  cubic-bezier(0.4,0,0.2,1);
  --serif:       'Cormorant Garamond', Georgia, serif;
  --sans:        'Jost', sans-serif;
  --display:     'Cinzel', serif;
}

/* ─── RESET & BASE ─── */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; font-size: 16px; }
body {
  background: var(--ivory);
  color: var(--charcoal);
  font-family: var(--sans);
  font-weight: 300;
  line-height: 1.7;
  overflow-x: hidden;
}
::selection { background: var(--gold); color: var(--cream); }

/* ─── SCROLL ANIMATIONS ─── */
.reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.9s var(--transition), transform 0.9s var(--transition);
}
.reveal.in-view { opacity: 1; transform: translateY(0); }
.reveal-delay-1 { transition-delay: 0.15s; }
.reveal-delay-2 { transition-delay: 0.3s; }
.reveal-delay-3 { transition-delay: 0.45s; }
.reveal-delay-4 { transition-delay: 0.6s; }

/* ─── NOISE TEXTURE OVERLAY ─── */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 999;
  opacity: 0.025;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
}

/* ─── GOLD DIVIDER ─── */
.gold-line {
  width: 60px; height: 1px;
  background: linear-gradient(90deg, transparent, var(--gold), transparent);
  margin: 1.2rem auto;
}

/* ─── NAVIGATION ─── */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  padding: 0 5%;
  height: 72px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: var(--glass-bg);
  backdrop-filter: blur(20px) saturate(1.4);
  -webkit-backdrop-filter: blur(20px) saturate(1.4);
  border-bottom: 1px solid var(--glass-border);
  transition: all 0.4s var(--transition);
}
nav.scrolled {
  height: 60px;
  box-shadow: 0 8px 32px rgba(44,42,38,0.08);
}
.nav-logo {
  font-family: var(--display);
  font-size: 1.15rem;
  letter-spacing: 0.12em;
  color: var(--charcoal);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.nav-logo span { color: var(--gold); }
.nav-links {
  display: flex;
  align-items: center;
  gap: 2.5rem;
  list-style: none;
}
.nav-links a {
  font-family: var(--sans);
  font-size: 0.78rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--slate);
  text-decoration: none;
  position: relative;
  transition: color 0.3s;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -3px; left: 0;
  width: 0; height: 1px;
  background: var(--gold);
  transition: width 0.3s var(--transition);
}
.nav-links a:hover { color: var(--charcoal); }
.nav-links a:hover::after { width: 100%; }
.btn-nav {
  font-family: var(--sans);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--cream) !important;
  background: var(--charcoal);
  border: 1px solid var(--charcoal);
  padding: 0.6rem 1.6rem;
  text-decoration: none;
  transition: all 0.35s var(--transition) !important;
}
.btn-nav:hover {
  background: var(--gold) !important;
  border-color: var(--gold) !important;
  color: var(--charcoal) !important;
}
.btn-nav::after { display: none !important; }
.nav-mobile-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
  padding: 6px;
}
.nav-mobile-toggle span {
  display: block; width: 24px; height: 1.5px;
  background: var(--charcoal);
  transition: all 0.3s;
}

/* ─── HERO ─── */
#hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  background: var(--ivory);
}
.hero-parallax-bg {
  position: absolute;
  inset: -10%;
  background:
    radial-gradient(ellipse 80% 60% at 70% 40%, rgba(212,175,55,0.08) 0%, transparent 60%),
    radial-gradient(ellipse 60% 80% at 20% 80%, rgba(212,175,55,0.05) 0%, transparent 50%),
    linear-gradient(160deg, var(--ivory) 0%, var(--cream) 50%, var(--linen) 100%);
  transition: transform 0.1s linear;
  will-change: transform;
}
.hero-geo {
  position: absolute;
  top: 10%; right: 8%;
  width: 420px; height: 420px;
  border: 1px solid rgba(212,175,55,0.18);
  border-radius: 50%;
  animation: rotateSlow 40s linear infinite;
}
.hero-geo::before {
  content: '';
  position: absolute;
  inset: 30px;
  border: 1px solid rgba(212,175,55,0.10);
  border-radius: 50%;
}
.hero-geo::after {
  content: '';
  position: absolute;
  inset: 80px;
  border: 1px solid rgba(212,175,55,0.06);
  border-radius: 50%;
}
@keyframes rotateSlow { to { transform: rotate(360deg); } }
.hero-content {
  position: relative;
  z-index: 2;
  padding: 0 8%;
  max-width: 780px;
  padding-top: 72px;
}
.hero-tag {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--gold-dark);
  margin-bottom: 1.8rem;
}
.hero-tag::before {
  content: '';
  display: block;
  width: 28px; height: 1px;
  background: var(--gold);
}
.hero-h1 {
  font-family: var(--serif);
  font-size: clamp(2.8rem, 6vw, 5.2rem);
  font-weight: 300;
  line-height: 1.12;
  letter-spacing: -0.01em;
  color: var(--charcoal);
  margin-bottom: 1.8rem;
}
.hero-h1 em {
  font-style: italic;
  color: var(--gold-dark);
}
.hero-sub {
  font-size: 1.05rem;
  font-weight: 300;
  color: var(--slate);
  max-width: 520px;
  margin-bottom: 3rem;
  line-height: 1.8;
}
.hero-ctas {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  align-items: center;
}
.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-family: var(--sans);
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--cream);
  background: var(--charcoal);
  border: 1px solid var(--charcoal);
  padding: 0.9rem 2.2rem;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.35s var(--transition);
  position: relative;
  overflow: hidden;
}
.btn-primary::before {
  content: '';
  position: absolute;
  inset: 0;
  background: var(--gold);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.35s var(--transition);
  z-index: -1;
}
.btn-primary:hover {
  border-color: var(--gold);
  color: var(--charcoal);
}
.btn-primary:hover::before { transform: scaleX(1); }
.btn-secondary {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-family: var(--sans);
  font-size: 0.78rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--charcoal);
  background: transparent;
  border: 1px solid rgba(44,42,38,0.25);
  padding: 0.9rem 2.2rem;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.35s var(--transition);
}
.btn-secondary:hover {
  border-color: var(--gold);
  color: var(--gold-dark);
}
.hero-scroll {
  position: absolute;
  bottom: 2.5rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.68rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--slate);
  z-index: 2;
}
.hero-scroll-line {
  width: 1px; height: 50px;
  background: linear-gradient(to bottom, var(--gold), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes scrollPulse {
  0%,100% { opacity: 0.4; transform: scaleY(1); }
  50% { opacity: 1; transform: scaleY(1.2); }
}

/* ─── SECTION SHARED ─── */
section { padding: 7rem 8%; }
.section-label {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: var(--gold-dark);
  margin-bottom: 1rem;
}
.section-label::before {
  content: '';
  display: block; width: 22px; height: 1px;
  background: var(--gold);
}
.section-title {
  font-family: var(--serif);
  font-size: clamp(2rem, 4vw, 3.2rem);
  font-weight: 300;
  line-height: 1.2;
  color: var(--charcoal);
  margin-bottom: 1rem;
}
.section-title em { font-style: italic; color: var(--gold-dark); }
.section-sub {
  font-size: 0.95rem;
  font-weight: 300;
  color: var(--slate);
  max-width: 540px;
  line-height: 1.8;
  margin-bottom: 3.5rem;
}

/* ─── DEMOS SECTION ─── */
#demos { background: var(--ivory); }
.demo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
}
.demo-card {
  position: relative;
  overflow: hidden;
  cursor: pointer;
  background: var(--cream);
  border: 1px solid rgba(212,175,55,0.2);
  transition: all 0.5s var(--transition);
}
.demo-card:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-gold), 0 20px 60px rgba(44,42,38,0.1);
  border-color: var(--gold);
}
.demo-card-visual {
  height: 220px;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}
.demo-card-visual svg { width: 100%; height: 100%; }
.demo-card-overlay {
  position: absolute;
  inset: 0;
  background: rgba(44,42,38,0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.4s var(--transition);
}
.demo-card:hover .demo-card-overlay { opacity: 1; }
.btn-select {
  font-family: var(--sans);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--charcoal);
  background: var(--gold);
  border: none;
  padding: 0.75rem 1.8rem;
  cursor: pointer;
  transition: all 0.3s;
  transform: translateY(10px);
  transition: transform 0.4s var(--transition), background 0.3s;
}
.demo-card:hover .btn-select { transform: translateY(0); }
.btn-select:hover { background: var(--gold-light); }
.btn-select.selected {
  background: var(--charcoal);
  color: var(--gold);
}
.demo-card-info { padding: 1.4rem 1.6rem; }
.demo-card-tag {
  font-size: 0.68rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--gold-dark);
  margin-bottom: 0.4rem;
}
.demo-card-name {
  font-family: var(--serif);
  font-size: 1.35rem;
  font-weight: 400;
  color: var(--charcoal);
  margin-bottom: 0.4rem;
}
.demo-card-desc {
  font-size: 0.82rem;
  color: var(--slate);
  font-weight: 300;
  line-height: 1.6;
}
.selected-badge {
  position: absolute;
  top: 1rem; right: 1rem;
  background: var(--gold);
  color: var(--charcoal);
  font-size: 0.65rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 0.3rem 0.8rem;
  font-weight: 500;
  opacity: 0;
  transition: opacity 0.3s;
}
.demo-card.is-selected .selected-badge { opacity: 1; }

/* ─── PROCESS SECTION ─── */
#process { background: var(--cream); }
.process-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 2rem;
  counter-reset: process-counter;
}
.process-step {
  position: relative;
  padding: 2.5rem 2rem;
  border: 1px solid rgba(212,175,55,0.15);
  background: var(--ivory);
  counter-increment: process-counter;
  transition: all 0.4s var(--transition);
}
.process-step:hover {
  border-color: var(--gold);
  transform: translateY(-4px);
  box-shadow: var(--shadow-gold);
}
.process-step::before {
  content: counter(process-counter, decimal-leading-zero);
  font-family: var(--serif);
  font-size: 3.5rem;
  font-weight: 300;
  color: rgba(212,175,55,0.2);
  line-height: 1;
  margin-bottom: 1rem;
  display: block;
}
.process-step h3 {
  font-family: var(--serif);
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--charcoal);
  margin-bottom: 0.6rem;
}
.process-step p {
  font-size: 0.85rem;
  color: var(--slate);
  font-weight: 300;
  line-height: 1.7;
}

/* ─── PRICING ─── */
#pricing { background: var(--ivory); }
.pricing-toggle {
  display: inline-flex;
  align-items: center;
  gap: 1rem;
  background: var(--cream);
  border: 1px solid rgba(212,175,55,0.2);
  padding: 0.5rem 1rem;
  margin-bottom: 3rem;
  font-size: 0.8rem;
  letter-spacing: 0.1em;
  color: var(--slate);
}
.toggle-switch {
  position: relative;
  width: 44px; height: 22px;
  cursor: pointer;
}
.toggle-switch input { opacity: 0; width: 0; height: 0; }
.toggle-slider {
  position: absolute;
  inset: 0;
  background: rgba(44,42,38,0.15);
  border-radius: 22px;
  transition: 0.3s;
}
.toggle-slider::before {
  content: '';
  position: absolute;
  left: 3px; top: 3px;
  width: 16px; height: 16px;
  background: var(--charcoal);
  border-radius: 50%;
  transition: 0.3s;
}
.toggle-switch input:checked + .toggle-slider { background: var(--gold); }
.toggle-switch input:checked + .toggle-slider::before { transform: translateX(22px); background: var(--cream); }
.pricing-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  align-items: start;
}
.pricing-card {
  border: 1px solid rgba(212,175,55,0.2);
  background: var(--cream);
  padding: 2.5rem 2rem;
  position: relative;
  transition: all 0.4s var(--transition);
}
.pricing-card.featured {
  background: var(--charcoal);
  border-color: var(--gold);
  transform: scale(1.03);
}
.pricing-card:hover:not(.featured) {
  border-color: var(--gold);
  box-shadow: var(--shadow-gold);
  transform: translateY(-4px);
}
.pricing-badge {
  display: inline-block;
  font-size: 0.65rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--charcoal);
  background: var(--gold);
  padding: 0.25rem 0.8rem;
  margin-bottom: 1.2rem;
  font-weight: 500;
}
.pricing-name {
  font-family: var(--serif);
  font-size: 1.5rem;
  font-weight: 400;
  color: var(--charcoal);
  margin-bottom: 0.3rem;
}
.pricing-card.featured .pricing-name { color: var(--cream); }
.pricing-price {
  font-family: var(--serif);
  font-size: 2.8rem;
  font-weight: 300;
  color: var(--charcoal);
  line-height: 1;
  margin-bottom: 0.4rem;
}
.pricing-card.featured .pricing-price { color: var(--gold); }
.pricing-price sup {
  font-size: 1.2rem;
  vertical-align: super;
  margin-right: 2px;
}
.pricing-period {
  font-size: 0.78rem;
  color: var(--slate);
  margin-bottom: 2rem;
  letter-spacing: 0.08em;
}
.pricing-card.featured .pricing-period { color: rgba(250,247,242,0.5); }
.pricing-divider {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(212,175,55,0.3), transparent);
  margin-bottom: 1.8rem;
}
.pricing-card.featured .pricing-divider { background: linear-gradient(90deg, transparent, rgba(212,175,55,0.5), transparent); }
.pricing-features {
  list-style: none;
  margin-bottom: 2rem;
}
.pricing-features li {
  font-size: 0.85rem;
  font-weight: 300;
  color: var(--bronze);
  padding: 0.5rem 0;
  border-bottom: 1px solid rgba(212,175,55,0.1);
  display: flex;
  align-items: center;
  gap: 0.6rem;
}
.pricing-card.featured .pricing-features li { color: rgba(250,247,242,0.8); border-bottom-color: rgba(212,175,55,0.15); }
.pricing-features li::before {
  content: '✦';
  color: var(--gold);
  font-size: 0.55rem;
  flex-shrink: 0;
}
.btn-pricing {
  width: 100%;
  font-family: var(--sans);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  padding: 0.9rem;
  cursor: pointer;
  transition: all 0.35s var(--transition);
  border: 1px solid var(--charcoal);
  background: transparent;
  color: var(--charcoal);
}
.pricing-card.featured .btn-pricing {
  background: var(--gold);
  border-color: var(--gold);
  color: var(--charcoal);
}
.btn-pricing:hover {
  background: var(--charcoal);
  color: var(--cream);
}
.pricing-card.featured .btn-pricing:hover {
  background: var(--gold-light);
  border-color: var(--gold-light);
}

/* ─── INTAKE FORM ─── */
#intake { background: var(--linen); }
.form-wrapper {
  max-width: 780px;
  margin: 0 auto;
  background: var(--ivory);
  border: 1px solid rgba(212,175,55,0.2);
  padding: 0;
  overflow: hidden;
}
.form-progress {
  display: flex;
  background: var(--cream);
  border-bottom: 1px solid rgba(212,175,55,0.15);
}
.form-step-tab {
  flex: 1;
  padding: 1.2rem 1rem;
  text-align: center;
  font-size: 0.7rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--slate);
  cursor: pointer;
  position: relative;
  transition: all 0.3s;
  border-bottom: 2px solid transparent;
}
.form-step-tab.active {
  color: var(--gold-dark);
  border-bottom-color: var(--gold);
  background: var(--ivory);
}
.form-step-tab .step-num {
  display: block;
  font-family: var(--serif);
  font-size: 1.4rem;
  font-weight: 300;
  margin-bottom: 0.1rem;
  color: inherit;
}
.form-body { padding: 3rem; }
.form-step { display: none; animation: fadeStep 0.4s var(--transition); }
.form-step.active { display: block; }
@keyframes fadeStep {
  from { opacity: 0; transform: translateX(20px); }
  to   { opacity: 1; transform: translateX(0); }
}
.form-step h3 {
  font-family: var(--serif);
  font-size: 1.6rem;
  font-weight: 300;
  color: var(--charcoal);
  margin-bottom: 0.4rem;
}
.form-step .step-desc {
  font-size: 0.85rem;
  color: var(--slate);
  margin-bottom: 2rem;
  font-weight: 300;
}
.form-group { margin-bottom: 1.5rem; }
.form-group label {
  display: block;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--bronze);
  margin-bottom: 0.5rem;
}
.form-control {
  width: 100%;
  background: var(--cream);
  border: 1px solid rgba(212,175,55,0.2);
  padding: 0.9rem 1rem;
  font-family: var(--sans);
  font-size: 0.9rem;
  font-weight: 300;
  color: var(--charcoal);
  outline: none;
  transition: border-color 0.3s;
}
.form-control:focus { border-color: var(--gold); }
.form-control::placeholder { color: rgba(107,101,96,0.5); }
select.form-control { cursor: pointer; appearance: none; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M0 0l5 6 5-6z' fill='%23D4AF37'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 1rem center; }
textarea.form-control { resize: vertical; min-height: 120px; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
.style-select-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.8rem;
  margin-top: 0.5rem;
}
.style-option {
  border: 1px solid rgba(212,175,55,0.2);
  padding: 1rem;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s;
  background: var(--cream);
}
.style-option:hover { border-color: var(--gold); }
.style-option.active { border-color: var(--gold); background: rgba(212,175,55,0.08); }
.style-option .style-icon { font-size: 1.5rem; margin-bottom: 0.4rem; }
.style-option .style-name { font-size: 0.72rem; font-weight: 500; letter-spacing: 0.1em; text-transform: uppercase; color: var(--charcoal); }
.budget-range { display: grid; grid-template-columns: repeat(2,1fr); gap: 0.8rem; }
.budget-option {
  border: 1px solid rgba(212,175,55,0.2);
  padding: 1rem;
  cursor: pointer;
  transition: all 0.3s;
  background: var(--cream);
  text-align: center;
}
.budget-option:hover { border-color: var(--gold); }
.budget-option.active { border-color: var(--gold); background: rgba(212,175,55,0.08); }
.budget-option .b-range { font-family: var(--serif); font-size: 1.1rem; color: var(--charcoal); }
.budget-option .b-desc { font-size: 0.7rem; color: var(--slate); margin-top: 0.2rem; }
.form-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 2.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(212,175,55,0.15);
}
.btn-form {
  font-family: var(--sans);
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  padding: 0.8rem 2rem;
  cursor: pointer;
  transition: all 0.35s;
  border: 1px solid;
}
.btn-form-next {
  background: var(--charcoal);
  border-color: var(--charcoal);
  color: var(--cream);
}
.btn-form-next:hover { background: var(--gold); border-color: var(--gold); color: var(--charcoal); }
.btn-form-back {
  background: transparent;
  border-color: rgba(44,42,38,0.2);
  color: var(--slate);
}
.btn-form-back:hover { border-color: var(--charcoal); color: var(--charcoal); }
.btn-form-submit {
  background: var(--gold);
  border-color: var(--gold);
  color: var(--charcoal);
}
.btn-form-submit:hover { background: var(--charcoal); border-color: var(--charcoal); color: var(--cream); }
.form-success {
  text-align: center;
  padding: 3rem;
  display: none;
}
.form-success.show { display: block; }
.success-icon { font-size: 3rem; margin-bottom: 1rem; }
.form-success h3 { font-family: var(--serif); font-size: 2rem; font-weight: 300; color: var(--charcoal); margin-bottom: 0.5rem; }
.form-success p { color: var(--slate); font-size: 0.9rem; }

/* ─── CHATBOT ─── */
#chatbot-toggle {
  position: fixed;
  bottom: 2rem; right: 2rem;
  width: 60px; height: 60px;
  background: var(--charcoal);
  border: 2px solid var(--gold);
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 500;
  box-shadow: 0 8px 32px rgba(44,42,38,0.25), 0 0 0 0 rgba(212,175,55,0.3);
  animation: chatPulse 3s ease-in-out infinite;
  transition: all 0.3s;
}
#chatbot-toggle:hover { transform: scale(1.08); }
@keyframes chatPulse {
  0%,100% { box-shadow: 0 8px 32px rgba(44,42,38,0.25), 0 0 0 0 rgba(212,175,55,0.3); }
  50% { box-shadow: 0 8px 32px rgba(44,42,38,0.25), 0 0 0 10px rgba(212,175,55,0); }
}
.chat-icon { font-size: 1.4rem; }
#chatbot-panel {
  position: fixed;
  bottom: 6.5rem; right: 2rem;
  width: 360px;
  max-height: 520px;
  background: var(--ivory);
  border: 1px solid var(--glass-border);
  box-shadow: 0 20px 60px rgba(44,42,38,0.18), var(--shadow-gold);
  z-index: 500;
  display: flex;
  flex-direction: column;
  transform: scale(0.9) translateY(20px);
  transform-origin: bottom right;
  opacity: 0;
  pointer-events: none;
  transition: all 0.35s var(--transition);
}
#chatbot-panel.open {
  transform: scale(1) translateY(0);
  opacity: 1;
  pointer-events: all;
}
.chat-header {
  background: var(--charcoal);
  padding: 1.2rem 1.4rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid rgba(212,175,55,0.2);
}
.chat-header-info { display: flex; align-items: center; gap: 0.8rem; }
.chat-avatar {
  width: 36px; height: 36px;
  background: var(--gold);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  flex-shrink: 0;
}
.chat-name {
  font-family: var(--sans);
  font-size: 0.82rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  color: var(--cream);
}
.chat-status {
  font-size: 0.68rem;
  color: rgba(212,175,55,0.7);
  letter-spacing: 0.06em;
}
.chat-close {
  background: none;
  border: none;
  color: rgba(250,247,242,0.5);
  font-size: 1.2rem;
  cursor: pointer;
  transition: color 0.2s;
  line-height: 1;
}
.chat-close:hover { color: var(--cream); }
.chat-messages {
  flex: 1;
  overflow-y: auto;
  padding: 1.2rem;
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  scrollbar-width: thin;
  scrollbar-color: var(--gold) transparent;
}
.chat-bubble {
  max-width: 85%;
  padding: 0.8rem 1rem;
  font-size: 0.82rem;
  line-height: 1.6;
  font-weight: 300;
  animation: bubbleIn 0.3s var(--transition);
}
@keyframes bubbleIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}
.chat-bubble.bot {
  background: var(--cream);
  border: 1px solid rgba(212,175,55,0.15);
  color: var(--charcoal);
  align-self: flex-start;
  border-radius: 0 8px 8px 8px;
}
.chat-bubble.user {
  background: var(--charcoal);
  color: var(--cream);
  align-self: flex-end;
  border-radius: 8px 8px 0 8px;
}
.chat-typing {
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 0.8rem 1rem;
  background: var(--cream);
  border: 1px solid rgba(212,175,55,0.15);
  align-self: flex-start;
  width: fit-content;
  border-radius: 0 8px 8px 8px;
}
.chat-typing span {
  width: 6px; height: 6px;
  background: var(--gold);
  border-radius: 50%;
  animation: typingBounce 1.2s ease-in-out infinite;
}
.chat-typing span:nth-child(2) { animation-delay: 0.2s; }
.chat-typing span:nth-child(3) { animation-delay: 0.4s; }
@keyframes typingBounce {
  0%,80%,100% { transform: translateY(0); opacity: 0.4; }
  40% { transform: translateY(-6px); opacity: 1; }
}
.chat-input-row {
  display: flex;
  border-top: 1px solid rgba(212,175,55,0.15);
}
.chat-input {
  flex: 1;
  background: var(--cream);
  border: none;
  padding: 0.9rem 1rem;
  font-family: var(--sans);
  font-size: 0.82rem;
  font-weight: 300;
  color: var(--charcoal);
  outline: none;
}
.chat-input::placeholder { color: rgba(107,101,96,0.4); }
.chat-send {
  background: var(--gold);
  border: none;
  padding: 0.9rem 1.2rem;
  cursor: pointer;
  font-size: 1rem;
  transition: background 0.2s;
  color: var(--charcoal);
}
.chat-send:hover { background: var(--gold-light); }
.quick-replies {
  padding: 0.6rem 1.2rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  border-top: 1px solid rgba(212,175,55,0.1);
  background: var(--cream);
}
.quick-reply {
  font-size: 0.7rem;
  letter-spacing: 0.06em;
  padding: 0.3rem 0.8rem;
  border: 1px solid rgba(212,175,55,0.3);
  background: transparent;
  color: var(--bronze);
  cursor: pointer;
  transition: all 0.2s;
}
.quick-reply:hover { background: var(--gold); border-color: var(--gold); color: var(--charcoal); }

/* ─── STATS ─── */
#stats {
  background: var(--charcoal);
  padding: 5rem 8%;
}
.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 2rem;
  text-align: center;
}
.stat-item {}
.stat-number {
  font-family: var(--serif);
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 300;
  color: var(--gold);
  line-height: 1;
  margin-bottom: 0.4rem;
}
.stat-label {
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: rgba(245,240,232,0.5);
}

/* ─── FOOTER ─── */
footer {
  background: #1A1815;
  padding: 5rem 8% 2.5rem;
  color: rgba(245,240,232,0.6);
}
.footer-grid {
  display: grid;
  grid-template-columns: 1.8fr 1fr 1fr;
  gap: 4rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid rgba(212,175,55,0.1);
  margin-bottom: 2rem;
}
.footer-brand .nav-logo {
  color: var(--cream);
  margin-bottom: 1rem;
  display: inline-flex;
}
.footer-brand p {
  font-size: 0.85rem;
  line-height: 1.8;
  max-width: 280px;
}
.footer-col h4 {
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 1.4rem;
}
.footer-col ul { list-style: none; }
.footer-col ul li { margin-bottom: 0.6rem; }
.footer-col ul li a {
  font-size: 0.85rem;
  color: rgba(245,240,232,0.5);
  text-decoration: none;
  transition: color 0.3s;
  letter-spacing: 0.04em;
}
.footer-col ul li a:hover { color: var(--gold); }
.footer-contact-item {
  display: flex;
  align-items: flex-start;
  gap: 0.6rem;
  margin-bottom: 0.7rem;
  font-size: 0.83rem;
}
.contact-icon { color: var(--gold); font-size: 0.9rem; flex-shrink: 0; }
.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 0.75rem;
  letter-spacing: 0.06em;
  flex-wrap: wrap;
  gap: 0.5rem;
}
.footer-bottom a { color: var(--gold); text-decoration: none; }

/* ─── RESPONSIVE ─── */
@media (max-width: 900px) {
  .nav-links { display: none; }
  .nav-mobile-toggle { display: flex; }
  .footer-grid { grid-template-columns: 1fr 1fr; gap: 2.5rem; }
  .footer-brand { grid-column: 1 / -1; }
  .form-row { grid-template-columns: 1fr; }
  .style-select-grid { grid-template-columns: repeat(3,1fr); gap: 0.5rem; }
  #chatbot-panel { width: calc(100vw - 2.5rem); right: 1.25rem; }
}
@media (max-width: 600px) {
  section { padding: 5rem 5%; }
  .hero-content { padding: 0 5%; padding-top: 72px; }
  .footer-grid { grid-template-columns: 1fr; }
  .pricing-card.featured { transform: scale(1); }
  .form-body { padding: 1.8rem; }
  .style-select-grid { grid-template-columns: repeat(2,1fr); }
  .budget-range { grid-template-columns: 1fr; }
  .hero-geo { width: 250px; height: 250px; top: 15%; right: 2%; opacity: 0.5; }
}

/* ─── MOBILE NAV OPEN ─── */
.mobile-nav-open .nav-links {
  display: flex;
  flex-direction: column;
  position: fixed;
  inset: 0;
  background: var(--ivory);
  align-items: center;
  justify-content: center;
  gap: 2.5rem;
  z-index: 99;
}
.mobile-nav-open .nav-links a {
  font-size: 1.8rem;
  font-family: var(--serif);
  font-weight: 300;
  letter-spacing: 0.04em;
  text-transform: none;
}
.mobile-nav-open .btn-nav {
  font-size: 1rem !important;
  padding: 1rem 3rem !important;
}
</style>
</head>
<body>

<!-- ─── NAVIGATION ─── -->
<nav id="main-nav">
  <a href="#" class="nav-logo">Mikmagic<span>✨</span></a>
  <ul class="nav-links">
    <li><a href="#demos">Demos</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#process">Process</a></li>
    <li><a href="#intake" class="btn-nav">Start Project</a></li>
  </ul>
  <div class="nav-mobile-toggle" id="mobileToggle" onclick="toggleMobileNav()">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- ─── HERO ─── -->
<section id="hero">
  <div class="hero-parallax-bg" id="parallaxBg"></div>
  <div class="hero-geo"></div>
  <div class="hero-content">
    <div class="hero-tag reveal">Digital Architecture</div>
    <h1 class="hero-h1 reveal reveal-delay-1">Digital Architecture<br/>for the <em>Modern</em><br/>Visionary.</h1>
    <p class="hero-sub reveal reveal-delay-2">We craft bespoke digital experiences that command attention, convert visitors into clients, and position your brand at the apex of your industry.</p>
    <div class="hero-ctas reveal reveal-delay-3">
      <a href="#intake" class="btn-primary">Begin Your Project ↗</a>
      <a href="#demos" class="btn-secondary">View Demos</a>
    </div>
  </div>
  <div class="hero-scroll">
    <div class="hero-scroll-line"></div>
    <span>Scroll</span>
  </div>
</section>

<!-- ─── STATS ─── -->
<section id="stats">
  <div class="stats-grid">
    <div class="stat-item reveal"><div class="stat-number" data-count="47">0</div><div class="stat-label">Projects Delivered</div></div>
    <div class="stat-item reveal reveal-delay-1"><div class="stat-number" data-count="98">0</div><div class="stat-label">Client Satisfaction</div></div>
    <div class="stat-item reveal reveal-delay-2"><div class="stat-number" data-count="5">0</div><div class="stat-label">Years of Mastery</div></div>
    <div class="stat-item reveal reveal-delay-3"><div class="stat-number" data-count="3">0</div><div class="stat-label">Avg. Turnaround (Days)</div></div>
  </div>
</section>

<!-- ─── DEMOS ─── -->
<section id="demos">
  <div class="section-label reveal">Portfolio Styles</div>
  <h2 class="section-title reveal">Choose Your <em>Aesthetic</em></h2>
  <p class="section-sub reveal">Each template is a fully engineered digital experience. Select the style that resonates — we'll tailor it entirely to your vision.</p>

  <div class="demo-grid">

    <!-- Card 1 -->
    <div class="demo-card reveal" id="demo-minimalist">
      <div class="selected-badge">✦ Selected</div>
      <div class="demo-card-visual">
        <svg viewBox="0 0 400 220" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="220" fill="#FAF7F2"/>
          <rect x="0" y="0" width="400" height="3" fill="#D4AF37" opacity="0.6"/>
          <rect x="30" y="30" width="60" height="8" rx="2" fill="#2C2A26" opacity="0.15"/>
          <rect x="30" y="70" width="200" height="20" rx="2" fill="#2C2A26" opacity="0.6"/>
          <rect x="30" y="100" width="160" height="12" rx="2" fill="#2C2A26" opacity="0.3"/>
          <rect x="30" y="120" width="140" height="12" rx="2" fill="#2C2A26" opacity="0.2"/>
          <rect x="30" y="150" width="90" height="28" rx="1" fill="#D4AF37" opacity="0.8"/>
          <rect x="260" y="50" width="110" height="140" rx="2" fill="#EDE8DE"/>
          <rect x="275" y="65" width="80" height="60" rx="1" fill="#D4AF37" opacity="0.15"/>
          <line x1="275" y1="145" x2="355" y2="145" stroke="#D4AF37" strokeWidth="0.5" opacity="0.5"/>
          <rect x="275" y="155" width="60" height="6" rx="1" fill="#2C2A26" opacity="0.15"/>
          <rect x="275" y="168" width="40" height="6" rx="1" fill="#2C2A26" opacity="0.1"/>
        </svg>
        <div class="demo-card-overlay">
          <button class="btn-select" onclick="selectDemo('minimalist', this)">Select This Style</button>
        </div>
      </div>
      <div class="demo-card-info">
        <div class="demo-card-tag">Portfolio & Personal</div>
        <div class="demo-card-name">The Minimalist</div>
        <p class="demo-card-desc">Elevated whitespace, refined typography. For consultants, creatives, and thought leaders who let their work speak.</p>
      </div>
    </div>

    <!-- Card 2 -->
    <div class="demo-card reveal reveal-delay-1" id="demo-powerplayer">
      <div class="selected-badge">✦ Selected</div>
      <div class="demo-card-visual">
        <svg viewBox="0 0 400 220" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="220" fill="#1A1815"/>
          <rect x="0" y="0" width="400" height="220" fill="url(#g1)"/>
          <defs><linearGradient id="g1" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#2C2A26"/><stop offset="100%" stop-color="#1A1815"/></linearGradient></defs>
          <rect x="0" y="0" width="400" height="2" fill="#D4AF37" opacity="0.8"/>
          <rect x="30" y="25" width="50" height="6" rx="1" fill="#D4AF37" opacity="0.6"/>
          <rect x="30" y="70" width="240" height="28" rx="2" fill="#FAF7F2" opacity="0.85"/>
          <rect x="30" y="108" width="200" height="14" rx="2" fill="#FAF7F2" opacity="0.25"/>
          <rect x="30" y="130" width="80" height="28" rx="1" fill="#D4AF37"/>
          <rect x="120" y="130" width="80" height="28" rx="1" fill="transparent" stroke="#D4AF37" strokeWidth="1" opacity="0.5"/>
          <rect x="270" y="55" width="100" height="140" rx="2" fill="#D4AF37" opacity="0.08" stroke="#D4AF37" strokeWidth="0.5"/>
          <rect x="285" y="70" width="70" height="40" rx="1" fill="#D4AF37" opacity="0.15"/>
          <rect x="285" y="120" width="50" height="5" rx="1" fill="#FAF7F2" opacity="0.2"/>
          <rect x="285" y="132" width="35" height="5" rx="1" fill="#FAF7F2" opacity="0.15"/>
          <rect x="285" y="145" width="55" height="18" rx="1" fill="#D4AF37" opacity="0.5"/>
          <circle cx="340" cy="185" r="10" fill="#D4AF37" opacity="0.2" stroke="#D4AF37" strokeWidth="0.5"/>
        </svg>
        <div class="demo-card-overlay">
          <button class="btn-select" onclick="selectDemo('powerplayer', this)">Select This Style</button>
        </div>
      </div>
      <div class="demo-card-info">
        <div class="demo-card-tag">Corporate & Finance</div>
        <div class="demo-card-name">The Power Player</div>
        <p class="demo-card-desc">Dark luxury aesthetic commanding authority. Ideal for law firms, investment houses, and executive brands.</p>
      </div>
    </div>

    <!-- Card 3 -->
    <div class="demo-card reveal reveal-delay-2" id="demo-ecommerce">
      <div class="selected-badge">✦ Selected</div>
      <div class="demo-card-visual">
        <svg viewBox="0 0 400 220" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="220" fill="#F5F0E8"/>
          <rect x="0" y="0" width="400" height="40" fill="#FAF7F2"/>
          <rect x="20" y="15" width="40" height="8" rx="1" fill="#2C2A26" opacity="0.5"/>
          <rect x="300" y="12" width="14" height="14" rx="2" fill="#D4AF37" opacity="0.8"/>
          <rect x="320" y="12" width="14" height="14" rx="2" fill="#2C2A26" opacity="0.2"/>
          <rect x="340" y="12" width="14" height="14" rx="2" fill="#2C2A26" opacity="0.2"/>
          <rect x="20" y="55" width="110" height="130" rx="2" fill="#EDE8DE"/>
          <rect x="35" y="65" width="80" height="70" rx="1" fill="#D4AF37" opacity="0.18"/>
          <rect x="35" y="143" width="55" height="7" rx="1" fill="#2C2A26" opacity="0.4"/>
          <rect x="35" y="157" width="40" height="6" rx="1" fill="#D4AF37" opacity="0.8"/>
          <rect x="145" y="55" width="110" height="130" rx="2" fill="#EDE8DE"/>
          <rect x="160" y="65" width="80" height="70" rx="1" fill="#2C2A26" opacity="0.08"/>
          <rect x="160" y="143" width="55" height="7" rx="1" fill="#2C2A26" opacity="0.4"/>
          <rect x="160" y="157" width="40" height="6" rx="1" fill="#D4AF37" opacity="0.8"/>
          <rect x="270" y="55" width="110" height="130" rx="2" fill="#EDE8DE"/>
          <rect x="285" y="65" width="80" height="70" rx="1" fill="#D4AF37" opacity="0.25"/>
          <rect x="285" y="143" width="55" height="7" rx="1" fill="#2C2A26" opacity="0.4"/>
          <rect x="285" y="157" width="40" height="6" rx="1" fill="#D4AF37" opacity="0.8"/>
        </svg>
        <div class="demo-card-overlay">
          <button class="btn-select" onclick="selectDemo('ecommerce', this)">Select This Style</button>
        </div>
      </div>
      <div class="demo-card-info">
        <div class="demo-card-tag">E-Commerce & Retail</div>
        <div class="demo-card-name">The Boutique</div>
        <p class="demo-card-desc">Conversion-first luxury storefront. Premium product presentation for brands that refuse to settle for ordinary.</p>
      </div>
    </div>

    <!-- Card 4 -->
    <div class="demo-card reveal" id="demo-creative">
      <div class="selected-badge">✦ Selected</div>
      <div class="demo-card-visual">
        <svg viewBox="0 0 400 220" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="220" fill="#F8F5EE"/>
          <circle cx="320" cy="40" r="80" fill="#D4AF37" opacity="0.07"/>
          <circle cx="80" cy="180" r="60" fill="#2C2A26" opacity="0.04"/>
          <rect x="30" y="30" width="8" height="160" rx="2" fill="#D4AF37" opacity="0.4"/>
          <rect x="55" y="55" width="180" height="30" rx="2" fill="#2C2A26" opacity="0.65"/>
          <rect x="55" y="95" width="130" height="12" rx="2" fill="#2C2A26" opacity="0.2"/>
          <rect x="55" y="115" width="100" height="12" rx="2" fill="#2C2A26" opacity="0.15"/>
          <rect x="55" y="145" width="70" height="24" rx="12" fill="#D4AF37" opacity="0.9"/>
          <rect x="240" y="50" width="130" height="130" rx="4" fill="#EDE8DE"/>
          <rect x="255" y="65" width="100" height="70" rx="2" fill="url(#g2)"/>
          <defs><linearGradient id="g2" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#D4AF37" stop-opacity="0.3"/><stop offset="100%" stop-color="#2C2A26" stop-opacity="0.1"/></linearGradient></defs>
          <rect x="255" y="145" width="70" height="6" rx="1" fill="#2C2A26" opacity="0.2"/>
          <rect x="255" y="158" width="50" height="6" rx="1" fill="#2C2A26" opacity="0.12"/>
        </svg>
        <div class="demo-card-overlay">
          <button class="btn-select" onclick="selectDemo('creative', this)">Select This Style</button>
        </div>
      </div>
      <div class="demo-card-info">
        <div class="demo-card-tag">Agency & Creative</div>
        <div class="demo-card-name">The Creative</div>
        <p class="demo-card-desc">Bold editorial design with asymmetric layouts. For agencies, studios, and brands with a strong visual point of view.</p>
      </div>
    </div>

    <!-- Card 5 -->
    <div class="demo-card reveal reveal-delay-1" id="demo-saas">
      <div class="selected-badge">✦ Selected</div>
      <div class="demo-card-visual">
        <svg viewBox="0 0 400 220" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="220" fill="#F5F0E8"/>
          <rect x="0" y="0" width="80" height="220" fill="#2C2A26"/>
          <rect x="10" y="20" width="60" height="8" rx="2" fill="#D4AF37" opacity="0.8"/>
          <rect x="15" y="50" width="50" height="6" rx="1" fill="#FAF7F2" opacity="0.15"/>
          <rect x="15" y="64" width="50" height="6" rx="1" fill="#FAF7F2" opacity="0.1"/>
          <rect x="15" y="78" width="50" height="6" rx="1" fill="#FAF7F2" opacity="0.1"/>
          <rect x="15" y="92" width="50" height="6" rx="1" fill="#D4AF37" opacity="0.6"/>
          <rect x="15" y="106" width="50" height="6" rx="1" fill="#FAF7F2" opacity="0.1"/>
          <rect x="95" y="20" width="160" height="70" rx="2" fill="#FAF7F2" stroke="#EDE8DE" strokeWidth="1"/>
          <rect x="108" y="32" width="60" height="8" rx="1" fill="#2C2A26" opacity="0.3"/>
          <rect x="108" y="50" width="100" height="20" rx="1" fill="#D4AF37" opacity="0.2"/>
          <rect x="270" y="20" width="110" height="70" rx="2" fill="#FAF7F2" stroke="#EDE8DE" strokeWidth="1"/>
          <rect x="283" y="32" width="50" height="8" rx="1" fill="#2C2A26" opacity="0.3"/>
          <rect x="283" y="50" width="84" height="20" rx="1" fill="#2C2A26" opacity="0.08"/>
          <rect x="95" y="105" width="285" height="95" rx="2" fill="#FAF7F2" stroke="#EDE8DE" strokeWidth="1"/>
          <rect x="108" y="118" width="100" height="6" rx="1" fill="#2C2A26" opacity="0.3"/>
          <rect x="108" y="132" width="245" height="40" rx="1" fill="#EDE8DE"/>
          <rect x="120" y="142" width="60" height="4" rx="1" fill="#D4AF37" opacity="0.6"/>
          <rect x="120" y="152" width="40" height="4" rx="1" fill="#2C2A26" opacity="0.2"/>
        </svg>
        <div class="demo-card-overlay">
          <button class="btn-select" onclick="selectDemo('saas', this)">Select This Style</button>
        </div>
      </div>
      <div class="demo-card-info">
        <div class="demo-card-tag">SaaS & Tech</div>
        <div class="demo-card-name">The Dashboard</div>
        <p class="demo-card-desc">Clean, functional SaaS interface with a sophisticated sidebar layout. Built for tech products that demand clarity.</p>
      </div>
    </div>

    <!-- Card 6 -->
    <div class="demo-card reveal reveal-delay-2" id="demo-hospitality">
      <div class="selected-badge">✦ Selected</div>
      <div class="demo-card-visual">
        <svg viewBox="0 0 400 220" xmlns="http://www.w3.org/2000/svg">
          <rect width="400" height="220" fill="#1A1815"/>
          <rect width="400" height="220" fill="url(#g3)" opacity="0.7"/>
          <defs>
            <linearGradient id="g3" x1="0" y1="0" x2="0" y2="1">
              <stop offset="0%" stop-color="#4A3F2F" stop-opacity="0.8"/>
              <stop offset="100%" stop-color="#1A1815"/>
            </linearGradient>
          </defs>
          <rect x="0" y="0" width="400" height="2" fill="#D4AF37" opacity="0.5"/>
          <text x="200" y="75" text-anchor="middle" font-family="Georgia,serif" font-size="10" fill="#D4AF37" opacity="0.6" letter-spacing="6">MIKMAGIC</text>
          <text x="200" y="110" text-anchor="middle" font-family="Georgia,serif" font-size="22" fill="#FAF7F2" opacity="0.9">Luxury Stays</text>
          <text x="200" y="132" text-anchor="middle" font-family="Georgia,serif" font-size="9" fill="#FAF7F2" opacity="0.4" letter-spacing="4">HOSPITALITY REDEFINED</text>
          <rect x="140" y="150" width="120" height="26" rx="0" fill="none" stroke="#D4AF37" strokeWidth="0.8" opacity="0.7"/>
          <text x="200" y="167" text-anchor="middle" font-family="sans-serif" font-size="7" fill="#D4AF37" letter-spacing="3">EXPLORE</text>
          <circle cx="200" cy="40" r="18" fill="none" stroke="#D4AF37" strokeWidth="0.5" opacity="0.4"/>
          <circle cx="200" cy="40" r="10" fill="none" stroke="#D4AF37" strokeWidth="0.5" opacity="0.25"/>
        </svg>
        <div class="demo-card-overlay">
          <button class="btn-select" onclick="selectDemo('hospitality', this)">Select This Style</button>
        </div>
      </div>
      <div class="demo-card-info">
        <div class="demo-card-tag">Hospitality & Luxury</div>
        <div class="demo-card-name">The Grand</div>
        <p class="demo-card-desc">Full-screen immersive luxury for hotels, spas, restaurants, and experiences that define a world apart.</p>
      </div>
    </div>

  </div>
</section>

<!-- ─── PROCESS ─── -->
<section id="process">
  <div class="section-label reveal">How It Works</div>
  <h2 class="section-title reveal">The <em>Atelier</em> Process</h2>
  <p class="section-sub reveal">Four refined steps from brief to launch. No guesswork, no delays — only precision.</p>
  <div class="process-grid">
    <div class="process-step reveal">
      <h3>Discovery Call</h3>
      <p>A 30-minute strategy session to understand your brand, audience, and competitive landscape. We define the north star before writing a single line of code.</p>
    </div>
    <div class="process-step reveal reveal-delay-1">
      <h3>Design Proposal</h3>
      <p>Within 48 hours, you receive a bespoke design direction — palette, typography, layout hierarchy — tailored precisely to your brand positioning.</p>
    </div>
    <div class="process-step reveal reveal-delay-2">
      <h3>Development Sprint</h3>
      <p>Rapid, meticulous build using modern technology. Daily progress updates. You see your vision take form in real time, with full input at every stage.</p>
    </div>
    <div class="process-step reveal reveal-delay-3">
      <h3>Launch & Retain</h3>
      <p>We deploy, test, and optimize. Then we hand you the keys — with full documentation, training, and an optional ongoing retainer for continued excellence.</p>
    </div>
  </div>
</section>

<!-- ─── PRICING ─── -->
<section id="pricing">
  <div class="section-label reveal">Investment</div>
  <h2 class="section-title reveal">Transparent <em>Pricing</em></h2>
  <p class="section-sub reveal">No hidden fees. No scope creep surprises. Choose the tier that matches your ambition.</p>

  <div class="pricing-toggle reveal">
    <span id="currency-label-inr" style="color:var(--charcoal);font-weight:500">₹ INR</span>
    <label class="toggle-switch">
      <input type="checkbox" id="currencyToggle" onchange="toggleCurrency()"/>
      <span class="toggle-slider"></span>
    </label>
    <span id="currency-label-usd">$ USD</span>
  </div>

  <div class="pricing-grid">

    <div class="pricing-card reveal">
      <div class="pricing-name">Essentials</div>
      <div class="pricing-price">
        <sup class="currency-symbol">₹</sup>
        <span class="price-value" data-inr="49,999" data-usd="599">49,999</span>
      </div>
      <div class="pricing-period">One-time · 7–10 day delivery</div>
      <div class="pricing-divider"></div>
      <ul class="pricing-features">
        <li>5-Page Custom Website</li>
        <li>Mobile-First Responsive Design</li>
        <li>Contact Form Integration</li>
        <li>Basic SEO Setup</li>
        <li>1 Round of Revisions</li>
        <li>30-Day Post-Launch Support</li>
      </ul>
      <button class="btn-pricing" onclick="document.getElementById('intake').scrollIntoView({behavior:'smooth'})">Begin with Essentials</button>
    </div>

    <div class="pricing-card featured reveal reveal-delay-1">
      <div class="pricing-badge">Most Popular</div>
      <div class="pricing-name">Signature</div>
      <div class="pricing-price">
        <sup class="currency-symbol">₹</sup>
        <span class="price-value" data-inr="1,49,999" data-usd="1,799">1,49,999</span>
      </div>
      <div class="pricing-period">One-time · 14–21 day delivery</div>
      <div class="pricing-divider"></div>
      <ul class="pricing-features">
        <li>10-Page Bespoke Website</li>
        <li>Custom Animations & Micro-interactions</li>
        <li>CMS Integration (Sanity/Contentful)</li>
        <li>Advanced SEO & Performance</li>
        <li>3 Rounds of Revisions</li>
        <li>E-Commerce (up to 50 products)</li>
        <li>90-Day Priority Support</li>
      </ul>
      <button class="btn-pricing" onclick="document.getElementById('intake').scrollIntoView({behavior:'smooth'})">Begin with Signature</button>
    </div>

    <div class="pricing-card reveal reveal-delay-2">
      <div class="pricing-name">Bespoke</div>
      <div class="pricing-price">
        <sup class="currency-symbol">₹</sup>
        <span class="price-value" data-inr="3,99,999" data-usd="4,799">3,99,999</span>
      </div>
      <div class="pricing-period">One-time · 30–45 day delivery</div>
      <div class="pricing-divider"></div>
      <ul class="pricing-features">
        <li>Unlimited Pages & Complexity</li>
        <li>Full Custom Web Application</li>
        <li>Razorpay / Stripe Integration</li>
        <li>Custom Admin Dashboard</li>
        <li>AI Features & Automation</li>
        <li>Unlimited Revisions</li>
        <li>6-Month Retainer Included</li>
      </ul>
      <button class="btn-pricing" onclick="document.getElementById('intake').scrollIntoView({behavior:'smooth'})">Begin Bespoke</button>
    </div>

  </div>
</section>

<!-- ─── INTAKE FORM ─── -->
<section id="intake">
  <div class="section-label reveal">Start Your Project</div>
  <h2 class="section-title reveal">Tell Us About <em>Your Vision</em></h2>
  <p class="section-sub reveal">Complete the brief below and we'll respond within 24 hours with a tailored proposal.</p>

  <div class="form-wrapper reveal" id="formWrapper">
    <div class="form-progress">
      <div class="form-step-tab active" id="tab-1"><span class="step-num">01</span>Business</div>
      <div class="form-step-tab" id="tab-2"><span class="step-num">02</span>Style</div>
      <div class="form-step-tab" id="tab-3"><span class="step-num">03</span>Budget</div>
      <div class="form-step-tab" id="tab-4"><span class="step-num">04</span>Goals</div>
    </div>

    <div class="form-body" id="formBody">

      <!-- Step 1 -->
      <div class="form-step active" id="step-1">
        <h3>About Your Business</h3>
        <p class="step-desc">Let's start with the essentials. Who are we building for?</p>
        <div class="form-row">
          <div class="form-group">
            <label>Business Name *</label>
            <input type="text" class="form-control" id="businessName" placeholder="Your company name"/>
          </div>
          <div class="form-group">
            <label>Industry *</label>
            <select class="form-control" id="industry">
              <option value="">Select your industry</option>
              <option>E-Commerce / Retail</option>
              <option>Finance / Investment</option>
              <option>Healthcare / Wellness</option>
              <option>Real Estate</option>
              <option>Technology / SaaS</option>
              <option>Hospitality / Luxury</option>
              <option>Law / Consulting</option>
              <option>Creative / Agency</option>
              <option>Education</option>
              <option>Other</option>
            </select>
          </div>
        </div>
        <div class="form-group">
          <label>Your Name *</label>
          <input type="text" class="form-control" id="clientName" placeholder="Founder / Decision maker"/>
        </div>
        <div class="form-row">
          <div class="form-group">
            <label>Email Address *</label>
            <input type="email" class="form-control" id="clientEmail" placeholder="your@email.com"/>
          </div>
          <div class="form-group">
            <label>Phone Number</label>
            <input type="tel" class="form-control" id="clientPhone" placeholder="+91 XXXXX XXXXX"/>
          </div>
        </div>
        <div class="form-nav">
          <span></span>
          <button class="btn-form btn-form-next" onclick="goStep(2)">Next: Style Selection →</button>
        </div>
      </div>

      <!-- Step 2 -->
      <div class="form-step" id="step-2">
        <h3>Preferred Style</h3>
        <p class="step-desc">Choose the aesthetic direction that best represents your brand vision.</p>
        <div class="form-group">
          <label>Select a Design Style</label>
          <div class="style-select-grid" id="styleGrid">
            <div class="style-option" onclick="selectStyle(this,'The Minimalist')">
              <div class="style-icon">◻</div>
              <div class="style-name">Minimalist</div>
            </div>
            <div class="style-option" onclick="selectStyle(this,'The Power Player')">
              <div class="style-icon">◈</div>
              <div class="style-name">Power Player</div>
            </div>
            <div class="style-option" onclick="selectStyle(this,'The Boutique')">
              <div class="style-icon">◇</div>
              <div class="style-name">Boutique</div>
            </div>
            <div class="style-option" onclick="selectStyle(this,'The Creative')">
              <div class="style-icon">◉</div>
              <div class="style-name">Creative</div>
            </div>
            <div class="style-option" onclick="selectStyle(this,'The Dashboard')">
              <div class="style-icon">▦</div>
              <div class="style-name">Dashboard</div>
            </div>
            <div class="style-option" onclick="selectStyle(this,'The Grand')">
              <div class="style-icon">✦</div>
              <div class="style-name">The Grand</div>
            </div>
          </div>
          <input type="hidden" id="selectedStyle" value=""/>
        </div>
        <div class="form-group">
          <label>Reference Websites (Optional)</label>
          <input type="text" class="form-control" id="references" placeholder="Websites you admire (URLs or names)"/>
        </div>
        <div class="form-nav">
          <button class="btn-form btn-form-back" onclick="goStep(1)">← Back</button>
          <button class="btn-form btn-form-next" onclick="goStep(3)">Next: Budget →</button>
        </div>
      </div>

      <!-- Step 3 -->
      <div class="form-step" id="step-3">
        <h3>Investment Range</h3>
        <p class="step-desc">Select the budget range that aligns with your project scope.</p>
        <div class="form-group">
          <label>Your Budget (INR)</label>
          <div class="budget-range" id="budgetGrid">
            <div class="budget-option" onclick="selectBudget(this,'₹25K – ₹75K')">
              <div class="b-range">₹25K – ₹75K</div>
              <div class="b-desc">Essentials Tier</div>
            </div>
            <div class="budget-option" onclick="selectBudget(this,'₹75K – ₹2L')">
              <div class="b-range">₹75K – ₹2L</div>
              <div class="b-desc">Signature Tier</div>
            </div>
            <div class="budget-option" onclick="selectBudget(this,'₹2L – ₹5L')">
              <div class="b-range">₹2L – ₹5L</div>
              <div class="b-desc">Bespoke Tier</div>
            </div>
            <div class="budget-option" onclick="selectBudget(this,'₹5L+')">
              <div class="b-range">₹5L+</div>
              <div class="b-desc">Enterprise / Custom</div>
            </div>
          </div>
          <input type="hidden" id="selectedBudget" value=""/>
        </div>
        <div class="form-group">
          <label>Preferred Timeline</label>
          <select class="form-control" id="timeline">
            <option value="">Select timeline</option>
            <option>ASAP (Rush — within 7 days)</option>
            <option>2–3 Weeks</option>
            <option>1 Month</option>
            <option>Flexible (Best quality over speed)</option>
          </select>
        </div>
        <div class="form-nav">
          <button class="btn-form btn-form-back" onclick="goStep(2)">← Back</button>
          <button class="btn-form btn-form-next" onclick="goStep(4)">Next: Project Goals →</button>
        </div>
      </div>

      <!-- Step 4 -->
      <div class="form-step" id="step-4">
        <h3>Your Project Vision</h3>
        <p class="step-desc">The more you share, the more precisely we can craft your proposal.</p>
        <div class="form-group">
          <label>Primary Goal *</label>
          <select class="form-control" id="primaryGoal">
            <option value="">What's the #1 goal of your website?</option>
            <option>Generate Leads / Client Inquiries</option>
            <option>Sell Products / E-Commerce Revenue</option>
            <option>Build Brand Authority & Credibility</option>
            <option>Showcase Portfolio / Work</option>
            <option>Book Appointments / Reservations</option>
            <option>Launch a SaaS Product</option>
          </select>
        </div>
        <div class="form-group">
          <label>Describe Your Vision</label>
          <textarea class="form-control" id="vision" placeholder="Tell us about your business, target audience, what sets you apart, and what you envision for your digital presence..."></textarea>
        </div>
        <div class="form-group">
          <label>Anything Else?</label>
          <textarea class="form-control" id="extra" placeholder="Special features, integrations, competitors, concerns..." style="min-height:80px"></textarea>
        </div>
        <div class="form-nav">
          <button class="btn-form btn-form-back" onclick="goStep(3)">← Back</button>
          <button class="btn-form btn-form-submit" onclick="submitForm()">Submit Brief ✦</button>
        </div>
      </div>

    </div>

    <div class="form-success" id="formSuccess">
      <div class="success-icon">✦</div>
      <h3>Brief Received</h3>
      <div class="gold-line"></div>
      <p style="margin-bottom:0.5rem">Thank you, <strong id="successName"></strong>. Your project brief has been submitted.</p>
      <p style="color:var(--slate);font-size:0.82rem;margin-top:0.8rem">Mohit will personally review your brief and respond within <strong>24 hours</strong> with a tailored proposal. Keep an eye on your inbox.</p>
    </div>
  </div>
</section>

<!-- ─── FOOTER ─── -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <a href="#" class="nav-logo">Mikmagic<span>✨</span></a>
      <p>High-end web development and digital strategy for brands that refuse to compromise. Building digital architecture for the modern visionary.</p>
      <div class="gold-line" style="margin:1.5rem 0; background:linear-gradient(90deg,transparent,rgba(212,175,55,0.4),transparent);"></div>
      <p style="font-size:0.75rem;letter-spacing:0.08em;color:rgba(245,240,232,0.3);">FOUNDED BY MOHIT HARSH VARDHAN · INDIA</p>
    </div>
    <div class="footer-col">
      <h4>Navigation</h4>
      <ul>
        <li><a href="#demos">Demo Gallery</a></li>
        <li><a href="#pricing">Pricing Plans</a></li>
        <li><a href="#process">Our Process</a></li>
        <li><a href="#intake">Start a Project</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Get in Touch</h4>
      <div class="footer-contact-item">
        <span class="contact-icon">✉</span>
        <span>hello@mikmagic.studio</span>
      </div>
      <div class="footer-contact-item">
        <span class="contact-icon">◎</span>
        <span>India · Available Worldwide</span>
      </div>
      <div class="footer-contact-item">
        <span class="contact-icon">◷</span>
        <span>Response within 24 hours</span>
      </div>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 Mikmagic✨ · Mohit Harsh Vardhan · All rights reserved</span>
    <span>Crafted with precision in <a href="#">India</a></span>
  </div>
</footer>

<!-- ─── CHATBOT ─── -->
<button id="chatbot-toggle" onclick="toggleChat()" title="Chat with us">
  <span class="chat-icon" id="chatIconLabel">✦</span>
</button>

<div id="chatbot-panel">
  <div class="chat-header">
    <div class="chat-header-info">
      <div class="chat-avatar">✦</div>
      <div>
        <div class="chat-name">Mikmagic Assistant</div>
        <div class="chat-status">● Online · Powered by AI</div>
      </div>
    </div>
    <button class="chat-close" onclick="toggleChat()">✕</button>
  </div>
  <div class="chat-messages" id="chatMessages">
    <div class="chat-bubble bot">Welcome to Mikmagic ✨ I'm here to answer any questions about our services, pricing, or process. How can I help you today?</div>
  </div>
  <div class="quick-replies" id="quickReplies">
    <button class="quick-reply" onclick="sendQuick('What services do you offer?')">Services</button>
    <button class="quick-reply" onclick="sendQuick('What are your prices?')">Pricing</button>
    <button class="quick-reply" onclick="sendQuick('How long does a project take?')">Timeline</button>
    <button class="quick-reply" onclick="sendQuick('How do I start a project?')">Get Started</button>
  </div>
  <div class="chat-input-row">
    <input type="text" class="chat-input" id="chatInput" placeholder="Ask anything..." onkeydown="if(event.key==='Enter')sendMessage()"/>
    <button class="chat-send" onclick="sendMessage()">↑</button>
  </div>
</div>

<!-- ─── SCRIPTS ─── -->
<script>
/* ── PARALLAX ── */
const parallaxBg = document.getElementById('parallaxBg');
window.addEventListener('scroll', () => {
  const y = window.scrollY;
  if(parallaxBg) parallaxBg.style.transform = `translateY(${y * 0.3}px)`;
});

/* ── NAV SCROLL ── */
const nav = document.getElementById('main-nav');
window.addEventListener('scroll', () => {
  nav.classList.toggle('scrolled', window.scrollY > 60);
});

/* ── REVEAL ON SCROLL ── */
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if(e.isIntersecting) {
      e.target.classList.add('in-view');
      observer.unobserve(e.target);
    }
  });
}, { threshold: 0.12, rootMargin: '0px 0px -60px 0px' });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

/* ── COUNTER ANIMATION ── */
function animateCounters() {
  document.querySelectorAll('[data-count]').forEach(el => {
    const target = parseInt(el.dataset.count);
    let current = 0;
    const step = target / 60;
    const timer = setInterval(() => {
      current = Math.min(current + step, target);
      el.textContent = Math.round(current) + (el.dataset.count == '98' ? '%' : (el.dataset.count == '3' ? 'wk' : '+'));
      if(current >= target) clearInterval(timer);
    }, 25);
  });
}
const statsObs = new IntersectionObserver((entries) => {
  if(entries[0].isIntersecting) { animateCounters(); statsObs.disconnect(); }
}, { threshold: 0.3 });
const statsEl = document.getElementById('stats');
if(statsEl) statsObs.observe(statsEl);

/* ── MOBILE NAV ── */
let mobileNavOpen = false;
function toggleMobileNav() {
  mobileNavOpen = !mobileNavOpen;
  document.body.classList.toggle('mobile-nav-open', mobileNavOpen);
}
document.querySelectorAll('.nav-links a').forEach(a => {
  a.addEventListener('click', () => {
    mobileNavOpen = false;
    document.body.classList.remove('mobile-nav-open');
  });
});

/* ── CURRENCY TOGGLE ── */
let isUSD = false;
function toggleCurrency() {
  isUSD = !isUSD;
  const sym = isUSD ? '$' : '₹';
  document.querySelectorAll('.currency-symbol').forEach(el => el.textContent = sym);
  document.querySelectorAll('.price-value').forEach(el => {
    el.textContent = isUSD ? el.dataset.usd : el.dataset.inr;
  });
  document.getElementById('currency-label-inr').style.fontWeight = isUSD ? '300' : '500';
  document.getElementById('currency-label-inr').style.color = isUSD ? 'var(--slate)' : 'var(--charcoal)';
  document.getElementById('currency-label-usd').style.fontWeight = isUSD ? '500' : '300';
  document.getElementById('currency-label-usd').style.color = isUSD ? 'var(--charcoal)' : 'var(--slate)';
}

/* ── DEMO SELECTION ── */
let selectedDemoId = null;
function selectDemo(id, btn) {
  // deselect all
  document.querySelectorAll('.demo-card').forEach(c => c.classList.remove('is-selected'));
  document.querySelectorAll('.btn-select').forEach(b => { b.textContent = 'Select This Style'; b.classList.remove('selected'); });
  // select current
  const card = document.getElementById('demo-' + id);
  if(card) card.classList.add('is-selected');
  btn.textContent = '✦ Selected';
  btn.classList.add('selected');
  selectedDemoId = id;
  // Update form style
  const styleMap = {
    minimalist: 'The Minimalist', powerplayer: 'The Power Player',
    ecommerce: 'The Boutique', creative: 'The Creative',
    saas: 'The Dashboard', hospitality: 'The Grand'
  };
  const input = document.getElementById('selectedStyle');
  if(input) input.value = styleMap[id] || id;
}

/* ── MULTI-STEP FORM ── */
let currentStep = 1;
function goStep(n) {
  document.getElementById('step-' + currentStep).classList.remove('active');
  document.getElementById('tab-' + currentStep).classList.remove('active');
  currentStep = n;
  document.getElementById('step-' + n).classList.add('active');
  document.getElementById('tab-' + n).classList.add('active');
}

function selectStyle(el, name) {
  document.querySelectorAll('.style-option').forEach(o => o.classList.remove('active'));
  el.classList.add('active');
  document.getElementById('selectedStyle').value = name;
}

function selectBudget(el, val) {
  document.querySelectorAll('.budget-option').forEach(o => o.classList.remove('active'));
  el.classList.add('active');
  document.getElementById('selectedBudget').value = val;
}

async function submitForm() {
  const name = document.getElementById('clientName').value.trim();
  const email = document.getElementById('clientEmail').value.trim();
  const business = document.getElementById('businessName').value.trim();
  if(!name || !email || !business) {
    alert('Please fill in your Business Name, Name, and Email in Step 1 before submitting.');
    goStep(1); return;
  }
  // Show success state
  document.getElementById('formBody').style.display = 'none';
  document.querySelector('.form-progress').style.display = 'none';
  document.getElementById('successName').textContent = name;
  document.getElementById('formSuccess').classList.add('show');

  // Optional: send to Formspree
  // const data = { name, email, business, ... };
  // await fetch('https://formspree.io/f/YOUR_ID', { method:'POST', headers:{'Content-Type':'application/json'}, body:JSON.stringify(data) });
}

/* ── AI CHATBOT ── */
let chatOpen = false;
let chatHistory = [];

const SYSTEM_PROMPT = `You are the AI assistant for Mikmagic✨, a high-end web development agency founded by Mohit Harsh Vardhan in India. You help potential clients understand the agency's services, pricing, and process with warmth and professionalism.

Key facts:
- Agency: Mikmagic✨ by Mohit Harsh Vardhan
- Specialty: High-End Web Development & Digital Strategy
- Services: Custom websites, e-commerce, SaaS platforms, corporate sites, portfolios
- Pricing: Essentials (₹49,999 / $599), Signature (₹1,49,999 / $1,799), Bespoke (₹3,99,999 / $4,799)
- Timeline: 7 days (Essentials), 14-21 days (Signature), 30-45 days (Bespoke)
- Tech stack: React/Next.js, Firebase/Supabase, Razorpay/Stripe
- Location: India, serving clients worldwide
- Response time: 24 hours

Be concise, professional, and warm. Keep responses under 3 sentences unless detail is requested. Guide users towards filling the project intake form.`;

function toggleChat() {
  chatOpen = !chatOpen;
  document.getElementById('chatbot-panel').classList.toggle('open', chatOpen);
  document.getElementById('chatIconLabel').textContent = chatOpen ? '✕' : '✦';
}

async function sendMessage() {
  const input = document.getElementById('chatInput');
  const msg = input.value.trim();
  if(!msg) return;
  input.value = '';
  appendBubble(msg, 'user');
  document.getElementById('quickReplies').style.display = 'none';
  chatHistory.push({ role: 'user', content: msg });
  const typing = appendTyping();
  try {
    const res = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        system: SYSTEM_PROMPT,
        messages: chatHistory
      })
    });
    const data = await res.json();
    typing.remove();
    const reply = data.content?.[0]?.text || "I'm sorry, I couldn't process that. Please try again or contact us directly.";
    appendBubble(reply, 'bot');
    chatHistory.push({ role: 'assistant', content: reply });
  } catch(e) {
    typing.remove();
    appendBubble("Sorry, I'm having trouble connecting right now. Please reach out at hello@mikmagic.studio — Mohit will respond within 24 hours.", 'bot');
  }
}

function sendQuick(msg) {
  document.getElementById('chatInput').value = msg;
  sendMessage();
}

function appendBubble(text, type) {
  const msgs = document.getElementById('chatMessages');
  const div = document.createElement('div');
  div.className = 'chat-bubble ' + type;
  div.textContent = text;
  msgs.appendChild(div);
  msgs.scrollTop = msgs.scrollHeight;
  return div;
}

function appendTyping() {
  const msgs = document.getElementById('chatMessages');
  const div = document.createElement('div');
  div.className = 'chat-typing';
  div.innerHTML = '<span></span><span></span><span></span>';
  msgs.appendChild(div);
  msgs.scrollTop = msgs.scrollHeight;
  return div;
}
</script>
</body>
</html>
