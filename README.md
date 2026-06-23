<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEXUS MARKETPLACE — Premium</title>
<style>
/* ============================================================
   NEXUS MARKETPLACE v2.0 — Premium Dark Edition
   ============================================================ */
:root {
  --bg-primary: #07070d;
  --bg-secondary: #0c0c16;
  --bg-card: rgba(18, 18, 30, 0.75);
  --bg-card-hover: rgba(26, 26, 46, 0.9);
  --bg-glass: rgba(255, 255, 255, 0.04);
  --bg-glass-border: rgba(255, 255, 255, 0.08);
  --text-primary: #f0f0f5;
  --text-secondary: #8888aa;
  --text-muted: #555577;
  --accent: #ff6600;
  --accent-glow: rgba(255, 102, 0, 0.3);
  --accent2: #00e5ff;
  --accent2-glow: rgba(0, 229, 255, 0.2);
  --green: #00ff88;
  --green-dim: rgba(0, 255, 136, 0.15);
  --orange: #ff8800;
  --red: #ff2244;
  --red-dim: rgba(255, 34, 68, 0.15);
  --purple: #7c3aed;
  --border: rgba(255, 255, 255, 0.06);
  --border-light: rgba(255, 255, 255, 0.1);
  --shadow-card: 0 4px 24px rgba(0,0,0,0.4);
  --shadow-glow: 0 0 30px var(--accent-glow);
  --radius-sm: 6px;
  --radius-md: 12px;
  --radius-lg: 20px;
  --radius-xl: 28px;
  --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: var(--bg-primary);
  color: var(--text-primary);
  min-height: 100vh;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* --- Scrollbar Premium --- */
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: var(--bg-primary); }
::-webkit-scrollbar-thumb { background: var(--border-light); border-radius: 3px; }
::-webkit-scrollbar-thumb:hover { background: var(--text-muted); }

/* --- Background Pattern Subtle --- */
body::before {
  content: '';
  position: fixed;
  top: 0; left: 0; width: 100%; height: 100%;
  background:
    radial-gradient(ellipse at 20% 50%, rgba(124, 58, 237, 0.06) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 20%, rgba(255, 102, 0, 0.04) 0%, transparent 50%),
    radial-gradient(ellipse at 50% 80%, rgba(0, 229, 255, 0.03) 0%, transparent 50%);
  pointer-events: none;
  z-index: 0;
}

/* ===================== LAYOUT ===================== */
.layout { display: grid; grid-template-columns: 240px 1fr; min-height: 100vh; position: relative; z-index: 1; }

/* --- Sidebar --- */
.sidebar {
  background: var(--bg-secondary);
  border-right: 1px solid var(--border);
  padding: 20px 12px;
  position: sticky;
  top: 0;
  height: 100vh;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.logo {
  font-size: 22px;
  font-weight: 800;
  color: var(--accent);
  margin-bottom: 28px;
  padding: 0 8px;
  display: flex;
  align-items: center;
  gap: 8px;
  letter-spacing: -0.5px;
}
.logo .diamond { color: var(--text-primary); font-weight: 300; }
.logo .accent-text { color: var(--accent); }
.logo .logo-icon {
  display: inline-flex;
  width: 32px; height: 32px;
  background: linear-gradient(135deg, var(--accent), var(--purple));
  border-radius: 8px;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  box-shadow: 0 0 20px var(--accent-glow);
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 14px;
  border-radius: var(--radius-md);
  cursor: pointer;
  font-size: 13px;
  color: var(--text-muted);
  transition: var(--transition);
  position: relative;
  font-weight: 500;
}
.nav-item:hover { color: var(--text-primary); background: var(--bg-glass); }
.nav-item.active {
  color: var(--accent);
  background: linear-gradient(135deg, rgba(255, 102, 0, 0.12), rgba(124, 58, 237, 0.08));
  border: 1px solid rgba(255, 102, 0, 0.15);
}
.nav-item.active::before {
  content: '';
  position: absolute;
  left: -12px;
  top: 50%;
  transform: translateY(-50%);
  width: 3px;
  height: 20px;
  background: var(--accent);
  border-radius: 0 3px 3px 0;
  box-shadow: 0 0 10px var(--accent-glow);
}
.nav-item .nav-icon { font-size: 16px; width: 22px; text-align: center; }
.badge-cart {
  background: var(--accent);
  color: #000;
  border-radius: 50%;
  padding: 1px 6px;
  font-size: 9px;
  font-weight: 800;
  margin-left: auto;
  min-width: 20px;
  text-align: center;
  box-shadow: 0 0 12px var(--accent-glow);
}

.sidebar-footer {
  margin-top: auto;
  padding-top: 16px;
  border-top: 1px solid var(--border);
  font-size: 10px;
  color: var(--text-muted);
  text-align: center;
}

/* --- Main --- */
.main {
  padding: 24px 28px;
  position: relative;
  z-index: 1;
}

/* ===================== TOP BAR ===================== */
.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
  gap: 16px;
}
.topbar-left { display: flex; align-items: center; gap: 12px; }
.topbar-left h1 {
  font-size: 22px;
  font-weight: 700;
  background: linear-gradient(135deg, var(--text-primary), var(--text-secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.topbar-right { display: flex; align-items: center; gap: 12px; }

/* --- Search --- */
.search-box {
  display: flex;
  align-items: center;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 8px 16px;
  gap: 8px;
  transition: var(--transition);
  backdrop-filter: blur(12px);
  min-width: 260px;
}
.search-box:focus-within {
  border-color: var(--accent);
  box-shadow: 0 0 20px var(--accent-glow);
}
.search-box input {
  background: none;
  border: none;
  color: var(--text-primary);
  font-size: 13px;
  outline: none;
  width: 100%;
  font-family: inherit;
}
.search-box input::placeholder { color: var(--text-muted); }
.search-box .search-icon { color: var(--text-muted); font-size: 14px; }

/* --- User avatar --- */
.user-avatar {
  width: 36px; height: 36px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--accent), var(--purple));
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: 700;
  color: #fff;
  cursor: pointer;
  box-shadow: 0 0 20px var(--accent-glow);
  transition: var(--transition);
}
.user-avatar:hover { transform: scale(1.05); box-shadow: 0 0 30px var(--accent-glow); }

/* ===================== CARDS ===================== */
.card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 16px;
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  transition: var(--transition);
}
.card:hover { border-color: var(--border-light); }

