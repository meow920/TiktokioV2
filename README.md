<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>UltraTik – Ultimate TikTok Toolkit (10x Better)</title>
    <!-- Tailwind + Font Awesome (CDN) -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Custom Styles -->
    <style>
        /* Smooth transitions & glass morphism */
        .glass-card { background: rgba(255, 255, 255, 0.1); backdrop-filter: blur(12px); border-radius: 2rem; border: 1px solid rgba(255,255,255,0.2); }
        .btn-primary { background: linear-gradient(135deg, #FE2C55, #25F4EE); transition: transform 0.2s, box-shadow 0.2s; }
        .btn-primary:hover { transform: scale(1.02); box-shadow: 0 10px 20px -5px rgba(0,0,0,0.3); }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #1f1f2e; border-radius: 10px; }
        ::-webkit-scrollbar-thumb { background: #FE2C55; border-radius: 10px; }
        body { background: #0f0f1a; }
        .fade-in { animation: fadeIn 0.4s ease-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="text-white font-sans antialiased">

    <!-- Navigation Bar -->
    <nav class="fixed top-0 w-full z-50 bg-black/40 backdrop-blur-lg border-b border-white/10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center space-x-2">
                    <i class="fab fa-tiktok text-3xl text-[#FE2C55]"></i>
                    <span class="font-bold text-xl bg-gradient-to-r from-[#FE2C55] to-[#25F4EE] bg-clip-text text-transparent">UltraTik</span>
                    <span class="text-xs bg-white/20 px-2 py-0.5 rounded-full">Pro</span>
                </div>
                <div class="hidden md:flex space-x-6">
                    <a href="#" data-tab="downloader" class="tab-link text-white/80 hover:text-white transition">Downloader</a>
                    <a href="#" data-tab="editor" class="tab-link text-white/80 hover:text-white transition">Editor</a>
                    <a href="#" data-tab="scheduler" class="tab-link text-white/80 hover:text-white transition">Scheduler</a>
                    <a href="#" data-tab="library" class="tab-link text-white/80 hover:text-white transition">My Library</a>
                    <a href="#" data-tab="trends" class="tab-link text-white/80 hover:text-white transition">Trends</a>
                </div>
                <div class="flex items-center space-x-3">
                    <i class="fas fa-cloud-upload-alt text-xl cursor-pointer hover:text-[#25F4EE] transition" id="cloudBackupBtn" title="Backup library to cloud (demo)"></i>
                    <i class="fas fa-user-circle text-2xl cursor-pointer hover:text-[#FE2C55] transition"></i>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content Tabs -->
    <main class="pt-24 pb-12 px-4 max-w-7xl mx-auto">

        <!-- ==================== TAB 1: DOWNLOADER ==================== -->
        <div id="downloader" class="tab-content fade-in">
            <div class="glass-card p-6 md:p-8">
                <h1 class="text-3xl md:text-4xl font-bold mb-2">🚀 Download Any TikTok Content</h1>
                <p class="text-white/60 mb-8">No watermark, no limits. Supports video, story, live, and bulk mode.</p>
                
                <div class="flex flex-col md:flex-row gap-4">
                    <input type="text" id="videoUrl" placeholder="Paste TikTok URL (video, story, live, profile, hashtag)..." class="flex-1 bg-black/30 border border-white/20 rounded-xl px-5 py-3 focus:outline-none focus:border-[#FE2C55]">
                    <div class="flex gap-2">
                        <button id="downloadBtn" class="btn-primary px-6 py-3 rounded-xl font-semibold flex items-center gap-2"><i class="fas fa-download"></i> Download</button>
                        <button id="bulkBtn" class="bg-white/10 hover:bg-white/20 px-5 py-3 rounded-xl transition"><i class="fas fa-layer-group"></i> Bulk</button>
                    </div>
                </div>
                
                <!-- Format Selector -->
                <div class="mt-6 flex flex-wrap gap-4 items-center">
                    <span class="text-sm font-medium">Format:</span>
                    <label class="flex items-center gap-2"><input type="radio" name="format" value="mp4" checked class="accent-[#FE2C55]"> MP4 (Video + Audio)</label>
                    <label class="flex items-center gap-2"><input type="radio" name="format" value="mp3" class="accent-[#FE2C55]"> MP3 (Audio only)</label>
                    <label class="flex items-center gap-2"><input type="radio" name="format" value="hq" class="accent-[#FE2C55]"> 4K Ultra HD</label>
                </div>

                <!-- Results Panel -->
                <div id="downloadResult" class="mt-8 border-t border-white/10 pt-6 hidden"></div>

                <!-- Advanced Options -->
                <div class="mt-6 pt-4 border-t border-white/10 text-sm text-white/50 flex flex-wrap justify-between items-center">
                    <div><i class="fas fa-check-circle text-green-400"></i> No account required</div>
                    <div><i class="fas fa-infinity"></i> Unlimited downloads</div>
                    <div><i class="fas fa-history"></i> Download history saved</div>
                    <button id="clearHistory" class="text-red-400 hover:text-red-300 text-xs"><i class="fas fa-trash-alt"></i> Clear history</button>
                </div>
            </div>

            <!-- Recent History -->
            <div class="mt-8 glass-card p-6">
                <h3 class="text-xl font-semibold mb-4"><i class="fas fa-clock"></i> Recent Downloads</h3>
                <div id="historyList" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"></div>
            </div>
        </div>

        <!-- ==================== TAB 2: EDITOR ==================== -->
        <div id="editor" class="tab-content fade-in hidden">
            <div class="glass-card p-6 md:p-8">
                <h2 class="text-2xl font-bold mb-4"><i class="fas fa-cut"></i> Quick Video Editor</h2>
                <div class="grid md:grid-cols-2 gap-6">
                    <div>
                        <label class="block text-sm font-medium mb-2">Video URL or Upload</label>
                        <input type="text" id="editVideoUrl" placeholder="Paste downloaded video URL or select file" class="w-full bg-black/30 border border-white/20 rounded-xl px-4 py-2">
                        <input type="file" id="uploadVideo" accept="video/*" class="mt-3 w-full text-sm bg-black/30 border border-white/20 rounded-xl p-2">
                        <div class="mt-4 space-y-3">
                            <label class="flex items-center gap-3"><i class="fas fa-scissors w-6"></i> Trim (seconds): <input type="number" id="trimStart" placeholder="Start" class="w-20 bg-black/50 rounded px-2 py-1"> - <input type="number" id="trimEnd" placeholder="End" class="w-20 bg-black/50 rounded px-2 py-1"></label>
                            <label class="flex items-center gap-3"><i class="fas fa-crop-alt w-6"></i> Crop: <input type="text" id="crop" placeholder="x,y,width,height" class="flex-1 bg-black/50 rounded px-2 py-1"></label>
                            <label class="flex items-center gap-3"><i class="fas fa-font w-6"></i> Add Text: <input type="text" id="overlayText" placeholder="Your text here" class="flex-1 bg-black/50 rounded px-2 py-1"></label>
                            <label class="flex items-center gap-3"><i class="fas fa-chart-line w-6"></i> Progress Bar: <input type="text" id="progressText" placeholder="e.g., '🔥 Viral' " class="flex-1 bg-black/50 rounded px-2 py-1"></label>
                        </div>
                        <button id="applyEditsBtn" class="mt-5 w-full btn-primary py-2 rounded-xl font-semibold"><i class="fas fa-magic"></i> Apply & Export</button>
                    </div>
                    <div class="bg-black/40 rounded-xl p-3 flex flex-col items-center justify-center min-h-[200px]">
                        <video id="editorPreview" controls class="w-full rounded-lg max-h-60"></video>
                        <p id="editorStatus" class="text-xs text-white/50 mt-2">Preview will appear here</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- ==================== TAB 3: SCHEDULER ==================== -->
        <div id="scheduler" class="tab-content fade-in hidden">
            <div class="glass-card p-6 md:p-8">
                <h2 class="text-2xl font-bold mb-4"><i class="fas fa-calendar-alt"></i> Content Scheduler</h2>
                <div class="grid md:grid-cols-2 gap-6">
                    <div>
                        <input type="text" id="schedVideoUrl" placeholder="Video URL to schedule" class="w-full bg-black/30 border border-white/20 rounded-xl px-4 py-2 mb-3">
                        <input type="datetime-local" id="schedDateTime" class="w-full bg-black/30 border border-white/20 rounded-xl px-4 py-2 mb-3">
                        <textarea id="schedNote" placeholder="Notes / caption" rows="2" class="w-full bg-black/30 border border-white/20 rounded-xl px-4 py-2"></textarea>
                        <button id="addScheduleBtn" class="mt-4 w-full btn-primary py-2 rounded-xl"><i class="fas fa-plus-circle"></i> Schedule</button>
                    </div>
                    <div>
                        <h3 class="font-semibold mb-2">Upcoming Posts</h3>
                        <div id="scheduleList" class="space-y-2 max-h-64 overflow-y-auto"></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ==================== TAB 4: LIBRARY ==================== -->
        <div id="library" class="tab-content fade-in hidden">
            <div class="glass-card p-6">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-bold"><i class="fas fa-cloud-upload-alt"></i> My Cloud Library</h2>
                    <button id="refreshLibrary" class="text-sm bg-white/10 px-4 py-2 rounded-xl"><i class="fas fa-sync-alt"></i> Refresh</button>
                </div>
                <div id="libraryGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-5"></div>
                <p class="text-white/50 text-center text-sm mt-6">💾 Demo uses local storage – real cloud sync would connect to backend.</p>
            </div>
        </div>

        <!-- ==================== TAB 5: TRENDS ==================== -->
        <div id="trends" class="tab-content fade-in hidden">
            <div class="glass-card p-6">
                <h2 class="text-2xl font-bold mb-2"><i class="fas fa-chart-line"></i> Real‑time Trending</h2>
                <p class="text-white/60 mb-6">Top sounds, hashtags, and viral videos – updated daily.</p>
                <div id="trendsContainer" class="grid md:grid-cols-3 gap-6">
                    <!-- Simulated trends (would come from API in real deployment) -->
                    <div class="bg-white/5 p-4 rounded-xl"><i class="fas fa-music mr-2 text-[#FE2C55]"></i> <strong>Trending Sound:</strong> "Obsessed" by Olivia</div>
                    <div class="bg-white/5 p-4 rounded-xl"><i class="fas fa-hashtag mr-2 text-[#FE2C55]"></i> <strong>Hashtag:</strong> #SummerVibes (2.1M posts)</div>
                    <div class="bg-white/5 p-4 rounded-xl"><i class="fas fa-fire mr-2 text-[#FE2C55]"></i> <strong>Viral Video:</strong> 25M views – Dance challenge</div>
                </div>
            </div>
        </div>
    </main>

    <script>
        // ---------- Service Worker Registration (PWA) ----------
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('/sw.js').then(reg => console.log('✅ SW registered', reg)).catch(err => console.log('❌ SW failed', err));
        }

        // ---------- Global State ----------
        let downloadHistory = JSON.parse(localStorage.getItem('ultratik_history')) || [];
        let libraryItems = JSON.parse(localStorage.getItem('ultratik_library')) || [];
        let schedules = JSON.parse(localStorage.getItem('ultratik_schedules')) || [];

        // ---------- Utility Functions ----------
        function saveHistory() { localStorage.setItem('ultratik_history', JSON.stringify(downloadHistory)); renderHistory(); }
        function saveLibrary() { localStorage.setItem('ultratik_library', JSON.stringify(libraryItems)); renderLibrary(); }
        function saveSchedules() { localStorage.setItem('ultratik_schedules', JSON.stringify(schedules)); renderSchedules(); }

        // Format timestamp
        function formatDate(ts) { return new Date(ts).toLocaleString(); }

        // ---------- TAB SWITCHING ----------
        document.querySelectorAll('.tab-link').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const tabId = link.getAttribute('data-tab');
                document.querySelectorAll('.tab-content').forEach(tab => tab.classList.add('hidden'));
                document.getElementById(tabId).classList.remove('hidden');
            });
        });

        // ---------- TAB 1: DOWNLOAD LOGIC (Simulated) ----------
        function simulateDownload(url, format) {
            return new Promise((resolve) => {
                setTimeout(() => {
                    const fakeFile = {
                        id: Date.now(),
                        url: url,
                        format: format,
                        timestamp: Date.now(),
                        fileName: `tiktok_${Date.now()}.${format === 'mp3' ? 'mp3' : 'mp4'}`
                    };
                    downloadHistory.unshift(fakeFile);
                    if (downloadHistory.length > 20) downloadHistory.pop();
                    saveHistory();
                    // Simulate library save
                    libraryItems.unshift(fakeFile);
                    saveLibrary();
                    resolve(fakeFile);
                }, 1500);
            });
        }

        function renderHistory() {
            const container = document.getElementById('historyList');
            if (!container) return;
            if (downloadHistory.length === 0) { container.innerHTML = '<div class="col-span-full text-center text-white/40">No downloads yet</div>'; return; }
            container.innerHTML = downloadHistory.map(item => `
                <div class="bg-white/5 rounded-xl p-3 flex justify-between items-center">
                    <div class="truncate"><i class="fas fa-${item.format === 'mp3' ? 'music' : 'video'} mr-2"></i> ${item.fileName}</div>
                    <div class="text-xs text-white/40">${formatDate(item.timestamp)}</div>
                    <button class="text-sm text-[#25F4EE] hover:underline download-single" data-url="${item.url}" data-format="${item.format}"><i class="fas fa-download"></i></button>
                </div>
            `).join('');
            // Reattach events
            document.querySelectorAll('.download-single').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const url = btn.getAttribute('data-url');
                    const format = btn.getAttribute('data-format');
                    simulateDownload(url, format).then(() => alert('✅ Downloaded again!'));
                });
            });
        }

        document.getElementById('downloadBtn')?.addEventListener('click', async () => {
            const url = document.getElementById('videoUrl').value.trim();
            if (!url) return alert('Please paste a TikTok link');
            const format = document.querySelector('input[name="format"]:checked').value;
            const resultDiv = document.getElementById('downloadResult');
            resultDiv.classList.remove('hidden');
            resultDiv.innerHTML = '<div class="text-center py-6"><i class="fas fa-spinner fa-pulse text-2xl"></i> Processing...</div>';
            try {
                const file = await simulateDownload(url, format);
                resultDiv.innerHTML = `
                    <div class="bg-green-500/20 border border-green-400 rounded-xl p-4 flex justify-between items-center">
                        <div><i class="fas fa-check-circle text-green-400 mr-2"></i> Success! <strong>${file.fileName}</strong> saved to library.</div>
                        <button onclick="alert('In production, this would trigger actual file download.')" class="bg-white/20 px-4 py-1 rounded-full text-sm">Download</button>
                    </div>
                `;
            } catch(e) { resultDiv.innerHTML = '<div class="text-red-400">Error processing link</div>'; }
        });

        // Bulk mode alert (placeholder)
        document.getElementById('bulkBtn')?.addEventListener('click', () => alert('Bulk mode: paste multiple links separated by commas. Implemented via real backend.'));

        document.getElementById('clearHistory')?.addEventListener('click', () => { downloadHistory = []; saveHistory(); });

        // ---------- TAB 2: EDITOR ----------
        document.getElementById('uploadVideo')?.addEventListener('change', (e) => {
            const file = e.target.files[0];
            if (file) {
                const url = URL.createObjectURL(file);
                const video = document.getElementById('editorPreview');
                video.src = url;
                video.load();
            }
        });
        document.getElementById('editVideoUrl')?.addEventListener('input', (e) => {
            const video = document.getElementById('editorPreview');
            video.src = e.target.value;
            video.load();
        });
        document.getElementById('applyEditsBtn')?.addEventListener('click', () => {
            const trimStart = parseInt(document.getElementById('trimStart').value) || 0;
            const trimEnd = parseInt(document.getElementById('trimEnd').value);
            const crop = document.getElementById('crop').value;
            const text = document.getElementById('overlayText').value;
            const progress = document.getElementById('progressText').value;
            let message = `✨ Applied effects: trim ${trimStart}-${trimEnd || 'end'}, crop [${crop}], text "${text}", progress "${progress}".\nIn production, FFmpeg.wasm would export the final video.`;
            document.getElementById('editorStatus').innerText = message;
            alert(message);
        });

        // ---------- TAB 3: SCHEDULER ----------
        function renderSchedules() {
            const container = document.getElementById('scheduleList');
            if (!container) return;
            if (schedules.length === 0) { container.innerHTML = '<div class="text-white/40 text-center">No scheduled posts</div>'; return; }
            container.innerHTML = schedules.map((s, idx) => `
                <div class="bg-white/5 p-3 rounded-lg flex justify-between items-center">
                    <div class="text-sm"><i class="far fa-calendar-alt mr-2"></i> ${formatDate(s.datetime)}<br>${s.url.substring(0, 40)}...</div>
                    <button class="text-red-400 delete-sched" data-idx="${idx}"><i class="fas fa-trash-alt"></i></button>
                </div>
            `).join('');
            document.querySelectorAll('.delete-sched').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const idx = parseInt(btn.getAttribute('data-idx'));
                    schedules.splice(idx, 1);
                    saveSchedules();
                });
            });
        }

        document.getElementById('addScheduleBtn')?.addEventListener('click', () => {
            const url = document.getElementById('schedVideoUrl').value.trim();
            const datetime = document.getElementById('schedDateTime').value;
            const note = document.getElementById('schedNote').value;
            if (!url || !datetime) return alert('Please fill URL and date/time');
            schedules.push({ url, datetime: new Date(datetime).getTime(), note });
            saveSchedules();
            document.getElementById('schedVideoUrl').value = '';
            document.getElementById('schedNote').value = '';
            alert('✅ Scheduled!');
        });

        // ---------- TAB 4: LIBRARY ----------
        function renderLibrary() {
            const container = document.getElementById('libraryGrid');
            if (!container) return;
            if (libraryItems.length === 0) { container.innerHTML = '<div class="col-span-full text-center text-white/40">Your cloud library is empty. Download videos to see them here.</div>'; return; }
            container.innerHTML = libraryItems.map(item => `
                <div class="bg-white/5 rounded-xl p-3 text-center">
                    <i class="fas fa-${item.format === 'mp3' ? 'music' : 'video'} text-3xl mb-2 block"></i>
                    <div class="text-sm font-mono truncate">${item.fileName}</div>
                    <div class="text-xs text-white/40">${formatDate(item.timestamp)}</div>
                    <button class="mt-2 text-[#25F4EE] text-xs download-from-lib" data-url="${item.url}" data-format="${item.format}"><i class="fas fa-download"></i> Download again</button>
                </div>
            `).join('');
            document.querySelectorAll('.download-from-lib').forEach(btn => {
                btn.addEventListener('click', () => alert('Real download would start here.'));
            });
        }

        document.getElementById('refreshLibrary')?.addEventListener('click', () => renderLibrary());
        document.getElementById('cloudBackupBtn')?.addEventListener('click', () => alert('Cloud backup demo: would sync to real backend. Currently stored in localStorage.'));

        // Initial render
        renderHistory();
        renderLibrary();
        renderSchedules();

        // ---------- Simulated AI Smart Search (bonus) ----------
        const searchInput = document.createElement('input');
        searchInput.placeholder = '🔍 AI smart search (describe content)...';
        searchInput.className = 'mt-6 w-full bg-black/30 border border-white/20 rounded-xl px-5 py-3';
        document.querySelector('#downloader .glass-card').appendChild(searchInput);
        searchInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') alert(`🔎 AI search for "${searchInput.value}" would return relevant TikTok videos using external API.`);
        });
    </script>
    <!-- Minimal Service Worker for PWA -->
    <script>
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('/sw.js').catch(console.error);
            // Create a dummy sw.js if not exists (for demo)
            if (!localStorage.getItem('sw_created')) {
                const swCode = `self.addEventListener('fetch', event => { event.respondWith(fetch(event.request)); });`;
                localStorage.setItem('sw_created', 'true');
                console.log('Demo: Service Worker would be created in real deployment.');
            }
        }
    </script>
</body>
</html>
