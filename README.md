# myWD
Signal is an AI-powered Decision Intelligence platform that monitors business metrics in real time, detects anomalies, correlates data across multiple systems, identifies root causes, and recommends actions with confidence scores. It reduces decision-making time from hours to minutes, enabling faster smarter, and more reliable operational responses
https://relaxed-cuchufli-a21da7.netlify.app/
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Signal — Decision Intelligence</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#0E1420;
    --slate:#151E2E;
    --slate-2:#1C2740;
    --line: rgba(232,230,222,0.09);
    --paper:#E8E6DE;
    --paper-dim: rgba(232,230,222,0.56);
    --paper-dimmer: rgba(232,230,222,0.34);
    --amber:#F2B33D;
    --teal:#3FA796;
    --red:#E06C5C;
    --display: 'Fraunces', serif;
    --body: 'Inter', sans-serif;
    --mono: 'JetBrains Mono', monospace;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:var(--ink);
    color:var(--paper);
    font-family:var(--body);
    min-height:100vh;
    -webkit-font-smoothing:antialiased;
  }
  .wrap{max-width:1180px;margin:0 auto;padding:36px 28px 80px;}

  /* header */
  header{display:flex;align-items:flex-end;justify-content:space-between;margin-bottom:30px;flex-wrap:wrap;gap:16px;}
  .brand{display:flex;align-items:center;gap:12px;}
  .brand-mark{width:34px;height:34px;border-radius:8px;background:linear-gradient(155deg,var(--amber),var(--red));display:flex;align-items:center;justify-content:center;flex-shrink:0;}
  .brand-mark svg{width:18px;height:18px;}
  .brand h1{font-family:var(--display);font-size:24px;font-weight:500;margin:0;letter-spacing:0.2px;}
  .brand span{display:block;font-size:11px;letter-spacing:1.5px;text-transform:uppercase;color:var(--paper-dimmer);margin-top:2px;}
  .clock{font-family:var(--mono);font-size:12.5px;color:var(--paper-dim);text-align:right;line-height:1.5;}
  .clock b{color:var(--amber);font-weight:600;}

  /* metrics row */
  .metrics{display:grid;grid-template-columns:repeat(5,1fr);gap:12px;margin-bottom:28px;}
  .metric{background:var(--slate);border:1px solid var(--line);border-radius:10px;padding:16px 16px 14px;position:relative;overflow:hidden;}
  .metric .m-label{font-size:11.5px;color:var(--paper-dim);text-transform:uppercase;letter-spacing:1px;margin-bottom:8px;}
  .metric .m-value{font-family:var(--mono);font-size:22px;font-weight:600;}
  .metric .m-delta{font-size:12px;margin-top:4px;font-family:var(--mono);}
  .up{color:var(--teal);} .down{color:var(--red);} .flat{color:var(--paper-dimmer);}
  .metric svg{position:absolute;bottom:8px;right:10px;opacity:0.55;width:70px;height:26px;}
  .m-alert{border-color:rgba(224,108,92,0.5);box-shadow:0 0 0 1px rgba(224,108,92,0.12) inset;}
  .m-watch{border-color:rgba(242,179,61,0.4);}
  .status-dot{width:6px;height:6px;border-radius:50%;display:inline-block;margin-right:6px;}
  .dot-red{background:var(--red);box-shadow:0 0 6px var(--red);}
  .dot-amber{background:var(--amber);box-shadow:0 0 6px var(--amber);}
  .dot-teal{background:var(--teal);}

  /* main grid */
  .grid{display:grid;grid-template-columns:1.05fr 1.5fr;gap:18px;align-items:start;}
  .panel{background:var(--slate);border:1px solid var(--line);border-radius:12px;overflow:hidden;}
  .panel-head{padding:16px 18px 12px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;}
  .panel-head h2{font-family:var(--display);font-size:16.5px;font-weight:500;margin:0;}
  .panel-head .count{font-family:var(--mono);font-size:11px;color:var(--paper-dimmer);}

  /* anomaly feed */
  .feed{padding:6px;}
  .a-item{padding:13px 12px;border-radius:8px;cursor:pointer;transition:background 0.15s;border:1px solid transparent;margin-bottom:2px;}
  .a-item:hover{background:var(--slate-2);}
  .a-item.active{background:var(--slate-2);border-color:rgba(242,179,61,0.35);}
  .a-top{display:flex;align-items:center;justify-content:between;gap:8px;}
  .a-title{font-size:13.5px;font-weight:600;color:var(--paper);flex:1;}
  .a-meta{font-family:var(--mono);font-size:10.5px;color:var(--paper-dimmer);margin-top:5px;display:flex;gap:10px;}
  .sev-tag{font-size:9.5px;text-transform:uppercase;letter-spacing:0.6px;padding:2px 6px;border-radius:4px;font-weight:600;}
  .sev-alert{background:rgba(224,108,92,0.16);color:var(--red);}
  .sev-watch{background:rgba(242,179,61,0.16);color:var(--amber);}

  /* accelerator panel */
  .accel-body{padding:20px;}
  .accel-empty{padding:60px 30px;text-align:center;color:var(--paper-dimmer);font-size:13.5px;}
  .accel-empty svg{width:34px;height:34px;margin-bottom:12px;opacity:0.5;}

  .race-title{font-size:12px;text-transform:uppercase;letter-spacing:1px;color:var(--paper-dim);margin-bottom:14px;}
  .track{margin-bottom:16px;}
  .track-label{display:flex;justify-content:space-between;font-family:var(--mono);font-size:11.5px;margin-bottom:6px;}
  .track-label .name{color:var(--paper-dim);text-transform:uppercase;letter-spacing:0.5px;font-size:10.5px;}
  .track-bar{height:26px;background:var(--ink);border-radius:6px;border:1px solid var(--line);overflow:hidden;position:relative;display:flex;}
  .seg{height:100%;flex-shrink:0;position:relative;border-right:1px solid rgba(14,20,32,0.5);width:0%;transition:width 1.1s cubic-bezier(.2,.7,.2,1);}
  .seg.manual{background:linear-gradient(90deg,#3a3120,#5a4a24);}
  .seg.accel{background:linear-gradient(90deg,#1d4c46,#2f8579);}
  .track-time{font-family:var(--mono);font-weight:600;font-size:13px;}
  .time-manual{color:var(--amber);}
  .time-accel{color:var(--teal);}

  .saved-banner{margin-top:6px;padding:14px 16px;border-radius:9px;background:rgba(63,167,150,0.1);border:1px solid rgba(63,167,150,0.3);display:flex;align-items:center;justify-content:space-between;}
  .saved-banner .label{font-size:12px;color:var(--paper-dim);}
  .saved-banner .value{font-family:var(--mono);font-size:20px;font-weight:600;color:var(--teal);}

  .divider{height:1px;background:var(--line);margin:20px 0;}

  .rc-grid{display:grid;grid-template-columns:1fr auto;gap:14px;align-items:start;}
  .rc-label{font-size:11px;text-transform:uppercase;letter-spacing:1px;color:var(--paper-dim);margin-bottom:6px;}
  .rc-text{font-size:14px;line-height:1.5;}
  .confidence{text-align:center;}
  .conf-ring{width:64px;height:64px;position:relative;}
  .conf-num{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-family:var(--mono);font-weight:600;font-size:14px;}

  .steps{list-style:none;margin:14px 0 0;padding:0;display:flex;flex-direction:column;gap:8px;}
  .steps li{display:flex;align-items:center;gap:9px;font-size:12.5px;color:var(--paper-dim);opacity:0;transform:translateX(-6px);transition:all 0.4s ease;}
  .steps li.show{opacity:1;transform:translateX(0);}
  .steps li .chk{width:14px;height:14px;border-radius:50%;background:var(--teal);flex-shrink:0;display:flex;align-items:center;justify-content:center;}
  .steps li .chk svg{width:9px;height:9px;}

  .action-row{display:flex;gap:10px;margin-top:18px;}
  .btn{font-family:var(--body);font-weight:600;font-size:13px;padding:10px 18px;border-radius:7px;border:none;cursor:pointer;transition:transform 0.1s, opacity 0.15s;}
  .btn:active{transform:scale(0.97);}
  .btn-primary{background:var(--amber);color:#1a1305;}
  .btn-primary:hover{opacity:0.92;}
  .btn-ghost{background:transparent;border:1px solid var(--line);color:var(--paper-dim);}
  .btn-ghost:hover{background:var(--slate-2);}
  .toast{margin-top:12px;font-family:var(--mono);font-size:12px;color:var(--teal);opacity:0;transition:opacity 0.3s;}
  .toast.show{opacity:1;}

  @media (max-width:920px){
    .metrics{grid-template-columns:repeat(2,1fr);}
    .grid{grid-template-columns:1fr;}
  }
  @media (prefers-reduced-motion: reduce){
    .seg, .steps li{transition:none;}
  }
</style>
</head>
<body>
<div class="wrap">

  <header>
    <div class="brand">
      <div class="brand-mark">
        <svg viewBox="0 0 24 24" fill="none"><path d="M3 17L9 9L13 13L21 4" stroke="#0E1420" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </div>
      <div>
        <h1>Signal</h1>
        <span>Decision intelligence for operations</span>
      </div>
    </div>
    <div class="clock">Monitoring 214 data sources · live<br><b id="liveclock">—</b></div>
  </header>

  <div class="metrics" id="metrics"></div>

  <div class="grid">
    <div class="panel">
      <div class="panel-head">
        <h2>Detected anomalies</h2>
        <span class="count" id="anomaly-count"></span>
      </div>
      <div class="feed" id="feed"></div>
    </div>

    <div class="panel">
      <div class="panel-head">
        <h2>Decision accelerator</h2>
        <span class="count">time-to-decision, compared</span>
      </div>
      <div class="accel-body" id="accel-body">
        <div class="accel-empty">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2v4M12 18v4M4.9 4.9l2.8 2.8M16.3 16.3l2.8 2.8M2 12h4M18 12h4M4.9 19.1l2.8-2.8M16.3 7.7l2.8-2.8"/></svg><br>
          Select an anomaly on the left to see how Signal compresses the path from "something's off" to a confident decision.
        </div>
      </div>
    </div>
  </div>

</div>

<script>
/* ---------- clock ---------- */
function tick(){
  const d = new Date();
  document.getElementById('liveclock').textContent = d.toLocaleTimeString([], {hour:'2-digit',minute:'2-digit',second:'2-digit'});
}
tick(); setInterval(tick, 1000);

/* ---------- sparkline helper ---------- */
function spark(points, color){
  const w=70,h=26;
  const max=Math.max(...points), min=Math.min(...points);
  const norm = points.map((p,i)=>{
    const x = (i/(points.length-1))*w;
    const y = h - ((p-min)/((max-min)||1))*h;
    return `${x.toFixed(1)},${y.toFixed(1)}`;
  }).join(' ');
  return `<svg viewBox="0 0 ${w} ${h}"><polyline points="${norm}" fill="none" stroke="${color}" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/></svg>`;
}

/* ---------- metrics data ---------- */
const metrics = [
  {label:'Revenue today', value:'$284,920', delta:'+4.1%', cls:'up', trend:[210,225,218,240,232,255,268,280,285], status:''},
  {label:'Checkout conversion', value:'2.6%', delta:'−18.0%', cls:'down', trend:[3.5,3.4,3.3,3.2,3.0,2.9,2.7,2.6,2.6], status:'m-alert'},
  {label:'Monthly churn', value:'3.1%', delta:'+0.8pt', cls:'down', trend:[2.1,2.2,2.3,2.4,2.5,2.7,2.9,3.0,3.1], status:'m-watch'},
  {label:'Support tickets', value:'142', delta:'+37%', cls:'down', trend:[80,85,88,90,95,110,120,130,142], status:'m-watch'},
  {label:'Inventory health', value:'96%', delta:'−2pt', cls:'flat', trend:[99,98,98,97,97,96,96,96,96], status:''},
];
const metricsEl = document.getElementById('metrics');
metrics.forEach(m=>{
  const color = m.cls==='up' ? '#3FA796' : m.cls==='down' ? '#E06C5C' : 'rgba(232,230,222,0.5)';
  const dotClass = m.status==='m-alert' ? 'dot-red' : m.status==='m-watch' ? 'dot-amber' : 'dot-teal';
  metricsEl.insertAdjacentHTML('beforeend', `
    <div class="metric ${m.status}">
      <div class="m-label"><span class="status-dot ${dotClass}"></span>${m.label}</div>
      <div class="m-value">${m.value}</div>
      <div class="m-delta ${m.cls}">${m.delta} vs baseline</div>
      ${spark(m.trend, color)}
    </div>`);
});

/* ---------- anomaly data ---------- */
const anomalies = [
  {
    id:1, sev:'alert', title:'APAC checkout conversion down 18%', detected:'Detected 04:12 today', region:'Payments · APAC',
    rootCause:'A routing change on the Razorpay gateway is adding ~2.1s of latency to card auth calls for APAC traffic, causing a spike in checkout timeouts.',
    confidence:91,
    action:'Fail over APAC card traffic to the backup gateway and page the payments on-call.',
    manual:[
      {label:'Pull funnel data from analytics, gateway logs, and infra dashboards separately', time:45},
      {label:'Cross-reference timestamps across three systems by hand', time:90},
      {label:'Loop in payments and regional infra teams for context', time:120},
      {label:'Form and test a hypothesis with engineering', time:70},
      {label:'Agree on a fix and get sign-off', time:35},
    ],
    accel:[
      {label:'Auto-correlates funnel, gateway, and infra logs in real time', time:1},
      {label:'Isolates the anomaly to APAC card-auth latency', time:1},
      {label:'Ranks 3 root-cause candidates by confidence', time:1},
      {label:'Surfaces the fix and drafts the on-call page', time:1},
    ]
  },
  {
    id:2, sev:'watch', title:'Enterprise-tier churn risk rising', detected:'Detected 07:40 today', region:'Customer success · Enterprise',
    rootCause:'12 enterprise accounts show a drop in weekly active seats after a recent SSO migration, a known precursor to churn in this segment.',
    confidence:78,
    action:'Trigger a CSM outreach playbook for the 12 flagged accounts this week.',
    manual:[
      {label:'Export seat-usage and login data account by account', time:60},
      {label:'Manually flag accounts below the usage threshold', time:80},
      {label:'Cross-check against support tickets and NPS scores', time:75},
      {label:'Prioritize which accounts CSMs should call first', time:40},
    ],
    accel:[
      {label:'Scores every account against churn precursors continuously', time:1},
      {label:'Flags the 12 accounts crossing the risk threshold', time:1},
      {label:'Ranks accounts by revenue-at-risk', time:1},
      {label:'Drafts the outreach list for CS', time:1},
    ]
  },
  {
    id:3, sev:'alert', title:'SKU-2291 stockout risk in 6 hours', detected:'Detected 08:55 today', region:'Inventory · West DC',
    rootCause:'Demand for SKU-2291 is running 3.4x forecast after a creator mention, and West DC has no scheduled replenishment for 2 days.',
    confidence:96,
    action:'Reroute 400 units from East DC and pause the promo email for this SKU.',
    manual:[
      {label:'Pull sell-through and inventory data by warehouse', time:35},
      {label:'Check demand forecast vs. actuals manually', time:50},
      {label:'Call other DCs to check available stock', time:45},
      {label:'Decide on a reroute plan', time:25},
    ],
    accel:[
      {label:'Detects the 3.4x demand deviation automatically', time:1},
      {label:'Finds available stock across all DCs instantly', time:1},
      {label:'Proposes a reroute plan that avoids the stockout', time:1},
    ]
  },
  {
    id:4, sev:'watch', title:'EU refund rate up 3.2x this week', detected:'Detected yesterday, 21:05', region:'Finance · EU',
    rootCause:'A size-chart error on 4 apparel listings, live since Tuesday, is driving most of the refund spike in that category.',
    confidence:84,
    action:'Correct the size charts and flag the 4 listings for a quality review.',
    manual:[
      {label:'Pull refund reasons from support tickets manually', time:55},
      {label:'Group refunds by product category and SKU', time:65},
      {label:'Spot-check listings for recent changes', time:60},
      {label:'Confirm the size-chart error with merchandising', time:30},
    ],
    accel:[
      {label:'Clusters refund reasons and finds the category spike', time:1},
      {label:'Matches the spike to 4 listings changed this week', time:1},
      {label:'Flags the size-chart edit as the likely cause', time:1},
    ]
  },
];

const feedEl = document.getElementById('feed');
document.getElementById('anomaly-count').textContent = anomalies.length + ' active';
anomalies.forEach(a=>{
  feedEl.insertAdjacentHTML('beforeend', `
    <div class="a-item" data-id="${a.id}" id="item-${a.id}">
      <div class="a-top">
        <div class="a-title">${a.title}</div>
      </div>
      <div class="a-meta">
        <span class="sev-tag ${a.sev==='alert'?'sev-alert':'sev-watch'}">${a.sev}</span>
        <span>${a.detected}</span>
        <span>${a.region}</span>
      </div>
    </div>`);
});

/* ---------- accelerator logic ---------- */
const accelBody = document.getElementById('accel-body');
let activeId = null;

function fmtTime(mins){
  if(mins < 1) return '<1 min';
  if(mins < 60) return Math.round(mins) + ' min';
  const h = Math.floor(mins/60), m = Math.round(mins%60);
  return m ? `${h}h ${m}m` : `${h}h`;
}

function renderAccelerator(a){
  const manualTotal = a.manual.reduce((s,x)=>s+x.time,0);
  const accelTotal = a.accel.reduce((s,x)=>s+x.time,0);
  const saved = manualTotal - accelTotal;
  const maxTotal = Math.max(manualTotal, accelTotal);

  accelBody.innerHTML = `
    <div class="race-title">${a.title}</div>

    <div class="track">
      <div class="track-label"><span class="name">Without Signal</span><span class="track-time time-manual" id="manual-time">0 min</span></div>
      <div class="track-bar" id="manual-bar">
        ${a.manual.map((s,i)=>`<div class="seg manual" style="width:0%" data-w="${(s.time/maxTotal*100).toFixed(2)}" title="${s.label}"></div>`).join('')}
      </div>
    </div>

    <div class="track">
      <div class="track-label"><span class="name">With Signal</span><span class="track-time time-accel" id="accel-time">0 min</span></div>
      <div class="track-bar" id="accel-bar">
        ${a.accel.map((s,i)=>`<div class="seg accel" style="width:0%" data-w="${(s.time/maxTotal*100).toFixed(2)}" title="${s.label}"></div>`).join('')}
      </div>
    </div>

    <div class="saved-banner">
      <span class="label">Time-to-decision, compressed by</span>
      <span class="value" id="saved-value">0 min</span>
    </div>

    <div class="divider"></div>

    <div class="rc-grid">
      <div>
        <div class="rc-label">Likely root cause</div>
        <div class="rc-text">${a.rootCause}</div>
      </div>
      <div class="confidence">
        <div class="rc-label">Confidence</div>
        <svg class="conf-ring" viewBox="0 0 64 64">
          <circle cx="32" cy="32" r="27" stroke="rgba(232,230,222,0.12)" stroke-width="6" fill="none"/>
          <circle cx="32" cy="32" r="27" stroke="#3FA796" stroke-width="6" fill="none"
            stroke-dasharray="${2*Math.PI*27}" stroke-dashoffset="${2*Math.PI*27*(1-a.confidence/100)}"
            stroke-linecap="round" transform="rotate(-90 32 32)"/>
        </svg>
        <div class="conf-num" style="top:-64px;position:relative;">${a.confidence}%</div>
      </div>
    </div>

    <ul class="steps" id="step-list">
      ${a.accel.map(s=>`<li><span class="chk"><svg viewBox="0 0 24 24" fill="none" stroke="#0E1420" stroke-width="3"><path d="M4 12l5 5L20 6"/></span>${s.label}</li>`).join('')}
    </ul>

    <div class="action-row">
      <button class="btn btn-primary" id="take-action">Take action: ${a.action}</button>
      <button class="btn btn-ghost" id="dismiss">Dismiss</button>
    </div>
    <div class="toast" id="toast">✓ Action queued — routed to the on-call owner.</div>
  `;

  // animate bars
  requestAnimationFrame(()=>{
    const manualSegs = document.querySelectorAll('#manual-bar .seg');
    const accelSegs = document.querySelectorAll('#accel-bar .seg');
    manualSegs.forEach((el,i)=> setTimeout(()=>{ el.style.width = el.dataset.w + '%'; }, i*120));
    accelSegs.forEach((el,i)=> setTimeout(()=>{ el.style.width = el.dataset.w + '%'; }, i*90));

    // count up numbers roughly in sync
    countUp('manual-time', manualTotal, 1300);
    countUp('accel-time', accelTotal, 700);
    setTimeout(()=> countUp('saved-value', saved, 900), 400);

    // reveal step list
    document.querySelectorAll('#step-list li').forEach((li,i)=>{
      setTimeout(()=> li.classList.add('show'), 500 + i*140);
    });
  });

  document.getElementById('take-action').addEventListener('click', ()=>{
    const t = document.getElementById('toast');
    t.classList.add('show');
  });
  document.getElementById('dismiss').addEventListener('click', ()=>{
    document.getElementById('item-'+a.id).style.opacity = '0.4';
  });
}

function countUp(id, target, duration){
  const el = document.getElementById(id);
  const start = performance.now();
  function step(now){
    const p = Math.min(1, (now-start)/duration);
    const val = target * p;
    el.textContent = fmtTime(val);
    if(p<1) requestAnimationFrame(step);
    else el.textContent = fmtTime(target);
  }
  requestAnimationFrame(step);
}

document.querySelectorAll('.a-item').forEach(el=>{
  el.addEventListener('click', ()=>{
    document.querySelectorAll('.a-item').forEach(x=>x.classList.remove('active'));
    el.classList.add('active');
    const id = parseInt(el.dataset.id);
    activeId = id;
    const a = anomalies.find(x=>x.id===id);
    renderAccelerator(a);
  });
});

// auto-open the first, most severe anomaly
document.getElementById('item-1').click();
</script>
</body>
</html>