/* ===================== PRODUCT GRID ===================== */
.grid-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}
.grid-header .grid-info { font-size: 12px; color: var(--text-muted); }
.grid-toggle {
  display: flex; gap: 4px;
  background: var(--bg-card);
  border-radius: var(--radius-sm);
  padding: 3px;
  border: 1px solid var(--border);
}
.grid-toggle button {
  background: none;
  border: none;
  color: var(--text-muted);
  padding: 4px 8px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: var(--transition);
}
.grid-toggle button.active { background: var(--accent); color: #000; }

.grid-prod {
  display: grid;
  gap: 12px;
  transition: var(--transition);
}
.grid-prod.grid { grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); }
.grid-prod.list { grid-template-columns: 1fr; }

/* --- Product Card --- */
.prod-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 14px;
  transition: var(--transition);
  position: relative;
  overflow: hidden;
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  cursor: pointer;
  animation: fadeInUp 0.4s ease both;
}
.prod-card:nth-child(1) { animation-delay: 0.02s; }
.prod-card:nth-child(2) { animation-delay: 0.06s; }
.prod-card:nth-child(3) { animation-delay: 0.10s; }
.prod-card:nth-child(4) { animation-delay: 0.14s; }
.prod-card:nth-child(5) { animation-delay: 0.18s; }
.prod-card:nth-child(6) { animation-delay: 0.22s; }
.prod-card:nth-child(7) { animation-delay: 0.26s; }
.prod-card:nth-child(8) { animation-delay: 0.30s; }

.prod-card:hover {
  border-color: var(--accent);
  transform: translateY(-4px) scale(1.01);
  box-shadow: 0 12px 40px rgba(0,0,0,0.5), 0 0 30px var(--accent-glow);
}
.prod-card::after {
  content: '';
  position: absolute;
  top: 0; left: -100%;
  width: 100%; height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.03), transparent);
  transition: 0.6s;
  pointer-events: none;
}
.prod-card:hover::after { left: 100%; }

.prod-card .img-wrap {
  width: 100%;
  height: 160px;
  border-radius: var(--radius-sm);
  overflow: hidden;
  background: var(--bg-secondary);
  position: relative;
}
.prod-card .img-wrap img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: var(--transition);
}
.prod-card:hover .img-wrap img { transform: scale(1.05); }

.prod-card .badge-stock {
  position: absolute;
  top: 8px; right: 8px;
  padding: 3px 10px;
  border-radius: 20px;
  font-size: 8px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  z-index: 2;
}
.badge-stock.low { background: var(--orange); color: #000; }
.badge-stock.out { background: var(--red); color: #fff; }
.badge-stock.ok { display: none; }

.prod-card .name {
  font-size: 13px;
  font-weight: 600;
  margin-top: 10px;
  line-height: 1.3;
  color: var(--text-primary);
}
.prod-card .seller-name {
  font-size: 10px;
  color: var(--text-muted);
  margin-top: 2px;
}
.prod-card .price {
  font-size: 20px;
  font-weight: 800;
  color: var(--accent);
  margin-top: 4px;
  letter-spacing: -0.5px;
}
.prod-card .desc {
  font-size: 11px;
  color: var(--text-secondary);
  margin-top: 4px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  line-height: 1.5;
}
.prod-card .actions {
  display: flex;
  gap: 6px;
  margin-top: 12px;
}
.prod-card .actions button { flex: 1; }

/* List view */
.grid-prod.list .prod-card {
  display: flex;
  gap: 16px;
  align-items: center;
}
.grid-prod.list .prod-card .img-wrap { width: 100px; height: 100px; flex-shrink: 0; }
.grid-prod.list .prod-card .name { margin-top: 0; }
.grid-prod.list .prod-card .price { margin-top: 0; }
.grid-prod.list .prod-card .desc { -webkit-line-clamp: 1; }
.grid-prod.list .prod-card .actions { margin-top: 0; min-width: 160px; }

/* ===================== BUTTONS ===================== */
.btn {
  padding: 8px 18px;
  border: none;
  border-radius: var(--radius-sm);
  cursor: pointer;
  font-size: 12px;
  font-weight: 600;
  transition: var(--transition);
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-family: inherit;
  position: relative;
  overflow: hidden;
}
.btn::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(255,255,255,0.1), transparent);
  opacity: 0;
  transition: var(--transition);
}
.btn:hover::after { opacity: 1; }

