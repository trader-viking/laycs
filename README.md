<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ANALYST_v3 — Back + Lay Placar</title>
<style>
/* ══════════════════════════════════════════════════════
   DARK SIGNAL THEME — ANALYST_v3
   ══════════════════════════════════════════════════════ */
:root{
  --bg:      #000;
  --card:    #0f0f0f;
  --card2:   #141414;
  --card3:   #0a0a0a;
  --border:  #282828;
  --border2: #404040;
  --text:    #fff;
  --text2:   #c0c0c0;
  --text3:   #888;
  --green:   #00ff88;
  --yellow:  #fbbf24;
  --red:     #f43f5e;
  --purple:  #a78bfa;
  --orange:  #fb923c;
  --blue:    #38bdf8;
  --cyan:    #22d3ee;
}
*{box-sizing:border-box;margin:0;padding:0}
html,body{
  height:100%;overflow:hidden;
  background:var(--bg);
  color:var(--text);
  font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',system-ui,sans-serif;
  font-size:13px;
}

/* ── SIDEBAR LAYOUT ── */
#body-wrap{display:flex;height:calc(100vh - 50px);overflow:hidden}
#sidebar{
  width:210px;min-width:210px;flex-shrink:0;
  background:var(--card3);
  border-right:1px solid var(--border);
  display:flex;flex-direction:column;
  overflow-y:auto;overflow-x:hidden;
}
#main-area{flex:1;overflow-y:auto;padding:16px 20px;min-width:0}
.sb-logo{
  padding:14px 16px 10px;
  border-bottom:1px solid var(--border);
  margin-bottom:4px;
}
.sb-logo-title{font-size:11px;font-weight:800;letter-spacing:.25em;color:var(--green);font-family:'Courier New',monospace}
.sb-logo-sub{font-size:8px;color:var(--cyan);letter-spacing:.2em;margin-top:2px;font-family:'Courier New',monospace}
.sb-sep{
  font-size:8px;color:var(--text3);letter-spacing:.26em;
  text-transform:uppercase;font-weight:700;
  padding:10px 16px 3px;
}
.sb-item{
  display:flex;align-items:center;justify-content:space-between;
  padding:9px 14px 9px 16px;
  background:none;border:none;border-left:2px solid transparent;
  color:var(--text2);
  font-family:inherit;font-size:11px;font-weight:600;letter-spacing:.04em;
  cursor:pointer;transition:all .12s;width:100%;text-align:left;
}
.sb-item:hover{color:var(--text);background:rgba(255,255,255,.03)}
.sb-item.active{color:var(--green);border-left-color:var(--green);background:rgba(0,255,136,.04)}
.sb-item.active-lay{color:var(--purple);border-left-color:var(--purple);background:rgba(167,139,250,.04)}
.sb-item.active-rej{color:var(--red);border-left-color:var(--red);background:rgba(244,63,94,.04)}
.sb-item.sec-active{color:var(--text);border-left-color:var(--cyan);background:rgba(34,211,238,.04)}
.sb-item .n{
  background:var(--border2);color:var(--text2);border:1px solid var(--border2);
  padding:1px 6px;font-size:9px;font-weight:700;border-radius:3px;min-width:22px;text-align:center;
}
.sb-item.active .n{background:var(--green);color:#000;border-color:var(--green);box-shadow:0 0 6px rgba(0,255,136,.4)}
.sb-item.active-lay .n{background:var(--purple);color:#fff;border-color:var(--purple)}
.sb-item.active-rej .n{background:var(--red);color:#fff;border-color:var(--red)}
.sb-item.sec-active .n{background:var(--cyan);color:#000;border-color:var(--cyan)}
.sb-todos{padding:4px 16px 6px;display:flex;gap:6px;align-items:center}
.sb-todos-btn{
  font-size:9px;font-weight:700;letter-spacing:.14em;text-transform:uppercase;
  background:none;border:1px solid var(--border2);color:var(--text3);
  padding:3px 10px;cursor:pointer;border-radius:3px;transition:all .12s;font-family:inherit;
}
.sb-todos-btn:hover{border-color:var(--text2);color:var(--text2)}
.sb-todos-btn.all-on{border-color:var(--cyan);color:var(--cyan)}
.sb-bottom{margin-top:auto;border-top:1px solid var(--border);padding-top:4px}

/* ── HEADER ── */
#header{
  border-bottom:1px solid var(--border);
  background:#000;
  padding:0 20px;
  height:50px;
  display:flex;align-items:center;justify-content:space-between;
  position:sticky;top:0;z-index:100;
}
.brand{display:flex;align-items:center;gap:12px}
.dot{
  width:7px;height:7px;border-radius:50%;
  background:var(--green);
  box-shadow:0 0 10px var(--green),0 0 20px rgba(0,255,136,.4);
  animation:pulse 2s infinite;
}
@keyframes pulse{0%,100%{opacity:1;box-shadow:0 0 10px var(--green),0 0 20px rgba(0,255,136,.35)}50%{opacity:.5;box-shadow:0 0 4px var(--green)}}
h1{font-size:12px;letter-spacing:.35em;font-weight:800;text-transform:uppercase;color:var(--green);font-family:'Courier New',monospace;text-shadow:0 0 16px rgba(0,255,136,.4)}
.sub{font-size:8px;color:var(--cyan);letter-spacing:.28em;margin-top:2px;font-family:'Courier New',monospace}

/* ── TABS ── */
#tabs{
  display:flex;
  border-bottom:1px solid var(--border);
  background:#000;
  padding:0 16px;
  overflow-x:auto;
  gap:0;
}
.tb{
  padding:14px 16px;
  background:none;border:none;
  border-bottom:3px solid transparent;
  color:var(--text3);
  font-family:inherit;font-size:10px;font-weight:700;letter-spacing:.18em;
  text-transform:uppercase;cursor:pointer;
  transition:all .15s;white-space:nowrap;
}
.tb:hover{color:var(--text)}
.tb.on{color:var(--green);border-bottom-color:var(--green);text-shadow:0 0 14px rgba(0,255,136,.6)}
.tb.lay-active{color:var(--purple);border-bottom-color:var(--purple);text-shadow:0 0 14px rgba(155,138,251,.6)}
.tb.rej-active{color:var(--red);border-bottom-color:var(--red)}
.tb.rej-active .n{background:var(--red);color:#fff;border-color:var(--red)}
.tb .n{
  display:inline-block;
  background:var(--border2);
  color:var(--text2);
  border:1px solid var(--border2);
  padding:1px 6px;font-size:9px;font-weight:700;margin-left:7px;border-radius:3px;
}
.tb.on .n{background:var(--green);color:#000;border-color:var(--green);box-shadow:0 0 8px rgba(0,255,136,.5)}
.tb.lay-active .n{background:var(--purple);color:#fff;border-color:var(--purple)}

/* ── LAYOUT ── */
#wrap{max-width:1440px;margin:0 auto;padding:16px 20px}
.rl-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;align-items:start}
@media(max-width:1100px){.rl-grid{grid-template-columns:repeat(2,1fr)}}
@media(max-width:640px){.rl-grid{grid-template-columns:1fr}}
.pane{display:none}.pane.on{display:block}

/* ── DROP ZONE ── */
#dz{
  border:1px dashed var(--border2);
  background:var(--card);
  padding:48px 40px;text-align:center;
  cursor:pointer;transition:all .2s;margin-bottom:12px;
}
#dz:hover,#dz.hover{
  border-color:var(--green);
  background:rgba(0,255,136,.03);
  box-shadow:inset 0 0 40px rgba(0,255,136,.04);
}
#dz .ico{font-size:28px;opacity:.4;display:block;margin-bottom:12px;color:var(--green)}
#dz .t{color:var(--text);font-size:11px;letter-spacing:.2em;text-transform:uppercase;margin-bottom:4px;font-weight:700}
#dz .s{color:var(--text2);font-size:10px;letter-spacing:.12em}
#fi{display:none}

/* ── ALL BAR ── */
#abar{
  background:var(--card);
  border:1px solid var(--border);
  border-left:3px solid var(--yellow);
  padding:10px 14px;display:none;
  align-items:center;justify-content:space-between;
  margin-bottom:12px;
}
#abar span{font-size:11px;color:var(--text2);letter-spacing:.1em}

/* ── MATCH QUEUE CARDS ── */
.mc{border:1px solid var(--border);background:var(--card);margin-bottom:8px;transition:border-color .15s}
.mc:hover{border-color:var(--border2)}
.mh{padding:10px 14px;display:flex;align-items:flex-start;justify-content:space-between;border-bottom:1px solid var(--border)}
.mt{font-size:13px;color:var(--text);margin-bottom:2px;font-weight:700}
.mt span{color:var(--text3);margin:0 6px}
.mm{font-size:10px;color:var(--text2);letter-spacing:.08em}
.bk{font-size:9px;padding:2px 7px;border:1px solid;letter-spacing:.1em;text-transform:uppercase;font-weight:600}
.bk-p{border-color:var(--yellow);color:var(--yellow)}
.bk-r{border-color:var(--border2);color:var(--text3)}
.bk-d{border-color:var(--green);color:var(--green)}
.bk-e{border-color:var(--red);color:var(--red)}
.mb{padding:12px 14px}
.sl{font-size:9px;color:var(--text3);letter-spacing:.2em;text-transform:uppercase;margin-bottom:8px;display:flex;align-items:center;gap:6px}
.sl::after{content:'';flex:1;height:1px;background:var(--border)}

/* ── STATS GRID ── */
.sg{display:grid;grid-template-columns:1fr 34px 1fr;gap:6px;margin-bottom:12px}
.sc{font-size:9px;text-align:center;color:var(--text3);letter-spacing:.1em;text-transform:uppercase;padding:3px 0;border-bottom:1px solid var(--border);margin-bottom:4px}
.si{display:flex;justify-content:space-between;padding:2px 0;border-bottom:1px solid rgba(255,255,255,.02);font-size:11px}
.sk{color:var(--text3)}.sv{color:var(--text2);font-weight:bold}
.sv.g{color:var(--green)}.sv.r{color:var(--red)}
.vs{display:flex;align-items:center;justify-content:center;color:var(--border2);font-size:10px;padding-top:20px}
.fs{display:flex;gap:3px;flex-wrap:wrap;margin-top:6px}
.fw{background:rgba(0,255,136,.1);color:var(--green);border:1px solid rgba(0,255,136,.3);padding:1px 5px;font-size:10px;font-weight:800}
.fd{background:rgba(245,158,11,.08);color:var(--yellow);border:1px solid rgba(245,158,11,.25);padding:1px 5px;font-size:10px;font-weight:800}
.fl{background:rgba(244,63,94,.07);color:var(--red);border:1px solid rgba(244,63,94,.2);padding:1px 5px;font-size:10px;font-weight:800}
.chip{display:inline-block;background:rgba(0,255,136,.08);border:1px solid rgba(0,255,136,.2);color:var(--green);font-size:9px;padding:1px 6px;letter-spacing:.08em;text-transform:uppercase;margin-left:6px;font-weight:700}
.lbadge{display:inline-block;background:rgba(155,138,251,.08);border:1px solid rgba(155,138,251,.2);color:var(--purple);font-size:9px;padding:1px 6px;letter-spacing:.08em;text-transform:uppercase;margin-left:6px;font-weight:700}

/* ── FORM INPUTS ── */
.og{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;margin-bottom:10px}
.og2{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px}
.cg{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px}
.og label,.og2 label,.cg label{display:block;font-size:9px;color:var(--text2);letter-spacing:.15em;text-transform:uppercase;margin-bottom:4px;font-weight:600}
.og input,.og2 input{
  width:100%;background:var(--card2);
  border:1px solid var(--border);
  color:var(--text);padding:7px 9px;font-family:inherit;font-size:13px;
  transition:border-color .15s;border-radius:3px;
}
.og input:focus,.og2 input:focus{outline:none;border-color:var(--blue);box-shadow:0 0 0 2px rgba(56,189,248,.12)}
.cg select{
  width:100%;background:var(--card2);
  border:1px solid var(--border);
  color:var(--text);padding:7px 9px;font-family:inherit;font-size:12px;cursor:pointer;border-radius:3px;
}
.cg select:focus{outline:none}

/* ── BUTTONS ── */
.ban{
  width:100%;padding:11px;
  background:var(--green);color:#000;
  font-family:inherit;font-size:11px;font-weight:800;
  letter-spacing:.3em;text-transform:uppercase;
  border:none;cursor:pointer;transition:all .15s;
  box-shadow:0 0 20px rgba(0,255,136,.3);border-radius:3px;
}
.ban:hover{background:#1affa0;box-shadow:0 0 30px rgba(0,255,136,.5)}
.bsec{
  padding:8px 14px;
  border:1px solid var(--border2);
  background:none;color:var(--text2);
  font-family:inherit;font-size:10px;font-weight:600;letter-spacing:.2em;
  text-transform:uppercase;cursor:pointer;transition:all .15s;border-radius:3px;
}
.bsec:hover{border-color:var(--text);color:var(--text)}
.brm{background:none;border:none;color:var(--text3);cursor:pointer;font-size:14px;padding:0 4px;transition:color .15s}
.brm:hover{color:var(--red)}

/* ── RESULTS (legacy) ── */
.rc{border:1px solid var(--border);background:var(--card);margin-bottom:8px}
.rh{padding:12px 14px;border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:flex-start}
.rm{font-size:13px;margin-bottom:3px;font-weight:bold}
.rcomp{font-size:10px;color:var(--text2);letter-spacing:.08em}
.vd{font-size:14px;font-weight:bold;letter-spacing:.1em;text-align:right}
.rk{font-size:10px;color:var(--text3);text-align:right;margin-top:3px;letter-spacing:.1em}
.cb{display:flex;justify-content:space-between;font-size:10px;color:var(--text3);letter-spacing:.1em;margin-bottom:3px}
.cf{height:2px;background:var(--border);margin-bottom:10px}
.ci{height:100%}
.pb{display:grid;grid-template-columns:1fr 1fr 1fr;gap:6px;margin-bottom:10px}
.px{border:1px solid var(--border);background:var(--card3);padding:10px;text-align:center}
.pl{font-size:9px;color:var(--text3);letter-spacing:.1em;text-transform:uppercase;margin-bottom:3px}
.pv{font-size:20px;font-weight:bold}
.rec{border-left:2px solid var(--border2);padding:8px 12px;margin-bottom:10px;font-size:11px;color:var(--text2);line-height:1.6}
.wl{border:1px solid rgba(251,146,60,.25);background:rgba(251,146,60,.04);padding:10px 12px;margin-top:8px}
.wt{font-size:9px;color:var(--orange);letter-spacing:.15em;text-transform:uppercase;margin-bottom:5px}
.wi{font-size:11px;color:rgba(251,146,60,.65);display:flex;gap:5px;padding:1px 0}

/* ── EMPTY + DISC ── */
.emp{text-align:center;padding:50px 20px;color:var(--text3)}
.emp .ei{font-size:22px;opacity:.2;display:block;margin-bottom:10px}
.emp p{font-size:9px;letter-spacing:.2em;text-transform:uppercase;font-weight:600}
.disc{text-align:center;font-size:9px;color:var(--text3);margin-top:14px;letter-spacing:.1em}

/* ── SUB-TABS (LAY CS) ── */
.sub-tabs{
  display:flex;
  border-bottom:1px solid var(--border);
  background:#000;
  margin-bottom:14px;
  overflow-x:auto;
}
.stb{
  padding:10px 16px;background:none;border:none;
  border-bottom:2px solid transparent;
  color:var(--text3);font-family:inherit;
  font-size:9px;font-weight:600;letter-spacing:.2em;text-transform:uppercase;
  cursor:pointer;transition:all .15s;white-space:nowrap;
}
.stb:hover{color:var(--purple)}
.stb.on{color:var(--purple);border-bottom-color:var(--purple);text-shadow:0 0 12px rgba(155,138,251,.5)}
.spane{display:none}.spane.on{display:block}

/* ══════════════════════════════════════════
   ENTRY CARDS — DARK SIGNAL STYLE
   ══════════════════════════════════════════ */
.ec{
  margin-bottom:10px;
  border:1px solid var(--border);
  background:var(--card);
  overflow:hidden;
  transition:border-color .15s, box-shadow .15s;
  font-family:inherit;
  border-radius:4px;
}
.ec:hover{
  border-color:var(--border2);
  box-shadow:0 4px 24px rgba(0,0,0,.7);
}

/* ── top meta row ── */
.ec-top{
  padding:10px 14px 0;
  display:flex;align-items:center;justify-content:space-between;
}
.ec-top-left{
  display:flex;align-items:center;gap:8px;
  font-size:10px;color:var(--text2);font-weight:500;
}
.ec-top-time{display:flex;align-items:center;gap:3px}
.ec-top-comp{display:flex;align-items:center;gap:4px}

/* ── match title ── */
.ec-title{
  padding:8px 14px 4px;
  font-size:16px;font-weight:800;
  color:var(--text);letter-spacing:-.01em;
  line-height:1.25;
}
.ec-title .ec-vs{color:var(--text3);margin:0 5px;font-weight:400;font-size:14px}

/* ── position/stats row ── */
.ec-pos-row{
  padding:0 14px 10px;
  display:flex;align-items:center;gap:6px;
  font-size:11px;color:var(--text2);flex-wrap:wrap;
}
.ec-pos-sep{color:var(--text3);font-size:10px;margin:0 3px}
.ec-pos-dash{
  display:inline-block;width:18px;height:2px;
  background:var(--border2);margin-left:4px;vertical-align:middle;
}

/* ══ SIGNAL BANNER — full width colored strip ══ */
.ec-signal-banner{
  display:flex;align-items:center;justify-content:space-between;
  padding:11px 16px;
  position:relative;overflow:hidden;
}
.ec-signal-banner::before{
  content:'';position:absolute;inset:0;
  background:inherit;opacity:.9;
  pointer-events:none;
}
.ec-signal-name{
  font-size:12px;font-weight:800;letter-spacing:.18em;text-transform:uppercase;
  position:relative;z-index:1;display:flex;align-items:center;gap:8px;
}
.ec-signal-arrow{font-size:16px;line-height:1}
.ec-signal-conf{
  font-size:10px;font-weight:700;letter-spacing:.12em;
  position:relative;z-index:1;opacity:.85;
}

/* banner color variants */
.ec-signal-banner.sig-back-ok{
  background:linear-gradient(90deg,rgba(0,255,136,.18) 0%,rgba(0,255,136,.04) 100%);
  border-top:1px solid rgba(0,255,136,.35);
  border-bottom:1px solid rgba(0,255,136,.15);
  color:var(--green);
}
.ec-signal-banner.sig-back-ok::before{background:transparent}
.ec-signal-banner.sig-back-pos{
  background:linear-gradient(90deg,rgba(245,158,11,.14) 0%,rgba(245,158,11,.03) 100%);
  border-top:1px solid rgba(245,158,11,.3);
  border-bottom:1px solid rgba(245,158,11,.12);
  color:var(--yellow);
}
.ec-signal-banner.sig-back-pos::before{background:transparent}
.ec-signal-banner.sig-lay-ok{
  background:linear-gradient(90deg,rgba(155,138,251,.18) 0%,rgba(155,138,251,.04) 100%);
  border-top:1px solid rgba(155,138,251,.35);
  border-bottom:1px solid rgba(155,138,251,.15);
  color:var(--purple);
}
.ec-signal-banner.sig-lay-ok::before{background:transparent}
.ec-signal-banner.sig-lay-pos{
  background:linear-gradient(90deg,rgba(155,138,251,.12) 0%,rgba(155,138,251,.03) 100%);
  border-top:1px solid rgba(155,138,251,.25);
  border-bottom:1px solid rgba(155,138,251,.08);
  color:#c4b5fd;
}
.ec-signal-banner.sig-lay-pos::before{background:transparent}
.ec-signal-banner.sig-warn{
  background:linear-gradient(90deg,rgba(251,146,60,.12) 0%,rgba(251,146,60,.02) 100%);
  border-top:1px solid rgba(251,146,60,.25);
  border-bottom:1px solid rgba(251,146,60,.1);
  color:var(--orange);
}
.ec-signal-banner.sig-warn::before{background:transparent}
.ec-signal-banner.sig-bad{
  background:linear-gradient(90deg,rgba(244,63,94,.1) 0%,rgba(244,63,94,.02) 100%);
  border-top:1px solid rgba(244,63,94,.22);
  border-bottom:1px solid rgba(244,63,94,.08);
  color:var(--red);
}
.ec-signal-banner.sig-bad::before{background:transparent}

/* ── old signal classes — kept for compatibility ── */
.ec-signal-row{padding:0 14px 12px;display:flex;align-items:center;gap:8px}
.ec-signal{display:inline-flex;align-items:center;gap:5px;padding:5px 11px;border-radius:3px;font-size:11px;font-weight:700;letter-spacing:.03em;white-space:nowrap}
.ec-signal.back{background:rgba(0,255,136,.1);color:var(--green);border:1px solid rgba(0,255,136,.25)}
.ec-signal.lay{background:rgba(155,138,251,.1);color:var(--purple);border:1px solid rgba(155,138,251,.25)}
.ec-signal.warn{background:rgba(245,158,11,.1);color:var(--yellow);border:1px solid rgba(245,158,11,.22)}

/* ── divider ── */
.ec-div{height:1px;background:var(--border);margin:0}

/* ── market section ── */
.ec-mkt-row{
  padding:10px 14px 8px;
  display:flex;align-items:flex-start;justify-content:space-between;gap:12px;
}
.ec-mkt-left{}
.ec-mkt-lbl{
  font-size:8px;color:var(--cyan);letter-spacing:.22em;
  text-transform:uppercase;margin-bottom:4px;font-weight:700;
}
.ec-mkt-name{
  font-size:13px;font-weight:800;color:var(--text);
  letter-spacing:.01em;
}
.ec-mkt-sub{font-size:10px;color:var(--yellow);margin-top:2px;font-weight:600}
.ec-odd-box{text-align:right;flex-shrink:0}
.ec-odd-lbl{
  font-size:8px;color:var(--cyan);letter-spacing:.18em;
  text-transform:uppercase;margin-bottom:4px;font-weight:700;
}
.ec-odd-val{
  font-size:17px;font-weight:800;
  font-variant-numeric:tabular-nums;
  font-family:'Courier New',monospace;
}

/* ── metrics bar ── */
.ec-metrics{
  display:grid;grid-template-columns:1fr 1fr 1fr;
  gap:1px;background:var(--border);
  border-top:1px solid var(--border);
}
.ec-metric{
  background:var(--card3);padding:12px 10px;text-align:center;
}
.ec-metric-lbl{
  font-size:8px;letter-spacing:.22em;
  text-transform:uppercase;margin-bottom:6px;font-weight:700;
}
.ec-metric:nth-child(1) .ec-metric-lbl{color:var(--orange)}
.ec-metric:nth-child(2) .ec-metric-lbl{color:var(--green)}
.ec-metric:nth-child(3) .ec-metric-lbl{color:var(--blue)}
.ec-metric-val{
  font-size:22px;font-weight:800;
  font-variant-numeric:tabular-nums;
  font-family:'Courier New',monospace;
  letter-spacing:.02em;line-height:1;
}
.ec-metric-val.sm{font-size:16px}

/* ── warns bar ── */
.ec-warns-bar{
  padding:10px 14px;
  background:rgba(251,146,60,.05);
  border-top:1px solid rgba(251,146,60,.2);
  border-bottom:1px solid rgba(251,146,60,.1);
  display:flex;flex-direction:column;gap:5px;
}
.ec-warn-item{
  font-size:11px;color:var(--orange);
  display:flex;align-items:flex-start;gap:8px;line-height:1.4;
}
.ec-warn-ico{flex-shrink:0;font-size:12px;margin-top:1px}

/* ── ver detalhes toggle ── */
.ec-toggle{
  width:100%;padding:11px 14px;
  background:var(--card2);border:none;
  border-top:1px solid var(--border);
  color:var(--cyan);font-family:inherit;font-weight:700;
  font-size:10px;letter-spacing:.14em;text-transform:uppercase;
  cursor:pointer;display:flex;align-items:center;justify-content:center;gap:8px;
  transition:background .15s, color .15s;
}
.ec-toggle:hover{background:var(--card3);color:var(--text)}
.ec-toggle.open{color:var(--text)}
.ec-toggle .ec-arr{transition:transform .2s;display:inline-block;font-size:11px}
.ec-toggle.open .ec-arr{transform:rotate(180deg)}
.ec-details{display:none}
.ec-details.open{display:block}

/* ── details internals ── */
.ec-sec{
  padding:12px 14px;
  border-bottom:1px solid var(--border);
  font-family:'Courier New',Courier,monospace;
}
.ec-sec:last-child{border-bottom:none}
.ec-lbl{
  font-size:8px;color:var(--cyan);letter-spacing:.24em;
  text-transform:uppercase;margin-bottom:8px;font-weight:700;
  display:flex;align-items:center;gap:6px;
}
.ec-lbl::after{content:'';flex:1;height:1px;background:var(--border)}
.ec-market{font-size:13px;color:var(--text);font-weight:800}
.ec-subt{font-size:10px;color:var(--yellow);margin-top:3px;font-weight:600}
.ec-motives{display:flex;flex-direction:column;gap:3px}
.ec-m{display:flex;align-items:flex-start;gap:8px;font-size:11px;padding:3px 0;border-bottom:1px solid rgba(255,255,255,.025)}
.ec-m:last-child{border-bottom:none}
.ec-m-ico{flex-shrink:0;font-size:11px;width:14px;margin-top:1px}
.ec-m-text{flex:1;line-height:1.4}
.ec-m-key{color:var(--text)}.ec-m-val{color:var(--text2);margin-left:4px;font-size:10px}
.ec-timing{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--border)}
.ec-t{padding:10px 14px;background:var(--card)}
.ec-tlbl{font-size:8px;color:var(--yellow);letter-spacing:.22em;text-transform:uppercase;margin-bottom:4px;font-weight:700}
.ec-tval{font-size:12px;color:var(--text);line-height:1.5;font-weight:600}
.ec-tval span{display:block;color:var(--text2);font-size:10px;margin-top:2px}
.ec-prob{display:grid;grid-template-columns:1fr 1fr 1fr;gap:1px;background:var(--border)}
.ec-p{background:var(--card3);padding:10px 12px;text-align:center}
.ec-plbl{font-size:8px;color:var(--purple);letter-spacing:.14em;text-transform:uppercase;margin-bottom:4px;font-weight:700}
.ec-pval{font-size:20px;font-weight:800;font-variant-numeric:tabular-nums;font-family:'Courier New',monospace}
.ec-fail-items{display:flex;flex-direction:column;gap:3px}
.ec-fi{font-size:11px;color:var(--red);display:flex;gap:8px;align-items:flex-start;padding:3px 0}
.ec-fi-v{color:var(--text2);font-size:10px;margin-left:4px}
.ec-pill{
  font-size:8px;letter-spacing:.16em;text-transform:uppercase;
  padding:3px 8px;border:1px solid currentColor;opacity:.8;font-weight:700;
}

/* ── checklist ── */
.cl{border:none;background:none}
.ch{
  padding:6px 14px;border-bottom:1px solid var(--border);
  display:flex;justify-content:space-between;
  font-size:9px;color:var(--cyan);letter-spacing:.15em;text-transform:uppercase;font-weight:700;
  background:var(--card3);
}
.cr{display:flex;gap:8px;padding:7px 14px;border-bottom:1px solid rgba(255,255,255,.025)}
.cr:last-child{border-bottom:none}
.ci2{font-size:11px;margin-top:1px;flex-shrink:0;width:12px}
.cb2{flex:1}
.cl2{font-size:11px;color:var(--text2);margin-bottom:1px}.cl2.ok{color:var(--text)}
.cd{font-size:10px;color:var(--text2)}
.cw{font-size:9px;color:var(--text3);flex-shrink:0}

/* ── rejected list ── */
.rej-list{display:flex;flex-direction:column;gap:2px;margin-bottom:12px}
.rej-row{
  display:flex;align-items:center;gap:12px;
  background:var(--card);border:1px solid var(--border);
  padding:10px 14px;
  transition:border-color .15s;
}
.rej-row:hover{border-color:var(--border2)}
.rej-time{
  font-family:'Courier New',monospace;font-size:11px;font-weight:800;
  color:var(--green);white-space:nowrap;min-width:46px;
}
.rej-match{
  font-size:13px;font-weight:800;color:var(--text);flex:1;min-width:0;
  white-space:nowrap;overflow:hidden;text-overflow:ellipsis;
}
.rej-match span{color:var(--text3);font-weight:400;margin:0 5px;font-size:12px}
.rej-comp{
  font-size:9px;color:var(--blue);font-weight:600;letter-spacing:.08em;
  white-space:nowrap;max-width:140px;overflow:hidden;text-overflow:ellipsis;
}
.rej-tags{display:flex;gap:5px;flex-wrap:wrap;justify-content:flex-end;min-width:0}
.rej-tag{
  font-size:8px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;
  padding:3px 8px;border:1px solid currentColor;white-space:nowrap;
  opacity:.85;
}

/* ── download button ── */
.ec-dl-btn{
  margin-left:auto;
  background:none;border:1px solid var(--border2);
  color:var(--text2);cursor:pointer;
  font-size:11px;padding:4px 9px;
  display:flex;align-items:center;gap:5px;
  transition:all .15s;border-radius:3px;
  font-family:inherit;font-weight:600;letter-spacing:.06em;
  flex-shrink:0;
}
.ec-dl-btn:hover{
  border-color:var(--green);color:var(--green);
  box-shadow:0 0 8px rgba(0,255,136,.2);
}
.ec-dl-btn.loading{opacity:.5;pointer-events:none}
</style>
</head>
<body>
<div id="header">
  <div class="brand">
    <div class="dot"></div>
    <div>
      <h1>ANALYST_v3</h1>
      <div class="sub">BACK · OVER · LAY CS</div>
    </div>
  </div>
  <div style="display:flex;align-items:center;gap:16px">
    <div style="font-size:9px;color:var(--text3);letter-spacing:.1em;text-align:right">
      <div style="color:var(--green);font-size:11px;font-family:'Courier New',monospace;font-weight:700" id="hclock">—</div>
      <div style="margin-top:2px;letter-spacing:.2em;font-weight:600">FOOTBALL TRADER</div>
    </div>
    <div style="width:1px;height:24px;background:var(--border)"></div>
    <div style="font-size:9px;color:var(--text2);letter-spacing:.08em;text-align:right;font-weight:500" id="hdate">—</div>
  </div>
</div>

<div id="body-wrap">
  <!-- ── SIDEBAR ── -->
  <aside id="sidebar">
    <div class="sb-logo">
      <div class="sb-logo-title">ANALYST_v3</div>
      <div class="sb-logo-sub">BACK · OVER · LAY CS</div>
    </div>

    <button class="sb-item sec-active sb-section-btn" data-section="fila" onclick="showSection('fila')">
      <span>📋 Fila de Jogos</span><span class="n" id="bn-fila">0</span>
    </button>

    <div class="sb-sep">BACK</div>
    <div class="sb-todos">
      <button id="sb-todos-btn" class="sb-todos-btn all-on" onclick="clearFilters()">Todos</button>
    </div>
    <button class="sb-item sb-filter" data-method="backfav" onclick="filterMethod('backfav')">
      <span>Back Favorito</span><span class="n" id="bn-backfav">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="back2x2" onclick="filterMethod('back2x2')">
      <span>Back 2×2</span><span class="n" id="bn-back2x2">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="backgoleada" onclick="filterMethod('backgoleada')">
      <span>Back Goleada</span><span class="n" id="bn-backgoleada">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="over70" onclick="filterMethod('over70')">
      <span>Over 70min</span><span class="n" id="bn-over70">0</span>
    </button>

    <div class="sb-sep">LAY CS</div>
    <button class="sb-item sb-filter" data-method="lay1x0" onclick="filterMethod('lay1x0')">
      <span>Lay 1×0</span><span class="n" id="bn-lay1x0">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="lay0x1" onclick="filterMethod('lay0x1')">
      <span>Lay 0×1</span><span class="n" id="bn-lay0x1">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="lay2x0" onclick="filterMethod('lay2x0')">
      <span>Lay 2×0</span><span class="n" id="bn-lay2x0">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="lay0x2" onclick="filterMethod('lay0x2')">
      <span>Lay 0×2</span><span class="n" id="bn-lay0x2">0</span>
    </button>
    <button class="sb-item sb-filter" data-method="layzebra" onclick="filterMethod('layzebra')">
      <span>Lay Zebra</span><span class="n" id="bn-layzebra">0</span>
    </button>

    <div class="sb-bottom">
      <button class="sb-item sb-section-btn" data-section="rejeitados" onclick="showSection('rejeitados')">
        <span>⚠ Rejeitados</span><span class="n" id="bn-rejeitados">0</span>
      </button>
    </div>
  </aside>

  <!-- ── MAIN AREA ── -->
  <main id="main-area">
    <div id="pane-fila" class="pane on">
      <div id="dz" onclick="document.getElementById('fi').click()"
           ondragover="ev(event,'hover',1)" ondragleave="ev(event,'hover',0)" ondrop="drop(event)">
        <span class="ico">⊕</span>
        <div class="t">Arraste PDFs aqui ou clique para selecionar</div>
        <div class="s">Múltiplos arquivos · Formato: Partidas Favoritos</div>
      </div>
      <input type="file" id="fi" accept=".pdf" multiple onchange="onFiles(this.files)">
      <div id="abar">
        <span id="abar-txt"></span>
        <button class="ban" style="width:auto;padding:8px 18px" onclick="allAnalyze()">ANALISAR TODOS →</button>
      </div>
      <div id="ml"></div>
    </div>
    <div id="pane-resultados" class="pane">
      <div id="rl-all" class="rl-grid"></div>
      <p class="disc">Ferramenta de análise quantitativa. Não constitui aconselhamento financeiro.</p>
    </div>
    <div id="pane-rejeitados" class="pane">
      <div id="rl-rejeitados"></div>
      <p class="disc">Análises não recomendadas ou alto risco. Não constitui aconselhamento financeiro.</p>
    </div>
  </main>
</div>

<script>
// ── STATE ────────────────────────────────────────────────────────────────────
// ── LIVE CLOCK ────────────────────────────────────────────────────────────────
(function updateClock(){
  const now = new Date();
  const d = document.getElementById('hdate');
  const c = document.getElementById('hclock');
  if(d) d.textContent = now.toLocaleDateString('pt-BR',{weekday:'short',day:'2-digit',month:'short',year:'numeric'}).toUpperCase();
  if(c) c.textContent = now.toLocaleTimeString('pt-BR',{hour:'2-digit',minute:'2-digit',second:'2-digit'});
  setTimeout(updateClock, 1000);
})();
const S = { matches: [], results: [], id: 1, activeFilters: new Set() };

// ── NAVIGATION & FILTER ──────────────────────────────────────────────────────
const SECTIONS = ['fila','resultados','rejeitados'];

function showSection(name) {
  SECTIONS.forEach(s => {
    const p = document.getElementById('pane-'+s);
    if (p) p.classList.toggle('on', s===name);
  });
  document.querySelectorAll('.sb-section-btn').forEach(btn => {
    btn.classList.toggle('sec-active', btn.getAttribute('data-section')===name);
  });
  // If going to results, clear filter highlights (keep active filters intact)
  if (name === 'resultados') applyFilter();
}

function filterMethod(k) {
  showSection('resultados');
  const f = S.activeFilters;
  if (f.has(k)) f.delete(k); else f.add(k);
  // Update sidebar button styles
  const isLay = ['lay1x0','lay0x1','lay2x0','lay0x2','layzebra'].includes(k);
  document.querySelectorAll('.sb-filter').forEach(btn => {
    const m = btn.getAttribute('data-method');
    btn.classList.remove('active','active-lay');
    if (f.has(m)) btn.classList.add(['lay1x0','lay0x1','lay2x0','lay0x2','layzebra'].includes(m)?'active-lay':'active');
  });
  const todosBtn = document.getElementById('sb-todos-btn');
  if (todosBtn) todosBtn.classList.toggle('all-on', f.size===0);
  applyFilter();
}

function clearFilters() {
  S.activeFilters.clear();
  document.querySelectorAll('.sb-filter').forEach(btn => btn.classList.remove('active','active-lay'));
  const todosBtn = document.getElementById('sb-todos-btn');
  if (todosBtn) todosBtn.classList.add('all-on');
  showSection('resultados');
  applyFilter();
}

function applyFilter() {
  const allEl = document.getElementById('rl-all');
  if (!allEl) return;
  const f = S.activeFilters;
  allEl.querySelectorAll('[data-method]').forEach(el => {
    el.style.display = (!f.size || f.has(el.getAttribute('data-method'))) ? '' : 'none';
  });
}

// ── DROP ─────────────────────────────────────────────────────────────────────
function ev(e,cls,add){ e.preventDefault(); document.getElementById('dz').classList.toggle(cls,!!add); }
function drop(e){ e.preventDefault(); document.getElementById('dz').classList.remove('hover'); onFiles(e.dataTransfer.files); }
function onFiles(files){ for(const f of files) if(f.type==='application/pdf') addMatch(f); }

// ── ADD MATCH ─────────────────────────────────────────────────────────────────
function addMatch(file) {
  const id = S.id++;
  const m = { id, file, status:'parsing', data:null, analysis:null,
    opts:{ oddBack2x2:'', oddLay1x0:'', oddLay0x1:'' } };
  S.matches.push(m);
  refreshBadges(); renderList();
  extractPDF(file)
    .then(data => {
      m.data = data;
      // Auto-analyze immediately with default opts (sem odds)
      const opts = { oddBack2x2:0, oddLay1x0:0, oddLay0x1:0, oddLay2x0:0, oddLay0x2:0, oddBackFav:0, oddOver70:0, oddBackGoleada:0 };
      m.analysis = {
        backfav:     analyzeBackFavorito(data, opts),
        back2x2:     analyzeBack2x2(data, opts),
        backgoleada: analyzeBackGoleada(data, opts),
        over70:      analyzeOver70(data, opts),
        lay1x0:      analyzeLay1x0(data, opts),
        lay0x1:      analyzeLay0x1(data, opts),
        lay2x0:      analyzeLay2x0(data, opts),
        lay0x2:      analyzeLay0x2(data, opts),
        layzebra:    analyzeLayZebra(data, opts),
      };
      m.status = 'done';
      const ei  = S.results.findIndex(r=>r.mid===m.id);
      const rec = { mid:m.id, d:data, ...m.analysis };
      if (ei>=0) S.results[ei]=rec; else S.results.unshift(rec);
      renderList(); renderResults(); refreshBadges(); refreshABar();
      showSection('resultados');
    })
    .catch(err => { m.status='error'; m.errMsg=err.message||'Erro ao processar PDF'; renderList(); });
}

// ── PDF EXTRACTION ────────────────────────────────────────────────────────────
async function extractPDF(file) {
  if (!window._pdfjs) {
    window._pdfjs = await new Promise((res, rej) => {
      const s = document.createElement('script');
      s.src = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js';
      s.onload = () => {
        pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';
        res(pdfjsLib);
      };
      s.onerror = () => rej(new Error('PDF.js não carregou. Verifique conexão com internet.'));
      document.head.appendChild(s);
    });
  }
  const lib = window._pdfjs;
  const data = new Uint8Array(await file.arrayBuffer());
  const pdf = await lib.getDocument({ data }).promise;

  let items = [], pageW = 600;
  for (let p = 1; p <= pdf.numPages; p++) {
    const page = await pdf.getPage(p);
    const vp = page.getViewport({ scale: 1 });
    if (p === 1) pageW = vp.width;
    const tc = await page.getTextContent();
    for (const it of tc.items) {
      const t = (it.str||'').trim();
      if (t) items.push({ t, x: it.transform[4], y: it.transform[5] + (p-1)*99999 });
    }
  }
  return parseItems(items, pageW);
}

// ── PARSE ITEMS ───────────────────────────────────────────────────────────────
function parseItems(items, pageW) {
  const mid = pageW / 2;
  const rowMap = {};
  for (const it of items) {
    const ry = Math.round(it.y / 8) * 8;
    if (!rowMap[ry]) rowMap[ry] = [];
    rowMap[ry].push(it);
  }
  const leftL = [], rightL = [], fullL = [];
  for (const ry of Object.keys(rowMap).map(Number).sort((a,b)=>b-a)) {
    const row = rowMap[ry].sort((a,b)=>a.x-b.x);
    const left  = row.filter(i=>i.x<mid).map(i=>i.t).join(' ').trim();
    const right = row.filter(i=>i.x>=mid).map(i=>i.t).join(' ').trim();
    const full  = row.map(i=>i.t).join(' ').trim();
    if (left)  leftL.push(left);
    if (right) rightL.push(right);
    if (full)  fullL.push(full);
  }
  return buildMatch(leftL, rightL, fullL);
}

// ── BUILD MATCH ───────────────────────────────────────────────────────────────
function buildMatch(LL, RL, FL) {
  const M = {
    homeTeam:'', awayTeam:'', competition:'', date:'', round:'',
    homeForm:'', awayForm:'',
    home: mkS(), away: mkS()
  };

  const formRx = /^[WwDdLlVv](\s*[WwDdLlVv])+$/;
  const isName = l => l.length>2 && l.length<60 && !/^\d/.test(l) && !/%/.test(l) &&
    !/Aproveitamento|Gols|Finalizações|Escanteios|Cartões|Partidas|Menu|Rodada|Tempo|Média|Falhou|Ambas|Primeiro|Jogos|Pontos|Total|Vitórias|Posição|xG|Finalizac|Desempenho|Brazil|Serie|JOSE|Felipe|Geral|Copa|Liga/i.test(l);

  for (let i=0; i<LL.length; i++) {
    if (formRx.test(LL[i].trim())) {
      M.homeForm = LL[i].replace(/\s+/g,'').toUpperCase();
      for (let j=i-1; j>=Math.max(0,i-3); j--) {
        if (isName(LL[j])) { M.homeTeam = LL[j].trim(); break; }
      }
      break;
    }
  }
  for (let i=0; i<RL.length; i++) {
    if (formRx.test(RL[i].trim())) {
      M.awayForm = RL[i].replace(/\s+/g,'').toUpperCase();
      for (let j=i-1; j>=Math.max(0,i-3); j--) {
        if (isName(RL[j]) && RL[j].trim()!==M.homeTeam) { M.awayTeam = RL[j].trim(); break; }
      }
      break;
    }
  }

  const compSrc = RL.find(l=>/Rodada/i.test(l)) || FL.find(l=>/Rodada/i.test(l)) || '';
  if (compSrc) {
    const cm = compSrc.match(/(.+?)\s+Rodada\s*[-–]?\s*(\d+)/i);
    if (cm) { M.competition = cm[1].replace(/\d{2}\/\d{2}\/\d{4}/,'').replace(/\d{2}:\d{2}/,'').trim(); M.round = cm[2]; }
  }
  const dateLine = FL.find(l=>/\d{2}\/\d{2}\/\d{4}/.test(l)) || '';
  const dm = dateLine.match(/(\d{2}\/\d{2}\/\d{4})/);
  if (dm) M.date = dm[1];
  const tm = dateLine.match(/(\d{2}:\d{2})/);
  if (tm) M.time = tm[1];

  parseStats(LL, M.home, 'home');
  parseStats(RL, M.away, 'away');
  return M;
}

function mkS() {
  return { ppg:0,winPct:0,games:0,wins:0,avgScored:0,avgConceded:0,avgTotal:0,
           xgFor:0,xgAgainst:0,position:0,shotsAvg:0,firstToScore:0,
           cleanSheets:0,failedToScore:0,bothScore:0,over05:0,over15:0,over25:0 };
}

function parseStats(lines, S, type) {
  const startKey = type==='home' ? 'Aproveitamento em Casa' : 'Aproveitamento Fora de Casa';
  const startIdx = lines.findIndex(l=>l.includes(startKey));
  const src = startIdx>=0 ? lines.slice(startIdx+1) : lines;

  function getNum(key) {
    for (let i=0; i<src.length; i++) {
      if (i>32) break;
      if (src[i].toLowerCase().includes(key.toLowerCase())) {
        const m = src[i].match(/(\d+[,.]?\d*)\s*%?\s*$/);
        if (m) return parseFloat(m[1].replace(',','.'));
        if (i+1<src.length) {
          const m2 = src[i+1].match(/^(\d+[,.]?\d*)/);
          if (m2) return parseFloat(m2[1].replace(',','.'));
        }
      }
    }
    return 0;
  }

  function getPct(key) {
    for (let i=0; i<src.length; i++) {
      if (i>32) break;
      if (src[i].toLowerCase().includes(key.toLowerCase())) {
        const m = src[i].match(/(\d+)\s*%/);
        if (m) return parseInt(m[1])/100;
        if (i+1<src.length) {
          const m2 = src[i+1].match(/^(\d+)\s*%/);
          if (m2) return parseInt(m2[1])/100;
        }
      }
    }
    return 0;
  }

  S.ppg          = getNum('Pontos por Jogo');
  S.winPct       = getPct('% de Vitórias');
  S.games        = getNum('Total de Jogos');
  S.wins         = getNum('Vitórias');
  S.avgScored    = getNum('Média de gols marcados');
  S.avgConceded  = getNum('Média de gols sofridos');
  S.avgTotal     = getNum('Média total de gols');
  S.xgFor        = getNum('xG médio a favor');
  S.xgAgainst    = getNum('xG médio contra');
  S.shotsAvg     = getNum('Média de Finalizações');
  S.firstToScore = getPct('Primeiro a marcar');
  S.cleanSheets  = getPct('Jogos sem sofrer');
  S.failedToScore= getPct('Falhou em marcar');
  S.bothScore    = getPct('Ambas marcam');
  S.position     = getNum(type==='home'?'Posição como Mandante':'Posição como Visitante');

  // Over stats from "Total de Gols em Casa/Fora" section (appears ~50 lines down)
  const overKey = type==='home' ? 'Total de Gols em Casa' : 'Total de Gols Fora de Casa';
  const overIdx = lines.findIndex(l=>l.includes(overKey));
  if (overIdx >= 0) {
    const overSrc = lines.slice(overIdx, overIdx + 8);
    function getO(key) {
      for (const l of overSrc) {
        if (l.toLowerCase().includes(key.toLowerCase())) {
          const m = l.match(/(\d+)\s*%/);
          if (m) return parseInt(m[1])/100;
        }
      }
      return 0;
    }
    S.over05 = getO('Over 0.5');
    S.over15 = getO('Over 1.5');
    S.over25 = getO('Over 2.5');
  }
}

// ── MATH UTIL ─────────────────────────────────────────────────────────────────
function poisson(k, lambda) {
  if (lambda <= 0) return k===0 ? 1 : 0;
  let p = Math.exp(-lambda);
  for (let i=0; i<k; i++) p *= lambda / (i+1);
  return Math.max(0, Math.min(1, p));
}

// P(total goals > 2.5) via independent Poisson — Over 2.5
function estPOver25(md) {
  const lam = md.home.avgScored || 1.2;
  const mu  = md.away.avgScored || 1.0;
  // P(total ≤ 2) = P(0-0)+P(1-0)+P(0-1)+P(2-0)+P(1-1)+P(0-2)
  const under = poisson(0,lam)*poisson(0,mu) + poisson(1,lam)*poisson(0,mu) +
                poisson(0,lam)*poisson(1,mu) + poisson(2,lam)*poisson(0,mu) +
                poisson(1,lam)*poisson(1,mu) + poisson(0,lam)*poisson(2,mu);
  return Math.max(0, Math.min(1, 1 - under));
}

// P(both score ≥ 2) — ambas marcam pelo menos 2
function estPBothScore2(md) {
  const lam = md.home.avgScored || 1.2;
  const mu  = md.away.avgScored || 1.0;
  const pH2 = 1 - poisson(0,lam) - poisson(1,lam); // P(home ≥ 2)
  const pA2 = 1 - poisson(0,mu)  - poisson(1,mu);  // P(away ≥ 2)
  return Math.max(0, Math.min(1, pH2 * pA2));
}

// Estimated probability of 1×0
function estP1x0(md) {
  return poisson(1, md.home.avgScored||1.2) * poisson(0, md.away.avgScored||1.0);
}
// Estimated probability of 0×1
function estP0x1(md) {
  return poisson(0, md.home.avgScored||1.2) * poisson(1, md.away.avgScored||1.0);
}
// Estimated probability of 2×0
function estP2x0(md) {
  return poisson(2, md.home.avgScored||1.2) * poisson(0, md.away.avgScored||1.0);
}
// Estimated probability of 0×2
function estP0x2(md) {
  return poisson(0, md.home.avgScored||1.2) * poisson(2, md.away.avgScored||1.0);
}

// ── BACK FAVORITO ANALYZER ───────────────────────────────────────────────────
function analyzeBackFavorito(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  // Determina o favorito: PPG ou winPct maior
  const hScore = (h.ppg||0)*2 + (h.winPct||0);
  const aScore = (a.ppg||0)*2 + (a.winPct||0);
  const isFavHome = hScore >= aScore;
  const fav = isFavHome ? h : a;
  const opp = isFavHome ? a : h;
  const favN = isFavHome ? hN : aN;
  const oppN = isFavHome ? aN : hN;
  const backOdd = parseFloat(opts.oddBackFav)||0;
  const hasOdd  = backOdd > 1;
  const impliedP = hasOdd ? 1/backOdd : null;
  const modelP   = Math.min(0.95, Math.max(0.05, fav.winPct||0.5));
  const edge     = hasOdd ? (modelP - impliedP) : null;

  const crit = [];
  crit.push({ label:`Win% ${favN} ≥55%`, ok:(fav.winPct||0)>=0.55, w:3,
    info:`${favN} vence ${Math.round((fav.winPct||0)*100)}% dos jogos como ${isFavHome?'mandante':'visitante'}` });
  crit.push({ label:`PPG ${favN} ≥1.6`, ok:(fav.ppg||0)>=1.6, w:3,
    info:`${favN} faz em média ${(fav.ppg||0).toFixed(2)} pontos/jogo` });
  crit.push({ label:`${oppN} win% ≤40%`, ok:(opp.winPct||0)<=0.4, w:2.5,
    info:`${oppN} vence apenas ${Math.round((opp.winPct||0)*100)}% dos jogos como ${isFavHome?'visitante':'mandante'}` });
  crit.push({ label:`${favN} média gols ≥1.5/j`, ok:(fav.avgScored||0)>=1.5, w:2,
    info:`${favN} marca em média ${(fav.avgScored||0).toFixed(2)} gols/j` });
  crit.push({ label:`${oppN} falha em marcar ≥35%`, ok:(opp.failedToScore||0)>=0.35, w:2,
    info:`${oppN} não marca em ${Math.round((opp.failedToScore||0)*100)}% dos jogos` });
  if (fav.xgFor>0) crit.push({ label:`xG ${favN} a favor ≥1.5`, ok:fav.xgFor>=1.5, w:2,
    info:`${favN} tem xG de ${fav.xgFor.toFixed(2)} — qualidade de chances criadas` });
  if (fav.cleanSheets>0) crit.push({ label:`CS ${favN} ≥25%`, ok:fav.cleanSheets>=0.25, w:1.5,
    info:`${favN} manteve CS em ${Math.round(fav.cleanSheets*100)}% dos jogos` });
  if (fav.firstToScore>0) crit.push({ label:`${favN} marca primeiro ≥50%`, ok:fav.firstToScore>=0.5, w:1.5,
    info:`${favN} abre o placar em ${Math.round(fav.firstToScore*100)}% dos jogos` });
  if (hasOdd) crit.push({ label:'Edge positivo (P(vitória) modelo > implícita)', ok:edge>0, w:3,
    info:`P modelo: ${Math.round(modelP*100)}% · P implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);
  const warns = [];
  if ((fav.winPct||0)<0.5) warns.push(`${favN} vence menos de 50% — superioridade questionável`);
  if ((opp.winPct||0)>0.35) warns.push(`${oppN} não é fraco — risco de surpresa`);
  if (hasOdd && backOdd < 1.4) warns.push('Odd muito baixa — retorno limitado para o risco');
  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72&&edge>0.03){vd='ENTRADA CONFIRMADA';rk='BAIXO';rec=`Back no favorito ${favN}. Odd: ${backOdd}. Edge positivo de ${Math.round(edge*100)}%.`;}
    else if (conf>=58&&edge>=0){vd='ENTRADA POSSÍVEL';rk='MÉDIO';rec='Favorito com boa estatística mas margem pequena. Stake moderado.';}
    else if (conf>=40){vd='EVITAR';rk='ALTO';rec='Favorito incerto. Estatísticas não justificam entrada.';}
    else{vd='REJEITAR';rk='EXTREMO';rec='Não há superioridade clara. Não apostar.';}
  } else {
    if (conf>=70){vd='ENTRADA CONFIRMADA';rk='BAIXO';rec=`${favN} é o favorito estatístico. Insira a odd para confirmar value.`;}
    else if (conf>=52){vd='ENTRADA POSSÍVEL';rk='MÉDIO';rec='Favorito com sinais positivos mas não dominante. Avaliar odd.';}
    else{vd='EVITAR';rk='ALTO';rec='Sem superioridade clara suficiente para back confiável.';}
  }
  return { method:'backfav', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, backOdd, favN, oppN, hN, aN };
}

// ── BACK GOLEADA ANALYZER (vence com 4+ gols) ────────────────────────────────
function analyzeBackGoleada(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  // Favorito em goleada = mandante (home advantage) ou quem tem maior avgScored
  const isFavHome = (h.avgScored||0) >= (a.avgScored||0);
  const fav = isFavHome ? h : a;
  const opp = isFavHome ? a : h;
  const favN = isFavHome ? hN : aN;
  const backOdd = parseFloat(opts.oddBackGoleada)||0;
  const hasOdd  = backOdd > 1;
  // Poisson: P(favoritescores 4+) * P(opp scores <4 against fav)
  const p4plus = 1 - poisson(0,fav.avgScored||1.5) - poisson(1,fav.avgScored||1.5) - poisson(2,fav.avgScored||1.5) - poisson(3,fav.avgScored||1.5);
  const impliedP = hasOdd ? 1/backOdd : null;
  const edge     = hasOdd ? (p4plus - impliedP) : null;

  const crit = [];
  crit.push({ label:`${favN} média gols ≥2.2/j`, ok:(fav.avgScored||0)>=2.2, w:4,
    info:`${favN} marca em média ${(fav.avgScored||0).toFixed(2)} gols/j — ataque prolífico` });
  crit.push({ label:`${favN} win% ≥65%`, ok:(fav.winPct||0)>=0.65, w:3,
    info:`${favN} vence ${Math.round((fav.winPct||0)*100)}% dos jogos como ${isFavHome?'mandante':'visitante'}` });
  crit.push({ label:`${aN} concede ≥2 gols/j fora`, ok:(opp.avgConceded||0)>=2.0, w:3,
    info:`${opp===a?aN:hN} sofre em média ${(opp.avgConceded||0).toFixed(2)} gols/j` });
  if (fav.over25>0) crit.push({ label:`Over 2.5 gols ≥60% jogos de ${favN}`, ok:fav.over25>=0.6, w:2.5,
    info:`${Math.round(fav.over25*100)}% dos jogos de ${favN} têm 3+ gols` });
  if (fav.xgFor>0) crit.push({ label:`xG ${favN} ≥2.2`, ok:fav.xgFor>=2.2, w:2.5,
    info:`${favN} tem xG a favor de ${fav.xgFor.toFixed(2)} — domínio ofensivo` });
  crit.push({ label:`${isFavHome?aN:hN} failedToScore ≥40%`, ok:(opp.failedToScore||0)>=0.4, w:2,
    info:`${isFavHome?aN:hN} não marca em ${Math.round((opp.failedToScore||0)*100)}% dos jogos` });
  if (fav.avgScored>0) crit.push({ label:`P(4+ gols) Poisson ≥10%`, ok:p4plus>=0.10, w:2,
    info:`Probabilidade modelo: ${Math.round(p4plus*100)}%` });
  if (hasOdd) crit.push({ label:'Edge positivo para goleada', ok:edge>0, w:3,
    info:`P modelo: ${Math.round(p4plus*100)}% · P implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);
  const warns = [];
  if ((fav.avgScored||0)<1.8) warns.push(`${favN} não é prolífico o suficiente para goleadas frequentes`);
  if ((opp.winPct||0)>0.3) warns.push('Adversário competitivo — goleada improvável');
  if (hasOdd && backOdd < 3) warns.push('Odd baixa para um mercado de alta variância');
  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=68&&edge>0.02){vd='ENTRADA CONFIRMADA';rk='MÉDIO';rec=`Back Goleada ${favN}. Odd: ${backOdd}. Ataque dominante + defesa fraca do adversário.`;}
    else if (conf>=52&&edge>=0){vd='ENTRADA POSSÍVEL';rk='ALTO';rec='Perfil de goleada presente mas com risco. Stake reduzida.';}
    else{vd='EVITAR';rk='EXTREMO';rec='Probabilidade de goleada muito baixa. Não apostar.';}
  } else {
    if (conf>=68){vd='ENTRADA CONFIRMADA';rk='MÉDIO';rec=`${favN} tem perfil de goleada. Insira a odd para análise de value.`;}
    else if (conf>=50){vd='ENTRADA POSSÍVEL';rk='ALTO';rec='Sinais parciais de goleada. Insira a odd para confirmar.';}
    else{vd='EVITAR';rk='EXTREMO';rec='Perfil estatístico não suporta goleada.';}
  }
  return { method:'backgoleada', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP:p4plus, impliedP, edge, backOdd, favN, hN, aN };
}

