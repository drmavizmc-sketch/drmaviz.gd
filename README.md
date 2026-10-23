<!DOCTYPE html>
<html lang="en" class="dark scroll-smooth select-none">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>DrMaviz.games — Ultra-Realistic Liquid Glass Vault</title>

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Fira+Code:wght@400;600&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            orbitron: ['Orbitron', 'sans-serif'],
            sans: ['Plus Jakarta Sans', 'sans-serif'],
            mono: ['Fira Code', 'monospace'],
          }
        }
      }
    }
  </script>

  <style>
    /* Pure OLED Base */
    body {
      background-color: #000000;
      color: #ffffff;
      overflow-x: hidden;
      font-family: 'Plus Jakarta Sans', sans-serif;
    }

    /* Background Image */
    .flower-bg {
      position: fixed;
      inset: 0;
      z-index: -1;
      background-image: url('906982812476854291(1).jpg');[cite: 5]
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }

    .flower-bg-overlay {
      position: fixed;
      inset: 0;
      z-index: -1;
      background: radial-gradient(circle at center, rgba(0, 0, 0, 0.2) 0%, rgba(0, 0, 0, 0.85) 100%), rgba(0, 0, 0, 0.5);
      pointer-events: none;
    }

    /* Custom Scrollbar */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: #000000; }
    ::-webkit-scrollbar-thumb { background: rgba(255, 255, 255, 0.2); border-radius: 3px; }
    ::-webkit-scrollbar-thumb:hover { background: rgba(255, 255, 255, 0.5); box-shadow: 0 0 12px rgba(255, 255, 255, 0.8); }

    /* --- ULTRA-REALISTIC LIQUID GLASS TIER SYSTEM --- */
    .liquid-glass-tier-1 {
      background: rgba(18, 18, 26, 0.58);
      backdrop-filter: blur(50px) saturate(220%);
      -webkit-backdrop-filter: blur(50px) saturate(220%);
      border: 1px solid rgba(255, 255, 255, 0.18);
      border-top: 1px solid rgba(255, 255, 255, 0.35);
      border-left: 1px solid rgba(255, 255, 255, 0.25);
      box-shadow: 0 40px 80px -20px rgba(0, 0, 0, 0.95), 
                  inset 0 1px 0 rgba(255, 255, 255, 0.4), 
                  inset 0 -1px 0 rgba(0, 0, 0, 0.6);
    }

    .liquid-glass-tier-2 {
      background: rgba(24, 24, 35, 0.45);
      backdrop-filter: blur(35px) saturate(200%);
      -webkit-backdrop-filter: blur(35px) saturate(200%);
      border: 1px solid rgba(255, 255, 255, 0.15);
      border-top: 1px solid rgba(255, 255, 255, 0.3);
      box-shadow: 0 25px 50px rgba(0, 0, 0, 0.8), 
                  inset 0 1px 0 rgba(255, 255, 255, 0.25);
      transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .liquid-glass-tier-2:hover {
      background: rgba(30, 30, 45, 0.6);
      border-color: rgba(168, 85, 247, 0.6);
      border-top-color: rgba(168, 85, 247, 0.9);
      transform: translateY(-6px) scale(1.01);
      box-shadow: 0 35px 70px -10px rgba(168, 85, 247, 0.3), 
                  0 20px 40px rgba(0, 0, 0, 0.9),
                  inset 0 1px 0 rgba(255, 255, 255, 0.5);
    }

    .liquid-glass-tier-3 {
      background: rgba(35, 35, 50, 0.5);
      backdrop-filter: blur(20px) saturate(180%);
      -webkit-backdrop-filter: blur(20px) saturate(180%);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-top: 1px solid rgba(255, 255, 255, 0.35);
      box-shadow: 0 15px 30px rgba(0,0,0,0.6), inset 0 1px 0 rgba(255,255,255,0.3);
    }

    .oled-nav {
      background: rgba(0, 0, 0, 0.75);
      backdrop-filter: blur(40px) saturate(200%);
      -webkit-backdrop-filter: blur(40px) saturate(200%);
      border-bottom: 1px solid rgba(255, 255, 255, 0.12);
      box-shadow: 0 15px 35px rgba(0,0,0,0.8);
    }

    /* Inputs & Buttons with Specular Glass Glint */
    .liquid-input {
      background: rgba(255, 255, 255, 0.04);
      border: 1px solid rgba(255, 255, 255, 0.18);
      border-top: 1px solid rgba(255, 255, 255, 0.3);
      backdrop-filter: blur(15px);
      transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
      color: #ffffff;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.1);
    }
    .liquid-input:focus {
      border-color: rgba(168, 85, 247, 0.9);
      box-shadow: 0 0 30px rgba(168, 85, 247, 0.4), inset 0 1px 0 rgba(255, 255, 255, 0.4);
      background: rgba(255, 255, 255, 0.08);
      outline: none;
    }

    .liquid-btn-primary {
      background: linear-gradient(135deg, rgba(168, 85, 247, 0.85) 0%, rgba(139, 92, 246, 0.95) 50%, rgba(236, 72, 153, 0.85) 100%);
      color: #ffffff;
      font-weight: 700;
      border: 1px solid rgba(255, 255, 255, 0.4);
      border-top: 1px solid rgba(255, 255, 255, 0.6);
      box-shadow: 0 12px 35px rgba(168, 85, 247, 0.45), inset 0 1px 0 rgba(255, 255, 255, 0.6);
      transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
      border-radius: 9999px;
    }
    .liquid-btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 18px 45px rgba(168, 85, 247, 0.65), inset 0 1px 0 rgba(255, 255, 255, 0.8);
      filter: brightness(1.1);
    }

    .liquid-btn-secondary {
      background: linear-gradient(135deg, rgba(6, 182, 212, 0.75) 0%, rgba(59, 130, 246, 0.85) 100%);
      color: #ffffff;
      font-weight: 700;
      border: 1px solid rgba(255, 255, 255, 0.35);
      border-top: 1px solid rgba(255, 255, 255, 0.55);
      box-shadow: 0 12px 35px rgba(6, 182, 212, 0.4), inset 0 1px 0 rgba(255, 255, 255, 0.6);
      transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
      border-radius: 9999px;
    }
    .liquid-btn-secondary:hover {
      transform: translateY(-2px);
      box-shadow: 0 18px 45px rgba(6, 182, 212, 0.6), inset 0 1px 0 rgba(255, 255, 255, 0.8);
      filter: brightness(1.1);
    }

    .liquid-btn-outline {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-top: 1px solid rgba(255, 255, 255, 0.35);
      color: #ffffff;
      backdrop-filter: blur(15px);
      transition: all 0.3s ease;
      box-shadow: 0 10px 25px rgba(0,0,0,0.4), inset 0 1px 0 rgba(255,255,255,0.2);
      border-radius: 9999px;
    }
    .liquid-btn-outline:hover {
      background: rgba(255, 255, 255, 0.12);
      border-color: rgba(255, 255, 255, 0.5);
      box-shadow: 0 15px 35px rgba(168, 85, 247, 0.3), inset 0 1px 0 rgba(255, 255, 255, 0.4);
      transform: translateY(-1px);
    }

    .card-action-btn {
      width: 36px; height: 36px; border-radius: 9999px;
      display: flex; align-items: center; justify-content: center;
      background: rgba(15,15,22,0.65); color: #fff;
      border: 1px solid rgba(255,255,255,0.25);
      border-top: 1px solid rgba(255,255,255,0.45);
      backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.5), inset 0 1px 0 rgba(255,255,255,0.3);
      transition: all 0.25s ease; cursor: pointer;
    }
    .card-action-btn:hover { background: rgba(6,182,212,0.5); border-color: rgba(6,182,212,0.95); transform: scale(1.1); }
    .card-action-btn.danger:hover { background: rgba(239,68,68,0.6); border-color: rgba(248,113,113,0.95); }
    
    .liquid-btn-danger {
      background: linear-gradient(135deg, rgba(239,68,68,0.9) 0%, rgba(190,18,60,0.95) 100%);
      color: #fff; font-weight: 700; border: 1px solid rgba(255,255,255,0.35);
      box-shadow: 0 10px 30px rgba(239,68,68,0.4), inset 0 1px 0 rgba(255,255,255,0.4);
      border-radius: 9999px; transition: all 0.3s ease;
    }
    .liquid-btn-danger:hover { transform: translateY(-2px); filter: brightness(1.1); }

    /* ===== SCROLL SCENES ===== */
    .scene-track { position: relative; width: 100vw; margin-left: calc(50% - 50vw); }
    .scene-stage { position: sticky; top: 0; height: 100vh; overflow: hidden; }
    .scene { position: absolute; inset: 0; pointer-events: none; }
    .scene.active { pointer-events: auto; z-index: 2; }
    .scene .s-bg { opacity: 0; transition: opacity 1s ease; }
    .scene.active .s-bg { opacity: 1; }
    .scene .poster-img.s-bgimg { transform: scale(1.12); transition: opacity .6s ease, transform 7s cubic-bezier(.16,1,.3,1); }
    .scene.active .poster-img.s-bgimg { transform: scale(1); }
    .poster-img.loaded.s-bgimg { opacity: .45; }
    .scene .s-line { opacity: 0; transform: translateY(46px); transition: opacity .7s ease, transform .8s cubic-bezier(.16,1,.3,1); }
    .scene.active .s-line { opacity: 1; transform: none; transition-delay: calc(var(--i) * .09s + .3s); }
    .scene.past .s-line { transform: translateY(-46px); }
    .scene .s-frame { opacity: 0; transform: translateX(180px) scale(.96); transition: opacity .7s ease, transform 1.1s cubic-bezier(.16,1,.3,1); }
    .scene.active .s-frame { opacity: 1; transform: none; transition-delay: .15s; }
    .scene.past .s-frame { transform: translateX(-140px) scale(.96); }
    .scene-dots { position: absolute; right: 2vw; top: 50%; transform: translateY(-50%); display: flex; flex-direction: column; align-items: center; gap: var(--dg, 10px); z-index: 20; }
    .scene-dot { position: relative; width: var(--ds, 10px); height: var(--ds, 10px); border-radius: 9999px; background: rgba(255,255,255,.28); cursor: pointer; border: 0; padding: 0;
      transform: scale(calc(1 + .5 * var(--k, 0)), calc(1 + 1.6 * var(--k, 0))); transition: transform .15s linear, box-shadow .3s ease, background .3s ease; }
    .scene-dot::after { content: ''; position: absolute; inset: 0; border-radius: inherit; background: linear-gradient(#c084fc, #ec4899); box-shadow: 0 0 16px rgba(168,85,247,.95), 0 0 32px rgba(236,72,153,.55); opacity: var(--k, 0); }
    .scene-dot::before { content: attr(data-t); position: absolute; right: 26px; top: 50%; transform: translateY(-50%) translateX(8px); white-space: nowrap; font: 700 10px 'Orbitron', sans-serif; letter-spacing: .12em; color: #fff; background: rgba(0,0,0,.85); border: 1px solid rgba(255,255,255,.25); padding: 5px 12px; border-radius: 9999px; opacity: 0; pointer-events: none; backdrop-filter: blur(10px); transition: opacity .3s ease, transform .3s ease; }
    .scene-dot.on { z-index: 2; }
    .scene-dot.on::before, .scene-dot:hover::before { opacity: 1; transform: translateY(-50%) translateX(0); }
    .scene-dot:hover { background: rgba(255,255,255,.6); }
    .scene-dots.scrolling .scene-dot {
      background: rgba(255,255,255, calc(.28 + .6 * var(--g, 0)));
      box-shadow: 0 0 calc(18px * var(--g, 0)) rgba(168,85,247, calc(.95 * var(--g, 0))), 0 0 calc(36px * var(--g, 0)) rgba(236,72,153, calc(.55 * var(--g, 0)));
    }
    .scene-hint { position: absolute; bottom: 26px; left: 50%; transform: translateX(-50%); z-index: 20; text-align: center; font-family: 'Orbitron', sans-serif; font-size: 10px; letter-spacing: .35em; color: #9ca3af; transition: opacity .5s ease; pointer-events: none; }
    .scene-hint::after { content: ''; display: block; width: 1px; height: 28px; margin: 8px auto 0; background: linear-gradient(#a855f7, transparent); animation: hintPulse 1.6s ease-in-out infinite; }
    .scene-hint.gone { opacity: 0; }
    @keyframes hintPulse { 0%,100% { transform: scaleY(.3); transform-origin: top; } 50% { transform: scaleY(1); transform-origin: top; } }

    .poster-img { opacity: 0; transition: opacity .6s ease, transform .7s cubic-bezier(.16,1,.3,1); }
    .poster-img.loaded { opacity: 1; }

    #gameModal, #uploadModal, #deleteModal, #posterModal, #renameModal, #dropOverlay, #signInGate {
      backdrop-filter: blur(30px) !important; background: rgba(0,0,0,0.85) !important;
    }
    #gameModal.opacity-0, #uploadModal.opacity-0, #deleteModal.opacity-0, #posterModal.opacity-0, #renameModal.opacity-0 {
      visibility: hidden; transition: opacity .3s ease, visibility 0s linear .3s;
    }
  </style>
</head>
<body class="relative antialiased selection:bg-purple-500 selection:text-white">

  <!-- ULTRA-REALISTIC LIQUID GLASS BACKGROUND -->
  <div class="flower-bg"></div>
  <div class="flower-bg-overlay"></div>

  <!-- SIGN-IN GATE MODAL -->
  <div id="signInGate" class="fixed inset-0 z-50 flex items-center justify-center p-4">
    <div class="liquid-glass-tier-1 w-full max-w-md rounded-3xl p-8 shadow-2xl relative z-10 text-center">
      <div class="w-16 h-16 mx-auto mb-5 rounded-2xl overflow-hidden liquid-glass-tier-3 p-1 flex items-center justify-center shadow-xl">
        <img src="Gemini_Generated_Image.png" alt="Avatar Icon" class="w-full h-full object-cover rounded-xl">[cite: 6]
      </div>
      <h2 class="font-orbitron text-2xl font-black text-white mb-1">SIGN IN TO VAULT</h2>
      <p class="text-xs text-gray-400 font-mono mb-6">Enter your username to access DrMaviz.games</p>
      
      <form onsubmit="handleSignIn(event)" class="space-y-4">
        <div class="text-left">
          <label class="block text-[11px] font-orbitron font-bold text-cyan-300 mb-2 uppercase tracking-wider">Username</label>
          <div class="relative">
            <i data-lucide="user" class="w-4 h-4 text-gray-400 absolute left-4 top-1/2 -translate-y-1/2"></i>
            <input type="text" id="signInUsername" placeholder="e.g. GamerPro99" required autocomplete="off" class="w-full pl-11 pr-4 py-3.5 rounded-full liquid-input text-xs font-semibold text-white placeholder-gray-500" />
          </div>
        </div>
        
        <button type="submit" class="w-full liquid-btn-primary py-3.5 font-orbitron text-xs tracking-wider uppercase mt-2">
          UNLOCK VAULT ACCESS
        </button>
      </form>
    </div>
  </div>

  <!-- NAVIGATION HEADER -->
  <header class="fixed top-0 left-0 right-0 z-40 oled-nav">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
      
      <!-- Brand Logo featuring Custom Avatar Icon -->
      <a href="#" class="flex items-center gap-3 group">
        <div class="w-12 h-12 rounded-2xl liquid-glass-tier-3 p-0.5 group-hover:scale-105 transition-transform flex items-center justify-center overflow-hidden shadow-lg border border-white/20">
          <img src="Gemini_Generated_Image.png" alt="DrMaviz Icon" class="w-full h-full object-cover rounded-[14px]">[cite: 6]
        </div>
        <div>
          <span class="font-orbitron text-xl font-black tracking-wider text-white">DrMaviz<span class="text-purple-400">.games</span></span>
          <span class="block text-[9px] font-mono text-cyan-400 -mt-1 tracking-widest uppercase">LIQUID GLASS VAULT</span>
        </div>
      </a>

      <!-- Navigation Links -->
      <nav id="unlockedNav" class="hidden md:flex items-center space-x-8 text-xs font-bold tracking-widest font-orbitron">
        <a href="#grid3d" class="text-gray-300 hover:text-white transition-colors flex items-center gap-1.5"><i data-lucide="grid" class="w-3.5 h-3.5 text-purple-400"></i> STEAM DECK</a>
        <a href="#coverflow" class="text-gray-300 hover:text-white transition-colors flex items-center gap-1.5"><i data-lucide="layers" class="w-3.5 h-3.5 text-cyan-400"></i> 3D COVERFLOW</a>
        <a href="#lua-vault" class="text-white hover:text-purple-300 transition-colors flex items-center gap-1.5">
          <i data-lucide="terminal" class="w-4 h-4 text-pink-400"></i> LUA VAULT
        </a>
      </nav>

      <!-- Right User Member State Pill -->
      <div class="flex items-center gap-3">
        <div id="userProfilePill" class="hidden px-4 py-2 rounded-full liquid-glass-tier-3 flex items-center gap-2.5">
          <div class="w-2.5 h-2.5 rounded-full bg-emerald-400 animate-pulse shadow-[0_0_10px_rgba(52,211,153,0.8)]"></div>
          <span id="displayUsername" class="font-orbitron text-[11px] font-bold text-gray-200">USER</span>
          <button onclick="handleSignOut()" title="Sign Out" class="ml-2 text-gray-400 hover:text-red-400 transition-colors">
            <i data-lucide="log-out" class="w-3.5 h-3.5"></i>
          </button>
        </div>
      </div>
    </div>
  </header>

  <!-- MAIN SCROLL CONTAINER -->
  <main class="relative z-10 pt-28 pb-20">

    <!-- UNLOCKED CONTENT VAULT -->
    <div id="unlockedVault" class="hidden">

      <!-- ADMIN PUBLISHER BANNER -->
      <div id="adminBanner" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 mb-12">
        <div class="p-6 sm:p-8 rounded-3xl liquid-glass-tier-1 flex flex-col sm:flex-row items-center justify-between gap-6 relative overflow-hidden">
          <div class="absolute -right-20 -bottom-20 w-60 h-60 bg-purple-500/20 rounded-full blur-3xl pointer-events-none"></div>
          <div class="flex items-center gap-4 relative z-10">
            <div class="w-14 h-14 rounded-2xl liquid-glass-tier-3 flex items-center justify-center text-purple-400 shadow-xl shrink-0 overflow-hidden">
              <img src="Gemini_Generated_Image.png" alt="Avatar" class="w-full h-full object-cover">[cite: 6]
            </div>
            <div>
              <div class="inline-flex items-center gap-1.5 px-3 py-0.5 rounded-full bg-purple-500/20 border border-purple-500/40 text-purple-300 font-mono text-[10px] uppercase tracking-wider mb-1">
                Developer Mode Active
              </div>
              <h3 class="font-orbitron text-xl sm:text-2xl font-black text-white">CREATOR PUBLISHER STUDIO</h3>
              <p class="text-xs text-gray-400 font-mono mt-0.5">Import custom .lua files, auto-fetch Steam posters, and manage executable trainers.</p>
            </div>
          </div>

          <button onclick="openUploadModal()" class="liquid-btn-primary px-7 py-3.5 font-orbitron text-xs tracking-wider flex items-center gap-2.5 whitespace-nowrap relative z-10">
            <i data-lucide="upload-cloud" class="w-4 h-4"></i>
            <span>+ UPLOAD GAME LUA SCRIPT</span>
          </button>
        </div>
      </div>

      <!-- SECTION 1: 3D STEAM CASCADE DECK -->
      <section id="grid3d" class="py-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
        <div class="flex flex-col md:flex-row md:items-end justify-between mb-10 gap-6">
          <div>
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-cyan-500/10 border border-cyan-500/30 text-cyan-300 font-mono text-xs mb-3">
              <i data-lucide="sparkles" class="w-3.5 h-3.5"></i> ULTRA LIQUID DECK
            </div>
            <h2 class="font-orbitron text-3xl sm:text-5xl font-black text-white">STEAM GAMES <span class="bg-gradient-to-r from-purple-400 via-pink-400 to-cyan-400 bg-clip-text text-transparent">VAULT</span></h2>
          </div>

          <div class="flex flex-col sm:flex-row items-center gap-3 w-full md:w-auto">
            <button type="button" onclick="openUploadModal()" class="w-full sm:w-auto liquid-btn-secondary px-5 py-3 font-orbitron text-xs tracking-wider flex items-center justify-center gap-2 whitespace-nowrap">
              <i data-lucide="upload-cloud" class="w-4 h-4"></i>
              <span>UPLOAD LUA FILES</span>
            </button>
            <button type="button" onclick="document.getElementById('aiFileInput').click()" class="w-full sm:w-auto liquid-btn-primary px-5 py-3 font-orbitron text-xs tracking-wider flex items-center justify-center gap-2 whitespace-nowrap">
              <i data-lucide="sparkles" class="w-4 h-4"></i>
              <span>AI AUTO IMPORT</span>
            </button>
            <input id="aiFileInput" type="file" accept=".lua,text/plain" multiple class="hidden" onchange="importLuaFiles(event)" />
            <div class="relative w-full sm:w-64">
              <i data-lucide="search" class="w-4 h-4 text-gray-400 absolute left-4 top-1/2 -translate-y-1/2"></i>
              <input type="text" id="searchInput" oninput="debouncedFilter()" placeholder="Search all games..." class="w-full pl-11 pr-4 py-3 rounded-full liquid-input text-xs placeholder-gray-400" />
            </div>

            <select id="genreFilter" onchange="filterGames()" class="w-full sm:w-auto px-4 py-3 rounded-full liquid-input text-xs text-gray-200 focus:outline-none bg-[#0a0a0f]/80 cursor-pointer">
              <option value="ALL">All Categories</option>
              <option value="Action">Action & RPG</option>
              <option value="Open World">Open World</option>
              <option value="FPS">FPS & Shooters</option>
              <option value="Racing">Racing & Sim</option>
            </select>
          </div>
        </div>

        <div id="deckContainer" class="perspective-stage grid grid-cols-1 gap-8">
          <!-- Dynamically Populated -->
        </div>
      </section>

      <!-- SECTION 2: 3D COVERFLOW GALLERY -->
      <section id="coverflow" class="py-24 relative overflow-hidden my-12 border-y border-white/10 bg-black/40 backdrop-blur-3xl">
        <div class="absolute inset-0 bg-gradient-to-r from-purple-900/10 via-transparent to-cyan-900/10 pointer-events-none"></div>
        <div class="text-center mb-12 px-4 relative z-10">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-pink-500/10 border border-pink-500/30 text-pink-300 font-mono text-xs mb-3">
            <i data-lucide="box" class="w-3.5 h-3.5"></i> IMMERSIVE CAROUSEL
          </div>
          <h2 class="font-orbitron text-3xl sm:text-5xl font-black text-white">3D <span class="bg-gradient-to-r from-pink-400 to-purple-400 bg-clip-text text-transparent">COVERFLOW</span></h2>
        </div>

        <div class="relative w-full overflow-hidden py-10">
          <div id="coverflowTrack" class="perspective-stage flex items-center justify-center gap-4 px-8 min-h-[400px] cursor-grab">
            <!-- Dynamically Populated -->
          </div>

          <div class="flex items-center justify-center gap-6 mt-10 relative z-10">
            <button id="prevBtn" class="p-4 rounded-full liquid-glass-tier-2 hover:bg-white/20 text-white transition-all shadow-xl">
              <i data-lucide="chevron-left" class="w-6 h-6"></i>
            </button>
            <span id="coverflowCounter" class="font-orbitron text-sm font-bold text-cyan-400 px-4 py-2 rounded-full liquid-glass-tier-3">1 / 9</span>
            <button id="nextBtn" class="p-4 rounded-full liquid-glass-tier-2 hover:bg-white/20 text-white transition-all shadow-xl">
              <i data-lucide="chevron-right" class="w-6 h-6"></i>
            </button>
          </div>
        </div>
      </section>

      <!-- SECTION 3: LUA VAULT -->
      <section id="lua-vault" class="py-16 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">
        <div class="liquid-glass-tier-1 rounded-3xl p-8 sm:p-12 relative overflow-hidden shadow-2xl">
          <div class="absolute top-0 right-0 w-96 h-96 bg-cyan-500/10 rounded-full blur-3xl pointer-events-none"></div>
          <div class="flex flex-col lg:flex-row lg:items-center justify-between gap-8 mb-10 relative z-10">
            <div>
              <div class="inline-flex items-center gap-2 px-3.5 py-1 rounded-full bg-cyan-500/15 border border-cyan-500/30 text-cyan-300 font-mono text-xs mb-3">
                <i data-lucide="terminal" class="w-3.5 h-3.5"></i>
                DRMAVIZ EXECUTION VAULT
              </div>
              <h2 class="font-orbitron text-3xl sm:text-4xl font-black text-white">STEAM <span class="text-purple-400">LUA SCRIPTS</span> HUB</h2>
              <p class="text-gray-400 text-sm mt-2">Import your own Lua mods/configuration files, search your library, and download instantly.</p>
            </div>
          </div>

          <div id="luaVaultGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 relative z-10">
            <!-- Dynamically Populated -->
          </div>
        </div>
      </section>

    </div>

  </main>

  <!-- FOOTER -->
  <footer class="border-t border-white/10 bg-black/60 backdrop-blur-md py-12 relative z-10 text-gray-400 text-sm">
    <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-6">
      <div class="flex items-center gap-3">
        <span class="font-orbitron font-bold text-white">DrMaviz.games</span>
        <span class="text-gray-500">— Ultra Liquid Glass Steam Vault</span>
      </div>
      <div class="text-xs text-gray-400 font-mono flex items-center gap-2">
        <span class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span>
        Status: <span class="text-white">Liquid Glass Engine Operational</span>
      </div>
    </div>
  </footer>

  <!-- MODAL 1: GAME INSPECTOR -->
  <div id="gameModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
    <div class="liquid-glass-tier-1 w-full max-w-3xl rounded-3xl overflow-hidden shadow-2xl transform scale-95 transition-transform duration-300 relative max-h-[90vh] overflow-y-auto">
      <button onclick="closeGameModal()" class="absolute top-4 right-4 z-20 p-3 rounded-full liquid-glass-tier-3 hover:bg-white/20 text-white transition-all">
        <i data-lucide="x" class="w-5 h-5"></i>
      </button>
      <div id="gameModalContent"></div>
    </div>
  </div>

  <!-- MODAL 2: UPLOAD STUDIO -->
  <div id="uploadModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
    <div class="liquid-glass-tier-1 w-full max-w-xl rounded-3xl p-8 relative shadow-2xl max-h-[90vh] overflow-y-auto">
      <button onclick="closeUploadModal()" class="absolute top-4 right-4 p-2.5 rounded-full liquid-glass-tier-3 text-gray-300 hover:text-white">
        <i data-lucide="x" class="w-5 h-5"></i>
      </button>

      <div class="flex items-center gap-3 mb-6">
        <div class="w-12 h-12 rounded-2xl liquid-glass-tier-3 flex items-center justify-center text-purple-400 shadow-xl overflow-hidden">
          <img src="Gemini_Generated_Image.png" alt="Avatar" class="w-full h-full object-cover">[cite: 6]
        </div>
        <div>
          <h3 class="font-orbitron text-xl font-bold text-white">LUA FILE IMPORT & STUDIO</h3>
          <p class="text-xs text-gray-400 font-mono">Developer Vault Uploader</p>
        </div>
      </div>

      <form onsubmit="handleUploadSubmit(event)" class="space-y-4">
        <div class="p-5 rounded-2xl liquid-glass-tier-2 border border-white/20">
          <label class="block text-xs font-orbitron font-bold text-purple-300 mb-2 flex items-center gap-1.5"><i data-lucide="file-code" class="w-4 h-4"></i> AI AUTO-IMPORT .LUA FILES</label>
          <input id="luaFileInput" type="file" accept=".lua,text/plain" multiple onchange="importLuaFiles(event)" class="block w-full text-xs text-gray-300 file:mr-4 file:py-2.5 file:px-4 file:rounded-full file:border-0 file:text-xs file:font-semibold file:bg-purple-500/20 file:text-purple-300 hover:file:bg-purple-500/30 cursor-pointer" />
          <p class="text-[11px] text-gray-400 mt-2">Drop or pick .lua files: the game is identified automatically, poster downloaded, and script added to vault.</p>
          <div class="mt-3 p-3 rounded-2xl bg-black/40 border border-white/10">
            <label class="block text-[10px] font-orbitron font-bold text-cyan-300 mb-1.5 flex items-center gap-1.5"><i data-lucide="sparkles" class="w-3.5 h-3.5"></i> CLAUDE AI (OPTIONAL)</label>
            <input id="aiKeyInput" type="password" autocomplete="off" placeholder="Anthropic API key (sk-ant-...)" onchange="saveAiKey(this.value)" class="w-full px-4 py-2.5 rounded-full liquid-input text-xs text-white placeholder-gray-500" />
          </div>
          <label class="mt-3 flex items-center gap-2 text-[11px] text-gray-300 cursor-pointer">
            <input id="autoNameToggle" type="checkbox" checked onchange="try{localStorage.setItem('drmavizAutoName', this.checked ? '1' : '0')}catch(e){}" class="accent-purple-500 w-4 h-4" />
            Auto-name Lua files
          </label>
          <div id="aiImportStatus" class="mt-3 space-y-1 text-[11px] font-mono text-gray-300 max-h-32 overflow-y-auto"></div>
        </div>

        <div>
          <label class="block text-xs font-orbitron font-bold text-gray-300 mb-1.5">SELECT OR ADD GAME</label>
          <select id="uploadGameSelect" class="w-full px-4 py-3 rounded-full liquid-input text-xs text-white focus:outline-none bg-[#0a0a0f] cursor-pointer"></select>
          <div class="flex gap-2.5 mt-2.5">
            <input id="newGameTitle" type="text" placeholder="New game title (if not listed)" class="min-w-0 flex-1 px-4 py-2.5 rounded-full liquid-input text-xs text-white placeholder-gray-500" />
            <button type="button" onclick="addCustomGame()" class="liquid-btn-secondary px-5 py-2.5 text-xs whitespace-nowrap">ADD GAME</button>
          </div>
        </div>

        <div>
          <label class="block text-xs font-orbitron font-bold text-gray-300 mb-1.5">SCRIPT FEATURE TITLE</label>
          <input type="text" id="uploadTitle" placeholder="e.g. GodMode & Unlimited Ammo V2" required class="w-full px-4 py-3 rounded-full liquid-input text-xs text-white placeholder-gray-500" />
        </div>

        <div>
          <label class="block text-xs font-orbitron font-bold text-gray-300 mb-1.5">DESCRIPTION</label>
          <input type="text" id="uploadDesc" placeholder="e.g. Executable Lua trainer for single-player engine." required class="w-full px-4 py-3 rounded-full liquid-input text-xs text-white placeholder-gray-500" />
        </div>

        <div>
          <label class="block text-xs font-orbitron font-bold text-gray-300 mb-1.5">LUA CODE SOURCE</label>
          <textarea id="uploadCode" rows="4" placeholder="-- Enter executable Lua script..." required class="w-full p-4 rounded-2xl liquid-input text-xs text-white font-mono placeholder-gray-600"></textarea>
        </div>

        <button type="submit" class="w-full liquid-btn-primary py-3.5 font-orbitron text-xs tracking-wider uppercase">
          PUBLISH TO VAULT
        </button>
      </form>
    </div>
  </div>

  <!-- MODAL 3: DELETE CONFIRM -->
  <div id="deleteModal" class="fixed inset-0 z-[60] flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
    <div class="liquid-glass-tier-1 w-full max-w-md rounded-3xl p-8 relative shadow-2xl text-center">
      <div class="w-14 h-14 mx-auto mb-4 rounded-2xl liquid-glass-tier-3 flex items-center justify-center text-red-400">
        <i data-lucide="trash-2" class="w-7 h-7"></i>
      </div>
      <h3 class="font-orbitron text-lg font-bold text-white mb-2">DELETE GAME?</h3>
      <p class="text-xs text-gray-300 leading-relaxed mb-6">
        <span id="deleteGameName" class="font-bold text-white"></span> and all of its Lua scripts will be removed from your vault.
      </p>
      <div class="flex gap-3">
        <button type="button" onclick="closeDeleteModal()" class="flex-1 liquid-btn-outline py-3 text-xs font-orbitron tracking-wider">CANCEL</button>
        <button type="button" onclick="confirmDeleteGame()" class="flex-1 liquid-btn-danger py-3 text-xs font-orbitron tracking-wider">DELETE</button>
      </div>
    </div>
  </div>

  <!-- MODAL: RENAME GAME -->
  <div id="renameModal" class="fixed inset-0 z-[60] flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
    <div class="liquid-glass-tier-1 w-full max-w-md rounded-3xl p-8 relative shadow-2xl">
      <button onclick="closeRenameModal()" class="absolute top-4 right-4 p-2.5 rounded-full liquid-glass-tier-3 text-gray-300 hover:text-white">
        <i data-lucide="x" class="w-5 h-5"></i>
      </button>
      <div class="flex items-center gap-3 mb-5">
        <div class="w-12 h-12 rounded-2xl liquid-glass-tier-3 flex items-center justify-center text-cyan-400 shadow-xl">
          <i data-lucide="pencil" class="w-6 h-6"></i>
        </div>
        <div>
          <h3 class="font-orbitron text-lg font-bold text-white">RENAME GAME</h3>
          <p class="text-xs text-gray-400 font-mono">Change the title shown in your vault</p>
        </div>
      </div>
      <form onsubmit="confirmRename(event)" class="space-y-4">
        <input id="renameInput" type="text" maxlength="80" autocomplete="off" placeholder="Game title" class="w-full px-5 py-3 rounded-full liquid-input text-sm text-white placeholder-gray-500" />
        <div class="flex gap-3">
          <button type="button" onclick="closeRenameModal()" class="flex-1 liquid-btn-outline py-3 text-xs font-orbitron tracking-wider">CANCEL</button>
          <button type="submit" class="flex-1 liquid-btn-primary py-3 text-xs font-orbitron tracking-wider">SAVE NAME</button>
        </div>
      </form>
    </div>
  </div>

  <!-- MODAL 4: POSTER EDITOR -->
  <div id="posterModal" class="fixed inset-0 z-[60] flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
    <div class="liquid-glass-tier-1 w-full max-w-lg rounded-3xl p-8 relative shadow-2xl max-h-[90vh] overflow-y-auto">
      <button onclick="closePosterModal()" class="absolute top-4 right-4 p-2.5 rounded-full liquid-glass-tier-3 text-gray-300 hover:text-white">
        <i data-lucide="x" class="w-5 h-5"></i>
      </button>
      <div class="flex items-center gap-3 mb-5">
        <div class="w-12 h-12 rounded-2xl liquid-glass-tier-3 flex items-center justify-center text-cyan-400 shadow-xl">
          <i data-lucide="image-plus" class="w-6 h-6"></i>
        </div>
        <div>
          <h3 class="font-orbitron text-lg font-bold text-white">GAME POSTER</h3>
          <p id="posterGameName" class="text-xs text-gray-400 font-mono"></p>
        </div>
      </div>

      <div class="aspect-video w-full rounded-2xl overflow-hidden bg-black/80 border border-white/15 mb-5">
        <img id="posterPreview" class="w-full h-full object-cover" alt="Poster preview">
      </div>

      <div class="space-y-4">
        <div class="p-4 rounded-2xl liquid-glass-tier-2 border border-white/20">
          <label class="block text-xs font-orbitron font-bold text-purple-300 mb-2">UPLOAD IMAGE FROM DEVICE</label>
          <input id="posterFileInput" type="file" accept="image/*" onchange="handlePosterFile(event)" class="block w-full text-xs text-gray-300 file:mr-4 file:py-2.5 file:px-4 file:rounded-full file:border-0 file:text-xs file:font-semibold file:bg-purple-500/20 file:text-purple-300 hover:file:bg-purple-500/30 cursor-pointer" />
        </div>

        <div>
          <label class="block text-xs font-orbitron font-bold text-gray-300 mb-1.5">OR PASTE IMAGE URL</label>
          <div class="flex gap-2.5">
            <input id="posterUrlInput" type="url" placeholder="https://..." class="min-w-0 flex-1 px-4 py-2.5 rounded-full liquid-input text-xs text-white placeholder-gray-500" />
            <button type="button" onclick="applyPosterUrl()" class="liquid-btn-secondary px-5 py-2.5 text-xs whitespace-nowrap">APPLY</button>
          </div>
        </div>

        <div class="flex flex-col sm:flex-row gap-3 pt-1">
          <button type="button" onclick="fetchPosterFromSteam()" class="flex-1 liquid-btn-outline py-3 text-[11px] font-orbitron tracking-wider flex items-center justify-center gap-2">
            <i data-lucide="search" class="w-4 h-4"></i> FETCH FROM STEAM
          </button>
          <button type="button" onclick="resetPoster()" class="flex-1 liquid-btn-outline py-3 text-[11px] font-orbitron tracking-wider flex items-center justify-center gap-2">
            <i data-lucide="rotate-ccw" class="w-4 h-4"></i> RESET
          </button>
        </div>
        <button type="button" onclick="closePosterModal()" class="w-full liquid-btn-primary py-3.5 font-orbitron text-xs tracking-wider">DONE</button>
      </div>
    </div>
  </div>

  <!-- TOAST NOTIFICATION -->
  <div id="toast" class="fixed bottom-6 right-6 z-50 transform translate-y-20 opacity-0 transition-all duration-300 liquid-glass-tier-1 px-6 py-4 rounded-2xl flex items-center gap-3.5 shadow-2xl">
    <div class="w-8 h-8 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center shrink-0">
      <i data-lucide="check" class="w-4 h-4"></i>
    </div>
    <span id="toastMsg" class="text-xs font-semibold text-white font-orbitron">Action completed</span>
  </div>

  <!-- SCRIPT ENGINE -->
  <script>
    function checkAuth() {
      const storedUser = localStorage.getItem('drmavizUser');
      if (storedUser) {
        document.getElementById('signInGate').classList.add('hidden');
        document.getElementById('unlockedVault').classList.remove('hidden');
        document.getElementById('displayUsername').innerText = storedUser.toUpperCase();
        document.getElementById('userProfilePill').classList.remove('hidden');
        document.getElementById('userProfilePill').classList.add('flex');
      } else {
        document.getElementById('signInGate').classList.remove('hidden');
        document.getElementById('unlockedVault').classList.add('hidden');
        document.getElementById('userProfilePill').classList.add('hidden');
        document.getElementById('userProfilePill').classList.remove('flex');
      }
    }

    function handleSignIn(e) {
      e.preventDefault();
      const username = document.getElementById('signInUsername').value.trim();
      if (!username) return;
      localStorage.setItem('drmavizUser', username);
      checkAuth();
      showToast(`Welcome back, ${username}!`);
    }

    function handleSignOut() {
      localStorage.removeItem('drmavizUser');
      checkAuth();
      showToast('Signed out successfully.');
    }

    const gameDatabase = [
      {
        id: 'gta6',
        steamId: 271590,
        title: 'Grand Theft Auto VI',
        genre: 'Open World',
        rating: '10/10 Upcoming Masterpiece',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/271590/header.jpg',
        desc: 'Vice City open world action RPG experience.',
        luaScripts: [{ name: 'gta6_vice_money_spawner.lua', desc: 'Infinite Money & Vehicle Trainer', code: 'print("GTA 6 Lua Loaded")\nMoney = 9999999' }]
      },
      {
        id: 'cyberpunk2077',
        steamId: 1091500,
        title: 'Cyberpunk 2077',
        genre: 'Action',
        rating: '9/10 Very Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/1091500/header.jpg',
        desc: 'Cyberpunk 2077 is an open-world action-adventure RPG set in Night City.',
        luaScripts: [{ name: 'cyberpunk_eddies_godmode.lua', desc: 'Infinite Health, Eddies & Cyberware Max', code: 'print("Cyberpunk 2077 Lua Loaded")\nGodMode = true\nEddies = 9999999' }]
      },
      {
        id: 'eldenring',
        steamId: 1245620,
        title: 'Elden Ring',
        genre: 'Action',
        rating: '10/10 Overwhelmingly Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/1245620/header.jpg',
        desc: 'Rise, Tarnished, and be guided by grace to brandish the power of the Elden Ring.',
        luaScripts: [{ name: 'elden_ring_rune_autofarm.lua', desc: 'Automated Rune Spawner & Infinite Stamina', code: 'print("Elden Ring Lua Loaded")\nRunesMultiplier = 100' }]
      },
      {
        id: 'wukong',
        steamId: 2358720,
        title: 'Black Myth: Wukong',
        genre: 'Action',
        rating: '9.5/10 Overwhelmingly Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/2358720/header.jpg',
        desc: 'Action RPG rooted in Chinese mythology.',
        luaScripts: [{ name: 'wukong_mana_spells.lua', desc: 'Unlimited Mana & Instant Transformations', code: 'print("Wukong Lua Loaded")\nInfiniteMana = true' }]
      },
      {
        id: 'rdr2',
        steamId: 1174180,
        title: 'Red Dead Redemption 2',
        genre: 'Open World',
        rating: '10/10 Overwhelmingly Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/1174180/header.jpg',
        desc: 'Arthur Morgan and the Van der Linde gang are outlaws on the run.',
        luaScripts: [{ name: 'rdr2_deadeye_trainer.lua', desc: 'Infinite Dead Eye & Weapon Unlocker', code: 'print("RDR2 Lua Loaded")\nDeadEye = 100' }]
      },
      {
        id: 'godofwar',
        steamId: 2322010,
        title: 'God of War Ragnarök',
        genre: 'Action',
        rating: '10/10 Overwhelmingly Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/2322010/header.jpg',
        desc: 'Kratos and Atreus journey to each of the Nine Realms for answers.',
        luaScripts: [{ name: 'god_of_war_rage_boost.lua', desc: 'Max Spartan Rage & Armor Sets', code: 'print("GoW Lua Loaded")\nRage = 100' }]
      },
      {
        id: 'bg3',
        steamId: 1086940,
        title: "Baldur's Gate 3",
        genre: 'Action',
        rating: '10/10 Overwhelmingly Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/1086940/header.jpg',
        desc: 'Gather your party and return to the Forgotten Realms.',
        luaScripts: [{ name: 'bg3_dice_always20.lua', desc: 'Natural 20 Guaranteed Roll Engine', code: 'print("BG3 Lua Loaded")\nAlwaysRoll20 = true' }]
      },
      {
        id: 'forza5',
        steamId: 1551360,
        title: 'Forza Horizon 5',
        genre: 'Racing',
        rating: '9/10 Very Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/1551360/header.jpg',
        desc: 'Explore the vibrant open world landscapes of Mexico.',
        luaScripts: [{ name: 'forza5_super_wheelspins.lua', desc: 'Unlimited Wheelspins & Car Unlocks', code: 'print("Forza Lua Loaded")\nWheelspins = 999' }]
      },
      {
        id: 'cs2',
        steamId: 730,
        title: 'Counter-Strike 2',
        genre: 'FPS',
        rating: '9/10 Very Positive',
        poster: 'https://cdn.akamai.steamstatic.com/steam/apps/730/header.jpg',
        desc: 'Counter-Strike 2 is the largest technical leap forward.',
        luaScripts: [{ name: 'recoil_control_assistant.lua', desc: 'Recoil Control Pattern Assistant', code: 'print("CS2 Assistant Loaded")\nRecoilReduction = 0.9' }]
      }
    ];

    let coverflowIndex = 0;

    window.onload = function() {
      lucide.createIcons();
      checkAuth();
      try {
        const deleted = getDeletedIds();
        for (let i = gameDatabase.length - 1; i >= 0; i--) { if (deleted.includes(gameDatabase[i].id)) gameDatabase.splice(i, 1); }
        const saved = JSON.parse(localStorage.getItem('drmavizGameLibrary') || '[]');
        for (const item of saved) {
          if (deleted.includes(item.id)) continue;
          const existing = gameDatabase.find(g => g.id === item.id || g.title.toLowerCase() === String(item.title || '').toLowerCase());
          if (existing) { existing.luaScripts = item.luaScripts || existing.luaScripts || []; if (item.titleCustom && item.title) { existing.title = item.title; existing.titleCustom = true; }
          if (item.poster && (String(existing.id).startsWith('custom-') || item.posterCustom)) { existing.poster = item.poster; if (item.posterCustom) existing.posterCustom = true; } }
          else if (item.id && item.title) gameDatabase.push(item);
        }
      } catch (e) { console.warn('Could not restore saved library', e); }
      sortGames();
      render3DGridDeck(gameDatabase);
      renderCoverflow();
      renderLuaVault();
      setup3DScrollEffects();
      setupCoverflowControls();
    };

    function fadeSwap(img, src) {
      if (!img || img.getAttribute('src') === src || img.dataset.pending === src) return;
      img.dataset.pending = src;
      const pre = new Image();
      pre.onload = () => {
        img.style.transition = 'opacity .3s ease';
        img.style.opacity = '0';
        setTimeout(() => {
          img.src = src;
          img.classList.add('loaded');
          delete img.dataset.pending;
          requestAnimationFrame(() => requestAnimationFrame(() => { img.style.opacity = ''; }));
          setTimeout(() => { img.style.transition = ''; }, 400);
        }, 300);
      };
      pre.onerror = () => { delete img.dataset.pending; };
      pre.src = src;
    }

    function posterFallback(img) {
      img.onerror = null;
      img.src = makeGeneratedPoster(img.dataset.title || '');
    }

    const deckCache = new Map();
    let sceneCount = 0, sceneKey = -2, sceneRaf = false, wheelLock = false;

    function sceneHtml(game) {
      const img = (cls) => `<img class="poster-img ${cls}" src="${escAttr(game.poster)}" alt="" decoding="async" data-title="${escAttr(game.title)}" onerror="posterFallback(this)" onload="this.classList.add('loaded')">`;
      return `
        <div class="s-bg absolute inset-0 pointer-events-none">
          ${img('s-bgimg absolute inset-0 w-full h-full object-cover')}
          <div class="absolute inset-0 bg-gradient-to-r from-black via-black/85 to-black/35"></div>
          <div class="absolute inset-0 bg-gradient-to-t from-black via-transparent to-black/75"></div>
        </div>
        <div class="relative z-10 h-full flex flex-col md:flex-row items-center justify-center gap-6 md:gap-12 px-6 md:px-[6vw] pt-24 pb-12">
          <div class="w-full md:w-[42%] space-y-4 order-2 md:order-1">
            <div class="s-line" style="--i:0"><span class="s-count font-mono text-xs text-cyan-300 tracking-[.3em]"></span></div>
            <div class="s-line" style="--i:1"><span class="inline-block px-3 py-1 rounded-full liquid-glass-tier-3 text-[10px] font-orbitron font-bold text-cyan-300 tracking-wider">${game.genre}</span></div>
            <h3 class="s-line font-orbitron text-3xl md:text-5xl lg:text-6xl font-black text-white leading-[1.05]" style="--i:2">${game.title}</h3>
            <p class="s-line text-sm text-gray-300 leading-relaxed max-w-md" style="--i:3">${game.desc}</p>
            <div class="s-line flex flex-wrap items-center gap-3" style="--i:4">
              <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full liquid-glass-tier-3 text-xs font-mono text-purple-300"><i data-lucide="file-code" class="w-3.5 h-3.5"></i> ${game.luaScripts.length} Executable Script(s)</span>
              <span class="text-[11px] font-mono text-gray-400">${game.rating}</span>
            </div>
            <div class="s-line" style="--i:5"><button type="button" onclick="openGameModal('${game.id}')" class="liquid-btn-primary px-7 py-3.5 text-xs font-orbitron tracking-wider">GET .LUA SCRIPTS</button></div>
          </div>
          <div class="s-frame relative aspect-video w-full md:w-[58%] max-h-[62vh] rounded-3xl overflow-hidden border border-white/25 shadow-2xl bg-black cursor-pointer order-1 md:order-2" onclick="if(!event.target.closest('button')) openGameModal('${game.id}')">
            ${img('w-full h-full object-cover')}
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent pointer-events-none"></div>
            ${gameActionButtons(game)}
          </div>
        </div>`;
    }

    function render3DGridDeck(games) {
      const deck = document.getElementById('deckContainer');
      deck.className = 'scene-track';
      const live = new Set(gameDatabase.map(g => g.id));
      for (const id of Array.from(deckCache.keys())) if (!live.has(id)) deckCache.delete(id);

      if (!games.length) {
        sceneCount = 0;
        deck.style.height = 'auto';
        deck.innerHTML = '<div class="liquid-glass-tier-3 rounded-3xl p-10 text-center text-sm text-gray-400 font-mono mx-auto max-w-xl">No games to show. Add one with the upload button above.</div>';
        return;
      }

      let stage = deck.querySelector('.scene-stage');
      if (!stage) {
        deck.innerHTML = '';
        stage = document.createElement('div');
        stage.className = 'scene-stage';
        stage.innerHTML = '<div class="scene-dots"></div><div class="scene-hint">SCROLL</div>';
        deck.appendChild(stage);
      }
      const dots = stage.querySelector('.scene-dots');

      const els = games.map((game, i) => {
        let entry = deckCache.get(game.id);
        if (!entry) {
          const el = document.createElement('div');
          el.className = 'scene';
          entry = { el, textSig: null, poster: null };
          deckCache.set(game.id, entry);
        }
        const textSig = [game.title, game.genre, game.desc, game.rating, game.luaScripts.length].join('\u0001');
        if (entry.textSig !== textSig) {
          entry.el.innerHTML = sceneHtml(game);
          entry.textSig = textSig; entry.poster = game.poster;
        } else if (entry.poster !== game.poster) {
          entry.el.querySelectorAll('img.poster-img').forEach(img => fadeSwap(img, game.poster));
          entry.poster = game.poster;
        }
        entry.el.querySelector('.s-count').textContent = String(i + 1).padStart(2, '0') + ' — ' + String(game.genre || '').toUpperCase();
        return entry.el;
      });

      Array.from(stage.querySelectorAll('.scene')).forEach(el => { if (!els.includes(el)) el.remove(); });
      els.forEach(el => stage.insertBefore(el, dots));
      dots.innerHTML = games.map((g, i) => `<button type="button" class="scene-dot" data-t="${String(i + 1).padStart(2, '0')} · ${escAttr(g.title)}" onclick="goScene(${i})"></button>`).join('');

      sceneCount = games.length;
      layoutDots();
      deck.style.height = (games.length * 100) + 'vh';
      lucide.createIcons();
      sceneKey = -2;
      updateScenes();
    }

    function layoutDots() {
      const dots = document.querySelector('.scene-dots');
      if (!dots || !sceneCount) return;
      const pitch = Math.min(22, (window.innerHeight - 260) / sceneCount);
      const size = Math.max(4, Math.min(10, pitch * 0.5));
      dots.style.setProperty('--ds', size.toFixed(1) + 'px');
      dots.style.setProperty('--dg', Math.max(1, pitch - size).toFixed(1) + 'px');
    }

    function updateScenes() {
      const deck = document.getElementById('deckContainer');
      if (!sceneCount) return;
      const vh = window.innerHeight, rect = deck.getBoundingClientRect();
      const idx = Math.max(0, Math.min(sceneCount - 1, Math.round(-rect.top / vh)));
      const visible = rect.top < vh * 0.55 && rect.bottom > vh * 0.45;
      const prog = -rect.top / vh;
      deck.querySelectorAll('.scene-dot').forEach((d, i) => {
        const k = visible ? Math.max(0, 1 - Math.abs(prog - i)) : 0;
        d.style.setProperty('--k', k.toFixed(3));
        d.style.setProperty('--g', (visible ? Math.max(0, 1 - Math.abs(prog - i) / 3) : 0).toFixed(3));
      });
      const key = visible ? idx : -1;
      if (key === sceneKey) return;
      sceneKey = key;
      deck.querySelectorAll('.scene').forEach((el, i) => {
        el.classList.toggle('active', visible && i === idx);
        el.classList.toggle('past', visible && i < idx);
      });
      deck.querySelectorAll('.scene-dot').forEach((d, i) => d.classList.toggle('on', visible && i === idx));
      const hint = deck.querySelector('.scene-hint');
      if (hint) hint.classList.toggle('gone', !visible || idx > 0);
    }

    function goScene(i) {
      const deck = document.getElementById('deckContainer');
      const top = deck.getBoundingClientRect().top + window.scrollY + i * window.innerHeight;
      window.scrollTo({ top, behavior: 'smooth' });
    }

    (function setupScenes() {
      const tick = () => { if (!sceneRaf) { sceneRaf = true; requestAnimationFrame(() => { sceneRaf = false; updateScenes(); }); } };
      let scrollTimer = null;
      window.addEventListener('scroll', () => {
        const dots = document.querySelector('.scene-dots');
        if (dots) { dots.classList.add('scrolling'); clearTimeout(scrollTimer); scrollTimer = setTimeout(() => dots.classList.remove('scrolling'), 700); }
        tick();
      }, { passive: true });
      window.addEventListener('resize', () => { layoutDots(); sceneKey = -2; tick(); });

      window.addEventListener('wheel', (e) => {
        if (e.ctrlKey || sceneCount < 2) return;
        if (document.querySelector('#gameModal:not(.opacity-0), #uploadModal:not(.opacity-0), #deleteModal:not(.opacity-0), #posterModal:not(.opacity-0), #renameModal:not(.opacity-0)')) return;
        const deck = document.getElementById('deckContainer');
        const rect = deck.getBoundingClientRect(), vh = window.innerHeight;
        if (!(rect.top <= 2 && rect.bottom >= vh - 2)) return;
        const idx = Math.max(0, Math.min(sceneCount - 1, Math.round(-rect.top / vh)));
        const dir = e.deltaY > 0 ? 1 : -1;
        if ((dir > 0 && idx >= sceneCount - 1) || (dir < 0 && idx <= 0)) return;
        e.preventDefault();
        if (wheelLock) return;
        wheelLock = true;
        goScene(idx + dir);
        setTimeout(() => { wheelLock = false; }, 950);
      }, { passive: false });
    })();

    let filterTimer = null;
    function debouncedFilter() { clearTimeout(filterTimer); filterTimer = setTimeout(filterGames, 150); }

    function filterGames() {
      const search = document.getElementById('searchInput').value.toLowerCase();
      const genre = document.getElementById('genreFilter').value;

      const filtered = gameDatabase.filter(game => {
        const matchesSearch = game.title.toLowerCase().includes(search) || game.desc.toLowerCase().includes(search) || game.genre.toLowerCase().includes(search) || game.luaScripts.some(script => script.name.toLowerCase().includes(search));
        const matchesGenre = (genre === 'ALL' || game.genre === genre);
        return matchesSearch && matchesGenre;
      });

      render3DGridDeck(filtered);
    }

    function setup3DScrollEffects() {
      let ticking = false;
      function absTop(el) { let y = 0; while (el) { y += el.offsetTop; el = el.offsetParent; } return y; }
      function update() {
        ticking = false;
        const vh = window.innerHeight, sy = window.scrollY;
        const cards = document.querySelectorAll('.scroll-card-3d');
        cards.forEach((card, i) => {
          const center = absTop(card) + card.offsetHeight / 2 - sy;
          if (center < -300 || center > vh + 300) return;
          const t = Math.max(-1, Math.min(1, (center - vh / 2) / vh));
          card.style.transform = `perspective(1200px) rotateX(${(t * 6).toFixed(2)}deg) rotateY(${((i % 2 === 0 ? 1 : -1) * t * 3).toFixed(2)}deg)`;
        });
      }
      window.requestTilt = () => { if (!ticking) { ticking = true; requestAnimationFrame(update); } };
      window.addEventListener('scroll', window.requestTilt, { passive: true });
      window.addEventListener('resize', window.requestTilt);
      window.requestTilt();
    }

    const cfCache = new Map();
    function cfCardHtml(game) {
      return `
          <img loading="lazy" decoding="async" src="${escAttr(game.poster)}" class="poster-img w-full h-full object-cover" alt="${game.title}" data-title="${escAttr(game.title)}" onerror="posterFallback(this)" onload="this.classList.add('loaded')">
          ${gameActionButtons(game)}
          <div class="absolute inset-0 bg-gradient-to-t from-black via-black/40 to-transparent p-5 flex flex-col justify-end">
            <h3 class="font-orbitron text-sm font-black text-white mb-2">${game.title}</h3>
            <button onclick="openGameModal('${game.id}')" class="w-full py-2 rounded-full liquid-btn-primary font-orbitron text-[10px] tracking-wider">INSPECT SCRIPTS</button>
          </div>
        `;
    }

    function renderCoverflow() {
      const track = document.getElementById('coverflowTrack');
      if (!gameDatabase.length) {
        cfCache.clear();
        track.innerHTML = '<p class="text-sm text-gray-400 font-mono">No games in the vault.</p>';
        document.getElementById('coverflowCounter').innerText = '0 / 0';
        return;
      }
      const live = new Set(gameDatabase.map(g => g.id));
      for (const [id, e] of Array.from(cfCache.entries())) if (!live.has(id)) { e.el.remove(); cfCache.delete(id); }

      gameDatabase.forEach(game => {
        const textSig = [game.title, game.genre].join('\u0001');
        let entry = cfCache.get(game.id);
        if (!entry) {
          const el = document.createElement('div');
          el.dataset.cf = '1';
          el.className = "absolute w-80 aspect-video rounded-3xl overflow-hidden liquid-glass-tier-2 border border-white/25 shadow-2xl cursor-pointer";
          el.style.transition = 'transform .6s cubic-bezier(.16,1,.3,1), opacity .5s ease, visibility .5s, border-color .3s ease, box-shadow .3s ease';
          const id = game.id;
          el.onclick = (e) => {
            if (e.target.closest('.card-action-btn')) return;
            const i = gameDatabase.findIndex(g => g.id === id);
            if (i > -1) { coverflowIndex = i; positionCoverflow(); }
          };
          el.innerHTML = cfCardHtml(game);
          track.appendChild(el);
          entry = { el, textSig, poster: game.poster };
          cfCache.set(game.id, entry);
        } else {
          if (entry.textSig !== textSig) { entry.el.innerHTML = cfCardHtml(game); entry.textSig = textSig; entry.poster = game.poster; }
          else if (entry.poster !== game.poster) { fadeSwap(entry.el.querySelector('img.poster-img'), game.poster); entry.poster = game.poster; }
        }
      });
      positionCoverflow();
      lucide.createIcons();
    }

    function positionCoverflow() {
      if (!gameDatabase.length) return;
      if (coverflowIndex >= gameDatabase.length) coverflowIndex = gameDatabase.length - 1;
      if (coverflowIndex < 0) coverflowIndex = 0;
      gameDatabase.forEach((game, idx) => {
        const e = cfCache.get(game.id);
        if (!e) return;
        const offset = idx - coverflowIndex, abs = Math.abs(offset), far = abs > 3;
        const el = e.el;
        el.style.transform = `translateX(${offset * 210}px) translateZ(${-abs * 160}px) rotateY(${offset * -22}deg)`;
        el.style.opacity = far ? 0 : (1 - abs * 0.28);
        el.style.zIndex = 30 - abs;
        el.style.visibility = far ? 'hidden' : 'visible';
        el.style.pointerEvents = far ? 'none' : '';
      });
      document.getElementById('coverflowCounter').innerText = `${coverflowIndex + 1} / ${gameDatabase.length}`;
    }

    function setupCoverflowControls() {
      document.getElementById('prevBtn').onclick = () => {
        if (!gameDatabase.length) return;
        coverflowIndex = (coverflowIndex - 1 + gameDatabase.length) % gameDatabase.length;
        positionCoverflow();
      };
      document.getElementById('nextBtn').onclick = () => {
        if (!gameDatabase.length) return;
        coverflowIndex = (coverflowIndex + 1) % gameDatabase.length;
        positionCoverflow();
      };
    }

    function renderLuaVault() {
      const container = document.getElementById('luaVaultGrid');
      container.innerHTML = '';

      gameDatabase.forEach(game => {
        game.luaScripts.forEach(script => {
          const card = document.createElement('div');
          card.className = "p-6 rounded-3xl liquid-glass-tier-2 border border-white/10 hover:border-purple-500/50 flex flex-col justify-between gap-5 group";
          card.innerHTML = `
            <div>
              <div class="flex items-center justify-between mb-3">
                <span class="text-[10px] font-mono px-3 py-1 rounded-full liquid-glass-tier-3 text-cyan-300 font-bold tracking-wider">${game.title}</span>
                <div class="w-8 h-8 rounded-full liquid-glass-tier-3 flex items-center justify-center text-purple-400 group-hover:scale-110 transition-transform">
                  <i data-lucide="terminal" class="w-4 h-4"></i>
                </div>
              </div>
              <h4 class="font-mono text-sm font-bold text-white break-all mb-1.5">${script.name}</h4>
              <p class="text-xs text-gray-300">${script.desc}</p>
            </div>
            <button onclick="downloadLuaScript('${script.name}', \`${script.code}\`)" class="w-full py-3 rounded-full liquid-btn-secondary text-xs font-mono font-bold flex items-center justify-center gap-2">
              <i data-lucide="download" class="w-4 h-4"></i> DOWNLOAD DIRECT (.LUA)
            </button>
          `;
          container.appendChild(card);
        });
      });
      lucide.createIcons();
    }

    function downloadLuaScript(scriptName, code) {
      const content = `-- DrMaviz.games Official Liquid Script\n-- File: ${scriptName}\n\n${code}`;
      const blob = new Blob([content], { type: 'text/x-lua' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = scriptName;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
      showToast(`Downloaded ${scriptName}`);
    }

    function openGameModal(gameId) {
      const game = gameDatabase.find(g => g.id === gameId);
      if (!game) return;

      const modalContent = document.getElementById('gameModalContent');
      modalContent.innerHTML = `
        <div class="relative aspect-video w-full overflow-hidden bg-black/90">
          <img loading="lazy" decoding="async" src="${escAttr(game.poster)}" class="poster-img w-full h-full object-cover" data-title="${escAttr(game.title)}" onerror="posterFallback(this)" onload="this.classList.add('loaded')">
          <div class="absolute inset-0 bg-gradient-to-t from-black via-black/40 to-transparent"></div>
          <div class="absolute bottom-6 left-6">
            <h2 class="font-orbitron text-3xl font-black text-white drop-shadow-md">${game.title}</h2>
            <span class="text-xs font-mono text-cyan-300">Steam App ID: ${game.steamId} • ${game.genre}</span>
          </div>
        </div>
        <div class="p-8 space-y-5">
          <p class="text-xs text-gray-300 leading-relaxed">${game.desc}</p>
          <div class="flex flex-wrap gap-3">
            <button type="button" onclick="openPosterModal('${game.id}')" class="liquid-btn-outline px-5 py-2.5 text-[11px] font-orbitron tracking-wider flex items-center gap-2"><i data-lucide="image-plus" class="w-4 h-4"></i> CHANGE POSTER</button>
            <button type="button" onclick="openRenameModal('${game.id}')" class="liquid-btn-outline px-5 py-2.5 text-[11px] font-orbitron tracking-wider flex items-center gap-2"><i data-lucide="pencil" class="w-4 h-4"></i> RENAME GAME</button>
            <button type="button" onclick="requestDeleteGame('${game.id}')" class="liquid-btn-outline px-5 py-2.5 text-[11px] font-orbitron tracking-wider flex items-center gap-2 text-red-300 hover:text-red-200"><i data-lucide="trash-2" class="w-4 h-4"></i> DELETE GAME</button>
          </div>
          <div class="space-y-3">
            <h4 class="font-orbitron text-xs font-bold text-purple-300 tracking-wider uppercase">Available Executable Lua Scripts</h4>
            ${game.luaScripts.map(s => `
              <div class="p-4 rounded-2xl liquid-glass-tier-2 flex items-center justify-between gap-4">
                <div>
                  <div class="font-mono text-xs font-bold text-white">${s.name}</div>
                  <div class="text-[11px] text-gray-400 mt-0.5">${s.desc}</div>
                </div>
                <button onclick="downloadLuaScript('${s.name}', \`${s.code}\`)" class="liquid-btn-primary px-4 py-2 text-xs font-mono font-bold flex items-center gap-1.5 shrink-0">
                  <i data-lucide="download" class="w-3.5 h-3.5"></i> GET
                </button>
              </div>
            `).join('')}
          </div>
        </div>
      `;

      lucide.createIcons();
      document.getElementById('gameModal').classList.remove('opacity-0', 'pointer-events-none');
    }

    function closeGameModal() {
      document.getElementById('gameModal').classList.add('opacity-0', 'pointer-events-none');
    }

    function openUploadModal() {
      const select = document.getElementById('uploadGameSelect');
      select.innerHTML = gameDatabase.map(g => `<option value="${g.id}">${g.title}</option>`).join('');
      const k = document.getElementById('aiKeyInput'); if (k) k.value = getAiKey();
      const t = document.getElementById('autoNameToggle'); if (t) t.checked = isAutoNameOn();
      document.getElementById('uploadModal').classList.remove('opacity-0', 'pointer-events-none');
    }

    function closeUploadModal() {
      document.getElementById('uploadModal').classList.add('opacity-0', 'pointer-events-none');
    }

    function escapeSvgText(value) { return String(value).replace(/[&<>"\']/g, ch => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&apos;'}[ch])); }
    
    function makeGeneratedPoster(title) {
      const safe = escapeSvgText(title).slice(0, 54);
      const hue = Array.from(title).reduce((n, c) => n + c.charCodeAt(0), 0) % 360;
      const svg = `<svg xmlns="http://www.w3.org/2000/svg" width="900" height="1200" viewBox="0 0 900 1200"><defs><linearGradient id="g" x1="0" y1="0" x2="1" y2="1"><stop stop-color="hsl(${hue},70%,15%)"/><stop offset="1" stop-color="hsl(${(hue+60)%360},80%,5%)"/></linearGradient></defs><rect width="900" height="1200" fill="url(#g)"/><circle cx="700" cy="300" r="320" fill="hsl(${hue},90%,60%)" opacity=".3"/><text x="64" y="1000" font-family="Arial,sans-serif" font-size="24" letter-spacing="8" fill="#fff" opacity=".8">DRMAVIZ LIQUID VAULT</text><text x="64" y="1075" font-family="Arial,sans-serif" font-weight="800" font-size="56" fill="#fff">${safe}</text></svg>`;
      return 'data:image/svg+xml;charset=UTF-8,' + encodeURIComponent(svg);
    }

    function saveLibraryLocally() {
      try { localStorage.setItem('drmavizGameLibrary', JSON.stringify(gameDatabase)); }
      catch (err) { showToast('Browser storage is full'); }
    }

    async function findOfficialGamePoster(title) {
      const query = String(title || '').trim();
      if (!query) return null;
      try {
        const searchUrl = 'https://store.steampowered.com/api/storesearch/?term=' + encodeURIComponent(query) + '&l=english&cc=us';
        const response = await fetch(searchUrl);
        if (!response.ok) throw new Error('Store search unavailable');
        const data = await response.json();
        const items = Array.isArray(data.items) ? data.items : [];
        const exact = items.find(item => String(item.name || '').toLowerCase() === query.toLowerCase());
        const match = exact || items[0];
        if (!match || !match.id) return null;
        const detailsResponse = await fetch('https://store.steampowered.com/api/appdetails?appids=' + encodeURIComponent(match.id) + '&l=english');
        if (!detailsResponse.ok) throw new Error('Game details unavailable');
        const details = await detailsResponse.json();
        const app = details[String(match.id)] && details[String(match.id)].data;
        if (!app || !app.header_image) return null;
        return { poster: app.header_image, steamId: String(match.id), title: app.name || match.name };
      } catch (error) {
        return null;
      }
    }

    async function downloadPoster(steamId, title) {
      if (steamId && /^\d+$/.test(String(steamId))) {
        const url = `https://cdn.akamai.steamstatic.com/steam/apps/${steamId}/header.jpg`;
        return { poster: url, steamId: String(steamId) };
      }
      return await findOfficialGamePoster(title);
    }

    function addCustomGame(titleOverride) {
      const title = (titleOverride || document.getElementById('newGameTitle').value).trim();
      if (!title) { showToast('Enter a game title first'); return; }
      let game = gameDatabase.find(g => g.title.toLowerCase() === title.toLowerCase());
      if (!game) {
        const id = 'custom-' + title.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/^-|-$/g, '') + '-' + Date.now().toString(36);
        game = { id, steamId: 'N/A', title, genre: 'Other', rating: 'User added', poster: makeGeneratedPoster(title), desc: 'Custom imported game vault entry.', luaScripts: [] };
        gameDatabase.push(game);
      }
      sortGames();
      const select = document.getElementById('uploadGameSelect');
      select.innerHTML = gameDatabase.map(g => `<option value="${g.id}">${g.title}</option>`).join('');
      select.value = game.id;
      document.getElementById('newGameTitle').value = '';
      refreshAll();
      showToast(`Added ${game.title} to Vault & Coverflow`);
      return game;
    }

    function getAiKey() { try { return localStorage.getItem('drmavizAiKey') || ''; } catch (e) { return ''; } }
    function saveAiKey(v) { try { localStorage.setItem('drmavizAiKey', String(v || '').trim()); showToast(v ? 'AI key saved' : 'AI key cleared'); } catch (e) {} }

    function logAi(msg) {
      showToast(msg);
      const box = document.getElementById('aiImportStatus');
      if (box) { const d = document.createElement('div'); d.textContent = '› ' + msg; box.appendChild(d); box.scrollTop = box.scrollHeight; }
    }

    function parseSteamIdsFromLua(code) {
      const ids = [];
      const explicit = /(?:app[_\s-]?id|steam[_\s-]?app[_\s-]?id)\s*[=:]\s*["']?(\d{3,9})/i.exec(code);
      if (explicit) ids.push(explicit[1]);
      const re = /addappid\s*\(\s*(\d{3,9})/gi; let m;
      while ((m = re.exec(code))) ids.push(m[1]);
      return [...new Set(ids)];
    }

    function cleanFileTitle(fileName) {
      return fileName.replace(/\.lua$/i, '').replace(/^\d+[\s._-]*/, '').replace(/[._-]+/g, ' ').replace(/([a-z])([A-Z])/g, '$1 $2').trim();
    }

    function titleCase(str) {
      return String(str || '').replace(/\s+/g, ' ').trim().replace(/\b([a-z])([a-z']*)/g, (m, a, b) => a.toUpperCase() + b);
    }

    function isAutoNameOn() {
      try { return localStorage.getItem('drmavizAutoName') !== '0'; } catch (e) { return true; }
    }

    function createGameEntry(title, extra) {
      const id = 'custom-' + title.toLowerCase().replace(/[^a-z0-9]+/g, '-').replace(/^-|-$/g, '') + '-' + Date.now().toString(36);
      const game = Object.assign({ id, steamId: 'N/A', title, genre: 'Other', rating: 'AI imported', poster: makeGeneratedPoster(title), desc: 'Custom imported game vault entry.', luaScripts: [] }, extra || {});
      gameDatabase.push(game);
      return game;
    }

    async function importLuaFiles(event) {
      const files = Array.from(event.target.files || []);
      if (!files.length) return;
      let imported = 0, created = 0, posters = 0;

      for (const file of files) {
        if (!file.name.toLowerCase().endsWith('.lua')) continue;
        const code = await file.text();
        const ids = parseSteamIdsFromLua(code);
        const base = cleanFileTitle(file.name);
        
        logAi(`Analyzing ${file.name}…`);
        let game = ids.map(id => gameDatabase.find(g => String(g.steamId) === id)).find(Boolean);
        if (!game && base) game = gameDatabase.find(g => base.toLowerCase().includes(g.title.toLowerCase()) || g.title.toLowerCase().includes(base.toLowerCase()));

        let isNew = false;
        if (!game) {
          let title = titleCase(base || file.name.replace(/\.lua$/i, ''));
          const foundSteam = ids[0] ? await findOfficialGamePoster(title) : null;
          game = createGameEntry(foundSteam ? foundSteam.title : title, {
            steamId: ids[0] || 'N/A',
            rating: 'AI Auto-Imported'
          });
          isNew = !gameDatabase.some(g => g.id === game.id);
          created++;
          logAi(`Created new game entry: ${game.title}`);
        }

        if (!Array.isArray(game.luaScripts)) game.luaScripts = [];
        if (!game.luaScripts.some(x => x.name === file.name)) {
          game.luaScripts.push({ name: file.name, desc: 'Imported Lua script trainer', code });
          imported++;
        }

        if (isNew || String(game.poster).startsWith('data:image/svg')) {
          const found = await downloadPoster(ids[0], game.title);
          if (found && found.poster) {
            game.poster = found.poster;
            game.steamId = found.steamId || game.steamId;
            game.posterCustom = true;
            posters++;
            logAi(`Fetched poster for ${game.title}`);
          }
        }
      }

      saveLibraryLocally();
      refreshAll();
      showToast(imported ? `Imported ${imported} script(s), ${created} game(s) added to 3D Coverflow!` : 'No files imported');
      if (event.target) event.target.value = '';
    }

    function handleUploadSubmit(e) {
      e.preventDefault();
      const gameId = document.getElementById('uploadGameSelect').value;
      const title = document.getElementById('uploadTitle').value;
      const desc = document.getElementById('uploadDesc').value;
      const code = document.getElementById('uploadCode').value;

      const game = gameDatabase.find(g => g.id === gameId);
      if (game) {
        const fileName = title.toLowerCase().replace(/[^a-z0-9]/g, '_') + '.lua';
        game.luaScripts.push({ name: fileName, desc: desc, code: code });
        saveLibraryLocally();
        refreshAll();
        closeUploadModal();
        showToast(`Published ${fileName} to vault!`);
      }
    }

    let pendingDeleteId = null;
    let posterTargetId = null;

    function escAttr(v) { return String(v == null ? '' : v).replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace/>/g,'&gt;'); }

    function gameActionButtons(game) {
      return `<div class="absolute top-3 left-3 z-20 flex gap-2">
        <button type="button" title="Add / change poster" onclick="event.stopPropagation(); openPosterModal('${game.id}')" class="card-action-btn"><i data-lucide="image-plus" class="w-4 h-4"></i></button>
        <button type="button" title="Rename game" onclick="event.stopPropagation(); openRenameModal('${game.id}')" class="card-action-btn"><i data-lucide="pencil" class="w-4 h-4"></i></button>
        <button type="button" title="Delete game" onclick="event.stopPropagation(); requestDeleteGame('${game.id}')" class="card-action-btn danger"><i data-lucide="trash-2" class="w-4 h-4"></i></button>
      </div>`;
    }

    function sortGames() {
      const cur = gameDatabase[coverflowIndex] && gameDatabase[coverflowIndex].id;
      gameDatabase.sort((a, b) => String(a.title).localeCompare(String(b.title), undefined, { numeric: true, sensitivity: 'base' }));
      if (cur) { const i = gameDatabase.findIndex(g => g.id === cur); if (i > -1) coverflowIndex = i; }
    }

    function refreshAll() {
      sortGames();
      filterGames();
      renderCoverflow();
      renderLuaVault();
      lucide.createIcons();
    }

    function getDeletedIds() {
      try { return JSON.parse(localStorage.getItem('drmavizDeletedGames') || '[]'); } catch (e) { return []; }
    }

    function requestDeleteGame(id) {
      const game = gameDatabase.find(g => g.id === id);
      if (!game) return;
      pendingDeleteId = id;
      document.getElementById('deleteGameName').textContent = game.title;
      document.getElementById('deleteModal').classList.remove('opacity-0', 'pointer-events-none');
    }

    function closeDeleteModal() {
      pendingDeleteId = null;
      document.getElementById('deleteModal').classList.add('opacity-0', 'pointer-events-none');
    }

    function confirmDeleteGame() {
      const idx = gameDatabase.findIndex(g => g.id === pendingDeleteId);
      if (idx === -1) { closeDeleteModal(); return; }
      const [removed] = gameDatabase.splice(idx, 1);
      saveLibraryLocally();
      closeDeleteModal();
      closeGameModal();
      refreshAll();
      showToast(`Deleted ${removed.title}`);
    }

    function openPosterModal(id) {
      const game = gameDatabase.find(g => g.id === id);
      if (!game) return;
      posterTargetId = id;
      document.getElementById('posterGameName').textContent = game.title;
      const pv = document.getElementById('posterPreview'); pv.style.opacity = ''; delete pv.dataset.pending; pv.src = game.poster;
      document.getElementById('posterUrlInput').value = '';
      document.getElementById('posterFileInput').value = '';
      document.getElementById('posterModal').classList.remove('opacity-0', 'pointer-events-none');
      lucide.createIcons();
    }

    function closePosterModal() {
      posterTargetId = null;
      document.getElementById('posterModal').classList.add('opacity-0', 'pointer-events-none');
    }

    function setGamePoster(poster, extra) {
      const game = gameDatabase.find(g => g.id === posterTargetId);
      if (!game) return;
      game.poster = poster;
      game.posterCustom = true;
      if (extra) Object.assign(game, extra);
      saveLibraryLocally();
      fadeSwap(document.getElementById('posterPreview'), poster);
      refreshAll();
      if (!document.getElementById('gameModal').classList.contains('opacity-0')) openGameModal(game.id);
    }

    async function handlePosterFile(event) {
      const file = event.target.files && event.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = () => setGamePoster(reader.result);
      reader.readAsDataURL(file);
    }

    function applyPosterUrl() {
      const url = document.getElementById('posterUrlInput').value.trim();
      if (url) { setGamePoster(url); showToast('Poster updated'); }
    }

    async function fetchPosterFromSteam() {
      const game = gameDatabase.find(g => g.id === posterTargetId);
      if (!game) return;
      const found = await findOfficialGamePoster(game.title);
      if (found) { setGamePoster(found.poster, { steamId: found.steamId }); showToast('Steam poster applied'); }
      else showToast('No Steam poster found');
    }

    function resetPoster() {
      const game = gameDatabase.find(g => g.id === posterTargetId);
      if (!game) return;
      setGamePoster(makeGeneratedPoster(game.title));
      showToast('Poster reset');
    }

    let renameTargetId = null;
    function openRenameModal(id) {
      const game = gameDatabase.find(g => g.id === id);
      if (!game) return;
      renameTargetId = id;
      const input = document.getElementById('renameInput');
      input.value = game.title;
      document.getElementById('renameModal').classList.remove('opacity-0', 'pointer-events-none');
      lucide.createIcons();
      setTimeout(() => { input.focus(); input.select(); }, 50);
    }

    function closeRenameModal() {
      renameTargetId = null;
      document.getElementById('renameModal').classList.add('opacity-0', 'pointer-events-none');
    }

    function confirmRename(e) {
      e.preventDefault();
      const game = gameDatabase.find(g => g.id === renameTargetId);
      if (!game) return;
      const title = document.getElementById('renameInput').value.trim();
      if (!title) return;
      game.title = title;
      saveLibraryLocally();
      closeRenameModal();
      refreshAll();
      showToast(`Renamed to ${title}`);
    }

    document.addEventListener('keydown', (e) => {
      if (e.key !== 'Escape') return;
      closeRenameModal(); closeDeleteModal(); closePosterModal(); closeGameModal(); closeUploadModal();
    });

    function showToast(msg) {
      const toast = document.getElementById('toast');
      document.getElementById('toastMsg').innerText = msg;
      toast.classList.remove('translate-y-20', 'opacity-0');
      setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
      }, 3500);
    }
  </script>
</body>
</html>
