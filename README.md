<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Message for Akang</title>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Comfortaa:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    
    <style>
        :root {
            --bg-dark: #020617;
            --primary-blue: #1e40af;
            --accent-cyan: #22d3ee;
            --accent-pink: #f472b6;
            --text-white: #f8fafc;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body, html {
            height: 100%;
            background-color: var(--bg-dark);
            color: var(--text-white);
            font-family: 'Comfortaa', cursive;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Animasi Background Grid */
        .bg-overlay {
            position: fixed;
            inset: 0;
            background-image: 
                linear-gradient(rgba(34, 211, 238, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(34, 211, 238, 0.05) 1px, transparent 1px);
            background-size: 40px 40px;
            z-index: -1;
            animation: move 20s linear infinite;
        }

        @keyframes move {
            from { background-position: 0 0; }
            to { background-position: 40px 40px; }
        }

        .container {
            width: 90%;
            max-width: 500px;
            z-index: 10;
        }

        /* Dialog Box ala Game */
        .card {
            background: rgba(15, 23, 42, 0.9);
            border: 4px solid var(--accent-cyan);
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 0 40px rgba(34, 211, 238, 0.2);
            text-align: center;
            display: none; /* Sembunyi secara default */
            animation: slideUp 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .card.active { display: block; }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .tag {
            font-family: 'Press Start 2P', cursive;
            font-size: 10px;
            color: var(--accent-cyan);
            margin-bottom: 20px;
            display: block;
        }

        h1 { font-family: 'Press Start 2P', cursive; font-size: 16px; margin-bottom: 15px; color: #fff; line-height: 1.6; }
        p { font-size: 16px; line-height: 1.8; margin-bottom: 25px; }

        /* Tombol Next */
        .next-btn {
            background: var(--accent-cyan);
            color: var(--bg-dark);
            border: none;
            padding: 15px 30px;
            font-family: 'Press Start 2P', cursive;
            font-size: 11px;
            cursor: pointer;
            border-radius: 4px;
            transition: 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            box-shadow: 4px 4px 0 var(--primary-blue);
        }

        .next-btn:hover {
            background: #fff;
            transform: translate(-2px, -2px);
            box-shadow: 6px 6px 0 var(--primary-blue);
        }

        .next-btn:active { transform: translate(2px, 2px); box-shadow: 0 0 0; }

        .icon-box { font-size: 40px; color: var(--accent-cyan); margin-bottom: 20px; }
        .heart { color: var(--accent-pink); }
    </style>
</head>
<body>

    <div class="bg-overlay"></div>

    <div class="container">
        <div class="card active" id="s1">
            <span class="tag">STAGE 01</span>
            <div class="icon-box"><i class="fas fa-gamepad"></i></div>
            <h1>"Halo, my new special person 24/7"</h1>
            <button class="next-btn" onclick="next(2)">START <i class="fas fa-play"></i></button>
        </div>

        <div class="card" id="s2">
            <span class="tag">STAGE 02</span>
            <div class="icon-box"><i class="fas fa-bed"></i></div>
            <p>"lagi apaa? aku tebak lagi rebahan"</p>
            <button class="next-btn" onclick="next(3)">NEXT</button>
        </div>

        <div class="card" id="s3">
            <span class="tag">WARNING</span>
            <div class="icon-box" style="color: yellow;"><i class="fas fa-exclamation-triangle"></i></div>
            <p>"aku mau melakukan sesuatu tapi jangan baper yaa"</p>
            <button class="next-btn" onclick="next(4)">OKEY</button>
        </div>

        <div class="card" id="s4">
            <span class="tag">QUEST</span>
            <div class="icon-box"><i class="fas fa-key"></i></div>
            <h1>"janji?"</h1>
            <button class="next-btn" onclick="next(5)">JANJI!</button>
        </div>

        <div class="card" id="s5">
            <span class="tag">STAGE 05</span>
            <div class="icon-box"><i class="fas fa-users"></i></div>
            <p>"Hai, makasih yaaa karena dari banyaknya manusia di dunia ini, terimakasih sudah memilih aku untuk menemani hari hari akang"</p>
            <button class="next-btn" onclick="next(6)">NEXT</button>
        </div>

        <div class="card" id="s6">
            <span class="tag">HONESTY</span>
            <div class="icon-box"><i class="fas fa-face-sad-tear"></i></div>
            <p>"iyaa aku tau aku selalu ngereog, aku selalu tantrum, marah marah, prengat prengut, dan bikin akang kesel. Maaf yaaa"</p>
            <button class="next-btn" onclick="next(7)">NEXT</button>
        </div>

        <div class="card" id="s7">
            <span class="tag">LEVEL UP!</span>
            <div class="icon-box"><i class="fas fa-heart heart"></i></div>
            <p>"terimakasih karena akang memilih aku untuk mempunyai perasaan akang yang kang rasakan hari ini. Rasa sayang, cinta, dan ketulusan"</p>
            <button class="next-btn" onclick="next(8)">NEXT</button>
        </div>

        <div class="card" id="s8">
            <span class="tag">GRATITUDE</span>
            <div class="icon-box"><i class="fas fa-star"></i></div>
            <p>"aku bersyukur sekali menjadi seseorang yang akang pilih di hari ini, dan semoga selamanya"</p>
            <button class="next-btn" onclick="next(9)">NEXT</button>
        </div>

        <div class="card" id="s9">
            <span class="tag">REFLECTION</span>
            <p style="font-size: 14px;">"maaf kalau kehadiran aku membawa banyak perubahan di hidup akang. akang jadi ngerasa ga bebas, harus call aku tiap malem, harus ngabarin aku, ngeladenin aku tantrum, dan kadang harus menjelaskan suatu hal agar aku ga cemburu"</p>
            <button class="next-btn" onclick="next(10)">NEXT</button>
        </div>

        <div class="card" id="s10">
            <span class="tag">FINAL STORY</span>
            <div style="max-height: 250px; overflow-y: auto; text-align: left; padding: 10px;">
                <p style="font-size: 14px;">"aku makasih bangettttt ke akang karena apa yang akang lakukan sekarang sudah membuat aku jauh lebih senang, dan bersyukur. aku akan selalu berusaha ada buat akang, ada buat kita, dan ada di setiap waktunya. kalau ini hanya sementara, aku ingin menciptakan banyak sekali kenangan agar kita bisa saling mensyukuri kehadiran satu sama lain, dan mengikhlaskan jika kita tidak dibuku takdir yang sama. Tapi, kalau kita ada di buku takdir yang sama, Ridha Nya akan mempermudah perjalanan kita. Aku percaya... akan hal itu."</p>
            </div>
            <button class="next-btn" onclick="next(11)">FINISH</button>
        </div>

        <div class="card" id="s11">
            <div class="icon-box" style="color: var(--accent-pink);"><i class="fas fa-dove"></i></div>
            <span class="tag">GAME COMPLETED</span>
            <h1>FROM YOUR BUTTERFLY, MAISHA</h1>
            <p style="font-size: 12px; color: var(--accent-cyan);">"I love you and I'm glad you're here."</p>
            <button class="next-btn" onclick="location.reload()">REPLAY <i class="fas fa-redo"></i></button>
        </div>
    </div>

    <script>
        function next(id) {
            document.querySelectorAll('.card').forEach(c => c.classList.remove('active'));
            document.getElementById('s' + id).classList.add('active');
        }
    </script>
</body>
</html>