// ── OVER 70MIN ANALYZER (gol marcado a partir dos 70min) ─────────────────────
function analyzeOver70(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  const backOdd = parseFloat(opts.oddOver70)||0;
  const hasOdd  = backOdd > 1;
  // Jogo com gols = maior chance de gol tardio
  const avgTotal = ((h.avgTotal||0) + (a.avgTotal||0)) / 2 || (h.avgScored||1.2) + (a.avgScored||1.0);
  // P(pelo menos 1 gol nos últimos 20 min) ≈ 1 - e^(-λ*20/90), λ = avgTotal
  const lambda20 = avgTotal * (20/90);
  const modelP   = Math.max(0.1, Math.min(0.95, 1 - Math.exp(-lambda20)));
  const impliedP = hasOdd ? 1/backOdd : null;
  const edge     = hasOdd ? (modelP - impliedP) : null;

  const crit = [];
  crit.push({ label:'Média total gols/jogo ≥2.5 (jogos com muitos gols)', ok:avgTotal>=2.5, w:3,
    info:`Média estimada: ${avgTotal.toFixed(2)} gols/jogo — favorece gols tardios` });
  if (h.over25>0||a.over25>0) {
    const over25avg = ((h.over25||0)+(a.over25||0))/2;
    crit.push({ label:'Over 2.5 médio ≥45%', ok:over25avg>=0.45, w:3,
      info:`Médio entre os dois times: ${Math.round(over25avg*100)}% dos jogos com 3+ gols` });
  }
  if (h.over15>0||a.over15>0) {
    const over15avg = ((h.over15||0)+(a.over15||0))/2;
    crit.push({ label:'Over 1.5 médio ≥70% (jogos abertos)', ok:over15avg>=0.70, w:2.5,
      info:`Médio entre os dois times: ${Math.round(over15avg*100)}% dos jogos com 2+ gols` });
  }
  const avgScored = (h.avgScored||0) + (a.avgScored||0);
  crit.push({ label:'Soma médias de gols ≥2.8', ok:avgScored>=2.8, w:2.5,
    info:`${hN} (${(h.avgScored||0).toFixed(2)}) + ${aN} (${(a.avgScored||0).toFixed(2)}) = ${avgScored.toFixed(2)} gols/j` });
  crit.push({ label:`${hN} não guarda CS com frequência (≤30%)`, ok:(h.cleanSheets||0)<=0.3, w:2,
    info:`${hN} CS em casa: ${Math.round((h.cleanSheets||0)*100)}% — mandante costuma sofrer` });
  crit.push({ label:`${aN} não guarda CS fora com frequência (≤25%)`, ok:(a.cleanSheets||0)<=0.25, w:2,
    info:`${aN} CS fora: ${Math.round((a.cleanSheets||0)*100)}% — visitante costuma sofrer` });
  if (h.bothScore>0||a.bothScore>0) {
    const bttsAvg = ((h.bothScore||0)+(a.bothScore||0))/2;
    crit.push({ label:'BTTS médio ≥55% (ambos marcam → jogo aberto)', ok:bttsAvg>=0.55, w:2,
      info:`BTTS médio: ${Math.round(bttsAvg*100)}% — ambas as equipas costumam marcar` });
  }
  if (hasOdd) crit.push({ label:'Edge positivo (P(gol 70min) modelo > implícita)', ok:edge>0, w:3,
    info:`P modelo: ${Math.round(modelP*100)}% · P implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);
  const warns = [];
  if (avgTotal < 2.0) warns.push('Jogos de baixa pontuação — gol tardio menos provável');
  if ((h.cleanSheets||0)>0.4||(a.cleanSheets||0)>0.4) warns.push('Um dos times guarda CS com frequência');
  if (hasOdd && backOdd > 2.5) warns.push('Odd elevada — mercado precifica baixa probabilidade de gol tardio');
  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=70&&edge>0.03){vd='ENTRADA CONFIRMADA';rk='BAIXO';rec=`Entrar ao vivo entre 65-70min. Odd: ${backOdd}. Jogos prolíficos favorecem gol tardio.`;}
    else if (conf>=55&&edge>=0){vd='ENTRADA POSSÍVEL';rk='MÉDIO';rec='Perfil favorável mas margem pequena. Aguardar contexto ao vivo antes de entrar.';}
    else if (conf>=40){vd='EVITAR';rk='ALTO';rec='Gol tardio menos provável com estes dados. Avaliar contexto ao vivo.';}
    else{vd='REJEITAR';rk='EXTREMO';rec='Jogo de baixa pontuação. Não apostar em gol tardio.';}
  } else {
    if (conf>=70){vd='ENTRADA CONFIRMADA';rk='BAIXO';rec='Perfil de jogo prolífico. Insira a odd de ao vivo para confirmar value.';}
    else if (conf>=52){vd='ENTRADA POSSÍVEL';rk='MÉDIO';rec='Sinais moderados. Avaliar contexto do jogo ao vivo antes de entrar.';}
    else{vd='EVITAR';rk='ALTO';rec='Estatísticas não suportam probabilidade alta de gol tardio.';}
  }
  return { method:'over70', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, backOdd, hN, aN };
}

// ── BACK 2×2 ANALYZER ────────────────────────────────────────────────────────
// Objetivo: jogo com ambas marcando e placar alto (2-2 é o ideal mas qualquer
// resultado pontuado basta — Over 2.5 + BTTS é o mercado principal)
function analyzeBack2x2(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  const backOdd = parseFloat(opts.oddBack2x2)||0;
  const hasOdd  = backOdd > 1;

  const modelPOver = estPOver25(md);           // P(Over 2.5)
  const modelPBoth2= estPBothScore2(md);       // P(ambas ≥ 2 gols)
  const impliedP   = hasOdd ? 1/backOdd : null;
  const edge       = hasOdd ? (modelPOver - impliedP) : null;

  const crit = [];

  // 1. BTTS em casa (visitante também marca)
  crit.push({ label:'BTTS em casa ≥60% (ambos marcam)', ok:h.bothScore>=0.6, w:3,
    info:`Ambas marcam nos jogos em casa: ${Math.round(h.bothScore*100)}%` });

  // 2. BTTS fora (padrão se repete fora de casa)
  crit.push({ label:'BTTS fora ≥55% (visitante também marca fora)', ok:a.bothScore>=0.55, w:2.5,
    info:`Ambas marcam nos jogos fora de ${aN}: ${Math.round(a.bothScore*100)}%` });

  // 3. Over 2.5 em casa
  if (h.over25 > 0) {
    crit.push({ label:'Over 2.5 gols em casa ≥50%', ok:h.over25>=0.5, w:2.5,
      info:`${Math.round(h.over25*100)}% dos jogos em casa têm 3+ gols` });
  }

  // 4. Over 2.5 fora
  if (a.over25 > 0) {
    crit.push({ label:'Over 2.5 gols fora ≥50%', ok:a.over25>=0.5, w:2,
      info:`${Math.round(a.over25*100)}% dos jogos fora de ${aN} têm 3+ gols` });
  }

  // 5. Média total de gols em casa alta
  if (h.avgTotal > 0) {
    crit.push({ label:'Média total de gols em casa ≥2.8', ok:h.avgTotal>=2.8, w:2,
      info:`Média de ${h.avgTotal.toFixed(2)} gols/j nos jogos em casa` });
  }

  // 6. Média total de gols fora alta
  if (a.avgTotal > 0) {
    crit.push({ label:'Média total de gols fora ≥2.5', ok:a.avgTotal>=2.5, w:2,
      info:`Média de ${a.avgTotal.toFixed(2)} gols/j nos jogos fora de ${aN}` });
  }

  // 7. xG total dos dois lados (em casa)
  if (h.xgFor > 0 && h.xgAgainst > 0) {
    const xgT = h.xgFor + h.xgAgainst;
    crit.push({ label:'xG total em casa ≥3.0 (alta expectativa)', ok:xgT>=3.0, w:2,
      info:`xG↑ ${h.xgFor.toFixed(2)} + xG↓ ${h.xgAgainst.toFixed(2)} = ${xgT.toFixed(2)} esperados` });
  }

  // 8. Mandante ataca bem em casa
  crit.push({ label:'Mandante marca ≥1.5 gols/j em casa', ok:h.avgScored>=1.5, w:1.5,
    info:`${hN} marca média de ${h.avgScored.toFixed(2)} gols/j em casa` });

  // 9. Visitante marca fora
  crit.push({ label:'Visitante marca ≥1.1 gols/j fora', ok:a.avgScored>=1.1, w:1.5,
    info:`${aN} marca média de ${a.avgScored.toFixed(2)} gols/j fora` });

  // 10. Defesas vazadas — nenhum CS dominante
  crit.push({ label:'CS mandante em casa ≤25% (visitante marca)', ok:h.cleanSheets<=0.25, w:1.5,
    info:`Mandante guarda GS em ${Math.round(h.cleanSheets*100)}% dos jogos em casa` });
  crit.push({ label:'CS visitante fora ≤25% (mandante marca)', ok:a.cleanSheets<=0.25, w:1.5,
    info:`${aN} guarda GS em ${Math.round(a.cleanSheets*100)}% dos jogos fora` });

  // 11. Nenhum time com muita falha ofensiva
  crit.push({ label:'Mandante falha em marcar em casa ≤25%', ok:h.failedToScore<=0.25, w:1,
    info:`${hN} falhou em ${Math.round(h.failedToScore*100)}% dos jogos em casa` });
  crit.push({ label:'Visitante falha em marcar fora ≤40%', ok:a.failedToScore<=0.4, w:1,
    info:`${aN} falhou em ${Math.round(a.failedToScore*100)}% dos jogos fora` });

  // 12. Odds + edge (se fornecidas)
  if (hasOdd) {
    crit.push({ label:'Odds no range Over 2.5/BTTS (1.50–2.20)', ok:backOdd>=1.5&&backOdd<=2.2, w:1.5,
      info:`Odd inserida: ${backOdd} · Range ideal: 1.50–2.20` });
    crit.push({ label:'Edge positivo — P(Over 2.5) modelo > implícita', ok:edge>0.02, w:3,
      info:`P(Over 2.5) modelo: ${Math.round(modelPOver*100)}% · Implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });
  }

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);

  const warns = [];
  if (h.bothScore < 0.45) warns.push('BTTS em casa baixa — risco real de jogo sem gols dos dois lados');
  if (a.failedToScore > 0.5) warns.push(`${aN} não marca em mais de 50% dos jogos fora — BTTS comprometida`);
  if (h.cleanSheets > 0.4) warns.push('Mandante guarda CS com frequência — visitante pode não marcar');
  if (a.cleanSheets > 0.4) warns.push(`${aN} guarda CS fora com frequência — mandante pode não marcar`);
  if (h.games < 4) warns.push('Amostra pequena em casa (<4 jogos)');
  if (hasOdd && backOdd > 2.5) warns.push('Odd elevada — mercado aponta jogo potencialmente de baixa pontuação');
  if (hasOdd && edge < 0) warns.push('Probabilidade modelo abaixo da implícita — possível sem value');

  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72&&edge>0.02){ vd='ENTRADA CONFIRMADA'; rk='BAIXO'; rec=`Back 2×2 (Over 2.5 + BTTS). Edge de ${Math.round(edge*100)}%. P(ambas≥2): ${Math.round(modelPBoth2*100)}%.`; }
    else if (conf>=55&&edge>=0){ vd='ENTRADA POSSÍVEL'; rk='MÉDIO'; rec='Perfil pontuado, mas alguns critérios fracos. Stake reduzida (50–70%).'; }
    else if (conf>=40){ vd='EVITAR'; rk='ALTO'; rec='Dados insuficientes para confirmar jogo de alta pontuação.'; }
    else { vd='REJEITAR'; rk='EXTREMO'; rec='Perfil defensivo. Fora dos parâmetros do Back 2×2.'; }
  } else {
    if (conf>=70){ vd='ESTATÍSTICA FAVORÁVEL'; rk='BAIXO'; rec=`Perfil pontuado. P(Over 2.5) ≈ ${Math.round(modelPOver*100)}%, P(ambas≥2) ≈ ${Math.round(modelPBoth2*100)}%. Insira a odd para análise de value.`; }
    else if (conf>=50){ vd='PERFIL NEUTRO'; rk='MÉDIO'; rec='Sinais mistos. Alguns indicadores de gols presentes, outros não.'; }
    else { vd='ESTATÍSTICA DESFAVORÁVEL'; rk='ALTO'; rec='Perfil defensivo. Baixa probabilidade de jogo pontuado.'; }
  }

  return { method:'back2x2', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelPOver, modelPBoth2, impliedP, edge, backOdd, hN, aN };
}

