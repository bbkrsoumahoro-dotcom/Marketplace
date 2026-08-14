

Pressing saint joseph · HTML
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pressing Saint Joseph — Progiciel de gestion</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;500;600;700;800&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.4/chart.umd.min.js"></script>
<style>
:root{
  --bg:#F3F5FA; --surface:#FFFFFF; --surface-alt:#EEF1F8; --border:#E1E5F0;
  --ink:#131735; --ink-dim:#6B7190; --ink-faint:#9AA0BC;
  --primary:#3452D9; --primary-dark:#22348F; --primary-soft:#E9EDFC;
  --accent:#C4923F; --accent-soft:#FBF1DF;
  --success:#1C9A6C; --success-soft:#E4F7EF;
  --danger:#D5473F; --danger-soft:#FCE9E8;
  --warning:#D68C22; --warning-soft:#FCF1DD;
  --info:#3452D9; --info-soft:#E9EDFC;
  --sidebar-bg:#0E1230; --sidebar-border:#232A55; --sidebar-fg:#A6ABD1; --sidebar-fg-active:#FFFFFF;
  --radius-lg:18px; --radius-md:12px; --radius-sm:8px;
  --shadow-sm:0 1px 2px rgba(19,23,53,.06); --shadow-md:0 8px 24px -8px rgba(19,23,53,.14); --shadow-lg:0 20px 48px -12px rgba(19,23,53,.22);
  --font-display:'Sora',sans-serif; --font-body:'Inter',sans-serif; --font-mono:'JetBrains Mono',monospace;
}
html[data-theme="dark"]{
  --bg:#0A0C1C; --surface:#12152C; --surface-alt:#171B38; --border:#262B52;
  --ink:#EEF0FA; --ink-dim:#9298BE; --ink-faint:#666C93;
  --primary:#5B79EE; --primary-dark:#3452D9; --primary-soft:#1B2350;
  --accent:#E0B15F; --accent-soft:#2B2415;
  --success:#33C08D; --success-soft:#0F2B22;
  --danger:#F0685F; --danger-soft:#341715;
  --warning:#F0AE43; --warning-soft:#332208;
  --info:#5B79EE; --info-soft:#1B2350;
  --sidebar-bg:#080A1C; --sidebar-border:#1B2040;
}
*{box-sizing:border-box; margin:0; padding:0;}
body{background:var(--bg); color:var(--ink); font-family:var(--font-body); font-size:14px; line-height:1.5; -webkit-font-smoothing:antialiased;}
::selection{background:var(--primary-soft); color:var(--primary-dark);}
::-webkit-scrollbar{width:8px; height:8px;}
::-webkit-scrollbar-thumb{background:var(--border); border-radius:8px;}
::-webkit-scrollbar-track{background:transparent;}
a{color:inherit;}
button{font-family:inherit; cursor:pointer;}
input,select,textarea{font-family:inherit;}
 
/* ── Layout ── */
#app{display:flex; height:100vh; overflow:hidden;}
.sidebar{width:264px; flex-shrink:0; background:var(--sidebar-bg); display:flex; flex-direction:column; height:100vh; position:fixed; top:0; left:0; z-index:40; transform:translateX(0); transition:transform .25s ease;}
.sidebar.closed{transform:translateX(-100%);}
@media(min-width:1024px){.sidebar{position:fixed; transform:translateX(0) !important;}}
.sidebar-scrim{display:none; position:fixed; inset:0; background:rgba(5,7,20,.55); z-index:35;}
.sidebar-scrim.show{display:block;}
.main-col{flex:1; min-width:0; display:flex; flex-direction:column; margin-left:0;}
@media(min-width:1024px){.main-col{margin-left:264px;}}
.content{flex:1; overflow-y:auto; padding:22px;}
.content-inner{max-width:1440px; margin:0 auto;}
 
