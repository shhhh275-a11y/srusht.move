<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>\ud83c\udfac \u0633\u0627\u06cc\u062a\u06cc \u0641\u06cc\u0644\u0645\u06d5\u06a9\u0627\u0646</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
            background: #1a1a2e;
            direction: rtl;
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
        }
        
        .comment-btn {
            width: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 15px;
            font-weight: 700;
            font-size: 1.05em;
            cursor: pointer;
            margin-top: 12px;
            transition: all 0.3s ease;
        }
        
        .comment-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
        }
        
        .rank {
            position: absolute;
            top: 20px;
            left: 20px;
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
        }
        
        /* \u0645\u06c6\u062f\u0627\u06b5\u06cc \u06a9\u06c6\u0645\u06ce\u0646\u062a */
        .comment-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            z-index: 2000;
            overflow-y: auto;
            padding: 20px;
        }
        
        .modal-content {
            background: linear-gradient(135deg, #2a2a3e 0%, #1a1a2e 100%);
            max-width: 700px;
            margin: 30px auto;
            border-radius: 25px;
            padding: 35px;
            position: relative;
            border: 1px solid rgba(255,255,255,0.1);
            box-shadow: 0 20px 60px rgba(0,0,0,0.8);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 20px;
            border-bottom: 2px solid rgba(255,255,255,0.1);
        }
        
        #modalMovieTitle {
            font-size: 2em;
            color: #f5c518;
            font-weight: bold;
        }
        
        .close-modal {
            background: #ff4444;
            border: none;
            color: white;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            font-size: 1.5em;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .close-modal:hover {
            transform: rotate(90deg);
            background: #ff0000;
        }
        
        .comment-form {
            background: rgba(255,255,255,0.05);
            padding: 25px;
            border-radius: 20px;
            margin-bottom: 30px;
        }
        
        .comment-form h3 {
            color: white;
            margin-bottom: 20px;
            font-size: 1.4em;
        }
        
        .comment-form input,
        .comment-form textarea {
            width: 100%;
            padding: 15px;
            margin-bottom: 15px;
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            border-radius: 12px;
            color: white;
            font-size: 1em;
            transition: all 0.3s;
        }
        
        .comment-form input:focus,
        .comment-form textarea:focus {
            outline: none;
            border-color: #667eea;
            background: rgba(255,255,255,0.15);
        }
        
        .comment-form textarea {
            resize: vertical;
            min-height: 100px;
            font-family: inherit;
        }
        
        .rating-input {
            margin-bottom: 15px;
        }
        
        .rating-input label {
            display: block;
            color: rgba(255,255,255,0.9);
            margin-bottom: 8px;
            font-weight: 600;
        }
        
        .rating-input select {
            width: 100%;
            padding: 12px;
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            border-radius: 12px;
            color: white;
            font-size: 1em;
            cursor: pointer;
        }
        
        .submit-comment {
            width: 100%;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border: none;
            padding: 15px;
            border-radius: 12px;
            color: white;
            font-weight: bold;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .submit-comment:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.5);
        }
        
        .comments-section h3 {
            color: white;
            margin-bottom: 20px;
            font-size: 1.4em;
        }
        
        .comment-item {
            background: rgba(255,255,255,0.08);
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 15px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: all 0.3s;
        }
        
        .comment-item:hover {
            background: rgba(255,255,255,0.12);
            transform: translateX(-5px);
        }
        
        .comment-header-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }
        
        .comment-author {
            font-weight: bold;
            color: #f5c518;
            font-size: 1.1em;
        }
        
        .comment-rating {
            background: linear-gradient(135deg, #f5c518, #d4af37);
            color: #000;
            padding: 5px 12px;
            border-radius: 8px;
            font-weight: bold;
        }
        
        .delete-comment {
            background: #ff4444;
            border: none;
            color: white;
            padding: 6px 12px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s;
        }
        
        .delete-comment:hover {
            background: #ff0000;
        }
        
        .comment-text {
            color: rgba(255,255,255,0.9);
            line-height: 1.6;
            margin-bottom: 10px;
        }
        
        .comment-time {
            color: rgba(255,255,255,0.5);
            font-size: 0.85em;
        }
        
        .no-comments {
            text-align: center;
            padding: 40px 20px;
            color: rgba(255,255,255,0.6);
            font-size: 1.1em;
        }
        
        .owner-box {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 25px;
            padding: 30px;
            margin: 50px auto;
            max-width: 500px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 12px 35px rgba(0,0,0,0.4);
            text-align: center;
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
        }
        
        .success-message {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, #00b894, #00cec9);
            color: white;
            padding: 18px 30px;
            border-radius: 12px;
            font-weight: bold;
            font-size: 1.1em;
            box-shadow: 0 10px 30px rgba(0,184,148,0.4);
            z-index: 3000;
            animation: slideIn 0.5s ease;
        }
        
        @keyframes slideIn {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
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
            .modal-content {
                padding: 20px;
            }
            #modalMovieTitle {
                font-size: 1.5em;
            }
        }
    </style>