// ── LAY 1×0 ANALYZER (mandante vence por 1×0 NÃO acontece) ───────────────────
function analyzeLay1x0(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  const layOdd = parseFloat(opts.oddLay1x0)||0;
  const hasOdd = layOdd > 1;

  const modelP  = estP1x0(md);
  const impliedP = hasOdd ? 1/layOdd : null;
  const edge    = hasOdd ? (impliedP - modelP) : null;

  const crit = [];

  // Core: if both teams score in home games → can't end 1-0 (away scored)
  crit.push({ label:'BTTS em casa ≥55% (visitante costuma marcar)', ok:h.bothScore>=0.55, w:3,
    info:`Ambas marcam em casa: ${Math.round(h.bothScore*100)}% — se visitante marca, nunca 1×0` });

  // Home team CS: if they don't keep clean sheets, away team scores → not 1-0
  crit.push({ label:'CS mandante em casa ≤25% (adversário marca)', ok:h.cleanSheets<=0.25, w:2.5,
    info:`Mandante guarda GS em apenas ${Math.round(h.cleanSheets*100)}% dos jogos em casa` });

  // Away team fails to score away: if low, they score more often → not 0 for away
  crit.push({ label:'Visitante falha em marcar fora ≤40%', ok:a.failedToScore<=0.4, w:2,
    info:`${aN} falhou em marcar em ${Math.round(a.failedToScore*100)}% dos jogos fora` });

  // xG total in home context: high xG → multiple goals expected
  if (h.xgFor>0 || h.xgAgainst>0) {
    const xgTotal = h.xgFor + h.xgAgainst;
    crit.push({ label:'xG total em casa ≥2.8 (jogo de muitos gols)', ok:xgTotal>=2.8, w:2,
      info:`xG a favor: ${h.xgFor.toFixed(2)} + xG contra: ${h.xgAgainst.toFixed(2)} = ${xgTotal.toFixed(2)} total` });
  }

  // Over 1.5 in home games: high → likely 2+ goals
  if (h.over15 > 0) {
    crit.push({ label:'Over 1.5 gols em casa ≥65%', ok:h.over15>=0.65, w:2,
      info:`${Math.round(h.over15*100)}% dos jogos em casa têm 2+ gols` });
  }

  // Over 2.5: if 3+ goals, impossible to be 1-0
  if (h.over25 > 0) {
    crit.push({ label:'Over 2.5 gols em casa ≥40% (3+ gols impossibilita 1×0)', ok:h.over25>=0.4, w:1.5,
      info:`${Math.round(h.over25*100)}% dos jogos em casa têm 3+ gols` });
  }

  // Average total goals: high → more scoring
  if (h.avgTotal > 0) {
    crit.push({ label:'Média total de gols em casa ≥2.3', ok:h.avgTotal>=2.3, w:1.5,
      info:`Média de ${h.avgTotal.toFixed(2)} gols totais por jogo em casa` });
  }

  // If home team scores a lot, likely more than 1 goal
  crit.push({ label:'Mandante marca ≥1.8 gols/j em casa (não para em 1)', ok:h.avgScored>=1.8, w:1,
    info:`${hN} marca em média ${h.avgScored.toFixed(2)} gols/j em casa` });

  // Away CS away (their clean sheets away = host doesn't score)
  crit.push({ label:'Visitante CS fora ≤15% (mandante costuma marcar contra)', ok:a.cleanSheets<=0.15, w:1,
    info:`${aN} manteve CS fora em ${Math.round(a.cleanSheets*100)}% dos jogos` });

  // Edge criterion if odds provided
  if (hasOdd) {
    crit.push({ label:`Edge de lay positivo (P(1×0) modelo < implícita)`, ok:edge>0, w:3,
      info:`P(1×0) modelo: ${Math.round(modelP*100)}% · Implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });
  }

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);

  const warns = [];
  if (h.bothScore < 0.4) warns.push('BTTS baixa — visitante raramente marca em casa do mandante');
  if (a.failedToScore > 0.55) warns.push(`${aN} falha em marcar em mais de 55% dos jogos fora`);
  if (h.cleanSheets > 0.4) warns.push('Mandante mantém CS frequentemente — risco de 1×0 elevado');
  if (hasOdd && layOdd < 4) warns.push('Odd de lay baixa — exposição elevada em relação ao retorno');
  if (hasOdd && modelP > impliedP) warns.push(`Modelo sugere P(1×0) maior que implícita — possível lay sem value`);

  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72 && edge>0.02){ vd='LAY CONFIRMADO'; rk='BAIXO'; rec=`Lay 1×0. Estatísticas robustas contra este placar. Exposição: ${((layOdd-1)).toFixed(2)}× o stake.`; }
    else if (conf>=55 && edge>=0){ vd='LAY POSSÍVEL'; rk='MÉDIO'; rec='Entrada com stake reduzida. Alguns critérios não atendidos — confirme edge.'; }
    else if (conf>=40){ vd='EVITAR LAY'; rk='ALTO'; rec='Critérios insuficientes para lay seguro do 1×0.'; }
    else { vd='LAY REJEITADO'; rk='EXTREMO'; rec='Estatísticas suportam possibilidade de 1×0. Não lay.'; }
  } else {
    if (conf>=70){ vd='ESTATÍSTICA FAVORÁVEL'; rk='BAIXO'; rec='Perfil estatístico desfavorável ao 1×0. Insira a odd de lay para análise de value.'; }
    else if (conf>=50){ vd='PERFIL NEUTRO'; rk='MÉDIO'; rec='Sinais mistos. Insira a odd do lay para determinar value.'; }
    else { vd='ESTATÍSTICA DESFAVORÁVEL'; rk='ALTO'; rec='Estatísticas não descartam o 1×0 com clareza.'; }
  }

  return { method:'lay1x0', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, layOdd, hN, aN };
}

// ── LAY 0×1 ANALYZER (visitante vence por 0×1 NÃO acontece) ──────────────────
function analyzeLay0x1(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  const layOdd = parseFloat(opts.oddLay0x1)||0;
  const hasOdd = layOdd > 1;

  const modelP   = estP0x1(md);
  const impliedP = hasOdd ? 1/layOdd : null;
  const edge     = hasOdd ? (impliedP - modelP) : null;

  const crit = [];

  // STRONGEST: home team fails to score at home → if near 0%, can't end 0x1
  crit.push({ label:'Mandante falha em marcar em casa ≤20% (quase sempre marca)', ok:h.failedToScore<=0.2, w:3,
    info:`${hN} falhou em marcar em apenas ${Math.round(h.failedToScore*100)}% dos jogos em casa` });

  // Away team CS away (= home team fails to score against them)
  crit.push({ label:'Visitante CS fora ≤20% (mandante costuma marcar contra)', ok:a.cleanSheets<=0.2, w:3,
    info:`${aN} manteve CS fora em ${Math.round(a.cleanSheets*100)}% dos jogos` });

  // BTTS in away context: if both score in away games, 0x1 is less likely
  crit.push({ label:'BTTS fora ≥50% (ambos marcam nos jogos do visitante)', ok:a.bothScore>=0.5, w:2.5,
    info:`Ambas marcam nos jogos fora de ${aN}: ${Math.round(a.bothScore*100)}%` });

  // Home xG: if they create chances, they score → not 0
  if (h.xgFor>0) {
    crit.push({ label:'xG mandante a favor ≥1.4 (cria chances em casa)', ok:h.xgFor>=1.4, w:2,
      info:`${hN} tem xG a favor de ${h.xgFor.toFixed(2)} em casa` });
  }

  // Over 1.5 in away context: high → 2+ goals (if away team scores 1 and home scores 1+, not 0x1)
  if (a.over15 > 0) {
    crit.push({ label:'Over 1.5 gols fora ≥65%', ok:a.over15>=0.65, w:2,
      info:`${Math.round(a.over15*100)}% dos jogos fora de ${aN} têm 2+ gols` });
  }

  // Over 2.5 away: if 3+ goals, impossible 0-1
  if (a.over25 > 0) {
    crit.push({ label:'Over 2.5 gols fora ≥40% (3+ gols impossibilita 0×1)', ok:a.over25>=0.4, w:1.5,
      info:`${Math.round(a.over25*100)}% dos jogos fora de ${aN} têm 3+ gols` });
  }

  // Average total away: high → more scoring
  if (a.avgTotal > 0) {
    crit.push({ label:'Média total de gols fora ≥2.3', ok:a.avgTotal>=2.3, w:1.5,
      info:`Média de ${a.avgTotal.toFixed(2)} gols totais por jogo fora` });
  }

  // Home avg scored: if they score well, won't be 0
  crit.push({ label:'Mandante marca ≥1.4 gols/j em casa', ok:h.avgScored>=1.4, w:1,
    info:`${hN} marca em média ${h.avgScored.toFixed(2)} gols/j em casa` });

  // Home first to score
  if (h.firstToScore > 0) {
    crit.push({ label:'Mandante marca primeiro ≥45%', ok:h.firstToScore>=0.45, w:1,
      info:`${hN} marca primeiro em ${Math.round(h.firstToScore*100)}% dos jogos em casa` });
  }

  // Edge if odds provided
  if (hasOdd) {
    crit.push({ label:`Edge de lay positivo (P(0×1) modelo < implícita)`, ok:edge>0, w:3,
      info:`P(0×1) modelo: ${Math.round(modelP*100)}% · Implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });
  }

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);

  const warns = [];
  if (h.failedToScore > 0.3) warns.push(`${hN} falha em marcar em ${Math.round(h.failedToScore*100)}% dos jogos — risco real de 0×1`);
  if (a.cleanSheets > 0.3) warns.push(`${aN} mantém CS fora com frequência — mandante pode não marcar`);
  if (a.avgScored > 1.5) warns.push(`${aN} marca bem fora (${a.avgScored.toFixed(2)}/j) — precisa de mais que 1 para não ser 0×1`);
  if (hasOdd && layOdd < 4) warns.push('Odd de lay baixa — exposição elevada em relação ao retorno');
  if (hasOdd && modelP > impliedP) warns.push(`Modelo sugere P(0×1) maior que implícita — possível lay sem value`);

  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72 && edge>0.02){ vd='LAY CONFIRMADO'; rk='BAIXO'; rec=`Lay 0×1. Estatísticas robustas contra este placar. Exposição: ${((layOdd-1)).toFixed(2)}× o stake.`; }
    else if (conf>=55 && edge>=0){ vd='LAY POSSÍVEL'; rk='MÉDIO'; rec='Entrada com stake reduzida. Confirme edge antes de entrar.'; }
    else if (conf>=40){ vd='EVITAR LAY'; rk='ALTO'; rec='Critérios insuficientes para lay seguro do 0×1.'; }
    else { vd='LAY REJEITADO'; rk='EXTREMO'; rec='Estatísticas suportam possibilidade de 0×1. Não lay.'; }
  } else {
    if (conf>=70){ vd='ESTATÍSTICA FAVORÁVEL'; rk='BAIXO'; rec='Perfil estatístico desfavorável ao 0×1. Insira a odd de lay para análise de value.'; }
    else if (conf>=50){ vd='PERFIL NEUTRO'; rk='MÉDIO'; rec='Sinais mistos. Insira a odd do lay para determinar value.'; }
    else { vd='ESTATÍSTICA DESFAVORÁVEL'; rk='ALTO'; rec='Estatísticas não descartam o 0×1 com clareza.'; }
  }

  return { method:'lay0x1', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, layOdd, hN, aN };
}

