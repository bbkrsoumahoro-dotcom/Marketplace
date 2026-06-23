<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEXUS MARKETPLACE — Premium + Paiements</title>
<style>
/* ============================================================
   NEXUS MARKETPLACE v4.0 — Premium + Paiements CI
   ============================================================ */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');

:root {
  --bg-deep: #050508; --bg-primary: #07070e; --bg-secondary: #0b0b18; --bg-tertiary: #111122;
  --bg-card: rgba(16,16,34,0.75); --bg-card-hover: rgba(24,24,48,0.92); --bg-glass: rgba(255,255,255,0.03);
  --text-primary: #f0f0f5; --text-secondary: #9999bb; --text-muted: #555577;
  --accent: #ff6600; --accent-dark: #cc5200; --accent-glow: rgba(255,102,0,0.35); --accent-glow-soft: rgba(255,102,0,0.12);
  --green: #00ff88; --green-dim: rgba(0,255,136,0.12); --orange: #ff8800; --red: #ff2244; --purple: #7c3aed; --gold: #ffd700;
  --border: rgba(255,255,255,0.06); --border-light: rgba(255,255,255,0.1);
  --radius-sm: 8px; --radius-md: 14px; --radius-lg: 22px;
  --transition: 0.35s cubic-bezier(0.4,0,0.2,1); --transition-bounce: 0.5s cubic-bezier(0.34,1.56,0.64,1);
}

[data-theme="light"] {
  --bg-deep: #f0f0f5; --bg-primary: #fff; --bg-secondary: #f5f5fa; --bg-tertiary: #e8e8f0;
  --bg-card: rgba(255,255,255,0.85); --text-primary: #111; --text-secondary: #555; --text-muted: #888;
  --border: rgba(0,0,0,0.08); --border-light: rgba(0,0,0,0.12);
}

*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'Inter','Segoe UI',system-ui,sans-serif;background:var(--bg-deep);color:var(--text-primary);min-height:100vh;overflow-x:hidden;-webkit-font-smoothing:antialiased}
::-webkit-scrollbar{width:4px}
::-webkit-scrollbar-track{background:var(--bg-deep)}
::-webkit-scrollbar-thumb{background:linear-gradient(180deg,var(--accent),var(--purple));border-radius:4px}

body::before{content:'';position:fixed;top:0;left:0;width:100%;height:100%;background:radial-gradient(ellipse at 15% 30%,rgba(124,58,237,0.05) 0%,transparent 55%),radial-gradient(ellipse at 85% 20%,rgba(255,102,0,0.04) 0%,transparent 50%);pointer-events:none;z-index:0}

.layout{display:grid;grid-template-columns:240px 1fr;min-height:100vh;position:relative;z-index:1}

.sidebar{background:linear-gradient(180deg,var(--bg-secondary),var(--bg-tertiary));border-right:1px solid var(--border);position:sticky;top:0;height:100vh;overflow:hidden;display:flex;flex-direction:column;transition:width var(--transition);width:240px}
.sidebar.collapsed{width:64px}
.sidebar.collapsed:hover{width:240px}
.sidebar-inner{padding:20px 12px;display:flex;flex-direction:column;gap:1px;height:100%;overflow-y:auto;overflow-x:hidden}
.sidebar.collapsed .sidebar-inner{padding:20px 8px}

.logo-wrap{display:flex;align-items:center;gap:12px;padding:4px 10px;margin-bottom:22px;overflow:hidden;white-space:nowrap;min-height:40px}
.logo-icon-bg{flex-shrink:0;width:34px;height:34px;background:linear-gradient(135deg,var(--accent),var(--purple));border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;box-shadow:0 0 24px var(--accent-glow)}
.logo-text{font-size:16px;font-weight:800;letter-spacing:-0.5px}
.logo-text .accent{color:var(--accent)}
.logo-text .dim{color:var(--text-muted)}

.nav-item{display:flex;align-items:center;gap:12px;padding:10px 14px;border-radius:var(--radius-md);cursor:pointer;font-size:12px;font-weight:500;color:var(--text-muted);transition:var(--transition);position:relative;overflow:hidden;white-space:nowrap;user-select:none}
.nav-item:hover{color:var(--text-primary);background:var(--bg-glass)}
.nav-item.active{color:var(--accent);background:linear-gradient(135deg,rgba(255,102,0,0.1),rgba(124,58,237,0.06));border:1px solid rgba(255,102,0,0.12)}
.nav-item.active .nav-slider{position:absolute;left:-14px;top:50%;transform:translateY(-50%);width:3px;height:20px;background:linear-gradient(180deg,var(--accent),var(--purple));border-radius:0 4px 4px 0;box-shadow:0 0 12px var(--accent-glow);animation:slideIn 0.4s ease}
@keyframes slideIn{from{height:0;opacity:0}to{height:20px;opacity:1}}
.nav-icon{font-size:15px;width:22px;text-align:center;flex-shrink:0}
.nav-label{overflow:hidden;text-overflow:ellipsis}
.sidebar.collapsed .nav-label,.sidebar.collapsed .logo-text,.sidebar.collapsed .sidebar-footer-text{opacity:0;width:0;display:none}
.sidebar.collapsed .logo-wrap{justify-content:center;padding:4px 0}
.sidebar.collapsed .nav-item{justify-content:center;padding:10px 0}
.sidebar.collapsed .nav-item.active .nav-slider{left:-8px}
.sidebar.collapsed:hover .nav-label,.sidebar.collapsed:hover .logo-text,.sidebar.collapsed:hover .sidebar-footer-text{display:inline;opacity:1;width:auto}
.sidebar.collapsed:hover .nav-item{justify-content:flex-start;padding:10px 14px}
.sidebar.collapsed:hover .logo-wrap{justify-content:flex-start;padding:4px 10px}
.sidebar.collapsed:hover .nav-item.active .nav-slider{left:-14px}

.sidebar-toggle{position:absolute;top:20px;right:-14px;width:28px;height:28px;background:var(--bg-card);border:1px solid var(--border-light);border-radius:50%;display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:12px;color:var(--text-muted);transition:var(--transition);z-index:10;backdrop-filter:blur(10px)}
.sidebar-toggle:hover{background:var(--accent);color:#000;transform:scale(1.1)}
.sidebar.collapsed .sidebar-toggle{transform:rotate(180deg)}

.badge-cart{background:linear-gradient(135deg,var(--accent),var(--red));color:#fff;border-radius:50%;padding:1px 6px;font-size:9px;font-weight:800;margin-left:auto;min-width:20px;text-align:center;box-shadow:0 0 12px var(--accent-glow);flex-shrink:0}
.sidebar-footer{margin-top:auto;padding:12px 14px 8px;border-top:1px solid var(--border);font-size:8px;color:var(--text-muted);text-align:center;overflow:hidden;white-space:nowrap}
.version-badge{display:inline-block;padding:2px 8px;border-radius:10px;background:var(--accent-glow-soft);color:var(--accent);font-weight:700;font-size:7px;margin-bottom:4px}

.main{padding:20px 28px;position:relative;z-index:1}

.topbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:20px;gap:16px;flex-wrap:wrap}
.topbar-left{display:flex;align-items:center;gap:12px}
.topbar-left h1{font-size:20px;font-weight:800;background:linear-gradient(135deg,var(--text-primary) 30%,var(--accent) 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;letter-spacing:-0.5px}
.topbar-right{display:flex;align-items:center;gap:10px;flex-wrap:wrap}

.search-box{display:flex;align-items:center;background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-lg);padding:7px 16px;gap:8px;transition:var(--transition);backdrop-filter:blur(16px);min-width:240px}
.search-box:focus-within{border-color:var(--accent);box-shadow:0 0 20px var(--accent-glow-soft)}
.search-box input{background:none;border:none;color:var(--text-primary);font-size:12px;outline:none;width:100%;font-family:inherit}
.search-box input::placeholder{color:var(--text-muted)}

.stats-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:10px;margin-bottom:16px}
.stat-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-md);padding:14px;backdrop-filter:blur(16px);transition:var(--transition)}
.stat-card:hover{border-color:var(--border-light);transform:translateY(-2px)}
.stat-card .stat-value{font-size:22px;font-weight:800;letter-spacing:-0.5px}
.stat-card .stat-label{font-size:9px;color:var(--text-muted);margin-top:2px;font-weight:500;text-transform:uppercase;letter-spacing:0.5px}