/* ── Sidebar ── */
.brand{display:flex; align-items:center; gap:11px; padding:20px 18px; border-bottom:1px solid var(--sidebar-border); flex-shrink:0;}
.brand-mark{width:38px; height:38px; border-radius:11px; background:linear-gradient(145deg,var(--primary),var(--primary-dark)); display:flex; align-items:center; justify-content:center; flex-shrink:0; box-shadow:0 4px 14px -4px rgba(52,82,217,.6);}
.brand-name{color:#fff; font-family:var(--font-display); font-weight:700; font-size:14.5px; line-height:1.2;}
.brand-sub{color:var(--sidebar-fg); font-size:11px; letter-spacing:.04em;}
.brand-close{margin-left:auto; color:var(--sidebar-fg); background:none; border:none;}
.nav-scroll{flex:1; overflow-y:auto; padding:16px 12px; scrollbar-width:none;}
.nav-scroll::-webkit-scrollbar{display:none;}
.nav-group{margin-bottom:18px;}
.nav-group-label{font-size:10px; font-weight:700; letter-spacing:.11em; text-transform:uppercase; color:#5B6193; padding:0 10px 7px;}
.nav-item{width:100%; display:flex; align-items:center; gap:11px; padding:9px 11px; border-radius:10px; border:none; background:none; color:var(--sidebar-fg); font-size:13.5px; font-weight:500; text-align:left; transition:all .15s;}
.nav-item:hover{background:#1A2050; color:#fff;}
.nav-item.active{background:linear-gradient(90deg,var(--primary),var(--primary-dark)); color:#fff; box-shadow:0 4px 14px -5px rgba(52,82,217,.7);}
.nav-item svg{flex-shrink:0;}
.nav-badge{margin-left:auto; background:var(--danger); color:#fff; font-family:var(--font-mono); font-size:10px; font-weight:700; padding:1px 6px; border-radius:20px;}
.sidebar-foot{padding:13px 12px; border-top:1px solid var(--sidebar-border); flex-shrink:0;}
.user-chip{display:flex; align-items:center; gap:10px; padding:8px 9px; border-radius:10px; cursor:pointer;}
.user-chip:hover{background:#1A2050;}
.avatar{width:32px; height:32px; border-radius:50%; background:linear-gradient(145deg,var(--accent),#a97524); display:flex; align-items:center; justify-content:center; color:#fff; font-weight:700; font-size:13px; flex-shrink:0;}
.user-chip-name{color:#fff; font-size:13px; font-weight:600;}
.user-chip-role{color:var(--sidebar-fg); font-size:11px;}
.reset-link{display:block; width:100%; text-align:left; background:none; border:none; color:#5B6193; font-size:11px; padding:9px 9px 0; }
.reset-link:hover{color:var(--danger);}
 
/* ── Header ── */
.topbar{height:60px; background:var(--surface); border-bottom:1px solid var(--border); display:flex; align-items:center; gap:14px; padding:0 18px; position:sticky; top:0; z-index:20; flex-shrink:0;}
.burger{display:flex; background:none; border:none; color:var(--ink-dim);}
@media(min-width:1024px){.burger{display:none;}}
.module-title{font-family:var(--font-display); font-weight:700; font-size:15px; display:none;}
@media(min-width:640px){.module-title{display:block;}}
.search-wrap{position:relative; margin-left:auto; flex:1; max-width:300px; display:none;}
@media(min-width:768px){.search-wrap{display:block;}}
.search-wrap svg{position:absolute; left:11px; top:50%; transform:translateY(-50%); color:var(--ink-faint);}
.search-input{width:100%; padding:8px 12px 8px 34px; font-size:13px; border-radius:10px; border:1px solid var(--border); background:var(--surface-alt); color:var(--ink); outline:none;}
.search-input:focus{border-color:var(--primary); background:var(--surface); box-shadow:0 0 0 3px var(--primary-soft);}
.topbar-actions{display:flex; align-items:center; gap:6px; margin-left:auto;}
@media(min-width:768px){.topbar-actions{margin-left:0;}}
.clock-chip{display:none; align-items:center; gap:6px; background:var(--surface-alt); padding:6px 11px; border-radius:9px; font-family:var(--font-mono); font-size:12px; color:var(--ink-dim);}
@media(min-width:640px){.clock-chip{display:flex;}}
.icon-btn{position:relative; display:flex; align-items:center; justify-content:center; width:36px; height:36px; border-radius:10px; border:none; background:none; color:var(--ink-dim); transition:all .15s;}
.icon-btn:hover{background:var(--surface-alt); color:var(--ink);}
.icon-dot{position:absolute; top:7px; right:7px; width:7px; height:7px; border-radius:50%; background:var(--danger); border:2px solid var(--surface);}
 
/* ── Typography / sections ── */
.page-head{display:flex; align-items:flex-start; justify-content:space-between; gap:16px; margin-bottom:20px; flex-wrap:wrap;}
.page-title{font-family:var(--font-display); font-weight:700; font-size:21px; letter-spacing:-.01em;}
.page-sub{color:var(--ink-dim); font-size:13px; margin-top:3px;}
.page-actions{display:flex; gap:8px; flex-wrap:wrap;}
.rail{height:3px; border-radius:3px; background:repeating-linear-gradient(90deg,var(--primary) 0 10px, transparent 10px 16px); opacity:.55; margin:2px 0 22px;}
 
/* ── Buttons ── */
.btn{display:inline-flex; align-items:center; gap:7px; font-size:13px; font-weight:600; border-radius:10px; padding:9px 15px; border:1px solid transparent; transition:all .15s; white-space:nowrap;}
.btn-sm{padding:6.5px 11px; font-size:12.5px;}
.btn-primary{background:var(--primary); color:#fff; box-shadow:0 4px 12px -4px rgba(52,82,217,.5);}
.btn-primary:hover{background:var(--primary-dark);}
.btn-secondary{background:var(--surface-alt); color:var(--ink); border-color:var(--border);}
.btn-secondary:hover{background:var(--border);}
.btn-ghost{background:none; color:var(--ink-dim);}
.btn-ghost:hover{background:var(--surface-alt); color:var(--ink);}
.btn-danger{background:var(--danger-soft); color:var(--danger);}
.btn-danger:hover{opacity:.8;}
.btn:disabled{opacity:.5; cursor:not-allowed;}
 
/* ── Cards / grid ── */
.grid-kpi{display:grid; grid-template-columns:repeat(2,1fr); gap:14px; margin-bottom:22px;}
@media(min-width:900px){.grid-kpi{grid-template-columns:repeat(4,1fr);}}
.kpi-card{background:var(--surface); border:1px solid var(--border); border-radius:var(--radius-lg); padding:17px; display:flex; flex-direction:column; gap:11px; box-shadow:var(--shadow-sm); transition:box-shadow .2s, transform .2s;}
.kpi-card:hover{box-shadow:var(--shadow-md); transform:translateY(-1px);}
.kpi-top{display:flex; align-items:flex-start; justify-content:space-between;}
.kpi-icon{width:38px; height:38px; border-radius:11px; display:flex; align-items:center; justify-content:center;}
.kpi-trend{display:flex; align-items:center; gap:3px; font-family:var(--font-mono); font-size:11px; font-weight:600;}
.kpi-label{font-size:10.5px; color:var(--ink-dim); text-transform:uppercase; letter-spacing:.08em; font-weight:600;}
.kpi-value{font-family:var(--font-display); font-size:23px; font-weight:700; margin-top:3px;}
.kpi-sub{font-size:11.5px; color:var(--ink-faint); margin-top:2px;}
 
.panel{background:var(--surface); border:1px solid var(--border); border-radius:var(--radius-lg); padding:19px; box-shadow:var(--shadow-sm);}
.panel + .panel{margin-top:18px;}
.panel-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:15px; gap:10px;}
.panel-title{font-family:var(--font-display); font-weight:700; font-size:14.5px;}
.panel-sub{font-size:11.5px; color:var(--ink-dim); margin-top:2px;}
 
.banner{display:flex; align-items:center; gap:11px; padding:12px 15px; border-radius:13px; font-size:13px; border:1px solid;}
.banner-danger{background:var(--danger-soft); border-color:color-mix(in srgb, var(--danger) 30%, transparent); color:var(--danger);}
.banner-warning{background:var(--warning-soft); border-color:color-mix(in srgb, var(--warning) 30%, transparent); color:var(--warning);}
.banner-info{background:var(--info-soft); border-color:color-mix(in srgb, var(--info) 30%, transparent); color:var(--primary-dark);}
html[data-theme="dark"] .banner-info{color:#C4D0FF;}
 
/* ── Filters row ── */
.filters-row{display:flex; gap:10px; margin-bottom:16px; flex-wrap:wrap;}
.filter-search{position:relative; flex:1; min-width:200px; max-width:340px;}
.filter-search svg{position:absolute; left:11px; top:50%; transform:translateY(-50%); color:var(--ink-faint);}
.filter-search input{width:100%; padding:8.5px 12px 8.5px 34px; border-radius:10px; border:1px solid var(--border); background:var(--surface); color:var(--ink); font-size:13px; outline:none;}
.filter-search input:focus{border-color:var(--primary); box-shadow:0 0 0 3px var(--primary-soft);}
select.filter-select{padding:8.5px 30px 8.5px 12px; border-radius:10px; border:1px solid var(--border); background:var(--surface); color:var(--ink); font-size:13px; outline:none; appearance:none; background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%236B7190' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat:no-repeat; background-position:right 12px center;}
 
/* ── Table ── */
.table-wrap{border:1px solid var(--border); border-radius:var(--radius-lg); overflow:hidden; background:var(--surface);}
.table-scroll{overflow-x:auto;}
table{width:100%; border-collapse:collapse; font-size:13px;}
thead tr{background:var(--surface-alt);}
th{text-align:left; padding:11px 14px; font-size:10.5px; font-weight:700; text-transform:uppercase; letter-spacing:.06em; color:var(--ink-dim); white-space:nowrap; border-bottom:1px solid var(--border);}
tbody tr{border-bottom:1px solid var(--border); transition:background .12s;}
tbody tr:last-child{border-bottom:none;}
tbody tr:hover{background:var(--surface-alt);}
td{padding:11px 14px; white-space:nowrap; color:var(--ink);}
.td-mono{font-family:var(--font-mono); font-size:11.5px; color:var(--ink-dim);}
.td-strong{font-weight:600;}
.row-actions{display:flex; gap:3px;}
.row-actions button{width:28px; height:28px; display:flex; align-items:center; justify-content:center; border-radius:8px; border:none; background:none; color:var(--ink-faint);}
.row-actions button:hover{background:var(--surface-alt); color:var(--primary);}
.row-actions button.danger:hover{color:var(--danger);}
.empty-row td{text-align:center; padding:40px; color:var(--ink-faint);}
 
/* Badge */
.badge{display:inline-flex; align-items:center; gap:4px; padding:3px 9px; border-radius:7px; font-size:11px; font-weight:600; font-family:var(--font-mono); white-space:nowrap;}
.avatar-sm{width:26px; height:26px; border-radius:50%; background:var(--primary-soft); color:var(--primary); display:flex; align-items:center; justify-content:center; font-size:11px; font-weight:700; flex-shrink:0;}
.name-cell{display:flex; align-items:center; gap:8px;}
.ticket-id{font-family:var(--font-mono); font-size:11px; color:var(--ink-dim); border:1px dashed var(--border); padding:2px 7px; border-radius:6px; background:var(--surface-alt);}
 
/* ── Modal ── */
.modal-scrim{position:fixed; inset:0; background:rgba(8,10,25,.55); backdrop-filter:blur(2px); z-index:100; display:flex; align-items:center; justify-content:center; padding:16px;}
.modal-box{background:var(--surface); border-radius:20px; width:100%; max-width:560px; max-height:88vh; overflow-y:auto; box-shadow:var(--shadow-lg); border:1px solid var(--border);}
.modal-head{display:flex; align-items:center; justify-content:space-between; padding:19px 22px; border-bottom:1px solid var(--border); position:sticky; top:0; background:var(--surface); z-index:2;}
.modal-title{font-family:var(--font-display); font-weight:700; font-size:15.5px;}
.modal-close{background:none; border:none; color:var(--ink-dim); width:30px; height:30px; border-radius:9px; display:flex; align-items:center; justify-content:center;}
.modal-close:hover{background:var(--surface-alt); color:var(--ink);}
.modal-body{padding:22px;}
.form-grid{display:grid; grid-template-columns:1fr 1fr; gap:14px;}
.form-field{display:flex; flex-direction:column; gap:6px;}
.form-field.full{grid-column:1/-1;}
.form-field label{font-size:12.5px; font-weight:600; color:var(--ink);}
.form-field input, .form-field select, .form-field textarea{padding:9px 11px; border-radius:9px; border:1px solid var(--border); background:var(--surface-alt); color:var(--ink); font-size:13px; outline:none; width:100%;}
.form-field input:focus, .form-field select:focus, .form-field textarea:focus{border-color:var(--primary); background:var(--surface); box-shadow:0 0 0 3px var(--primary-soft);}
.form-field textarea{resize:vertical; min-height:70px;}
.checkbox-row{display:flex; align-items:center; gap:9px; padding-top:6px;}
.checkbox-row input{width:16px; height:16px;}
.form-foot{display:flex; justify-content:flex-end; gap:10px; margin-top:20px; padding-top:16px; border-top:1px solid var(--border);}
.confirm-text{font-size:13.5px; color:var(--ink-dim); line-height:1.6;}
 
/* ── Toast ── */
#toast-stack{position:fixed; bottom:20px; right:20px; z-index:200; display:flex; flex-direction:column; gap:8px; align-items:flex-end;}
.toast{display:flex; align-items:center; gap:9px; background:var(--ink); color:#fff; padding:11px 16px; border-radius:11px; font-size:13px; font-weight:500; box-shadow:var(--shadow-lg); animation:toastIn .25s ease; max-width:320px;}
html[data-theme="dark"] .toast{background:#1E2450;}
@keyframes toastIn{from{opacity:0; transform:translateY(8px);} to{opacity:1; transform:translateY(0);}}
.toast.success svg{color:#33C08D;}
.toast.danger svg{color:#F0685F;}
 
/* ── Pipeline (signature element) ── */
.pipeline-strip{display:flex; align-items:center; gap:2px; overflow-x:auto; padding-bottom:6px;}
.pipe-step{display:flex; flex-direction:column; align-items:center; gap:3px; min-width:84px; padding:10px 8px; border-radius:12px; border:1px solid transparent; flex-shrink:0;}
.pipe-step.active{background:var(--primary-soft); border-color:color-mix(in srgb, var(--primary) 25%, transparent);}
.pipe-num{font-family:var(--font-display); font-size:17px; font-weight:700; color:var(--ink-faint);}
.pipe-step.active .pipe-num{color:var(--primary);}
.pipe-label{font-size:9.5px; text-align:center; line-height:1.2; color:var(--ink-dim);}
.pipe-connector{color:var(--ink-faint); flex-shrink:0;}
 
/* Machine / camera cards */
.card-grid{display:grid; grid-template-columns:1fr; gap:14px;}
@media(min-width:680px){.card-grid{grid-template-columns:1fr 1fr;}}
@media(min-width:1100px){.card-grid{grid-template-columns:1fr 1fr 1fr;}}
.tile{background:var(--surface); border:1px solid var(--border); border-radius:var(--radius-lg); padding:17px; display:flex; flex-direction:column; gap:12px; box-shadow:var(--shadow-sm);}
.tile.alert{border-color:color-mix(in srgb, var(--danger) 35%, var(--border));}
.progress-track{height:6px; background:var(--surface-alt); border-radius:6px; overflow:hidden;}
.progress-fill{height:100%; border-radius:6px; transition:width .3s;}
.cam-preview{aspect-ratio:16/9; border-radius:11px; background:linear-gradient(160deg,#1B2040,#0A0C1C); display:flex; align-items:center; justify-content:center; position:relative; overflow:hidden;}
 
.report-tile{cursor:default;}
.chip{display:inline-flex; align-items:center; padding:2px 8px; border-radius:6px; font-size:10.5px; background:var(--surface-alt); color:var(--ink-dim); font-weight:600;}
 
.audit-row{display:flex; align-items:center; gap:11px; padding:10px 12px; border-radius:11px; background:var(--surface-alt);}
.alert-row{display:flex; align-items:flex-start; gap:11px; padding:11px 13px; border-radius:12px; border:1px solid;}
.sev-dot{width:8px; height:8px; border-radius:50%; margin-top:5px; flex-shrink:0;}
 
.loading-screen{position:fixed; inset:0; background:var(--bg); display:flex; flex-direction:column; align-items:center; justify-content:center; gap:14px; z-index:999;}
.spinner{width:34px; height:34px; border-radius:50%; border:3px solid var(--border); border-top-color:var(--primary); animation:spin .8s linear infinite;}
@keyframes spin{to{transform:rotate(360deg);}}
 
.select-inline{padding:5px 26px 5px 9px; border-radius:7px; border:1px solid var(--border); background:var(--surface-alt); color:var(--ink); font-size:11.5px; font-weight:600; outline:none; appearance:none; background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M1 1l4 4 4-4' stroke='%236B7190' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat:no-repeat; background-position:right 8px center;}
 
.hidden{display:none !important;}
</style>
</head>
<body>
 
<div class="loading-screen" id="loadingScreen">
  <div class="spinner"></div>
  <div style="font-family:var(--font-display);font-weight:600;font-size:13px;color:var(--ink-dim);">Chargement du progiciel…</div>
</div>
 
<div id="app" class="hidden">
  <div class="sidebar-scrim" id="scrim" onclick="closeSidebar()"></div>
  <aside class="sidebar closed" id="sidebar">
    <div class="brand">
      <div class="brand-mark">
        <svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16v4H4z"/><path d="M4 12c0 4 4 8 8 8s8-4 8-8"/><path d="M4 12h16"/></svg>
      </div>
      <div>
        <div class="brand-name">Pressing</div>
        <div class="brand-sub">Saint&nbsp;Joseph</div>
      </div>
      <button class="brand-close" onclick="closeSidebar()">
        <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M18 6L6 18M6 6l12 12"/></svg>
      </button>
    </div>
    <nav class="nav-scroll" id="navScroll"></nav>
    <div class="sidebar-foot">
      <div class="user-chip">
        <div class="avatar">J</div>
        <div>
          <div class="user-chip-name">Joseph Akua</div>
          <div class="user-chip-role">Administrateur</div>
        </div>
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="var(--sidebar-fg)" stroke-width="2" stroke-linecap="round" style="margin-left:auto"><path d="M9 21H5a2 2 0 01-2-2V5a2 2 0 012-2h4"/><path d="M16 17l5-5-5-5"/><path d="M21 12H9"/></svg>
      </div>
      <button class="reset-link" onclick="confirmReset()">Réinitialiser les données de démonstration</button>
    </div>
  </aside>
 
  <div class="main-col">
    <header class="topbar">
      <button class="burger" onclick="openSidebar()">
        <svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M3 6h18M3 12h18M3 18h18"/></svg>
      </button>
      <div class="module-title" id="moduleTitle">Tableau de Bord</div>
      <div class="search-wrap">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4-4"/></svg>
        <input class="search-input" id="globalSearch" placeholder="Rechercher un client, un reçu…" onkeydown="if(event.key==='Enter')globalSearchGo()">
      </div>
      <div class="topbar-actions">
        <div class="clock-chip">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 3"/></svg>
          <span id="clockText">--:--:--</span>
        </div>
        <button class="icon-btn" title="Alertes" onclick="go('control')">
          <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><path d="M6 8a6 6 0 0112 0c0 7 3 9 3 9H3s3-2 3-9"/><path d="M10.3 21a2 2 0 003.4 0"/></svg>
          <span class="icon-dot" id="alertDot"></span>
        </button>
        <button class="icon-btn" title="Changer le thème" onclick="toggleTheme()">
          <svg id="themeIconSun" width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.9 4.9l1.4 1.4M17.7 17.7l1.4 1.4M2 12h2M20 12h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4"/></svg>
          <svg id="themeIconMoon" width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" class="hidden"><path d="M20 14.5A8.5 8.5 0 119.5 4a7 7 0 0010.5 10.5z"/></svg>
        </button>
        <div class="avatar" style="width:32px;height:32px;font-size:12px;">J</div>
      </div>
    </header>
    <main class="content"><div class="content-inner" id="viewRoot"></div></main>
  </div>
</div>
 
<div id="modalRoot"></div>
<div id="toast-stack"></div>
 
<script>
/* ============================= ICONS ============================= */
const ic = (path,size=15)=>`<svg width="${size}" height="${size}" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">${path}</svg>`;
const I = {
 plus:s=>ic('<path d="M12 5v14M5 12h14"/>',s),
 x:s=>ic('<path d="M18 6L6 18M6 6l12 12"/>',s),
 edit:s=>ic('<path d="M12 20h9"/><path d="M16.5 3.5a2.12 2.12 0 013 3L7 19l-4 1 1-4L16.5 3.5z"/>',s),
 trash:s=>ic('<path d="M3 6h18"/><path d="M8 6V4h8v2"/><path d="M19 6l-1 14H6L5 6"/><path d="M10 11v6M14 11v6"/>',s),
 search:s=>ic('<circle cx="11" cy="11" r="7"/><path d="M21 21l-4-4"/>',s),
 filter:s=>ic('<path d="M4 5h16l-6 8v6l-4 2v-8z"/>',s),
 download:s=>ic('<path d="M12 3v12M7 10l5 5 5-5"/><path d="M5 21h14"/>',s),
 printer:s=>ic('<path d="M7 8V4h10v4"/><rect x="4" y="8" width="16" height="8" rx="1.5"/><path d="M7 16h10v5H7z"/>',s),
 eye:s=>ic('<path d="M2 12s3.5-7 10-7 10 7 10 7-3.5 7-10 7-10-7-10-7z"/><circle cx="12" cy="12" r="3"/>',s),
 check:s=>ic('<path d="M4 12l6 6L20 6"/>',s),
 checkCircle:s=>ic('<circle cx="12" cy="12" r="9"/><path d="M8.5 12.5l2.5 2.5 5-5.5"/>',s),
 alertTri:s=>ic('<path d="M12 3l10 18H2z"/><path d="M12 10v4"/><path d="M12 17.3v.1"/>',s),
 alertCirc:s=>ic('<circle cx="12" cy="12" r="9"/><path d="M12 7.5v5.5"/><path d="M12 16.3v.1"/>',s),
 clock:s=>ic('<circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 3"/>',s),
 bell:s=>ic('<path d="M6 8a6 6 0 0112 0c0 7 3 9 3 9H3s3-2 3-9"/><path d="M10.3 21a2 2 0 003.4 0"/>',s),
 menu:s=>ic('<path d="M3 6h18M3 12h18M3 18h18"/>',s),
 chevR:s=>ic('<path d="M9 6l6 6-6 6"/>',s),
 chevD:s=>ic('<path d="M6 9l6 6 6-6"/>',s),
 phone:s=>ic('<path d="M6.6 10.8a15 15 0 006.6 6.6l2.2-2.2a1.5 1.5 0 011.5-.4c1.2.4 2.5.6 3.8.6a1.5 1.5 0 011.5 1.5V20a1.5 1.5 0 01-1.5 1.5C10.9 21.5 2.5 13.1 2.5 3.5A1.5 1.5 0 014 2h3.1A1.5 1.5 0 018.6 3.5c0 1.3.2 2.6.6 3.8a1.5 1.5 0 01-.4 1.5z"/>',s),
 msg:s=>ic('<path d="M21 12a8 8 0 01-11.5 7.2L3 21l1.8-6.5A8 8 0 1121 12z"/>',s),
 wifi:s=>ic('<path d="M2 8.5a16 16 0 0120 0"/><path d="M5.5 12a11 11 0 0113 0"/><path d="M9 15.5a6 6 0 016 0"/><circle cx="12" cy="19" r="1"/>',s),
 wifiOff:s=>ic('<path d="M2 2l20 20"/><path d="M8.5 16.5a6 6 0 017 0"/><path d="M5 12.5a11 11 0 013.5-2.4"/><path d="M15.5 10a11 11 0 013.5 2.4"/><path d="M2.5 8.5a16 16 0 014-2.5"/><path d="M17.5 6a16 16 0 014 2.5"/><circle cx="12" cy="19" r="1"/>',s),
 users:s=>ic('<circle cx="8.5" cy="8" r="3.3"/><path d="M2.5 20a6 6 0 0112 0"/><path d="M15.5 6a3.3 3.3 0 010 6.4"/><path d="M14.5 14a6 6 0 017 6"/>',s),
 pkg:s=>ic('<path d="M12 3l9 5v8l-9 5-9-5V8z"/><path d="M3 8l9 5 9-5"/><path d="M12 13v8"/>',s),
 cpu:s=>ic('<rect x="6" y="6" width="12" height="12" rx="2"/><rect x="10" y="10" width="4" height="4"/><path d="M9 2v3M15 2v3M9 19v3M15 19v3M2 9h3M2 15h3M19 9h3M19 15h3"/>',s),
 userCheck:s=>ic('<circle cx="9" cy="8" r="3.3"/><path d="M3 20a6 6 0 0112 0"/><path d="M17 11l2 2 3.5-3.5"/>',s),
 dollar:s=>ic('<path d="M12 2v20"/><path d="M16.5 6.5c0-1.7-2-3-4.5-3s-4.5 1.2-4.5 3c0 4 9 2.5 9 6.5 0 1.8-2 3-4.5 3s-4.5-1.3-4.5-3"/>',s),
 trendUp:s=>ic('<path d="M3 17l6-6 4 4 8-9"/><path d="M15 6h6v6"/>',s),
 trendDown:s=>ic('<path d="M3 7l6 6 4-4 8 9"/><path d="M15 18h6v-6"/>',s),
 megaphone:s=>ic('<path d="M3 11v2a2 2 0 002 2h1l3 5V4l-3 5H5a2 2 0 00-2 2z"/><path d="M12 9l7-4v14l-7-4"/>',s),
 star:s=>ic('<path d="M12 2l2.9 6.9L22 9.2l-5.5 4.8L18 22l-6-4-6 4 1.5-8L2 9.2l7.1-.3z"/>',s),
 shield:s=>ic('<path d="M12 2l8 4v6c0 5-3.5 8.5-8 10-4.5-1.5-8-5-8-10V6z"/><path d="M8.5 12l2.5 2.5 4.5-5"/>',s),
 camera:s=>ic('<path d="M4 8h3l1.5-2h7L17 8h3a1 1 0 011 1v10a1 1 0 01-1 1H4a1 1 0 01-1-1V9a1 1 0 011-1z"/><circle cx="12" cy="14" r="3.5"/>',s),
 bar:s=>ic('<path d="M4 20V10M12 20V4M20 20v-7"/>',s),
 bell2:s=>ic('<path d="M6 8a6 6 0 0112 0c0 7 3 9 3 9H3s3-2 3-9"/>',s),
 activity:s=>ic('<path d="M2 12h4l3-9 4 18 3-9h6"/>',s),
 layers:s=>ic('<path d="M12 2l9 5-9 5-9-5z"/><path d="M3 12l9 5 9-5"/><path d="M3 17l9 5 9-5"/>',s),
 logout:s=>ic('<path d="M9 21H5a2 2 0 01-2-2V5a2 2 0 012-2h4"/><path d="M16 17l5-5-5-5"/><path d="M21 12H9"/>',s),
 more:s=>ic('<circle cx="5" cy="12" r="1.4"/><circle cx="12" cy="12" r="1.4"/><circle cx="19" cy="12" r="1.4"/>',s),
 refresh:s=>ic('<path d="M21 12a9 9 0 10-3.2 6.9"/><path d="M21 6v6h-6"/>',s),
 radio:s=>ic('<circle cx="12" cy="12" r="2.5"/><path d="M8.5 8.5a5 5 0 000 7"/><path d="M15.5 15.5a5 5 0 000-7"/><path d="M5.5 5.5a9.5 9.5 0 000 13"/><path d="M18.5 18.5a9.5 9.5 0 000-13"/>',s),
 lock:s=>ic('<rect x="5" y="11" width="14" height="9" rx="2"/><path d="M8 11V7a4 4 0 018 0v4"/>',s),
 target:s=>ic('<circle cx="12" cy="12" r="8.5"/><circle cx="12" cy="12" r="5"/><circle cx="12" cy="12" r="1.5"/>',s),
 zap:s=>ic('<path d="M13 2L4 14h6l-1 8 9-12h-6z"/>',s),
 wrench:s=>ic('<path d="M14.7 6.3a4 4 0 01-5.4 5.4L4 17l3 3 5.3-5.3a4 4 0 015.4-5.4l-3-3z"/>',s),
 thumbsDown:s=>ic('<path d="M17 14V3"/><path d="M9 21l6-6V3H6a2 2 0 00-2 2l1.5 8a2 2 0 002 2H12l-1 5 4-2z" transform="scale(1,-1) translate(0,-24)"/>',s),
 calendar:s=>ic('<rect x="3" y="5" width="18" height="16" rx="2"/><path d="M8 3v4M16 3v4M3 10h18"/>',s),
 award:s=>ic('<circle cx="12" cy="8" r="6"/><path d="M8.5 13.5L7 21l5-3 5 3-1.5-7.5"/>',s),
};
 
/* ============================= HELPERS ============================= */
const $=(sel,el=document)=>el.querySelector(sel);
const $$=(sel,el=document)=>[...el.querySelectorAll(sel)];
const fcfa=n=>Math.round(Math.abs(n||0)).toLocaleString('fr-FR')+' FCFA';
const esc=s=>String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
function uid(prefix){ DB.counters[prefix]=(DB.counters[prefix]||0)+1; return prefix+'-'+String(DB.counters[prefix]).padStart(4,'0'); }
function todayFR(){ const d=new Date(); return d.toLocaleDateString('fr-FR',{day:'2-digit',month:'2-digit',year:'numeric'}); }
function nowFR(){ const d=new Date(); return todayFR()+' '+d.toLocaleTimeString('fr-FR',{hour:'2-digit',minute:'2-digit'}); }
function addDays(n){ const d=new Date(); d.setDate(d.getDate()+n); return d.toLocaleDateString('fr-FR',{day:'2-digit',month:'2-digit',year:'numeric'}); }
 
const STATUS_COLORS = {
  "Reçu":['#64748B','#F1F5F9'], "Tri":['#8B5CF6','#F1F5F9'], "Lavage":['#3452D9','#EEF1FE'], "Séchage":['#0891B2','#E6F6FA'],
  "Repassage":['#D68C22','#FCF1DD'], "Finition":['#CA8A04','#FEF9E3'], "Contrôle qualité":['#6366F1','#EEF0FE'],
  "Emballage":['#DB2777','#FCE9F2'], "Prêt":['#1C9A6C','#E4F7EF'], "Livré":['#0D9488','#E1F5F2'],
  "En fonctionnement":['#1C9A6C','#E4F7EF'], "En panne":['#D5473F','#FCE9E8'], "Maintenance":['#D68C22','#FCF1DD'],
  "En ligne":['#1C9A6C','#E4F7EF'], "Hors ligne":['#D5473F','#FCE9E8'],
  "VIP":['#C4923F','#FBF1DF'], "Premium":['#7C3AED','#F1EBFD'], "Entreprise":['#3452D9','#EEF1FE'], "Standard":['#64748B','#F1F5F9'],
  "Active":['#1C9A6C','#E4F7EF'], "Planifiée":['#3452D9','#EEF1FE'], "Terminée":['#64748B','#F1F5F9'],
  "En cours":['#D68C22','#FCF1DD'], "Résolu":['#1C9A6C','#E4F7EF'],
  "Présent":['#1C9A6C','#E4F7EF'], "Absent":['#D5473F','#FCE9E8'], "En congé":['#3452D9','#EEF1FE'],
  "Actif":['#1C9A6C','#E4F7EF'], "Inactif":['#64748B','#F1F5F9'],
  "Payé":['#1C9A6C','#E4F7EF'], "Impayé":['#D5473F','#FCE9E8'],
  "Élevée":['#D5473F','#FCE9E8'], "Modérée":['#D68C22','#FCF1DD'], "Mineure":['#CA8A04','#FEF9E3'],
};
function badge(label,customTxt){
  const c = STATUS_COLORS[label] || ['#64748B','#F1F5F9'];
  return `<span class="badge" style="color:${c[0]};background:${c[1]}">${esc(customTxt||label)}</span>`;
}
 
let toastSeq=0;
function toast(msg,type='success'){
  const id='t'+(++toastSeq);
  const icon = type==='danger'?I.x(14):I.check(14);
  const el=document.createElement('div');
  el.className='toast '+type; el.id=id;
  el.innerHTML=icon+`<span>${esc(msg)}</span>`;
  $('#toast-stack').appendChild(el);
  setTimeout(()=>{ el.style.transition='opacity .3s'; el.style.opacity='0'; setTimeout(()=>el.remove(),300); },2600);
}
function logAudit(module,action){
  DB.auditLog.unshift({user:'Vous', action, module, time:nowFR()});
  if(DB.auditLog.length>60) DB.auditLog.length=60;
}
 
const PIPELINE = ["Reçu","Tri","Lavage","Séchage","Repassage","Finition","Contrôle qualité","Emballage","Prêt","Livré"];
 
/* ============================= SEED DATA ============================= */
function seedDB(){
  return {
    counters:{REC:847,ART:847,CLI:8,INV:8,MCH:6,EMP:6,TXN:7,CMP:4,REC_C:4,CAM:6,USR:6},
    orders:[
      {id:"REC-2024-0847",date:"14/08/2024",client:"Aminata Koné",tel:"+225 07 48 23 19",articles:5,statut:"Prêt",montant:28500,paye:true,delai:addDays(1)},
      {id:"REC-2024-0846",date:"14/08/2024",client:"Jean-Baptiste Osei",tel:"+225 05 32 11 67",articles:3,statut:"Repassage",montant:15000,paye:false,delai:addDays(2)},
      {id:"REC-2024-0845",date:"13/08/2024",client:"Fatou Diallo",tel:"+225 01 76 54 32",articles:8,statut:"Lavage",montant:42000,paye:true,delai:addDays(3)},
      {id:"REC-2024-0844",date:"13/08/2024",client:"Kwame Mensah",tel:"+225 07 22 88 45",articles:2,statut:"Livré",montant:11000,paye:true,delai:addDays(-1)},
      {id:"REC-2024-0843",date:"12/08/2024",client:"Marie-Claire Dubois",tel:"+225 05 99 44 21",articles:12,statut:"Contrôle qualité",montant:68500,paye:false,delai:addDays(2)},
      {id:"REC-2024-0842",date:"12/08/2024",client:"Abdou Traoré",tel:"+225 07 15 33 88",articles:4,statut:"Emballage",montant:22000,paye:true,delai:addDays(1)},
      {id:"REC-2024-0841",date:"11/08/2024",client:"Hôtel Ivoire Prestige",tel:"+225 27 22 55 00",articles:48,statut:"Livré",montant:245000,paye:true,delai:addDays(-2)},
      {id:"REC-2024-0840",date:"11/08/2024",client:"Dr. Kofi Asante",tel:"+225 07 88 12 34",articles:6,statut:"Prêt",montant:33000,paye:false,delai:addDays(0)},
    ],
    articles:[
      {id:"ART-847-001",recu:"REC-2024-0847",type:"Chemise",couleur:"Blanche",marque:"Arrow",taille:"42",etat:"Bon",taches:"Aucune",statut:"Prêt",client:"Aminata Koné",prix:3500},
      {id:"ART-847-002",recu:"REC-2024-0847",type:"Pantalon",couleur:"Gris",marque:"Hugo Boss",taille:"44",etat:"Tache légère",taches:"Tache graisse col",statut:"Prêt",client:"Aminata Koné",prix:5000},
      {id:"ART-847-003",recu:"REC-2024-0847",type:"Costume",couleur:"Marine",marque:"Zara",taille:"L",etat:"Bon",taches:"Aucune",statut:"Prêt",client:"Aminata Koné",prix:12000},
      {id:"ART-846-001",recu:"REC-2024-0846",type:"Chemise",couleur:"Bleue",marque:"H&M",taille:"40",etat:"Bon",taches:"Aucune",statut:"Repassage",client:"Jean-Baptiste Osei",prix:3500},
      {id:"ART-846-002",recu:"REC-2024-0846",type:"Pantalon",couleur:"Noir",marque:"Uniqlo",taille:"42",etat:"Bon",taches:"Aucune",statut:"Repassage",client:"Jean-Baptiste Osei",prix:4500},
      {id:"ART-845-001",recu:"REC-2024-0845",type:"Couverture",couleur:"Beige",marque:"—",taille:"200×220",etat:"Bon",taches:"Tache légère",statut:"Lavage",client:"Fatou Diallo",prix:8000},
      {id:"ART-845-002",recu:"REC-2024-0845",type:"Robe",couleur:"Rouge",marque:"Guess",taille:"M",etat:"Tache café",taches:"2 taches café",statut:"Lavage",client:"Fatou Diallo",prix:7500},
      {id:"ART-843-001",recu:"REC-2024-0843",type:"Costume",couleur:"Anthracite",marque:"Pierre Cardin",taille:"XL",etat:"Bon",taches:"Aucune",statut:"Contrôle qualité",client:"Marie-Claire Dubois",prix:14000},
    ],
    clients:[
      {id:"CLI-001",nom:"Aminata Koné",tel:"+225 07 48 23 19",whatsapp:true,email:"aminata.kone@email.ci",quartier:"Cocody",categorie:"VIP",commandes:24,depenses:385000,solde:0,derniere:"14/08/2024",points:320},
      {id:"CLI-002",nom:"Jean-Baptiste Osei",tel:"+225 05 32 11 67",whatsapp:true,email:"",quartier:"Plateau",categorie:"Premium",commandes:18,depenses:220000,solde:15000,derniere:"14/08/2024",points:180},
      {id:"CLI-003",nom:"Fatou Diallo",tel:"+225 01 76 54 32",whatsapp:false,email:"fdiallo@gmail.com",quartier:"Yopougon",categorie:"Standard",commandes:12,depenses:145000,solde:0,derniere:"13/08/2024",points:120},
      {id:"CLI-004",nom:"Kwame Mensah",tel:"+225 07 22 88 45",whatsapp:true,email:"",quartier:"Marcory",categorie:"Standard",commandes:8,depenses:88000,solde:0,derniere:"14/08/2024",points:80},
      {id:"CLI-005",nom:"Marie-Claire Dubois",tel:"+225 05 99 44 21",whatsapp:true,email:"mcdubois@corporate.ci",quartier:"Zone 4",categorie:"VIP",commandes:31,depenses:520000,solde:68500,derniere:"12/08/2024",points:450},
      {id:"CLI-006",nom:"Abdou Traoré",tel:"+225 07 15 33 88",whatsapp:false,email:"",quartier:"Abobo",categorie:"Standard",commandes:6,depenses:62000,solde:0,derniere:"12/08/2024",points:60},
      {id:"CLI-007",nom:"Hôtel Ivoire Prestige",tel:"+225 27 22 55 00",whatsapp:false,email:"linge@hotelivoire.ci",quartier:"Cocody",categorie:"Entreprise",commandes:52,depenses:1250000,solde:0,derniere:"13/08/2024",points:850},
      {id:"CLI-008",nom:"Dr. Kofi Asante",tel:"+225 07 88 12 34",whatsapp:true,email:"k.asante@chuabi.ci",quartier:"Riviera",categorie:"Premium",commandes:15,depenses:198000,solde:33000,derniere:"11/08/2024",points:155},
    ],
    inventory:[
      {id:"INV-001",produit:"Lessive liquide profess.",categorie:"Lavage",stock:18,min:20,unite:"L",fournisseur:"ProChem CI",prix:8500},
      {id:"INV-002",produit:"Détachant multi-usages",categorie:"Lavage",stock:45,min:15,unite:"L",fournisseur:"ProChem CI",prix:12000},
      {id:"INV-003",produit:"Cintres métal (lot 50)",categorie:"Emballage",stock:8,min:20,unite:"Lot",fournisseur:"Embal Plus",prix:3500},
      {id:"INV-004",produit:"Sacs plastique grand",categorie:"Emballage",stock:320,min:100,unite:"Pcs",fournisseur:"Embal Plus",prix:150},
      {id:"INV-005",produit:"Améliorant de blancheur",categorie:"Lavage",stock:6,min:10,unite:"Kg",fournisseur:"ProChem CI",prix:15000},
      {id:"INV-006",produit:"Papier d'emballage kraft",categorie:"Emballage",stock:12,min:5,unite:"Rouleau",fournisseur:"Embal Plus",prix:2500},
      {id:"INV-007",produit:"Adoucissant tissus",categorie:"Lavage",stock:28,min:10,unite:"L",fournisseur:"ProChem CI",prix:7500},
      {id:"INV-008",produit:"Apprêt repassage",categorie:"Repassage",stock:3,min:8,unite:"Boîte",fournisseur:"ProChem CI",prix:5500},
    ],
    machines:[
      {id:"MCH-001",nom:"Lave-linge LG 20 kg",type:"Lave-linge",etat:"En fonctionnement",cycles:4820,maintenance:addDays(19),utilisation:78},
      {id:"MCH-002",nom:"Lave-linge Samsung 15 kg",type:"Lave-linge",etat:"En fonctionnement",cycles:3210,maintenance:addDays(32),utilisation:65},
      {id:"MCH-003",nom:"Séchoir Electrolux 12 kg",type:"Séchoir",etat:"En panne",cycles:2890,maintenance:addDays(2),utilisation:0},
      {id:"MCH-004",nom:"Presse industrielle #1",type:"Presse",etat:"En fonctionnement",cycles:6100,maintenance:addDays(47),utilisation:85},
      {id:"MCH-005",nom:"Table à repasser #1",type:"Repassage",etat:"En fonctionnement",cycles:8900,maintenance:addDays(78),utilisation:92},
      {id:"MCH-006",nom:"Table à repasser #2",type:"Repassage",etat:"Maintenance",cycles:7650,maintenance:addDays(2),utilisation:0},
    ],
    staff:[
      {id:"EMP-001",nom:"Joseph Akua",fonction:"Gérant",presence:true,arrivee:"07:45",taches:0,rendement:95,conge:false},
      {id:"EMP-002",nom:"Mariam Coulibaly",fonction:"Réceptionniste",presence:true,arrivee:"08:02",taches:12,rendement:88,conge:false},
      {id:"EMP-003",nom:"Koffi Adou",fonction:"Lavage",presence:true,arrivee:"07:55",taches:18,rendement:82,conge:false},
      {id:"EMP-004",nom:"Aïcha Bamba",fonction:"Repassage",presence:true,arrivee:"08:10",taches:24,rendement:91,conge:false},
      {id:"EMP-005",nom:"Serge Konan",fonction:"Repassage",presence:false,arrivee:"—",taches:0,rendement:75,conge:true},
      {id:"EMP-006",nom:"Patricia Yao",fonction:"Finition/Emballage",presence:true,arrivee:"08:00",taches:15,rendement:87,conge:false},
    ],
    transactions:[
      {id:"TXN-001",date:"14/08/2024 09:32",type:"Encaissement",desc:"REC-2024-0847 — Aminata Koné",montant:28500,mode:"Mobile Money",agent:"Mariam C."},
      {id:"TXN-002",date:"14/08/2024 10:15",type:"Encaissement",desc:"REC-2024-0844 — Kwame Mensah",montant:11000,mode:"Espèces",agent:"Mariam C."},
      {id:"TXN-003",date:"14/08/2024 11:00",type:"Dépense",desc:"Achat lessive — ProChem CI",montant:-45000,mode:"Espèces",agent:"Joseph A."},
      {id:"TXN-004",date:"13/08/2024 14:20",type:"Encaissement",desc:"REC-2024-0845 — Fatou Diallo",montant:42000,mode:"Espèces",agent:"Mariam C."},
      {id:"TXN-005",date:"13/08/2024 16:00",type:"Dépense",desc:"Électricité — Août 2024",montant:-85000,mode:"Virement",agent:"Joseph A."},
      {id:"TXN-006",date:"12/08/2024 08:00",type:"Encaissement",desc:"Hôtel Ivoire — Lot mensuel",montant:245000,mode:"Virement",agent:"Joseph A."},
      {id:"TXN-007",date:"11/08/2024 17:45",type:"Dépense",desc:"Salaires — Juillet 2024",montant:-380000,mode:"Virement",agent:"Joseph A."},
    ],
    campaigns:[
      {id:"CMP-001",nom:"Rentrée Scolaire — Uniformes",statut:"Active",cible:"Familles",clientsN:42,debut:"01/09/2024",fin:"30/09/2024",type:"Promo -20%"},
      {id:"CMP-002",nom:"Fidélité VIP — Août",statut:"Active",cible:"VIP",clientsN:8,debut:"01/08/2024",fin:"31/08/2024",type:"Points ×2"},
      {id:"CMP-003",nom:"Réactivation clients inactifs",statut:"Planifiée",cible:"Inactifs 60j+",clientsN:23,debut:"20/08/2024",fin:"05/09/2024",type:"SMS WhatsApp"},
      {id:"CMP-004",nom:"Pack Mariage — Juin",statut:"Terminée",cible:"Tous",clientsN:15,debut:"01/06/2024",fin:"30/06/2024",type:"Bundle -15%"},
    ],
    claims:[
      {id:"REC-C001",date:"13/08/2024",client:"Fatou Diallo",type:"Tache non traitée",article:"ART-845-002 — Robe rouge",gravite:"Modérée",statut:"En cours",responsable:"Koffi A."},
      {id:"REC-C002",date:"10/08/2024",client:"Jean-Baptiste Osei",type:"Bouton manquant",article:"ART-812-001 — Chemise bleue",gravite:"Mineure",statut:"Résolu",responsable:"Mariam C."},
      {id:"REC-C003",date:"05/08/2024",client:"Hôtel Ivoire",type:"Délai non respecté",article:"Lot REC-2024-0821",gravite:"Élevée",statut:"Résolu",responsable:"Joseph A."},
      {id:"REC-C004",date:"01/08/2024",client:"Dr. Kofi Asante",type:"Article endommagé",article:"ART-801-003 — Veste noire",gravite:"Élevée",statut:"En cours",responsable:"Joseph A."},
    ],
    cameras:[
      {id:"CAM-001",nom:"Réception / Accueil",zone:"Zone clients",statut:"En ligne",resolution:"1080p",ip:"192.168.1.101"},
      {id:"CAM-002",nom:"Zone de lavage",zone:"Production",statut:"En ligne",resolution:"1080p",ip:"192.168.1.102"},
      {id:"CAM-003",nom:"Zone repassage",zone:"Production",statut:"En ligne",resolution:"1080p",ip:"192.168.1.103"},
      {id:"CAM-004",nom:"Stock / Inventaire",zone:"Arrière-boutique",statut:"Hors ligne",resolution:"720p",ip:"192.168.1.104"},
      {id:"CAM-005",nom:"Entrée principale",zone:"Sécurité",statut:"En ligne",resolution:"4K",ip:"192.168.1.105"},
      {id:"CAM-006",nom:"Parking extérieur",zone:"Extérieur",statut:"En ligne",resolution:"1080p",ip:"192.168.1.106"},
    ],
    users:[
      {nom:"Joseph Akua",role:"Administrateur",acces:"Total",lastLogin:"Aujourd'hui 07:45",actif:true},
      {nom:"Mariam Coulibaly",role:"Réceptionniste / Caissière",acces:"Commandes, Clients, Caisse",lastLogin:"Aujourd'hui 08:02",actif:true},
      {nom:"Koffi Adou",role:"Opérateur Lavage",acces:"Traçabilité (lecture + statut)",lastLogin:"Aujourd'hui 07:55",actif:true},
      {nom:"Aïcha Bamba",role:"Opérateur Repassage",acces:"Traçabilité (lecture + statut)",lastLogin:"Aujourd'hui 08:10",actif:true},
      {nom:"Serge Konan",role:"Opérateur Repassage",acces:"Traçabilité (lecture + statut)",lastLogin:"09/08/2024",actif:false},
      {nom:"Patricia Yao",role:"Finition / Emballage",acces:"Traçabilité (lecture + statut)",lastLogin:"Aujourd'hui 08:00",actif:true},
    ],
    competition:[
      {prestation:"Chemise",psj:3500,excellence:3000,quickpress:2500,central:3500},
      {prestation:"Pantalon",psj:5000,excellence:4000,quickpress:3500,central:4500},
      {prestation:"Costume (complet)",psj:12000,excellence:10000,quickpress:9000,central:12000},
      {prestation:"Robe de soirée",psj:9000,excellence:8000,quickpress:7000,central:10000},
      {prestation:"Couverture",psj:8000,excellence:7000,quickpress:6000,central:8500},
      {prestation:"Tapis (petit)",psj:6000,excellence:5500,quickpress:5000,central:6000},
      {prestation:"Uniforme (complet)",psj:7000,excellence:6000,quickpress:5500,central:7500},
      {prestation:"Rideau (par mètre)",psj:4500,excellence:4000,quickpress:3800,central:5000},
    ],
    revenueHistory:[
      {month:"Jan",ca:485000,objectif:500000},{month:"Fév",ca:520000,objectif:500000},{month:"Mar",ca:498000,objectif:520000},
      {month:"Avr",ca:575000,objectif:520000},{month:"Mai",ca:610000,objectif:550000},{month:"Jun",ca:545000,objectif:550000},
      {month:"Jul",ca:590000,objectif:570000},{month:"Aoû",ca:635000,objectif:570000},
    ],
    auditLog:[
      {user:"Mariam C.",action:"Création reçu REC-2024-0847",module:"Commandes",time:"14/08 09:28"},
      {user:"Koffi A.",action:"Statut ART-847-001 → Prêt",module:"Traçabilité",time:"14/08 09:15"},
      {user:"Mariam C.",action:"Encaissement 28 500 FCFA Mobile Money",module:"Finances",time:"14/08 09:32"},
      {user:"Joseph A.",action:"Ajout client : Dr. Kofi Asante",module:"Clients",time:"14/08 08:45"},
    ],
  };
}
 
/* ============================= STORAGE ============================= */
const STORAGE_KEY='psj-erp-database-v1';
let DB=null;
async function loadDB(){
  try{
    const r=await window.storage.get(STORAGE_KEY);
    DB = r && r.value ? JSON.parse(r.value) : seedDB();
  }catch(e){ DB = seedDB(); }
  if(!DB || !DB.orders) DB = seedDB();
}
let saveTimer=null;
function persist(){
  clearTimeout(saveTimer);
  saveTimer=setTimeout(async ()=>{
    try{ await window.storage.set(STORAGE_KEY, JSON.stringify(DB)); }
    catch(e){ console.error('Erreur de sauvegarde',e); toast("Erreur de sauvegarde des données","danger"); }
  },250);
}
async function confirmReset(){
  openConfirm("Réinitialiser les données", "Toutes vos modifications seront perdues et remplacées par les données de démonstration initiales. Cette action est irréversible.", async ()=>{
    DB = seedDB(); persist(); closeModal(); render(); toast("Données réinitialisées");
  });
}
 
/* ============================= NAV CONFIG ============================= */
const NAV = [
  {label:"Pilotage", items:[
    {id:"dashboard", label:"Tableau de Bord", icon:I.bar},
    {id:"control", label:"Centre de Contrôle", icon:I.activity},
    {id:"cameras", label:"Caméras", icon:I.camera},
  ]},
  {label:"Opérations", items:[
    {id:"orders", label:"Commandes & Reçus", icon:I.pkg},
    {id:"tracking", label:"Traçabilité", icon:I.layers},
    {id:"quality", label:"Qualité & Réclamations", icon:I.star},
  ]},
  {label:"Clients", items:[
    {id:"clients", label:"Clients", icon:I.users},
    {id:"marketing", label:"Marketing & Fidélité", icon:I.megaphone},
  ]},
  {label:"Ressources", items:[
    {id:"inventory", label:"Inventaire", icon:I.pkg},
    {id:"machines", label:"Machines", icon:I.cpu},
    {id:"hr", label:"Ressources Humaines", icon:I.userCheck},
  ]},
  {label:"Gestion", items:[
    {id:"finance", label:"Finances", icon:I.dollar},
    {id:"reports", label:"Rapports", icon:I.bar},
    {id:"competition", label:"Concurrence", icon:I.trendUp},
    {id:"security", label:"Sécurité", icon:I.shield},
  ]},
];
const MODULE_LABEL = {}; NAV.forEach(g=>g.items.forEach(i=>MODULE_LABEL[i.id]=i.label));
 
/* ============================= APP STATE ============================= */
let state = { module:'dashboard', theme:'light', search:{}, filter:{} };
 
function go(m){ state.module=m; state.search[m]=state.search[m]||''; renderView(); renderNav(); window.scrollTo(0,0); $('.content').scrollTop=0; }
function openSidebar(){ $('#sidebar').classList.remove('closed'); $('#scrim').classList.add('show'); }
function closeSidebar(){ $('#sidebar').classList.add('closed'); $('#scrim').classList.remove('show'); }
function toggleTheme(){
  state.theme = state.theme==='dark'?'light':'dark';
  document.documentElement.setAttribute('data-theme', state.theme);
  $('#themeIconSun').classList.toggle('hidden', state.theme==='dark');
  $('#themeIconMoon').classList.toggle('hidden', state.theme!=='dark');
  localStorage.setItem('psj-theme-pref', state.theme); // ok: purely a UI pref, not app data
}
function globalSearchGo(){
  const q = $('#globalSearch').value.trim();
  if(!q) return;
  state.module='clients'; state.search['clients']=q;
  go('clients');
}
 
/* ============================= RENDER: SHELL ============================= */
function renderNav(){
  $('#navScroll').innerHTML = NAV.map(g=>`
    <div class="nav-group">
      <div class="nav-group-label">${g.label}</div>
      <div>
        ${g.items.map(it=>`
          <button class="nav-item ${state.module===it.id?'active':''}" onclick="go('${it.id}')">
            ${it.icon(16)}<span>${it.label}</span>
            ${it.id==='control' ? `<span class="nav-badge">${countAlerts()}</span>` : ''}
          </button>`).join('')}
      </div>
    </div>`).join('');
  $('#moduleTitle').textContent = MODULE_LABEL[state.module] || 'Tableau de Bord';
}
 
function tick(){ $('#clockText').textContent = new Date().toLocaleTimeString('fr-FR',{hour:'2-digit',minute:'2-digit',second:'2-digit'}); }
 
/* ============================= COMPUTED / INTELLIGENCE ============================= */
function computeAlerts(){
  const alerts=[];
  DB.inventory.forEach(i=>{ if(i.stock<i.min) alerts.push({sev:i.stock<i.min*0.5?'critical':'high', msg:`${i.produit} sous le seuil minimum (${i.stock} ${i.unite} / min ${i.min} ${i.unite})`, time:'Stock'}); });
  DB.machines.forEach(m=>{ if(m.etat==='En panne') alerts.push({sev:'critical', msg:`${m.nom} en panne — intervention urgente requise`, time:'Machine'}); });
  DB.clients.forEach(c=>{ if(c.solde>0) alerts.push({sev:c.solde>50000?'high':'medium', msg:`${c.nom} : solde impayé ${fcfa(c.solde)}`, time:'Impayé'}); });
  DB.orders.forEach(o=>{ if(!o.paye && o.statut!=='Livré') alerts.push({sev:'medium', msg:`${o.id} — ${o.client} : commande non réglée`, time:'Paiement'}); });
  return alerts;
}
function countAlerts(){ return computeAlerts().length; }
 
/* ============================= MODAL SYSTEM ============================= */
function closeModal(){ $('#modalRoot').innerHTML=''; }
function openModal(title, bodyHtml){
  $('#modalRoot').innerHTML = `
    <div class="modal-scrim" onmousedown="if(event.target===this)closeModal()">
      <div class="modal-box">
        <div class="modal-head">
          <div class="modal-title">${esc(title)}</div>
          <button class="modal-close" onclick="closeModal()">${I.x(16)}</button>
        </div>
        <div class="modal-body">${bodyHtml}</div>
      </div>
    </div>`;
}
function openConfirm(title, text, onYes){
  openModal(title, `
    <p class="confirm-text">${esc(text)}</p>
    <div class="form-foot">
      <button class="btn btn-secondary" onclick="closeModal()">Annuler</button>
      <button class="btn btn-danger" id="confirmYesBtn">Confirmer</button>
    </div>`);
  $('#confirmYesBtn').onclick = onYes;
}
 
/* Generic form field renderer */
function fieldHTML(f, val){
  val = val ?? f.default ?? '';
  const req = f.required?'required':'';
  if(f.type==='select'){
    return `<select name="${f.key}" ${req}>${f.options.map(o=>`<option value="${esc(o)}" ${val===o?'selected':''}>${esc(o)}</option>`).join('')}</select>`;
  }
  if(f.type==='textarea') return `<textarea name="${f.key}" ${req} placeholder="${esc(f.placeholder||'')}">${esc(val)}</textarea>`;
  if(f.type==='checkbox') return `<input type="checkbox" name="${f.key}" ${val?'checked':''}>`;
  return `<input type="${f.type||'text'}" name="${f.key}" value="${esc(val)}" placeholder="${esc(f.placeholder||'')}" ${req} ${f.step?`step="${f.step}"`:''}>`;
}
function renderFormFields(fields, data={}){
  return fields.map(f=>{
    if(f.type==='checkbox'){
      return `<div class="form-field ${f.full?'full':''}"><div class="checkbox-row">${fieldHTML(f,data[f.key])}<label style="font-size:13px;font-weight:500;">${f.label}</label></div></div>`;
    }
    return `<div class="form-field ${f.full?'full':''}"><label>${f.label}</label>${fieldHTML(f,data[f.key])}</div>`;
  }).join('');
}
function readForm(form, fields){
  const fd = new FormData(form); const out={};
  fields.forEach(f=>{
    if(f.type==='checkbox') out[f.key] = form.querySelector(`[name="${f.key}"]`).checked;
    else if(f.type==='number') out[f.key] = parseFloat(fd.get(f.key))||0;
    else out[f.key] = (fd.get(f.key)||'').toString().trim();
  });
  return out;
}
 
/* ============================= CRUD ENGINE ============================= */
function crudAdd(list, fields, prefix, moduleLabel, moduleId, extra={}, title){
  openModal(title||`Ajouter — ${moduleLabel}`, `
    <form id="crudForm">
      <div class="form-grid">${renderFormFields(fields)}</div>
      <div class="form-foot">
        <button type="button" class="btn btn-secondary" onclick="closeModal()">Annuler</button>
        <button type="submit" class="btn btn-primary">${I.check(14)}Enregistrer</button>
      </div>
    </form>`);
  $('#crudForm').onsubmit = (e)=>{
    e.preventDefault();
    const data = readForm(e.target, fields);
    const rec = Object.assign({id:uid(prefix)}, extra, data);
    list.unshift(rec);
    logAudit(moduleLabel, `Ajout — ${rec.id}`);
    persist(); closeModal(); renderView(); renderNav();
    toast(`${moduleLabel} : enregistrement ajouté`);
  };
}
function crudEdit(list, fields, row, moduleLabel, title){
  openModal(title||`Modifier — ${row.id||''}`, `
    <form id="crudForm">
      <div class="form-grid">${renderFormFields(fields, row)}</div>
      <div class="form-foot">
        <button type="button" class="btn btn-secondary" onclick="closeModal()">Annuler</button>
        <button type="submit" class="btn btn-primary">${I.check(14)}Mettre à jour</button>
      </div>
    </form>`);
  $('#crudForm').onsubmit = (e)=>{
    e.preventDefault();
    const data = readForm(e.target, fields);
    Object.assign(row, data);
    logAudit(moduleLabel, `Modification — ${row.id||row.nom}`);
    persist(); closeModal(); renderView(); renderNav();
    toast(`${moduleLabel} : mis à jour`);
  };
}
function crudDelete(list, row, moduleLabel, labelKey){
  openConfirm('Supprimer cet enregistrement ?', `Cette action supprimera définitivement "${row[labelKey]||row.id}". Voulez-vous continuer ?`, ()=>{
    const idx=list.indexOf(row); if(idx>-1) list.splice(idx,1);
    logAudit(moduleLabel, `Suppression — ${row[labelKey]||row.id}`);
    persist(); closeModal(); renderView(); renderNav();
    toast(`${moduleLabel} : élément supprimé`,'danger');
  });
}
 
/* ============================= VIEWS ============================= */
function renderView(){
  const root = $('#viewRoot');
  const map = {
    dashboard: viewDashboard, orders: viewOrders, tracking: viewTracking, clients: viewClients,
    inventory: viewInventory, machines: viewMachines, hr: viewHR, finance: viewFinance,
    competition: viewCompetition, marketing: viewMarketing, quality: viewQuality,
    control: viewControl, cameras: viewCameras, reports: viewReports, security: viewSecurity,
  };
  root.innerHTML = (map[state.module]||viewDashboard)();
  afterRenderHook();
}
function afterRenderHook(){
  if(state.module==='dashboard') drawDashboardCharts();
}
 
function sectionHead(title, sub, actionsHtml){
  return `<div class="page-head"><div><div class="page-title">${title}</div><div class="page-sub">${sub}</div></div><div class="page-actions">${actionsHtml||''}</div></div><div class="rail"></div>`;
}
function searchBar(moduleId, placeholder, extraSelect){
  return `<div class="filters-row">
    <div class="filter-search">${I.search(14)}<input value="${esc(state.search[moduleId]||'')}" placeholder="${placeholder}" oninput="state.search['${moduleId}']=this.value; renderView();"></div>
    ${extraSelect||''}
  </div>`;
}
 
/* ---- DASHBOARD ---- */
function viewDashboard(){
  const today = todayFR();
  const caJour = DB.orders.filter(o=>o.date===today).reduce((s,o)=>s+o.montant,0);
  const encJour = DB.transactions.filter(t=>t.type==='Encaissement' && t.date.startsWith(today)).reduce((s,t)=>s+t.montant,0);
  const aRecouvrer = DB.clients.reduce((s,c)=>s+c.solde,0);
  const cmdJour = DB.orders.filter(o=>o.date===today).length;
  const enTraitement = DB.articles.filter(a=>!['Prêt','Livré'].includes(a.statut)).length;
  const prets = DB.articles.filter(a=>a.statut==='Prêt').length;
  const clientsActifs = new Set(DB.orders.filter(o=>o.date===today).map(o=>o.client)).size;
  const stocksFaibles = DB.inventory.filter(i=>i.stock<i.min).length;
  const alerts = computeAlerts();
  const critCount = alerts.filter(a=>a.sev==='critical').length;
 
  const typeCounts = {};
  DB.articles.forEach(a=>{ typeCounts[a.type]=(typeCounts[a.type]||0)+1; });
 
  return `
  ${sectionHead('Tableau de Bord', `${today} — Vue en temps réel`, `
    <button class="btn btn-secondary btn-sm" onclick="renderView();toast('Tableau actualisé')">${I.refresh(13)}Actualiser</button>
    <button class="btn btn-secondary btn-sm" onclick="window.print()">${I.printer(13)}Imprimer</button>`)}
 
  ${critCount>0?`<div class="banner banner-danger" style="margin-bottom:20px">${I.alertTri(16)}<span><b>${critCount} alerte${critCount>1?'s':''} critique${critCount>1?'s':''}</b> — ${alerts.filter(a=>a.sev==='critical').map(a=>a.msg).join(' · ')}</span><button class="btn btn-ghost btn-sm" style="margin-left:auto;color:var(--danger)" onclick="go('control')">Voir tout</button></div>`:''}
 
  <div class="grid-kpi">
    ${kpi(I.dollar(17),'CA du jour',fcfa(caJour),`Objectif : 150 000 F`,null,'var(--info)','var(--info-soft)')}
    ${kpi(I.checkCircle(17),'Encaissements',fcfa(encJour),`${DB.transactions.filter(t=>t.type==='Encaissement'&&t.date.startsWith(today)).length} paiement(s) reçu(s)`,null,'var(--success)','var(--success-soft)')}
    ${kpi(I.alertCirc(17),'À recouvrer',fcfa(aRecouvrer),`${DB.clients.filter(c=>c.solde>0).length} client(s) en attente`,null,'var(--warning)','var(--warning-soft)')}
    ${kpi(I.pkg(17),'Commandes',cmdJour,`Aujourd'hui`,null,'#7C3AED','#F1EBFD')}
    ${kpi(I.activity(17),'Articles en traitement',enTraitement,'En cours de production',null,'var(--info)','var(--info-soft)')}
    ${kpi(I.checkCircle(17),'Articles prêts',prets,'Prêts à retirer',null,'var(--success)','var(--success-soft)')}
    ${kpi(I.users(17),'Clients actifs',clientsActifs,'Visites aujourd\'hui',null,'#4F46E5','#EEF0FE')}
    ${kpi(I.pkg(17),'Stocks faibles',stocksFaibles,'Produits sous seuil',null,'var(--danger)','var(--danger-soft)')}
  </div>
 
  <div style="display:grid;grid-template-columns:1fr;gap:16px;margin-bottom:18px" class="dash-charts-grid">
    <div class="panel" style="grid-column:span 2">
      <div class="panel-head"><div><div class="panel-title">Chiffre d'affaires mensuel</div><div class="panel-sub">Historique vs objectif</div></div></div>
      <canvas id="revChart" height="90"></canvas>
    </div>
    <div class="panel">
      <div class="panel-head"><div><div class="panel-title">Prestations</div><div class="panel-sub">Répartition des articles</div></div></div>
      <canvas id="pieChart" height="180"></canvas>
    </div>
  </div>
 
  <div class="panel">
    <div class="panel-head"><div class="panel-title">Commandes récentes</div><button class="btn btn-ghost btn-sm" onclick="go('orders')">Voir tout ${I.chevR(12)}</button></div>
    <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Reçu</th><th>Client</th><th>Articles</th><th>Statut</th><th>Montant</th><th>Délai</th><th>Payé</th></tr></thead><tbody>
      ${DB.orders.slice(0,5).map(o=>`<tr><td class="td-mono">${o.id}</td><td class="td-strong">${esc(o.client)}</td><td>${o.articles} art.</td><td>${badge(o.statut)}</td><td class="td-mono">${fcfa(o.montant)}</td><td class="td-mono">${o.delai}</td><td>${o.paye?I.checkCircle(15):I.x(15)}</td></tr>`).join('')}
    </tbody></table></div></div>
  </div>
 
  <div class="panel">
    <div class="panel-title" style="margin-bottom:14px">Alertes prioritaires</div>
    <div style="display:flex;flex-direction:column;gap:8px">
      ${alerts.slice(0,6).map(a=>alertRow(a)).join('') || `<div style="color:var(--ink-faint);font-size:13px;padding:20px;text-align:center">Aucune alerte active — tout va bien.</div>`}
    </div>
  </div>`;
}
function kpi(icon,label,value,sub,trend,color,soft){
  return `<div class="kpi-card"><div class="kpi-top"><div class="kpi-icon" style="background:${soft};color:${color}">${icon}</div></div><div><div class="kpi-label">${label}</div><div class="kpi-value">${value}</div><div class="kpi-sub">${sub}</div></div></div>`;
}
function alertRow(a){
  const map={critical:['var(--danger)','var(--danger-soft)'],high:['var(--warning)','var(--warning-soft)'],medium:['var(--info)','var(--info-soft)']};
  const c = map[a.sev]||map.medium;
  return `<div class="alert-row" style="border-color:${c[0]}33;background:${c[1]}"><span class="sev-dot" style="background:${c[0]}"></span><div style="flex:1"><div style="font-size:13px;color:var(--ink)">${esc(a.msg)}</div><div style="font-size:10.5px;color:var(--ink-dim);margin-top:2px">${a.time}</div></div></div>`;
}
let chartRefs={};
function drawDashboardCharts(){
  if(!window.Chart) return;
  const isDark = state.theme==='dark';
  const gridColor = isDark?'#262B52':'#E1E5F0';
  const textColor = isDark?'#9298BE':'#6B7190';
  if(chartRefs.rev) chartRefs.rev.destroy();
  if(chartRefs.pie) chartRefs.pie.destroy();
  const revEl = $('#revChart'); const pieEl=$('#pieChart');
  if(revEl){
    chartRefs.rev = new Chart(revEl, {
      type:'line',
      data:{ labels: DB.revenueHistory.map(r=>r.month), datasets:[
        {label:'CA', data:DB.revenueHistory.map(r=>r.ca), borderColor:'#3452D9', backgroundColor:'rgba(52,82,217,.12)', fill:true, tension:.35, borderWidth:2.5, pointRadius:0},
        {label:'Objectif', data:DB.revenueHistory.map(r=>r.objectif), borderColor:'#9AA0BC', borderDash:[4,4], fill:false, tension:.2, borderWidth:1.5, pointRadius:0},
      ]},
      options:{responsive:true, plugins:{legend:{labels:{color:textColor,font:{size:11}}}}, scales:{ x:{grid:{display:false},ticks:{color:textColor,font:{size:11}}}, y:{grid:{color:gridColor},ticks:{color:textColor,font:{size:10},callback:v=>(v/1000)+'k'}}}}
    });
  }
  if(pieEl){
    const typeCounts={}; DB.articles.forEach(a=>{ typeCounts[a.type]=(typeCounts[a.type]||0)+1; });
    const palette=['#3452D9','#7C3AED','#C4923F','#DB2777','#0D9488','#64748B','#D68C22'];
    chartRefs.pie = new Chart(pieEl, {
      type:'doughnut',
      data:{ labels:Object.keys(typeCounts), datasets:[{data:Object.values(typeCounts), backgroundColor:palette, borderWidth:0}]},
      options:{responsive:true, cutout:'62%', plugins:{legend:{position:'bottom',labels:{color:textColor,font:{size:10.5},boxWidth:9,padding:9}}}}
    });
  }
}
 
/* ---- ORDERS ---- */
const orderFields = [
  {key:'client',label:'Client',type:'select',options:()=>DB.clients.map(c=>c.nom),required:true},
  {key:'tel',label:'Téléphone',type:'text',required:true},
  {key:'articles',label:"Nombre d'articles",type:'number',required:true},
  {key:'montant',label:'Montant (FCFA)',type:'number',required:true},
  {key:'statut',label:'Statut',type:'select',options:PIPELINE,required:true},
  {key:'delai',label:'Date de retrait (JJ/MM/AAAA)',type:'text',required:true},
  {key:'paye',label:'Paiement reçu',type:'checkbox'},
];
function resolveFields(fields){ return fields.map(f=> f.type==='select' && typeof f.options==='function' ? {...f, options:f.options()} : f); }
function viewOrders(){
  const q=(state.search.orders||'').toLowerCase();
  const rows = DB.orders.filter(o=> o.client.toLowerCase().includes(q) || o.id.toLowerCase().includes(q));
  return `
  ${sectionHead('Commandes & Reçus', `${DB.orders.length} reçus au total`, `
    <button class="btn btn-secondary btn-sm" onclick="exportCSV(DB.orders,'commandes')">${I.download(13)}Exporter</button>
    <button class="btn btn-primary btn-sm" onclick="orderAdd()">${I.plus(13)}Nouvelle commande</button>`)}
  ${searchBar('orders','Rechercher client, reçu...')}
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Reçu</th><th>Date</th><th>Client</th><th>Téléphone</th><th>Art.</th><th>Statut</th><th>Montant</th><th>Délai</th><th>Payé</th><th></th></tr></thead><tbody>
    ${rows.map(o=>`<tr>
      <td class="ticket-id">${o.id}</td><td class="td-mono">${o.date}</td><td class="td-strong">${esc(o.client)}</td><td class="td-mono">${o.tel}</td>
      <td>${o.articles}</td>
      <td>${inlineStatusSelect(o,'statut',PIPELINE,'orderChangeStatus')}</td>
      <td class="td-mono">${fcfa(o.montant)}</td><td class="td-mono">${o.delai}</td>
      <td><label style="display:flex;align-items:center;gap:6px;cursor:pointer"><input type="checkbox" ${o.paye?'checked':''} onchange="orderTogglePaid('${o.id}')"><span style="font-size:11.5px;color:${o.paye?'var(--success)':'var(--danger)'}">${o.paye?'Payé':'Impayé'}</span></label></td>
      <td><div class="row-actions">
        <button title="Imprimer" onclick="printReceipt('${o.id}')">${I.printer(14)}</button>
        <button title="Modifier" onclick="orderEdit('${o.id}')">${I.edit(14)}</button>
        <button class="danger" title="Supprimer" onclick="orderDelete('${o.id}')">${I.trash(14)}</button>
      </div></td>
    </tr>`).join('') || emptyRow(10)}
  </tbody></table></div></div>`;
}
function inlineStatusSelect(row,key,options,handler){
  return `<select class="select-inline" onchange="${handler}('${row.id}',this.value)">${options.map(o=>`<option value="${esc(o)}" ${row[key]===o?'selected':''}>${esc(o)}</option>`).join('')}</select>`;
}
function emptyRow(colspan){ return `<tr class="empty-row"><td colspan="${colspan}">Aucun résultat pour cette recherche.</td></tr>`; }
function orderAdd(){ crudAdd(DB.orders, resolveFields(orderFields), 'REC-2024', 'Commandes', 'orders', {date:todayFR()}, 'Nouvelle commande'); }
function orderEdit(id){ const row=DB.orders.find(o=>o.id===id); crudEdit(DB.orders, resolveFields(orderFields), row, 'Commandes'); }
function orderDelete(id){ const row=DB.orders.find(o=>o.id===id); crudDelete(DB.orders,row,'Commandes','id'); }
function orderTogglePaid(id){ const row=DB.orders.find(o=>o.id===id); row.paye=!row.paye; logAudit('Commandes',`Paiement ${row.id} → ${row.paye?'Payé':'Impayé'}`); persist(); renderView(); toast('Statut de paiement mis à jour'); }
function orderChangeStatus(id,val){ const row=DB.orders.find(o=>o.id===id); row.statut=val; logAudit('Commandes',`Statut ${row.id} → ${val}`); persist(); renderView(); renderNav(); toast('Statut de la commande mis à jour'); }
function printReceipt(id){
  const o=DB.orders.find(x=>x.id===id); if(!o) return;
  const w=window.open('','_blank','width=420,height=600');
  w.document.write(`<html><head><title>${o.id}</title><style>body{font-family:monospace;padding:20px;font-size:13px}h2{margin:0 0 4px}hr{border:none;border-top:1px dashed #999;margin:10px 0}</style></head><body>
    <h2>Pressing Saint Joseph</h2><div>Reçu de dépôt</div><hr>
    <div><b>${o.id}</b></div><div>Date : ${o.date}</div><div>Client : ${o.client}</div><div>Tél : ${o.tel}</div>
    <hr><div>Articles : ${o.articles}</div><div>Statut : ${o.statut}</div><div>Délai : ${o.delai}</div>
    <hr><div><b>Total : ${fcfa(o.montant)}</b></div><div>Paiement : ${o.paye?'Réglé':'En attente'}</div><hr>
    <div style="text-align:center;margin-top:14px">Merci de votre confiance</div>
  </body></html>`);
  w.document.close(); w.print();
}
function exportCSV(list, name){
  if(!list.length){ toast('Aucune donnée à exporter','danger'); return; }
  const keys=Object.keys(list[0]);
  const csv=[keys.join(';'), ...list.map(r=>keys.map(k=>`"${String(r[k]??'').replace(/"/g,'""')}"`).join(';'))].join('\\n');
  const blob=new Blob(['\\ufeff'+csv],{type:'text/csv;charset=utf-8;'});
  const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download=name+'.csv'; a.click();
  toast('Export CSV généré');
}
 
/* ---- TRACKING ---- */
const articleFields = [
  {key:'recu',label:'N° de reçu',type:'text',required:true},
  {key:'client',label:'Client',type:'select',options:()=>DB.clients.map(c=>c.nom),required:true},
  {key:'type',label:'Type d\'article',type:'select',options:['Chemise','Pantalon','Costume','Robe','Veste','Couverture','Tapis','Rideau','Uniforme']},
  {key:'couleur',label:'Couleur',type:'text'},
  {key:'marque',label:'Marque',type:'text'},
  {key:'taille',label:'Taille',type:'text'},
  {key:'etat',label:'État',type:'text'},
  {key:'taches',label:'Taches / défauts',type:'text'},
  {key:'statut',label:'Statut',type:'select',options:PIPELINE,required:true},
  {key:'prix',label:'Prix (FCFA)',type:'number',required:true},
];
function viewTracking(){
  const q=(state.search.tracking||'').toLowerCase();
  const filterStatus = state.filter.tracking || 'Tous';
  const rows = DB.articles.filter(a=> (filterStatus==='Tous'||a.statut===filterStatus) && (a.client.toLowerCase().includes(q)||a.id.toLowerCase().includes(q)));
  return `
  ${sectionHead('Traçabilité des Articles', 'Suivi individuel de chaque article dans le circuit', `
    <button class="btn btn-secondary btn-sm" onclick="exportCSV(DB.articles,'tracabilite')">${I.download(13)}Exporter</button>
    <button class="btn btn-primary btn-sm" onclick="articleAdd()">${I.plus(13)}Ajouter un article</button>`)}
  <div class="panel" style="margin-bottom:18px">
    <div class="panel-sub" style="text-transform:uppercase;letter-spacing:.07em;font-weight:700;margin-bottom:12px;font-size:10.5px">Circuit de traitement</div>
    <div class="pipeline-strip">
      ${PIPELINE.map((step,i)=>{ const c=DB.articles.filter(a=>a.statut===step).length; return `<div class="pipe-step ${c>0?'active':''}"><div class="pipe-num">${c}</div><div class="pipe-label">${step}</div></div>${i<PIPELINE.length-1?`<span class="pipe-connector">${I.chevR(12)}</span>`:''}`; }).join('')}
    </div>
  </div>
  ${searchBar('tracking','ID article, client, reçu...', `<select class="filter-select" onchange="state.filter.tracking=this.value;renderView()"><option ${filterStatus==='Tous'?'selected':''}>Tous</option>${PIPELINE.map(p=>`<option ${filterStatus===p?'selected':''}>${p}</option>`).join('')}</select>`)}
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>ID Article</th><th>Reçu</th><th>Type</th><th>Couleur</th><th>Marque</th><th>Taille</th><th>État</th><th>Taches</th><th>Statut</th><th>Client</th><th>Prix</th><th></th></tr></thead><tbody>
    ${rows.map(a=>`<tr>
      <td class="ticket-id">${a.id}</td><td class="td-mono">${a.recu}</td><td class="td-strong">${esc(a.type)}</td><td>${esc(a.couleur)}</td><td>${esc(a.marque)}</td><td class="td-mono">${esc(a.taille)}</td><td>${esc(a.etat)}</td>
      <td style="color:var(--ink-dim);font-size:12px">${esc(a.taches)}</td>
      <td>${inlineStatusSelect(a,'statut',PIPELINE,'articleChangeStatus')}</td>
      <td>${esc(a.client)}</td><td class="td-mono">${fcfa(a.prix)}</td>
      <td><div class="row-actions"><button onclick="articleEdit('${a.id}')">${I.edit(14)}</button><button class="danger" onclick="articleDelete('${a.id}')">${I.trash(14)}</button></div></td>
    </tr>`).join('') || emptyRow(12)}
  </tbody></table></div></div>`;
}
function articleAdd(){ crudAdd(DB.articles, resolveFields(articleFields), 'ART', 'Traçabilité', 'tracking', {}, 'Ajouter un article'); }
function articleEdit(id){ const row=DB.articles.find(a=>a.id===id); crudEdit(DB.articles, resolveFields(articleFields), row, 'Traçabilité'); }
function articleDelete(id){ const row=DB.articles.find(a=>a.id===id); crudDelete(DB.articles,row,'Traçabilité','id'); }
function articleChangeStatus(id,val){ const row=DB.articles.find(a=>a.id===id); row.statut=val; logAudit('Traçabilité',`Statut ${row.id} → ${val}`); persist(); renderView(); toast('Statut article mis à jour'); }
 
/* ---- CLIENTS ---- */
const clientFields = [
  {key:'nom',label:'Nom complet',type:'text',required:true,full:true},
  {key:'tel',label:'Téléphone',type:'text',required:true},
  {key:'whatsapp',label:'WhatsApp disponible',type:'checkbox'},
  {key:'email',label:'Email',type:'email'},
  {key:'quartier',label:'Quartier',type:'text'},
  {key:'categorie',label:'Catégorie',type:'select',options:['Standard','Premium','VIP','Entreprise']},
  {key:'solde',label:'Solde impayé (FCFA)',type:'number'},
];
function viewClients(){
  const q=(state.search.clients||'').toLowerCase();
  const rows = DB.clients.filter(c=> c.nom.toLowerCase().includes(q) || c.tel.includes(q) || c.quartier.toLowerCase().includes(q));
  const vip = DB.clients.filter(c=>c.categorie==='VIP').length;
  const solde = DB.clients.reduce((s,c)=>s+c.solde,0);
  return `
  ${sectionHead('Clients & Carnet d\'adresses', `${DB.clients.length} clients · ${vip} VIP`, `
    <button class="btn btn-secondary btn-sm" onclick="exportCSV(DB.clients,'clients')">${I.download(13)}Exporter</button>
    <button class="btn btn-primary btn-sm" onclick="clientAdd()">${I.plus(13)}Nouveau client</button>`)}
  <div class="grid-kpi">
    ${kpi(I.users(16),'Total clients',DB.clients.length,'Base active',null,'var(--info)','var(--info-soft)')}
    ${kpi(I.award(16),'Clients VIP',vip,'CA > 200k FCFA',null,'var(--accent)','var(--accent-soft)')}
    ${kpi(I.alertCirc(16),'Soldes impayés',fcfa(solde),`${DB.clients.filter(c=>c.solde>0).length} clients`,null,'var(--warning)','var(--warning-soft)')}
    ${kpi(I.clock(16),'Points fidélité cumulés',DB.clients.reduce((s,c)=>s+c.points,0).toLocaleString('fr-FR'),'Programme actif',null,'#7C3AED','#F1EBFD')}
  </div>
  ${searchBar('clients','Nom, téléphone, quartier...')}
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Client</th><th>Téléphone</th><th>Quartier</th><th>Catégorie</th><th>Commandes</th><th>Dépenses</th><th>Solde</th><th>Points</th><th>Dernière visite</th><th></th></tr></thead><tbody>
    ${rows.map(c=>`<tr>
      <td><div class="name-cell"><div class="avatar-sm">${esc(c.nom[0])}</div><span class="td-strong">${esc(c.nom)}</span></div></td>
      <td><div style="display:flex;align-items:center;gap:6px"><span class="td-mono">${c.tel}</span>${c.whatsapp?`<span style="color:var(--success)">${I.msg(12)}</span>`:''}</div></td>
      <td>${esc(c.quartier)}</td><td>${badge(c.categorie)}</td><td class="td-mono">${c.commandes}</td><td class="td-mono">${fcfa(c.depenses)}</td>
      <td>${c.solde>0?`<span style="color:var(--danger);font-family:var(--font-mono);font-size:11.5px;font-weight:600">${fcfa(c.solde)}</span>`:`<span style="color:var(--success)">—</span>`}</td>
      <td><span class="chip" style="background:var(--accent-soft);color:var(--accent)">${c.points} pts</span></td>
      <td class="td-mono">${c.derniere}</td>
      <td><div class="row-actions"><button onclick="clientEdit('${c.id}')">${I.edit(14)}</button><button class="danger" onclick="clientDelete('${c.id}')">${I.trash(14)}</button></div></td>
    </tr>`).join('') || emptyRow(10)}
  </tbody></table></div></div>`;
}
function clientAdd(){ crudAdd(DB.clients, clientFields, 'CLI', 'Clients', 'clients', {commandes:0,depenses:0,points:0,derniere:todayFR()}, 'Nouveau client'); }
function clientEdit(id){ const row=DB.clients.find(c=>c.id===id); crudEdit(DB.clients, clientFields, row, 'Clients'); }
function clientDelete(id){ const row=DB.clients.find(c=>c.id===id); crudDelete(DB.clients,row,'Clients','nom'); }
 
/* ---- INVENTORY ---- */
const invFields = [
  {key:'produit',label:'Produit',type:'text',required:true,full:true},
  {key:'categorie',label:'Catégorie',type:'select',options:['Lavage','Emballage','Repassage','Autre']},
  {key:'stock',label:'Stock actuel',type:'number',required:true},
  {key:'min',label:'Seuil minimum',type:'number',required:true},
  {key:'unite',label:'Unité',type:'text',placeholder:'L, Kg, Pcs...'},
  {key:'fournisseur',label:'Fournisseur',type:'text'},
  {key:'prix',label:'Prix unitaire (FCFA)',type:'number'},
];
function viewInventory(){
  const q=(state.search.inventory||'').toLowerCase();
  const rows = DB.inventory.filter(i=>i.produit.toLowerCase().includes(q));
  const alertCount = DB.inventory.filter(i=>i.stock<i.min).length;
  return `
  ${sectionHead('Inventaire & Stocks', `${DB.inventory.length} références · ${alertCount} alertes`, `
    <button class="btn btn-secondary btn-sm" onclick="exportCSV(DB.inventory,'inventaire')">${I.download(13)}Exporter</button>
    <button class="btn btn-primary btn-sm" onclick="invAdd()">${I.plus(13)}Entrée de stock</button>`)}
  ${alertCount>0?`<div class="banner banner-warning" style="margin-bottom:18px">${I.alertTri(15)}<span><b>${alertCount} produits</b> sont en dessous du seuil minimum — commande fournisseur recommandée</span></div>`:''}
  ${searchBar('inventory','Rechercher un produit...')}
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Réf.</th><th>Produit</th><th>Catégorie</th><th>Stock</th><th>Seuil</th><th>Unité</th><th>Fournisseur</th><th>Prix unit.</th><th>Valeur</th><th>Statut</th><th></th></tr></thead><tbody>
    ${rows.map(i=>{ const low=i.stock<i.min; return `<tr style="${low?'background:var(--danger-soft)':''}">
      <td class="td-mono">${i.id}</td><td class="td-strong">${esc(i.produit)}</td><td>${esc(i.categorie)}</td>
      <td><span style="font-family:var(--font-mono);font-weight:700;color:${low?'var(--danger)':'var(--ink)'}">${i.stock}</span></td>
      <td class="td-mono">${i.min}</td><td>${esc(i.unite)}</td><td>${esc(i.fournisseur)}</td><td class="td-mono">${fcfa(i.prix)}</td><td class="td-mono">${fcfa(i.stock*i.prix)}</td>
      <td>${low?`<span style="color:var(--danger);font-size:11.5px;font-weight:600;display:flex;align-items:center;gap:4px">${I.alertTri(12)}Alerte</span>`:`<span style="color:var(--success);font-size:11.5px;font-weight:600;display:flex;align-items:center;gap:4px">${I.checkCircle(12)}OK</span>`}</td>
      <td><div class="row-actions"><button onclick="invEdit('${i.id}')">${I.edit(14)}</button><button class="danger" onclick="invDelete('${i.id}')">${I.trash(14)}</button></div></td>
    </tr>`; }).join('') || emptyRow(11)}
  </tbody></table></div></div>`;
}
function invAdd(){ crudAdd(DB.inventory, invFields, 'INV', 'Inventaire', 'inventory', {}, 'Entrée de stock'); }
function invEdit(id){ const row=DB.inventory.find(i=>i.id===id); crudEdit(DB.inventory, invFields, row, 'Inventaire'); }
function invDelete(id){ const row=DB.inventory.find(i=>i.id===id); crudDelete(DB.inventory,row,'Inventaire','produit'); }
 
/* ---- MACHINES ---- */
const machineFields = [
  {key:'nom',label:'Nom de l\'équipement',type:'text',required:true,full:true},
  {key:'type',label:'Type',type:'select',options:['Lave-linge','Séchoir','Presse','Repassage','Autre']},
  {key:'etat',label:'État',type:'select',options:['En fonctionnement','En panne','Maintenance']},
  {key:'cycles',label:'Cycles totaux',type:'number'},
  {key:'maintenance',label:'Prochaine maintenance (JJ/MM/AAAA)',type:'text'},
  {key:'utilisation',label:'Utilisation (%)',type:'number'},
];
function viewMachines(){
  const panne = DB.machines.filter(m=>m.etat==='En panne').length;
  return `
  ${sectionHead('Machines & Équipements', `${DB.machines.length} équipements · ${panne} en panne`, `<button class="btn btn-primary btn-sm" onclick="machineAdd()">${I.plus(13)}Ajouter équipement</button>`)}
  <div class="card-grid">
    ${DB.machines.map(m=>`
    <div class="tile ${m.etat==='En panne'?'alert':''}">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;gap:10px">
        <div><div class="td-strong">${esc(m.nom)}</div><div style="font-size:11.5px;color:var(--ink-dim);margin-top:2px">${esc(m.type)} · ${m.id}</div></div>
        ${badge(m.etat)}
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;font-size:11.5px">
        <div><div style="color:var(--ink-dim)">Cycles totaux</div><div class="td-mono" style="font-weight:700;color:var(--ink)">${m.cycles.toLocaleString('fr-FR')}</div></div>
        <div><div style="color:var(--ink-dim)">Maintenance</div><div class="td-mono" style="font-weight:700;color:${m.etat==='En panne'?'var(--danger)':'var(--ink)'}">${m.maintenance}</div></div>
      </div>
      ${m.etat!=='En panne'?`<div><div style="display:flex;justify-content:space-between;font-size:11px;margin-bottom:5px"><span style="color:var(--ink-dim)">Utilisation</span><span class="td-mono">${m.utilisation}%</span></div><div class="progress-track"><div class="progress-fill" style="width:${m.utilisation}%;background:${m.utilisation>85?'var(--danger)':m.utilisation>60?'var(--info)':'var(--success)'}"></div></div></div>`
      : `<div class="banner banner-danger" style="padding:8px 11px;font-size:11.5px">${I.alertTri(13)}Intervention requise — hors service</div>`}
      <div style="display:flex;gap:7px"><button class="btn btn-ghost btn-sm" style="flex:1" onclick="machineEdit('${m.id}')">${I.wrench(12)}Gérer</button><button class="btn btn-ghost btn-sm danger" onclick="machineDelete('${m.id}')">${I.trash(12)}</button></div>
    </div>`).join('')}
  </div>`;
}
function machineAdd(){ crudAdd(DB.machines, machineFields, 'MCH', 'Machines', 'machines', {}, 'Ajouter un équipement'); }
function machineEdit(id){ const row=DB.machines.find(m=>m.id===id); crudEdit(DB.machines, machineFields, row, 'Machines'); }
function machineDelete(id){ const row=DB.machines.find(m=>m.id===id); crudDelete(DB.machines,row,'Machines','nom'); }
 
/* ---- HR ---- */
const staffFields = [
  {key:'nom',label:'Nom complet',type:'text',required:true,full:true},
  {key:'fonction',label:'Fonction',type:'text',required:true},
  {key:'presence',label:'Présent aujourd\'hui',type:'checkbox'},
  {key:'arrivee',label:'Heure d\'arrivée',type:'text',placeholder:'08:00'},
  {key:'taches',label:'Tâches réalisées',type:'number'},
  {key:'rendement',label:'Rendement (%)',type:'number'},
  {key:'conge',label:'En congé',type:'checkbox'},
];
function viewHR(){
  const present = DB.staff.filter(s=>s.presence).length;
  const avgR = Math.round(DB.staff.reduce((s,e)=>s+e.rendement,0)/(DB.staff.length||1));
  return `
  ${sectionHead('Ressources Humaines', `${DB.staff.length} employés · ${present} présents aujourd'hui`, `<button class="btn btn-primary btn-sm" onclick="staffAdd()">${I.plus(13)}Ajouter employé</button>`)}
  <div class="grid-kpi">
    ${kpi(I.userCheck(16),'Présents',present,"Aujourd'hui",null,'var(--success)','var(--success-soft)')}
    ${kpi(I.x(16),'Absents',DB.staff.length-present,'Dont congés',null,'var(--danger)','var(--danger-soft)')}
    ${kpi(I.activity(16),'Tâches réalisées',DB.staff.reduce((s,e)=>s+e.taches,0),'Ce jour',null,'var(--info)','var(--info-soft)')}
    ${kpi(I.target(16),'Rendement moyen',avgR+'%','Équipe complète',null,'#7C3AED','#F1EBFD')}
  </div>
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Employé</th><th>Fonction</th><th>Présence</th><th>Arrivée</th><th>Tâches</th><th>Rendement</th><th>Statut</th><th></th></tr></thead><tbody>
    ${DB.staff.map(s=>`<tr>
      <td><div class="name-cell"><span style="width:8px;height:8px;border-radius:50%;background:${s.presence?'var(--success)':'var(--danger)'}"></span><span class="td-strong">${esc(s.nom)}</span></div></td>
      <td>${esc(s.fonction)}</td>
      <td><label style="cursor:pointer;display:flex;align-items:center;gap:6px"><input type="checkbox" ${s.presence?'checked':''} onchange="staffTogglePresence('${s.id}')"><span style="font-size:11.5px;color:${s.presence?'var(--success)':'var(--danger)'}">${s.presence?'Présent':'Absent'}</span></label></td>
      <td class="td-mono">${esc(s.arrivee)}</td><td class="td-mono">${s.taches}</td>
      <td><div style="display:flex;align-items:center;gap:8px"><div class="progress-track" style="width:64px"><div class="progress-fill" style="width:${s.rendement}%;background:var(--primary)"></div></div><span class="td-mono">${s.rendement}%</span></div></td>
      <td>${s.conge?badge('En congé'):badge(s.presence?'Présent':'Absent')}</td>
      <td><div class="row-actions"><button onclick="staffEdit('${s.id}')">${I.edit(14)}</button><button class="danger" onclick="staffDelete('${s.id}')">${I.trash(14)}</button></div></td>
    </tr>`).join('') || emptyRow(8)}
  </tbody></table></div></div>`;
}
function staffAdd(){ crudAdd(DB.staff, staffFields, 'EMP', 'RH', 'hr', {}, 'Ajouter employé'); }
function staffEdit(id){ const row=DB.staff.find(s=>s.id===id); crudEdit(DB.staff, staffFields, row, 'RH'); }
function staffDelete(id){ const row=DB.staff.find(s=>s.id===id); crudDelete(DB.staff,row,'RH','nom'); }
function staffTogglePresence(id){ const row=DB.staff.find(s=>s.id===id); row.presence=!row.presence; logAudit('RH',`Présence ${row.nom} → ${row.presence?'Présent':'Absent'}`); persist(); renderView(); toast('Présence mise à jour'); }
 
/* ---- FINANCE ---- */
const txnFields = [
  {key:'type',label:'Type',type:'select',options:['Encaissement','Dépense'],required:true},
  {key:'desc',label:'Description',type:'text',required:true,full:true},
  {key:'montant',label:'Montant (FCFA, positif)',type:'number',required:true},
  {key:'mode',label:'Mode de paiement',type:'select',options:['Espèces','Mobile Money','Carte','Virement']},
  {key:'agent',label:'Agent',type:'text'},
];
function viewFinance(){
  const enc = DB.transactions.filter(t=>t.montant>0).reduce((s,t)=>s+t.montant,0);
  const dep = Math.abs(DB.transactions.filter(t=>t.montant<0).reduce((s,t)=>s+t.montant,0));
  const solde = DB.clients.reduce((s,c)=>s+c.solde,0);
  return `
  ${sectionHead('Finances & Comptabilité', 'Suivi des flux financiers', `
    <button class="btn btn-secondary btn-sm" onclick="exportCSV(DB.transactions,'finances')">${I.download(13)}Exporter</button>
    <button class="btn btn-primary btn-sm" onclick="txnAdd()">${I.plus(13)}Nouvelle transaction</button>`)}
  <div class="grid-kpi">
    ${kpi(I.trendUp(16),'Encaissements',fcfa(enc),'Cumul',null,'var(--success)','var(--success-soft)')}
    ${kpi(I.trendDown(16),'Dépenses',fcfa(dep),'Cumul',null,'var(--danger)','var(--danger-soft)')}
    ${kpi(I.dollar(16),'Bénéfice net',fcfa(enc-dep),'Cumul',null,'var(--info)','var(--info-soft)')}
    ${kpi(I.alertCirc(16),'À recouvrer',fcfa(solde),`${DB.clients.filter(c=>c.solde>0).length} clients`,null,'var(--warning)','var(--warning-soft)')}
  </div>
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>ID</th><th>Date</th><th>Type</th><th>Description</th><th>Montant</th><th>Mode</th><th>Agent</th><th></th></tr></thead><tbody>
    ${DB.transactions.map(t=>`<tr>
      <td class="td-mono">${t.id}</td><td class="td-mono">${t.date}</td>
      <td><span style="font-size:11.5px;font-weight:600;color:${t.montant>0?'var(--success)':'var(--danger)'}">${t.type}</span></td>
      <td>${esc(t.desc)}</td>
      <td><span class="td-mono" style="font-weight:700;color:${t.montant>0?'var(--success)':'var(--danger)'}">${t.montant>0?'+':'-'}${fcfa(t.montant)}</span></td>
      <td><span class="chip">${esc(t.mode)}</span></td><td>${esc(t.agent)}</td>
      <td><div class="row-actions"><button onclick="txnEdit('${t.id}')">${I.edit(14)}</button><button class="danger" onclick="txnDelete('${t.id}')">${I.trash(14)}</button></div></td>
    </tr>`).join('') || emptyRow(8)}
  </tbody></table></div></div>`;
}
function fixTxnSign(data){ data.montant = Math.abs(data.montant) * (data.type==='Dépense' ? -1 : 1); return data; }
function txnAdd(){
  openModal('Nouvelle transaction', `
    <form id="crudForm">
      <div class="form-grid">${renderFormFields(txnFields)}</div>
      <div class="form-foot"><button type="button" class="btn btn-secondary" onclick="closeModal()">Annuler</button><button type="submit" class="btn btn-primary">${I.check(14)}Enregistrer</button></div>
    </form>`);
  $('#crudForm').onsubmit=(e)=>{
    e.preventDefault();
    const data = fixTxnSign(readForm(e.target, txnFields));
    const rec = Object.assign({id:uid('TXN'), date:nowFR()}, data);
    DB.transactions.unshift(rec);
    logAudit('Finances', `Ajout — ${rec.id}`);
    persist(); closeModal(); renderView(); renderNav();
    toast('Finances : transaction enregistrée');
  };
}
function txnEdit(id){
  const row=DB.transactions.find(t=>t.id===id);
  openModal(`Modifier — ${row.id}`, `
    <form id="crudForm">
      <div class="form-grid">${renderFormFields(txnFields,row)}</div>
      <div class="form-foot"><button type="button" class="btn btn-secondary" onclick="closeModal()">Annuler</button><button type="submit" class="btn btn-primary">${I.check(14)}Mettre à jour</button></div>
    </form>`);
  $('#crudForm').onsubmit=(e)=>{
    e.preventDefault();
    const data = fixTxnSign(readForm(e.target, txnFields));
    Object.assign(row, data);
    logAudit('Finances', `Modification — ${row.id}`);
    persist(); closeModal(); renderView(); renderNav();
    toast('Finances : transaction mise à jour');
  };
}
function txnDelete(id){ const row=DB.transactions.find(t=>t.id===id); crudDelete(DB.transactions,row,'Finances','desc'); }
 
/* ---- COMPETITION ---- */
const compFields = [
  {key:'prestation',label:'Prestation',type:'text',required:true,full:true},
  {key:'psj',label:'Prix PSJ (FCFA)',type:'number',required:true},
  {key:'excellence',label:'Pressing Excellence (FCFA)',type:'number'},
  {key:'quickpress',label:'Quick Press (FCFA)',type:'number'},
  {key:'central',label:'Pressing Central (FCFA)',type:'number'},
];
function viewCompetition(){
  return `
  ${sectionHead('Concurrence & Tarification', 'Analyse comparative des prix — Abidjan', `<button class="btn btn-primary btn-sm" onclick="compAdd()">${I.plus(13)}Ajouter prestation</button>`)}
  <div class="banner banner-info" style="margin-bottom:18px">${I.zap(15)}<span>PSJ est <b>bien positionné</b> sur les articles premium. Modifiez librement les tarifs ci-dessous pour refléter le marché.</span></div>
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Prestation</th><th>PSJ</th><th>Pressing Excellence</th><th>Quick Press</th><th>Pressing Central</th><th>Position</th><th></th></tr></thead><tbody>
    ${DB.competition.map((r,idx)=>{ const all=[r.excellence,r.quickpress,r.central]; const min=Math.min(...all),max=Math.max(...all);
      const pos = r.psj<=min?'Plus bas':r.psj>=max?'Plus haut':'Milieu';
      const col = pos==='Plus bas'?'var(--success)':pos==='Plus haut'?'var(--warning)':'var(--info)';
      return `<tr><td class="td-strong">${esc(r.prestation)}</td><td><span class="td-mono" style="font-weight:800;color:var(--primary)">${r.psj.toLocaleString('fr-FR')} F</span></td>
      <td class="td-mono">${r.excellence.toLocaleString('fr-FR')} F</td><td class="td-mono">${r.quickpress.toLocaleString('fr-FR')} F</td><td class="td-mono">${r.central.toLocaleString('fr-FR')} F</td>
      <td><span style="color:${col};font-size:11.5px;font-weight:700">${pos}</span></td>
      <td><div class="row-actions"><button onclick="compEdit(${idx})">${I.edit(14)}</button><button class="danger" onclick="compDelete(${idx})">${I.trash(14)}</button></div></td></tr>`; }).join('')}
  </tbody></table></div></div>`;
}
function compAdd(){ crudAdd(DB.competition, compFields, null, 'Concurrence', 'competition', {}, 'Ajouter une prestation'); }
function compEdit(idx){ crudEdit(DB.competition, compFields, DB.competition[idx], 'Concurrence'); }
function compDelete(idx){ crudDelete(DB.competition, DB.competition[idx], 'Concurrence', 'prestation'); }
 
/* ---- MARKETING ---- */
const campFields = [
  {key:'nom',label:'Nom de la campagne',type:'text',required:true,full:true},
  {key:'type',label:'Type d\'offre',type:'text',placeholder:'Promo -20%, Points x2...'},
  {key:'cible',label:'Cible',type:'text'},
  {key:'clientsN',label:'Clients touchés',type:'number'},
  {key:'debut',label:'Début (JJ/MM/AAAA)',type:'text'},
  {key:'fin',label:'Fin (JJ/MM/AAAA)',type:'text'},
  {key:'statut',label:'Statut',type:'select',options:['Planifiée','Active','Terminée']},
];
function viewMarketing(){
  const active = DB.campaigns.filter(c=>c.statut==='Active').length;
  return `
  ${sectionHead('Marketing & Fidélisation', 'Campagnes, promotions et programme de fidélité', `<button class="btn btn-primary btn-sm" onclick="campAdd()">${I.plus(13)}Nouvelle campagne</button>`)}
  <div class="grid-kpi">
    ${kpi(I.star(16),'Clients VIP',DB.clients.filter(c=>c.categorie==='VIP').length,'Fidélité max',null,'var(--accent)','var(--accent-soft)')}
    ${kpi(I.award(16),'Points en circulation',DB.clients.reduce((s,c)=>s+c.points,0).toLocaleString('fr-FR'),'Programme fidélité',null,'#7C3AED','#F1EBFD')}
    ${kpi(I.megaphone(16),'Campagnes actives',active,'En ce moment',null,'var(--info)','var(--info-soft)')}
    ${kpi(I.clock(16),'Clients inactifs',DB.clients.filter(c=>c.solde===0 && c.commandes<8).length,'60 jours sans commande (est.)',null,'var(--ink-faint)','var(--surface-alt)')}
  </div>
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>ID</th><th>Campagne</th><th>Type</th><th>Cible</th><th>Clients</th><th>Période</th><th>Statut</th><th></th></tr></thead><tbody>
    ${DB.campaigns.map(c=>`<tr><td class="td-mono">${c.id}</td><td class="td-strong">${esc(c.nom)}</td><td><span class="chip">${esc(c.type)}</span></td><td>${esc(c.cible)}</td><td class="td-mono">${c.clientsN}</td><td class="td-mono">${c.debut} → ${c.fin}</td><td>${badge(c.statut)}</td>
      <td><div class="row-actions"><button onclick="campEdit('${c.id}')">${I.edit(14)}</button><button class="danger" onclick="campDelete('${c.id}')">${I.trash(14)}</button></div></td></tr>`).join('') || emptyRow(8)}
  </tbody></table></div></div>`;
}
function campAdd(){ crudAdd(DB.campaigns, campFields, 'CMP', 'Marketing', 'marketing', {statut:'Planifiée'}, 'Nouvelle campagne'); }
function campEdit(id){ const row=DB.campaigns.find(c=>c.id===id); crudEdit(DB.campaigns, campFields, row, 'Marketing'); }
function campDelete(id){ const row=DB.campaigns.find(c=>c.id===id); crudDelete(DB.campaigns,row,'Marketing','nom'); }
 
/* ---- QUALITY ---- */
const claimFields = [
  {key:'client',label:'Client',type:'select',options:()=>DB.clients.map(c=>c.nom),required:true},
  {key:'type',label:'Type de réclamation',type:'text',required:true},
  {key:'article',label:'Article concerné',type:'text'},
  {key:'gravite',label:'Gravité',type:'select',options:['Mineure','Modérée','Élevée']},
  {key:'statut',label:'Statut',type:'select',options:['En cours','Résolu']},
  {key:'responsable',label:'Responsable',type:'text'},
];
function viewQuality(){
  const resolues = DB.claims.filter(c=>c.statut==='Résolu').length;
  const rate = DB.claims.length? Math.round(resolues/DB.claims.length*100):0;
  return `
  ${sectionHead('Qualité & Réclamations', 'Suivi des avis et réclamations clients', `<button class="btn btn-primary btn-sm" onclick="claimAdd()">${I.plus(13)}Nouvelle réclamation</button>`)}
  <div class="grid-kpi">
    ${kpi(I.star(16),'Note qualité','4.7 / 5','Sur 88 avis',null,'var(--accent)','var(--accent-soft)')}
    ${kpi(I.alertCirc(16),'Réclamations',DB.claims.length,'Total',null,'var(--danger)','var(--danger-soft)')}
    ${kpi(I.checkCircle(16),'Résolues',resolues,rate+'% de résolution',null,'var(--success)','var(--success-soft)')}
    ${kpi(I.clock(16),'En cours',DB.claims.length-resolues,'À traiter',null,'var(--warning)','var(--warning-soft)')}
  </div>
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Réf.</th><th>Date</th><th>Client</th><th>Type</th><th>Article</th><th>Gravité</th><th>Statut</th><th>Responsable</th><th></th></tr></thead><tbody>
    ${DB.claims.map(c=>`<tr><td class="td-mono">${c.id}</td><td class="td-mono">${c.date}</td><td class="td-strong">${esc(c.client)}</td><td>${esc(c.type)}</td><td class="td-mono" style="font-size:11.5px">${esc(c.article)}</td>
      <td>${badge(c.gravite)}</td><td>${inlineStatusSelect(c,'statut',['En cours','Résolu'],'claimChangeStatus')}</td><td>${esc(c.responsable)}</td>
      <td><div class="row-actions"><button onclick="claimEdit('${c.id}')">${I.edit(14)}</button><button class="danger" onclick="claimDelete('${c.id}')">${I.trash(14)}</button></div></td></tr>`).join('') || emptyRow(9)}
  </tbody></table></div></div>`;
}
function claimAdd(){ crudAdd(DB.claims, resolveFields(claimFields), 'REC-C', 'Qualité', 'quality', {date:todayFR(),statut:'En cours'}, 'Nouvelle réclamation'); }
function claimEdit(id){ const row=DB.claims.find(c=>c.id===id); crudEdit(DB.claims, resolveFields(claimFields), row, 'Qualité'); }
function claimDelete(id){ const row=DB.claims.find(c=>c.id===id); crudDelete(DB.claims,row,'Qualité','type'); }
function claimChangeStatus(id,val){ const row=DB.claims.find(c=>c.id===id); row.statut=val; logAudit('Qualité',`Statut ${row.id} → ${val}`); persist(); renderView(); toast('Réclamation mise à jour'); }
 
/* ---- CONTROL CENTER ---- */
function viewControl(){
  const alerts = computeAlerts();
  return `
  ${sectionHead('Centre de Contrôle & Surveillance', 'Alertes automatiques, anomalies et journal d\'audit', `<button class="btn btn-secondary btn-sm" onclick="renderView();toast('Analyse actualisée')">${I.refresh(13)}Actualiser</button>`)}
  <div style="display:grid;grid-template-columns:1fr;gap:16px" class="control-grid">
    <div class="panel">
      <div class="panel-head"><div class="panel-title">Alertes actives (calculées en temps réel)</div><span class="chip" style="background:var(--danger-soft);color:var(--danger)">${alerts.length}</span></div>
      <div style="display:flex;flex-direction:column;gap:8px">${alerts.map(a=>alertRow(a)).join('')||`<div style="color:var(--ink-faint);padding:20px;text-align:center;font-size:13px">Aucune alerte active.</div>`}</div>
    </div>
    <div class="panel">
      <div class="panel-head"><div class="panel-title">Journal d'audit</div><button class="btn btn-ghost btn-sm" onclick="exportCSV(DB.auditLog,'journal_audit')">${I.download(12)}Export</button></div>
      <div style="display:flex;flex-direction:column;gap:8px">
        ${DB.auditLog.slice(0,25).map(e=>`<div class="audit-row"><div class="avatar-sm">${esc(e.user[0])}</div><div style="flex:1;min-width:0"><div style="font-size:12.5px">${esc(e.action)}</div><div style="font-size:11px;color:var(--ink-dim)">${esc(e.user)} · <span style="color:var(--primary)">${esc(e.module)}</span></div></div><span class="td-mono" style="font-size:10.5px;color:var(--ink-faint);white-space:nowrap">${e.time}</span></div>`).join('') || `<div style="color:var(--ink-faint);padding:20px;text-align:center;font-size:13px">Aucune activité récente.</div>`}
      </div>
    </div>
  </div>
  <style>@media(min-width:1000px){.control-grid{grid-template-columns:1fr 1fr !important}}</style>`;
}
 
/* ---- CAMERAS ---- */
const camFields = [
  {key:'nom',label:'Nom de la caméra',type:'text',required:true,full:true},
  {key:'zone',label:'Zone',type:'text'},
  {key:'statut',label:'Statut',type:'select',options:['En ligne','Hors ligne']},
  {key:'resolution',label:'Résolution',type:'select',options:['720p','1080p','4K']},
  {key:'ip',label:'Adresse IP',type:'text'},
];
function viewCameras(){
  const online = DB.cameras.filter(c=>c.statut==='En ligne').length;
  return `
  ${sectionHead('Supervision Vidéo', `${DB.cameras.length} caméras · ${online} en ligne`, `<button class="btn btn-primary btn-sm" onclick="camAdd()">${I.plus(13)}Ajouter caméra</button>`)}
  <div class="banner banner-info" style="margin-bottom:18px">${I.radio(15)}<span>Module de supervision vidéo — la connexion aux flux en direct nécessite la configuration du système NVR sur le réseau local.</span></div>
  <div class="card-grid">
    ${DB.cameras.map(c=>`
    <div class="tile ${c.statut==='Hors ligne'?'alert':''}">
      <div class="cam-preview">
        ${c.statut==='En ligne'?`<div style="display:flex;flex-direction:column;align-items:center;gap:8px;color:#7B84B8">${I.camera(28)}<div style="display:flex;align-items:center;gap:6px;font-family:var(--font-mono);font-size:11px;color:#33C08D"><span style="width:6px;height:6px;border-radius:50%;background:#33C08D"></span>LIVE · ${c.resolution}</div></div>`
        :`<div style="display:flex;flex-direction:column;align-items:center;gap:8px;color:#F0685F">${I.wifiOff(24)}<span style="font-family:var(--font-mono);font-size:11px">HORS LIGNE</span></div>`}
        <span style="position:absolute;top:8px;left:8px;font-family:var(--font-mono);font-size:9.5px;color:#ffffffa0;background:#00000060;padding:2px 6px;border-radius:5px">${c.id}</span>
      </div>
      <div><div class="td-strong" style="font-size:13px">${esc(c.nom)}</div><div style="font-size:11px;color:var(--ink-dim)">${esc(c.zone)} · IP ${c.ip}</div></div>
      <div style="display:flex;justify-content:space-between;align-items:center">${badge(c.statut)}<div class="row-actions"><button onclick="camEdit('${c.id}')">${I.edit(14)}</button><button class="danger" onclick="camDelete('${c.id}')">${I.trash(14)}</button></div></div>
    </div>`).join('')}
  </div>`;
}
function camAdd(){ crudAdd(DB.cameras, camFields, 'CAM', 'Caméras', 'cameras', {}, 'Ajouter une caméra'); }
function camEdit(id){ const row=DB.cameras.find(c=>c.id===id); crudEdit(DB.cameras, camFields, row, 'Caméras'); }
function camDelete(id){ const row=DB.cameras.find(c=>c.id===id); crudDelete(DB.cameras,row,'Caméras','nom'); }
 
/* ---- REPORTS ---- */
function viewReports(){
  const items = [
    {icon:I.bar(20),title:'Rapport journalier',desc:'CA, commandes, encaissements du jour',data:()=>DB.orders,name:'rapport_journalier'},
    {icon:I.trendUp(20),title:'Rapport hebdomadaire',desc:'Synthèse de la semaine',data:()=>DB.transactions,name:'rapport_hebdo'},
    {icon:I.calendar(20),title:'Rapport mensuel',desc:'CA, bénéfices, performances',data:()=>DB.revenueHistory,name:'rapport_mensuel'},
    {icon:I.users(20),title:'Rapport clients',desc:'Acquisition, fidélité, recouvrement',data:()=>DB.clients,name:'rapport_clients'},
    {icon:I.pkg(20),title:'Rapport inventaire',desc:'Stocks, consommations, fournisseurs',data:()=>DB.inventory,name:'rapport_inventaire'},
    {icon:I.cpu(20),title:'Rapport machines',desc:'Cycles, pannes, disponibilité',data:()=>DB.machines,name:'rapport_machines'},
    {icon:I.userCheck(20),title:'Rapport RH',desc:'Présences, absences, rendement',data:()=>DB.staff,name:'rapport_rh'},
    {icon:I.dollar(20),title:'Rapport financier',desc:'Encaissements, dépenses, caisse',data:()=>DB.transactions,name:'rapport_financier'},
  ];
  window.__reportItems = items;
  return `
  ${sectionHead('Rapports & Analyses', 'Générez et exportez vos rapports de gestion', '')}
  <div class="card-grid">
    ${items.map((r,idx)=>`
    <div class="tile report-tile">
      <div class="kpi-icon" style="background:var(--primary-soft);color:var(--primary)">${r.icon}</div>
      <div><div class="td-strong" style="font-size:13.5px">${r.title}</div><div style="font-size:11.5px;color:var(--ink-dim);margin-top:3px;line-height:1.5">${r.desc}</div></div>
      <div style="display:flex;gap:7px"><button class="btn btn-secondary btn-sm" style="flex:1" onclick="window.print()">${I.eye(11)}Aperçu</button><button class="btn btn-ghost btn-sm" onclick="exportCSV(window.__reportItems[${idx}].data(), window.__reportItems[${idx}].name)">${I.download(11)}CSV</button></div>
    </div>`).join('')}
  </div>`;
}
 
/* ---- SECURITY ---- */
const userFields = [
  {key:'nom',label:'Nom complet',type:'text',required:true,full:true},
  {key:'role',label:'Rôle',type:'text',required:true},
  {key:'acces',label:'Modules accessibles',type:'text',full:true},
  {key:'actif',label:'Compte actif',type:'checkbox'},
];
function viewSecurity(){
  return `
  ${sectionHead('Sécurité & Accès', 'Gestion des utilisateurs, rôles et permissions', `<button class="btn btn-primary btn-sm" onclick="userAdd()">${I.plus(13)}Ajouter utilisateur</button>`)}
  <div class="table-wrap"><div class="table-scroll"><table><thead><tr><th>Utilisateur</th><th>Rôle</th><th>Modules accessibles</th><th>Dernière connexion</th><th>Statut</th><th></th></tr></thead><tbody>
    ${DB.users.map((u,idx)=>`<tr>
      <td><div class="name-cell"><div class="avatar-sm" style="${u.actif?'':'opacity:.5'}">${esc(u.nom[0])}</div><span class="td-strong">${esc(u.nom)}</span></div></td>
      <td>${esc(u.role)}</td><td style="font-size:11.5px;color:var(--ink-dim)">${esc(u.acces)}</td><td class="td-mono">${esc(u.lastLogin)}</td>
      <td>${u.actif?`<span style="color:var(--success);font-size:11.5px;font-weight:600;display:flex;align-items:center;gap:4px">${I.checkCircle(12)}Actif</span>`:`<span style="color:var(--ink-faint);font-size:11.5px;font-weight:600;display:flex;align-items:center;gap:4px">${I.x(12)}Inactif</span>`}</td>
      <td><div class="row-actions"><button onclick="userEdit(${idx})">${I.edit(14)}</button><button onclick="userEdit(${idx})">${I.lock(14)}</button></div></td>
    </tr>`).join('')}
  </tbody></table></div></div>`;
}
function userAdd(){ crudAdd(DB.users, userFields, null, 'Sécurité', 'security', {lastLogin:nowFR()}, 'Ajouter utilisateur'); }
function userEdit(idx){ crudEdit(DB.users, userFields, DB.users[idx], 'Sécurité', `Modifier — ${DB.users[idx].nom}`); }
 
/* ============================= INIT ============================= */
async function init(){
  await loadDB();
  const savedTheme = localStorage.getItem('psj-theme-pref');
  if(savedTheme==='dark'){ state.theme='dark'; document.documentElement.setAttribute('data-theme','dark'); $('#themeIconSun').classList.add('hidden'); $('#themeIconMoon').classList.remove('hidden'); }
  renderNav();
  renderView();
  tick(); setInterval(tick,1000);
  $('#loadingScreen').classList.add('hidden');
  $('#app').classList.remove('hidden');
}
window.addEventListener('resize',()=>{ if(window.innerWidth>=1024) closeSidebar(); });
init();
</script>
</body>
</html>
 