// ── LAY ZEBRA ANALYZER (lay na vitória do azarão) ────────────────────────────
// Azarão = time com winPct claramente menor. Lay = apostamos que ele NÃO vence.
function analyzeLayZebra(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';

  // Identifica zebra: quem tem menor PPG+winPct
  const hPower = (h.ppg||0)*2 + (h.winPct||0);
  const aPower = (a.ppg||0)*2 + (a.winPct||0);
  const isZebraHome = hPower <= aPower;
  const zebra = isZebraHome ? h : a;
  const fav   = isZebraHome ? a : h;
  const zebraN = isZebraHome ? hN : aN;
  const favN   = isZebraHome ? aN : hN;
  const gap    = Math.abs(hPower - aPower); // diferença de poder

  const layOdd  = parseFloat(opts.oddLayZebra)||0;
  const hasOdd  = layOdd > 1;
  // P(zebra vence) ≈ winPct do zebra no contexto
  const modelP  = Math.max(0.03, Math.min(0.45, zebra.winPct||0.2));
  const impliedP = hasOdd ? 1/layOdd : null;
  const edge     = hasOdd ? (impliedP - modelP) : null;

  const crit = [];

  // Diferença de poder entre os times
  crit.push({ label:`Gap de poder ≥1.0 (favorito claramente superior)`, ok:gap>=1.0, w:4,
    info:`Gap calculado: ${gap.toFixed(2)} — ${favN} (${hPower.toFixed(2)}) vs ${zebraN} (${aPower.toFixed(2)})` });

  // Zebra vence raramente
  crit.push({ label:`Win% do azarão ≤30%`, ok:(zebra.winPct||0)<=0.3, w:3.5,
    info:`${zebraN} vence apenas ${Math.round((zebra.winPct||0)*100)}% como ${isZebraHome?'mandante':'visitante'}` });

  // Favorito tem PPG forte
  crit.push({ label:`PPG do favorito ≥1.6`, ok:(fav.ppg||0)>=1.6, w:3,
    info:`${favN} acumula ${(fav.ppg||0).toFixed(2)} pontos/jogo — consistência alta` });

  // Zebra falha em marcar frequentemente
  crit.push({ label:`Azarão falha em marcar ≥45%`, ok:(zebra.failedToScore||0)>=0.45, w:2.5,
    info:`${zebraN} não marca em ${Math.round((zebra.failedToScore||0)*100)}% dos jogos — ataque ineficiente` });

  // Favorito marca bem
  crit.push({ label:`Favorito marca ≥1.5 gols/j`, ok:(fav.avgScored||0)>=1.5, w:2,
    info:`${favN} marca em média ${(fav.avgScored||0).toFixed(2)} gols/j` });

  // Zebra concede muito
  crit.push({ label:`Azarão concede ≥1.8 gols/j`, ok:(zebra.avgConceded||0)>=1.8, w:2,
    info:`${zebraN} sofre em média ${(zebra.avgConceded||0).toFixed(2)} gols/j — defesa exposta` });

  // Zebra raramente bate o favorito (CS favorito)
  if (fav.cleanSheets>0) {
    crit.push({ label:`CS do favorito ≥25%`, ok:fav.cleanSheets>=0.25, w:1.5,
      info:`${favN} mantém CS em ${Math.round(fav.cleanSheets*100)}% dos jogos — zebra raramente passa` });
  }

  // xG desfavorável ao zebra
  if (zebra.xgFor>0 && fav.xgFor>0) {
    const xgGap = fav.xgFor - zebra.xgFor;
    crit.push({ label:`xG favorito supera zebra em ≥0.6`, ok:xgGap>=0.6, w:1.5,
      info:`${favN} xG: ${fav.xgFor.toFixed(2)} vs ${zebraN} xG: ${zebra.xgFor.toFixed(2)} — diferença: +${xgGap.toFixed(2)}` });
  }

  // Edge com odd
  if (hasOdd) {
    crit.push({ label:`Edge positivo (P(zebra vence) modelo < implícita)`, ok:edge>0, w:3,
      info:`P modelo: ${Math.round(modelP*100)}% · Implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });
  }

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);

  const warns = [];
  if (gap < 0.8) warns.push('Gap de poder pequeno — zebra mais competitiva do que parece');
  if ((zebra.winPct||0) > 0.3) warns.push(`${zebraN} vence com mais frequência do que o esperado para um azarão`);
  if (hasOdd && layOdd < 3) warns.push('Odd de lay baixa para um azarão — exposição elevada para retorno pequeno');
  if (hasOdd && layOdd > 10) warns.push('Odd muito alta — modelo subestima a zebra ou há erro nos dados');
  if (hasOdd && modelP > impliedP) warns.push('P(zebra vence) maior que implícita — sem value no lay');

  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72&&edge>0.03){vd='LAY CONFIRMADO';rk='BAIXO';rec=`Lay Zebra — ${zebraN} tem baixíssima chance de vitória. Exposição: ${((layOdd-1)).toFixed(2)}× stake.`;}
    else if (conf>=55&&edge>=0){vd='LAY POSSÍVEL';rk='MÉDIO';rec=`Lay Zebra com stake reduzida. ${zebraN} raramente vence neste contexto.`;}
    else if (conf>=40){vd='EVITAR LAY';rk='ALTO';rec='Gap insuficiente para lay seguro. Azarão mais competitivo do que aparenta.';}
    else{vd='LAY REJEITADO';rk='EXTREMO';rec='Zebra tem chances reais de vitória. Não lay.';}
  } else {
    if (conf>=70){vd='ESTATÍSTICA FAVORÁVEL';rk='BAIXO';rec=`${zebraN} é o azarão claro. Insira a odd de lay para análise de value.`;}
    else if (conf>=50){vd='PERFIL NEUTRO';rk='MÉDIO';rec='Superioridade relativa do favorito mas não dominante. Avaliar odd.';}
    else{vd='ESTATÍSTICA DESFAVORÁVEL';rk='ALTO';rec='Zebra tem capacidade de surpreender. Sem lay recomendado.';}
  }

  return { method:'layzebra', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, layOdd, zebraN, favN, hN, aN };
}

// ── LAY 2×0 ANALYZER (mandante vence por 2×0 NÃO acontece) ───────────────────
function analyzeLay2x0(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  const layOdd = parseFloat(opts.oddLay2x0)||0;
  const hasOdd = layOdd > 1;

  const modelP   = estP2x0(md);
  const impliedP = hasOdd ? 1/layOdd : null;
  const edge     = hasOdd ? (impliedP - modelP) : null;

  const crit = [];

  // Visitante falha pouco em marcar fora → quase sempre marca → não sai 2x0
  crit.push({ label:'Visitante falha em marcar fora ≤40%', ok:a.failedToScore<=0.4, w:3,
    info:`${aN} falhou em marcar em ${Math.round(a.failedToScore*100)}% dos jogos fora — marca com frequência` });

  // BTTS em casa alto → visitante costuma marcar → não fica em 0
  crit.push({ label:'BTTS em casa ≥55% (visitante costuma marcar)', ok:h.bothScore>=0.55, w:2.5,
    info:`Ambas marcam em ${Math.round(h.bothScore*100)}% dos jogos em casa do mandante` });

  // Over 2.5 em casa → 3+ gols → se visitante marca, não é 2x0
  if (h.over25 > 0) {
    crit.push({ label:'Over 2.5 gols em casa ≥40% (3+ gols desfaz 2×0)', ok:h.over25>=0.4, w:2,
      info:`${Math.round(h.over25*100)}% dos jogos em casa têm 3+ gols` });
  }

  // xG total alto → múltiplos gols esperados
  if (h.xgFor>0 || h.xgAgainst>0) {
    const xgT = h.xgFor + h.xgAgainst;
    crit.push({ label:'xG total em casa ≥2.8', ok:xgT>=2.8, w:2,
      info:`xG total: ${xgT.toFixed(2)} — favorece mais gols e placar diferente de 2×0` });
  }

  // Visitante CS fora baixo → mandante marca contra eles, mas visitante também costuma marcar
  crit.push({ label:'Visitante CS fora ≤20% (quase sempre sofre e marca)', ok:a.cleanSheets<=0.2, w:1.5,
    info:`${aN} manteve CS fora em apenas ${Math.round(a.cleanSheets*100)}% dos jogos` });

  // Over 1.5 fora do visitante → jogos do visitante têm múltiplos gols
  if (a.over15 > 0) {
    crit.push({ label:'Over 1.5 gols fora ≥65%', ok:a.over15>=0.65, w:1.5,
      info:`${Math.round(a.over15*100)}% dos jogos fora de ${aN} têm 2+ gols` });
  }

  // Mandante não para no 2° gol → costuma marcar mais ou sofre gols
  if (h.avgTotal > 0) {
    crit.push({ label:'Média total de gols em casa ≥2.5', ok:h.avgTotal>=2.5, w:1,
      info:`Média de ${h.avgTotal.toFixed(2)} gols/jogo em casa — placar tende a crescer além de 2×0` });
  }

  if (hasOdd) {
    crit.push({ label:'Edge de lay positivo (P(2×0) modelo < implícita)', ok:edge>0, w:3,
      info:`P(2×0) modelo: ${Math.round(modelP*100)}% · Implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });
  }

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);

  const warns = [];
  if (a.failedToScore > 0.5) warns.push(`${aN} falha em marcar em mais da metade dos jogos fora — risco de 2×0 elevado`);
  if (h.cleanSheets > 0.35) warns.push('Mandante mantém CS com frequência — possível defesa forte');
  if (hasOdd && layOdd < 5) warns.push('Odd de lay baixa para placar específico — exposição elevada');
  if (hasOdd && modelP > impliedP) warns.push('Modelo sugere P(2×0) maior que implícita — possível lay sem value');

  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72 && edge>0.02){ vd='LAY CONFIRMADO'; rk='BAIXO'; rec=`Lay 2×0. Estatísticas contra este placar. Exposição: ${((layOdd-1)).toFixed(2)}× o stake.`; }
    else if (conf>=55 && edge>=0){ vd='LAY POSSÍVEL'; rk='MÉDIO'; rec='Entrada com stake reduzida. Confirme edge.'; }
    else if (conf>=40){ vd='EVITAR LAY'; rk='ALTO'; rec='Critérios insuficientes para lay seguro do 2×0.'; }
    else { vd='LAY REJEITADO'; rk='EXTREMO'; rec='Estatísticas não descartam o 2×0. Não lay.'; }
  } else {
    if (conf>=70){ vd='ESTATÍSTICA FAVORÁVEL'; rk='BAIXO'; rec='Perfil desfavorável ao 2×0. Insira a odd de lay para análise de value.'; }
    else if (conf>=50){ vd='PERFIL NEUTRO'; rk='MÉDIO'; rec='Sinais mistos. Insira a odd do lay para determinar value.'; }
    else { vd='ESTATÍSTICA DESFAVORÁVEL'; rk='ALTO'; rec='Estatísticas não descartam o 2×0 com clareza.'; }
  }

  return { method:'lay2x0', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, layOdd, hN, aN };
}

