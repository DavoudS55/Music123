<!DOCTYPE html>
<html dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مشارکت‌گذاری موسیقی - آهنگ‌های همه</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Tahoma', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }

        h1 {
            color: #333;
            text-align: center;
            margin-bottom: 10px;
        }

        .subtitle {
            text-align: center;
            color: #666;
            margin-bottom: 30px;
        }

        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            border-bottom: 2px solid #e0e0e0;
        }

        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border: none;
            background: none;
            font-size: 16px;
            color: #666;
            transition: all 0.3s;
        }

        .tab.active {
            color: #667eea;
            border-bottom: 3px solid #667eea;
            font-weight: bold;
        }

        .upload-area {
            border: 3px dashed #667eea;
            border-radius: 15px;
            padding: 40px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 20px;
        }

        .upload-area:hover {
            background: #f0f0ff;
            border-color: #764ba2;
        }

        .file-input {
            display: none;
        }

        .songs-grid {
            display: grid;
            gap: 15px;
            margin-top: 20px;
        }

        .song-card {
            background: #f8f9fa;
            border-radius: 12px;
            padding: 15px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            transition: all 0.3s;
        }

        .song-card:hover {
            background: #e9ecef;
            transform: translateX(-5px);
        }

        .song-info {
            flex: 1;
        }

        .song-title {
            font-weight: bold;
            color: #333;
            margin-bottom: 5px;
        }

        .song-meta {
            font-size: 12px;
            color: #666;
            display: flex;
            gap: 15px;
        }

        .uploader-name {
            color: #667eea;
        }

        .play-btn {
            background: #667eea;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .play-btn:hover {
            background: #764ba2;
            transform: scale(1.05);
        }

        .player {
            background: #f8f9fa;
            border-radius: 12px;
            padding: 20px;
            margin-top: 20px;
            position: sticky;
            bottom: 20px;
        }

        .current-song {
            font-weight: bold;
            color: #667eea;
            margin-bottom: 10px;
        }

        audio {
            width: 100%;
            margin-top: 10px;
        }

        .loading {
            text-align: center;
            padding: 40px;
            color: #666;
        }

        .user-info {
            background: #e8eaf6;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .username-input {
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 14px;
            direction: ltr;
        }

        .save-btn {
            background: #667eea;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            cursor: pointer;
        }

        .empty-state {
            text-align: center;
            padding: 40px;
            color: #999;
        }

        .progress-bar {
            width: 100%;
            height: 4px;
            background: #e0e0e0;
            border-radius: 2px;
            overflow: hidden;
            margin-top: 10px;
        }

        .progress-fill {
            height: 100%;
            background: #667eea;
            transition: width 0.3s;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎵 کتابخانه موسیقی اشتراکی</h1>
        <div class="subtitle">هر کسی می‌تواند آهنگ آپلود کند - همه می‌توانند گوش کنند</div>

        <div class="user-info">
            <span>👤 نام شما در سایت:</span>
            <div>
                <input type="text" id="username" class="username-input" placeholder="نام خود را وارد کنید" maxlength="20">
                <button onclick="saveUsername()" class="save-btn">ذخیره</button>
            </div>
        </div>

        <div class="tabs">
            <button class="tab active" onclick="showTab('upload')">📤 آپلود آهنگ</button>
            <button class="tab" onclick="showTab('library')">🎵 کتابخانه عمومی</button>
        </div>

        <div id="uploadTab">
            <div class="upload-area" onclick="document.getElementById('fileInput').click()">
                <div style="font-size: 48px;">📁</div>
                <div>برای آپلود آهنگ کلیک کنید</div>
                <div style="font-size: 12px; margin-top: 10px;">فرمت‌های مجاز: MP3, M4A, WAV, OGG (حداکثر 10 مگابایت)</div>
            </div>
            <input type="file" id="fileInput" accept=".mp3,.m4a,.wav,.ogg">
            <div id="uploadProgress" style="display: none;">
                <div class="progress-bar">
                    <div class="progress-fill" style="width: 0%"></div>
                </div>
                <div style="text-align: center; margin-top: 5px; font-size: 12px;">در حال آپلود...</div>
            </div>
        </div>

        <div id="libraryTab" style="display: none;">
            <div class="songs-grid" id="songsList">
                <div class="loading">در حال بارگذاری آهنگ‌ها...</div>
            </div>
        </div>

        <div class="player" id="player" style="display: none;">
            <div class="current-song" id="currentSong">هیچ آهنگی انتخاب نشده</div>
            <audio id="audioPlayer" controls></audio>
        </div>
    </div>

    <!-- Firebase SDK -->
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-storage-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore-compat.js"></script>

    <script>
        // پیکربندی Firebase (شما باید این را با اطلاعات خودتان جایگزین کنید)
        // برای دریافت این اطلاعات به console.firebase.google.com بروید
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_AUTH_DOMAIN",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_STORAGE_BUCKET",
            messagingSenderId: "YOUR_SENDER_ID",
            appId: "YOUR_APP_ID"
        };

        // راهنمای ساخت Firebase (فعلاً از LocalStorage استفاده می‌کنیم)
        let useFirebase = false;
        
        // نسخه ساده با LocalStorage (برای تست اولیه)
        let songs = JSON.parse(localStorage.getItem('sharedSongs') || '[]');
        
        function saveToLocalStorage() {
            localStorage.setItem('sharedSongs', JSON.stringify(songs));
        }

        function getCurrentUser() {
            return localStorage.getItem('shareMusicUser') || 'ناشناس';
        }

        function saveUsername() {
            const username = document.getElementById('username').value;
            if (username) {
                localStorage.setItem('shareMusicUser', username);
                alert('نام شما ذخیره شد!');
                displaySongs();
            }
        }

        document.getElementById('username').value = getCurrentUser();

        document.getElementById('fileInput').addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file && file.size <= 10 * 1024 * 1024) { // 10MB limit
                uploadSong(file);
            } else {
                alert('فایل بزرگتر از 10 مگابایت است!');
            }
        });

        function uploadSong(file) {
            const progressDiv = document.getElementById('uploadProgress');
            progressDiv.style.display = 'block';
            
            const reader = new FileReader();
            reader.onload = function(e) {
                const song = {
                    id: Date.now(),
                    name: file.name.replace(/\.[^/.]+$/, ""),
                    data: e.target.result,
                    uploader: getCurrentUser(),
                    date: new Date().toLocaleDateString('fa-IR'),
                    size: (file.size / (1024 * 1024)).toFixed(2)
                };
                
                songs.unshift(song);
                saveToLocalStorage();
                displaySongs();
                
                progressDiv.style.display = 'none';
                document.getElementById('fileInput').value = '';
                alert('آهنگ با موفقیت آپلود شد!');
                
                showTab('library');
            };
            reader.readAsDataURL(file);
        }

        function displaySongs() {
            const songsList = document.getElementById('songsList');
            
            if (songs.length === 0) {
                songsList.innerHTML = '<div class="empty-state">🎵 هنوز آهنگی آپلود نشده است<br>اولین نفری باشید که آهنگ آپلود می‌کند!</div>';
                return;
            }
            
            songsList.innerHTML = '';
            songs.forEach(song => {
                const songCard = document.createElement('div');
                songCard.className = 'song-card';
                songCard.innerHTML = `
                    <div class="song-info">
                        <div class="song-title">${escapeHtml(song.name)}</div>
                        <div class="song-meta">
                            <span>👤 ${escapeHtml(song.uploader)}</span>
                            <span>📅 ${song.date}</span>
                            <span>📦 ${song.size} MB</span>
                        </div>
                    </div>
                    <button class="play-btn" onclick="playSong('${song.id}')">▶ پخش</button>
                `;
                songsList.appendChild(songCard);
            });
        }

        function playSong(songId) {
            const song = songs.find(s => s.id == songId);
            if (song && song.data) {
                const audioPlayer = document.getElementById('audioPlayer');
                audioPlayer.src = song.data;
                audioPlayer.play();
                document.getElementById('currentSong').innerHTML = `🎵 در حال پخش: ${escapeHtml(song.name)} - آپلود شده توسط ${escapeHtml(song.uploader)}`;
                document.getElementById('player').style.display = 'block';
            }
        }

        function showTab(tab) {
            const uploadTab = document.getElementById('uploadTab');
            const libraryTab = document.getElementById('libraryTab');
            const tabs = document.querySelectorAll('.tab');
            
            if (tab === 'upload') {
                uploadTab.style.display = 'block';
                libraryTab.style.display = 'none';
                tabs[0].classList.add('active');
                tabs[1].classList.remove('active');
            } else {
                uploadTab.style.display = 'none';
                libraryTab.style.display = 'block';
                tabs[0].classList.remove('active');
                tabs[1].classList.add('active');
                displaySongs();
            }
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        displaySongs();

        // راهنمای اتصال به Firebase (برای ذخیره واقعی روی سرور)
        console.log('💡 برای ذخیره دائمی آهنگ‌ها روی سرور، مراحل زیر را انجام دهید:');
        console.log('1. به سایت console.firebase.google.com بروید');
        console.log('2. یک پروژه جدید بسازید');
        console.log('3. در بخش Storage، قوانین امنیتی را به حالت آزمایشی بگذارید');
        console.log('4. تنظیمات پروژه را کپی کنید و در firebaseConfig قرار دهید');
    </script>
</body>
</html>
