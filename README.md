import os

# Menyiapkan konten HTML Game
html_content = """
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Maisha's Special Quest</title>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Comfortaa:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #020617;
            --box-bg: rgba(30, 58, 138, 0.8);
            --accent-cyan: #22d3ee;
            --accent-pink: #f472b6;
            --text-white: #f8fafc;
        }

        body, html {
            margin: 0; padding: 0;
            width: 100%; height: 100%;
            background-color: var(--bg-color);
            color: var(--text-white);
            font-family: 'Comfortaa', cursive;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Background Animasi Grid */
        .bg-grid {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-image: 
                linear-gradient(rgba(34, 211, 238, 0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(34, 211, 238, 0.1) 1px, transparent 1px);
            background-size: 40px 40px;
            z-index: -1;
            animation: moveGrid 20s linear infinite;
        }

        @keyframes moveGrid {
            from { background-position: 0 0; }
            to { background-position: 40px 40px; }
        }

        .container {
            width: 90%;
            max-width: 600px;
            perspective: 1000px;
        }

        .card {
            background: var(--box-bg);
            border: 4px solid var(--accent-cyan);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 0 30px rgba(34, 211, 238, 0.3);
            text-align: center;
            display: none; /* Hidden by default */
            animation: slideIn 0.5s ease-out;
        }

        .card.active {
            display: block;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(20px) rotateX(-10deg); }
            to { opacity: 1; transform: translateY(0) rotateX(0); }
        }

        .level-tag {
            font-family: 'Press Start 2P', cursive;
            font-size: 10px;
            color: var(--accent-cyan);
            margin-bottom: 20px;
            display: block;
            text-transform: uppercase;
        }

        h1, h2 {
            font-family: 'Press Start 2P', cursive;
            font-size: 16px;
            line-height: 1.6;
            color: var(--text-white);
            margin-bottom: 20px;
        }

        p {
            font-size: 16px;
            line-height: 1.8;
            margin-bottom: 25px;
        }

        .next-btn {
            background: var(--accent-cyan);
            color: #020617;
            border: none;
            padding: 12px 25px;
            font-family: 'Press Start 2P', cursive;
            font-size: 12px;
            cursor: pointer;
            border-radius: 5px;
            transition: all 0.3s;
            box-shadow: 4px 4px 0px #155e75;
        }

        .next-btn:hover {
            transform: translate(-2px, -2px);
            box-shadow: 6px 6px 0px #155e75;
            background: #fff;
        }

        .next-btn:active {
            transform: translate(2px, 2px);
            box-shadow: 0px 0px 0px #155e75;
        }

        .butterfly {
            font-size: 40px;
            margin-bottom: 10px;
            display: block;
        }

        .stats {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
            font-family: 'Press Start 2P', cursive;
            font-size: 8px;
            color: var(--accent-pink);
        }
    </style>
</head>
<body>

<div class="bg-grid"></div>

<div class="container">
    <div class="card active" id="s1">
        <span class="level-tag">Stage 01: Entrance</span>
        <h1>"Halo, my new special person 24/7"</h1>
        <button class="next-btn" onclick="go(2)">NEXT ></button>
    </div>

    <div class="card" id="s2">
        <span class="level-tag">Stage 02: Checking Status</span>
        <p>"lagi apaa? aku tebak lagi rebahan"</p>
        <button class="next-btn" onclick="go(3)">NEXT ></button>
    </div>

    <div class="card" id="s3">
        <span class="level-tag">Stage 03: Warning</span>
        <p>"aku mau melakukan sesuatu tapi jangan baper yaa"</p>
        <button class="next-btn" onclick="go(4)">NEXT ></button>
    </div>

    <div class="card" id="s4">
        <span class="level-tag">Stage 04: Validation</span>
        <h1>"janji?"</h1>
        <button class="next-btn" onclick="go(5)">JANJI !</button>
    </div>

    <div class="card" id="s5">
        <span class="level-tag">Stage 05: Gratitude</span>
        <p>"Hai, makasih yaaa karena dari banyaknya manusia di dunia ini, terimakasih sudah memilih aku untuk menemani hari hari akang"</p>
        <button class="next-btn" onclick="go(6)">NEXT ></button>
    </div>

    <div class="card" id="s6">
        <span class="level-tag">Stage 06: Honest Talk</span>
        <p>"iyaa aku tau aku selalu ngereog, aku selalu tantrum, marah marah, prengat prengut, dan bikin akang kesel. Maaf yaaa"</p>
        <button class="next-btn" onclick="go(7)">NEXT ></button>
    </div>

    <div class="card" id="s7">
        <span class="level-tag">Stage 07: Achievement Unlocked</span>
        <p>"terimakasih karena akang memilih aku untuk mempunyai perasaan akang yang kang rasakan hari ini. Rasa sayang, cinta, dan ketulusan"</p>
        <button class="next-btn" onclick="go(8)">NEXT ></button>
    </div>

    <div class="card" id="s8">
        <span class="level-tag">Stage 08: Blessing</span>
        <p>"aku bersyukur sekali menjadi seseorang yang akang pilih di hari ini, dan semoga selamanya"</p>
        <button class="next-btn" onclick="go(9)">NEXT ></button>
    </div>

    <div class="card" id="s9">
        <span class="level-tag">Stage 09: System Change</span>
        <p style="font-size: 14px;">"maaf kalau kehadiran aku membawa banyak perubahan di hidup akang. akang jadi ngerasa ga bebas, harus call aku tiap malem, harus ngabarin aku, ngeladenin aku tantrum, dan kadang harus menjelaskan suatu hal agar aku ga cemburu"</p>
        <button class="next-btn" onclick="go(10)">NEXT ></button>
    </div>

    <div class="card" id="s10">
        <span class="level-tag">Stage 10: Final Quest</span>
        <div style="text-align: left; font-size: 13px; max-height: 300px; overflow-y: auto; padding-right: 10px;">
            <p>"aku makasih bangettttt ke akang karena apa yang akang lakukan sekarang sudah membuat aku jauh lebih senang, dan bersyukur. aku akan selalu berusaha ada buat akang, ada buat kita, dan ada di setiap waktunya. kalau ini hanya sementara, aku ingin menciptakan banyak sekali kenangan agar kita bisa saling mensyukuri kehadiran satu sama lain, dan mengikhlaskan jika kita tidak dibuku takdir yang sama. Tapi, kalau kita ada di buku takdir yang sama, Ridha Nya akan mempermudah perjalanan kita. Aku percaya... akan hal itu."</p>
        </div>
        <button class="next-btn" onclick="go(11)">NEXT ></button>
    </div>

    <div class="card" id="s11">
        <span class="butterfly">🦋</span>
        <span class="level-tag">Game Completed</span>
        <h1>FROM YOUR BUTTERFLY, MAISHA</h1>
        <div class="stats">
            <span>LOVE: 100%</span>
            <span>FAITH: 100%</span>
        </div>
        <button class="next-btn" style="margin-top:20px;" onclick="go(1)">REPLAY</button>
    </div>
</div>

<script>
    function go(slideId) {
        // Sembunyikan semua card
        document.querySelectorAll('.card').forEach(card => {
            card.classList.remove('active');
        });
        // Tampilkan card yang dituju
        document.getElementById('s' + slideId).classList.add('active');
    }
</script>

</body>
</html>
"""

with open("game_maisha_untuk_akang.html", "w", encoding="utf-8") as f:
    f.write(html_content)
"""