// ── LAY 0×2 ANALYZER (visitante vence por 0×2 NÃO acontece) ──────────────────
function analyzeLay0x2(md, opts) {
  const h = md.home, a = md.away;
  const hN = md.homeTeam||'Mandante', aN = md.awayTeam||'Visitante';
  const layOdd = parseFloat(opts.oddLay0x2)||0;
  const hasOdd = layOdd > 1;

  const modelP   = estP0x2(md);
  const impliedP = hasOdd ? 1/layOdd : null;
  const edge     = hasOdd ? (impliedP - modelP) : null;

  const crit = [];

  // Mandante falha pouco em marcar em casa → quase sempre marca → não fica em 0
  crit.push({ label:'Mandante falha em marcar em casa ≤20%', ok:h.failedToScore<=0.2, w:3,
    info:`${hN} falhou em marcar em apenas ${Math.round(h.failedToScore*100)}% dos jogos em casa` });

  // CS do visitante fora baixo → mandante marca contra eles
  crit.push({ label:'Visitante CS fora ≤20% (mandante costuma marcar)', ok:a.cleanSheets<=0.2, w:2.5,
    info:`${aN} manteve CS fora em ${Math.round(a.cleanSheets*100)}% dos jogos` });

  // BTTS fora alto → ambos marcam → mandante não fica em 0
  crit.push({ label:'BTTS fora ≥50% (mandante quase sempre marca contra)', ok:a.bothScore>=0.5, w:2.5,
    info:`Ambas marcam em ${Math.round(a.bothScore*100)}% dos jogos fora de ${aN}` });

  // Over 2.5 fora → 3+ gols → se mandante marca, não é 0x2
  if (a.over25 > 0) {
    crit.push({ label:'Over 2.5 gols fora ≥40% (3+ gols desfaz 0×2)', ok:a.over25>=0.4, w:2,
      info:`${Math.round(a.over25*100)}% dos jogos fora de ${aN} têm 3+ gols` });
  }

  // xG mandante a favor alto
  if (h.xgFor > 0) {
    crit.push({ label:'xG mandante a favor ≥1.4 em casa', ok:h.xgFor>=1.4, w:2,
      info:`${hN} tem xG a favor de ${h.xgFor.toFixed(2)} em casa — cria oportunidades` });
  }

  // Over 1.5 em casa → jogos com múltiplos gols
  if (h.over15 > 0) {
    crit.push({ label:'Over 1.5 gols em casa ≥65%', ok:h.over15>=0.65, w:1.5,
      info:`${Math.round(h.over15*100)}% dos jogos em casa têm 2+ gols` });
  }

  // Mandante marca primeiro com frequência
  if (h.firstToScore > 0) {
    crit.push({ label:'Mandante marca primeiro ≥45% em casa', ok:h.firstToScore>=0.45, w:1,
      info:`${hN} marca primeiro em ${Math.round(h.firstToScore*100)}% dos jogos em casa` });
  }

  if (hasOdd) {
    crit.push({ label:'Edge de lay positivo (P(0×2) modelo < implícita)', ok:edge>0, w:3,
      info:`P(0×2) modelo: ${Math.round(modelP*100)}% · Implícita: ${Math.round(impliedP*100)}% · Edge: ${edge>=0?'+':''}${Math.round(edge*100)}%` });
  }

  const score = crit.reduce((s,c)=>s+(c.ok?c.w:0),0);
  const maxS  = crit.reduce((s,c)=>s+c.w,0);
  const conf  = Math.round(score/maxS*100);

  const warns = [];
  if (h.failedToScore > 0.3) warns.push(`${hN} falha em marcar em ${Math.round(h.failedToScore*100)}% dos jogos em casa — risco real de 0×2`);
  if (a.avgScored > 1.8) warns.push(`${aN} marca muito fora (${a.avgScored.toFixed(2)}/j) — pode construir 0×2`);
  if (hasOdd && layOdd < 5) warns.push('Odd de lay baixa para placar específico — exposição elevada');
  if (hasOdd && modelP > impliedP) warns.push('Modelo sugere P(0×2) maior que implícita — possível lay sem value');

  let vd, rk, rec;
  if (hasOdd) {
    if (conf>=72 && edge>0.02){ vd='LAY CONFIRMADO'; rk='BAIXO'; rec=`Lay 0×2. Estatísticas contra este placar. Exposição: ${((layOdd-1)).toFixed(2)}× o stake.`; }
    else if (conf>=55 && edge>=0){ vd='LAY POSSÍVEL'; rk='MÉDIO'; rec='Entrada com stake reduzida. Confirme edge.'; }
    else if (conf>=40){ vd='EVITAR LAY'; rk='ALTO'; rec='Critérios insuficientes para lay seguro do 0×2.'; }
    else { vd='LAY REJEITADO'; rk='EXTREMO'; rec='Estatísticas não descartam o 0×2. Não lay.'; }
  } else {
    if (conf>=70){ vd='ESTATÍSTICA FAVORÁVEL'; rk='BAIXO'; rec='Perfil desfavorável ao 0×2. Insira a odd de lay para análise de value.'; }
    else if (conf>=50){ vd='PERFIL NEUTRO'; rk='MÉDIO'; rec='Sinais mistos. Insira a odd do lay para determinar value.'; }
    else { vd='ESTATÍSTICA DESFAVORÁVEL'; rk='ALTO'; rec='Estatísticas não descartam o 0×2 com clareza.'; }
  }

  return { method:'lay0x2', vd, rk, rec, conf, score, maxS, crit, warns, hasOdd,
           modelP, impliedP, edge, layOdd, hN, aN };
}

