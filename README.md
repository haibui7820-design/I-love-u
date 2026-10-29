# I-love-u
To Quynh Chi
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gửi Em Bé Đáng Yêu 🥺</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ffe5ec, #ffc2d1);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }
        .card {
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(255, 182, 193, 0.5);
            text-align: center;
            max-width: 400px;
            width: 90%;
            z-index: 10;
            transition: all 0.3s ease;
        }
        h1 {
            color: #ff4d6d;
            font-size: 24px;
            margin-bottom: 15px;
        }
        p {
            color: #4a4a4a;
            font-size: 16px;
            line-height: 1.6;
            margin-bottom: 25px;
        }
        .gif-container img {
            width: 150px;
            height: 150px;
            margin-bottom: 20px;
            border-radius: 10px;
        }
        .btn-group {
            display: flex;
            justify-content: center;
            gap: 20px;
            position: relative;
            height: 50px;
        }
        button {
            padding: 12px 30px;
            font-size: 16px;
            font-weight: bold;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.2s ease;
        }
        #yesBtn {
            background-color: #ff4d6d;
            color: white;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4);
        }
        #yesBtn:hover {
            transform: scale(1.1);
            background-color: #ff758f;
        }
        #noBtn {
            background-color: #adadeb;
            color: white;
            position: absolute;
        }
        /* Hiệu ứng tim rơi */
        .heart {
            position: absolute;
            color: #ff758f;
            font-size: 20px;
            animation: fall linear forwards;
            z-index: 1;
            user-select: none;
        }
        @keyframes fall {
            to {
                transform: translateY(105vh) rotate(360deg);
            }
        }
    </style>
</head>
<body>

    <!-- Nhạc nền dỗ dành (Bạn có thể đổi link audio khác nếu muốn) -->
    <audio id="bgMusic" loop>
        <source src="https://soundhelix.com" type="audio/mpeg">
    </audio>

    <div class="card" id="mainCard">
        <div class="gif-container">
            <!-- Ảnh gif gấu xin lỗi dễ thương -->
            <img id="statusGif" src="https://giphy.com" alt="Cute gif">
        </div>
        <h1 id="title">Anh biết lỗi rồi mà... 🥺</h1>
        <p id="message">Ngoan, đừng giận anh nữa nhé? Anh mua trà sữa với đồ ăn ngon qua tạ lỗi với em nhaaa. Hết giận anh đi mà! ❤️</p>
        
        <div class="btn-group">
            <button id="yesBtn" onclick="forgive()">Cáooo</button>
            <button id="noBtn" onmouseover="flyAway()" onclick="flyAway()">Không</button>
        </div>
    </div>

    <script>
        // Bật nhạc khi người dùng tương tác lần đầu với trang web
        document.body.addEventListener('click', () => {
            const music = document.getElementById('bgMusic');
            music.play().catch(e => console.log("Chờ tương tác để bật nhạc"));
        }, { once: true });

        // Hàm làm nút "Không" bỏ chạy khi di chuột vào hoặc chạm vào
        function flyAway() {
            const noBtn = document.getElementById('noBtn');
            const card = document.getElementById('mainCard');
            const cardRect = card.getBoundingClientRect();
            
            // Giới hạn nút chỉ chạy quanh khu vực chiếc Card để không bị tràn ra ngoài màn hình
            const maxX = cardRect.width - noBtn.offsetWidth - 40;
            const maxY = cardRect.height - noBtn.offsetHeight - 40;
            
            const randomX = Math.floor(Math.random() * maxX) - (maxX / 2);
            const randomY = Math.floor(Math.random() * maxY) - (maxY / 2);
            
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
        }

        // Hàm xử lý khi bấm nút "Có" (Đồng ý hết giận)
        function forgive() {
            document.getElementById('statusGif').src = "https://giphy.com"; // Đổi sang gif vui vẻ
            document.getElementById('title').innerHTML = "Yêu em nhất trên đời! 🥰";
            document.getElementById('message').innerHTML = "Chờ anh 15 phút, anh phi trâu qua đón đi ăn liền nèee! Moahh 😘❤️";
            document.querySelector('.btn-group').style.display = 'none'; // Ẩn các nút bấm đi
            
            // Tăng tốc độ rơi tim ăn mừng
            setInterval(createHeart, 100);
        }

        // Tạo hiệu ứng tim rơi lãng mạn
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.top = '-5vh';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            heart.style.opacity = Math.random();
            heart.style.fontSize = Math.random() * 15 + 15 + 'px';
            
            document.body.appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
            }, 5000);
        }

        // Cứ mỗi 400ms tạo ra 1 trái tim rơi nhẹ nhàng ban đầu
        setInterval(createHeart, 400);
    </script>
</body>
</html>