.btn-primary { background: linear-gradient(135deg, var(--accent), #e05500); color: #000; box-shadow: 0 4px 16px var(--accent-glow); }
.btn-primary:hover { transform: translateY(-1px); box-shadow: 0 6px 24px var(--accent-glow); }
.btn-success { background: linear-gradient(135deg, var(--green), #00cc6a); color: #000; box-shadow: 0 4px 16px var(--green-dim); }
.btn-success:hover { transform: translateY(-1px); box-shadow: 0 6px 24px var(--green-dim); }
.btn-danger { background: linear-gradient(135deg, var(--red), #cc0033); color: #fff; box-shadow: 0 4px 16px var(--red-dim); }
.btn-danger:hover { transform: translateY(-1px); }
.btn-ghost { background: var(--bg-glass); color: var(--text-secondary); border: 1px solid var(--border); }
.btn-ghost:hover { background: var(--bg-card-hover); color: var(--text-primary); border-color: var(--border-light); }

.btn-sm { padding: 5px 12px; font-size: 10px; }
.btn-lg { padding: 12px 24px; font-size: 14px; }
.btn-block { width: 100%; justify-content: center; }
.btn-icon { width: 32px; height: 32px; padding: 0; justify-content: center; border-radius: 50%; }

/* ===================== FORM ===================== */
.input {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 10px 14px;
  color: var(--text-primary);
  font-size: 13px;
  width: 100%;
  transition: var(--transition);
  font-family: inherit;
}
.input:focus { outline: none; border-color: var(--accent); box-shadow: 0 0 16px var(--accent-glow); }
.input::placeholder { color: var(--text-muted); }

.textarea {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 10px 14px;
  color: var(--text-primary);
  font-size: 13px;
  width: 100%;
  resize: vertical;
  transition: var(--transition);
  font-family: inherit;
  min-height: 80px;
}
.textarea:focus { outline: none; border-color: var(--accent); box-shadow: 0 0 16px var(--accent-glow); }
.textarea::placeholder { color: var(--text-muted); }

select.input {
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' fill='%238888aa'%3E%3Cpath d='M6 8L1 3h10z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 12px center;
  padding-right: 36px;
}

.input-group { margin-bottom: 12px; }
.input-group label {
  display: block;
  font-size: 11px;
  color: var(--text-secondary);
  margin-bottom: 4px;
  font-weight: 500;
  letter-spacing: 0.3px;
}

/* ===================== TABS ===================== */
.tabs {
  display: flex;
  gap: 6px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}
.tabs button {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 6px 16px;
  color: var(--text-muted);
  cursor: pointer;
  font-size: 11px;
  transition: var(--transition);
  font-family: inherit;
  font-weight: 500;
}
.tabs button:hover { color: var(--text-primary); border-color: var(--border-light); }
.tabs button.active {
  background: linear-gradient(135deg, var(--accent), #e05500);
  color: #000;
  border-color: var(--accent);
  font-weight: 700;
  box-shadow: 0 4px 16px var(--accent-glow);
}

/* ===================== CART ===================== */
.cart-item {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 12px;
  margin-bottom: 8px;
  display: flex;
  gap: 14px;
  align-items: center;
  transition: var(--transition);
  backdrop-filter: blur(12px);
}
.cart-item:hover { border-color: var(--border-light); }
.cart-item img {
  width: 60px; height: 60px;
  object-fit: cover;
  border-radius: var(--radius-sm);
  flex-shrink: 0;
}
.cart-item .info { flex: 1; min-width: 0; }
.cart-item .info .name { font-size: 13px; font-weight: 600; }
.cart-item .info .price { font-size: 15px; color: var(--accent); font-weight: 700; margin-top: 2px; }
.cart-item .qty {
  display: flex;
  align-items: center;
  gap: 6px;
  background: var(--bg-secondary);
  border-radius: var(--radius-lg);
  padding: 2px;
  border: 1px solid var(--border);
}
.cart-item .qty button {
  width: 28px; height: 28px;
  border-radius: 50%;
  border: none;
  background: var(--bg-card);
  color: var(--text-primary);
  cursor: pointer;
  font-size: 14px;
  font-weight: 700;
  transition: var(--transition);
}
.cart-item .qty button:hover { background: var(--accent); color: #000; }
.cart-item .qty span {
  font-size: 13px;
  font-weight: 700;
  min-width: 24px;
  text-align: center;
  color: var(--text-primary);
}

/* ===================== CART SUMMARY ===================== */
.cart-summary {
  margin-top: 16px;
  padding: 20px;
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  backdrop-filter: blur(16px);
}
.cart-summary .total-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.cart-summary .total-label { font-size: 13px; color: var(--text-secondary); }
.cart-summary .total-price {
  font-size: 24px;
  font-weight: 800;
  color: var(--accent);
  letter-spacing: -0.5px;
}

/* ===================== ORDER CARD ===================== */
.order-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 14px;
  margin-bottom: 8px;
  transition: var(--transition);
  backdrop-filter: blur(12px);
}
.order-card:hover { border-color: var(--border-light); }
.order-card .order-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.order-card .order-id { font-size: 12px; font-weight: 600; color: var(--accent); }
.order-card .order-date { font-size: 11px; color: var(--text-muted); }
.order-card .order-items { font-size: 11px; color: var(--text-secondary); margin: 6px 0; }
.order-card .order-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 6px;
}
.order-card .order-status {
  padding: 3px 12px;
  border-radius: 20px;
  font-size: 9px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  background: var(--green-dim);
  color: var(--green);
}
.order-card .order-total { font-size: 16px; font-weight: 700; color: var(--accent); }
.order-card .order-meta { font-size: 9px; color: var(--text-muted); margin-top: 4px; }

/* ===================== MODAL ===================== */
.modal-overlay {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.7);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  z-index: 1000;
  display: none;
  align-items: center;
  justify-content: center;
  animation: fadeIn 0.2s ease;
}
.modal-overlay.show { display: flex; }

.modal {
  background: var(--bg-card);
  border: 1px solid var(--border-light);
  border-radius: var(--radius-lg);
  padding: 28px;
  max-width: 520px;
  width: 90%;
  max-height: 85vh;
  overflow-y: auto;
  box-shadow: 0 24px 80px rgba(0,0,0,0.6);
  animation: scaleIn 0.25s ease;
  backdrop-filter: blur(24px);
}
.modal h3 {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 16px;
  background: linear-gradient(135deg, var(--text-primary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.modal hr {
  border: none;
  border-top: 1px solid var(--border);
  margin: 12px 0;
}

/* ===================== TOAST ===================== */
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background: var(--bg-card);
  border: 1px solid var(--border-light);
  color: var(--text-primary);
  padding: 12px 20px;
  border-radius: var(--radius-md);
  font-size: 13px;
  font-weight: 500;
  z-index: 2000;
  opacity: 0;
  transform: translateY(16px) scale(0.95);
  transition: var(--transition);
  pointer-events: none;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0 8px 32px rgba(0,0,0,0.4);
  display: flex;
  align-items: center;
  gap: 8px;
}
.toast.show { opacity: 1; transform: translateY(0) scale(1); pointer-events: auto; }

/* ===================== STATS CARDS ===================== */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 12px;
  margin-bottom: 16px;
}
.stat-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 18px;
  backdrop-filter: blur(12px);
  transition: var(--transition);
}
.stat-card:hover { border-color: var(--border-light); transform: translateY(-2px); }
.stat-card .stat-value { font-size: 24px; font-weight: 800; letter-spacing: -0.5px; }
.stat-card .stat-label { font-size: 10px; color: var(--text-muted); margin-top: 2px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.5px; }
.stat-card .stat-bar {
  margin-top: 10px;
  height: 3px;
  background: var(--border);
  border-radius: 2px;
  overflow: hidden;
}
.stat-card .stat-bar .fill {
  height: 100%;
  border-radius: 2px;
  transition: width 1s ease;
}

/* ===================== ADMIN SECTIONS ===================== */
.admin-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.admin-section {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 18px;
  backdrop-filter: blur(12px);
}
.admin-section h3 {
  font-size: 13px;
  font-weight: 600;
  margin-bottom: 12px;
  color: var(--text-primary);
}
.admin-section .admin-item {
  display: flex;
  justify-content: space-between;
  font-size: 11px;
  padding: 6px 0;
  border-bottom: 1px solid var(--border);
  color: var(--text-secondary);
}
.admin-section .admin-item:last-child { border-bottom: none; }

/* ===================== EMPTY STATE ===================== */
.empty-state {
  text-align: center;
  padding: 60px 20px;
  color: var(--text-muted);
}
.empty-state .empty-icon { font-size: 48px; margin-bottom: 12px; opacity: 0.5; }
.empty-state .empty-title { font-size: 16px; font-weight: 600; color: var(--text-secondary); margin-bottom: 4px; }
.empty-state .empty-desc { font-size: 12px; }

/* ===================== SELL FORM ===================== */
.sell-form { max-width: 560px; margin: 0 auto; }
.sell-form .form-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 24px;
  backdrop-filter: blur(12px);
}
.sell-form .form-card .form-step { font-size: 10px; color: var(--text-muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 4px; }
.sell-form .form-card .form-title { font-size: 18px; font-weight: 700; margin-bottom: 20px; }
.image-preview {
  margin-top: 6px;
  height: 100px;
  background: var(--bg-secondary);
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  color: var(--text-muted);
  overflow: hidden;
  border: 1px dashed var(--border);
}
.image-preview img { width: 100%; height: 100%; object-fit: cover; }

/* ===================== ANIMATIONS ===================== */
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.92); }
  to { opacity: 1; transform: scale(1); }
}
@keyframes shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}
@keyframes pulse {
  0%, 100% { box-shadow: 0 0 16px var(--accent-glow); }
  50% { box-shadow: 0 0 32px var(--accent-glow); }
}

/* ===================== RESPONSIVE ===================== */
@media (max-width: 768px) {
  .layout { grid-template-columns: 1fr; }
  .sidebar {
    position: fixed;
    bottom: 0;
    top: auto;
    height: auto;
    z-index: 100;
    display: flex;
    flex-direction: row;
    overflow-x: auto;
    padding: 8px 12px;
    gap: 4px;
    border-top: 1px solid var(--border);
    border-right: none;
    width: 100%;
    backdrop-filter: blur(20px);
    background: rgba(10, 10, 15, 0.92);
  }
  .sidebar .logo { display: none; }
  .sidebar .nav-item { white-space: nowrap; flex-shrink: 0; padding: 8px 14px; font-size: 11px; }
  .sidebar .nav-item span { display: none; }
  .sidebar .nav-item.active::before { display: none; }
  .sidebar .sidebar-footer { display: none; }
  .main { padding: 16px; padding-bottom: 72px; }
  .topbar { flex-direction: column; align-items: stretch; }
  .search-box { min-width: unset; }
  .grid-prod.grid { grid-template-columns: repeat(2, 1fr); }
  .grid-prod.list .prod-card { flex-direction: column; }
  .grid-prod.list .prod-card .img-wrap { width: 100%; height: 140px; }
  .admin-grid { grid-template-columns: 1fr; }
  .stats-grid { grid-template-columns: repeat(2, 1fr); }
  .cart-item { flex-wrap: wrap; }
  .cart-item .qty { margin-left: auto; }
  .modal { padding: 20px; }
}

@media (max-width: 480px) {
  .grid-prod.grid { grid-template-columns: 1fr; }
  .stats-grid { grid-template-columns: 1fr; }
}

/* ===================== UTILITY ===================== */
.flex { display: flex; gap: 8px; align-items: center; }
.flex-between { display: flex; justify-content: space-between; align-items: center; }
.flex-center { display: flex; justify-content: center; align-items: center; }
.flex-wrap { flex-wrap: wrap; }
.gap-4 { gap: 4px; }
.mb-4 { margin-bottom: 4px; }
.mb-6 { margin-bottom: 6px; }
.mb-8 { margin-bottom: 8px; }
.mb-12 { margin-bottom: 12px; }
.mt-6 { margin-top: 6px; }
.mt-8 { margin-top: 8px; }
.mt-12 { margin-top: 12px; }
.text-center { text-align: center; }
.text-accent { color: var(--accent); }
.text-green { color: var(--green); }
.text-muted { color: var(--text-muted); }
.text-secondary { color: var(--text-secondary); }
.fw-600 { font-weight: 600; }
.fw-700 { font-weight: 700; }
.fw-800 { font-weight: 800; }
.font-sm { font-size: 11px; }
</style>
</head>
<body>

<div class="layout">
  <!-- ===== SIDEBAR ===== -->
  <nav class="sidebar" id="sidebar">
    <div class="logo">
      <span class="logo-icon">⟡</span>
      NEXUS<span class="diamond">MARKET</span>
    </div>

    <div class="nav-item active" data-page="shop">
      <span class="nav-icon">🏪</span> <span>Boutique</span>
    </div>
    <div class="nav-item" data-page="cart">
      <span class="nav-icon">🛒</span> <span>Panier</span>
      <span class="badge-cart" id="cartCount">0</span>
    </div>
    <div class="nav-item" data-page="orders">
      <span class="nav-icon">📦</span> <span>Commandes</span>
    </div>
    <div class="nav-item" data-page="sell">
      <span class="nav-icon">💰</span> <span>Vendre</span>
    </div>
    <div class="nav-item" data-page="admin">
      <span class="nav-icon">⚙️</span> <span>Admin</span>
    </div>

    <div class="sidebar-footer">
      NEXUS MARKET v2.0 · Premium
    </div>
  </nav>

  <!-- ===== MAIN ===== -->
  <main class="main" id="mainContent">
    <!-- Rendu dynamique ici -->
  </main>
</div>

<!-- ===== MODAL ===== -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal" id="modalContent"></div>
</div>

<!-- ===== TOAST ===== -->
<div class="toast" id="toast">
  <span id="toastIcon">⟡</span>
  <span id="toastMsg">Message</span>
</div>

<script>
// ============================================================
// NEXUS MARKETPLACE v2.0 — Premium Edition
// ============================================================

// ===================== DONNÉES =====================
const STATE = {
  products: [
    {
      id: 1,
      name: "Rapport Cybersécurité CI 2025",
      desc: "Analyse complète des cyberattaques en Côte d'Ivoire — tendances, acteurs, recommandations sectorielles.",
      price: 15000,
      category: "rapports",
      image: "https://placehold.co/400x260/1a1a28/00ff88?text=Rapport+CI",
      stock: 50,
      seller: "NEXUS Intel"
    },
    {
      id: 2,
      name: "Pack OSINT Pro",
      desc: "120+ outils de renseignement open source avec guides d'utilisation et scripts automatisés.",
      price: 25000,
      category: "outils",
      image: "https://placehold.co/400x260/1a1a28/ff6600?text=OSINT+Pro",
      stock: 30,
      seller: "NEXUS Intel"
    },
    {
      id: 3,
      name: "Formation Ethical Hacking",
      desc: "Cours complet vidéo + PDF — 200 heures de contenu certifiant avec support dédié.",
      price: 45000,
      category: "formations",
      image: "https://placehold.co/400x260/1a1a28/ff2244?text=Hacking",
      stock: 100,
      seller: "NEXUS Academy"
    },
    {
      id: 4,
      name: "Base de données CVEs CI",
      desc: "Liste exhaustive des vulnérabilités affectant les systèmes en Côte d'Ivoire et Afrique.",
      price: 20000,
      category: "données",
      image: "https://placehold.co/400x260/1a1a28/0088ff?text=CVE+CI",
      stock: 25,
      seller: "NEXUS Intel"
    },
    {
      id: 5,
      name: "T-Shirt NEXUS Édition Limitée",
      desc: "T-shirt noir premium avec logo NEXUS DIAMOND sérigraphié en édition limitée.",
      price: 8500,
      category: "merch",
      image: "https://placehold.co/400x260/1a1a28/ffffff?text=NEXUS",
      stock: 200,
      seller: "NEXUS Store"
    },
    {
      id: 6,
      name: "Script Automatisation Scan RSS",
      desc: "Script Python/JS pour scanner et classifier automatiquement des flux RSS avec alertes.",
      price: 12000,
      category: "outils",
      image: "https://placehold.co/400x260/1a1a28/00ff88?text=Script+RSS",
      stock: 80,
      seller: "NEXUS Dev"
    },
    {
      id: 7,
      name: "Template Dashboard Intelligence",
      desc: "Template HTML/CSS/JS prêt à l'emploi — interface sombre style NEXUS DIAMOND.",
      price: 18000,
      category: "outils",
      image: "https://placehold.co/400x260/1a1a28/ff6600?text=Dashboard",
      stock: 60,
      seller: "NEXUS Dev"
    },
    {
      id: 8,
      name: "Abonnement Premium 1 Mois",
      desc: "Accès aux briefs quotidiens, alertes critiques en temps réel et rapports exclusifs.",
      price: 9500,
      category: "abonnements",
      image: "https://placehold.co/400x260/1a1a28/ff8800?text=Premium",
      stock: 999,
      seller: "NEXUS Intel"
    }
  ],
  cart: [],
  orders: [],
  sellers: [],
  nextId: 9
}

// ===================== ÉTATS UI =====================
let categoryFilter = 'all'
let viewMode = 'grid'
let searchQuery = ''

// ===================== UTILITAIRES =====================
function escHtml(s) {
  if (!s) return ''
  return String(s)
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;')
    .replace(/"/g, '&quot;')
    .replace(/'/g, '&#039;')
}

function formatPrice(p) {
  return Number(p).toLocaleString('fr-FR', { minimumFractionDigits: 0, maximumFractionDigits: 0 }) + ' FCFA'
}

function formatDate(d) {
  return new Date(d).toLocaleDateString('fr-FR', {
    day: 'numeric', month: 'short', year: 'numeric',
    hour: '2-digit', minute: '2-digit'
  })
}

// ===================== TOAST =====================
function showToast(msg, type) {
  const t = document.getElementById('toast')
  const icon = document.getElementById('toastIcon')
  const text = document.getElementById('toastMsg')

  const icons = { success: '✅', error: '❌', info: '⟡', warning: '⚠️' }
  icon.textContent = icons[type] || '⟡'
  text.textContent = msg

  t.className = 'toast show'
  clearTimeout(t._timeout)
  t._timeout = setTimeout(() => t.classList.remove('show'), 3000)
}

// ===================== MODAL =====================
function openModal(title, content) {
  const overlay = document.getElementById('modalOverlay')
  document.getElementById('modalContent').innerHTML = `
    <div style="display:flex;justify-content:space-between;align-items:start;margin-bottom:16px">
      <h3>${title}</h3>
      <button class="btn btn-ghost btn-icon" onclick="closeModal()" style="font-size:16px">✕</button>
    </div>
    ${content}
  `
  overlay.classList.add('show')
  overlay.onclick = function(e) { if (e.target === this) closeModal() }
}

function closeModal() {
  document.getElementById('modalOverlay').classList.remove('show')
}

// ===================== CART BADGE =====================
function updateCartBadge() {
  const c = document.getElementById('cartCount')
  if (c) c.textContent = STATE.cart.reduce((a, i) => a + i.qty, 0)
}

// ===================== NAVIGATION =====================
function showPage(page) {
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'))
  const el = document.querySelector(`.nav-item[data-page="${page}"]`)
  if (el) el.classList.add('active')

  switch (page) {
    case 'shop': renderShop(); break
    case 'cart': renderCart(); break
    case 'orders': renderOrders(); break
    case 'sell': renderSell(); break
    case 'admin': renderAdmin(); break
  }
}

// Init navigation listeners
document.addEventListener('DOMContentLoaded', () => {
  document.querySelectorAll('.nav-item[data-page]').forEach(el => {
    el.addEventListener('click', () => showPage(el.dataset.page))
  })
  showPage('shop')
})

// ===================== BOUTIQUE =====================
function renderShop() {
  const app = document.getElementById('mainContent')
  let prods = STATE.products

  // Filtre par catégorie
  if (categoryFilter !== 'all') prods = prods.filter(p => p.category === categoryFilter)

  // Filtre par recherche
  if (searchQuery.trim()) {
    const q = searchQuery.trim().toLowerCase()
    prods = prods.filter(p =>
      p.name.toLowerCase().includes(q) ||
      p.desc.toLowerCase().includes(q) ||
      p.seller.toLowerCase().includes(q)
    )
  }

  const cats = {}
  STATE.products.forEach(p => { cats[p.category] = true })

  app.innerHTML = `
    <div class="topbar">
      <div class="topbar-left">
        <h1>🏪 Boutique</h1>
        <span class="font-sm text-muted">${prods.length} article${prods.length > 1 ? 's' : ''}</span>
      </div>
      <div class="topbar-right">
        <div class="search-box">
          <span class="search-icon">🔍</span>
          <input type="text" id="searchInput" placeholder="Rechercher un article..." value="${escHtml(searchQuery)}" oninput="searchQuery=this.value;renderShop()">
        </div>
        <div class="user-avatar" title="Profil">N</div>
      </div>
    </div>

    <div class="tabs">
      <button class="${categoryFilter === 'all' ? 'active' : ''}" onclick="setCat('all')">📋 Tout</button>
      ${Object.keys(cats).map(c =>
        `<button class="${categoryFilter === c ? 'active' : ''}" onclick="setCat('${c}')">${c.charAt(0).toUpperCase() + c.slice(1)}</button>`
      ).join('')}
    </div>

    <div class="grid-header">
      <span class="grid-info">${prods.length} résultat${prods.length > 1 ? 's' : ''}</span>
      <div class="grid-toggle">
        <button class="${viewMode === 'grid' ? 'active' : ''}" onclick="viewMode='grid';renderShop()" title="Grille">▦</button>
        <button class="${viewMode === 'list' ? 'active' : ''}" onclick="viewMode='list';renderShop()" title="Liste">☰</button>
      </div>
    </div>

    <div class="grid-prod ${viewMode}">
      ${prods.length ? prods.map(p => {
        const stockClass = p.stock <= 0 ? 'out' : p.stock < 10 ? 'low' : 'ok'
        const stockLabel = p.stock <= 0 ? 'Épuisé' : p.stock < 10 ? 'Stock limité' : ''
        return `
        <div class="prod-card" onclick="viewProduct(${p.id})">
          <div class="img-wrap">
            <img src="${p.image}" alt="${escHtml(p.name)}" loading="lazy">
            ${stockLabel ? `<div class="badge-stock ${stockClass}">${stockLabel}</div>` : ''}
          </div>
          <div class="name">${escHtml(p.name)}</div>
          <div class="seller-name">par ${escHtml(p.seller)}</div>
          <div class="price">${formatPrice(p.price)}</div>
          <div class="desc">${escHtml(p.desc)}</div>
          <div class="actions">
            <button class="btn btn-primary btn-sm" onclick="event.stopPropagation();addToCart(${p.id})">🛒 Ajouter</button>
            <button class="btn btn-ghost btn-sm" onclick="event.stopPropagation();viewProduct(${p.id})">Détails</button>
          </div>
        </div>`
      }).join('') : `
        <div class="empty-state" style="grid-column:1/-1">
          <div class="empty-icon">🔍</div>
          <div class="empty-title">Aucun résultat</div>
          <div class="empty-desc">Essayez de modifier vos filtres ou votre recherche.</div>
        </div>`
      }
    </div>
  `
}

function setCat(c) {
  categoryFilter = c
  renderShop()
}

function viewProduct(id) {
  const p = STATE.products.find(x => x.id === id)
  if (!p) return

  const related = STATE.products.filter(x => x.category === p.category && x.id !== p.id).slice(0, 4)
  const stockLabel = p.stock <= 0 ? '<span style="color:var(--red)">Épuisé</span>' :
    p.stock < 10 ? `<span style="color:var(--orange)">Plus que ${p.stock} en stock</span>` :
    `<span style="color:var(--green)">En stock (${p.stock})</span>`

  openModal(escHtml(p.name), `
    <img src="${p.image}" style="width:100%;height:200px;object-fit:cover;border-radius:var(--radius-sm);margin-bottom:12px">
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;font-size:12px;margin-bottom:12px">
      <div><span class="text-muted">Prix</span><br><span style="font-size:20px;font-weight:800;color:var(--accent)">${formatPrice(p.price)}</span></div>
      <div><span class="text-muted">Stock</span><br>${stockLabel}</div>
      <div><span class="text-muted">Vendeur</span><br>${escHtml(p.seller)}</div>
      <div><span class="text-muted">Catégorie</span><br>${p.category}</div>
    </div>
    <div style="font-size:12px;color:var(--text-secondary);line-height:1.6;margin-bottom:12px">${escHtml(p.desc)}</div>
    <button class="btn btn-primary btn-block btn-lg" onclick="addToCart(${p.id});closeModal()">🛒 Ajouter au panier — ${formatPrice(p.price)}</button>
    ${related.length ? `
      <hr>
      <div style="font-size:11px;font-weight:600;margin-bottom:8px">Articles similaires</div>
      <div style="display:flex;gap:8px;overflow-x:auto">
        ${related.map(r => `
          <div style="min-width:120px;background:var(--bg-card);border-radius:var(--radius-sm);padding:8px;cursor:pointer" onclick="closeModal();viewProduct(${r.id})">
            <img src="${r.image}" style="width:100%;height:60px;object-fit:cover;border-radius:4px">
            <div style="font-size:9px;font-weight:600;margin-top:4px">${escHtml(r.name)}</div>
            <div style="font-size:11px;font-weight:700;color:var(--accent)">${formatPrice(r.price)}</div>
          </div>
        `).join('')}
      </div>` : ''}
  `)
}

// ===================== PANIER =====================
function addToCart(id) {
  const p = STATE.products.find(x => x.id === id)
  if (!p) return
  if (p.stock <= 0) return showToast('Article épuisé', 'error')

  const existing = STATE.cart.find(x => x.id === id)
  if (existing) {
    if (existing.qty >= p.stock) return showToast('Stock insuffisant', 'warning')
    existing.qty++
  } else {
    STATE.cart.push({ id: p.id, name: p.name, price: p.price, image: p.image, qty: 1, maxStock: p.stock })
  }
  saveState()
  updateCartBadge()
  showToast(`✓ ${p.name} ajouté au panier`, 'success')
}

function removeFromCart(id) {
  const item = STATE.cart.find(x => x.id === id)
  STATE.cart = STATE.cart.filter(x => x.id !== id)
  saveState()
  updateCartBadge()
  showToast(`✕ ${item ? item.name : 'Article'} retiré`, 'info')
  reRenderCurrent()
}

function changeQty(id, delta) {
  const item = STATE.cart.find(x => x.id === id)
  if (!item) return
  const p = STATE.products.find(x => x.id === id)
  item.qty += delta

  if (item.qty <= 0) { removeFromCart(id); return }
  if (p && item.qty > p.stock) { item.qty = p.stock; showToast('Stock maximum atteint', 'warning') }

  saveState()
  updateCartBadge()
  renderCart()
}

function renderCart() {
  const app = document.getElementById('mainContent')
  const total = STATE.cart.reduce((a, i) => a + i.price * i.qty, 0)

  if (!STATE.cart.length) {
    app.innerHTML = `
      <div class="topbar"><div class="topbar-left"><h1>🛒 Panier</h1></div></div>
      <div class="empty-state">
        <div class="empty-icon">🛒</div>
        <div class="empty-title">Votre panier est vide</div>
        <div class="empty-desc">Explorez la boutique pour ajouter des articles.</div>
        <button class="btn btn-primary mt-12" onclick="showPage('shop')">🏪 Découvrir la boutique</button>
      </div>
    `
    return
  }

  app.innerHTML = `
    <div class="topbar">
      <div class="topbar-left">
        <h1>🛒 Panier</h1>
        <span class="font-sm text-muted">${STATE.cart.reduce((a, i) => a + i.qty, 0)} article(s)</span>
      </div>
      <div class="topbar-right">
        <button class="btn btn-ghost btn-sm" onclick="STATE.cart=[];saveState();updateCartBadge();renderCart();showToast('Panier vidé','info')">🗑️ Vider</button>
      </div>
    </div>

    ${STATE.cart.map(i => `
      <div class="cart-item">
        <img src="${i.image}" alt="${escHtml(i.name)}" loading="lazy">
        <div class="info">
          <div class="name">${escHtml(i.name)}</div>
          <div class="price">${formatPrice(i.price)}</div>
        </div>
        <div class="qty">
          <button onclick="changeQty(${i.id}, -1)">−</button>
          <span>${i.qty}</span>
          <button onclick="changeQty(${i.id}, 1)">+</button>
        </div>
        <button class="btn btn-danger btn-sm" onclick="removeFromCart(${i.id})">✕</button>
      </div>
    `).join('')}

    <div class="cart-summary">
      <div class="total-row">
        <span class="total-label">Total</span>
        <span class="total-price">${formatPrice(total)}</span>
      </div>
      <button class="btn btn-success btn-block btn-lg mt-8" onclick="showCheckout()">
        💳 Commander — ${formatPrice(total)}
      </button>
    </div>
  `
}

// ===================== CHECKOUT =====================
function showCheckout() {
  const total = STATE.cart.reduce((a, i) => a + i.price * i.qty, 0)
  const items = STATE.cart.map(i =>
    `<div style="display:flex;justify-content:space-between;font-size:11px;padding:4px 0">
      <span>${i.qty}x ${escHtml(i.name)}</span>
      <span style="font-weight:600;color:var(--accent)">${formatPrice(i.price * i.qty)}</span>
    </div>`
  ).join('')

  openModal('💳 Finaliser la commande', `
    <div style="background:var(--bg-card);border-radius:var(--radius-sm);padding:12px;margin-bottom:12px;border:1px solid var(--border)">
      <div style="font-size:11px;font-weight:600;margin-bottom:6px">Récapitulatif</div>
      ${items}
      <hr style="border-color:var(--border);margin:8px 0">
      <div style="display:flex;justify-content:space-between;font-size:14px;font-weight:700">
        <span>Total</span>
        <span style="color:var(--accent)">${formatPrice(total)}</span>
      </div>
    </div>

    <div class="input-group">
      <label>Nom complet *</label>
      <input class="input" id="checkName" placeholder="Votre nom" required>
    </div>
    <div class="input-group">
      <label>Téléphone (Orange Money / MTN MoMo / Wave) *</label>
      <input class="input" id="checkPhone" placeholder="+225 01 XX XX XX XX" type="tel" required>
    </div>
    <div class="flex gap-4">
      <div class="input-group" style="flex:1">
        <label>Email (pour le reçu)</label>
        <input class="input" id="checkEmail" placeholder="email@exemple.com" type="email">
      </div>
      <div class="input-group" style="flex:1">
        <label>Moyen de paiement</label>
        <select class="input" id="checkMethod">
          <option value="orange">Orange Money CI</option>
          <option value="mtn">MTN MoMo CI</option>
          <option value="wave">Wave CI</option>
          <option value="paydunya">PayDunya (Carte/Canal+)</option>
        </select>
      </div>
    </div>
    <div class="input-group">
      <label>Adresse de livraison (optionnel)</label>
      <textarea class="textarea" id="checkAddress" rows="2" placeholder="Abidjan, Cocody..."></textarea>
    </div>

    <button class="btn btn-success btn-block btn-lg mt-8" onclick="placeOrder()">
      ✅ Confirmer et payer ${formatPrice(total)}
    </button>
    <div style="font-size:9px;color:var(--text-muted);text-align:center;margin-top:8px">
      🔒 Paiement sécurisé via PayDunya / Mobile Money CI
    </div>
  `)
}

function placeOrder() {
  const name = document.getElementById('checkName')?.value.trim()
  const phone = document.getElementById('checkPhone')?.value.trim()
  const email = document.getElementById('checkEmail')?.value.trim()
  const method = document.getElementById('checkMethod')?.value
  const address = document.getElementById('checkAddress')?.value.trim()

  // Validation
  const errors = []
  if (!name) errors.push('Nom requis')
  if (!phone) errors.push('Téléphone requis')
  else if (phone.replace(/[\s+]/g, '').length < 8) errors.push('Numéro invalide')

  if (errors.length) {
    return showToast('❌ ' + errors.join(' · '), 'error')
  }

  const total = STATE.cart.reduce((a, i) => a + i.price * i.qty, 0)
  const order = {
    id: 'NX-' + Date.now().toString(36).toUpperCase() + '-' + Math.random().toString(36).substr(2, 4).toUpperCase(),
    date: new Date().toISOString(),
    name, phone, email, method, address,
    items: STATE.cart.map(i => ({ ...i })),
    total,
    status: 'payé',
    paymentRef: 'PAY-' + Math.random().toString(36).substr(2, 10).toUpperCase()
  }

  STATE.orders.push(order)
  STATE.cart = []
  saveState()
  updateCartBadge()
  closeModal()
  showToast(`✅ Commande ${order.id} confirmée ! Reçu envoyé par email.`, 'success')
  showPage('orders')
}

// ===================== COMMANDES =====================
function renderOrders() {
  const app = document.getElementById('mainContent')

  if (!STATE.orders.length) {
    app.innerHTML = `
      <div class="topbar"><div class="topbar-left"><h1>📦 Mes commandes</h1></div></div>
      <div class="empty-state">
        <div class="empty-icon">📦</div>
        <div class="empty-title">Aucune commande</div>
        <div class="empty-desc">Passez votre première commande dès maintenant.</div>
        <button class="btn btn-primary mt-12" onclick="showPage('shop')">🏪 Boutique</button>
      </div>
    `
    return
  }

  app.innerHTML = `
    <div class="topbar">
      <div class="topbar-left">
        <h1>📦 Mes commandes</h1>
        <span class="font-sm text-muted">${STATE.orders.length} commande(s)</span>
      </div>
    </div>
    ${STATE.orders.slice().reverse().map(o => `
      <div class="order-card">
        <div class="order-header">
          <span class="order-id">⟡ ${o.id}</span>
          <span class="order-date">${formatDate(o.date)}</span>
        </div>
        <div class="order-items">
          ${o.items.map(i => `${i.qty}x ${escHtml(i.name)}`).join(', ')}
        </div>
        <div class="order-footer">
          <span class="order-status">${o.status}</span>
          <span class="order-total">${formatPrice(o.total)}</span>
        </div>
        <div class="order-meta">
          ${escHtml(o.name)} · ${escHtml(o.phone)} · Réf: ${o.paymentRef}
          ${o.method ? '· ' + o.method : ''}
        </div>
      </div>
    `).join('')}
  `
}

// ----- VENDRE -----
function renderSell(){
  const app=document.getElementById('mainContent')
  app.innerHTML=`
    <div class="header"><h1>💰 Vendre un article</h1></div>
    <div style="max-width:500px;margin:auto">
      <div class="input-group"><label>Nom de l'article</label><input class="input" id="sellName" placeholder="Ex: Pack OSINT Premium"></div>
      <div class="input-group"><label>Description détaillée</label><textarea class="textarea" id="sellDesc" rows="3" placeholder="Décrivez votre article..."></textarea></div>
      <div class="flex">
        <div class="input-group" style="flex:1"><label>Prix (FCFA)</label><input class="input" id="sellPrice" type="number" placeholder="15000"></div>
        <div class="input-group" style="flex:1"><label>Stock</label><input class="input" id="sellStock" type="number" value="10"></div>
      </div>
      <div class="input-group"><label>Catégorie</label>
        <select id="sellCat" style="width:100%;background:var(--card2);border:1px solid var(--border);border-radius:6px;padding:8px;color:var(--text);font-size:10px">
          <option value="outils">🔧 Outils</option>
          <option value="formations">📚 Formations</option>
          <option value="rapports">📊 Rapports</option>
          <option value="données">💾 Données</option>
          <option value="merch">👕 Merch</option>
          <option value="abonnements">📅 Abonnements</option>
          <option value="autres">📦 Autres</option>
        </select>
      </div>
      <div class="input-group"><label>Image URL (ou upload)</label>
        <input class="input" id="sellImage" placeholder="https://...">
        <input type="file" id="sellImageFile" accept="image/*" style="width:100%;margin-top:4px;font-size:9px;color:var(--text2)" onchange="previewSellImage(event)">
        <div id="sellImagePreview" style="margin-top:4px;height:80px;background:var(--card2);border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:7px;color:var(--text2);overflow:hidden"></div>
      </div>
      <div class="input-group"><label>Votre nom de vendeur</label><input class="input" id="sellSeller" placeholder="Votre pseudo"></div>
      <button class="btn btn-success btn-block" onclick="submitProduct()">📦 Mettre en vente</button>
    </div>
  `
}

function previewSellImage(event){
  const file=event.target.files[0]
  if(!file)return
  const reader=new FileReader()
  reader.onload=function(e){
    document.getElementById('sellImagePreview').innerHTML=`<img src="${e.target.result}" style="width:100%;height:100%;object-fit:cover">`
    document.getElementById('sellImage').value='UPLOAD:'+e.target.result
  }
  reader.readAsDataURL(file)
}

function submitProduct(){
  const name=document.getElementById('sellName')?.value.trim()
  const desc=document.getElementById('sellDesc')?.value.trim()
  const price=parseInt(document.getElementById('sellPrice')?.value)
  const stock=parseInt(document.getElementById('sellStock')?.value)||1
  const cat=document.getElementById('sellCat')?.value
  let img=document.getElementById('sellImage')?.value.trim()
  const seller=document.getElementById('sellSeller')?.value.trim()||'Vendeur NEXUS'

  if(!name||!desc||!price)return showToast('❌ Remplissez tous les champs')
  if(price<100)return showToast('❌ Prix minimum 100 FCFA')
  if(!img)img='https://placehold.co/300x200/1a1a28/ff6600?text='+encodeURIComponent(name.substring(0,15))

  STATE.products.push({
    id:STATE.nextId++,
    name,desc,price,category:cat,
    image:img.startsWith('UPLOAD:')?img.replace('UPLOAD:',''):img,
    stock,seller,date:new Date().toISOString()
  })
  saveState()
  showToast(`✅ "${escHtml(name)}" mis en vente !`)
  showPage('shop')
}

// ----- ADMIN -----
function renderAdmin(){
  const app=document.getElementById('mainContent')
  const totalVentes=STATE.orders.reduce((a,o)=>a+o.total,0)
  app.innerHTML=`
    <div class="header"><h1>⚙️ Administration</h1></div>
    <div class="stats-grid" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:8px;margin-bottom:12px">
      <div class="card"><div style="font-size:18px;font-weight:700;color:var(--accent)">${STATE.products.length}</div><div style="font-size:8px;color:var(--text2)">Articles</div></div>
      <div class="card"><div style="font-size:18px;font-weight:700;color:var(--green)">${STATE.orders.length}</div><div style="font-size:8px;color:var(--text2)">Commandes</div></div>
      <div class="card"><div style="font-size:18px;font-weight:700;color:var(--orange)">${formatPrice(totalVentes)}</div><div style="font-size:8px;color:var(--text2)">CA Total</div></div>
      <div class="card"><div style="font-size:18px;font-weight:700">${STATE.cart.reduce((a,i)=>a+i.qty,0)}</div><div style="font-size:8px;color:var(--text2)">Panier actuel</div></div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
      <div class="card"><h3 style="font-size:10px;margin-bottom:6px">📦 Dernières commandes</h3>
        ${STATE.orders.slice(-5).reverse().map(o=>`
          <div style="font-size:7px;padding:2px 0;border-bottom:1px solid var(--border)">⟡ ${o.id} — ${formatPrice(o.total)} — ${o.status}</div>
        `).join('')||'<span style="font-size:8px;color:var(--text2)">Aucune commande</span>'}
      </div>
      <div class="card"><h3 style="font-size:10px;margin-bottom:6px">💾 Sauvegarde</h3>
        <button class="btn btn-sm btn-primary btn-block" onclick="exportMarketData()">📤 Exporter données</button>
        <button class="btn btn-sm btn-primary btn-block mt-6" onclick="document.getElementById('importMarketFile').click()">📥 Importer</button>
        <input type="file" id="importMarketFile" style="display:none" onchange="importMarketData(event)" accept=".json">
        <button class="btn btn-sm btn-danger btn-block mt-6" onclick="resetMarket()">🗑️ Réinitialiser</button>
      </div>
    </div>
    <div class="card mt-6"><h3 style="font-size:10px;margin-bottom:6px">📋 Articles en vente</h3>
      ${STATE.products.map(p=>`
        <div style="display:flex;justify-content:space-between;font-size:8px;padding:2px 0;border-bottom:1px solid var(--border)">
          <span>${escHtml(p.name)}</span>
          <span>${formatPrice(p.price)} · Stock: ${p.stock} · ${escHtml(p.seller)}</span>
        </div>
      `).join('')}
    </div>
  `
}

function exportMarketData(){
  const blob=new Blob([JSON.stringify(STATE,null,2)],{type:'application/json'})
  const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download=`NEXUS_MARKET_${new Date().toISOString().slice(0,10)}.json`;a.click()
  showToast('✅ Données exportées')
}

function importMarketData(event){
  const file=event.target.files[0];if(!file)return
  const reader=new FileReader()
  reader.onload=function(e){
    try{
      const d=JSON.parse(e.target.result)
      Object.keys(d).forEach(k=>{STATE[k]=d[k]})
      saveState();updateCartBadge();showToast('✅ Données importées')
    }catch(err){showToast('❌ Erreur: '+err.message)}
  }
  reader.readAsText(file)
  event.target.value=''
}

function resetMarket(){
  if(!confirm('🗑️ Réinitialiser toutes les données ?'))return
  STATE.cart=[];STATE.orders=[];STATE.products=STATE.products.slice(0,8)
  saveState();updateCartBadge();showToast('🗑️ Réinitialisé')
}

// ===================== STOCKAGE =====================
function saveState(){
  try{localStorage.setItem('nexus-market',JSON.stringify(STATE))}catch(e){}
}
function loadState(){
  try{
    const s=localStorage.getItem('nexus-market')
    if(s){const d=JSON.parse(s);Object.keys(d).forEach(k=>{STATE[k]=d[k]})}
  }catch(e){}
}

// ===================== INIT =====================
loadState()
updateCartBadge()
showPage('shop')
setInterval(saveState,30000)
console.log('⟡ NEXUS MARKETPLACE v1.0 — Prêt')
</script>
</body>
</html>
