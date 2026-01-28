    body {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        min-height: 100vh;
        position: relative;
        overflow-x: hidden;
        background: #1a1a2e;
    }
    
    body::before {
        content: '';
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(135deg, rgba(0,0,0,0.8) 0%, rgba(26,26,46,0.9) 100%);
        z-index: -2;
    }
    
    .background-image {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 600px;
        height: 600px;
        border-radius: 50%;
        background: radial-gradient(circle, #c77b63 0%, #8b5a4a 50%, transparent 70%);
        opacity: 0.15;
        filter: blur(60px);
        z-index: -1;
        animation: float 25s ease-in-out infinite;
    }
    
    .bot-background {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: url('https://images.unsplash.com/photo-1489599809505-7c8e1a48bcc0?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
        background-size: cover;
        background-position: center;
        opacity: 0.1;
        z-index: -1;
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
    
    .header-section {
        text-align: center;
        margin-bottom: 40px;
        padding: 20px 0;
    }
    
    .main-title {
        font-size: 1.8em;
        font-weight: 700;
        margin-bottom: 15px;
        padding: 20px 50px;
        border: 2px solid rgba(255,255,255,0.3);
        border-radius: 60px;
        display: inline-block;
        background: rgba(255,255,255,0.05);
        backdrop-filter: blur(10px);
        color: white;
        animation: fadeInDown 1s ease;
        text-shadow: 0 2px 10px rgba(0,0,0,0.5);
    }
    
    .brand-name {
        font-size: 3.5em;
        font-weight: 900;
        color: white;
        text-shadow: 3px 3px 0px rgba(0,0,0,0.4), 0 0 30px rgba(255,255,255,0.3);
        background: linear-gradient(45deg, #ffffff, #e0e0e0, #a8a8a8);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        margin-bottom: 5px;
        animation: fadeIn 1.5s ease;
        letter-spacing: 3px;
    }
    
    .search-section {
        max-width: 600px;
        margin: 30px auto;
        padding: 0 20px;
    }
    
    .search-box {
        display: flex;
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(15px);
        border-radius: 50px;
        padding: 5px;
        border: 1px solid rgba(255, 255, 255, 0.2);
        box-shadow: 0 8px 25px rgba(0,0,0,0.3);
    }
    
    .search-input {
        flex: 1;
        background: transparent;
        border: none;
        padding: 15px 20px;
        color: white;
        font-size: 1.1em;
        outline: none;
    }
    
    .search-input::placeholder {
        color: rgba(255,255,255,0.6);
    }
    
    .search-button {
        background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
        border: none;
        border-radius: 50px;
        padding: 15px 30px;
        color: white;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
    }
    
    .search-button:hover {
        transform: scale(1.05);
        box-shadow: 0 0 15px rgba(253,29,29,0.5);
    }
    
    @keyframes fadeInDown {
        from {
            opacity: 0;
            transform: translateY(-40px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }
    
    @keyframes fadeIn {
        from { opacity: 0; }
        to { opacity: 1; }
    }
    
    .movie-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
        gap: 35px;
        padding: 20px 0;
    }
    
    .movie-card {
        background: rgba(255, 255, 255, 0.08);
        backdrop-filter: blur(15px);
        border-radius: 25px;
        overflow: hidden;
        box-shadow: 0 12px 40px rgba(0,0,0,0.4);
        border: 1px solid rgba(255, 255, 255, 0.12);
        transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
        cursor: pointer;
        position: relative;
        animation: fadeInUp 0.7s ease backwards;
    }
    
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
    
    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(40px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }
    
    .movie-card:hover {
        transform: translateY(-18px) scale(1.03);
        box-shadow: 0 25px 70px rgba(0,0,0,0.6);
        background: rgba(255, 255, 255, 0.12);
        border: 1px solid rgba(255, 255, 255, 0.25);
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
        background: linear-gradient(
            45deg,
            transparent 30%,
            rgba(255, 255, 255, 0.08) 50%,
            transparent 70%
        );
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
    
    .movie-title {
        font-size: 1.6em;
        font-weight: 700;
        margin-bottom: 12px;
        color: #fff;
        text-shadow: 2px 2px 6px rgba(0,0,0,0.5);
        line-height: 1.3;
    }
    
    .movie-year {
        color: rgba(255, 255, 255, 0.85);
        font-size: 1em;
        margin-bottom: 14px;
        font-weight: 500;
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
    
    .rating-container {
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
    
    .movie-card:hover .age-rating {
        transform: scale(1.08);
    }
    
    .rank {
        position: absolute;
        top: 20px;
        right: 20px;
        background: rgba(0,0,0,0.9);
        color: #f5c518;
        width: 55px;
        height: 55px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 800;
        font-size: 1.5em;
        border: 3px solid #f5c518;
        box-shadow: 0 5px 25px rgba(245, 197, 24, 0.6);
        z-index: 10;
        animation: pulse 2.5s infinite;
    }
    
    @keyframes pulse {
        0%, 100% { transform: scale(1); }
        50% { transform: scale(1.08); }
    }
    
    /*----- خاونی سایەت / ئینستاگرام -----*/
    .social-section {
        text-align: center;
        margin: 40px auto;
    }
    
    .ig-banner {
        font-size: 1.15em;
        margin-bottom: 25px;
    }
    
    .ig-banner a {
        display: inline-flex;
        align-items: center;
        gap: 10px;
        padding: 14px 32px;
        border-radius: 60px;
        background: linear-gradient(45deg, #833ab4, #fd1d1d, #fcb045);
        color: #fff;
        text-decoration: none;
        font-weight: 700;
        box-shadow: 0 0 25px rgba(253,29,29,.6), 0 6px 20px rgba(0,0,0,.3);
        transition: transform .3s, box-shadow .3s;
    }
    
    .ig-banner a:hover {
        transform: translateY(-4px) scale(1.06);
        box-shadow: 0 0 35px rgba(253,29,29,.8), 0 8px 25px rgba(0,0,0,.4);
    }
    
    .ig-banner .ig-icon {
        font-size: 1.5em;
    }
    
    .owner-box {
        background: rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(15px);
        border-radius: 25px;
        padding: 30px;
        margin: 35px auto;
        max-width: 500px;
        border: 1px solid rgba(255, 255, 255, 0.2);
        box-shadow: 0 12px 35px rgba(0,0,0,0.4);
        text-align: center;
        position: relative;
        overflow: hidden;
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
    
    .owner-name {
        font-size: 2.2em;
        color: #f5c518;
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
    
    .footer {
        text-align: center;
        margin-top: 60px;
        padding: 25px;
        color: rgba(255,255,255,0.7);
        font-size: 0.95em;
        border-top: 1px solid rgba(255,255,255,0.15);
    }
    
    @media (max-width: 768px) {
        .main-title { 
            font-size: 1.4em; 
            padding: 16px 30px;
        }
        .brand-name { 
            font-size: 2.5em; 
        }
        .movie-grid {
            grid-template-columns: 1fr;
            gap: 25px;
        }
        .background-image {
            width: 400px;
            height: 400px;
        }
        .social-section {
            margin: 30px auto;
        }
        .owner-box {
            max-width: 90%;
            padding: 25px;
        }
        .owner-name {
            font-size: 1.8em;
        }
        .movie-poster {
            height: 380px;
        }
        .search-section {
            padding: 0 15px;
        }
    }
</style>