# Music123
<!DOCTYPE html>
<html dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>پخش‌کننده آهنگ‌های من</title>
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
            max-width: 800px;
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

        .upload-area {
            border: 3px dashed #667eea;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 30px;
        }

        .upload-area:hover {
            background: #f0f0ff;
            border-color: #764ba2;
        }

        .upload-icon {
            font-size: 48px;
            margin-bottom: 10px;
        }

        .file-input {
            display: none;
        }

        .songs-list {
            margin-top: 20px;
        }

        .song-card {
            background: #f8f9fa;
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            transition: all 0.3s;
            cursor: pointer;
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

        .song-size {
            font-size: 12px;
            color: #666;
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

        .delete-btn {
            background: #dc3545;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            margin-left: 8px;
            transition: all 0.3s;
        }

        .delete-btn:hover {
            background: #c82333;
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

        .empty-state {
            text-align: center;
            color: #999;
            padding: 40px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎵 کتابخانه موسیقی من</h1>
        <div class="subtitle">آهنگ‌های گوشی خود را آپلود کنید و به راحتی پخش کنید</div>

        <div class="upload-area" onclick="document.getElementById('fileInput').click()">
            <div class="upload-icon">📁</div>
            <div>برای آپلود آهنگ کلیک کنید</div>
            <div style="font-size: 12px; margin-top: 10px;">فرمت‌های مجاز: MP3, M4A, WAV, OGG</div>
        </div>
        <input type="file" id="fileInput" multiple accept=".mp3,.m4a,.wav,.ogg" class="file-input">

        <div class="songs-list" id="songsList">
            <div class="empty-state">
                🎵 هنوز آهنگی اضافه نکرده‌اید<br>
                روی قسمت بالا کلیک کنید و آهنگ‌های گوشی خود را انتخاب کنید
            </div>
        </div>

        <div class="player" id="player" style="display: none;">
            <div class="current-song" id="currentSong">هیچ آهنگی انتخاب نشده</div>
            <audio id="audioPlayer" controls></audio>
        </div>
    </div>

    <script>
        let songs = [];

        document.getElementById('fileInput').addEventListener('change', function(e) {
            const files = Array.from(e.target.files);
            
            files.forEach(file => {
                if (file.type.startsWith('audio/')) {
                    const song = {
                        id: Date.now() + Math.random(),
                        name: file.name.replace(/\.[^/.]+$/, ""),
                        file: file,
                        size: (file.size / (1024 * 1024)).toFixed(2)
                    };
                    songs.push(song);
                }
            });
            
            displaySongs();
        });

        function displaySongs() {
            const songsList = document.getElementById('songsList');
            
            if (songs.length === 0) {
                songsList.innerHTML = '<div class="empty-state">🎵 هنوز آهنگی اضافه نکرده‌اید<br>روی قسمت بالا کلیک کنید و آهنگ‌های گوشی خود را انتخاب کنید</div>';
                document.getElementById('player').style.display = 'none';
                return;
            }
            
            songsList.innerHTML = '';
            songs.forEach(song => {
                const songCard = document.createElement('div');
                songCard.className = 'song-card';
                songCard.innerHTML = `
                    <div class="song-info">
                        <div class="song-title">${escapeHtml(song.name)}</div>
                        <div class="song-size">${song.size} مگابایت</div>
                    </div>
                    <div>
                        <button class="play-btn" onclick="playSong('${song.id}')">▶ پخش</button>
                        <button class="delete-btn" onclick="deleteSong('${song.id}')">🗑 حذف</button>
                    </div>
                `;
                songsList.appendChild(songCard);
            });
        }

        function playSong(songId) {
            const song = songs.find(s => s.id == songId);
            if (song) {
                const audioPlayer = document.getElementById('audioPlayer');
                const url = URL.createObjectURL(song.file);
                audioPlayer.src = url;
                audioPlayer.play();
                document.getElementById('currentSong').innerHTML = `🎵 در حال پخش: ${escapeHtml(song.name)}`;
                document.getElementById('player').style.display = 'block';
            }
        }

        function deleteSong(songId) {
            songs = songs.filter(s => s.id != songId);
            displaySongs();
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }
    </script>
</body>
</html>