.card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-md);padding:14px;backdrop-filter:blur(16px);transition:var(--transition)}
.card:hover{border-color:var(--border-light)}

.tabs{display:flex;gap:4px;margin-bottom:12px;flex-wrap:wrap}
.tabs button{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-lg);padding:5px 14px;color:var(--text-muted);cursor:pointer;font-size:10px;font-weight:500;transition:var(--transition);font-family:inherit}
.tabs button:hover{color:var(--text-primary)}
.tabs button.active{background:linear-gradient(135deg,var(--accent),var(--accent-dark));color:#000;border-color:var(--accent);font-weight:700}

.grid-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
.grid-header .grid-info{font-size:10px;color:var(--text-muted)}
.grid-toggle{display:flex;gap:3px;background:var(--bg-card);border-radius:var(--radius-sm);padding:3px;border:1px solid var(--border)}
.grid-toggle button{background:none;border:none;color:var(--text-muted);padding:3px 8px;border-radius:4px;cursor:pointer;font-size:12px;transition:var(--transition)}
.grid-toggle button.active{background:var(--accent);color:#000}

.grid-prod{display:grid;gap:10px;transition:var(--transition)}
.grid-prod.grid{grid-template-columns:repeat(auto-fill,minmax(200px,1fr))}
.grid-prod.list{grid-template-columns:1fr}

.prod-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-md);padding:12px;transition:var(--transition);position:relative;overflow:hidden;backdrop-filter:blur(12px);cursor:pointer}
.prod-card:hover{border-color:var(--accent);transform:translateY(-3px);box-shadow:0 12px 40px rgba(0,0,0,0.4),0 0 24px var(--accent-glow-soft)}
.prod-card::after{content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;background:linear-gradient(90deg,transparent,rgba(255,255,255,0.03),transparent);transition:0.6s;pointer-events:none}
.prod-card:hover::after{left:100%}

