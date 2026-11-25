# Web1
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GAME88 - Cấu Hình Được</title>
<style>
*{box-sizing:border-box;font-family:'Segoe UI',Arial}body{margin:0;background:#08080f;color:#fff}
.top{background:linear-gradient(90deg,#ff0055,#ff6a00,#ffd700);padding:12px 14px;display:flex;justify-content:space-between;align-items:center;position:sticky;top:0;z-index:20}
.top b{font-size:22px}.top .user{background:rgba(0,0,0,.35);padding:6px 12px;border-radius:20px}.top .user b{color:#ffd700;font-size:16px}
.banner{max-width:480px;margin:12px auto;background:linear-gradient(135deg,#1a0033,#ff0055);border:1px solid #ffaa00;border-radius:16px;padding:16px}
.banner h2{margin:0}.banner p{color:#ffe9a8}
.stats{max-width:480px;margin:0 auto;display:flex;gap:8px;padding:0 10px}
.stats div{flex:1;background:#1c1c2e;border:1px solid #2e2e4a;border-radius:12px;padding:10px;text-align:center}
.stats b{font-size:19px;color:#ffd700}
.tabs{max-width:480px;margin:12px auto;display:grid;grid-template-columns:repeat(5,1fr);gap:6px;padding:0 10px}
.tabs button{background:#1c1c2e;color:#fff;border:1px solid #2e2e4a;padding:10px 2px;border-radius:12px;font-weight:700;cursor:pointer;font-size:13px}
.tabs button.active{background:linear-gradient(90deg,#ff0055,#ffaa00)}
.card{max-width:480px;margin:0 auto 16px;background:#161626;border:1px solid #2e2e4a;border-radius:16px;padding:16px;display:none}
.card.active{display:block}
.slot{font-size:52px;background:#000;padding:14px;border-radius:12px;border:2px solid #ffd700;text-align:center}
.dice{font-size:42px;background:#000;padding:12px;border-radius:12px;text-align:center}
.baucua{display:flex;flex-wrap:wrap;gap:8px;justify-content:center}
.baucua span{background:#2a2a3d;padding:12px;border-radius:12px;cursor:pointer;font-size:22px;border:2px solid transparent}
.baucua span.sel{border-color:#ffd700;background:#3a2a00}
input,select{padding:10px;border-radius:10px;border:1px solid #444;background:#0f0f1a;color:#fff;width:100%;margin:5px 0}
label{font-size:13px;color:#aaa;display:block;margin-top:10px;text-align:left}
.btn{background:linear-gradient(90deg,#ffd700,#ffaa00);color:#000;border:none;padding:12px 18px;border-radius:25px;font-weight:900;cursor:pointer;width:100%;margin-top:10px}
.btn2{background:#2a2a3d;color:#fff;border:1px solid #444;padding:9px 12px;border-radius:20px;font-weight:700;cursor:pointer;margin:3px}
.btn2.active{background:#ff0055}
.win{color:#00ff88;font-weight:800}.lose{color:#ff5a5a;font-weight:800}
.history{font-size:13px;color:#bbb;text-align:left;max-height:110px;overflow:auto;background:#0f0f1a;padding:10px;border-radius:10px;margin-top:10px}
canvas{background:linear-gradient(#00bfff,#003a7a);border-radius:12px;border:3px solid #00c6ff;display:block;margin:8px auto;cursor:crosshair;touch-action:none;max-width:100%}
.row{display:flex;gap:8px}.row>*{flex:1}
.config-box{background:#0f0f1a;border:1px dashed #ffaa00;padding:12px;border-radius:12px;text-align:left}
</style>
</head>
<body>
<div class="top"><b id="logoText">🎰 GAME88</b><div class="user">👤 <span id="tenUser">Khách</span> | 💰 <b id="xu">0</b></div></div>
<div class="banner"><h2 id="bannerTitle">🐉 Săn Rồng Vàng - Ăn 5000 Xu!</h2><p id="bannerDesc">Chơi xu ảo, hết xu bấm nhận free. Tỉ lệ thắng chỉnh được trong Cấu Hình.</p></div>
<div class="stats"><div>💰 Ví<br><b id="xu2">0</b></div><div>🏆 Đã Thắng<br><b id="thang">0</b></div><div>📊 Ván<br><b id="van">0</b></div></div>
<div style="text-align:center;padding:10px"><button class="btn2" onclick="nhanXu()">+ NHẬN XU FREE</button> <button class="btn2" onclick="resetGame()">🔄 Reset</button></div>

<div class="tabs">
<button class="active" onclick="showTab('slot',this)">🎰 Quay Hũ</button>
<button onclick="showTab('taixiu',this)">🎲 Tài Xỉu</button>
<button onclick="showTab('baucua',this)">🦀 Bầu Cua</button>
<button onclick="showTab('banca',this)">🐟 Bắn Cá</button>
<button onclick="showTab('config',this)">⚙️ Cấu Hình</button>
</div>

<div id="slot" class="card active"><h2>🎰 QUAY HŨ</h2><div class="slot" id="slotShow">🍒 🍒 🍒</div><div class="row"><div><label>Cược</label><select id="slotBet"><option>100</option><option>500</option><option>1000</option><option>5000</option></select></div><div><label>Tỉ lệ hiện tại</label><input id="slotRateShow" readonly></div></div><button class="btn" onclick="quaySlot()">QUAY NGAY</button><p id="slotRes"></p><div class="history" id="hisSlot"></div></div>

<div id="taixiu" class="card"><h2>🎲 TÀI XỈU</h2><div class="dice" id="diceShow">🎲 🎲 🎲</div><div class="row"><div><label>Cược</label><select id="txBet"><option>100</option><option>500</option><option>1000</option><option>5000</option></select></div></div><button class="btn" onclick="choiTX('tai')">ĐẶT TÀI 🔼</button><button class="btn" style="background:#00c6ff" onclick="choiTX('xiu')">ĐẶT XỈU 🔽</button><p id="txRes"></p><div class="history" id="hisTX"></div></div>

<div id="baucua" class="card"><h2>🦀 BẦU CUA</h2><div class="baucua"><span onclick="chonBau('🦀',this)">🦀</span><span onclick="chonBau('🦐',this)">🦐</span><span onclick="chonBau('🐟',this)">🐟</span><span onclick="chonBau('🐓',this)">🐓</span><span onclick="chonBau('🦌',this)">🦌</span><span onclick="chonBau('🎃',this)">🎃</span></div><p>Đã chọn: <b id="daChon">Chưa chọn</b></p><label>Cược</label><select id="bcBet"><option>100</option><option>500</option><option>1000</option><option>5000</option></select><button class="btn" onclick="choiBauCua()">LẮC NGAY</button><p id="bcRes"></p><div class="dice" id="bcShow">❓ ❓ ❓</div><div class="history" id="hisBC"></div></div>

<div id="banca" class="card"><h2>🐟 BẮN CÁ</h2><p>🐟20 | 🐠30 | 🦐40 | 🦀60 | 🐙100 | 🦈200 | 🐳500 | 🐉5000</p><canvas id="game" width="400" height="420"></canvas><div style="text-align:center">Đạn: <button class="btn2 active" onclick="doiDan(10,this)">10</button><button class="btn2" onclick="doiDan(50,this)">50</button><button class="btn2" onclick="doiDan(100,this)">100</button><button class="btn2" onclick="doiDan(200,this)">200</button></div><p id="bcFishRes">Bấm vào cá để bắn!</p><div class="history" id="hisFish"></div></div>

<div id="config" class="card"><h2>⚙️ CẤU HÌNH HỆ THỐNG</h2><p style="font-size:13px;color:#aaa">Chỉnh xong bấm Lưu, nó tự áp dụng luôn, không cần sửa code.</p><div class="config-box">
<label>Tên Web</label><input id="cfgTen" value="GAME88">
<label>Xu tặng ban đầu</label><input type="number" id="cfgXuDau" value="1000">
<label>Xu tặng khi bấm Nhận Free</label><input type="number" id="cfgXuFree" value="500">
<label>Tỉ lệ thắng Quay Hũ (%) - 0 đến 100</label><input type="number" id="cfgSlot" value="35">
<label>Tỉ lệ thắng Tài Xỉu (%)</label><input type="number" id="cfgTX" value="48">
<label>Tỉ lệ thắng Bầu Cua (%)</label><input type="number" id="cfgBC" value="45">
<label>Ăn Jackpot Quay Hũ x mấy</label><input type="number" id="cfgJack" value="5">
<label>Tốc độ ra cá (giây) - càng nhỏ càng nhiều cá</label><input type="number" step="0.1" id="cfgCa" value="0.8">
<label>Màu chủ đạo</label><select id="cfgMau"><option value="do">Đỏ - Vàng (như XX88)</option><option value="xanh">Xanh Dương</option><option value="tim">Tím</option></select>
</div><button class="btn" onclick="luuConfig()">💾 LƯU CẤU HÌNH</button><p id="cfgRes"></p></div>

<script>
// ===== CẤU HÌNH MẶC ĐỊNH - M CHỈNH Ở TRANG CẤU HÌNH LÀ ĐƯỢC =====
let CFG = JSON.parse(localStorage.getItem('cfg88')||'{"ten":"GAME88","xuDau":1000,"xuFree":500,"slot":35,"tx":48,"bc":45,"jack":5,"ca":0.8,"mau":"do"}');
let xu = parseInt(localStorage.getItem('xu88cfg') ?? CFG.xuDau);
let thang=parseInt(localStorage.getItem('thang88cfg')||0), van=parseInt(localStorage.getItem('van88cfg')||0);
let chonConBau='', danGia=10;
function capNhat(){document.getElementById('xu').innerText=xu;document.getElementById('xu2').innerText=xu;document.getElementById('thang').innerText=thang;document.getElementById('van').innerText=van;document.getElementById('logoText').innerText='🎰 '+CFG.ten;document.getElementById('slotRateShow').value=CFG.slot+'% thắng';localStorage.setItem('xu88cfg',xu);localStorage.setItem('thang88cfg',thang);localStorage.setItem('van88cfg',van)}
function nhanXu(){xu+=CFG.xuFree;capNhat();alert('Đã +'+CFG.xuFree+' xu!')}
function resetGame(){if(confirm('Reset hết xu về ban đầu?')){xu=CFG.xuDau;thang=0;van=0;capNhat()}}
function showTab(id,btn){document.querySelectorAll('.card').forEach(e=>e.classList.remove('active'));document.querySelectorAll('.tabs button').forEach(e=>e.classList.remove('active'));document.getElementById(id).classList.add('active');btn.classList.add('active')}
function addHis(id,txt){document.getElementById(id).innerHTML='<div>'+txt+'</div>'+document.getElementById(id).innerHTML}
function luuConfig(){CFG={ten:document.getElementById('cfgTen').value,xuDau:+document.getElementById('cfgXuDau').value,xuFree:+document.getElementById('cfgXuFree').value,slot:+document.getElementById('cfgSlot').value,tx:+document.getElementById('cfgTX').value,bc:+document.getElementById('cfgBC').value,jack:+document.getElementById('cfgJack').value,ca:+document.getElementById('cfgCa').value,mau:document.getElementById('cfgMau').value};localStorage.setItem('cfg88',JSON.stringify(CFG));document.getElementById('cfgRes').innerHTML='<span class="win">Đã lưu! Tải lại trang để áp màu mới.</span>';capNhat();setTimeout(()=>location.reload(),800)}
function loadConfigToForm(){document.getElementById('cfgTen').value=CFG.ten;document.getElementById('cfgXuDau').value=CFG.xuDau;document.getElementById('cfgXuFree').value=CFG.xuFree;document.getElementById('cfgSlot').value=CFG.slot;document.getElementById('cfgTX').value=CFG.tx;document.getElementById('cfgBC').value=CFG.bc;document.getElementById('cfgJack').value=CFG.jack;document.getElementById('cfgCa').value=CFG.ca;document.getElementById('cfgMau').value=CFG.mau}
function quaySlot(){let bet=+document.getElementById('slotBet').value;if(bet>xu)return alert('Xu không đủ!');van++;let ic=['🍒','🍋','🍇','⭐','💎','7️⃣'];let thangGame=Math.random()*100<CFG.slot;let r;if(thangGame){let c=ic[Math.floor(Math.random()*6)];r=[c,c,c]}else{r=[ic[Math.floor(Math.random()*6)],ic[Math.floor(Math.random()*6)],ic[Math.floor(Math.random()*6)]]}document.getElementById('slotShow').innerText=r.join(' ');if(r[0]==r[1]&&r[1]==r[2]){let nhan=bet*CFG.jack;xu+=nhan;thang+=nhan;document.getElementById('slotRes').innerHTML='<span class="win">JACKPOT +'+nhan+'</span>';addHis('hisSlot','🎰 '+r.join('')+' +'+nhan)}else if(r[0]==r[1]||r[1]==r[2]||r[0]==r[2]){xu+=bet;thang+=bet;document.getElementById('slotRes').innerHTML='<span class="win">Trúng +'+bet+'</span>';addHis('hisSlot','🎰 '+r.join('')+' +'+bet)}else{xu-=bet;document.getElementById('slotRes').innerHTML='<span class="lose">Hụt -'+bet+'</span>';addHis('hisSlot','🎰 '+r.join('')+' -'+bet)}capNhat()}
function choiTX(chon){let bet=+document.getElementById('txBet').value;if(bet>xu)return alert('Xu không đủ!');van++;let thangGame=Math.random()*100<CFG.tx;let d;if(thangGame){do{d=[1+Math.floor(Math.random()*6),1+Math.floor(Math.random()*6),1+Math.floor(Math.random()*6)]}while(!((chon=='tai'&&d[0]+d[1]+d[2]>=11&&d[0]+d[1]+d[2]<=17)||(chon=='xiu'&&d[0]+d[1]+d[2]>=4&&d[0]+d[1]+d[2]<=10)))}else{d=[1+Math.floor(Math.random()*6),1+Math.floor(Math.random()*6),1+Math.floor(Math.random()*6)]}let tong=d[0]+d[1]+d[2];document.getElementById('diceShow').innerText=d.join(' - ')+' = '+tong;let kq=tong>=11?'tai':'xiu';if(chon==kq){xu+=bet;thang+=bet;document.getElementById('txRes').innerHTML='<span class="win">Thắng +'+bet+' - Ra '+(kq=='tai'?'TÀI':'XỈU')+'</span>';addHis('hisTX','🎲 '+tong+' +'+bet)}else{xu-=bet;document.getElementById('txRes').innerHTML='<span class="lose">Thua -'+bet+' - Ra '+(kq=='tai'?'TÀI':'XỈU')+'</span>';addHis('hisTX','🎲 '+tong+' -'+bet)}capNhat()}
function chonBau(ic,el){chonConBau=ic;document.querySelectorAll('.baucua span').forEach(e=>e.classList.remove('sel'));el.classList.add('sel');document.getElementById('daChon').innerText=ic}
function choiBauCua(){if(!chonConBau)return alert('Chọn 1 con!');let bet=+document.getElementById('bcBet').value;if(bet>xu)return alert('Xu không đủ!');van++;let ic=['🦀','🦐','🐟','🐓','🦌','🎃'];let thangGame=Math.random()*100<CFG.bc;let r;if(thangGame){r=[chonConBau,ic[Math.floor(Math.random()*6)],ic[Math.floor(Math.random()*6)]]}else{do{r=[ic[Math.floor(Math.random()*6)],ic[Math.floor(Math.random()*6)],ic[Math.floor(Math.random()*6)]]}while(r.includes(chonConBau))}document.getElementById('bcShow').innerText=r.join(' ');let dem=r.filter(x=>x==chonConBau).length;if(dem>0){xu+=bet*dem;thang+=bet*dem;document.getElementById('bcRes').innerHTML='<span class="win">Trúng '+dem+' con +'+bet*dem+'</span>';addHis('hisBC','🦀 '+r.join('')+' +'+bet*dem)}else{xu-=bet;document.getElementById('bcRes').innerHTML='<span class="lose">Hụt -'+bet+'</span>';addHis('hisBC','🦀 '+r.join('')+' -'+bet)}capNhat()}
// BẮN CÁ
let canvas=document.getElementById('game'),ctx=canvas.getContext('2d'),fishes=[],bullets=[],particles=[];
let loaiCa=[{icon:'🐟',toc:1.3,gia:20,hp:2},{icon:'🐠',toc:1.7,gia:30,hp:3},{icon:'🦐',toc:2.1,gia:40,hp:4},{icon:'🦀',toc:1,gia:60,hp:6},{icon:'🐙',toc:0.9,gia:100,hp:10},{icon:'🦈',toc:1.5,gia:200,hp:18},{icon:'🐳',toc:0.6,gia:500,hp:35},{icon:'🐉',toc:0.8,gia:5000,hp:80}];
function doiDan(g,btn){danGia=g;document.querySelectorAll('#banca .btn2').forEach(b=>b.classList.remove('active'));btn.classList.add('active')}
function taoCa(){let loai=loaiCa[Math.floor(Math.random()*loaiCa.length)];let trai=Math.random()>0.5;fishes.push({x:trai?-40:canvas.width+40,y:40+Math.random()*300,toc:loai.toc*(trai?1:-1),icon:loai.icon,gia:loai.gia,hp:loai.hp,size:26+loai.gia/12})}
setInterval(()=>taoCa(),CFG.ca*1000);
function ban(x,y){if(xu<danGia){document.getElementById('bcFishRes').innerText='Hết xu! Bấm nhận free!';return} xu-=danGia;van++;capNhat();bullets.push({x:canvas.width/2,y:canvas.height-10,tx:x,ty:y})}
canvas.addEventListener('click',e=>{let r=canvas.getBoundingClientRect();ban(e.clientX-r.left,e.clientY-r.top)});
canvas.addEventListener('touchstart',e=>{e.preventDefault();let r=canvas.getBoundingClientRect();let t=e.touches[0];ban(t.clientX-r.left,t.clientY-r.top)},{passive:false});
function ve(){ctx.clearRect(0,0,canvas.width,canvas.height);ctx.font='36px Arial';ctx.textAlign='center';ctx.fillText('🔫',canvas.width/2,canvas.height-4);fishes.forEach(f=>{ctx.font=(f.size||30)+'px Arial';ctx.fillText(f.icon,f.x,f.y)});ctx.fillStyle='#ffd700';bullets.forEach(b=>{ctx.beginPath();ctx.arc(b.x,b.y,6,0,Math.PI*2);ctx.fill()});particles.forEach(p=>{ctx.font='bold 18px Arial';ctx.fillStyle='#ffd700';ctx.fillText(p.text,p.x,p.y)});requestAnimationFrame(ve);fishes.forEach(f=>f.x+=f.toc);fishes=fishes.filter(f=>f.x>-60&&f.x<canvas.width+60);bullets.forEach(b=>{b.x+=(b.tx-canvas.width/2)*0.07;b.y+=(b.ty-(canvas.height-10))*0.07;fishes.forEach((f,i)=>{if(Math.abs(b.x-f.x)<28&&Math.abs(b.y-f.y)<28){f.hp-=danGia/10;if(f.hp<=0){xu+=f.gia;thang+=f.gia;particles.push({text:'+'+f.gia,x:f.x,y:f.y});document.getElementById('bcFishRes').innerHTML='<span class="win">Trúng '+f.icon+' +'+f.gia+'</span>';addHis('hisFish',f.icon+' +'+f.gia);fishes.splice(i,1);capNhat()}b.dead=true}})});bullets=bullets.filter(b=>!b.dead&&b.y>0&&b.y<canvas.height);particles.forEach(p=>p.y-=1.2);particles=particles.filter(p=>p.y>0)}ve();
loadConfigToForm();capNhat();
</script>
</body>
</html>