// ── RENDER MATCH LIST ─────────────────────────────────────────────────────────
function renderList() {
  const el = document.getElementById('ml');
  if (!S.matches.length) { el.innerHTML='<div class="emp"><span class="ei">○</span><p>Nenhum jogo na fila</p></div>'; return; }
  el.innerHTML = S.matches.map(m=>{ try{ return cardMatch(m); } catch(e){ return `<div style="color:#f87171;padding:10px;border:1px solid #333;margin-bottom:8px">${e.message}</div>`; } }).join('');
  refreshABar();
}

function fmt(n)  { return (n&&n>0)?n.toFixed(2):'N/D'; }
function fmtP(n) { return (n&&n>0)?Math.round(n*100)+'%':'N/D'; }
function fmtPp(n){ return (n&&n>0)?Math.round(n*100)+'%':'—'; } // shorter
function fmForm(seq) {
  if(!seq) return '<span style="color:#5e5e5e">N/D</span>';
  return seq.split('').slice(-6).map(c=>{
    const lc=c.toUpperCase();
    const cls=lc==='W'?'fw':lc==='D'?'fd':'fl';
    return `<span class="${cls}">${lc}</span>`;
  }).join('');
}

function cardMatch(m) {
  if (m.status==='parsing') return `<div class="mc"><div class="mh"><div><div class="mt" style="color:#666">Processando...</div><div class="mm">${m.file.name}</div></div><span class="bk bk-p">▶ PARSEANDO</span></div></div>`;
  if (m.status==='error')   return `<div class="mc"><div class="mh"><div><div class="mt" style="color:#f87171">Erro ao processar</div><div class="mm">${m.errMsg||''}</div></div><div style="display:flex;gap:8px;align-items:center"><span class="bk bk-e">✕ ERRO</span><button class="brm" onclick="rm(${m.id})">✕</button></div></div></div>`;

  const d  = m.data;
  const hN = d.homeTeam||'Mandante', aN = d.awayTeam||'Visitante';
  const isFH = (d.home.ppg*0.6+d.home.winPct*0.4) >= (d.away.ppg*0.6+d.away.winPct*0.4);
  const favN = isFH?hN:aN;
  const p1x0  = Math.round(estP1x0(d)*100);
  const p0x1  = Math.round(estP0x1(d)*100);
  const pOver = Math.round(estPOver25(d)*100);
  const pB2   = Math.round(estPBothScore2(d)*100);

  return `<div class="mc" id="mc${m.id}">
  <div class="mh">
    <div>
      <div class="mt">${hN}<span>×</span>${aN}<span class="chip">O2.5≈${pOver}%</span><span class="chip">B≥2≈${pB2}%</span><span class="lbadge">P(1×0)≈${p1x0}%</span><span class="lbadge">P(0×1)≈${p0x1}%</span></div>
      <div class="mm">${d.competition||'—'}${d.round?' · R'+d.round:''}${d.date?' · '+d.date:''}</div>
    </div>
    <div style="display:flex;gap:8px;align-items:center">
      <span class="bk bk-r">PRONTO</span>
      <button class="brm" onclick="rm(${m.id})" title="Remover">✕</button>
    </div>
  </div>
  <div class="mb">
    <div class="sl">Estatísticas do Contexto</div>
    <div class="sg">
      <div>
        <div class="sc">${hN} (casa)</div>
        <div class="si"><span class="sk">PPG</span><span class="sv">${fmt(d.home.ppg)}</span></div>
        <div class="si"><span class="sk">Win%</span><span class="sv">${fmtP(d.home.winPct)}</span></div>
        <div class="si"><span class="sk">Gols/j</span><span class="sv">${fmt(d.home.avgScored)}</span></div>
        <div class="si"><span class="sk">Sofre/j</span><span class="sv">${fmt(d.home.avgConceded)}</span></div>
        <div class="si"><span class="sk">Total/j</span><span class="sv">${fmt(d.home.avgTotal)}</span></div>
        <div class="si"><span class="sk">xG↑</span><span class="sv">${fmt(d.home.xgFor)}</span></div>
        <div class="si"><span class="sk">CS%</span><span class="sv">${fmtP(d.home.cleanSheets)}</span></div>
        <div class="si"><span class="sk">Falhou%</span><span class="sv">${fmtP(d.home.failedToScore)}</span></div>
        <div class="si"><span class="sk">BTTS%</span><span class="sv">${fmtP(d.home.bothScore)}</span></div>
        <div class="si"><span class="sk">O1.5%</span><span class="sv">${fmtPp(d.home.over15)}</span></div>
        <div class="si"><span class="sk">O2.5%</span><span class="sv">${fmtPp(d.home.over25)}</span></div>
        <div class="fs">${fmForm(d.homeForm)}</div>
      </div>
      <div class="vs">VS</div>
      <div>
        <div class="sc">${aN} (fora)</div>
        <div class="si"><span class="sk">PPG</span><span class="sv">${fmt(d.away.ppg)}</span></div>
        <div class="si"><span class="sk">Win%</span><span class="sv">${fmtP(d.away.winPct)}</span></div>
        <div class="si"><span class="sk">Gols/j</span><span class="sv">${fmt(d.away.avgScored)}</span></div>
        <div class="si"><span class="sk">Sofre/j</span><span class="sv">${fmt(d.away.avgConceded)}</span></div>
        <div class="si"><span class="sk">Total/j</span><span class="sv">${fmt(d.away.avgTotal)}</span></div>
        <div class="si"><span class="sk">xG↑</span><span class="sv">${fmt(d.away.xgFor)}</span></div>
        <div class="si"><span class="sk">CS%</span><span class="sv">${fmtP(d.away.cleanSheets)}</span></div>
        <div class="si"><span class="sk">Falhou%</span><span class="sv">${fmtP(d.away.failedToScore)}</span></div>
        <div class="si"><span class="sk">BTTS%</span><span class="sv">${fmtP(d.away.bothScore)}</span></div>
        <div class="si"><span class="sk">O1.5%</span><span class="sv">${fmtPp(d.away.over15)}</span></div>
        <div class="si"><span class="sk">O2.5%</span><span class="sv">${fmtPp(d.away.over25)}</span></div>
        <div class="fs">${fmForm(d.awayForm)}</div>
      </div>
    </div>

    <div class="sl">Back 2×2 — Odd (Over 2.5 / BTTS / mercado combinado)</div>
    <div class="og2" style="grid-template-columns:1fr">
      <div><label>Odd de back (Over 2.5, BTTS, etc.)</label><input type="number" step="0.01" min="1.01" placeholder="ex: 1.85" value="${m.opts.oddBack2x2}" oninput="setOpt(${m.id},'oddBack2x2',this.value)"></div>
    </div>

    <div class="sl">Lay Placar — Odds de back no exchange (opcional)</div>
    <div class="og2">
      <div><label>Lay 1×0 — odd de back no 1×0</label><input type="number" step="0.01" min="2" placeholder="ex: 8.00" value="${m.opts.oddLay1x0}" oninput="setOpt(${m.id},'oddLay1x0',this.value)"></div>
      <div><label>Lay 0×1 — odd de back no 0×1</label><input type="number" step="0.01" min="2" placeholder="ex: 10.00" value="${m.opts.oddLay0x1}" oninput="setOpt(${m.id},'oddLay0x1',this.value)"></div>
    </div>

    <button class="ban" onclick="runAnalyze(${m.id})">↺ REANALISAR COM ODDS ATUALIZADAS →</button>
  </div></div>`;
}