.img-wrap{width:100%;height:140px;border-radius:var(--radius-sm);overflow:hidden;background:var(--bg-secondary);position:relative}
.img-wrap img{width:100%;height:100%;object-fit:cover;transition:transform 0.5s ease}
.prod-card:hover .img-wrap img{transform:scale(1.05)}
.badge-stock{position:absolute;top:6px;right:6px;padding:3px 10px;border-radius:20px;font-size:7px;font-weight:700;text-transform:uppercase;z-index:2;backdrop-filter:blur(8px)}
.badge-stock.low{background:rgba(255,136,0,0.85);color:#000}
.badge-stock.out{background:rgba(255,34,68,0.85);color:#fff}
.badge-stock.ok{display:none}

.prod-card .name{font-size:12px;font-weight:600;margin-top:8px;line-height:1.3}
.prod-card .seller-name{font-size:9px;color:var(--text-muted);margin-top:2px}
.prod-card .price{font-size:18px;font-weight:800;color:var(--accent);margin-top:3px;letter-spacing:-0.5px}
.prod-card .desc{font-size:10px;color:var(--text-secondary);margin-top:3px;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;line-height:1.4}
.prod-card .actions{display:flex;gap:4px;margin-top:8px}
.prod-card .actions button{flex:1;font-size:9px;padding:4px 8px}

.grid-prod.list .prod-card{display:flex;gap:14px;align-items:center}
.grid-prod.list .prod-card .img-wrap{width:80px;height:80px;flex-shrink:0}
.grid-prod.list .prod-card .name{margin-top:0}
.grid-prod.list .prod-card .price{margin-top:0}
.grid-prod.list .prod-card .desc{-webkit-line-clamp:1}
.grid-prod.list .prod-card .actions{margin-top:0;min-width:140px}

.btn{padding:7px 14px;border:none;border-radius:var(--radius-sm);cursor:pointer;font-size:10px;font-weight:600;transition:var(--transition);display:inline-flex;align-items:center;gap:5px;font-family:inherit;text-decoration:none}
.btn-primary{background:linear-gradient(135deg,var(--accent),#e05500);color:#000;box-shadow:0 3px 12px var(--accent-glow-soft)}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 6px 20px var(--accent-glow)}
.btn-success{background:linear-gradient(135deg,var(--green),#00cc6a);color:#000;box-shadow:0 3px 12px var(--green-dim)}
.btn-success:hover{transform:translateY(-1px)}
.btn-danger{background:linear-gradient(135deg,var(--red),#cc0033);color:#fff}
.btn-warning{background:linear-gradient(135deg,var(--orange),#cc6600);color:#fff}
.btn-ghost{background:var(--bg-glass);color:var(--text-secondary);border:1px solid var(--border)}
.btn-ghost:hover{background:var(--bg-card-hover);color:var(--text-primary)}
.btn-sm{padding:4px 10px;font-size:9px;border-radius:6px}
.btn-lg{padding:10px 20px;font-size:12px}
.btn-block{width:100%;justify-content:center}

.input{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-sm);padding:8px 12px;color:var(--text-primary);font-size:11px;width:100%;transition:var(--transition);font-family:inherit}
.input:focus{outline:none;border-color:var(--accent);box-shadow:0 0 16px var(--accent-glow-soft)}
.textarea{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-sm);padding:8px 12px;color:var(--text-primary);font-size:11px;width:100%;resize:vertical;transition:var(--transition);font-family:inherit;min-height:60px}
.textarea:focus{outline:none;border-color:var(--accent)}
select.input{appearance:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' fill='%238888aa'%3E%3Cpath d='M6 8L1 3h10z'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 12px center;padding-right:32px}
.input-group{margin-bottom:10px}
.input-group label{display:block;font-size:10px;color:var(--text-secondary);margin-bottom:3px;font-weight:500}

.cart-item{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-md);padding:12px;margin-bottom:8px;display:flex;gap:12px;align-items:center;transition:var(--transition);backdrop-filter:blur(12px)}
.cart-item:hover{border-color:var(--border-light)}
.cart-item img{width:50px;height:50px;object-fit:cover;border-radius:var(--radius-sm);flex-shrink:0}
.cart-item .info{flex:1;min-width:0}
.cart-item .info .name{font-size:12px;font-weight:600}
.cart-item .info .price{font-size:14px;color:var(--accent);font-weight:700;margin-top:2px}
.cart-item .qty{display:flex;align-items:center;gap:6px;background:var(--bg-secondary);border-radius:var(--radius-lg);padding:2px;border:1px solid var(--border)}
.cart-item .qty button{width:26px;height:26px;border-radius:50%;border:none;background:var(--bg-card);color:var(--text-primary);cursor:pointer;font-size:13px;font-weight:700;transition:var(--transition)}
.cart-item .qty button:hover{background:var(--accent);color:#000}
.cart-item .qty span{font-size:12px;font-weight:700;min-width:22px;text-align:center}

.cart-summary{margin-top:12px;padding:18px;background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-md);backdrop-filter:blur(16px)}
.cart-summary .total-row{display:flex;justify-content:space-between;align-items:center}
.cart-summary .total-label{font-size:12px;color:var(--text-secondary)}
.cart-summary .total-price{font-size:24px;font-weight:800;color:var(--accent);letter-spacing:-0.5px}

.order-card{background:var(--bg-card);border:1px solid var(--border);border-radius:var(--radius-md);padding:14px;margin-bottom:8px;transition:var(--transition);backdrop-filter:blur(12px)}
.order-card:hover{border-color:var(--border-light)}
.order-card .order-header{display:flex;justify-content:space-between;align-items:center}
.order-card .order-id{font-size:11px;font-weight:700;color:var(--accent)}
.order-card .order-date{font-size:10px;color:var(--text-muted)}
.order-card .order-items{font-size:10px;color:var(--text-secondary);margin:6px 0;line-height:1.5}
.order-card .order-footer{display:flex;justify-content:space-between;align-items:center;margin-top:4px}
.order-card .order-status{padding:3px 12px;border-radius:20px;font-size:8px;font-weight:700;text-transform:uppercase;background:var(--green-dim);color:var(--green)}
.order-card .order-total{font-size:16px;font-weight:700;color:var(--accent)}
.order-card .order-meta{font-size:8px;color:var(--text-muted);margin-top:3px}

.modal-overlay{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.7);backdrop-filter:blur(12px);z-index:1000;display:none;align-items:center;justify-content:center}
.modal-overlay.show{display:flex}
.modal{background:var(--bg-card);border:1px solid var(--border-light);border-radius:var(--radius-lg);padding:24px;max-width:520px;width:92%;max-height:85vh;overflow-y:auto;box-shadow:0 24px 80px rgba(0,0,0,0.6);animation:scaleIn 0.3s cubic-bezier(0.34,1.56,0.64,1);backdrop-filter:blur(24px)}
@keyframes scaleIn{from{opacity:0;transform:scale(0.88)}to{opacity:1;transform:scale(1)}}
.modal h3{font-size:16px;font-weight:700;margin-bottom:14px}
.modal hr{border:none;border-top:1px solid var(--border);margin:12px 0}

.toast{position:fixed;bottom:24px;right:24px;background:var(--bg-card);border:1px solid var(--border-light);color:var(--text-primary);padding:12px 18px;border-radius:var(--radius-md);font-size:11px;font-weight:500;z-index:2000;opacity:0;transform:translateY(16px) scale(0.95);transition:var(--transition-bounce);pointer-events:none;backdrop-filter:blur(24px);box-shadow:0 8px 32px rgba(0,0,0,0.4);display:flex;align-items:center;gap:8px}
.toast.show{opacity:1;transform:translateY(0) scale(1);pointer-events:auto}

.empty-state{text-align:center;padding:50px 20px;color:var(--text-muted)}
.empty-state .empty-icon{font-size:40px;margin-bottom:12px;opacity:0.4}
.empty-state .empty-title{font-size:14px;font-weight:700;color:var(--text-secondary);margin-bottom:4px}
.empty-state .empty-desc{font-size:11px}

.image-preview{margin-top:4px;height:80px;background:var(--bg-secondary);border-radius:var(--radius-sm);display:flex;align-items:center;justify-content:center;font-size:9px;color:var(--text-muted);overflow:hidden;border:1px dashed var(--border)}
.image-preview img{width:100%;height:100%;object-fit:cover}

.flex{display:flex;gap:8px;align-items:center}
.flex-wrap{flex-wrap:wrap}
.flex-col{flex-direction:column}
.gap-4{gap:4px}
.mb-4{margin-bottom:4px}
.mb-6{margin-bottom:6px}
.mb-8{margin-bottom:8px}
.mt-6{margin-top:6px}
.mt-8{margin-top:8px}
.text-center{text-align:center}
.text-muted{color:var(--text-muted)}
.font-sm{font-size:10px}
.fw-700{font-weight:700}
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px}
.table{width:100%;border-collapse:collapse;font-size:10px}
.table th,.table td{padding:6px 8px;text-align:left;border-bottom:1px solid var(--border)}
.table th{color:var(--text-muted);font-weight:600;font-size:9px;text-transform:uppercase}

@media(max-width:768px){
  .layout{grid-template-columns:1fr}
  .sidebar{position:fixed;bottom:0;top:auto;height:auto;flex-direction:row;overflow-x:auto;border-top:1px solid var(--border);border-right:none;width:100%;backdrop-filter:blur(24px);background:rgba(10,10,15,0.94)}
  .sidebar .sidebar-inner{flex-direction:row;padding:4px 6px;overflow-x:auto;gap:1px;width:100%}
  .sidebar .logo-wrap,.sidebar .sidebar-footer,.sidebar .sidebar-toggle{display:none}
  .sidebar .nav-item{white-space:nowrap;flex-shrink:0;padding:6px 8px;font-size:10px;justify-content:center}
  .sidebar .nav-item .nav-label{display:none}
  .sidebar .nav-item.active .nav-slider{display:none}
  .main{padding:12px;padding-bottom:60px}
  .stats-grid,.grid-2,.grid-3{grid-template-columns:repeat(2,1fr)}
  .grid-prod.grid{grid-template-columns:repeat(2,1fr)}
}
@media(max-width:480px){
  .stats-grid,.grid-2,.grid-3,.grid-prod.grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<div class="layout">
  <nav class="sidebar" id="sidebar">
    <div class="sidebar-toggle" id="sidebarToggle">◀</div>
    <div class="sidebar-inner">
      <div class="logo-wrap"><div class="logo-icon-bg">⟡</div><span class="logo-text"><span class="accent">NEXUS</span><span class="dim">MARKET</span></span></div>
      <div class="nav-item active" data-page="shop"><span class="nav-slider"></span><span class="nav-icon">🏪</span><span class="nav-label">Boutique</span></div>
      <div class="nav-item" data-page="cart"><span class="nav-slider"></span><span class="nav-icon">🛒</span><span class="nav-label">Panier</span><span class="badge-cart" id="cartCount">0</span></div>
      <div class="nav-item" data-page="orders"><span class="nav-slider"></span><span class="nav-icon">📦</span><span class="nav-label">Commandes</span></div>
      <div class="nav-item" data-page="sell"><span class="nav-slider"></span><span class="nav-icon">💰</span><span class="nav-label">Vendre</span></div>
      <div class="nav-item" data-page="whatsapp"><span class="nav-slider"></span><span class="nav-icon">💬</span><span class="nav-label">WhatsApp</span></div>
      <div class="nav-item" data-page="pages"><span class="nav-slider"></span><span class="nav-icon">🔗</span><span class="nav-label">Mes Pages</span></div>
      <div class="nav-item" data-page="themes"><span class="nav-slider"></span><span class="nav-icon">🎨</span><span class="nav-label">Thèmes</span></div>
      <div class="nav-item" data-page="admin"><span class="nav-slider"></span><span class="nav-icon">⚙️</span><span class="nav-label">Admin</span></div>
      <div class="sidebar-footer"><div class="version-badge">v4.0 PRO</div><div class="sidebar-footer-text">NEXUS MARKETPLACE</div></div>
    </div>
  </nav>
  <main class="main" id="mainContent"></main>
</div>

<div class="modal-overlay" id="modalOverlay"><div class="modal" id="modalContent"></div></div>
<div class="toast" id="toast"><span id="toastIcon">⟡</span><span id="toastMsg">Message</span></div>

<script>
// ============================================================
// NEXUS MARKETPLACE v4.0 — CORRIGÉ ET OPTIMISÉ
// ============================================================
const STATE = {
  products: [
    {id:1,name:"Rapport Cybersécurité CI 2025",desc:"Analyse complète des cyberattaques en Côte d'Ivoire.",price:15000,category:"rapports",image:"https://placehold.co/400x260/1a1a28/00ff88?text=Rapport+CI",stock:50,seller:"NEXUS Intel"},
    {id:2,name:"Pack OSINT Pro",desc:"120+ outils OSINT avec guides.",price:25000,category:"outils",image:"https://placehold.co/400x260/1a1a28/ff6600?text=OSINT+Pro",stock:30,seller:"NEXUS Intel"},
    {id:3,name:"Formation Ethical Hacking",desc:"200h de contenu certifiant.",price:45000,category:"formations",image:"https://placehold.co/400x260/1a1a28/ff2244?text=Hacking",stock:100,seller:"NEXUS Academy"},
    {id:4,name:"Base CVEs CI",desc:"Vulnérabilités affectant la Côte d'Ivoire.",price:20000,category:"données",image:"https://placehold.co/400x260/1a1a28/0088ff?text=CVE+CI",stock:25,seller:"NEXUS Intel"},
    {id:5,name:"T-Shirt NEXUS",desc:"Édition limitée premium.",price:8500,category:"merch",image:"https://placehold.co/400x260/1a1a28/ffffff?text=NEXUS",stock:200,seller:"NEXUS Store"},
    {id:6,name:"Script Scan RSS Auto",desc:"Python/JS pour scan RSS automatisé.",price:12000,category:"outils",image:"https://placehold.co/400x260/1a1a28/00ff88?text=Script+RSS",stock:80,seller:"NEXUS Dev"},
    {id:7,name:"Template Dashboard",desc:"Interface sombre style NEXUS.",price:18000,category:"outils",image:"https://placehold.co/400x260/1a1a28/ff6600?text=Dashboard",stock:60,seller:"NEXUS Dev"},
    {id:8,name:"Abonnement Premium",desc:"Briefs et alertes en temps réel.",price:9500,category:"abonnements",image:"https://placehold.co/400x260/1a1a28/ff8800?text=Premium",stock:999,seller:"NEXUS Intel"}
  ],
  cart: [], orders: [], nextId: 9,
  whatsapp: {phoneId:"",token:"",active:false,number:"+2250101020304"},
  pages: [],
  theme: "dark",
  accentColor: "#ff6600",
  fontSize: "14px",
  auth: {
    connected: false,
    user: null,
    users: [
      {id:1,login:"admin",pass:"admin2025",nom:"Admin NEXUS",role:"Super Admin"}
    ]
  }
}

let currentPage = 'shop', categoryFilter = 'all', viewMode = 'grid', searchQuery = '', sidebarCollapsed = false

function escHtml(s){if(!s)return '';return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;')}
function formatPrice(p){return Number(p).toLocaleString('fr-FR',{minimumFractionDigits:0,maximumFractionDigits:0})+' FCFA'}
function formatDate(d){if(!d)return '';try{return new Date(d).toLocaleDateString('fr-FR',{day:'numeric',month:'short',year:'numeric',hour:'2-digit',minute:'2-digit'})}catch(e){return d}}
function showToast(msg,type){const t=document.getElementById('toast'),icon=document.getElementById('toastIcon'),txt=document.getElementById('toastMsg');const icons={success:'✅',error:'❌',info:'⟡',warning:'⚠️',pay:'💳'};icon.textContent=icons[type]||'⟡';txt.textContent=msg;t.className='toast show';clearTimeout(t._timeout);t._timeout=setTimeout(()=>t.classList.remove('show'),3200)}
function openModal(title,content){const overlay=document.getElementById('modalOverlay');document.getElementById('modalContent').innerHTML=`<div style="display:flex;justify-content:space-between;align-items:start;margin-bottom:14px"><h3>${title}</h3><button class="btn btn-ghost btn-sm" onclick="closeModal()" style="font-size:16px">✕</button></div>${content}`;overlay.classList.add('show');overlay.onclick=function(e){if(e.target===this)closeModal()}}
function closeModal(){document.getElementById('modalOverlay').classList.remove('show')}
function toggleSidebar(){sidebarCollapsed=!sidebarCollapsed;document.getElementById('sidebar').classList.toggle('collapsed',sidebarCollapsed);localStorage.setItem('nexus-market-sidebar',sidebarCollapsed?'collapsed':'')}
function updateCartBadge(){const c=document.getElementById('cartCount');if(c)c.textContent=STATE.cart.reduce((a,i)=>a+i.qty,0)}
function reRenderCurrent(){showPage(currentPage)}

function checkAuth(){
  if(STATE.auth.connected) return true
  openModal('🔐 Connexion Admin',`
    <div class="input-group"><label>Identifiant</label><input class="input" id="authLogin" placeholder="admin" value="admin"></div>
    <div class="input-group"><label>Mot de passe</label><input class="input" id="authPass" type="password" placeholder="••••••" value="admin2025"></div>
    <button class="btn btn-primary btn-block mt-6" onclick="login()">🔐 Se connecter</button>
    <div style="font-size:9px;color:var(--text-muted);text-align:center;margin-top:8px">admin / admin2025</div>
  `)
  return false
}
function login(){
  const l=document.getElementById('authLogin')?.value.trim(),p=document.getElementById('authPass')?.value.trim()
  const user=STATE.auth.users.find(u=>u.login===l&&u.pass===p)
  if(user){STATE.auth.connected=true;STATE.auth.user=user;saveState();closeModal();showToast(`✅ Bienvenue ${user.nom}`,'success');reRenderCurrent()}
  else showToast('❌ Identifiants incorrects','error')
}
function logout(){STATE.auth.connected=false;STATE.auth.user=null;saveState();showToast('🔌 Déconnecté','info');reRenderCurrent()}

function showPage(page){
  currentPage = page
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'))
  const el = document.querySelector(`.nav-item[data-page="${page}"]`)
  if(el) el.classList.add('active')
  switch(page){
    case'shop': renderShop(); break
    case'cart': renderCart(); break
    case'orders': renderOrders(); break
    case'sell': renderSell(); break
    case'whatsapp': renderWhatsApp(); break
    case'pages': renderPages(); break
    case'themes': renderThemes(); break
    case'admin': renderAdmin(); break
    default: renderShop()
  }
}

// =================== SHOP ===================
function renderShop(){
  const app=document.getElementById('mainContent')
  let prods=STATE.products
  if(categoryFilter!=='all') prods=prods.filter(p=>p.category===categoryFilter)
  if(searchQuery.trim()){const q=searchQuery.trim().toLowerCase();prods=prods.filter(p=>p.name.toLowerCase().includes(q)||p.desc.toLowerCase().includes(q)||p.seller.toLowerCase().includes(q))}
  const cats={};STATE.products.forEach(p=>{cats[p.category]=true})
  app.innerHTML=`
    <div class="topbar"><div class="topbar-left"><h1>🏪 Boutique</h1><span class="font-sm text-muted">${prods.length} article${prods.length>1?'s':''}</span></div><div class="topbar-right"><div class="search-box"><span style="font-size:11px">🔍</span><input type="text" placeholder="Rechercher..." value="${escHtml(searchQuery)}" oninput="searchQuery=this.value;renderShop()"></div></div></div>
    <div class="tabs"><button class="${categoryFilter==='all'?'active':''}" onclick="setCat('all')">📋 Tout</button>${Object.keys(cats).map(c=>`<button class="${categoryFilter===c?'active':''}" onclick="setCat('${c}')">${c.charAt(0).toUpperCase()+c.slice(1)}</button>`).join('')}</div>
    <div class="grid-header"><span class="grid-info">${prods.length} résultat${prods.length>1?'s':''}</span><div class="grid-toggle"><button class="${viewMode==='grid'?'active':''}" onclick="viewMode='grid';renderShop()">▦</button><button class="${viewMode==='list'?'active':''}" onclick="viewMode='list';renderShop()">☰</button></div></div>
    <div class="grid-prod ${viewMode}">${prods.length?prods.map(p=>{const sc=p.stock<=0?'out':p.stock<10?'low':'ok',sl=p.stock<=0?'Épuisé':p.stock<10?'Stock limité':'';return`<div class="prod-card" onclick="viewProduct(${p.id})"><div class="img-wrap"><img src="${p.image}" alt="${escHtml(p.name)}" loading="lazy">${sl?`<div class="badge-stock ${sc}">${sl}</div>`:''}</div><div class="name">${escHtml(p.name)}</div><div class="seller-name">${escHtml(p.seller)}</div><div class="price">${formatPrice(p.price)}</div><div class="desc">${escHtml(p.desc)}</div><div class="actions"><button class="btn btn-primary btn-sm" onclick="event.stopPropagation();addToCart(${p.id})">🛒</button><button class="btn btn-ghost btn-sm" onclick="event.stopPropagation();viewProduct(${p.id})">Détails</button></div></div>`}).join(''):`<div class="empty-state" style="grid-column:1/-1"><div class="empty-icon">🔍</div><div class="empty-title">Aucun résultat</div></div>`}</div>`
}
function setCat(c){categoryFilter=c;renderShop()}

function viewProduct(id){
  const p=STATE.products.find(x=>x.id===id);if(!p)return
  const related=STATE.products.filter(x=>x.category===p.category&&x.id!==p.id).slice(0,4)
  const sl=p.stock<=0?'<span style="color:var(--red)">Épuisé</span>':p.stock<10?`<span style="color:var(--orange)">Plus que ${p.stock}</span>`:`<span style="color:var(--green)">En stock (${p.stock})</span>`
  openModal(escHtml(p.name),`<img src="${p.image}" style="width:100%;height:180px;object-fit:cover;border-radius:var(--radius-sm);margin-bottom:12px"><div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;font-size:11px;margin-bottom:12px"><div><span class="text-muted">Prix</span><br><span style="font-size:20px;font-weight:800;color:var(--accent)">${formatPrice(p.price)}</span></div><div><span class="text-muted">Stock</span><br>${sl}</div><div><span class="text-muted">Vendeur</span><br>${escHtml(p.seller)}</div><div><span class="text-muted">Catégorie</span><br>${p.category}</div></div><div style="font-size:11px;color:var(--text-secondary);line-height:1.6;margin-bottom:12px">${escHtml(p.desc)}</div><button class="btn btn-primary btn-block" onclick="addToCart(${p.id});closeModal()">🛒 Ajouter — ${formatPrice(p.price)}</button>`)
}

function addToCart(id){
  const p=STATE.products.find(x=>x.id===id);if(!p||p.stock<=0)return showToast(p?'Épuisé':'Erreur','error')
  const e=STATE.cart.find(x=>x.id===id)
  if(e){if(e.qty>=p.stock)return showToast('Stock max','warning');e.qty++}
  else STATE.cart.push({id:p.id,name:p.name,price:p.price,image:p.image,qty:1})
  saveState();updateCartBadge();showToast(`✓ ${p.name} ajouté`,'success')
}

function changeQty(id,d){
  const i=STATE.cart.find(x=>x.id===id);if(!i)return
  const p=STATE.products.find(x=>x.id===id)
  i.qty+=d;if(i.qty<=0){removeFromCart(id);return}
  if(p&&i.qty>p.stock){i.qty=p.stock;showToast('Stock max','warning')}
  saveState();updateCartBadge();renderCart()
}
function removeFromCart(id){const i=STATE.cart.find(x=>x.id===id);STATE.cart=STATE.cart.filter(x=>x.id!==id);saveState();updateCartBadge();showToast(`✕ ${i?i.name:'Article'} retiré`,'info');reRenderCurrent()}

// =================== CART ===================
function renderCart(){
  const app=document.getElementById('mainContent'),total=STATE.cart.reduce((a,i)=>a+i.price*i.qty,0)
  if(!STATE.cart.length)return app.innerHTML=`<div class="topbar"><div class="topbar-left"><h1>🛒 Panier</h1></div></div><div class="empty-state"><div class="empty-icon">🛒</div><div class="empty-title">Vide</div><div class="empty-desc">Ajoutez des articles depuis la boutique.</div><button class="btn btn-primary mt-6" onclick="showPage('shop')">🏪 Boutique</button></div>`
  app.innerHTML=`<div class="topbar"><div class="topbar-left"><h1>🛒 Panier</h1><span class="font-sm text-muted">${STATE.cart.reduce((a,i)=>a+i.qty,0)} article(s)</span></div><div class="topbar-right"><button class="btn btn-ghost btn-sm" onclick="if(confirm('Vider le panier ?')){STATE.cart=[];saveState();updateCartBadge();renderCart();showToast('🗑️ Vidé','info')}">🗑️ Vider</button></div></div>${STATE.cart.map(i=>`<div class="cart-item"><img src="${i.image}" alt="${escHtml(i.name)}" loading="lazy"><div class="info"><div class="name">${escHtml(i.name)}</div><div class="price">${formatPrice(i.price)}</div></div><div class="qty"><button onclick="changeQty(${i.id},-1)">−</button><span>${i.qty}</span><button onclick="changeQty(${i.id},1)">+</button></div><button class="btn btn-danger btn-sm" onclick="removeFromCart(${i.id})">✕</button></div>`).join('')}<div class="cart-summary"><div class="total-row"><span class="total-label">Total</span><span class="total-price">${formatPrice(total)}</span></div><button class="btn btn-success btn-block mt-6" onclick="showCheckout()">💳 Commander — ${formatPrice(total)}</button></div>`
}

// =================== CHECKOUT ===================
function showCheckout(){
  const total=STATE.cart.reduce((a,i)=>a+i.price*i.qty,0)
  const items=STATE.cart.map(i=>`<div style="display:flex;justify-content:space-between;font-size:10px;padding:4px 0;border-bottom:1px solid var(--border)"><span>${i.qty}x ${escHtml(i.name)}</span><span style="font-weight:600;color:var(--accent)">${formatPrice(i.price*i.qty)}</span></div>`).join('')
  openModal('💳 Paiement',`
    <div style="background:var(--bg-card);border-radius:var(--radius-sm);padding:12px;margin-bottom:12px;border:1px solid var(--border)"><div style="font-size:10px;font-weight:600;margin-bottom:6px">Récapitulatif</div>${items}<hr style="border-color:var(--border);margin:8px 0"><div style="display:flex;justify-content:space-between;font-size:14px;font-weight:700"><span>Total</span><span style="color:var(--accent)">${formatPrice(total)}</span></div></div>
    <div class="input-group"><label>Nom complet *</label><input class="input" id="checkName" placeholder="Votre nom"></div>
    <div class="input-group"><label>Téléphone *</label><input class="input" id="checkPhone" placeholder="+225 01 XX XX XX XX"></div>
    <div class="flex"><div class="input-group" style="flex:1"><label>Email</label><input class="input" id="checkEmail" placeholder="email@exemple.com"></div><div class="input-group" style="flex:1"><label>Paiement</label><select class="input" id="checkMethod"><option value="orange">Orange Money CI</option><option value="mtn">MTN MoMo CI</option><option value="wave">Wave CI</option><option value="paydunya">PayDunya (Carte)</option></select></div></div>
    <div class="input-group"><label>Adresse (optionnel)</label><textarea class="textarea" id="checkAddress" rows="2" placeholder="Abidjan, Cocody..."></textarea></div>
    <button class="btn btn-success btn-block mt-6" onclick="placeOrder()">💳 Payer ${formatPrice(total)}</button>
    <div style="font-size:8px;color:var(--text-muted);text-align:center;margin-top:6px">🔒 Paiement sécurisé · Orange Money / MTN / Wave / Carte</div>
  `)
}

function placeOrder(){
  const name=document.getElementById('checkName')?.value.trim(),phone=document.getElementById('checkPhone')?.value.trim()
  const email=document.getElementById('checkEmail')?.value.trim(),method=document.getElementById('checkMethod')?.value,address=document.getElementById('checkAddress')?.value.trim()
  if(!name||!phone)return showToast('❌ Nom et téléphone requis','error')
  if(phone.replace(/[\s+]/g,'').length<8)return showToast('❌ Numéro invalide','error')
  const total=STATE.cart.reduce((a,i)=>a+i.price*i.qty,0)
  const ref='PAY-'+Math.random().toString(36).substr(2,10).toUpperCase()
  const order={id:'NX-'+Date.now().toString(36).toUpperCase()+'-'+Math.random().toString(36).substr(2,4).toUpperCase(),date:new Date().toISOString(),name,phone,email,method,address,items:STATE.cart.map(i=>({...i})),total,status:'payé',paymentRef:ref}
  STATE.orders.push(order)
  order.items.forEach(i=>{const p=STATE.products.find(x=>x.id===i.id);if(p)p.stock-=i.qty})
  STATE.cart=[];saveState();updateCartBadge();closeModal()
  showToast(`✅ Paiement confirmé (${ref})`,'success');showToast(`📦 Commande ${order.id} enregistrée`,'info');renderOrders()
}

// =================== ORDERS ===================
function renderOrders(){
  const app=document.getElementById('mainContent')
  if(!STATE.orders.length)return app.innerHTML=`<div class="topbar"><div class="topbar-left"><h1>📦 Commandes</h1></div></div><div class="empty-state"><div class="empty-icon">📦</div><div class="empty-title">Aucune commande</div></div>`
  app.innerHTML=`<div class="topbar"><div class="topbar-left"><h1>📦 Commandes</h1><span class="font-sm text-muted">${STATE.orders.length} commande(s)</span></div></div><div class="order-list">${STATE.orders.slice().reverse().map(o=>`<div class="order-card"><div class="order-header"><span class="order-id">${o.id}</span><span class="order-status">${o.status}</span></div><div class="order-meta">${formatDate(o.date)} · ${o.method} · ${o.paymentRef}</div><div style="font-size:10px;color:var(--text-secondary)">${escHtml(o.name)} · ${o.phone}</div><div class="order-footer"><span class="order-total">${formatPrice(o.total)}</span></div><div style="font-size:9px;color:var(--text-muted);margin-top:4px">${o.items.map(i=>`${i.qty}x ${escHtml(i.name)}`).join(', ')}</div></div>`).join('')}</div>`
}

// =================== SELL ===================
function renderSell(){
  const app=document.getElementById('mainContent')
  app.innerHTML=`
    <div class="topbar"><div class="topbar-left"><h1>💰 Vendre un article</h1></div></div>
    <div class="card" style="max-width:500px;margin:auto">
      <div class="input-group"><label>Nom du produit *</label><input class="input" id="sName" placeholder="Ex: Rapport Cybersécurité"></div>
      <div class="input-group"><label>Description *</label><textarea class="textarea" id="sDesc" rows="2" placeholder="Description détaillée"></textarea></div>
      <div class="flex"><div class="input-group" style="flex:1"><label>Prix (FCFA) *</label><input class="input" id="sPrice" type="number" placeholder="15000"></div><div class="input-group" style="flex:1"><label>Stock</label><input class="input" id="sStock" type="number" value="10"></div></div>
      <div class="flex"><div class="input-group" style="flex:1"><label>Catégorie</label><select class="input" id="sCat"><option value="rapports">Rapports</option><option value="outils">Outils</option><option value="formations">Formations</option><option value="données">Données</option><option value="merch">Merch</option><option value="abonnements">Abonnements</option><option value="services">Services</option></select></div><div class="input-group" style="flex:1"><label>Image URL</label><input class="input" id="sImg" placeholder="https://..." value="https://placehold.co/400x260/1a1a28/ff6600?text="></div></div>
      <div class="input-group"><label>Votre nom vendeur *</label><input class="input" id="sSeller" placeholder="Votre nom ou pseudo"></div>
      <button class="btn btn-primary btn-block" onclick="submitSell()">🚀 Mettre en vente</button>
    </div>`
}
function submitSell(){
  const name=document.getElementById('sName')?.value.trim(),desc=document.getElementById('sDesc')?.value.trim()
  const price=parseInt(document.getElementById('sPrice')?.value),stock=parseInt(document.getElementById('sStock')?.value)||1
  const cat=document.getElementById('sCat')?.value,img=document.getElementById('sImg')?.value.trim()||'https://placehold.co/400x260/1a1a28/ff6600?text=Article'
  const seller=document.getElementById('sSeller')?.value.trim()
  if(!name||!desc||!price||!seller)return showToast('❌ Champs * obligatoires','error')
  if(price<500)return showToast('❌ Prix minimum: 500 FCFA','error')
  STATE.products.push({id:STATE.nextId++,name,desc,price,category:cat,image:img,stock,seller})
  saveState();showToast(`✅ "${name}" en vente !`,'success');renderShop()
}

// =================== WHATSAPP ===================
function renderWhatsApp(){
  const app=document.getElementById('mainContent');const w=STATE.whatsapp
  app.innerHTML=`
    <div class="topbar"><div class="topbar-left"><h1>💬 WhatsApp Connection</h1></div></div>
    <div class="grid-2">
      <div class="card"><h3 style="font-size:11px;margin-bottom:6px">🔌 Configuration API</h3>
        <div class="input-group"><label>Phone Number ID</label><input class="input" id="wPhone" value="${escHtml(w.phoneId)}" style="font-size:10px"></div>
        <div class="input-group"><label>Token d'accès</label><input class="input" id="wToken" value="${escHtml(w.token)}" style="font-size:10px" type="password"></div>
        <div class="input-group"><label>Numéro WhatsApp</label><input class="input" id="wNumber" value="${escHtml(w.number)}" style="font-size:10px"></div>
        <div class="flex" style="gap:6px;margin-top:6px"><button class="btn ${w.active?'btn-success':'btn-primary'} btn-sm" onclick="toggleWA()">${w.active?'✅ Activé':'🔌 Connecter'}</button><button class="btn btn-primary btn-sm" onclick="saveWAConfig()">💾 Sauvegarder</button></div>
        <div style="font-size:9px;margin-top:4px">Statut: <strong style="color:${w.active?'var(--green)':'var(--text-muted)'}">${w.active?'Connecté':'Déconnecté'}</strong></div>
      </div>
      <div class="card"><h3 style="font-size:11px;margin-bottom:6px">📤 Envoyer message</h3>
        <div class="input-group"><label>Numéro destinataire</label><input class="input" id="waTo" placeholder="+2250101020304" style="font-size:10px"></div>
        <div class="input-group"><label>Message</label><textarea class="textarea" id="waMsg" rows="3" placeholder="Votre message..."></textarea></div>
        <button class="btn btn-primary btn-sm btn-block" onclick="sendWA()">📤 Envoyer via API</button>
      </div>
    </div>`
}
function saveWAConfig(){
  STATE.whatsapp.phoneId=document.getElementById('wPhone').value
  STATE.whatsapp.token=document.getElementById('wToken').value
  STATE.whatsapp.number=document.getElementById('wNumber').value
  saveState();showToast('💾 Configuration WhatsApp sauvegardée','success')
}
function toggleWA(){STATE.whatsapp.active=!STATE.whatsapp.active;saveState();renderWhatsApp();showToast(STATE.whatsapp.active?'✅ WhatsApp connecté':'🔌 WhatsApp déconnecté',STATE.whatsapp.active?'success':'info')}
async function sendWA(){
  const to=document.getElementById('waTo')?.value.trim(),msg=document.getElementById('waMsg')?.value.trim()
  if(!to||!msg)return showToast('❌ Numéro + message requis','error')
  if(!STATE.whatsapp.token||!STATE.whatsapp.phoneId)return showToast('❌ Configurez d\'abord l\'API','error')
  showToast('📤 Envoi en cours...','info')
  try{
    const res=await fetch(`https://graph.facebook.com/v18.0/${STATE.whatsapp.phoneId}/messages`,{
      method:'POST',headers:{'Authorization':`Bearer ${STATE.whatsapp.token}`,'Content-Type':'application/json'},
      body:JSON.stringify({messaging_product:'whatsapp',to:to.replace(/[^0-9]/g,''),type:'text',text:{body:msg}})
    })
    if(res.ok){showToast('✅ Message envoyé','success');document.getElementById('waMsg').value=''}
    else{const d=await res.json();showToast(`❌ Erreur: ${d.error?.message||res.status}`,'error')}
  }catch(e){showToast('❌ Erreur réseau: '+e.message,'error')}
}

// ===================== PAGES =====================
function renderPages(){
  const app=document.getElementById('mainContent')
  app.innerHTML=`
    <div class="topbar"><div class="topbar-left"><h1>🔗 Mes Pages</h1><span class="font-sm text-muted">${STATE.pages.length} page(s)</span></div><div class="topbar-right"><button class="btn btn-primary btn-sm" onclick="openModal('Créer une page','${escHtml(`<div class="input-group"><label>Titre</label><input class="input" id="pgTitle" placeholder="Titre de la page"></div><div class="input-group"><label>Contenu (HTML)</label><textarea class="textarea" id="pgBody" rows="8" placeholder="<h2>Votre contenu</h2><p>...</p>"></textarea></div><div class="input-group"><label>URL (slug)</label><input class="input" id="pgSlug" placeholder="ma-page"></div><button class="btn btn-primary btn-block" onclick="createPage()">Créer</button>`)}')">➕ Nouvelle page</button></div></div>
    ${STATE.pages.length?STATE.pages.map(p=>`<div class="card flex" style="justify-content:space-between"><div><strong style="font-size:11px">${escHtml(p.title)}</strong><br><span style="font-size:9px;color:var(--text-muted)">/${p.slug}</span></div><div class="flex"><button class="btn btn-ghost btn-sm" onclick="viewPublishedPage('${p.slug}')">👁️</button><button class="btn btn-ghost btn-sm" onclick="editPage('${p.slug}')">✏️</button><button class="btn btn-danger btn-sm" onclick="deletePage('${p.slug}')">✕</button></div></div>`).join(''):`<div class="empty-state"><div class="empty-icon">🔗</div><div class="empty-title">Aucune page</div></div>`}`
}

function createPage(){
  const t=document.getElementById('pgTitle')?.value.trim(),b=document.getElementById('pgBody')?.value,s=document.getElementById('pgSlug')?.value.trim()
  if(!t||!b||!s)return showToast('❌ Tous les champs requis','error')
  STATE.pages.push({title:t,body:b,slug:s,date:new Date().toISOString()})
  saveState();closeModal();renderPages();showToast(`✅ Page "${t}" créée`,'success')
}

function deletePage(slug){STATE.pages=STATE.pages.filter(p=>p.slug!==slug);saveState();renderPages();showToast('🗑️ Page supprimée','info')}

function viewPublishedPage(slug){
  const p=STATE.pages.find(x=>x.slug===slug);if(!p)return
  openModal(escHtml(p.title),`<div style="font-size:11px;color:var(--text-secondary);line-height:1.6">${p.body}</div><hr><div style="font-size:9px;color:var(--text-muted)">📅 ${formatDate(p.date)} · /${p.slug}</div>`)
}

function editPage(slug){
  const p=STATE.pages.find(x=>x.slug===slug);if(!p)return
  openModal(`✏️ Modifier : ${escHtml(p.title)}`,`<div class="input-group"><label>Titre</label><input class="input" id="pgTitleE" value="${escHtml(p.title)}"></div><div class="input-group"><label>Contenu (HTML)</label><textarea class="textarea" id="pgBodyE" rows="8">${escHtml(p.body)}</textarea></div><div class="input-group"><label>URL</label><input class="input" id="pgSlugE" value="${p.slug}"></div><button class="btn btn-primary btn-block" onclick="savePageEdit('${p.slug}')">💾 Sauvegarder</button>`)
}

function savePageEdit(slug){
  const p=STATE.pages.find(x=>x.slug===slug);if(!p)return
  p.title=document.getElementById('pgTitleE')?.value||p.title
  p.body=document.getElementById('pgBodyE')?.value||p.body
  const newSlug=document.getElementById('pgSlugE')?.value.trim()
  if(newSlug&&newSlug!==slug&&!STATE.pages.find(x=>x.slug===newSlug))p.slug=newSlug
  saveState();closeModal();renderPages();showToast('💾 Page mise à jour','success')
}

// =================== THEMES ===================
function renderThemes(){
  const app=document.getElementById('mainContent')
  app.innerHTML=`
    <div class="topbar"><div class="topbar-left"><h1>🎨 Thèmes & Apparence</h1></div></div>
    <div class="grid-2">
      <div class="card">
        <h3 style="font-size:11px;margin-bottom:8px">🌙 Mode d'affichage</h3>
        <div class="flex" style="gap:10px">
          <button class="btn ${STATE.theme==='dark'?'btn-primary':'btn-ghost'} btn-sm" onclick="setTheme('dark')">🌙 Nuit</button>
          <button class="btn ${STATE.theme==='light'?'btn-primary':'btn-ghost'} btn-sm" onclick="setTheme('light')">☀️ Jour</button>
        </div>
        <div style="font-size:9px;color:var(--text-muted);margin-top:6px">Actuel: <strong>${STATE.theme==='dark'?'Mode Nuit':'Mode Jour'}</strong></div>
      </div>
      <div class="card">
        <h3 style="font-size:11px;margin-bottom:8px">🎨 Personnalisation</h3>
        <div class="input-group"><label>Couleur d'accent</label>
          <div class="flex" style="gap:6px">
            <button style="width:28px;height:28px;border-radius:50%;border:2px solid ${!STATE.accentColor||STATE.accentColor==='#ff6600'?'var(--accent)':'transparent'};background:#ff6600;cursor:pointer" onclick="setAccent('#ff6600')" title="Orange NEXUS"></button>
            <button style="width:28px;height:28px;border-radius:50%;border:2px solid ${STATE.accentColor==='#00d4ff'?'var(--accent)':'transparent'};background:#00d4ff;cursor:pointer" onclick="setAccent('#00d4ff')" title="Cyan"></button>
            <button style="width:28px;height:28px;border-radius:50%;border:2px solid ${STATE.accentColor==='#7c3aed'?'var(--accent)':'transparent'};background:#7c3aed;cursor:pointer" onclick="setAccent('#7c3aed')" title="Violet"></button>
            <button style="width:28px;height:28px;border-radius:50%;border:2px solid ${STATE.accentColor==='#00ff88'?'var(--accent)':'transparent'};background:#00ff88;cursor:pointer" onclick="setAccent('#00ff88')" title="Vert"></button>
            <button style="width:28px;height:28px;border-radius:50%;border:2px solid ${STATE.accentColor==='#ff2244'?'var(--accent)':'transparent'};background:#ff2244;cursor:pointer" onclick="setAccent('#ff2244')" title="Rouge"></button>
          </div>
        </div>
        <div class="input-group"><label>Taille de police</label>
          <select class="input" id="fontSize" style="font-size:10px" onchange="setFontSize(this.value)">
            <option value="12px" ${STATE.fontSize==='12px'?'selected':''}>Petite</option>
            <option value="14px" ${!STATE.fontSize||STATE.fontSize==='14px'?'selected':''}>Normale</option>
            <option value="16px" ${STATE.fontSize==='16px'?'selected':''}>Grande</option>
          </select>
        </div>
      </div>
    </div>
    <div class="card mt-6">
      <h3 style="font-size:11px;margin-bottom:6px">📊 Aperçu</h3>
      <div style="font-size:${STATE.fontSize||'14px'};color:var(--text-primary)">
        <div style="background:var(--bg-card);padding:10px;border-radius:8px;border:1px solid var(--border)">
          <p style="font-weight:600">Texte d'exemple avec la police actuelle</p>
          <p style="color:var(--text-secondary);font-size:0.9em">Ceci est un texte secondaire de démonstration.</p>
          <span style="background:var(--accent);color:#000;padding:2px 8px;border-radius:4px;font-size:0.8em;font-weight:700">BADGE ACCENT</span>
        </div>
      </div>
    </div>`
}

function setTheme(t){
  STATE.theme=t;document.documentElement.setAttribute('data-theme',t);saveState();renderThemes()
  showToast(`🎨 Mode ${t==='dark'?'Nuit':'Jour'} activé`,'success')
}
function setAccent(c){
  STATE.accentColor=c;document.documentElement.style.setProperty('--accent',c);saveState();renderThemes()
  showToast('🎨 Couleur changée','success')
}
function setFontSize(s){
  STATE.fontSize=s;saveState();renderThemes()
  showToast('🔤 Taille mise à jour','success')
}

// =================== ADMIN (CORRIGÉ) ===================
function renderAdmin(){
  if(!checkAuth()) return
  const app=document.getElementById('mainContent')
  const totalVentes=STATE.orders.reduce((a,o)=>a+o.total,0)
  app.innerHTML=`
    <div class="topbar">
      <div class="topbar-left"><h1>⚙️ Administration</h1><span class="font-sm text-muted">👤 ${escHtml(STATE.auth.user?.nom)}</span></div>
      <div class="topbar-right"><button class="btn btn-ghost btn-sm" onclick="logout()">🔌 Déconnexion</button></div>
    </div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-value" style="color:var(--accent)">${STATE.products.length}</div><div class="stat-label">Articles</div></div>
      <div class="stat-card"><div class="stat-value" style="color:var(--green)">${STATE.orders.length}</div><div class="stat-label">Commandes</div></div>
      <div class="stat-card"><div class="stat-value" style="color:var(--gold)">${formatPrice(totalVentes)}</div><div class="stat-label">Chiffre d'affaires</div></div>
      <div class="stat-card"><div class="stat-value" style="color:var(--purple)">${STATE.auth.users.length}</div><div class="stat-label">Utilisateurs</div></div>
    </div>
    <div class="card mb-6">
      <h3 style="font-size:11px;margin-bottom:8px">📦 Gestion des produits</h3>
      <table class="table">
        <thead><tr><th>ID</th><th>Nom</th><th>Prix</th><th>Stock</th><th>Catégorie</th><th>Actions</th></tr></thead>
        <tbody>${STATE.products.map(p=>`
          <tr>
            <td>#${p.id}</td>
            <td><strong>${escHtml(p.name)}</strong></td>
            <td style="color:var(--accent);font-weight:700">${formatPrice(p.price)}</td>
            <td>${p.stock}</td>
            <td>${p.category}</td>
            <td>
              <button class="btn btn-primary btn-sm" onclick="editProduct(${p.id})">✏️</button>
              <button class="btn btn-danger btn-sm" onclick="deleteProduct(${p.id})">🗑️</button>
            </td>
          </tr>`).join('')}</tbody>
      </table>
    </div>
    <div class="grid-2">
      <div class="card">
        <h3 style="font-size:11px;margin-bottom:8px">👥 Utilisateurs</h3>
        <table class="table">
          <thead><tr><th>Login</th><th>Nom</th><th>Rôle</th><th>Actions</th></tr></thead>
          <tbody>${STATE.auth.users.map(u=>`
            <tr>
              <td>${escHtml(u.login)}</td>
              <td>${escHtml(u.nom)}</td>
              <td>${escHtml(u.role)}</td>
              <td><button class="btn btn-danger btn-sm" onclick="deleteUser(${u.id})">🗑️</button></td>
            </tr>`).join('')}</tbody>
        </table>
        <button class="btn btn-primary btn-sm btn-block mt-6" onclick="addUser()">➕ Ajouter un utilisateur</button>
      </div>
      <div class="card">
        <h3 style="font-size:11px;margin-bottom:8px">⚙️ Paramètres</h3>
        <div class="input-group"><label>Identifiant admin</label><input class="input" id="cfgLogin" value="${escHtml(STATE.auth.users[0]?.login||'admin')}"></div>
        <div class="input-group"><label>Mot de passe</label><input class="input" id="cfgPass" value="${escHtml(STATE.auth.users[0]?.pass||'admin2025')}"></div>
        <button class="btn btn-primary btn-sm btn-block" onclick="saveAdmin()">💾 Sauvegarder</button>
        <hr style="border-color:var(--border);margin:12px 0">
        <button class="btn btn-danger btn-sm btn-block" onclick="if(confirm('Réinitialiser toutes les données ?')){localStorage.clear();location.reload()}">🗑️ Réinitialiser</button>
      </div>
    </div>`
}

function editProduct(id){
  const p=STATE.products.find(x=>x.id===id);if(!p)return
  openModal(`✏️ Modifier : ${escHtml(p.name)}`,`
    <div class="input-group"><label>Nom</label><input class="input" id="epName" value="${escHtml(p.name)}"></div>
    <div class="input-group"><label>Description</label><textarea class="textarea" id="epDesc" rows="2">${escHtml(p.desc)}</textarea></div>
    <div class="flex"><div class="input-group" style="flex:1"><label>Prix (FCFA)</label><input class="input" id="epPrice" type="number" value="${p.price}"></div><div class="input-group" style="flex:1"><label>Stock</label><input class="input" id="epStock" type="number" value="${p.stock}"></div></div>
    <div class="input-group"><label>Image URL</label><input class="input" id="epImg" value="${escHtml(p.image)}"></div>
    <button class="btn btn-primary btn-block mt-6" onclick="saveProductEdit(${id})">💾 Sauvegarder</button>
  `)
}
function saveProductEdit(id){
  const p=STATE.products.find(x=>x.id===id);if(!p)return
  p.name=document.getElementById('epName')?.value||p.name
  p.desc=document.getElementById('epDesc')?.value||p.desc
  p.price=parseInt(document.getElementById('epPrice')?.value)||p.price
  p.stock=parseInt(document.getElementById('epStock')?.value)||0
  p.image=document.getElementById('epImg')?.value||p.image
  saveState();closeModal();renderAdmin();showToast('✅ Produit modifié','success')
}

function deleteProduct(id){
  if(!confirm('Supprimer cet article ?')) return
  STATE.products=STATE.products.filter(p=>p.id!==id)
  saveState();renderAdmin();showToast('🗑️ Produit supprimé','info')
}

function addUser(){
  openModal('➕ Ajouter un utilisateur',`
    <div class="input-group"><label>Login</label><input class="input" id="auLogin" placeholder="login"></div>
    <div class="input-group"><label>Mot de passe</label><input class="input" id="auPass" type="password" placeholder="••••••"></div>
    <div class="input-group"><label>Nom complet</label><input class="input" id="auNom" placeholder="Nom Prenom"></div>
    <div class="input-group"><label>Rôle</label><select class="input" id="auRole"><option>Admin</option><option>Vendeur</option><option>Modérateur</option></select></div>
    <button class="btn btn-primary btn-block mt-6" onclick="submitAddUser()">✅ Ajouter</button>
  `)
}
function submitAddUser(){
  const login=document.getElementById('auLogin')?.value.trim(),pass=document.getElementById('auPass')?.value.trim()
  const nom=document.getElementById('auNom')?.value.trim(),role=document.getElementById('auRole')?.value
  if(!login||!pass||!nom)return showToast('❌ Tous les champs requis','error')
  if(STATE.auth.users.find(u=>u.login===login))return showToast('❌ Login déjà existant','error')
  STATE.auth.users.push({id:STATE.auth.users.length+1,login,pass,nom,role,status:"offline"})
  saveState();closeModal();renderAdmin();showToast(`✅ Utilisateur ${nom} ajouté`,'success')
}

function deleteUser(id){
  if(STATE.auth.users.length<=1)return showToast('❌ Impossible : dernier admin','error')
  if(!confirm('Supprimer cet utilisateur ?')) return
  STATE.auth.users=STATE.auth.users.filter(u=>u.id!==id)
  saveState();renderAdmin();showToast('🗑️ Utilisateur supprimé','info')
}

function saveAdmin(){
  const login=document.getElementById('cfgLogin')?.value.trim(),pass=document.getElementById('cfgPass')?.value.trim()
  if(login&&pass){STATE.auth.users[0].login=login;STATE.auth.users[0].pass=pass;saveState();showToast('✅ Admin mis à jour','success')}
  else showToast('❌ Login et mot de passe requis','error')
}

// =================== STOCKAGE ===================
function saveState(){
  try{localStorage.setItem('nexus-market-state',JSON.stringify(STATE))}catch(e){}
}
function loadState(){
  try{
    const s=localStorage.getItem('nexus-market-state')
    if(s){const d=JSON.parse(s);Object.keys(d).forEach(k=>{STATE[k]=d[k]})}
  }catch(e){}
}

// =================== INIT ===================
function init(){
  loadState()
  const saved=localStorage.getItem('nexus-market-sidebar')
  if(saved==='collapsed'){sidebarCollapsed=true;document.getElementById('sidebar').classList.add('collapsed')}
  document.getElementById('sidebarToggle').addEventListener('click',toggleSidebar)
  document.querySelectorAll('.nav-item[data-page]').forEach(el=>{el.addEventListener('click',()=>showPage(el.dataset.page))})
  if(STATE.theme==='light')document.documentElement.setAttribute('data-theme','light')
  if(STATE.accentColor)document.documentElement.style.setProperty('--accent',STATE.accentColor)
  showPage('shop')
  updateCartBadge()
  setInterval(saveState,30000)
  console.log('⟡ NEXUS MARKETPLACE v4.0 chargée')
}

if(document.readyState==='loading')document.addEventListener('DOMContentLoaded',init)
else init()
</script>
</body>
</html>