</head>
<body>
    <div class="background-image"></div>
    
    <div class="container">
        <!-- \u0633\u06d5\u0631\u067e\u06d5\u0695\u06d5 -->
        <div class="header-section">
            <h1 class="main-title">\ud83c\udfa5 \u0628\u06d5\u062e\u06ce\u0631\u0628\u06ce\u06cc\u062a \u0628\u06c6 \u062c\u06cc\u0647\u0627\u0646\u06cc \u0641\u06cc\u0644\u0645\u06d5\u06a9\u0627\u0646</h1>
            <h2 class="brand-name">CINEMA WORLD</h2>
        </div>

        <!-- \u0628\u06d5\u0634\u06cc \u06af\u06d5\u0695\u0627\u0646 -->
        <div class="search-section">
            <div class="search-box">
                <input type="text" class="search-input" id="searchInput" placeholder="\ud83d\udd0d \u06af\u06d5\u0695\u0627\u0646 \u0628\u06d5\u062f\u0648\u0627\u06cc \u0641\u06cc\u0644\u0645 \u0628\u06d5 \u0646\u0627\u0648 \u06cc\u0627\u0646 \u0633\u0627\u06b5...">
                <button class="search-button" onclick="searchMovies()">\u06af\u06d5\u0695\u0627\u0646</button>
            </div>
        </div>

        <!-- \u0628\u06d5\u0634\u06cc \u0641\u06cc\u0644\u0645\u06d5\u06a9\u0627\u0646 -->
        <div class="movie-grid" id="movieGrid">
            <!-- \u0641\u06cc\u0644\u0645\u06d5\u06a9\u0627\u0646 \u0644\u06ce\u0631\u06d5 \u0632\u06cc\u0627\u062f \u062f\u06d5\u06a9\u0631\u06ce\u0646 \u0628\u06d5 JavaScript -->
        </div>

        <!-- \u062e\u0627\u0648\u06d5\u0646\u06cc \u0633\u0627\u06cc\u062a -->
        <div class="owner-box">
            <p class="owner-title">\u062e\u0627\u0648\u06d5\u0646\u06cc \u0633\u0627\u06cc\u062a</p>
            <h3 class="owner-name">\u0646\u0627\u0648\u06cc \u062a\u06c6 \u0644\u06ce\u0631\u06d5</h3>
            <p style="color: rgba(255,255,255,0.7); margin-top: 10px;">\ud83d\udcbb \u06af\u06d5\u0634\u06d5\u067e\u06ce\u062f\u06d5\u0631\u06cc \u0648\u06ce\u0628</p>
        </div>
    </div>

    <!-- \u0645\u06c6\u062f\u0627\u06b5\u06cc \u06a9\u06c6\u0645\u06ce\u0646\u062a \u0648 \u0695\u06d5\u062e\u0646\u06d5 -->
    <div id="commentModal" class="comment-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modalMovieTitle"></h2>
                <button class="close-modal" onclick="closeCommentModal()">\u2716</button>
            </div>
            
            <div class="comment-form">
                <h3>\ud83d\udcac \u0695\u06d5\u062e\u0646\u06d5 \u0648 \u0628\u06c6\u0686\u0648\u0648\u0646\u06d5\u06a9\u06d5\u062a \u0628\u0646\u0648\u0648\u0633\u06d5</h3>
                <input type="text" id="commentName" placeholder="\u0646\u0627\u0648\u062a \u0686\u06cc\u06cc\u06d5\u061f" maxlength="30">
                <textarea id="commentText" placeholder="\u0628\u06c6\u0686\u0648\u0648\u0646\u062a \u0644\u06d5\u0633\u06d5\u0631 \u0641\u06cc\u0644\u0645\u06d5\u06a9\u06d5\u060c \u0695\u06d5\u062e\u0646\u06d5\u06a9\u0627\u0646\u062a\u060c \u06cc\u0627\u0646 \u0647\u06d5\u0631\u0634\u062a\u06ce\u06a9..." rows="4" maxlength="500"></textarea>
                <div class="rating-input">
                    <label>\u2b50 \u0647\u06d5\u06b5\u0633\u06d5\u0646\u06af\u0627\u0646\u062f\u0646\u06cc \u062a\u06c6:</label>
                    <select id="commentRating">
                        <option value="10">10 - \u0646\u0627\u06cc\u0627\u0628! \u062a\u06d5\u0648\u0627\u0648 \u062a\u06d5\u0648\u0627\u0648 \u0646\u0627\u06cc\u0627\u0628\u06d5</option>
                        <option value="9">9 - \u0632\u06c6\u0631 \u0632\u06c6\u0631 \u0628\u0627\u0634\u06d5</option>
                        <option value="8">8 - \u0632\u06c6\u0631 \u0628\u0627\u0634\u06d5</option>
                        <option value="7">7 - \u0628\u0627\u0634\u06d5</option>
                        <option value="6">6 - \u062e\u0631\u0627\u067e \u0646\u06cc\u06cc\u06d5</option>
                        <option value="5" selected>5 - \u0645\u0627\u0645\u0646\u0627\u0648\u06d5\u0646\u062f</option>
                        <option value="4">4 - \u0644\u0627\u0648\u0627\u0632\u06d5</option>
                        <option value="3">3 - \u062e\u0631\u0627\u067e\u06d5</option>
                        <option value="2">2 - \u0632\u06c6\u0631 \u062e\u0631\u0627\u067e\u06d5</option>
                        <option value="1">1 - \u0646\u0627\u06a9\u0627\u0631\u0627\u0645\u06d5</option>
                    </select>
                </div>
                <button class="submit-comment" onclick="addComment()">\ud83d\ude80 \u0646\u0627\u0631\u062f\u0646\u06cc \u0695\u06d5\u062e\u0646\u06d5</button>
            </div>
            
            <div class="comments-section">
                <h3>\ud83d\udcdd \u0695\u06d5\u062e\u0646\u06d5 \u0648 \u06a9\u06c6\u0645\u06ce\u0646\u062a\u06d5\u06a9\u0627\u0646</h3>
                <div id="commentsList">
                    <!-- \u06a9\u06c6\u0645\u06ce\u0646\u062a\u06d5\u06a9\u0627\u0646 \u0644\u06ce\u0631\u06d5 \u067e\u06cc\u0634\u0627\u0646 \u062f\u06d5\u062f\u0631\u06ce\u0646 -->
                </div>
            </div>
        </div>
    </div>

    <script>
        // \u0644\u06cc\u0633\u062a\u06cc \u0641\u06cc\u0644\u0645\u06d5\u06a9\u0627\u0646 - \u062a\u06c6 \u062f\u06d5\u062a\u0648\u0627\u0646\u06cc\u062a \u0632\u06cc\u0627\u062a\u0631 \u0632\u06cc\u0627\u062f \u0628\u06a9\u06d5\u06cc\u062a!
        const movies = [
            {
                rank: 1,
                title: "The Shawshank Redemption",
                year: "1994",
                poster: "https://m.media-amazon.com/images/M/MV5BNDE3ODcxYzMtY2YzZC00NmNlLWJiNDMtZDViZWM2MzIxZDYwXkEyXkFqcGdeQXVyNjAwNDUxODI@._V1_.jpg",
                plot: "\u0686\u06cc\u0631\u06c6\u06a9\u06cc \u062f\u0648\u0648 \u062f\u06cc\u0644\u06ce\u06a9 \u06a9\u06d5 \u062f\u06c6\u0633\u062a\u0627\u06cc\u06d5\u062a\u06cc\u06cc\u06d5\u06a9\u06cc \u0642\u0648\u0648\u06b5 \u062f\u0631\u0648\u0633\u062a \u062f\u06d5\u06a9\u06d5\u0646 \u0644\u06d5 \u0632\u06cc\u0646\u062f\u0627\u0646 \u0648 \u0647\u06cc\u0648\u0627 \u062f\u06d5\u062f\u06c6\u0632\u0646\u06d5\u0648\u06d5 \u0644\u06d5 \u0695\u06ce\u06af\u0627\u06cc \u0628\u06d5\u0631\u062e\u06c6\u062f\u0627\u0631\u06cc\u06cc \u0648 \u06a9\u0627\u0631\u06d5 \u0628\u0627\u0634\u06d5\u06a9\u0627\u0646\u06d5\u0648\u06d5.",
                rating: "9.3",
                ageRating: "R"
            },
            {
                rank: 2,
                title: "The Godfather",
                year: "1972",
                poster: "https://m.media-amazon.com/images/M/MV5BM2MyNjYxNmUtYTAwNi00MTYxLWJmNWYtYzZlODY3ZTk3OTFlXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg",
                plot: "\u0686\u06cc\u0631\u06c6\u06a9\u06cc \u062e\u06ce\u0632\u0627\u0646\u06ce\u06a9\u06cc \u0645\u0627\u0641\u06cc\u0627 \u0644\u06d5 \u0626\u06d5\u0645\u0631\u06cc\u06a9\u0627 \u0648 \u0686\u06c6\u0646\u06cc\u06d5\u062a\u06cc \u06af\u0648\u0627\u0633\u062a\u0646\u06d5\u0648\u06d5\u06cc \u062f\u06d5\u0633\u06d5\u06b5\u0627\u062a \u0644\u06d5 \u0628\u0627\u0648\u06a9\u06ce\u06a9\u06cc \u067e\u06cc\u0631\u06d5\u0648\u06d5 \u0628\u06c6 \u06a9\u0648\u0695\u06d5 \u0647\u06d5\u06b5\u0646\u06d5\u0628\u0698\u06ce\u0631\u062f\u0631\u0627\u0648\u06d5\u06a9\u06d5\u06cc.",
                rating: "9.2",
                ageRating: "R"
            },
            {
                rank: 3,
                title: "The Dark Knight",
                year: "2008",
                poster: "https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_.jpg",
                plot: "\u0628\u0627\u062a\u0645\u0627\u0646 \u062f\u0698\u06cc \u062c\u06c6\u06a9\u06d5\u0631 \u062f\u06d5\u062c\u06d5\u0646\u06af\u06ce\u062a \u0628\u06c6 \u0695\u0632\u06af\u0627\u0631\u06a9\u0631\u062f\u0646\u06cc \u06af\u06c6\u062a\u0647\u0627\u0645 \u0633\u06cc\u062a\u06cc \u0644\u06d5 \u06a9\u0627\u06c6\u0633 \u0648 \u062a\u06cc\u0631\u06c6\u0631\u062f\u0627.",
                rating: "9.0",
                ageRating: "PG-13"
            },
            {
                rank: 4,
                title: "Inception",
                year: "2010",
                poster: "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_.jpg",
                plot: "\u062f\u0632\u06ce\u06a9\u06cc \u062a\u0648\u0627\u0646\u0627\u062f\u0627\u0631 \u062f\u06d5\u062a\u0648\u0627\u0646\u06ce\u062a \u0628\u0686\u06ce\u062a\u06d5 \u0646\u0627\u0648 \u062e\u06d5\u0648\u0646\u06d5\u06a9\u0627\u0646\u06cc \u062e\u06d5\u06b5\u06a9\u06cc\u06cc\u06d5\u0648\u06d5 \u0648 \u0628\u06cc\u0631\u06c6\u06a9\u06d5 \u0628\u062f\u0632\u06ce\u062a \u06cc\u0627\u0646 \u0628\u06cc\u0627\u0646\u0686\u06ce\u0646\u06ce\u062a.",
                rating: "8.8",
                ageRating: "PG-13"
            },
            {
                rank: 5,
                title: "Interstellar",
                year: "2014",
                poster: "https://m.media-amazon.com/images/M/MV5BZjdkOTU3MDktN2IxOS00OGEyLWFmMjktY2FiMmZkNWIyODZiXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg",
                plot: "\u06af\u06d5\u0634\u062a\u06ce\u06a9\u06cc \u0626\u0627\u0633\u0645\u0627\u0646\u06cc \u0628\u06c6 \u062f\u06c6\u0632\u06cc\u0646\u06d5\u0648\u06d5\u06cc \u06a9\u06c6\u0686\u0628\u06d5\u0631\u062e\u0627\u0646\u06d5\u06cc\u06d5\u06a9\u06cc \u0646\u0648\u06ce \u0628\u06c6 \u0645\u0631\u06c6\u06a4\u0627\u06cc\u06d5\u062a\u06cc \u067e\u06ce\u0634 \u0644\u06d5\u0646\u0627\u0648\u0686\u0648\u0648\u0646\u06cc \u0632\u06d5\u0648\u06cc.",
                rating: "8.7",
                ageRating: "PG-13"
            },
            {
                rank: 6,
                title: "The Matrix",
                year: "1999",
                poster: "https://m.media-amazon.com/images/M/MV5BNzQzOTk3OTAtNDQ0Zi00ZTVkLWI0MTEtMDllZjNkYzNjNTc4L2ltYWdlXkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg",
                plot: "\u0647\u0627\u06a9\u06d5\u0631\u06ce\u06a9 \u0695\u0627\u0633\u062a\u06cc\u06cc \u0633\u06d5\u0628\u0627\u0631\u06d5\u062a \u0628\u06d5 \u0698\u06cc\u0627\u0646 \u0648 \u0695\u06c6\u06b5\u06cc \u062e\u06c6\u06cc \u0644\u06d5 \u062c\u06d5\u0646\u06af\u06cc \u062f\u0698\u06cc \u06a9\u06c6\u0646\u062a\u0631\u06c6\u06b5\u06a9\u06d5\u0631\u0627\u0646\u06cc \u0698\u06cc\u0627\u0646 \u062f\u06d5\u0632\u0627\u0646\u06ce\u062a.",
                rating: "8.7",
                ageRating: "R"
            },
            {
                rank: 7,
                title: "Forrest Gump",
                year: "1994",
                poster: "https://m.media-amazon.com/images/M/MV5BNWIwODRlZTUtY2U3ZS00Yzg1LWJhNzYtMmZiYmEyNmU1NjMzXkEyXkFqcGdeQXVyMTQxNzMzNDI@._V1_.jpg",
                plot: "\u0686\u06cc\u0631\u06c6\u06a9\u06cc \u0698\u06cc\u0627\u0646\u06cc \u067e\u06cc\u0627\u0648\u06ce\u06a9\u06cc \u0633\u0627\u06a9\u0627\u0631 \u06a9\u06d5 \u0628\u06d5 \u0634\u06ce\u0648\u06d5\u06cc\u06d5\u06a9\u06cc \u0646\u0627\u0626\u0627\u0633\u0627\u06cc\u06cc \u06a9\u0627\u0631\u06cc\u06af\u06d5\u0631\u06cc \u0644\u06d5\u0633\u06d5\u0631 \u0628\u0648\u0648\u0646\u06d5\u0648\u06d5\u0631\u06d5\u06a9\u0627\u0646\u06cc \u0633\u06d5\u062f\u06d5\u06cc \u0662\u0660 \u0647\u06d5\u06cc\u06d5.",
                rating: "8.8",
                ageRating: "PG-13"
            },
            {
                rank: 8,
                title: "Fight Club",
                year: "1999",
                poster: "https://m.media-amazon.com/images/M/MV5BMmEzNTkxYjQtZTc0MC00YTVjLTg5ZTEtZWMwOWVlYzY0NWIwXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg",
                plot: "\u06a9\u0627\u0631\u0645\u06d5\u0646\u062f\u06ce\u06a9\u06cc \u0628\u06ce \u062e\u06d5\u0648 \u06cc\u0627\u0646\u06d5\u06cc\u06d5\u06a9 \u06cc\u06d5\u06a9\u0644\u0627\u06cc\u06cc \u06a9\u0644\u0648\u0628\u06ce\u06a9\u06cc \u0634\u06d5\u0695\u06a9\u0631\u062f\u0646\u06cc \u0646\u0647\u06ce\u0646\u06cc \u062f\u0627\u0645\u06d5\u0632\u0631\u06ce\u0646\u06ce\u062a \u06a9\u06d5 \u062f\u0648\u0627\u062a\u0631 \u062f\u06d5\u0628\u06ce\u062a\u06d5 \u0634\u062a\u06ce\u06a9\u06cc \u0632\u06cc\u0627\u062a\u0631.",
                rating: "8.8",
                ageRating: "R"
            },
            {
                rank: 9,
                title: "The Lord of the Rings",
                year: "2001",
                poster: "https://m.media-amazon.com/images/M/MV5BN2EyZjM3NzUtNWUzMi00MTgxLWI0NTctMzY4M2VlOTdjZWRiXkEyXkFqcGdeQXVyNDUzOTQ5MjY@._V1_.jpg",
                plot: "\u06af\u0631\u0648\u0648\u067e\u06ce\u06a9 \u06af\u06d5\u0634\u062a\u06ce\u06a9\u06cc \u0645\u06d5\u062a\u0631\u0633\u06cc\u062f\u0627\u0631 \u062f\u06d5\u0633\u062a \u067e\u06ce\u062f\u06d5\u06a9\u06d5\u0646 \u0628\u06c6 \u0644\u06d5\u0646\u0627\u0648\u0628\u0631\u062f\u0646\u06cc \u0626\u06d5\u0646\u06af\u0648\u0633\u062a\u06cc\u0644\u06d5\u06cc\u06d5\u06a9\u06cc \u062a\u0648\u0627\u0646\u0627\u062f\u0627\u0631.",
                rating: "8.9",
                ageRating: "PG-13"
            },
            {
                rank: 10,
                title: "Pulp Fiction",
                year: "1994",
                poster: "https://m.media-amazon.com/images/M/MV5BNGNhMDIzZTUtNTBlZi00MTRlLWFjM2ItYzViMjE3YzI5MjljXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg",
                plot: "\u0686\u06d5\u0646\u062f