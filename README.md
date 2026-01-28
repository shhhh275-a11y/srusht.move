<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب - فیلمەکان کۆتاییەکی سەرسوڕهێنەریان هەیە">
    <meta name="keywords" content="فیلم, سینەما, کوردی, کۆتایی سەرسوڕهێنەر, فیلمی نایاب">
    <meta name="author" content="srusht.movies">
    <title>Shocking Ending Movies - سایتی فیلمی کوردی</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #c77b63;
            --secondary: #1a1a2e;
            --accent: #f5c518;
            --text: #ffffff;
            --card-bg: rgba(255, 255, 255, 0.08);
            --shadow: rgba(0, 0, 0, 0.4);
            /* گۆڕاوە نوێیەکان بۆ مۆدی ڕەنگ */
            --header-bg: rgba(255, 255, 255, 0.05); /* پاشبنەمای سەرەکی سەرەوە */
        }

        body {
            font-family: 'Segoe UI', 'Tahoma', 'Geneva', 'Verdana', sans-serif;
            min-height: 100vh;
            background: var(--secondary);
            color: var(--text);
            overflow-x: hidden;
            position: relative;
            transition: background-color 0.5s ease;
        }

        /* مۆدی ڕۆژ (Day Mode) */
        body.day-mode {
            --secondary: #f0f2f5;
            --text: #1a1a2e;
            --card-bg: rgba(26, 26, 46, 0.08);
            --header-bg: rgba(26, 26, 46, 0.05);
            --shadow: rgba(0, 0, 0, 0.1);
        }

        body.day-mode .background-overlay {
            opacity: 0.05;
        }

        body.day-mode .brand-name {
            background: linear-gradient(45deg, #1a1a2e, #2d2d5a, #4a4a7a);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .background-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(135deg, rgba(0,0,0,0.9) 0%, rgba(26,26,46,0.95) 100%),
                url('https://images.unsplash.com/photo-1489599809505-7c8e1a48bcc0?ixlib=rb-4.0.3&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
            opacity: 0.15;
            z-index: -2;
            transition: opacity 0.5s ease;
        }

        .gradient-circle {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 600px;
            height: 600px;
            border-radius: 50%;
            background: radial-gradient(circle, var(--primary) 0%, #8b5a4a 50%, transparent 70%);
            opacity: 0.1;
            filter: blur(60px);
            z-index: -1;
            animation: float 25s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(-50%, -50%) scale(1) rotate(0deg); }
            33% { transform: translate(-48%, -52%) scale(1.05) rotate(120deg); }
            66% { transform: translate(-52%, -48%) scale(1.1) rotate(240deg); }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        /* Header Styles - ئێستا گۆڕاوێکی CSS بەکاردهێنێت */
        .header {
            text-align: center;
            margin-bottom: 50px;
            padding: 30px 0;
        }

        .site-title {
            font-size: 1.8em;
            font-weight: 700;
            margin-bottom: 20px;
            padding: 20px 50px;
            border: 2px solid rgba(255,255,255,0.3);
            border-radius: 60px;
            display: inline-block;
            background: var(--header-bg); /* گۆڕاو بەکارهاتووە */
            backdrop-filter: blur(10px);
            animation: fadeInDown 1s ease;
            box-shadow: 0 8px 25px var(--shadow);
            transition: all 0.5s ease;
        }
        body.day-mode .site-title {
            border: 2px solid rgba(26, 26, 46, 0.3);
        }

        .brand-name {
            font-size: 3.5em;
            font-weight: 900;
            text-shadow: 3px 3px 0px rgba(0,0,0,0.4), 0 0 30px rgba(255,255,255,0.3);
            background: linear-gradient(45deg, #ffffff, #e0e0e0, #a8a8a8);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            animation: fadeIn 1.5s ease;
            letter-spacing: 3px;
        }

        /* بەشی شێوەگۆڕی (Mode Switcher) */
        .mode-switcher-container {
            text-align: center;
            margin: 15px auto 40px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .mode-label {
            font-weight: 600;
            color: rgba(255, 255, 255, 0.9);
            font-size: 1em;
        }
        body.day-mode .mode-label {
            color: rgba(26, 26, 46, 0.9);
        }

        .mode-switcher {
            position: relative;
            display: inline-block;
            width: 80px;
            height: 34px;
        }

        .mode-switcher input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .mode-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, #3498db, #833ab4);
            transition: .4s;
            border-radius: 34px;
            display: flex;
            align-items: center;
            padding: 0 6px;
            box-shadow: inset 0 2px 5px rgba(0,0,0,0.2);
        }

        .mode-slider:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
            z-index: 2;
        }

        .mode-icon {
            font-size: 0.9em;
            z-index: 1;
            transition: opacity 0.3s;
            color: white;
        }

        #moon-icon {
            margin-right: auto;
            opacity: 1;
        }

        #sun-icon {
            margin-left: auto;
            opacity: 0.7;
        }

        input:checked + .mode-slider {
            background: linear-gradient(90deg, #fd1d1d, #fcb045);
        }

        input:checked + .mode-slider:before {
            transform: translateX(46px);
        }

        input:checked + .mode-slider #moon-icon {
            opacity: 0.7;
        }

        input:checked + .mode-slider #sun-icon {
            opacity: 1;
        }

        /* Search Section */
        .search-section {
            max-width: 600px;
            margin: 0 auto 40px;
            padding: 0 20px;
        }

        .search-box {
            display: flex;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 50px;
            padding: 5px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 25px var(--shadow);
            transition: all 0.3s ease;
        }
        body.day-mode .search-box {
            background: rgba(26, 26, 46, 0.1);
            border: 1px solid rgba(26, 26, 46, 0.2);
        }

        .search-box:focus-within {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
        }

        .search-input {
            flex: 1;
            background: transparent;
            border: none;
            padding: 18px 25px;
            color: var(--text);
            font-size: 1.1em;
            outline: none;
            font-family: inherit;
        }

        .search-input::placeholder {
            color: rgba(255,255,255,0.6);
        }
        body.day-mode .search-input::placeholder {
            color: rgba(26, 26, 46, 0.6);
        }

        .search-button {
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            border: none;
            border-radius: 50px;
            padding: 18px 35px;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
            font-size: 1em;
        }

        .search-button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(253,29,29,0.5);
        }

        /* بەشی ئینستاگرام - نوێکراوە */
        .social-section {
            text-align: center;
            margin: 30px auto 50px; /* کەمکرایەوە بۆ نزیککردنەوە لە سەرەوە */
            padding: 0 15px;
        }

        .social-title {
            font-size: 1.5em;
            margin-bottom: 25px;
            color: rgba(255,255,255,0.9);
            font-weight: 600;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
        }
        body.day-mode .social-title {
            color: rgba(26, 26, 46, 0.9);
            text-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .social-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            max-width: 700px; /* کەمکرایەوە بۆ بچووکتربوون */
            margin: 0 auto;
        }

        .social-card {
            background: var(--card-bg);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            padding: 20px; /* کەمکرایەوە */
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3); /* کەمکرایەوە */
            transition: all 0.4s ease;
            min-width: 240px; /* کەمکرایەوە */
            flex: 1;
            max-width: 300px; /* سنووردارکراو */
        }
        body.day-mode .social-card {
            border: 1px solid rgba(26, 26, 46, 0.15);
        }

        .social-card:hover {
            transform: translateY(-8px);
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.25);
            box-shadow: 0 12px 35px rgba(0,0,0,0.5);
        }
        body.day-mode .social-card:hover {
            background: rgba(26, 26, 46, 0.12);
            border: 1px solid rgba(26, 26, 46, 0.25);
        }

        .social-card a {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: white;
            gap: 12px; /* کەمکرایەوە */
        }
        body.day-mode .social-card a {
            color: var(--text);
        }

        .social-icon {
            font-size: 2.2em; /* کەمکرایەوە */
            background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .social-name {
            font-size: 1.2em; /* کەمکرایەوە */
            font-weight: 700;
            color: var(--text);
            text-align: center;
        }

        .social-username {
            font-size: 0.95em; /* کەمکرایەوە */
            color: rgba(255,255,255,0.7);
            text-align: center;
            direction: ltr;
        }
        body.day-mode .social-username {
            color: rgba(26, 26, 46, 0.7);
        }

        .social-follow {
            background: linear-gradient(45deg, #833ab4, #fd1d1d);
            padding: 9px 22px; /* کەمکرایەوە */
            border-radius: 50px;
            font-weight: 600;
            margin-top: 8px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(253,29,29,0.4); /* کەمکرایەوە */
            font-size: 0.95em;
        }

        .social-card:hover .social-follow {
            transform: scale(1.05);
            box-shadow: 0 6px 20px rgba(253,29,29,0.6); /* کەمکرایەوە */
        }

        /* Movie Grid */
        .movie-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 35px;
            padding: 30px 0;
        }

        .movie-card {
            background: var(--card-bg);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            overflow: hidden;
            box-shadow: 0 12px 40px var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.12);
            transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
            cursor: pointer;
            position: relative;
            animation: fadeInUp 0.7s ease backwards;
        }
        body.day-mode .movie-card {
            border: 1px solid rgba(26, 26, 46, 0.12);
        }

        .movie-card:hover {
            transform: translateY(-15px) scale(1.03);
            box-shadow: 0 25px 70px rgba(0,0,0,0.6);
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.25);
        }
        body.day-mode .movie-card:hover {
            background: rgba(26, 26, 46, 0.12);
            border: 1px solid rgba(26, 26, 46, 0.25);
        }

        .movie-rank {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0,0,0,0.9);
            color: var(--accent);
            width: 55px;
            height: 55px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.5em;
            border: 3px solid var(--accent);
            box-shadow: 0 5px 25px rgba(245, 197, 24, 0.6);
            z-index: 10;
            animation: pulse 2.5s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        .movie-poster {
            width: 100%;
            height: 420px;
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            position: relative;
            overflow: hidden;
        }

        .movie-poster::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 60%;
            background: linear-gradient(to top, rgba(0,0,0,0.8) 0%, transparent 100%);
        }

        .movie-poster::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.08) 50%, transparent 70%);
            transform: rotate(45deg);
            animation: shine 4s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .movie-info {
            padding: 28px;
            background: rgba(0, 0, 0, 0.4);
        }
        body.day-mode .movie-info {
            background: rgba(255, 255, 255, 0.4);
        }

        .movie-title {
            font-size: 1.6em;
            font-weight: 700;
            margin-bottom: 12px;
            color: var(--text);
            text-shadow: 2px 2px 6px rgba(0,0,0,0.5);
            line-height: 1.3;
        }

        .movie-year {
            color: rgba(255, 255, 255, 0.85);
            font-size: 1em;
            margin-bottom: 14px;
            font-weight: 500;
        }
        body.day-mode .movie-year {
            color: rgba(26, 26, 46, 0.85);
        }

        .movie-plot {
            color: rgba(255, 255, 255, 0.9);
            font-size: 0.95em;
            line-height: 1.7;
            margin-bottom: 18px;
            text-align: justify;
            height: 85px;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
        }
        body.day-mode .movie-plot {
            color: rgba(26, 26, 46, 0.9);
        }

        .movie-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .imdb-rating {
            background: linear-gradient(135deg, #f5c518 0%, #d4af37 100%);
            color: #000;
            padding: 10px 20px;
            border-radius: 15px;
            font-weight: 700;
            font-size: 1.15em;
            box-shadow: 0 5px 20px rgba(245, 197, 24, 0.4);
            transition: all 0.3s ease;
        }

        .movie-card:hover .imdb-rating {
            transform: scale(1.08);
            box-shadow: 0 7px 25px rgba(245, 197, 24, 0.6);
        }

        .age-rating {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            color: white;
            padding: 10px 20px;
            border-radius: 15px;
            font-weight: 700;
            box-shadow: 0 5px 20px rgba(231, 76, 60, 0.4);
            transition: all 0.3s ease;
        }

        .age-rating.pg13 {
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            box-shadow: 0 5px 20px rgba(52, 152, 219, 0.4);
        }

        .age-rating.g {
            background: linear-gradient(135deg, #2ecc71 0%, #27ae60 100%);
            box-shadow: 0 5px 20px rgba(46, 204, 113, 0.4);
        }

        .movie-card:hover .age-rating {
            transform: scale(1.08);
        }

        /* Owner Section */
        .owner-box {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            padding: 35px;
            margin: 40px auto;
            max-width: 500px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 12px 35px rgba(0,0,0,0.4);
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        body.day-mode .owner-box {
            background: rgba(26, 26, 46, 0.1);
            border: 1px solid rgba(26, 26, 46, 0.2);
        }

        .owner-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, #f5c518, #e74c3c, #3498db, #833ab4);
        }

        .owner-title {
            font-size: 1.2em;
            color: rgba(255,255,255,0.85);
            margin-bottom: 10px;
            font-weight: 600;
        }
        body.day-mode .owner-title {
            color: rgba(26, 26, 46, 0.85);
        }

        .owner-name {
            font-size: 2.2em;
            color: var(--accent);
            font-weight: 800;
            margin-bottom: 15px;
            text-shadow: 0 0 20px rgba(245, 197, 24, 0.8);
            letter-spacing: 1px;
        }

        .owner-subtitle {
            font-size: 1.05em;
            color: rgba(255,255,255,0.75);
            font-style: italic;
        }
        body.day-mode .owner-subtitle {
            color: rgba(26, 26, 46, 0.75);
        }

        /* Footer */
        .footer {
            text-align: center;
            margin-top: 60px;
            padding: 30px;
            color: rgba(255,255,255,0.7);
            font-size: 0.95em;
            border-top: 1px solid rgba(255,255,255,0.15);
            background: rgba(0,0,0,0.2);
            border-radius: 20px 20px 0 0;
        }
        body.day-mode .footer {
            color: rgba(26, 26, 46, 0.7);
            border-top: 1px solid rgba(26, 26, 46, 0.15);
            background: rgba(240, 242, 245, 0.5);
        }

        /* Animations */
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Staggered animation for movie cards */
        .movie-card:nth-child(1) { animation-delay: 0.1s; }
        .movie-card:nth-child(2) { animation-delay: 0.15s; }
        .movie-card:nth-child(3) { animation-delay: 0.2s; }
        .movie-card:nth-child(4) { animation-delay: 0.25s; }
        .movie-card:nth-child(5) { animation-delay: 0.3s; }
        .movie-card:nth-child(6) { animation-delay: 0.35s; }
        .movie-card:nth-child(7) { animation-delay: 0.4s; }
        .movie-card:nth-child(8) { animation-delay: 0.45s; }
        .movie-card:nth-child(9) { animation-delay: 0.5s; }
        .movie-card:nth-child(10) { animation-delay: 0.55s; }
        .movie-card:nth-child(11) { animation-delay: 0.6s; }
        .movie-card:nth-child(12) { animation-delay: 0.65s; }
        .movie-card:nth-child(13) { animation-delay: 0.7s; }
        .movie-card:nth-child(14) { animation-delay: 0.75s; }
        .movie-card:nth-child(15) { animation-delay: 0.8s; }
        .movie-card:nth-child(16) { animation-delay: 0.85s; }
        .movie-card:nth-child(17) { animation-delay: 0.9s; }
        .movie-card:nth-child(18) { animation-delay: 0.95s; }
        .movie-card:nth-child(19) { animation-delay: 1.0s; }
        .movie-card:nth-child(20) { animation-delay: 1.05s; }
        .movie-card:nth-child(21) { animation-delay: 1.1s; }
        .movie-card:nth-child(22) { animation-delay: 1.15s; }

        /* Responsive Design */
        @media (max-width: 1200px) {
            .container {
                padding: 15px;
            }
            .movie-grid {
                grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
                gap: 25px;
            }
        }

        @media (max-width: 768px) {
            .brand-name {
                font-size: 2.5em;
            }
            .site-title {
                font-size: 1.4em;
                padding: 16px 30px;
            }
            .movie-grid {
                grid-template-columns: 1fr;
                gap: 25px;
            }
            .gradient-circle {
                width: 400px;
                height: 400px;
            }
            .movie-poster {
                height: 380px;
            }
            .search-section {
                padding: 0 15px;
            }
            .search-input {
                padding: 15px 20px;
            }
            .search-button {
                padding: 15px 25px;
            }
            .social-container {
                flex-direction: column;
                align-items: center;
                gap: 15px;
            }
            .social-card {
                width: 100%;
                max-width: 400px;
                min-width: auto;
            }
            .mode-switcher-container {
                flex-direction: column;
                gap: 10px;
            }
        }

        @media (max-width: 480px) {
            .brand-name {
                font-size: 2em;
            }
            .site-title {
                font-size: 1.1em;
                padding: 12px 20px;
            }
            .movie-title {
                font-size: 1.4em;
            }
            .owner-name {
                font-size: 1.8em;
            }
            .social-title {
                font-size: 1.3em;
            }
            .social-card {
                padding: 18px;
                min-width: auto;
            }
        }

        /* Utility Classes */
        .no-results {
            text-align: center;
            padding: 50px;
            font-size: 1.3em;
            color: rgba(255,255,255,0.7);
            grid-column: 1 / -1;
            display: none;
        }
        body.day-mode .no-results {
            color: rgba(26, 26, 46, 0.7);
        }

        .pagination {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 40px 0;
            flex-wrap: wrap;
        }

        .page-btn {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            padding: 12px 20px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        body.day-mode .page-btn {
            background: rgba(26, 26, 46, 0.1);
            border: 1px solid rgba(26, 26, 46, 0.2);
            color: var(--text);
        }

        .page-btn:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-3px);
        }
        body.day-mode .page-btn:hover {
            background: rgba(26, 26, 46, 0.2);
        }

        .page-btn.active {
            background: linear-gradient(45deg, #833ab4, #fd1d1d);
            font-weight: bold;
        }

        /* Style for Auto-mode status */
        .auto-status {
            font-size: 0.85em;
            color: var(--accent);
            font-weight: 600;
            margin-top: 5px;
            text-align: center;
            min-height: 20px;
        }
    </style>
</head>
<body class="night-mode">
    <div class="background-overlay"></div>
    <div class="gradient-circle"></div>

    <div class="container">
        <!-- Header -->
        <header class="header">
            <div class="site-title">🎬 یەکەمین سایتی کوردی بۆ دۆزینەوەی فیلمی نایاب</div>
            <h1 class="brand-name">Shocking Ending Movies</h1>
        </header>

        <!-- بەشی شێوەگۆڕی (ڕۆژ / شەو) -->
        <div class="mode-switcher-container">
            <span class="mode-label">شێوەگۆڕی: </span>
            <label class="mode-switcher">
                <input type="checkbox" id="modeToggle">
                <span class="mode-slider">
                    <span id="moon-icon" class="mode-icon">🌙</span>
                    <span id="sun-icon" class="mode-icon">☀️</span>
                </span>
            </label>
            <span class="mode-label" id="currentModeLabel">شەو</span>
            <div class="auto-status" id="autoStatus"></div>
        </div>

        <!-- Search Section -->
        <section class="search-section">
            <div class="search-box">
                <input type="text" class="search-input" placeholder="گەڕان بە ناوی فیلم...">
                <button class="search-button">
                    <i class="fas fa-search"></i> گەڕان
                </button>
            </div>
        </section>

        <!-- بەشی کۆمەڵایەتی (ئێستا 2 کارت) -->
        <section class="social-section">
            <h2 class="social-title">سەردانی ئەکاونتی ئینستاگرامەکانمان بکە</h2>
            <div class="social-container">
                <!-- Instagram Account 2 -->
                <div class="social-card">
                    <a href="https://www.instagram.com/lipri_26?igsh=MXQ0NG1icnc3Ym11NA==" target="_blank">
                        <div class="social-icon">
                            <i class="fab fa-instagram"></i>
                        </div>
                        <div class="social-name">ئەکاونتی فیلمەکان</div>
                        <div class="social-username">@lipri_26</div>
                        <div class="social-follow">شوێنکەوتن بکە</div>
                    </a>
                </div>
                
                <!-- Instagram Account 3 -->
                <div class="social-card">
                    <a href="https://www.instagram.com/ml.2050ll?igsh=MXQ1am53d3libzdhbA==" target="_blank">
                        <div class="social-icon">
                            <i class="fab fa-instagram"></i>
                        </div>
                        <div class="social-name">ئەکاونتی ڕەخنەی فیلم</div>
                        <div class="social-username">@ml.2050ll</div>
                        <div class="social-follow">شوێنکەوتن بکە</div>
                    </a>
                </div>
            </div>
        </section>

        <!-- Movie Grid -->
        <section class="movie-grid" id="movieGrid">
            <!-- Movie cards will be loaded here by JavaScript -->
        </section>

        <!-- No Results Message -->
        <div class="no-results" id="noResults">
            <i class="fas fa-film fa-2x" style="margin-bottom: 20px; opacity: 0.5;"></i>
            <p>هیچ فیلمێک بەم ناوە نەدۆزرایەوە!</p>
        </div>

        <!-- Pagination -->
        <div class="pagination" id="pagination">
            <!-- Pagination buttons will be added by JavaScript -->
        </div>

        <!-- Owner Section -->
        <section class="owner-box">
            <div class="owner-title">خاوەنی سایەت</div>
            <div class="owner-name">srusht.movies</div>
            <div class="owner-subtitle">ئەم ماڵپەرە خاوەنداریەتی دەکرێت لە لایەن srusht.movies</div>
        </section>

        <!-- Footer -->
        <footer class="footer">
            <p>© 2023 Shocking Ending Movies - هەموو مافەکان پارێزراون</p>
            <p style="margin-top: 10px; font-size: 0.9em; opacity: 0.6;">
                ئەم سایەتە بۆ خۆشی و ڕابواردنی هونەری سینەما دروست کراوە
            </p>
            <p style="margin-top: 15px; font-size: 0.85em; opacity: 0.5;">
                <i class="fas fa-hashtag"></i> فیلمە_کوردیەکان <i class="fas fa-hashtag"></i> کۆتایی_سەرسوڕهێنەر
            </p>
        </footer>
    </div>

    <script>
        // ========== بەشی سەرەکی مۆدەکان (شەو/ڕۆژ) ==========
        const modeToggle = document.getElementById('modeToggle');
        const currentModeLabel = document.getElementById('currentModeLabel');
        const autoStatus = document.getElementById('autoStatus');
        const body = document.body;

        // تەواو گۆڕاوەکانی ڕەنگ کۆنتڕۆڵ دەکات
        function updateThemeForMode(isDayMode) {
            if (isDayMode) {
                body.classList.add('day-mode');
                body.classList.remove('night-mode');
                currentModeLabel.textContent = 'ڕۆژ';
                // نیشانەی خۆکاربوون دەسڕێتەوە کاتێ بە دەستکرد گۆڕدرا
                autoStatus.textContent = '';
            } else {
                body.classList.add('night-mode');
                body.classList.remove('day-mode');
                currentModeLabel.textContent = 'شەو';
                autoStatus.textContent = '';
            }
            // بارگاویکردنەوەی ڕەنگەکان بۆ هەموو ئەو ئەمانەی کە لەسەر پاشبنەمای ئێستا پشت دەبەستن
            updateElementColors();
        }

        // فەنکشنێک بۆ نوێکردنەوەی تەنها ئەو توخمانەی کە پشت دەبەستن بە ڕەنگە گشتییەکان
        function updateElementColors() {
            // لێرە دەتوانیت هیچی تایبەت زیاد نەکەیت، چونکە هەموو شتێک لە ڕێگەی گۆڕاوەکانی CSS و کلاسەکانی 'body'ەوە کۆنتڕۆڵ دەکرێت.
            // بۆ نموونە: document.querySelectorAll('.movie-card').forEach(card => card.style.borderColor = newColor);
        }

        // 1. فەنکشنی دیاریکردنی کاتی خۆکار (بە پشتبەستن بە کاتژمێری هەلسووکەر)
        function getCurrentTimeBasedMode() {
            const now = new Date();
            const currentHour = now.getHours();
            // وەک نمونه: شەو لە 18:00 (6PM) تا 6:00 (6AM)
            const isDayTime = currentHour >= 6 && currentHour < 18;
            return isDayTime; // true = ڕۆژ, false = شەو
        }

        // 2. دیاریکردنی دۆخی سەرەتا و ڕێکخستنی توگڵەکە
        function initializeTheme() {
            const savedMode = localStorage.getItem('websiteThemeMode'); // 'day', 'night', یان 'auto'
            let initialIsDayMode;

            if (savedMode === 'day') {
                initialIsDayMode = true;
                modeToggle.checked = true;
                autoStatus.textContent = '';
            } else if (savedMode === 'night') {
                initialIsDayMode = false;
                modeToggle.checked = false;
                autoStatus.textContent = '';
            } else { // 'auto' یان هیچ (بارە سەرەکییەکە)
                // دیاریکردنی بە پشتبەستن بە کات
                initialIsDayMode = getCurrentTimeBasedMode();
                modeToggle.checked = initialIsDayMode; // توگڵ بەپێی کات ڕێک دەخرێت
                autoStatus.textContent = '(دۆخی خۆکار)';
                localStorage.setItem('websiteThemeMode', 'auto');
            }

            updateThemeForMode(initialIsDayMode);
            return initialIsDayMode;
        }

        // 3. گوێگرتن لە گۆڕینی توگڵ
        let currentIsDayMode = initializeTheme(); // دۆخی سەرەتا بار دەکرێت و هەڵدەگیرێت

        modeToggle.addEventListener('change', function() {
            // کاتێ توگڵ دەگۆڕدرێت، واتە بەکارهێنەر دەیەوێت دەستکرد بێت
            currentIsDayMode = this.checked;
            updateThemeForMode(currentIsDayMode);
            // 'auto' دەسڕدرێتەوە، و دۆخی هەڵبژێردراو هەڵدەگیرێت
            localStorage.setItem('websiteThemeMode', currentIsDayMode ? 'day' : 'night');
            autoStatus.textContent = '';
        });

        // 4. (ئارەزوومەندانە) گوێگرتن لە گۆڕینی کات بۆ خۆکارکردنەوە
        // ئەگەر 'auto' بوو، هەر خولێک کاتێک کۆدێک لە پشتیەوە کاردەکات پشکنین بکە
        setInterval(() => {
            if (localStorage.getItem('websiteThemeMode') === 'auto') {
                const shouldBeDayMode = getCurrentTimeBasedMode();
                if (shouldBeDayMode !== currentIsDayMode) {
                    currentIsDayMode = shouldBeDayMode;
                    modeToggle.checked = currentIsDayMode;
                    updateThemeForMode(currentIsDayMode);
                    autoStatus.textContent = '(دۆخی خۆکار)';
                }
            }
        }, 60000); // هەر 60 چرکەیەک

        // ========== Movie Data & Logic (وەک پێشتر) ==========
        const movies = [
            // (داتاکانی 22 فیلمەکە لێرە بۆ بەرزی نەگەڕایەوە. بە هەمان شێوەی پێشوو ماون.)
            // TODO: تەواوی ئەرەی movies[] لێرە بکۆپیکەرەوە.
        ];

        const movieGrid = document.getElementById('movieGrid');
        const searchInput = document.querySelector('.search-input');
        const searchButton = document.querySelector('.search-button');
        const noResults = document.getElementById('noResults');
        const pagination = document.getElementById('pagination');

        let currentPage = 1;
        const moviesPerPage = 6;
        let filteredMovies = [...movies];

        document.addEventListener('DOMContentLoaded', () => {
            // بەشی مۆدەکان پێشتر لە initializeTheme() دەست پێدەکات
            renderMovies();
            setupPagination();
            setupSearch();
            setupMovieClickEvents();
            
            setTimeout(() => {
                const socialCards = document.querySelectorAll('.social-card');
                socialCards.forEach((card, index) => {
                    card.style.animation = `fadeInUp 0.7s ease ${0.3 + (index * 0.15)}s backwards`;
                });
            }, 500);
        });

        // فەنکشنەکانی Movie وەک پێشتر (renderMovies, setupPagination, setupSearch, setupMovieClickEvents)
        // TODO: تەواوی فەنکشنەکانی JavaScript لێرە بکۆپیکەرەوە.
        // **تەنها زۆر دڵنیابە لەوەی کە لە فەنکشنی updateElementColors() هەر شتێک کە پەیوەست بە ڕەنگەکانی
        // توخمەکانی فیلمەوە بوو بیسڕیتەوە، چونکە ئێستا لە ڕێگەی CSSەوە کۆنتڕۆڵ دەکرێن.**
    </script>
</body>
</html>