// ── ENTRY CARD HELPERS ────────────────────────────────────────────────────────
const POSITIVE_VD = new Set(['ENTRADA CONFIRMADA','ENTRADA POSSÍVEL','LAY CONFIRMADO','LAY POSSÍVEL','ESTATÍSTICA FAVORÁVEL']);
const isPositive  = vd => POSITIVE_VD.has(vd);

function getMercado(method, a) {
  if (method === 'backfav') {
    const odd = a.hasOdd ? ` · Odd ${a.backOdd}` : '';
    return { name:`Resultado do Favorito${odd}`, sub:`Apostar na vitória de ${a.favN} — equipa com melhor desempenho` };
  }
  if (method === 'back2x2') {
    const odd = a.hasOdd ? ` · Odd ${a.backOdd}` : '';
    return { name:`Over 2.5 Gols / Ambas Marcam (BTTS)${odd}`, sub:'Qualquer resultado com 3+ gols garante o lucro' };
  }
  if (method === 'backgoleada') {
    const odd = a.hasOdd ? ` · Odd ${a.backOdd}` : '';
    return { name:`Goleada — Vitória com 4+ Gols${odd}`, sub:`${a.favN} vence marcando 4 ou mais gols na partida` };
  }
  if (method === 'over70') {
    const odd = a.hasOdd ? ` · Odd ${a.backOdd}` : '';
    return { name:`Over Gol — Marcado a partir dos 70min${odd}`, sub:'Ao menos 1 gol acontece nos últimos 20 minutos de jogo' };
  }
  if (method === 'layzebra') {
    const odd = a.hasOdd ? ` · Lay odd ${a.layOdd} (exposição: ${((a.layOdd-1)).toFixed(2)}× stake)` : '';
    return { name:`Lay Zebra — Vitória do Azarão${odd}`, sub:`Apostando que ${a.zebraN} NÃO vence a partida` };
  }
  const layLabel = {lay1x0:'1×0',lay0x1:'0×1',lay2x0:'2×0',lay0x2:'0×2'}[method]||method;
  const odd = a.hasOdd ? ` · Lay odd ${a.layOdd} (exposição: ${((a.layOdd-1)).toFixed(2)}× stake)` : '';
  return { name:`Lay ${layLabel} — Bolsa de Apostas${odd}`, sub:`Lucra em qualquer resultado diferente de ${layLabel}` };
}

function getEntradaSaida(method, conf) {
  if (method === 'backfav') return {
    entrar: conf>=72 ? 'Pré-jogo' : 'Pré-jogo (stake reduzida)',
    entrarSub: 'Ao vivo: se o favorito sair perdendo antes dos 20min, reavaliar odd',
    sair: 'Full time — deixar correr até o apito final',
    sairSub: 'Cash out parcial se empate aos 75min com odd favorável'
  };
  if (method === 'back2x2') return {
    entrar: conf>=72 ? 'Pré-jogo' : 'Pré-jogo (stake reduzida)',
    entrarSub: conf>=72 ? 'Ao vivo: 0×0 até 15min com mercado ainda aberto' : 'Evitar ao vivo — aguardar confirmação',
    sair: '3° gol marcado → encerrar posição',
    sairSub: 'Cash out parcial ao atingir Over 1.5 se odd de saída for favorável'
  };
  if (method === 'layzebra') return {
    entrar: 'Pré-jogo',
    entrarSub: 'Ao vivo: se o azarão abrir o placar antes dos 25min, avaliar lay ao vivo com odd maior',
    sair: 'Gol do favorito → exposição reduz / win gradual',
    sairSub: 'Fechar manual se azarão vencer por 2+ gols no 2° tempo'
  };
  if (method === 'lay1x0') return {
    entrar: 'Pré-jogo',
    entrarSub: 'Ao vivo: se 1×0 ocorrer antes dos 30min, avaliar lay ao vivo',
    sair: '2° gol da partida → exposição encerrada',
    sairSub: 'Gol do visitante = win instantâneo · 2° gol do mandante = fechar manual'
  };
  if (method === 'lay0x1') return {
    entrar: 'Pré-jogo',
    entrarSub: 'Ao vivo: se 0×1 ocorrer antes dos 30min, avaliar lay ao vivo',
    sair: '1° gol do mandante → exposição encerrada',
    sairSub: 'Qualquer gol do mandante encerra o risco automaticamente'
  };
  if (method === 'backgoleada') return {
    entrar: conf>=72 ? 'Pré-jogo' : 'Pré-jogo (stake reduzida)',
    entrarSub: 'Ao vivo: se 1×0 ou 2×0 antes dos 30min, mercado de goleada ainda aberto',
    sair: '4° gol marcado → encerrar / deixar correr',
    sairSub: 'Cash out parcial no 3° gol se odd de saída for rentável'
  };
  if (method === 'over70') return {
    entrar: 'Ao vivo — entre os 65 e 70 minutos',
    entrarSub: 'Ideal: jogo sem gol ou empate em 0×0 / 1×1 com times pressionando',
    sair: '1° gol após os 70min → encerrar posição',
    sairSub: 'Se nenhum gol até 88min, fechar manual para minimizar perda'
  };
  if (method === 'lay2x0') return {
    entrar: 'Pré-jogo',
    entrarSub: 'Ao vivo: se 2×0 ocorrer antes dos 30min, avaliar lay ao vivo',
    sair: '3° gol ou 1° gol do visitante → exposição encerrada',
    sairSub: 'Gol do visitante = win · 3° gol do mandante = fechar manual'
  };
  return {
    entrar: 'Pré-jogo',
    entrarSub: 'Ao vivo: se 0×2 ocorrer antes dos 30min, avaliar lay ao vivo',
    sair: '3° gol ou 1° gol do mandante → exposição encerrada',
    sairSub: 'Gol do mandante = win · 3° gol do visitante = fechar manual'
  };
}

function getTopCriteria(crit, ok, n) {
  return crit.filter(c => c.ok===ok).slice(0, n);
}

function toggleChecklist(id) {
  const det = document.getElementById('det-'+id);
  const btn = document.getElementById('ckbtn-'+id);
  if (!det) return;
  det.classList.toggle('open');
  btn.classList.toggle('open');
  const arr = btn.querySelector('.ec-arr');
  if (arr) arr.textContent = det.classList.contains('open') ? '↑' : '↓';
}

// ── RENDER RESULTS ────────────────────────────────────────────────────────────
// Sort helpers
const sortByConf = (list, key) => [...list].sort((a,b) => b[key].conf - a[key].conf);

const VC = {
  'ENTRADA CONFIRMADA':    {c:'#00ff88',b:'rgba(0,255,136,.5)',bg:'rgba(0,255,136,.07)',bar:'#00ff88'},
  'ENTRADA POSSÍVEL':      {c:'#f59e0b',b:'rgba(245,158,11,.45)',bg:'rgba(245,158,11,.06)',bar:'#f59e0b'},
  'EVITAR':                {c:'#fb923c',b:'rgba(251,146,60,.4)',bg:'rgba(251,146,60,.05)',bar:'#fb923c'},
  'REJEITAR':              {c:'#f43f5e',b:'rgba(244,63,94,.4)',bg:'rgba(244,63,94,.05)',bar:'#f43f5e'},
  'ESTATÍSTICA FAVORÁVEL': {c:'#00ff88',b:'rgba(0,255,136,.4)',bg:'rgba(0,255,136,.05)',bar:'#00ff88'},
  'PERFIL NEUTRO':         {c:'#f59e0b',b:'rgba(245,158,11,.35)',bg:'rgba(245,158,11,.04)',bar:'#f59e0b'},
  'ESTATÍSTICA DESFAVORÁVEL':{c:'#f43f5e',b:'rgba(244,63,94,.38)',bg:'rgba(244,63,94,.04)',bar:'#f43f5e'},
  'LAY CONFIRMADO':        {c:'#9b8afb',b:'rgba(155,138,251,.52)',bg:'rgba(155,138,251,.07)',bar:'#9b8afb'},
  'LAY POSSÍVEL':          {c:'#c4b5fd',b:'rgba(196,181,253,.42)',bg:'rgba(196,181,253,.05)',bar:'#c4b5fd'},
  'EVITAR LAY':            {c:'#fb923c',b:'rgba(251,146,60,.4)',bg:'rgba(251,146,60,.05)',bar:'#fb923c'},
  'LAY REJEITADO':         {c:'#f43f5e',b:'rgba(244,63,94,.4)',bg:'rgba(244,63,94,.05)',bar:'#f43f5e'},
};
const RKC = {BAIXO:'#00ff88',MÉDIO:'#f59e0b',ALTO:'#fb923c',EXTREMO:'#f43f5e'};

const ALL_METHODS = ['backfav','back2x2','backgoleada','over70','lay1x0','lay0x1','lay2x0','lay0x2','layzebra'];
const METHOD_NAMES = {
  backfav:'Back Favorito', back2x2:'Back 2×2', backgoleada:'Back Goleada',
  over70:'Over 70min', lay1x0:'Lay 1×0', lay0x1:'Lay 0×1',
  lay2x0:'Lay 2×0', lay0x2:'Lay 0×2', layzebra:'Lay Zebra'
};
const isGood = a => isPositive(a.vd) && (a.rk === 'BAIXO' || a.rk === 'MÉDIO');

function renderResults() {
  const empty = '<div class="emp" style="grid-column:1/-1"><span class="ei">○</span><p>Nenhuma entrada recomendada</p></div>';
  const safeCard = (r, k) => { try { return cardResult(r, k); } catch(e) { return `<div style="color:var(--red);padding:10px">${e.message}</div>`; } };

  const allCards = [];   // {html, k}
  const rejected = [];   // {r, k}

  ALL_METHODS.forEach(k => {
    const sorted = sortByConf(S.results, k);
    sorted.forEach(r => {
      if (!r[k]) return;
      if (isGood(r[k])) allCards.push({html: safeCard(r, k), k});
      else rejected.push({r, k});
    });
  });

  // ── Single unified grid ──
  const allEl = document.getElementById('rl-all');
  if (allEl) {
    if (!allCards.length) {
      allEl.innerHTML = empty;
    } else {
      allEl.innerHTML = allCards
        .map(({html, k}) => `<div data-method="${k}">${html}</div>`)
        .join('');
    }
    applyFilter();
  }

  // ── Rejected tab — compact list, grouped by match ──
  const rejEl = document.getElementById('rl-rejeitados');
  if (rejEl) {
    if (!rejected.length) {
      rejEl.innerHTML = empty;
    } else {
      const byMatch = new Map();
      rejected.forEach(({r, k}) => {
        if (!byMatch.has(r.mid)) byMatch.set(r.mid, {r, methods: []});
        byMatch.get(r.mid).methods.push(k);
      });
      rejEl.innerHTML = '<div class="rej-list">' +
        [...byMatch.values()].map(({r, methods}) => {
          const d = r.d;
          const timeTxt = d.time || '—';
          const comp    = d.competition || '';
          const tags    = methods.map(k => {
            const vc = VC[(r[k]||{}).vd] || VC['PERFIL NEUTRO'];
            return `<span class="rej-tag" style="color:${vc.c};border-color:${vc.c}">${METHOD_NAMES[k]||k}</span>`;
          }).join('');
          return `<div class="rej-row">
            <div class="rej-time">${timeTxt}</div>
            <div class="rej-match">${d.homeTeam||'Mandante'}<span>×</span>${d.awayTeam||'Visitante'}</div>
            ${comp ? `<div class="rej-comp">${comp}</div>` : ''}
            <div class="rej-tags">${tags}</div>
          </div>`;
        }).join('') + '</div>';
    }
  }
}

let _cardUid = 0;

