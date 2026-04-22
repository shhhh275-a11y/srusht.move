<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Srusht Movies</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #0a0a0a;
            --bg2: #141414;
            --card: #1a1a1a;
            --accent: #e50914;
            --accent2: #ff6b35;
            --gold: #f5c518;
            --text: #fff;
            --text2: #999;
            --border: rgba(255,255,255,0.08);
        }
        * { margin:0; padding:0; box-sizing:border-box; }
        html { scroll-behavior: smooth; }

        body {
            font-family: 'Cairo', sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* SCROLLBAR */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--bg); }
        ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }

        /* ===== NAVBAR ===== */
        .navbar {
            position: fixed;
            top:0; left:0; right:0;
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 48px;
            height: 68px;
            background: linear-gradient(to bottom, rgba(0,0,0,0.9) 0%, transparent 100%);
            transition: background 0.4s;
        }
        .navbar.scrolled {
            background: rgba(10,10,10,0.97);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border);
        }
        .brand {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 2em;
            letter-spacing: 3px;
            background: linear-gradient(135deg, #e50914, #ff6b35);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-decoration: none;
            cursor: pointer;
        }
        .nav-links {
            display: flex; gap: 28px; list-style: none;
        }
        .nav-links a {
            color: #ccc; text-decoration: none; font-size: 0.9em;
            font-weight: 600; transition: color 0.2s; cursor: pointer;
        }
        .nav-links a:hover { color: #fff; }
        .nav-right { display: flex; align-items: center; gap: 14px; }
        .nav-icon-btn {
            background: none; border: none; color: #ccc;
            font-size: 1.05em; cursor: pointer; transition: color 0.2s;
            padding: 6px;
        }
        .nav-icon-btn:hover { color: #fff; }
        .mode-btn {
            background: rgba(255,255,255,0.07);
            border: 1px solid rgba(255,255,255,0.12);
            color: #ccc; border-radius: 20px;
            padding: 6px 14px; cursor: pointer;
            font-size: 0.82em; display: flex; align-items: center; gap: 6px;
            transition: all 0.2s; font-family: 'Cairo', sans-serif;
        }
        .mode-btn:hover { background: rgba(255,255,255,0.14); color: #fff; }

        /* LIGHT MODE */
        body.light {
            --bg: #f0f0f0; --bg2: #e8e8e8; --card: #fff;
            --text: #111; --text2: #555; --border: rgba(0,0,0,0.1);
        }
        body.light .navbar { background: linear-gradient(to bottom, rgba(240,240,240,0.95) 0%, transparent 100%); }
        body.light .navbar.scrolled { background: rgba(240,240,240,0.97); }
        body.light .nav-links a { color: #444; }
        body.light .movie-card { background: var(--card); box-shadow: 0 4px 20px rgba(0,0,0,0.1); }
        body.light .modal-bg { background: rgba(240,240,240,0.97); }
        body.light .modal-content { background: var(--card); }
        body.light .search-box { background: rgba(0,0,0,0.06); border-color: rgba(0,0,0,0.12); }
        body.light .tab-btn { color: #555; }
        body.light .tab-btn.active { color: #111; }
        body.light .comment-box { background: rgba(0,0,0,0.05); border-color: rgba(0,0,0,0.1); color: #111; }
        body.light .comment-item { background: rgba(0,0,0,0.04); border-color: rgba(0,0,0,0.08); }
        body.light .load-more { background: rgba(0,0,0,0.07); border-color: rgba(0,0,0,0.12); }

        /* ===== HERO ===== */
        .hero {
            position: relative;
            height: 100vh; min-height: 640px;
            overflow: hidden;
            display: flex; flex-direction: column;
            justify-content: flex-end;
        }

        /* SINGLE FULL BACKDROP */
        .hero-backdrop {
            position: absolute; inset: 0; z-index: 0;
            background-size: cover;
            background-position: center top;
            animation: heroZoom 18s ease-in-out infinite alternate;
        }
        @keyframes heroZoom {
            from { transform: scale(1.0); }
            to   { transform: scale(1.07); }
        }

        /* FEATURED POSTER — left side */
        .hero-poster-wrap {
            position: absolute;
            top: 50%; right: 8%;
            transform: translateY(-50%);
            z-index: 4;
            animation: posterIn 1.2s cubic-bezier(0.22,1,0.36,1) both;
        }
        @keyframes posterIn {
            from { opacity:0; transform: translateY(-44%) scale(0.92) rotateY(8deg); }
            to   { opacity:1; transform: translateY(-50%) scale(1) rotateY(0deg); }
        }
        .hero-poster-img {
            width: 260px;
            border-radius: 12px;
            box-shadow:
                0 30px 80px rgba(0,0,0,0.85),
                0 0 0 1px rgba(255,255,255,0.07),
                0 0 60px rgba(229,9,20,0.25);
            display: block;
        }
        .hero-poster-glow {
            position: absolute; inset: -20px;
            background: radial-gradient(ellipse at center, rgba(229,9,20,0.18) 0%, transparent 70%);
            z-index: -1; border-radius: 20px;
            animation: glowPulse 3s ease-in-out infinite alternate;
        }
        @keyframes glowPulse {
            from { opacity: 0.6; }
            to   { opacity: 1; }
        }

        /* OVERLAYS */
        .hero-overlay-top {
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to bottom,
                rgba(0,0,0,0.6) 0%,
                rgba(0,0,0,0.05) 25%,
                rgba(0,0,0,0.05) 55%,
                rgba(0,0,0,0.8) 85%,
                rgba(10,10,10,1) 100%
            );
        }
        .hero-overlay-sides {
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to left,
                rgba(0,0,0,0.45) 0%,
                rgba(0,0,0,0.15) 40%,
                rgba(0,0,0,0.7) 100%
            );
        }
        .hero-vignette {
            position: absolute; inset: 0; z-index: 1;
            background: radial-gradient(ellipse at 35% 50%,
                transparent 30%,
                rgba(0,0,0,0.15) 65%,
                rgba(0,0,0,0.5) 100%
            );
        }

        /* LEFT CONTENT */
        .hero-center {
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 160px;
            z-index: 3;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 0 56px;
            max-width: 600px;
        }
        .hero-site-badge {
            display: inline-flex; align-items: center; gap: 8px;
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1em; letter-spacing: 3px;
            color: rgba(255,255,255,0.55);
            margin-bottom: 18px;
            animation: fadeUp 0.8s ease both;
        }
        .hero-site-badge span {
            width: 28px; height: 2px;
            background: var(--accent);
            display: inline-block;
        }
        .hero-brand-en {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(2.8em, 6vw, 5.5em);
            letter-spacing: 0.1em;
            line-height: 0.9;
            background: linear-gradient(160deg, #ffffff 0%, rgba(255,255,255,0.85) 50%, rgba(229,9,20,0.95) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 30px rgba(229,9,20,0.3)) drop-shadow(0 4px 20px rgba(0,0,0,0.9));
            margin-bottom: 6px;
            animation: brandIn 1s cubic-bezier(0.22,1,0.36,1) 0.1s both;
        }
        @keyframes brandIn {
            from { opacity:0; transform: translateY(24px); }
            to   { opacity:1; transform: translateY(0); }
        }
        .hero-brand-line {
            width: 50px; height: 3px;
            background: var(--accent);
            border-radius: 2px;
            box-shadow: 0 0 16px rgba(229,9,20,0.8);
            margin: 16px 0;
            animation: lineIn 1.2s ease 0.3s both;
        }
        @keyframes lineIn { from { width:0; opacity:0; } to { width:50px; opacity:1; } }
        .hero-brand-sub {
            font-size: 0.95em;
            font-weight: 400;
            color: rgba(255,255,255,0.6);
            letter-spacing: 0.06em;
            margin-bottom: 28px;
            animation: fadeUp 1s ease 0.5s both;
        }

        /* FEATURED FILM INFO under brand */
        .hero-film-info {
            animation: fadeUp 1s ease 0.6s both;
        }
        .hero-film-label {
            font-size: 0.72em; font-weight: 700;
            color: var(--accent); letter-spacing: 2px;
            text-transform: uppercase; margin-bottom: 6px;
        }
        .hero-film-title-big {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(1.8em, 4vw, 3em);
            letter-spacing: 2px;
            color: #fff;
            line-height: 1; margin-bottom: 8px;
            text-shadow: 0 2px 20px rgba(0,0,0,0.8);
        }
        .hero-film-tags {
            display: flex; gap: 10px; flex-wrap: wrap;
            margin-bottom: 20px;
        }
        .hero-film-tag {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.18);
            color: #ddd; font-size: 0.75em; font-weight: 600;
            padding: 4px 12px; border-radius: 20px;
            backdrop-filter: blur(4px);
        }
        .hero-film-tag.red { background: rgba(229,9,20,0.2); border-color: rgba(229,9,20,0.35); color: #ff6b6b; }
        .hero-cta {
            display: inline-flex; align-items: center; gap: 10px;
            background: var(--accent); color: #fff;
            padding: 13px 28px; border-radius: 8px;
            border: none; cursor: pointer;
            font-family: 'Cairo', sans-serif;
            font-size: 0.95em; font-weight: 700;
            transition: background 0.2s, transform 0.2s;
            box-shadow: 0 4px 20px rgba(229,9,20,0.4);
        }
        .hero-cta:hover { background: #c4070f; transform: translateY(-2px); }

        @keyframes fadeUp {
            from { opacity:0; transform:translateY(16px); }
            to   { opacity:1; transform:translateY(0); }
        }

        /* BOTTOM FILM STRIP */
        .hero-film-row {
            position: relative; z-index: 4;
            display: flex; gap: 0;
        }
        .hero-film-card {
            flex: 1; position: relative;
            height: 150px; overflow: hidden;
            cursor: pointer;
            border-top: 2px solid rgba(229,9,20,0.4);
        }
        .hero-film-card::before {
            content: '';
            position: absolute; inset: 0; z-index: 1;
            background: linear-gradient(to top, rgba(0,0,0,0.88) 0%, rgba(0,0,0,0.1) 60%, transparent 100%);
            transition: background 0.3s;
        }
        .hero-film-card:hover::before {
            background: linear-gradient(to top, rgba(229,9,20,0.65) 0%, rgba(0,0,0,0.05) 70%, transparent 100%);
        }
        .hero-film-card-bg {
            position: absolute; inset: -4px;
            background-size: cover; background-position: center;
            transition: transform 0.5s ease;
        }
        .hero-film-card:hover .hero-film-card-bg { transform: scale(1.07); }
        .hero-film-card-info {
            position: absolute; bottom: 10px; left: 12px; right: 12px; z-index: 2;
        }
        .hero-film-card-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1.05em; letter-spacing: 1.5px;
            color: #fff; line-height: 1; margin-bottom: 3px;
            text-shadow: 0 2px 8px rgba(0,0,0,0.9);
        }
        .hero-film-card-meta {
            font-size: 0.7em; color: rgba(255,255,255,0.6);
            display: flex; gap: 7px;
        }
        .hero-film-card-rating { color: var(--gold); font-weight: 700; }
        .hero-film-card-divider {
            width: 1px; background: rgba(229,9,20,0.5);
            box-shadow: 0 0 6px rgba(229,9,20,0.4);
            flex-shrink: 0; align-self: stretch;
        }

        /* hide old unused classes */
        .hero-bg, .hero-glow, .hero-film-strip, .hero-poster,
        .hero-badge, .hero-title, .hero-meta, .hero-desc,
        .hero-btns, .btn-watch, .btn-more,
        .hero-bottom-gradient, .hero-content { display: none; }

        /* ===== MAIN ===== */
        .main { padding: 0 48px 80px; }

        /* SEARCH */
        .search-wrap { margin: 32px 0 10px; max-width: 680px; }
        .search-box {
            display: flex; align-items: center;
            background: rgba(255,255,255,0.06);
            border: 1px solid var(--border);
            border-radius: 10px; padding: 6px 6px 6px 20px;
            transition: border-color 0.2s;
        }
        .search-box:focus-within { border-color: var(--accent); }
        .search-box i { color: var(--text2); margin-left: 10px; }
        .search-input {
            flex: 1; background: transparent; border: none; outline: none;
            color: var(--text); font-size: 1em;
            font-family: 'Cairo', sans-serif; padding: 9px 0;
        }
        .search-input::placeholder { color: var(--text2); }
        .search-btn {
            background: var(--accent); border: none; border-radius: 7px;
            padding: 10px 24px; color: #fff; cursor: pointer;
            font-size: 0.9em; font-weight: 700;
            font-family: 'Cairo', sans-serif; transition: background 0.2s;
        }
        .search-btn:hover { background: #c4070f; }

        /* TABS */
        .tabs {
            display: flex; gap: 4px; margin: 26px 0 20px;
            border-bottom: 1px solid var(--border);
            flex-wrap: wrap;
        }
        .tab-btn {
            background: none; border: none; color: var(--text2);
            font-size: 0.9em; font-weight: 600;
            padding: 10px 20px; cursor: pointer;
            border-bottom: 2px solid transparent;
            margin-bottom: -1px; transition: all 0.2s;
            font-family: 'Cairo', sans-serif;
        }
        .tab-btn.active { color: var(--text); border-bottom-color: var(--accent); }
        .tab-btn:hover:not(.active) { color: var(--text); }

        /* SECTION TITLE */
        .sec-title {
            font-size: 1.25em; font-weight: 700;
            margin-bottom: 20px; display: flex;
            align-items: center; gap: 10px;
        }
        .sec-title .count { color: var(--accent); font-size: 0.82em; }

        /* FAVORITES ROW */
        .fav-section { margin-bottom: 42px; }
        .fav-empty {
            background: rgba(255,255,255,0.03);
            border: 1px dashed var(--border);
            border-radius: 12px; padding: 36px;
            text-align: center; color: var(--text2);
        }
        .fav-empty i { font-size: 2.2em; color: var(--accent); opacity:0.4; display:block; margin-bottom: 10px; }
        .fav-row {
            display: flex; gap: 14px; overflow-x: auto;
            padding-bottom: 10px; scroll-snap-type: x mandatory;
        }
        .fav-row::-webkit-scrollbar { height: 3px; }
        .fav-row::-webkit-scrollbar-thumb { background: var(--accent); }
        .fav-mini {
            min-width: 140px; border-radius: 8px; overflow: hidden;
            background: var(--card); cursor: pointer;
            position: relative; scroll-snap-align: start;
            transition: transform 0.2s; flex-shrink: 0;
        }
        .fav-mini:hover { transform: scale(1.04); }
        .fav-mini-img { width: 140px; height: 190px; object-fit: cover; display: block; background: #222; }
        .fav-mini-title { padding: 8px; font-size: 0.78em; font-weight: 600; color: var(--text); line-height: 1.3; }
        .fav-mini-remove {
            position: absolute; top: 6px; left: 6px;
            background: rgba(229,9,20,0.85); border: none;
            width: 26px; height: 26px; border-radius: 50%;
            color: #fff; font-size: 0.72em; cursor: pointer;
            display: flex; align-items: center; justify-content: center;
        }

        /* MOVIE GRID */
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(195px, 1fr));
            gap: 20px; margin-bottom: 30px;
        }
        .movie-card {
            background: var(--card); border-radius: 10px;
            overflow: hidden; cursor: pointer;
            transition: transform 0.25s, box-shadow 0.25s;
            position: relative;
        }
        .movie-card:hover {
            transform: scale(1.045);
            box-shadow: 0 14px 44px rgba(0,0,0,0.55), 0 0 0 1px rgba(229,9,20,0.25);
            z-index: 2;
        }
        .card-poster {
            width: 100%; height: 275px;
            object-fit: cover; display: block;
            background: #1a1a1a;
        }
        .card-overlay {
            position: absolute; inset: 0;
            background: linear-gradient(to top, rgba(0,0,0,0.9) 0%, transparent 55%);
            opacity: 0; transition: opacity 0.25s;
            display: flex; flex-direction: column;
            justify-content: flex-end; padding: 14px;
        }
        .movie-card:hover .card-overlay { opacity: 1; }
        .overlay-play {
            width: 40px; height: 40px; border-radius: 50%;
            background: rgba(229,9,20,0.9);
            display: flex; align-items: center; justify-content: center;
            color: #fff; font-size: 0.9em; margin-bottom: 8px;
        }
        .overlay-year { font-size: 0.8em; color: #ccc; }
        .fav-btn {
            position: absolute; top: 10px; left: 10px;
            background: rgba(0,0,0,0.72); border: none;
            width: 32px; height: 32px; border-radius: 50%;
            color: #fff; font-size: 0.82em; cursor: pointer;
            display: flex; align-items: center; justify-content: center;
            transition: all 0.2s; backdrop-filter: blur(4px);
        }
        .fav-btn:hover { background: var(--accent); }
        .fav-btn.on { background: var(--accent); }
        .age-tag {
            position: absolute; top: 10px; right: 10px;
            background: rgba(0,0,0,0.75);
            color: #ccc; font-size: 0.68em; font-weight: 700;
            padding: 3px 7px; border-radius: 4px;
            border: 1px solid rgba(255,255,255,0.18);
        }
        .card-info { padding: 13px; }
        .card-title { font-size: 0.9em; font-weight: 700; margin-bottom: 5px; line-height: 1.3; }
        .card-meta { display: flex; justify-content: space-between; }
        .card-meta span { font-size: 0.78em; color: var(--text2); }
        .card-rating { color: var(--gold) !important; font-weight: 700 !important; }

        /* NO RESULTS */
        .no-results {
            text-align: center; padding: 60px; color: var(--text2); display: none;
        }
        .no-results i { font-size: 2.5em; color: var(--accent); opacity:0.35; display:block; margin-bottom: 12px; }

        /* LOAD MORE */
        .load-more {
            display: block; margin: 10px auto 50px;
            padding: 12px 44px;
            background: rgba(255,255,255,0.07);
            border: 1px solid rgba(255,255,255,0.12);
            color: var(--text); border-radius: 8px;
            cursor: pointer; font-size: 0.95em; font-weight: 600;
            font-family: 'Cairo', sans-serif; transition: all 0.2s;
        }
        .load-more:hover { background: var(--accent); border-color: var(--accent); }

        /* ===== MOVIE MODAL ===== */
        .modal-wrap {
            position: fixed; inset: 0; z-index: 3000;
            display: flex; align-items: center; justify-content: center;
            padding: 20px;
            opacity: 0; pointer-events: none; transition: opacity 0.3s;
        }
        .modal-wrap.open { opacity: 1; pointer-events: all; }
        .modal-overlay {
            position: absolute; inset: 0;
            background: rgba(0,0,0,0.85); backdrop-filter: blur(8px);
        }
        .modal-box {
            position: relative; z-index: 1;
            background: var(--card);
            border-radius: 16px; overflow: hidden;
            width: 100%; max-width: 860px;
            max-height: 90vh; overflow-y: auto;
            box-shadow: 0 30px 80px rgba(0,0,0,0.8);
            animation: modalIn 0.35s ease both;
        }
        @keyframes modalIn {
            from { transform: scale(0.93) translateY(20px); opacity: 0; }
            to { transform: scale(1) translateY(0); opacity: 1; }
        }
        .modal-hero {
            position: relative; height: 320px;
            background-size: cover; background-position: center top;
        }
        .modal-hero-grad {
            position: absolute; inset: 0;
            background: linear-gradient(to top, var(--card) 0%, rgba(0,0,0,0.3) 60%, transparent 100%);
        }
        .modal-close {
            position: absolute; top: 14px; left: 14px; z-index: 2;
            background: rgba(0,0,0,0.7); border: none; color: #fff;
            width: 36px; height: 36px; border-radius: 50%;
            font-size: 0.95em; cursor: pointer;
            display: flex; align-items: center; justify-content: center;
            backdrop-filter: blur(4px); transition: background 0.2s;
        }
        .modal-close:hover { background: var(--accent); }
        .modal-hero-title {
            position: absolute; bottom: 20px; right: 24px; left: 24px; z-index: 2;
        }
        .modal-hero-title h2 {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 2.2em; letter-spacing: 2px;
            background: linear-gradient(135deg, #fff 0%, #ccc 100%);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            line-height: 1;
        }
        .modal-hero-title .en-title { font-size: 0.85em; color: #aaa; font-family: 'Bebas Neue', sans-serif; letter-spacing: 2px; }
        .modal-body { padding: 24px 28px 32px; }
        .modal-tags { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 18px; }
        .modal-tag {
            background: rgba(229,9,20,0.15); color: var(--accent);
            border: 1px solid rgba(229,9,20,0.25);
            font-size: 0.75em; font-weight: 700;
            padding: 4px 12px; border-radius: 20px;
        }
        .modal-tag.gold { background: rgba(245,197,24,0.1); color: var(--gold); border-color: rgba(245,197,24,0.25); }
        .modal-tag.blue { background: rgba(59,130,246,0.1); color: #60a5fa; border-color: rgba(59,130,246,0.25); }
        .modal-stats {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
            gap: 14px; margin-bottom: 22px;
        }
        .stat-box {
            background: rgba(255,255,255,0.04);
            border: 1px solid var(--border);
            border-radius: 8px; padding: 12px 14px;
        }
        .stat-label { font-size: 0.72em; color: var(--text2); margin-bottom: 4px; text-transform: uppercase; letter-spacing: 1px; }
        .stat-val { font-size: 1em; font-weight: 700; color: var(--text); }
        .stat-val.gold { color: var(--gold); }
        .modal-section { margin-bottom: 20px; }
        .modal-section h4 { font-size: 0.9em; font-weight: 700; color: var(--accent); margin-bottom: 8px; letter-spacing: 1px; text-transform: uppercase; }
        .modal-section p { font-size: 0.9em; color: var(--text2); line-height: 1.75; }
        .modal-section ul { padding-right: 18px; }
        .modal-section ul li { font-size: 0.88em; color: var(--text2); line-height: 1.8; }
        .awards-list { display: flex; flex-wrap: wrap; gap: 8px; }
        .award-chip {
            background: rgba(245,197,24,0.08);
            border: 1px solid rgba(245,197,24,0.2);
            color: var(--gold); font-size: 0.75em; font-weight: 600;
            padding: 5px 12px; border-radius: 20px;
        }
        .modal-fav-btn {
            display: flex; align-items: center; gap: 8px;
            background: rgba(229,9,20,0.12);
            border: 1px solid rgba(229,9,20,0.3);
            color: var(--accent); border-radius: 8px;
            padding: 10px 20px; cursor: pointer;
            font-size: 0.9em; font-weight: 700;
            font-family: 'Cairo', sans-serif; transition: all 0.2s;
            margin-bottom: 22px;
        }
        .modal-fav-btn:hover, .modal-fav-btn.on {
            background: var(--accent); color: #fff;
        }
        /* TRAILER */
        .trailer-btn {
            display: flex; align-items: center; gap: 12px;
            background: linear-gradient(135deg, #e50914, #b0060f);
            color: #fff; border: none; border-radius: 10px;
            padding: 14px 28px; cursor: pointer;
            font-size: 1em; font-weight: 700;
            font-family: 'Cairo', sans-serif;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 4px 20px rgba(229,9,20,0.4);
            width: 100%; justify-content: center;
            margin-bottom: 14px;
        }
        .trailer-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 28px rgba(229,9,20,0.55); }
        .trailer-btn .play-icon { font-size: 1.3em; }
        .trailer-player {
            display: none;
            width: 100%; aspect-ratio: 16/9;
            border-radius: 10px; overflow: hidden;
            margin-bottom: 20px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.7);
            border: 1px solid rgba(229,9,20,0.3);
        }
        .trailer-player iframe { width: 100%; height: 100%; border: none; display: block; }
        .trailer-player.open { display: block; animation: fadeUp 0.3s ease both; }

        /* ===== COMMENTS ===== */
        .comment-section { margin: 50px 0; border-top: 1px solid var(--border); padding-top: 44px; }
        .comment-form { display: flex; flex-direction: column; gap: 12px; margin-bottom: 30px; }
        .comment-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .comment-box {
            width: 100%; background: rgba(255,255,255,0.05);
            border: 1px solid var(--border); border-radius: 8px;
            padding: 12px 16px; color: var(--text);
            font-size: 0.92em; font-family: 'Cairo', sans-serif;
            outline: none; transition: border-color 0.2s; resize: none;
        }
        .comment-box:focus { border-color: var(--accent); }
        .comment-box::placeholder { color: var(--text2); }
        .comment-submit {
            align-self: flex-end;
            background: var(--accent); color: #fff; border: none;
            border-radius: 8px; padding: 12px 28px;
            font-size: 0.92em; font-weight: 700; cursor: pointer;
            font-family: 'Cairo', sans-serif; transition: background 0.2s;
            display: flex; align-items: center; gap: 8px;
        }
        .comment-submit:hover { background: #c4070f; }
        .comments-list { display: flex; flex-direction: column; gap: 12px; }
        .comment-item {
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border);
            border-radius: 10px; padding: 16px 20px;
            display: flex; gap: 14px; align-items: flex-start;
        }
        .c-avatar {
            width: 40px; height: 40px; border-radius: 50%;
            background: linear-gradient(135deg, var(--accent), var(--accent2));
            display: flex; align-items: center; justify-content: center;
            font-weight: 800; font-size: 1em; flex-shrink: 0;
        }
        .c-body { flex: 1; }
        .c-author { font-weight: 700; font-size: 0.88em; margin-bottom: 3px; }
        .c-movie-ref { color: var(--accent); font-size: 0.82em; font-weight: 600; }
        .c-text { font-size: 0.88em; color: var(--text2); line-height: 1.65; }
        .c-bottom { display: flex; align-items: center; gap: 12px; margin-top: 7px; }
        .c-time { font-size: 0.74em; color: var(--text2); opacity: 0.55; }
        .c-like {
            background: none; border: none; color: var(--text2);
            cursor: pointer; font-size: 0.82em;
            display: flex; align-items: center; gap: 4px;
            font-family: 'Cairo', sans-serif; transition: color 0.2s;
            padding: 3px 8px; border-radius: 4px;
        }
        .c-like:hover, .c-like.liked { color: var(--accent); }

        /* INSTAGRAM */
        .ig-section { text-align: center; margin: 36px 0; }
        .ig-btn {
            display: inline-flex; align-items: center; gap: 10px;
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            color: #fff; padding: 13px 32px; border-radius: 50px;
            text-decoration: none; font-weight: 700; font-size: 0.95em;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .ig-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(131,58,180,0.4); }

        /* FOOTER */
        .footer {
            background: rgba(0,0,0,0.35); border-top: 1px solid var(--border);
            padding: 28px 48px; text-align: center;
        }
        .footer p { color: var(--text2); font-size: 0.87em; }
        .footer a { color: var(--accent); text-decoration: none; }

        /* SCROLL TOP */
        .scroll-top {
            position: fixed; bottom: 28px; left: 28px;
            width: 42px; height: 42px; background: var(--accent);
            border: none; border-radius: 50%; color: #fff;
            font-size: 0.95em; cursor: pointer;
            display: flex; align-items: center; justify-content: center;
            opacity: 0; transform: translateY(16px);
            transition: opacity 0.3s, transform 0.3s; z-index: 800;
            box-shadow: 0 4px 16px rgba(229,9,20,0.45);
        }
        .scroll-top.show { opacity: 1; transform: translateY(0); }

        @keyframes fadeUp {
            from { opacity:0; transform: translateY(18px); }
            to { opacity:1; transform: translateY(0); }
        }
        .movie-card { animation: fadeUp 0.4s ease both; }

        @media(max-width:768px) {
            .navbar { padding: 0 16px; }
            .nav-links { display: none; }
            .hero { padding: 0 16px 50px; }
            .hero-title { font-size: 2.8em; }
            .main { padding: 0 16px 60px; }
            .movie-grid { grid-template-columns: repeat(auto-fill, minmax(155px, 1fr)); gap: 14px; }
            .card-poster { height: 215px; }
            .comment-row { grid-template-columns: 1fr; }
            .modal-stats { grid-template-columns: 1fr 1fr; }
            .modal-body { padding: 18px 18px 26px; }
            .footer { padding: 20px 16px; }
        }
    </style>
</head>
<body>

<!-- NAVBAR -->
<nav class="navbar" id="navbar">
    <span class="brand">Srusht Movies</span>
    <ul class="nav-links">
        <li><a onclick="scrollTo(0,0)">سەرەکی</a></li>
        <li><a onclick="document.getElementById('favSec').scrollIntoView({behavior:'smooth'})">دلخوازەکانم</a></li>
        <li><a onclick="document.getElementById('gridSec').scrollIntoView({behavior:'smooth'})">فیلمەکان</a></li>
        <li><a onclick="document.getElementById('commentSec').scrollIntoView({behavior:'smooth'})">کۆمینت</a></li>
    </ul>
    <div class="nav-right">
        <button class="mode-btn" id="modeBtn"><i class="fas fa-moon"></i><span>شەو</span></button>
    </div>
</nav>

<!-- HERO -->
<section class="hero" id="heroSec">

    <!-- full backdrop -->
    <div class="hero-backdrop" id="heroBackdrop"></div>

    <!-- overlays -->
    <div class="hero-overlay-top"></div>
    <div class="hero-overlay-sides"></div>
    <div class="hero-vignette"></div>

    <!-- poster right side -->
    <div class="hero-poster-wrap" id="heroPosterWrap">
        <div class="hero-poster-glow"></div>
        <img class="hero-poster-img" id="heroPosterImg" src="" alt="">
    </div>

    <!-- left content: site brand + featured film info -->
    <div class="hero-center">
        <div class="hero-site-badge">
            <span></span> SRUSHT MOVIES <span></span>
        </div>
        <div class="hero-brand-en">SRUSHT<br>MOVIES</div>
        <div class="hero-brand-line"></div>
        <div class="hero-brand-sub">یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلم و دراما</div>

        <div class="hero-film-info" id="heroFilmInfo"></div>
    </div>

    <!-- bottom 4-film strip -->
    <div class="hero-film-row" id="heroFilmRow"></div>

</section>

<!-- MAIN -->
<main class="main">

    <!-- SEARCH -->
    <div class="search-wrap">
        <div class="search-box">
            <i class="fas fa-search"></i>
            <input class="search-input" id="searchInput" placeholder="گەڕان بە ناوی فیلم...">
            <button class="search-btn" onclick="doSearch()">گەڕان</button>
        </div>
    </div>

    <!-- TABS -->
    <div class="tabs">
        <button class="tab-btn active" data-tab="all">هەموو</button>
        <button class="tab-btn" data-tab="thriller">Thriller</button>
        <button class="tab-btn" data-tab="drama">Drama</button>
        <button class="tab-btn" data-tab="scifi">Sci-Fi</button>
        <button class="tab-btn" data-tab="crime">Crime</button>
        <button class="tab-btn" data-tab="top9">⭐ +9.0</button>
    </div>

    <!-- FAVORITES -->
    <section class="fav-section" id="favSec">
        <div class="sec-title"><i class="fas fa-heart" style="color:var(--accent)"></i> دلخوازەکانم <span class="count" id="favCount">(0)</span></div>
        <div class="fav-empty" id="favEmpty"><i class="fas fa-heart-broken"></i>هیچ فیلمێک زیاد نەکردووە — لەسەر ❤️ کلیک بکە</div>
        <div class="fav-row" id="favRow" style="display:none"></div>
    </section>

    <!-- GRID -->
    <section id="gridSec">
        <div class="sec-title"><i class="fas fa-film" style="color:var(--accent)"></i> فیلمەکان <span class="count" id="movieCount"></span></div>
        <div class="movie-grid" id="movieGrid"></div>
        <div class="no-results" id="noRes"><i class="fas fa-search"></i>هیچ فیلمێک نەدۆزرایەوە</div>
        <button class="load-more" id="loadMore" style="display:none"><i class="fas fa-chevron-down"></i> زیاتر باربکە</button>
    </section>

    <!-- INSTAGRAM -->
    <div class="ig-section">
        <a href="https://www.instagram.com/lipri_26" class="ig-btn" target="_blank"><i class="fab fa-instagram"></i> سەردانی ئینستاگرام بکە</a>
    </div>

    <!-- COMMENTS -->
    <section class="comment-section" id="commentSec">
        <div class="sec-title"><i class="fas fa-comments" style="color:var(--accent)"></i> کۆمینتەکان <span class="count" id="commentCount">(0)</span></div>
        <div class="comment-form">
            <div class="comment-row">
                <input class="comment-box" id="cName" placeholder="ناوت...">
                <input class="comment-box" id="cMovie" placeholder="ناوی فیلم (ئارەزوومەند)">
            </div>
            <textarea class="comment-box" id="cText" rows="3" placeholder="کۆمینتەکەت بنووسە..."></textarea>
            <button class="comment-submit" onclick="addComment()"><i class="fas fa-paper-plane"></i> ناردن</button>
        </div>
        <div class="comments-list" id="commentsList"></div>
    </section>
</main>

<!-- FOOTER -->
<footer class="footer">
    <p>دروستکراوە بە ❤️ بۆ کوردەکان &nbsp;|&nbsp; <a href="https://www.instagram.com/lipri_26" target="_blank">@lipri_26</a> &nbsp;|&nbsp; Srusht Movies &copy; 2025</p>
</footer>

<!-- SCROLL TOP -->
<button class="scroll-top" id="scrollTop" onclick="scrollTo({top:0,behavior:'smooth'})"><i class="fas fa-arrow-up"></i></button>

<!-- MODAL -->
<div class="modal-wrap" id="modalWrap">
    <div class="modal-overlay" onclick="closeModal()"></div>
    <div class="modal-box" id="modalBox"></div>
</div>

<script>
// ===== 50 REAL MOVIES =====
const MOVIES = [
    {
        id:0, en:"Fight Club", ku:"فایت کلاب", year:1999, rating:8.8, duration:"139 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"David Fincher", cast:"Brad Pitt, Edward Norton, Helena Bonham Carter",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"کارمەندێکی ناڕازی لەگەڵ فرۆشیاری سابونی بازنی سیگار ئەدەن Durden کۆمەڵێکی شەڕی نهێنی دادەمەزرێنن کە بەم شێوەیە کۆمەڵگەیەکی تووڕەیان دروست دەکات. فیلمەکە کریتیکێکی زیندووی سیستەمی کۆنسومەریزم و ناسنامەی نێرینەیە. کۆتایی فیلمەکە یەکێک لە شۆکەکەرترین کۆتاییەکانی مێژووی سینەمایە.",
        awards:["Oscar: Best Film Editing (Nominated)", "BAFTA: Best Editing", "Saturn Award: Best Director"],
        trivia:"کتێبی بنچینەی فیلمەکە لە 1996 لەلایەن Chuck Palahniuk نووسراوە. Brad Pitt تەنها 137 خولەک لە فیلمەکەدا دەردەکەوێت.",
        tmdb_id:550,
        trailer:"qtRKdVHc-cE",
        poster:"https://upload.wikimedia.org/wikipedia/en/f/fc/Fight_Club_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/f/fc/Fight_Club_poster.jpg"
    },
    {
        id:1, en:"The Sixth Sense", ku:"هەستی شەشەم", year:1999, rating:8.1, duration:"107 خولەک",
        genre:["thriller","drama"], age:"PG-13",
        director:"M. Night Shyamalan", cast:"Bruce Willis, Haley Joel Osment, Toni Collette",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"کوڕێکی بچووک بە ئەستەرەی دەوتووی قسەی رووحەکان دەکات. دکتۆرێکی مێشک ئەوەی دەگرێتەوە و هەوڵی یارمەتیدانی دەدات. بەڵام ئەو ڕاستییەی لە کۆتاییدا ئاشکرا دەبێت هەموو بینینەکانت دووبارە دەگۆڕێت.",
        awards:["Oscar: Best Director (Nominated)", "Oscar: Best Supporting Actor (Nominated)", "Oscar: Best Picture (Nominated)"],
        trivia:"M. Night Shyamalan ئەم فیلمە لە 37 ڕۆژدا نووسی. فیلمەکە لە باجەتی 40 ملیۆن دۆلاری، 672 ملیۆن دۆلاری بەدەست هێنا.",
        tmdb_id:745,
        trailer:"VG9AGf66tXM",
        poster:"https://upload.wikimedia.org/wikipedia/en/2/28/Sixth_Sense_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/2/28/Sixth_Sense_poster.jpg"
    },
    {
        id:2, en:"Shutter Island", ku:"شوتەر ئایلەند", year:2010, rating:8.2, duration:"138 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Martin Scorsese", cast:"Leonardo DiCaprio, Mark Ruffalo, Ben Kingsley",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"دوو دیتێکتیڤی فیدرالی لە 1954 ئەرکداری دەبن تا مارشالی ئامریکا لە دوا گیراوەیەکی مەزن لەگەڵ نەخۆشانی دیوانەی گوێزراوەتەوە تاوانبار لەگەڵ خۆی دابگرن. ئەو چیرۆکە لەوەیە کە بیری لێ دەکەیتەوە.",
        awards:["Saturn Award: Best Horror Film", "Empire Award: Best Thriller"],
        trivia:"Leonardo DiCaprio بۆ ئامادەکاری بۆ ئەم ڕۆڵە، کتێبی دەروونناسی و مێژووی دەرمانگەی دیوانانەی خوێندەوە.",
        tmdb_id:11324,
        trailer:"5iaYLCiq5RM",
        poster:"https://upload.wikimedia.org/wikipedia/en/8/8d/Shutter_Island_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/8/8d/Shutter_Island_poster.jpg"
    },
    {
        id:3, en:"Parasite", ku:"پاراسایت", year:2019, rating:8.5, duration:"132 خولەک",
        genre:["thriller","drama","crime"], age:"R",
        director:"Bong Joon-ho", cast:"Song Kang-ho, Lee Sun-kyun, Cho Yeo-jeong",
        country:"کۆریای باشوور", language:"کۆری",
        plot:"خێزانێکی هەژار بە تیشکبازی ئامادەکاری دەکەن و خۆیان بە مامۆستای ئینگلیزی و دەروونناسی نیشان دەدەن بۆ خێزانێکی سەروەت. بەڵام نهێنییەکی ژێر خانووەکە هەموو شتێک دەگۆڕێت.",
        awards:["Oscar: Best Picture", "Oscar: Best Director", "Oscar: Best International Film", "Oscar: Best Original Screenplay", "Palme d'Or - Cannes 2019"],
        trivia:"یەکەمین فیلمی کۆریایی کە Oscar ی باشترین فیلمی وەرگرت. Bong Joon-ho کۆتاییەکەی لە 3 ڕۆڵی جیاواز نووسی.",
        tmdb_id:496243,
        trailer:"5xH0HfJHsaY",
        poster:"https://upload.wikimedia.org/wikipedia/en/5/53/Parasite_%282019%29_BongJoonho.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/5/53/Parasite_%282019%29_BongJoonho.png"
    },
    {
        id:4, en:"Inception", ku:"ئینسپشن", year:2010, rating:8.8, duration:"148 خولەک",
        genre:["scifi","thriller"], age:"PG-13",
        director:"Christopher Nolan", cast:"Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page",
        country:"ئەمریکا / UK", language:"ئینگلیزی",
        plot:"دزێک تەخصوصی کە بە تەکنۆلۆجیا دەتوانێت خەون و بیرەکانی کەسانی تر بدزێت، ئەرکی ئەوەی دەدرێتێ تا ئیدیایەک لە ذیهنی کەسێکدا دانانێت. سەفەری ناو خەونانەکان دەستپێدەکات.",
        awards:["Oscar: Best Cinematography", "Oscar: Best Visual Effects", "Oscar: Best Sound Editing", "Oscar: Best Sound Mixing"],
        trivia:"Christopher Nolan 10 ساڵ کارکرد لەسەر سکریپتەکە. فیلمەکە 160 ملیۆن دۆلاری باجەتی بوو و 836 ملیۆن بەدەست هێنا.",
        tmdb_id:27205,
        trailer:"YoHD9XEInc0",
        poster:"https://upload.wikimedia.org/wikipedia/en/2/2e/Inception_%282010%29_theatrical_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/2/2e/Inception_%282010%29_theatrical_poster.jpg"
    },
    {
        id:5, en:"Memento", ku:"مەمینتۆ", year:2000, rating:8.4, duration:"113 خولەک",
        genre:["thriller","crime"], age:"R",
        director:"Christopher Nolan", cast:"Guy Pearce, Carrie-Anne Moss, Joe Pantoliano",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"پیاوێک ناخۆشی بیرنەکردنەوەی بابکار هەیە — نەیدەتوانێت یادداشتی نوێ بگرێت. بۆ ئەوەی ئەو کەسە بدۆزێتەوە کە ژنی کوشتووه، لەسەر جەستەی خۆیدا تێبینی دەنووسێت و وێنەی دەکێشێت.",
        awards:["Oscar: Best Editing (Nominated)", "Oscar: Best Screenplay (Nominated)", "Writers Guild Award: Best Screenplay"],
        trivia:"فیلمەکە بە دوو ئیستراتیژی جیاواز بیناوەتەوە دەکرێت — یەکێک لە پێش بۆ دواوە، یەکیش لە دواوە بۆ پێش.",
        tmdb_id:77,
        trailer:"0vS0E9bBSL0",
        poster:"https://upload.wikimedia.org/wikipedia/en/3/35/Memento_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/3/35/Memento_poster.jpg"
    },
    {
        id:6, en:"The Prestige", ku:"دەستگیری", year:2006, rating:8.5, duration:"130 خولەک",
        genre:["thriller","drama"], age:"PG-13",
        director:"Christopher Nolan", cast:"Christian Bale, Hugh Jackman, Scarlett Johansson",
        country:"ئەمریکا / UK", language:"ئینگلیزی",
        plot:"دوو دۆستی سیحربازی کامل لەدواخستنەکەی یەکیان تەقی دەکەن و دەبنە دوژمن. هەر یەکیان هەوڵ دەدات نهێنی تیلسمی تەرافی یەکی تری ئاشکرا بکات. نهێنییەکە بەیەکەوە تا ئاخر یەک دوای یەک ئاشکرا دەبن.",
        awards:["Oscar: Best Cinematography (Nominated)", "Oscar: Best Art Direction (Nominated)"],
        trivia:"Christopher Nolan دوو سکریپت جیاواز نووسی — یەکێک بۆ Christian Bale، یەکیش بۆ Hugh Jackman — هەر یەکیان تەنها سکریپتی خۆیانی بینی.",
        tmdb_id:1124,
        trailer:"RLtaA9fFNXU",
        poster:"https://upload.wikimedia.org/wikipedia/en/d/df/The_Prestige_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/d/df/The_Prestige_poster.jpg"
    },
    {
        id:7, en:"Gone Girl", ku:"کچە ونبووە", year:2014, rating:8.1, duration:"149 خولەک",
        genre:["thriller","drama","crime"], age:"R",
        director:"David Fincher", cast:"Ben Affleck, Rosamund Pike, Neil Patrick Harris",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"ژنی پیاوێک لە ئەنیڤەرسەری ئازادییانەوە ناپەیدا دەبێت. پۆلیس و میدیا دوژمنایەتی بەرامبەر شووی دروست دەکەن. بەڵام ئەو کیسەیە زیاتر لەوەیە کە لە ئەتتل دەبینرێت.",
        awards:["Oscar: Best Actress (Nominated - Rosamund Pike)", "Golden Globe: Best Actress", "BAFTA: Best Editing"],
        trivia:"Rosamund Pike بۆ ئامادەکاری ئەم ڕۆڵە، کتێبی دەروونناسی خوێندەوە. David Fincher 50 دەرفەت هەموو سەحنەیەک دەگرێت.",
        tmdb_id:209112,
        trailer:"dcR0WYxzMkA",
        poster:"https://upload.wikimedia.org/wikipedia/en/d/d4/Gone_Girl_Poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/d/d4/Gone_Girl_Poster.jpg"
    },
    {
        id:8, en:"Get Out", ku:"دەرچۆ", year:2017, rating:7.7, duration:"104 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Jordan Peele", cast:"Daniel Kaluuya, Allison Williams, Bradley Whitford",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"کوڕێکی ڕەش کە بەرەوی خانوودایەی کچی سپیی ئەچێت، خۆی لەناو بارودۆخێکی ترسناکدا دەبینێت. ئەو مالبات و دۆستانە رەفتارێکی گواستراوەیان هەیە. نهێنی ئەوان بۆ کۆتایی ئاشکرا دەبێت.",
        awards:["Oscar: Best Original Screenplay", "BAFTA: Best Original Screenplay", "Sundance: Audience Award"],
        trivia:"Jordan Peele سکریپتەکەی لە 2008 نووسی. فیلمەکە لە باجەتی 4.5 ملیۆن دۆلاری، 255 ملیۆن بەدەست هێنا.",
        tmdb_id:419430,
        trailer:"DzfpyUB60YY",
        poster:"https://upload.wikimedia.org/wikipedia/en/a/a1/Get_Out_poster.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/a/a1/Get_Out_poster.png"
    },
    {
        id:9, en:"Oldboy", ku:"ئۆڵدبۆی", year:2003, rating:8.1, duration:"120 خولەک",
        genre:["thriller","drama","crime"], age:"R",
        director:"Park Chan-wook", cast:"Choi Min-sik, Yoo Ji-tae, Kang Hye-jung",
        country:"کۆریای باشوور", language:"کۆری",
        plot:"پیاوێک بەبێ هیچ هۆکارێک 15 ساڵ لە ژووری نهێنیدا دادەنرێت. کاتێک ئازاد دەکرێت، تەنها 5 ڕۆژی هەیە تا هۆکارەکەی بزانێت. ئەو ڕاستییەی لە کۆتایی ئاشکرا دەبێت ئاسمانت بەسەردا دەوەستێت.",
        awards:["Grand Prix - Cannes 2004", "Grand Bell Awards: Best Film"],
        trivia:"یەکێک لە باشترین فیلمەکانی مێژووی ئاسیایە. Quentin Tarantino ئەم فیلمەی وەرگرتووەتە لیستی باشترین فیلمەکانی.",
        tmdb_id:670,
        trailer:"2uHx1_UZtR4",
        poster:"https://upload.wikimedia.org/wikipedia/en/6/6e/Oldboykoreanposter.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/6/6e/Oldboykoreanposter.jpg"
    },
    {
        id:10, en:"Se7en", ku:"حەفت", year:1995, rating:8.6, duration:"127 خولەک",
        genre:["thriller","crime","drama"], age:"R",
        director:"David Fincher", cast:"Brad Pitt, Morgan Freeman, Kevin Spacey",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"دوو دیتێکتیڤ، یەکی کۆن یەکی نوێ، لەدواکەوتنی کوشتارچیێکی دا کە تاوانەکانیان بەپێی حەفت گوناهی گەورەی دین دادەمەزرێنێت. کۆتایی فیلمەکە یەکێک لە ئیکۆنیکترین کۆتاییەکانی تاریخی سینەمایە.",
        awards:["Oscar: Best Film Editing (Nominated)", "BAFTA: Best Editing (Nominated)"],
        trivia:"Kevin Spacey لە کرێدیتەکانی سەرەوەی فیلمەکە دانەنراوە، چونکە نەیویستووی بازیگەران کارکترەکەیان بزانن.",
        tmdb_id:807,
        trailer:"znmZoVkCjpI",
        poster:"https://upload.wikimedia.org/wikipedia/en/6/68/Seven_%28movie%29_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/6/68/Seven_%28movie%29_poster.jpg"
    },
    {
        id:11, en:"The Usual Suspects", ku:"گومانلێکراوەکانی ئاسایی", year:1995, rating:8.5, duration:"106 خولەک",
        genre:["crime","thriller"], age:"R",
        director:"Bryan Singer", cast:"Kevin Spacey, Gabriel Byrne, Benicio del Toro",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"پێنج تاوانبار کۆ دەبنەوە و ناچارن پرۆژەیەکی مەزن ئەنجام بدەن. یەکیان زیندوو دەمێنێتەوە و باسی ئەوەی دەکات چی ڕووی داوە. کۆتایی فیلمەکە هەموو بینینەکانت لەسەرخۆ دەگۆڕێت.",
        awards:["Oscar: Best Supporting Actor - Kevin Spacey", "Oscar: Best Original Screenplay"],
        trivia:"Bryan Singer ئەم فیلمەی لە باجەتی تەنها 6 ملیۆن دۆلاری دروست کرد. Keyser Söze یەکێک لە باشترین ڤیلانەکانی مێژووی سینەمایە.",
        tmdb_id:629,
        trailer:"oiXdPolca5w",
        poster:"https://upload.wikimedia.org/wikipedia/en/6/6e/The_Usual_Suspects.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/6/6e/The_Usual_Suspects.jpg"
    },
    {
        id:12, en:"Interstellar", ku:"ئینتەرستێلار", year:2014, rating:8.6, duration:"169 خولەک",
        genre:["scifi","drama"], age:"PG-13",
        director:"Christopher Nolan", cast:"Matthew McConaughey, Anne Hathaway, Jessica Chastain",
        country:"ئەمریکا / UK", language:"ئینگلیزی",
        plot:"لە ئایندەیەکدا کە زەوی داوەژانەوەیە، گروپێک لە شوێندۆزان ڕێکەوتنی بەرامبەر کڕمچاڵێک بۆ دۆزینەوەی گەردووی نوێ دەکەن. کاتبەندی و خوێندی نیشتەجێ بوون لە گەردوو تیۆریەکانی فیزیکی ئاشکرا دەکات.",
        awards:["Oscar: Best Visual Effects", "BAFTA: Best Visual Effects", "Saturn Award: Best Science Fiction Film"],
        trivia:"Kip Thorne، فیزیکدانی قازانجکاری نۆبێل، بۆ دروستکردنی وێنەی گرانکێشی تایبەتی بۆ فیلمەکە کاری کرد.",
        tmdb_id:157336,
        trailer:"zSWdZVtXT7E",
        poster:"https://upload.wikimedia.org/wikipedia/en/b/bc/Interstellar_film_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/b/bc/Interstellar_film_poster.jpg"
    },
    {
        id:13, en:"Joker", ku:"جۆکەر", year:2019, rating:8.4, duration:"122 خولەک",
        genre:["thriller","drama","crime"], age:"R",
        director:"Todd Phillips", cast:"Joaquin Phoenix, Robert De Niro, Zazie Beetz",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"Arthur Fleck، پیاوێکی ئازاردراو و کەمەوپتکراو، بەم شێوەیە بەرەو بوونە ئەو Joker ی نامداری دەگرێت. چیرۆکی کۆمەڵایەتی و دەروونی بەرامبەر نابەرابەری.",
        awards:["Oscar: Best Actor - Joaquin Phoenix", "Oscar: Best Original Score", "Venice: Golden Lion (باشترین فیلم)"],
        trivia:"Joaquin Phoenix 52 پاوند وزەی لادا بۆ ئامادەکاری ئەم ڕۆڵە. فیلمەکە 60 ملیۆن باجەتی بوو، زیاتر لە 1 بیلیۆن بەدەست هێنا.",
        tmdb_id:475557,
        trailer:"zAGVQLHvwOY",
        poster:"https://upload.wikimedia.org/wikipedia/en/e/e1/Joker_%282019_film%29_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/e/e1/Joker_%282019_film%29_poster.jpg"
    },
    {
        id:14, en:"Prisoners", ku:"بندیەکان", year:2013, rating:8.1, duration:"153 خولەک",
        genre:["thriller","crime","drama"], age:"R",
        director:"Denis Villeneuve", cast:"Hugh Jackman, Jake Gyllenhaal, Viola Davis",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"دوو کچی بچووک ناپەیدا دەبن. باوکی یەکێکیان گومانی لەسەر پیاوێکی تایبەت هەیە، بەڵام بەبێ بەڵگە. دیتێکتیڤێک کیسەکەی پەیوەندی دەکات. باوکەکە بڕیاری خۆی دەدات.",
        awards:["Oscar: Best Cinematography (Nominated)", "Critics Choice: Best Acting Ensemble"],
        trivia:"Denis Villeneuve 153 خولەک فیلمەکەی دانا، ستودیۆ نەیویستووی لەم دووریەدا بوو بەڵام قبوڵ کرد.",
        tmdb_id:146233,
        trailer:"oWf9B4sBSYQ",
        poster:"https://upload.wikimedia.org/wikipedia/en/0/0c/Prisoners_Poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/0/0c/Prisoners_Poster.jpg"
    },
    {
        id:15, en:"The Departed", ku:"دچووەتەوە", year:2006, rating:8.5, duration:"151 خولەک",
        genre:["crime","thriller","drama"], age:"R",
        director:"Martin Scorsese", cast:"Leonardo DiCaprio, Matt Damon, Jack Nicholson",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"پۆلیسێک لە نێو کۆمەڵی جینایی دانراوە، کاتێک کۆمەڵی جینایی ئاگانامەیەکی خۆیانی لە نێو پۆلیسدا هەیە. هەر دوویان دەبێت یەکی تریان بدۆزنەوە پێش ئەوەی ئاشکرا بن.",
        awards:["Oscar: Best Picture", "Oscar: Best Director - Martin Scorsese", "Oscar: Best Editing", "Oscar: Best Adapted Screenplay"],
        trivia:"Martin Scorsese ئەم فیلمە یێکترین جار Oscar ی باشترین دەرکەوتن وەرگرت لەوەی پێشتر 3 جار نومزەتی هەبوو.",
        tmdb_id:1422,
        trailer:"iqdyRSzLKkM",
        poster:"https://upload.wikimedia.org/wikipedia/en/5/50/The_Departed_Poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/5/50/The_Departed_Poster.jpg"
    },
    {
        id:16, en:"Black Swan", ku:"قوتاببازی تاریک", year:2010, rating:8.0, duration:"108 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Darren Aronofsky", cast:"Natalie Portman, Mila Kunis, Vincent Cassel",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"ڕاقیسەیەک بۆ ڕۆڵی Swan Lake هەڵدەبژێردرێت. بەڵام بۆ بازیکردنی ئەو ڕۆڵەی باشترین ئامادەبووی، پێویستی بە گۆڕینی کەسایەتیی هەیە. خیاڵ و ڕاستی تێکەڵ دەبن.",
        awards:["Oscar: Best Actress - Natalie Portman", "BAFTA: Best Actress", "Golden Globe: Best Actress"],
        trivia:"Natalie Portman 11 مانگ ئامادەکاری کرد. Mila Kunis لە ئەم فیلمەدا ئاموزی ڕاقص کرد.",
        tmdb_id:45269,
        trailer:"9PeNHFdS0Ys",
        poster:"https://upload.wikimedia.org/wikipedia/en/d/dc/Black_Swan_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/d/dc/Black_Swan_poster.jpg"
    },
    {
        id:17, en:"Hereditary", ku:"میراتبەری", year:2018, rating:7.3, duration:"127 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Ari Aster", cast:"Toni Collette, Alex Wolff, Gabriel Byrne",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"خێزانێک لەدوای مردنی دایکبووکەی گورپانی دروست دەکەن. تراژیدیای مالباتی بەدواوە پەیدا دەبێت. ئەو نهێنییە خانەدانیە هەموو چیرۆکەکە دەگۆڕێت.",
        awards:["Sundance: Nominated for Grand Jury Prize", "Critics Choice: Best Horror Film"],
        trivia:"Ari Aster ئەم فیلمەی ویستووە وەک \"بەدترین دایکی تاریخ\" ناو ببات. Toni Collette بۆ ئەم ڕۆڵە نومزەتی Golden Globe ی هەبوو.",
        tmdb_id:493922,
        trailer:"V6wWKNij_1M",
        poster:"https://upload.wikimedia.org/wikipedia/en/8/8e/Hereditary_poster.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/8/8e/Hereditary_poster.png"
    },
    {
        id:18, en:"Mulholland Drive", ku:"مۆڵهۆلاند درایڤ", year:2001, rating:7.9, duration:"147 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"David Lynch", cast:"Naomi Watts, Laura Harring, Justin Theroux",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"ئەکتەرەیەکی تازە لە Los Angeles دەگاتە بانەیەک کە لەدایک بوونی لا بووە. هەردوویان دەستی دەکەن تا ناسنامەی خۆیانیان بدۆزنەوە. خیاڵ و ڕاستی لێک دەدرێت.",
        awards:["Cannes: Best Director - David Lynch", "BAFTA: Best Director (Nominated)"],
        trivia:"David Lynch فیلمەکە سەرەتا بۆ تەلەفزیۆن نووسی. کاتێک رەتی کرایەوە، بەرگەیەکی سینەمایی نووسی.",
        tmdb_id:1018,
        trailer:"nlPJbEp6Y2s",
        poster:"https://upload.wikimedia.org/wikipedia/en/5/50/Mulholland_Drive_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/5/50/Mulholland_Drive_poster.jpg"
    },
    {
        id:19, en:"A Beautiful Mind", ku:"ذیهنێکی ئوقلومەند", year:2001, rating:8.2, duration:"135 خولەک",
        genre:["drama"], age:"PG-13",
        director:"Ron Howard", cast:"Russell Crowe, Ed Harris, Jennifer Connelly",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"ماتماتیکزانێکی ئەقلیی بەرز کە پشووی نۆبێل وەرگرتووە، بۆ دوایین ساڵانی ژیانی دووچاری ناخۆشی شیزۆفرینیا دەبێت. ئەو تێکەڵبوونی خیاڵ و ڕاستی لەیەکتری جیا دەکاتەوە.",
        awards:["Oscar: Best Picture", "Oscar: Best Director", "Oscar: Best Adapted Screenplay", "Oscar: Best Supporting Actress"],
        trivia:"John Nash ی ڕاستەقینە لە 2015 لە تاکسییەکدا لە بێ میقنەفەدا کوژرا. فیلمەکە بەپێی ژیانی ڕاستەقینەی ئەو دروست کرا.",
        tmdb_id:453,
        trailer:"oaQ01GfFny4",
        poster:"https://upload.wikimedia.org/wikipedia/en/5/54/A_Beautiful_Mind_Poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/5/54/A_Beautiful_Mind_Poster.jpg"
    },
    {
        id:20, en:"The Truman Show", ku:"شۆوی ترومان", year:1998, rating:8.1, duration:"103 خولەک",
        genre:["drama","scifi"], age:"PG",
        director:"Peter Weir", cast:"Jim Carrey, Laura Linney, Ed Harris",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"پیاوێک هەموو ژیانی لە شۆوی تەلەفزیۆنی ژیاوە بەبێ ئەوەی بزانێت. ئەگەر ئاشکرابووی ئەوە یەکەم چیرۆکی \"ڕیالیتی شۆ\" ی تاریخی سینەمایە.",
        awards:["Golden Globe: Best Actor - Jim Carrey", "Golden Globe: Best Director", "Oscar: Best Director (Nominated)"],
        trivia:"Jim Carrey بۆ ئەم ڕۆڵە ڕا خۆی گۆراوەتەوە. فیلمەکە پێشبینی کردی ئاینده رووحی ئینستاگرام و ڕیالیتی شۆ.",
        tmdb_id:37165,
        trailer:"loTIzXAS7s4",
        poster:"https://upload.wikimedia.org/wikipedia/en/9/9d/The_Truman_Show.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/9/9d/The_Truman_Show.jpg"
    },
    {
        id:21, en:"1917", ku:"١٩١٧", year:2019, rating:8.3, duration:"119 خولەک",
        genre:["drama"], age:"R",
        director:"Sam Mendes", cast:"George MacKay, Dean-Charles Chapman, Mark Strong",
        country:"UK / ئەمریکا", language:"ئینگلیزی",
        plot:"دوو سەربازی بریتانی لە جەنگی جیهانی یەکەم ئەرکی مەترسیدارترین مێشکیان دەدرێت: گواستنەوەی ئیشارەیەک بۆ دژایەتی فریوکاری ئەڵمانی. تەنها یەک شەو هەیانە.",
        awards:["Oscar: Best Cinematography", "Oscar: Best Sound Mixing", "Oscar: Best Visual Effects", "Golden Globe: Best Drama", "Golden Globe: Best Director"],
        trivia:"فیلمەکە بەشێوەی \"یەک شۆت\" فیلمبراوە — لە ڕاستیدا 61 دوور کراوەتەوە بەیەکەوە. Roger Deakins ئیتر Oscar ی سینەماتۆگرافی وەرگرت.",
        tmdb_id:530915,
        trailer:"YqNYrYUiMfg",
        poster:"https://upload.wikimedia.org/wikipedia/en/8/8e/1917_Film_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/8/8e/1917_Film_poster.jpg"
    },
    {
        id:22, en:"The Shining", ku:"درەوشانەوە", year:1980, rating:8.4, duration:"146 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Stanley Kubrick", cast:"Jack Nicholson, Shelley Duvall, Danny Lloyd",
        country:"UK / ئەمریکا", language:"ئینگلیزی",
        plot:"نووسەرێک لەگەڵ خێزانەکەی چاودێری مێمانخانەیەکی کوێستانی زستان دەکات. تاریکی مەکانەکە لەسەری کاری دەکات. کورەکەی هەستی تایبەتی هەیە کە ئاگای لەوانە هەیە.",
        awards:["Hugo Award: Best Dramatic Presentation", "Saturn Award: Best Horror Film (Nominated)"],
        trivia:"Kubrick زیاتر لە 100 دەرفەت ئەو سەحنەی دووباره گرتەوە کە Shelley Duvall لەوانەی گرییەکی ڕاستەقینە دەکات.",
        tmdb_id:694,
        trailer:"S014oGZiSdI",
        poster:"https://upload.wikimedia.org/wikipedia/en/b/b6/The_Shining_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/b/b6/The_Shining_poster.jpg"
    },
    {
        id:23, en:"Arrival", ku:"گەیشتن", year:2016, rating:7.9, duration:"116 خولەک",
        genre:["scifi","thriller","drama"], age:"PG-13",
        director:"Denis Villeneuve", cast:"Amy Adams, Jeremy Renner, Forest Whitaker",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"12 کەشتیی بیگانە لە جیاجیاکانی زەوی دادەنرێن. ژیانگەیاندەکارێک ئەرکداری دەبێت تا زمانی بیگانەکان فێربێت. ئەو چیزەی فێری دەبێت زمانی بیگانەکان کاتی ژیانیی دەگۆڕێت.",
        awards:["Oscar: Best Sound Editing (Nominated)", "Oscar: Best Cinematography (Nominated)", "Oscar: Best Director (Nominated)"],
        trivia:"Amy Adams بۆ ئامادەکاری ئەم ڕۆڵە بە مامۆستایانی زمان کارکرد. Denis Villeneuve فیلمەکە لە ٦ ژینگەی جیاواز فیلمکرا.",
        tmdb_id:329865,
        trailer:"tFMo3UJ4B4g",
        poster:"https://upload.wikimedia.org/wikipedia/en/d/d6/Arrival_film_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/d/d6/Arrival_film_poster.jpg"
    },
    {
        id:24, en:"Eternal Sunshine of the Spotless Mind", ku:"ڕووناکی هەمیشەیی ذیهنی پاک", year:2004, rating:8.3, duration:"108 خولەک",
        genre:["drama","scifi"], age:"R",
        director:"Michel Gondry", cast:"Jim Carrey, Kate Winslet, Tom Wilkinson",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"دوو خۆشەویست بڕیاری دەدەن یادی یەکیتریان لە ذیهنیان بسڕنەوە. بەڵام لەناو ئەو پرۆسەدا دووبارە خۆشویستی دروست دەبێت. کۆتایی فیلمەکە باسی تەقدیرو ئازادی ئیرادە دەکات.",
        awards:["Oscar: Best Original Screenplay - Charlie Kaufman", "BAFTA: Best Original Screenplay"],
        trivia:"Charlie Kaufman سکریپتەکەی بەوەیی نووسی کە بۆ لایەکی لادراو شێوازی نووسینی گۆرا.",
        tmdb_id:38,
        trailer:"hvDDD2rPaFQ",
        poster:"https://upload.wikimedia.org/wikipedia/en/e/e9/Requiem_for_a_Dream_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/e/e9/Requiem_for_a_Dream_poster.jpg"
    },
    {
        id:25, en:"A Ghost Story", ku:"چیرۆکی روح", year:2017, rating:6.9, duration:"92 خولەک",
        genre:["drama","thriller"], age:"R",
        director:"David Lowery", cast:"Casey Affleck, Rooney Mara",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"لەدوای مردنی پیاوێک، روحەکەی لە ژیندا دەمێنێتەوە بۆ ئەوەی مامۆستایی خۆی بباینێت. ئەو روحە بە ملاپۆشێکی ساده نمایش دەکرێت. دەمی تیدەپەڕێت بەڵام ئاماژەکانی تێدا ماوین.",
        awards:["Sundance: Special Jury Prize (Nominated)", "Critics Choice: Most Innovative Film"],
        trivia:"David Lowery فیلمەکەی لە 19 ڕۆژدا و باجەتی 100,000 دۆلاری فیلمکرد. Casey Affleck دووساعەت ژێر ملاپۆشەکەی مایەوە.",
        tmdb_id:401981,
        trailer:"1Rcbh7-hm9c",
        trailer:"bnCsAA6FvqA",
        poster:"https://upload.wikimedia.org/wikipedia/en/a/a9/A_Ghost_Story_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/a/a9/A_Ghost_Story_poster.jpg"
    },
    {
        id:26, en:"Annihilation", ku:"لەناوبردن", year:2018, rating:6.8, duration:"115 خولەک",
        genre:["scifi","thriller"], age:"R",
        director:"Alex Garland", cast:"Natalie Portman, Jennifer Jason Leigh, Oscar Isaac",
        country:"UK / ئەمریکا", language:"ئینگلیزی",
        plot:"ژیانزانەیەک بەشداری ئەرکێک دەکات بۆ ناو \"X-Area\" — ناوچەیەکی نهێنی کە لەجیای ئەوانەی چوونن. لەوپەڕینیاندا گواستنەوەی سەرسوڕهێنەر و بیۆلۆجی نامعقول دەبینن.",
        awards:["Saturn Award: Best Science Fiction Film (Nominated)", "BAFTA: Best Special Effects (Nominated)"],
        trivia:"Alex Garland سکریپتەکەی لە ئاستێکدا نووسی کە پێشتر کتێبەکەی نەخوێندبووەوە. فیلمەکە دوو کۆتایی جیاواز داشت.",
        tmdb_id:300668,
        trailer:"89OP6Okdm08",
        poster:"https://upload.wikimedia.org/wikipedia/en/a/a1/Annihilation_%282018%29_poster.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/a/a1/Annihilation_%282018%29_poster.png"
    },
    {
        id:27, en:"Zodiac", ku:"زۆدیاک", year:2007, rating:7.7, duration:"157 خولەک",
        genre:["thriller","crime","drama"], age:"R",
        director:"David Fincher", cast:"Jake Gyllenhaal, Mark Ruffalo, Robert Downey Jr.",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"لە بنچینەی ڕاستەقینەوە — کوژرانێکی بووە کە هەرگیز نەدۆزرایەوە. کارتوونیستێک لە رۆژنامەیەک بۆ دۆزینەوەی Zodiac کوژرانەکە تەرخانی ژیانی دەکات.",
        awards:["National Society of Film Critics: Best Film (2007)", "New York Film Critics: Best Editing"],
        trivia:"David Fincher زیاتر لە 65 ساعات فیلم گرت. Jake Gyllenhaal تۆخمی خۆی گۆرا بۆ ئەو ڕۆڵە.",
        tmdb_id:10443,
        trailer:"YQESwXNL6KY",
        poster:"https://upload.wikimedia.org/wikipedia/en/8/8d/Zodiac-2007-poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/8/8d/Zodiac-2007-poster.jpg"
    },
    {
        id:28, en:"Whiplash", ku:"وویپلاش", year:2014, rating:8.5, duration:"106 خولەک",
        genre:["drama"], age:"R",
        director:"Damien Chazelle", cast:"Miles Teller, J.K. Simmons, Melissa Benoist",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"تیلمیزانی دریمزی تازەکار بە مامۆستاوێکی داواکارترین و کراودارترین ئامادەدەبێت. ئەو پەیوەندییە بناغەیەکی دوژمنایەتی و ئارزووی بەرزی هاوپێچە. \"باشترین» بە چ بهایەک دێت؟",
        awards:["Oscar: Best Supporting Actor - J.K. Simmons", "Oscar: Best Editing", "Oscar: Best Sound Mixing", "Sundance: Grand Jury Prize + Audience Award"],
        trivia:"Damien Chazelle فیلمەکەی سەرەتا وەک کورتە فیلمی دروست کرد بۆ باجەت پەیدا بکات. Miles Teller ڕاستەقینە درامز ئەدا.",
        tmdb_id:244786,
        trailer:"7d65HCMEQls",
        poster:"https://upload.wikimedia.org/wikipedia/en/6/68/Whiplash_%282014%29_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/6/68/Whiplash_%282014%29_poster.jpg"
    },
    {
        id:29, en:"La La Land", ku:"لالالاند", year:2016, rating:8.0, duration:"128 خولەک",
        genre:["drama"], age:"PG-13",
        director:"Damien Chazelle", cast:"Ryan Gosling, Emma Stone, John Legend",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"پیانیستێک و ئەکتەرەیەک لە Los Angeles خۆشویستی دەکەن. بەڵام خەونەکانیان و خۆشویستییانیان ناگون لەگەڵ یەکتر. کۆتایی فیلمەکە باسی هەڵبژاردن و پشیمانی دەکات.",
        awards:["Oscar: Best Actress - Emma Stone", "Oscar: Best Director", "Oscar: Best Cinematography", "Oscar: Best Original Score", "Golden Globe: 7 خەلاتی جیاواز"],
        trivia:"فیلمەکە لە ئەو شەوەدا Oscar ی باشترین فیلمی هەڵبژاردرا — بەڵام ئەمەیە بوو: Moonlight ی ڕاستەقینە وەریگرت.",
        tmdb_id:313369,
        trailer:"0pdqf4P9MB8",
        poster:"https://upload.wikimedia.org/wikipedia/en/a/ab/La_La_Land_%28film%29.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/a/ab/La_La_Land_%28film%29.png"
    },
    {
        id:30, en:"No Country for Old Men", ku:"وڵاتێک بۆ پیرەمێرد نییە", year:2007, rating:8.2, duration:"122 خولەک",
        genre:["crime","thriller","drama"], age:"R",
        director:"Joel & Ethan Coen", cast:"Tommy Lee Jones, Javier Bardem, Josh Brolin",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"ڕووبار پەی ئیش دوو ملیۆن دۆلاری دروکانی دروست دەکات. کوژرانێکی ئاجیزکار بەدوایدا دەکەوێت. شەریفێکی کۆن دەبینێت کە ئەو جیهانە زیاتر لەوەیە کە تێبگات.",
        awards:["Oscar: Best Picture", "Oscar: Best Director", "Oscar: Best Supporting Actor - Javier Bardem", "Oscar: Best Adapted Screenplay"],
        trivia:"Coen Brothers یەکیتیان نەبوو کە ئەم فیلمەیان دروست بکات — بەڵام قبوڵیان کرد. Anton Chigurh یەکێک لە ترسناکترین ڤیلانەکانی مێژووی سینەمایە.",
        tmdb_id:6966,
        trailer:"38A__WT3-o0",
        poster:"https://upload.wikimedia.org/wikipedia/en/4/4b/No_Country_for_Old_Men_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/4/4b/No_Country_for_Old_Men_poster.jpg"
    },
    {
        id:31, en:"Blade Runner 2049", ku:"بلەید ڕەنەر ٢٠٤٩", year:2017, rating:8.0, duration:"164 خولەک",
        genre:["scifi","thriller","drama"], age:"R",
        director:"Denis Villeneuve", cast:"Ryan Gosling, Harrison Ford, Ana de Armas",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"K، بلەید ڕەنەرێکی نوێ، نهێنییەکی دروست دەکات کە شکاندنی هەموو جیهانەکەی دەکات. ئەو نهێنییە بەرەو هەوڵی دۆزینەوەی ئیمکانی ناردوستی Rick Deckard دەچێت.",
        awards:["Oscar: Best Cinematography - Roger Deakins", "Oscar: Best Visual Effects"],
        trivia:"Roger Deakins ئەم جار Oscar ی سینەماتۆگرافی وەرگرت لەدوای 13 نومزەتییەوە.",
        tmdb_id:335984,
        trailer:"gCcx85zbxz4",
        poster:"https://upload.wikimedia.org/wikipedia/en/9/9d/Blade_Runner_2049_poster.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/9/9d/Blade_Runner_2049_poster.png"
    },
    {
        id:32, en:"Moon", ku:"مانگ", year:2009, rating:7.9, duration:"97 خولەک",
        genre:["scifi","drama"], age:"R",
        director:"Duncan Jones", cast:"Sam Rockwell, Kevin Spacey",
        country:"UK", language:"ئینگلیزی",
        plot:"کارمەندێک تەنها لەسەر مانگ ئیشدەکات. لەوەی مانگ ئەگەڕێتەوە، دۆزینەوەیەکی سەرسوڕهێنەری دەکات. ئەو دۆزینەوەیە باسی ناسنامەی مرۆڤی دەکات.",
        awards:["BAFTA: Best British Film (Nominated)", "Saturn Award: Best Science Fiction Film (Nominated)"],
        trivia:"Duncan Jones ئەم فیلمەی لە باجەتی تەنها 5 ملیۆن دۆلاری دروست کرد. Sam Rockwell تەقریبن لە هەموو سەحنەکاندا تەنهاست.",
        tmdb_id:37686,
        trailer:"oY7eFiJKJRc",
        poster:"https://upload.wikimedia.org/wikipedia/en/a/a5/Moon_2009_film.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/a/a5/Moon_2009_film.jpg"
    },
    {
        id:33, en:"Ex Machina", ku:"ئێکس ماکینا", year:2014, rating:7.7, duration:"108 خولەک",
        genre:["scifi","thriller","drama"], age:"R",
        director:"Alex Garland", cast:"Domhnall Gleeson, Alicia Vikander, Oscar Isaac",
        country:"UK", language:"ئینگلیزی",
        plot:"پرۆگرامەرێک هەڵدەبژێردرێت تا تاقیکردنەوەی ئینتەلیجەنسی دەستکردی ڕۆبۆتێک بکات. بەڵام ئەو ڕۆبۆتە زیاتر لەوەیە کە دەرکەوت.",
        awards:["Oscar: Best Visual Effects", "BAFTA: Best British Film (Nominated)"],
        trivia:"Alicia Vikander یاری Ava کرد، بەڵام CGI لەسەر جەستەکەی بوو. فیلمەکە باسی مەترسی AI دەکات لە ئایندەدا.",
        tmdb_id:264660,
        trailer:"XYGzRJ4KWEM",
        poster:"https://upload.wikimedia.org/wikipedia/en/1/1f/Ex_Machina_%28film%29_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/1/1f/Ex_Machina_%28film%29_poster.jpg"
    },
    {
        id:34, en:"The Lighthouse", ku:"مناره", year:2019, rating:7.4, duration:"109 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Robert Eggers", cast:"Willem Dafoe, Robert Pattinson",
        country:"ئەمریکا / کەنەدا", language:"ئینگلیزی",
        plot:"دوو چاودێری مناره لەسەر گیراوەیەکی کوێستانی لە قۆناغی 19 کۆ دەبنەوە. دیۆسەلانی تووڕەیی و سەرکیژی دەستپێدەکات. خیاڵ و ئیشتیهایان لەیەکتری جیا ناکەوێت.",
        awards:["Oscar: Best Cinematography (Nominated)", "BAFTA: Best British Film (Nominated)"],
        trivia:"فیلمەکە بە ئاسپێکت ڕیشیۆی 4:3 و فیلمی سپی و ڕەش فیلمکرا — وەک فیلمەکانی دەههی 1930.",
        tmdb_id:519765,
        trailer:"a9_IjB6LXQU",
        poster:"https://upload.wikimedia.org/wikipedia/en/0/05/The-lighthouse-poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/0/05/The-lighthouse-poster.jpg"
    },
    {
        id:35, en:"Midsommar", ku:"نیوەی ئەستا", year:2019, rating:7.1, duration:"148 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Ari Aster", cast:"Florence Pugh, Jack Reynor, William Jackson Harper",
        country:"ئەمریکا / سوید", language:"ئینگلیزی",
        plot:"گروپێک لە ئەمریکا بۆ جەژنی تاریکی سوید دەچن. بەڵام ئەو گوندە جیاواز دەردەکەوێت لەوەی بیری لێ دەکراوه. هەموو شتێک بەڕووناکی ڕووی دەدات — بەڵام ترسناکەکانیش لە رووناکیدان.",
        awards:["Saturn Award: Best Horror Film (Nominated)", "Sundance Special Presentation"],
        trivia:"Ari Aster وتی ئەم فیلمە باسی جیابوونەوەی خۆشویستی دەکات. Florence Pugh بۆ ئەم ڕۆڵەی بازیکردووی نومزەتی BAFTA ی هەبوو.",
        tmdb_id:530385,
        trailer:"1Bud7YH-Tc8",
        poster:"https://upload.wikimedia.org/wikipedia/en/6/65/Midsommar_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/6/65/Midsommar_poster.jpg"
    },
    {
        id:36, en:"The Others", ku:"ئەوانی تر", year:2001, rating:7.6, duration:"101 خولەک",
        genre:["thriller","drama"], age:"PG-13",
        director:"Alejandro Amenábar", cast:"Nicole Kidman, Fionnula Flanagan, Christopher Eccleston",
        country:"ئیسپانیا / ئەمریکا", language:"ئینگلیزی",
        plot:"ئافرەتێک لەگەڵ دوو منداڵی خۆی لە مالێکی تاریکدا دەژین کە رووحی تێدایە. منداڵەکان ناخۆشییەکی تایبەتیان هەیە — ڕووناکی زیان دەگەیەنێتê. کۆتایی فیلمەکە هەموو بینینەکانت دووبارە دەگۆڕێت.",
        awards:["Goya Award: Best Film", "Goya Award: Best Director", "Saturn Award: Best Horror Film"],
        trivia:"Alejandro Amenábar سکریپت، دەرکەوتن و موزیک هەموویانی خۆی ئەنجام دا.",
        tmdb_id:1428,
        trailer:"T6U4pFsEI-s",
        poster:"https://upload.wikimedia.org/wikipedia/en/3/35/The_Others_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/3/35/The_Others_poster.jpg"
    },
    {
        id:37, en:"Nightcrawler", ku:"شەوگەرد", year:2014, rating:7.9, duration:"117 خولەک",
        genre:["thriller","crime","drama"], age:"R",
        director:"Dan Gilroy", cast:"Jake Gyllenhaal, Rene Russo, Bill Paxton",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"کەسێک بە ئەتتل دۆزینەوەی جینایەت لە رووناکی شەوی LA فیلمی دەگرێت و بۆ تەلەفزیۆن دەفرۆشێت. بەتەدریج بەرەو کرداری جینایی دەڕوات بۆ ئەوەی ڤیدیۆی باشتر وەربگرێت.",
        awards:["Oscar: Best Original Screenplay (Nominated)", "BAFTA: Best Original Screenplay (Nominated)"],
        trivia:"Jake Gyllenhaal 20 پاوند لادا بۆ ئەم ڕۆڵە. وتی پیاوەکەی wەک coyote بینی — نەخۆش و خواردنخواز.",
        tmdb_id:242582,
        trailer:"X8kYDQan0dE",
        poster:"https://upload.wikimedia.org/wikipedia/en/9/95/Nightcrawler_%282014_film%29.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/9/95/Nightcrawler_%282014_film%29.png"
    },
    {
        id:38, en:"Requiem for a Dream", ku:"ئاهەنگی خەونێک", year:2000, rating:8.3, duration:"102 خولەک",
        genre:["drama","thriller"], age:"R",
        director:"Darren Aronofsky", cast:"Jared Leto, Jennifer Connelly, Ellen Burstyn",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"چوار کەس، چوار ئیدیا، یەک کۆتایی. فیلمەکە ترسناکترین وێنەی مەترسی مادەی تاریک دەکات — بەبێ هیچ ئارامشێک.",
        awards:["Oscar: Best Actress (Nominated - Ellen Burstyn)", "BAFTA: Best Actress (Nominated)"],
        trivia:"Darren Aronofsky بۆ هەندێک سەحنە تەکنیکی Hip-Hop Montage بەکارهێنا — ئەوەی ئاسایی نەبوو لەوکاتەدا.",
        tmdb_id:4517,
        trailer:"1Rcbh7-hm9c",
        poster:"https://upload.wikimedia.org/wikipedia/en/e/e9/Requiem_for_a_Dream_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/e/e9/Requiem_for_a_Dream_poster.jpg"
    },
    {
        id:39, en:"Pan's Labyrinth", ku:"ئەستوری ئەفوون", year:2006, rating:8.2, duration:"118 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Guillermo del Toro", cast:"Ivana Baquero, Sergi López, Maribel Verdú",
        country:"ئیسپانیا / مێکسیکۆ", language:"ئیسپانی",
        plot:"دوای جەنگی شاری ئیسپانیا، کچێکی بچووک لە جیهانی خەیاڵی دا مرۆڤی دارووخانەیی دەچێت و ئەرکانی وەردەگرێت. بەڵام جیهانی ڕاستی لە ئەوش ترسناکتری.",
        awards:["Oscar: Best Cinematography", "Oscar: Best Art Direction", "Oscar: Best Makeup", "BAFTA: Best Film not in English Language"],
        trivia:"Guillermo del Toro سکریپتەکەی لە 16 مانگدا نووسی. Doug Jones بازیکەری ئەو پاری سەرەکییە دووانی کرد.",
        tmdb_id:1408,
        trailer:"lG7DGMgfB9Q",
        poster:"https://upload.wikimedia.org/wikipedia/en/b/b0/PansLabyrinthPoster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/b/b0/PansLabyrinthPoster.jpg"
    },
    {
        id:40, en:"Donnie Darko", ku:"دۆنی دارکۆ", year:2001, rating:8.0, duration:"113 خولەک",
        genre:["scifi","thriller","drama"], age:"R",
        director:"Richard Kelly", cast:"Jake Gyllenhaal, Jena Malone, Drew Barrymore",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"خورتێکی ناکۆک لە 1988 ئاگاداری دەبێت کە ئەو جیهانە ٢٨ ڕۆژ و ٦ ساعات و ٤٢ خولەک دواتر لەناو دەچێت. مرۆڤێکی خرگوش شێوەی بڕیارەکانی دەگۆڕێت.",
        awards:["Sundance: Nominated for Grand Jury Prize", "Saturn Award: Best Science Fiction Film (Nominated)"],
        trivia:"فیلمەکە لەسەر پەردە شکستی هێنا بەڵام DVD ی ئەوقەدر زیاد فرۆشرا کە کەلتی دروست کرد.",
        tmdb_id:141,
        trailer:"ZZyBhhKxhZA",
        poster:"https://upload.wikimedia.org/wikipedia/en/d/d4/Donnie_Darko_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/d/d4/Donnie_Darko_poster.jpg"
    },
    {
        id:41, en:"Her", ku:"ئەو", year:2013, rating:8.0, duration:"126 خولەک",
        genre:["drama","scifi"], age:"R",
        director:"Spike Jonze", cast:"Joaquin Phoenix, Scarlett Johansson, Amy Adams",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"نووسەرێک لە ئایندەیەکی نزیکدا دلدادەی سیستەمی ئۆپەریتینگی خۆی دەبێت کە دەنگی ژنانەی هەیە. ئەو خۆشویستییە باسی تەنهایی مرۆڤی ئەمڕۆ دەکات.",
        awards:["Oscar: Best Original Screenplay - Spike Jonze", "Golden Globe: Best Screenplay", "BAFTA: Best Original Screenplay"],
        trivia:"Scarlett Johansson تەنها دەنگی ئەو یاری کرد — هەرگیز لەسەر دەریا نەبوو. Spike Jonze سکریپتەکەی لە Los Angeles نووسی.",
        tmdb_id:152601,
        trailer:"WzV6mXIOVl4",
        poster:"https://upload.wikimedia.org/wikipedia/en/4/43/Her2013Poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/4/43/Her2013Poster.jpg"
    },
    {
        id:42, en:"The Road", ku:"ڕێگا", year:2009, rating:7.3, duration:"111 خولەک",
        genre:["drama","thriller"], age:"R",
        director:"John Hillcoat", cast:"Viggo Mortensen, Kodi Smit-McPhee, Charlize Theron",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"لەدوای ئەفلاکی نادیار، باوک و کوڕی تەنها دەڕۆن بۆ باشووری کەناری بەحر. ترس و خواردن و زیندووبوونەوە — هەموو شتێک لەسەر دانراوە.",
        awards:["Saturn Award: Best Horror Film (Nominated)", "AFI: Top 10 Films of 2009"],
        trivia:"فیلمەکە لەسەر بنیادی رۆمانی Cormac McCarthy ی ساڵی 2006 کرا، کە خەڵاتی Pulitzer وەریگرت.",
        tmdb_id:13610,
        trailer:"W0-EXwmGPFc",
        poster:"https://upload.wikimedia.org/wikipedia/en/9/9e/The_Road_film_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/9/9e/The_Road_film_poster.jpg"
    },
    {
        id:43, en:"Children of Men", ku:"منداڵانی مرۆڤ", year:2006, rating:7.9, duration:"109 خولەک",
        genre:["scifi","thriller","drama"], age:"R",
        director:"Alfonso Cuarón", cast:"Clive Owen, Julianne Moore, Michael Caine",
        country:"UK / ئەمریکا", language:"ئینگلیزی",
        plot:"لە 2027، هیچ منداڵێک 18 ساڵە لادایە. ئافرەتێک بووه بە هێمنی خستن کە دووگیانە. پیاوێکی ئاسایی ئەرکی گواستنی ئەوەی وەردەگرێت.",
        awards:["Oscar: Best Cinematography (Nominated)", "Oscar: Best Editing (Nominated)", "BAFTA: Best Cinematography"],
        trivia:"ئەو سەحنەی ڕواڵەتی شەر (دووریی ستاندی) ٤ ڕۆژ بۆ فیلمکردن خایەناند. Alfonso Cuarón ئەوش لەو نووکێش کرد.",
        tmdb_id:1984,
        trailer:"ZOC-h5Lkj60",
        poster:"https://upload.wikimedia.org/wikipedia/en/d/df/Children_of_Men.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/d/df/Children_of_Men.jpg"
    },
    {
        id:44, en:"Uncut Gems", ku:"گەوهەرە بەئێسک نەکراوەکان", year:2019, rating:7.4, duration:"135 خولەک",
        genre:["thriller","crime","drama"], age:"R",
        director:"Safdie Brothers", cast:"Adam Sandler, Julia Fox, Kevin Garnett",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"فرۆشیاری گەوهەرفرۆشی نیویۆرک بەردەوام لەسەر گرتن ئەحوالی خراپ دەنرێت. نهێنییەکی ئاشکرا دەبێت لە کۆتاییدا.",
        awards:["National Society of Film Critics: Best Film", "Boston Society: Best Film"],
        trivia:"Adam Sandler وتی ئەگەر Oscar ی وەرنەگرت دەگەڕێتەوە بۆ کۆمیدی، و ئیتر \"خراپتر\" دەکات. هەموو دیسێکی KG ڕاستەقینەی Kevin Garnett بوو.",
        tmdb_id:640146,
        trailer:"xEQQkq6DixQ",
        poster:"https://upload.wikimedia.org/wikipedia/en/b/b6/Uncut_Gems_poster.jpeg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/b/b6/Uncut_Gems_poster.jpeg"
    },
    {
        id:45, en:"The Platform", ku:"پلاتفۆرم", year:2019, rating:7.0, duration:"94 خولەک",
        genre:["thriller","scifi","drama"], age:"R",
        director:"Galder Gaztelu-Urrutia", cast:"Ivan Massagué, Zorion Eguileor, Antonia San Juan",
        country:"ئیسپانیا", language:"ئیسپانی",
        plot:"زیندانێکی ستراندراو لە قووشخانە بچووکانەوە دروست کراوە. هەر ڕۆژێک خواردن لە سەرەوە دادەنرێت. کەسانی خوارەوە تەنها ئەوەی دەخوەن کە دەماوە.",
        awards:["Toronto Film Festival: People's Choice Award (Midnight Madness)"],
        trivia:"فیلمەکە کریتیکێکی زیندووی نابەرابەری کۆمەڵایەتییە. ساڵی COVID-19 باوەڕەکەی گەیشتەوە بەحەد نورمال.",
        tmdb_id:717728,
        trailer:"p_YmHBMXhiQ",
        poster:"https://upload.wikimedia.org/wikipedia/en/a/a5/The_Platform_%282019_film%29.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/a/a5/The_Platform_%282019_film%29.jpg"
    },
    {
        id:46, en:"I Saw the Devil", ku:"شەیتانی بینیم", year:2010, rating:7.8, duration:"141 خولەک",
        genre:["thriller","crime"], age:"R",
        director:"Kim Jee-woon", cast:"Lee Byung-hun, Choi Min-sik",
        country:"کۆریای باشوور", language:"کۆری",
        plot:"دیتێکتیڤێک کاکرمی خۆی دەکاتە ناو تاریکی. ئەوی کوشتاری ئەو نامزێتی کوشت هەبووانی دەگرێت — بەڵام نەیکوژێت. بەردەوام ئازاری دەدات.",
        awards:["Grand Bell Awards: Best Director", "Blue Dragon Film Awards: Best Film"],
        trivia:"فیلمەکە لە کۆریا بکراویەوە چونکە زۆر توندوتیژ بوو. تەنها لە ڤێرشنی بڕکراویدا دیارکرا.",
        tmdb_id:49491,
        trailer:"MxiEkNmQlDc",
        poster:"https://upload.wikimedia.org/wikipedia/en/5/5e/I_Saw_the_Devil.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/5/5e/I_Saw_the_Devil.jpg"
    },
    {
        id:47, en:"Burning", ku:"سووتان", year:2018, rating:7.5, duration:"148 خولەک",
        genre:["thriller","drama","crime"], age:"R",
        director:"Lee Chang-dong", cast:"Yoo Ah-in, Steven Yeun, Jeon Jong-seo",
        country:"کۆریای باشوور", language:"کۆری",
        plot:"کورتچیرۆکنووسێکی تازەکار کچێکی ناسیاری پیا دەناسێت. ئەو کچەیش خۆی بە هاوڕێیەکی تازە لا دەکاتەوە — پیاوێکی سەروەت و نهێنی. ئینجا کچەکە ناپەیدا دەبێت.",
        awards:["Cannes: FIPRESCI Prize", "Asian Film Awards: Best Director"],
        trivia:"فیلمەکە لەسەر کورتچیرۆکی Haruki Murakami کراوە. ئەو کۆتاییە نهێنییانەیەی کە بەیەکەوە دەرکەوێت.",
        tmdb_id:519771,
        trailer:"XsuhJsclRp0",
        poster:"https://upload.wikimedia.org/wikipedia/en/3/35/Burning_2018_film.png",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/3/35/Burning_2018_film.png"
    },
    {
        id:48, en:"The Wailing", ku:"هاواری", year:2016, rating:7.4, duration:"156 خولەک",
        genre:["thriller","drama"], age:"R",
        director:"Na Hong-jin", cast:"Kwak Do-won, Hwang Jung-min, Chun Woo-hee",
        country:"کۆریای باشوور", language:"کۆری",
        plot:"لە گوندێکی ئاشتییدا کوژرانی سەرسوڕهێنەر دەستپێدەکات. بیگانەیەک لەم گوندەدا دانیشتووە. شەریف کچی خۆی له بوونکراوی نهێنییەک دەبینێت.",
        awards:["Grand Bell Awards: Best Director", "Blue Dragon Film Awards: Best Film", "Cannes: Nominated"],
        trivia:"Na Hong-jin 3 ساڵ وەختی گرت بۆ لیستی فیلمەکە. فیلمەکە باسی باوەڕ و شک دەکات.",
        tmdb_id:376867,
        trailer:"8DxRNxDgBJE",
        poster:"https://upload.wikimedia.org/wikipedia/en/3/3c/The_Wailing_film.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/3/3c/The_Wailing_film.jpg"
    },
    {
        id:49, en:"Coherence", ku:"کۆهیرینس", year:2013, rating:7.2, duration:"89 خولەک",
        genre:["scifi","thriller"], age:"R",
        director:"James Ward Byrkit", cast:"Emily Baldoni, Maury Sterling, Nicholas Brendon",
        country:"ئەمریکا", language:"ئینگلیزی",
        plot:"هەشت دۆست لە شەوی تێپەڕبوونی ستێرەیەکدا کۆدەبنەوە. رووناکی دەچێت. جیهانی پاراڵێل دەستپێدەکات. کێ کۆپییە؟ کێ ئەسڵییە؟",
        awards:["Tribeca Film Festival: Audience Award (Nominated)"],
        trivia:"فیلمەکە بەبێ سکریپت فیلمکرا — بازیگەران تەنها پەرتووکی زانیاریان هەبوو. هەموو سەحنەکان ئیمپرۆڤایز بوون.",
        tmdb_id:220289,
        trailer:"iz9PX2-O3q0",
        poster:"https://upload.wikimedia.org/wikipedia/en/5/58/Coherence_2013_film_poster.jpg",
        backdrop:"https://upload.wikimedia.org/wikipedia/en/5/58/Coherence_2013_film_poster.jpg"
    }
];

// ===== STATE =====
let favs = JSON.parse(localStorage.getItem('sarwashtFavs') || '[]');
let comments = JSON.parse(localStorage.getItem('sarwashtComments') || '[]');
let currentPage = 1;
const perPage = 15;
let activeTab = 'all';
let searchQ = '';

// ===== HERO SETUP =====
(function setupHero() {
    const featured = MOVIES[4]; // Inception as featured
    const stripMovies = [MOVIES[0], MOVIES[3], MOVIES[13], MOVIES[15]]; // Fight Club, Parasite, Joker, Departed

    // backdrop
    const backdrop = document.getElementById('heroBackdrop');
    if (backdrop) backdrop.style.backgroundImage = `url('${featured.backdrop}')`;

    // poster
    const posterImg = document.getElementById('heroPosterImg');
    if (posterImg) {
        posterImg.src = featured.poster;
        posterImg.alt = featured.en;
        document.getElementById('heroPosterWrap').addEventListener('click', () => openModal(featured.id));
        document.getElementById('heroPosterWrap').style.cursor = 'pointer';
    }

    // featured film info block
    const info = document.getElementById('heroFilmInfo');
    if (info) {
        info.innerHTML = `
            <div class="hero-film-label">⬤ فیلمی هەفتە</div>
            <div class="hero-film-title-big">${featured.en}</div>
            <div class="hero-film-tags">
                <span class="hero-film-tag red">⭐ ${featured.rating}/10</span>
                <span class="hero-film-tag">${featured.year}</span>
                <span class="hero-film-tag">${featured.duration}</span>
                <span class="hero-film-tag">${featured.age}</span>
            </div>
            <button class="hero-cta" onclick="openModal(${featured.id})">
                <i class="fas fa-info-circle"></i> زانیاری تەواو
            </button>
        `;
    }

    // bottom strip
    const row = document.getElementById('heroFilmRow');
    if (row) {
        stripMovies.forEach((m, i) => {
            if (i > 0) {
                const divider = document.createElement('div');
                divider.className = 'hero-film-card-divider';
                row.appendChild(divider);
            }
            const card = document.createElement('div');
            card.className = 'hero-film-card';
            card.innerHTML = `
                <div class="hero-film-card-bg" style="background-image:url('${m.backdrop}')"></div>
                <div class="hero-film-card-info">
                    <div class="hero-film-card-title">${m.en}</div>
                    <div class="hero-film-card-meta">
                        <span class="hero-film-card-rating">⭐ ${m.rating}</span>
                        <span>${m.year}</span>
                        <span>${m.age}</span>
                    </div>
                </div>
            `;
            card.addEventListener('click', () => openModal(m.id));
            row.appendChild(card);
        });
    }
})();

// ===== FILTER =====
function filtered() {
    let list = [...MOVIES];
    if (activeTab === 'thriller') list = list.filter(m => m.genre.includes('thriller'));
    else if (activeTab === 'drama') list = list.filter(m => m.genre.includes('drama'));
    else if (activeTab === 'scifi') list = list.filter(m => m.genre.includes('scifi'));
    else if (activeTab === 'crime') list = list.filter(m => m.genre.includes('crime'));
    else if (activeTab === 'top9') list = list.filter(m => m.rating >= 8.0);
    if (searchQ) list = list.filter(m =>
        m.ku.includes(searchQ) || m.en.toLowerCase().includes(searchQ.toLowerCase())
    );
    return list;
}

// ===== RENDER MOVIES =====
function renderMovies(reset = false) {
    const grid = document.getElementById('movieGrid');
    if (reset) { grid.innerHTML = ''; currentPage = 1; }
    const list = filtered();
    const start = (currentPage - 1) * perPage;
    const end = start + perPage;
    const show = list.slice(start, end);

    document.getElementById('movieCount').textContent = `(${list.length})`;
    document.getElementById('noRes').style.display = list.length === 0 ? 'block' : 'none';

    show.forEach((m, idx) => {
        const isFav = favs.includes(m.id);
        const card = document.createElement('div');
        card.className = 'movie-card';
        card.style.animationDelay = `${idx * 0.04}s`;
        const posterUrl = m.poster;
        const fallbackUrl = `https://placehold.co/300x420/1a1a1a/e50914?text=${encodeURIComponent(m.en.substring(0,15))}`;
        card.innerHTML = `
            <img class="card-poster" src="${posterUrl}" alt="${m.ku}" loading="lazy"
                onerror="this.onerror=null;this.src='${fallbackUrl}'">
            <div class="card-overlay">
                <div class="overlay-play"><i class="fas fa-info-circle"></i></div>
                <div class="overlay-year">${m.year} · ${m.duration}</div>
            </div>
            <button class="fav-btn ${isFav ? 'on' : ''}" data-id="${m.id}"><i class="${isFav ? 'fas' : 'far'} fa-heart"></i></button>
            <span class="age-tag">${m.age}</span>
            <div class="card-info">
                <div class="card-title">${m.ku}</div>
                <div class="card-meta">
                    <span class="card-rating">⭐ ${m.rating}</span>
                    <span>${m.year}</span>
                </div>
            </div>
        `;
        card.querySelector('.fav-btn').addEventListener('click', e => { e.stopPropagation(); toggleFav(m.id); });
        card.addEventListener('click', () => openModal(m.id));
        grid.appendChild(card);
    });

    document.getElementById('loadMore').style.display = end < list.length ? 'block' : 'none';
}

// ===== FAVORITES =====
function toggleFav(id) {
    const i = favs.indexOf(id);
    if (i === -1) favs.push(id); else favs.splice(i, 1);
    localStorage.setItem('sarwashtFavs', JSON.stringify(favs));
    renderFavs();
    document.querySelectorAll(`.fav-btn[data-id="${id}"]`).forEach(b => {
        const on = favs.includes(id);
        b.classList.toggle('on', on);
        b.querySelector('i').className = on ? 'fas fa-heart' : 'far fa-heart';
    });
}

function renderFavs() {
    const row = document.getElementById('favRow');
    const empty = document.getElementById('favEmpty');
    document.getElementById('favCount').textContent = `(${favs.length})`;
    if (!favs.length) { row.style.display = 'none'; empty.style.display = 'block'; return; }
    empty.style.display = 'none'; row.style.display = 'flex'; row.innerHTML = '';
    favs.forEach(id => {
        const m = MOVIES.find(x => x.id === id); if (!m) return;
        const c = document.createElement('div');
        c.className = 'fav-mini';
        c.innerHTML = `
            <img class="fav-mini-img" src="${m.poster}" alt="${m.ku}" loading="lazy" onerror="this.onerror=null;this.src='https://placehold.co/140x190/1a1a1a/e50914?text=${encodeURIComponent(m.en.substring(0,10))}'">
            <button class="fav-mini-remove" data-id="${m.id}"><i class="fas fa-times"></i></button>
            <div class="fav-mini-title">${m.ku}</div>
        `;
        c.querySelector('.fav-mini-remove').addEventListener('click', e => { e.stopPropagation(); toggleFav(m.id); });
        c.addEventListener('click', () => openModal(m.id));
        row.appendChild(c);
    });
}

// ===== MODAL =====
function openModal(id) {
    const m = MOVIES.find(x => x.id === id);
    if (!m) return;
    const isFav = favs.includes(m.id);
    const genres = m.genre.map(g => `<span class="modal-tag">${g.toUpperCase()}</span>`).join('');
    const awards = m.awards.map(a => `<div class="award-chip">🏆 ${a}</div>`).join('');
    document.getElementById('modalBox').innerHTML = `
        <div class="modal-hero" style="background-image:url('${m.poster}')">
            <div class="modal-hero-grad"></div>
            <button class="modal-close" onclick="closeModal()"><i class="fas fa-times"></i></button>
            <div class="modal-hero-title">
                <h2>${m.ku}</h2>
                <div class="en-title">${m.en}</div>
            </div>
        </div>
        <div class="modal-body">
            <div class="modal-tags">
                ${genres}
                <span class="modal-tag gold">⭐ ${m.rating}/10</span>
                <span class="modal-tag blue">${m.age}</span>
                <span class="modal-tag">${m.year}</span>
                <span class="modal-tag">${m.duration}</span>
            </div>
            <button class="modal-fav-btn ${isFav ? 'on' : ''}" id="modalFavBtn" onclick="toggleFav(${m.id}); this.classList.toggle('on')">
                <i class="${isFav ? 'fas' : 'far'} fa-heart"></i> ${isFav ? 'لە دلخوازەکانم' : 'زیادکردن بۆ دلخواز'}
            </button>
            ${m.trailer ? `
            <button class="trailer-btn" onclick="toggleTrailer('${m.trailer}', this)">
                <span class="play-icon">▶</span>
                <span id="trailerBtnText">تریلەری فیلم ببینە</span>
            </button>
            <div class="trailer-player" id="trailerPlayer"></div>
            ` : ''}
            <div class="modal-stats">
                <div class="stat-box"><div class="stat-label">دەرکەوتن</div><div class="stat-val">${m.director}</div></div>
                <div class="stat-box"><div class="stat-label">وڵات</div><div class="stat-val">${m.country}</div></div>
                <div class="stat-box"><div class="stat-label">زمان</div><div class="stat-val">${m.language}</div></div>
                <div class="stat-box"><div class="stat-label">ڕیتینگ IMDB</div><div class="stat-val gold">⭐ ${m.rating}</div></div>
            </div>
            <div class="modal-section">
                <h4><i class="fas fa-film"></i> باسی فیلم</h4>
                <p>${m.plot}</p>
            </div>
            <div class="modal-section">
                <h4><i class="fas fa-users"></i> بازیگەران</h4>
                <p>${m.cast}</p>
            </div>
            <div class="modal-section">
                <h4><i class="fas fa-trophy"></i> خەڵاتەکان</h4>
                <div class="awards-list">${awards}</div>
            </div>
            <div class="modal-section">
                <h4><i class="fas fa-lightbulb"></i> زانیاری سەرسوڕهێنەر</h4>
                <p>${m.trivia}</p>
            </div>
        </div>
    `;
    document.getElementById('modalWrap').classList.add('open');
    document.body.style.overflow = 'hidden';
}

function toggleTrailer(ytId, btn) {
    const player = document.getElementById('trailerPlayer');
    const btnText = document.getElementById('trailerBtnText');
    if (!player) return;
    if (player.classList.contains('open')) {
        player.classList.remove('open');
        player.innerHTML = '';
        btnText.textContent = 'تریلەری فیلم ببینە';
        btn.style.background = 'linear-gradient(135deg, #e50914, #b0060f)';
    } else {
        player.classList.add('open');
        player.innerHTML = `<iframe src="https://www.youtube.com/embed/${ytId}?autoplay=1&rel=0" allowfullscreen allow="autoplay; encrypted-media"></iframe>`;
        btnText.textContent = 'داخستنی تریلەر';
        btn.style.background = 'linear-gradient(135deg, #444, #222)';
        player.scrollIntoView({ behavior: 'smooth', block: 'center' });
    }
}

function closeModal() {
    // stop trailer iframe on close
    const player = document.getElementById('trailerPlayer');
    if (player) player.innerHTML = '';
    document.getElementById('modalWrap').classList.remove('open');
    document.body.style.overflow = '';
}

// ===== COMMENTS =====
function renderComments() {
    const list = document.getElementById('commentsList');
    document.getElementById('commentCount').textContent = `(${comments.length})`;
    list.innerHTML = '';
    [...comments].reverse().forEach((c, idx) => {
        const div = document.createElement('div');
        div.className = 'comment-item';
        div.innerHTML = `
            <div class="c-avatar">${c.name.charAt(0).toUpperCase()}</div>
            <div class="c-body">
                <div class="c-author">${c.name} ${c.movie ? `· <span class="c-movie-ref">${c.movie}</span>` : ''}</div>
                <div class="c-text">${c.text}</div>
                <div class="c-bottom">
                    <div class="c-time">${c.time}</div>
                    <button class="c-like ${c.liked ? 'liked' : ''}" data-idx="${comments.length - 1 - idx}">
                        <i class="${c.liked ? 'fas' : 'far'} fa-heart"></i> ${c.likes || 0}
                    </button>
                </div>
            </div>
        `;
        div.querySelector('.c-like').addEventListener('click', function() {
            const i = parseInt(this.dataset.idx);
            comments[i].liked = !comments[i].liked;
            comments[i].likes = (comments[i].likes || 0) + (comments[i].liked ? 1 : -1);
            localStorage.setItem('sarwashtComments', JSON.stringify(comments));
            renderComments();
        });
        list.appendChild(div);
    });
}

function addComment() {
    const name = document.getElementById('cName').value.trim();
    const text = document.getElementById('cText').value.trim();
    const movie = document.getElementById('cMovie').value.trim();
    if (!name || !text) return;
    const now = new Date();
    comments.push({ name, text, movie, likes: 0, liked: false, time: now.toLocaleDateString('ku') + ' · ' + now.toLocaleTimeString('ku', {hour:'2-digit', minute:'2-digit'}) });
    localStorage.setItem('sarwashtComments', JSON.stringify(comments));
    document.getElementById('cName').value = '';
    document.getElementById('cText').value = '';
    document.getElementById('cMovie').value = '';
    renderComments();
}

// ===== TABS =====
document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.addEventListener('click', function() {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        activeTab = this.dataset.tab;
        renderMovies(true);
    });
});

// ===== SEARCH =====
function doSearch() {
    searchQ = document.getElementById('searchInput').value.trim();
    renderMovies(true);
}
document.getElementById('searchInput').addEventListener('keydown', e => { if (e.key === 'Enter') doSearch(); });
document.getElementById('searchInput').addEventListener('input', function() { if (!this.value) { searchQ = ''; renderMovies(true); } });
document.querySelector('.search-btn').addEventListener('click', doSearch);

// ===== LOAD MORE =====
document.getElementById('loadMore').addEventListener('click', () => { currentPage++; renderMovies(); });

// ===== MODE =====
const modeBtn = document.getElementById('modeBtn');
if (localStorage.getItem('sarwashtMode') === 'light') {
    document.body.classList.add('light');
    modeBtn.querySelector('i').className = 'fas fa-sun';
    modeBtn.querySelector('span').textContent = 'ڕۆژ';
}
modeBtn.addEventListener('click', () => {
    document.body.classList.toggle('light');
    const isL = document.body.classList.contains('light');
    modeBtn.querySelector('i').className = isL ? 'fas fa-sun' : 'fas fa-moon';
    modeBtn.querySelector('span').textContent = isL ? 'ڕۆژ' : 'شەو';
    localStorage.setItem('sarwashtMode', isL ? 'light' : 'dark');
});

// ===== NAVBAR + SCROLL =====
window.addEventListener('scroll', () => {
    document.getElementById('navbar').classList.toggle('scrolled', scrollY > 50);
    document.getElementById('scrollTop').classList.toggle('show', scrollY > 400);
});

// ===== KEYBOARD =====
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModal(); });

// ===== INIT =====
renderMovies();
renderFavs();
renderComments();
</script>
</body>
</html>
