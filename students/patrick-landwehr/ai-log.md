<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Minnesota corn: what to plan for</title>

//ME:
  WHERE THE DATA IS STORED
The Minnesota rows were copied out of
     the CSV and pasted straight into this HTML file, in the two lines marked
     "DATA STARTS HERE" in the script at the bottom. The original CSV stays saved in the drive.

<style>
:root{--bg:#f1f4ee;--panel:#fbfcf9;--ink:#1c2a1f;--mute:#5d6b5f;--line:#d6ddd1;--bar:#2f6b45;--hi:#d9a521;--bar2:#a9c4b0}
@media (prefers-color-scheme:dark){:root{--bg:#141b15;--panel:#1b241d;--ink:#e6ede5;--mute:#9aaa9d;--line:#2e3b30;--bar:#5fae7a;--hi:#e8b93a;--bar2:#3b5443}}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:16px/1.5 system-ui,-apple-system,"Segoe UI",sans-serif}
main{max-width:1060px;margin:0 auto;padding:32px 20px 48px}
h1{font:600 clamp(1.7rem,4vw,2.5rem)/1.15 Georgia,"Times New Roman",serif;margin:0 0 8px;max-width:22ch}
.lede{color:var(--mute);max-width:64ch;margin:0 0 24px}
.answer{background:var(--panel);border:1px solid var(--line);border-left:6px solid var(--hi);padding:18px 22px;margin-bottom:20px}
.answer .big{font:600 clamp(2rem,6vw,3.4rem)/1.1 Georgia,serif}
.answer p{margin:6px 0 0;color:var(--mute);max-width:70ch}
.grid{display:grid;grid-template-columns:280px 1fr;gap:20px}
@media(max-width:780px){.grid{grid-template-columns:1fr}}
.panel{background:var(--panel);border:1px solid var(--line);padding:18px}
label{display:block;font-weight:600;margin:14px 0 4px}
label:first-child{margin-top:0}
select,input[type=range]{width:100%}
select{padding:8px;font:inherit;background:var(--bg);color:var(--ink);border:1px solid var(--line)}
.val{font-weight:400;color:var(--mute)}
.note{font-size:.85rem;color:var(--mute);margin-top:14px}
.stats{display:flex;gap:28px;flex-wrap:wrap;margin-bottom:12px}
.stats b{display:block;font:600 1.5rem Georgia,serif}
.stats span{color:var(--mute);font-size:.85rem}
.row{display:grid;grid-template-columns:120px 1fr 86px;gap:8px;align-items:center;padding:3px 0;font-size:.88rem;border:0;background:none;color:inherit;width:100%;text-align:left;cursor:pointer;font-family:inherit}
.row:hover .name,.row:focus-visible .name{text-decoration:underline}
.row:focus-visible{outline:2px solid var(--hi)}
.name{white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.track{background:transparent;height:16px}
.fill{height:100%;background:var(--bar);transition:width .35s}
.row.sel .fill{background:var(--hi)}
.row.dim .fill{background:var(--bar2)}
.num{text-align:right;font-variant-numeric:tabular-nums}
@media(prefers-reduced-motion:reduce){.fill{transition:none}}
</style>
</head>
<body>
<main>
  <h1>How much Minnesota corn should we plan for?</h1>
  <p class="lede">The attached file holds one year (2024) of <em>acres planted</em>, not bushels harvested. So the harvest figure below is a planning estimate: planted acres × the two assumptions you set on the left.</p>

  <section class="answer" aria-live="polite">
    <div class="big" id="headline"></div>
    <p id="headsub"></p>
  </section>

  <div class="grid">
    <aside class="panel">
      <label for="district">Ag district</label>
      <select id="district"></select>

      <label for="county">County</label>
      <select id="county"></select>

      <label for="metric">Chart shows</label>
      <select id="metric">
        <option value="acres">Acres planted (from data)</option>
        <option value="bu">Estimated bushels harvested</option>
      </select>

      <label for="yield">Yield assumption <span class="val" id="yv"></span></label>
      <input type="range" id="yield" min="120" max="230" step="1" value="180">

      <label for="share">Planted acres harvested for grain <span class="val" id="sv"></span></label>
      <input type="range" id="share" min="80" max="100" step="1" value="92">

      <p class="note">Year and crop can't be filtered: the file has only 2024 and only corn. The two sliders are placeholders, not data.</p>
    </aside>

    <section class="panel">
      <div class="stats">
        <div><b id="s1"></b><span id="l1"></span></div>
        <div><b id="s2"></b><span id="l2"></span></div>
        <div><b id="s3"></b><span id="l3"></span></div>
      </div>
      <div id="chart" role="list"></div>
      <p class="note" id="foot"></p>
    </section>
  </div>
</main>

<script>
  
// ME: Data begins here showing the loaded data, rows and values loaded by the AI
  
// Minnesota county rows from Corn_Data.csv: [county, ag district, acres planted in 2024]
const COUNTIES = [["Other Counties", "Other counties (combined)", 1744100], ["Benton", "Central", 55900], ["Carver", "Central", 51300], ["Kandiyohi", "Central", 156500], ["Mcleod", "Central", 112000], ["Morrison", "Central", 103500], ["Renville", "Central", 255000], ["Scott", "Central", 31500], ["Sherburne", "Central", 25200], ["Sibley", "Central", 151000], ["Stearns", "Central", 225500], ["Todd", "Central", 84300], ["Wadena", "Central", 23300], ["Aitkin", "East Central", 3000], ["Anoka", "East Central", 4100], ["Chisago", "East Central", 23900], ["Crow Wing", "East Central", 9600], ["Hennepin", "East Central", 10400], ["Isanti", "East Central", 31200], ["Mille Lacs", "East Central", 20100], ["Pine", "East Central", 16900], ["Washington", "East Central", 16000], ["Becker", "Northwest", 76400], ["Clay", "Northwest", 154500], ["Clearwater", "Northwest", 7900], ["Mahnomen", "Northwest", 50200], ["Marshall", "Northwest", 54400], ["Norman", "Northwest", 109500], ["Polk", "Northwest", 125000], ["Red Lake", "Northwest", 29900], ["Blue Earth", "South Central", 176500], ["Brown", "South Central", 155500], ["Freeborn", "South Central", 184500], ["Le Sueur", "South Central", 81500], ["Nicollet", "South Central", 113000], ["Rice", "South Central", 87300], ["Steele", "South Central", 105500], ["Waseca", "South Central", 112000], ["Watonwan", "South Central", 125500], ["Dakota", "Southeast", 85800], ["Dodge", "Southeast", 119500], ["Fillmore", "Southeast", 174500], ["Goodhue", "Southeast", 157500], ["Houston", "Southeast", 58000], ["Mower", "Southeast", 203500], ["Olmsted", "Southeast", 111000], ["Wabasha", "Southeast", 98100], ["Winona", "Southeast", 81900], ["Cottonwood", "Southwest", 164500], ["Jackson", "Southwest", 187000], ["Lincoln", "Southwest", 114500], ["Nobles", "Southwest", 205000], ["Pipestone", "Southwest", 115500], ["Redwood", "Southwest", 235500], ["Big Stone", "West Central", 92300], ["Grant", "West Central", 123000], ["Lac Qui Parle", "West Central", 173000], ["Otter Tail", "West Central", 203500], ["Pope", "West Central", 115000], ["Stevens", "West Central", 142000], ["Swift", "West Central", 200000], ["Wilkin", "West Central", 136000]];
// Minnesota state-level acres planted from the same file. "YEAR" is the final figure;
// the others are earlier USDA forecasts made during 2024.
const STATE = {"YEAR": 8200000, "YEAR - AUG FORECAST": 8200000, "YEAR - JUN ACREAGE": 8100000, "YEAR - MAR ACREAGE": 7900000, "YEAR - OCT FORECAST": 8200000, "YEAR - SEP FORECAST": 8200000};
// ===== DATA ENDS HERE =====

const $ = id => document.getElementById(id);
const fmt = n => Math.round(n).toLocaleString('en-US');
const short = n => n >= 1e9 ? (n/1e9).toFixed(2)+' billion' : n >= 1e6 ? (n/1e6).toFixed(2)+' million' : fmt(n);

// Fill the dropdowns once
const districts = [...new Set(COUNTIES.map(c => c[1]))].sort();
$('district').innerHTML = '<option value="">All of Minnesota</option>' + districts.map(d => `<option>${d}</option>`).join('');
let picked = '';          // county the user clicked or chose

function refill() {
  // County list only shows counties inside the chosen district
  const d = $('district').value;
  const list = COUNTIES.filter(c => !d || c[1] === d).map(c => c[0]).sort();
  $('county').innerHTML = '<option value="">All counties</option>' + list.map(n => `<option>${n}</option>`).join('');
  $('county').value = list.includes(picked) ? picked : '';
  picked = $('county').value;
}

function render() {
  const d = $('district').value, metric = $('metric').value;
  const yld = +$('yield').value, share = +$('share').value / 100;
  $('yv').textContent = yld + ' bu/acre';
  $('sv').textContent = Math.round(share * 100) + '%';
  const toBu = a => a * share * yld;

  const rows = COUNTIES.filter(c => !d || c[1] === d).sort((a, b) => b[2] - a[2]);
  const scopeAcres = rows.reduce((s, c) => s + c[2], 0);
  const scopeName = d ? d + ' district' : 'Minnesota';

  // Headline: the planning answer for the chosen area
  $('headline').textContent = short(toBu(scopeAcres)) + ' bushels';
  $('headsub').textContent = `Estimated harvest for ${scopeName}: ${fmt(scopeAcres)} acres planted in 2024 × ${Math.round(share*100)}% harvested × ${yld} bu/acre. One year of data, so this is a single-year estimate, not a multi-year average.`;

  // Summary numbers
  const p = rows.find(c => c[0] === picked);
  $('s1').textContent = fmt(p ? p[2] : scopeAcres);
  $('l1').textContent = 'acres planted, ' + (p ? p[0] : scopeName);
  $('s2').textContent = short(toBu(p ? p[2] : scopeAcres));
  $('l2').textContent = 'estimated bushels';
  $('s3').textContent = fmt(STATE.YEAR);
  $('l3').textContent = 'MN state total acres (final, 2024)';
// ME: Data is changed here, forming a barchard to help split and summarize the data
  // Bar chart (plain HTML, no outside libraries)
  const val = c => metric === 'acres' ? c[2] : toBu(c[2]);
  const max = Math.max(...rows.map(val));
  $('chart').innerHTML = rows.map(c => {
    const cls = c[0] === picked ? 'sel' : (picked ? 'dim' : '');
    return `<button class="row ${cls}" role="listitem" data-c="${c[0]}" title="${c[0]}, ${c[1]}">
      <span class="name">${c[0]}</span>
      <span class="track"><div class="fill" style="width:${val(c)/max*100}%"></div></span>
      <span class="num">${metric === 'acres' ? fmt(val(c)) : short(val(c))}</span></button>`;
  }).join('');

  const checkSum = COUNTIES.reduce((s, c) => s + c[2], 0);
  $('foot').textContent = `${rows.length} rows shown. "Other counties (combined)" is a group of counties the survey does not list individually. Click a bar to highlight it. All county rows add up to ${fmt(checkSum)} acres vs. the state total of ${fmt(STATE.YEAR)}.`;
}

$('district').onchange = () => { refill(); render(); };
$('county').onchange = () => { picked = $('county').value; render(); };
['metric', 'yield', 'share'].forEach(id => $(id).oninput = render);
$('chart').onclick = e => {
  const b = e.target.closest('.row'); if (!b) return;
  picked = picked === b.dataset.c ? '' : b.dataset.c;
  $('county').value = picked; render();
};
refill(); render();
</script>
</body>
</html>

// ME: AI ERROR The first version of the HTML header comment said the data sat in "the two lines marked DATA STARTS HERE". It is actually a block of two constants between a START and an END marker.