function cardResult(r, method) {
  const d   = r.d;
  const a   = r[method];
  const vc  = VC[a.vd] || VC['PERFIL NEUTRO'];
  const hN  = d.homeTeam||'Mandante', aN = d.awayTeam||'Visitante';
  const uid = ++_cardUid;
  const pos = isPositive(a.vd);

  const mercado = getMercado(method, a);
  const timing  = getEntradaSaida(method, a.conf);

  // Time em destaque (só para métodos com time específico)
  const teamLabel = (method==='backfav'||method==='backgoleada') ? { label:'Apostar em', name:a.favN }
                  : method==='layzebra' ? { label:'Lay no azarão', name:a.zebraN }
                  : null;

  // ── Probability section (inside details) ──
  let probHtml = '';
  if (method==='backfav'||method==='backgoleada'||method==='over70') {
    const edgeColor = a.hasOdd ? (a.edge>0?'#00ff88':'#f43f5e') : '#333';
    const edgeVal   = a.hasOdd ? `${a.edge>=0?'+':''}${Math.round(a.edge*100)}%` : '—';
    const pLabel    = method==='backfav'?'P(Vitória)':method==='backgoleada'?'P(4+ gols)':'P(Gol 70min)';
    probHtml = `<div class="ec-prob">
      <div class="ec-p"><div class="ec-plbl">${pLabel}</div><div class="ec-pval" style="color:#00e676">${Math.round(a.modelP*100)}%</div></div>
      <div class="ec-p"><div class="ec-plbl">P Implícita</div><div class="ec-pval" style="color:var(--text2)">${a.hasOdd?Math.round(a.impliedP*100)+'%':'—'}</div></div>
      <div class="ec-p"><div class="ec-plbl">Edge</div><div class="ec-pval" style="color:${edgeColor}">${edgeVal}</div></div>
    </div>`;
  } else if (method==='back2x2') {
    const edgeColor = a.hasOdd ? (a.edge>0?'#00ff88':'#f43f5e') : '#333';
    const edgeVal   = a.hasOdd ? `${a.edge>=0?'+':''}${Math.round(a.edge*100)}%` : '—';
    probHtml = `<div class="ec-prob">
      <div class="ec-p"><div class="ec-plbl">P(Over 2.5)</div><div class="ec-pval" style="color:#00e676">${Math.round(a.modelPOver*100)}%</div></div>
      <div class="ec-p"><div class="ec-plbl">P(Ambas ≥2)</div><div class="ec-pval" style="color:#00e676">${Math.round(a.modelPBoth2*100)}%</div></div>
      <div class="ec-p"><div class="ec-plbl">Edge</div><div class="ec-pval" style="color:${edgeColor}">${edgeVal}</div></div>
    </div>`;
  } else {
    const label     = method==='lay1x0'?'1×0':method==='lay0x1'?'0×1':method==='lay2x0'?'2×0':method==='lay0x2'?'0×2':`Zebra (${a.zebraN||'Azarão'})`;
    const edgeColor = a.hasOdd ? (a.edge>0?'#9b8afb':'#f43f5e') : '#333';
    const edgeVal   = a.hasOdd ? `${a.edge>=0?'+':''}${Math.round(a.edge*100)}%` : '—';
    probHtml = `<div class="ec-prob">
      <div class="ec-p"><div class="ec-plbl">P(${label}) Modelo</div><div class="ec-pval" style="color:#a78bfa">${Math.round(a.modelP*100)}%</div></div>
      <div class="ec-p"><div class="ec-plbl">P(${label}) Implícita</div><div class="ec-pval" style="color:var(--text2)">${a.hasOdd?Math.round(a.impliedP*100)+'%':'—'}</div></div>
      <div class="ec-p"><div class="ec-plbl">Edge Lay</div><div class="ec-pval" style="color:${edgeColor}">${edgeVal}</div></div>
    </div>`;
  }

  // ── Motivos ──
  const topOk   = getTopCriteria(a.crit, true,  6);
  const topFail = getTopCriteria(a.crit, false, 5);

  const motivesHtml = pos ? `<div class="ec-motives">
    ${topOk.map(c=>`<div class="ec-m">
      <div class="ec-m-ico" style="color:#00e676">✓</div>
      <div class="ec-m-text"><span class="ec-m-key">${c.label}</span><span class="ec-m-val">— ${c.info}</span></div>
    </div>`).join('')}
  </div>` : `<div class="ec-fail-items">
    ${topFail.map(c=>`<div class="ec-fi">
      <span style="flex-shrink:0;color:#ff4757">✗</span>
      <span><span style="color:var(--text2)">${c.label}</span><span class="ec-fi-v">— ${c.info}</span></span>
    </div>`).join('')}
  </div>`;

  const warnsHtml = a.warns.length ? `<div class="ec-sec" style="background:rgba(251,146,60,.04);border-left:2px solid rgba(251,146,60,.4)">
    <div class="ec-lbl" style="color:#fb923c">⚠ Alertas</div>
    ${a.warns.map(w=>`<div style="font-size:11px;color:rgba(251,146,60,.65);padding:2px 0">— ${w}</div>`).join('')}
  </div>` : '';

  const checklistHtml = `<div class="cl">
    <div class="ch"><span>Checklist</span><span style="color:var(--text2)">${a.score.toFixed(1)} / ${a.maxS.toFixed(1)} pts</span></div>
    ${a.crit.map(c=>`<div class="cr">
      <div class="ci2" style="color:${c.ok?'#00ff88':'#333'}">${c.ok?'✓':'✗'}</div>
      <div class="cb2"><div class="cl2 ${c.ok?'ok':''}">${c.label}</div><div class="cd">${c.info}</div></div>
      <div class="cw">×${c.w}</div>
    </div>`).join('')}
  </div>`;

  // ── Signal badge classification ──
  const isLayMethod = ['lay1x0','lay0x1','lay2x0','lay0x2','layzebra'].includes(method);
  const sigClass    = pos ? (isLayMethod ? 'lay' : 'back') : 'warn';
  const sigArrow    = pos ? (isLayMethod ? '↓' : '↑') : '—';
  const sigLabels   = {
    backfav:'Back Favorito', back2x2:'Back 2×2', backgoleada:'Back Goleada',
    over70:'Over 70min', lay1x0:'Lay 1×0', lay0x1:'Lay 0×1',
    lay2x0:'Lay 2×0', lay0x2:'Lay 0×2', layzebra:'Lay Zebra'
  };
  const sigLabel = sigLabels[method] || method;
  // banner class
  const bannerClass = (() => {
    const vd2 = a.vd || '';
    if (vd2.includes('CONFIRMADA')) return isLayMethod ? 'sig-lay-ok' : 'sig-back-ok';
    if (vd2.includes('POSSÍVEL'))   return isLayMethod ? 'sig-lay-pos' : 'sig-back-pos';
    if (vd2.includes('EVITAR'))     return 'sig-warn';
    return 'sig-bad';
  })();

  // ── Min/Max recommended odd ──
  const oddLabel = isLayMethod ? 'Odd Máx.' : 'Odd Mín.';
  const recOdd   = a.modelP > 0 ? (1 / a.modelP).toFixed(2) : null;
  const oddColor = isLayMethod ? '#9b8afb' : '#00ff88';
  const riskCol  = RKC[a.rk] || '#333';

  // ── Position row ──
  const hPos = d.home.position > 0 ? `${d.home.position}º` : null;
  const aPos = d.away.position > 0 ? `${d.away.position}º` : null;

  // ── Form letters with color ──
  function formHtml(str) {
    if (!str) return '';
    return str.slice(0,5).split('').map(c => {
      const col = (c==='W'||c==='V') ? '#00ff88' : c==='D' ? '#f59e0b' : '#f43f5e';
      return `<span style="color:${col};font-size:10px;font-weight:700;margin-right:2px">${c==='V'?'W':c}</span>`;
    }).join('');
  }

  // ── Stats pills ──
  function statPill(label, val, col) {
    return `<span style="font-size:9px;color:${col||'var(--text2)'};background:var(--card3);border:1px solid var(--border2);border-radius:3px;padding:2px 6px;white-space:nowrap">${label}: <b>${val}</b></span>`;
  }
  const hAvg = d.home.avgScored > 0 ? d.home.avgScored.toFixed(1) : '—';
  const aAvg = d.away.avgScored > 0 ? d.away.avgScored.toFixed(1) : '—';
  const hWin = d.home.winPct > 0 ? Math.round(d.home.winPct*100)+'%' : '—';
  const aWin = d.away.winPct > 0 ? Math.round(d.away.winPct*100)+'%' : '—';

  // ── Team spotlight for methods with a target team ──
  const spotlightHtml = teamLabel ? `
  <div style="padding:4px 14px 0;display:flex;align-items:center;gap:6px">
    <span style="font-size:8px;color:var(--text2);letter-spacing:.2em;text-transform:uppercase;font-weight:700">${teamLabel.label}:</span>
    <span style="font-size:13px;font-weight:800;color:${vc.c}">${teamLabel.name}</span>
  </div>` : '';

  // ── Competition / time meta ──
  const timePart = d.time ? `⏰ ${d.time}` : '';
  const compPart = [d.competition, d.round?'R'+d.round:null].filter(Boolean).join(' · ');
  const datePart = d.date || '';

  return `<div class="ec" id="ec-${uid}" style="border-color:${pos?vc.b:'var(--border)'}">

  <!-- TOP META ROW -->
  <div class="ec-top">
    <div class="ec-top-left" style="flex-wrap:wrap;gap:6px">
      ${timePart ? `<span style="color:var(--green);font-family:'Courier New',monospace;font-weight:800">${timePart}</span><span style="color:var(--border2)">·</span>` : ''}
      <span style="color:var(--blue);font-weight:600">🏆 ${compPart||'—'}</span>
      ${datePart ? `<span style="color:var(--border2)">·</span><span style="color:var(--text2);font-weight:500">${datePart}</span>` : ''}
    </div>
    <button class="ec-dl-btn" id="dl-${uid}" onclick="downloadCard(${uid})">⬇ Salvar</button>
  </div>

  <!-- MATCH TITLE -->
  <div class="ec-title">${hN}<span class="ec-vs">×</span>${aN}</div>

  ${spotlightHtml}

  <!-- HOME ROW -->
  <div class="ec-pos-row" style="padding-bottom:4px">
    <span style="font-size:12px">🏠</span>
    ${hPos ? `<span style="font-weight:800;color:var(--yellow)">${hPos} em casa</span><span class="ec-pos-dash"></span>` : ''}
    <span style="font-size:9px;letter-spacing:.06em;font-family:'Courier New',monospace"><span style="color:var(--green);font-weight:700">${hWin}</span><span style="color:var(--text2)"> vit · </span><span style="color:var(--cyan);font-weight:700">${hAvg} gl/j</span></span>
    <span style="margin-left:auto">${formHtml(d.homeForm)}</span>
  </div>
  <!-- AWAY ROW -->
  <div class="ec-pos-row" style="padding-top:0;padding-bottom:10px">
    <span style="font-size:12px">✈</span>
    ${aPos ? `<span style="font-weight:800;color:var(--yellow)">${aPos} fora</span><span class="ec-pos-dash"></span>` : ''}
    <span style="font-size:9px;letter-spacing:.06em;font-family:'Courier New',monospace"><span style="color:var(--green);font-weight:700">${aWin}</span><span style="color:var(--text2)"> vit · </span><span style="color:var(--cyan);font-weight:700">${aAvg} gl/j</span></span>
    <span style="margin-left:auto">${formHtml(d.awayForm)}</span>
  </div>

  <!-- ★ SIGNAL BANNER ★ -->
  <div class="ec-signal-banner ${bannerClass}">
    <div class="ec-signal-name">
      <span class="ec-signal-arrow">${sigArrow}</span>
      <span>${a.vd}</span>
    </div>
    <div class="ec-signal-conf" style="font-family:'Courier New',monospace">${sigLabel}</div>
  </div>

  <!-- ★ METRICS BAR — RISCO / CONFIANÇA / ODD ★ -->
  <div class="ec-metrics">
    <div class="ec-metric">
      <div class="ec-metric-lbl">Risco</div>
      <div class="ec-metric-val" style="color:${riskCol};font-size:${a.rk.length>5?'14px':'22px'}">${a.rk}</div>
    </div>
    <div class="ec-metric">
      <div class="ec-metric-lbl">Confiança</div>
      <div class="ec-metric-val" style="color:${vc.c}">${a.conf}<span style="font-size:11px;opacity:.5">%</span></div>
    </div>
    <div class="ec-metric">
      <div class="ec-metric-lbl">${oddLabel}</div>
      <div class="ec-metric-val sm" style="color:${recOdd&&pos?oddColor:'var(--text3)'}">${recOdd&&pos?recOdd:'—'}</div>
    </div>
  </div>

  <!-- VISIBLE WARNS -->
  ${a.warns&&a.warns.length ? `<div class="ec-warns-bar">
    ${a.warns.map(w=>`<div class="ec-warn-item"><span class="ec-warn-ico">⚠</span><span>${w}</span></div>`).join('')}
  </div>` : ''}

  <!-- DIVIDER -->
  <div class="ec-div"></div>

  <!-- MARKET ROW -->
  <div class="ec-mkt-row" style="padding-bottom:8px">
    <div class="ec-mkt-left">
      <div class="ec-mkt-lbl">Mercado Principal</div>
      <div class="ec-mkt-name">${pos ? mercado.name : (a.rec||'Sem entrada recomendada')}</div>
      ${pos ? `<div class="ec-mkt-sub">Entrar: ${timing.entrar} · Sair: ${timing.sair}</div>` : ''}
    </div>
  </div>

  <!-- VER DETALHES TOGGLE -->
  <button class="ec-toggle" id="ckbtn-${uid}" onclick="toggleChecklist(${uid})">
    Ver detalhes <span class="ec-arr">↓</span>
  </button>

  <!-- DETAILS (hidden by default) -->
  <div class="ec-details" id="det-${uid}">
    <div style="background:var(--card3)">
    ${probHtml}
    ${pos ? `
    <div class="ec-sec">
      <div class="ec-lbl">Motivos da entrada</div>
      ${motivesHtml}
    </div>
    <div class="ec-timing">
      <div class="ec-t">
        <div class="ec-tlbl">Entrar</div>
        <div class="ec-tval">${timing.entrar}<span>${timing.entrarSub}</span></div>
      </div>
      <div class="ec-t" style="border-left:1px solid var(--border)">
        <div class="ec-tlbl">Sair</div>
        <div class="ec-tval">${timing.sair}<span>${timing.sairSub}</span></div>
      </div>
    </div>
    ` : `
    <div class="ec-sec">
      <div class="ec-lbl">Por que evitar</div>
      ${motivesHtml}
    </div>
    `}
    ${checklistHtml}
    </div>
  </div>

</div>`;
}

// ── ACTIONS ───────────────────────────────────────────────────────────────────
function setOpt(id, k, v) { const m=S.matches.find(m=>m.id===id); if(m) m.opts[k]=v; }

function rm(id) { S.matches=S.matches.filter(m=>m.id!==id); renderList(); refreshBadges(); refreshABar(); }

function runAnalyze(id) {
  const m = S.matches.find(m=>m.id===id);
  if (!m||!m.data) return;
  const opts = {
    oddBack2x2:parseFloat(m.opts.oddBack2x2)||0,
    oddLay1x0: parseFloat(m.opts.oddLay1x0)||0,
    oddLay0x1: parseFloat(m.opts.oddLay0x1)||0,
    oddLay2x0: parseFloat(m.opts.oddLay2x0)||0,
    oddLay0x2: parseFloat(m.opts.oddLay0x2)||0,
  };
  const rec = { mid:id, d:m.data,
    backfav:     analyzeBackFavorito(m.data, opts),
    back2x2:     analyzeBack2x2(m.data, opts),
    backgoleada: analyzeBackGoleada(m.data, opts),
    over70:      analyzeOver70(m.data, opts),
    lay1x0:      analyzeLay1x0(m.data, opts),
    lay0x1:      analyzeLay0x1(m.data, opts),
    lay2x0:      analyzeLay2x0(m.data, opts),
    lay0x2:      analyzeLay0x2(m.data, opts),
  };
  m.status = 'done';
  const ei = S.results.findIndex(r=>r.mid===id);
  if (ei>=0) S.results[ei]=rec; else S.results.unshift(rec);
  renderList(); renderResults(); refreshBadges(); showSection('resultados');
}

function allAnalyze() {
  S.matches.filter(m=>m.status==='ready'||m.status==='done').forEach(m=>{
    const opts = {
      oddBack2x2:parseFloat(m.opts.oddBack2x2)||0,
      oddLay1x0: parseFloat(m.opts.oddLay1x0)||0,
      oddLay0x1: parseFloat(m.opts.oddLay0x1)||0,
    };
    const rec = { mid:m.id, d:m.data,
      backfav:     analyzeBackFavorito(m.data, opts),
      back2x2:     analyzeBack2x2(m.data, opts),
      backgoleada: analyzeBackGoleada(m.data, opts),
      over70:      analyzeOver70(m.data, opts),
      lay1x0:      analyzeLay1x0(m.data, opts),
      lay0x1:      analyzeLay0x1(m.data, opts),
      lay2x0:      analyzeLay2x0(m.data, opts),
      lay0x2:      analyzeLay0x2(m.data, opts),
      layzebra:    analyzeLayZebra(m.data, opts),
    };
    m.status = 'done';
    const ei = S.results.findIndex(r=>r.mid===m.id);
    if (ei>=0) S.results[ei]=rec; else S.results.unshift(rec);
  });
  renderList(); renderResults(); refreshBadges(); showSection('resultados');
}

function refreshBadges() {
  document.getElementById('bn-fila').textContent = S.matches.length;
  let rejCount = 0;
  ALL_METHODS.forEach(k => {
    let good = 0;
    S.results.forEach(r => { if (r[k]) { isGood(r[k]) ? good++ : rejCount++; } });
    const el = document.getElementById('bn-'+k);
    if (el) el.textContent = good;
  });
  const rejEl = document.getElementById('bn-rejeitados');
  if (rejEl) rejEl.textContent = rejCount;
}

function refreshABar() {
  const bar = document.getElementById('abar');
  const n = S.matches.filter(m=>m.status==='ready'||m.status==='done').length;
  if (n>=2) { bar.style.display='flex'; document.getElementById('abar-txt').textContent=`${n} partidas prontas`; }
  else bar.style.display='none';
}
// ── DOWNLOAD CARD AS IMAGE ─────────────────────────────────────────────────────
function loadHtml2Canvas() {
  return new Promise((res, rej) => {
    if (window.html2canvas) return res(window.html2canvas);
    const s = document.createElement('script');
    s.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js';
    s.onload  = () => res(window.html2canvas);
    s.onerror = () => rej(new Error('html2canvas failed to load'));
    document.head.appendChild(s);
  });
}

async function downloadCard(uid) {
  const card = document.getElementById('ec-' + uid);
  const btn  = document.getElementById('dl-' + uid);
  if (!card || !btn) return;

  btn.classList.add('loading');
  btn.textContent = '…';

  try {
    const h2c = await loadHtml2Canvas();
    const canvas = await h2c(card, {
      backgroundColor: '#0f0f0f',
      scale: 2,
      useCORS: true,
      logging: false,
    });
    const link = document.createElement('a');
    const label = card.querySelector('.ec-title')
      ? card.querySelector('.ec-title').textContent.replace(/\s+/g,'_').replace(/[^\w_-]/g,'').slice(0,40)
      : 'card';
    link.download = `sinal_${label}_${uid}.png`;
    link.href = canvas.toDataURL('image/png');
    link.click();
  } catch(e) {
    alert('Erro ao gerar imagem: ' + e.message);
  } finally {
    btn.classList.remove('loading');
    btn.innerHTML = '⬇ Salvar';
  }
}
</script>
</body>
</html>
