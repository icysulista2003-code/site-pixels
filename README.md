<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Píxeis à Venda — MVP</title>
  <style>
    :root{
      --bg:#f7f7f9; --card:#fff; --accent:#111827; --muted:#6b7280;
      --max-width:1200px;
    }
    *{box-sizing:border-box}
    body{font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; margin:0; background:var(--bg); color:var(--accent)}
    header{background:#fff;border-bottom:1px solid #e6e6e9;padding:18px 20px;display:flex;align-items:center;justify-content:space-between}
    header h1{font-size:18px;margin:0}
    main{max-width:var(--max-width);margin:28px auto;padding:0 20px;display:grid;grid-template-columns:1fr 340px;gap:20px}
    .canvas-card{background:var(--card);border-radius:12px;padding:12px;box-shadow:0 6px 18px rgba(15,23,42,0.06)}
    #board-wrap{width:100%;height:calc(100vh - 180px);display:flex;align-items:center;justify-content:center;}
    canvas{background:#fff;border:1px solid #ddd;image-rendering:pixelated;max-width:100%;height:auto;border-radius:6px}

    .controls{position:sticky;top:28px;background:var(--card);padding:16px;border-radius:12px;box-shadow:0 6px 18px rgba(15,23,42,0.04)}
    .controls h2{margin:0 0 10px 0;font-size:16px}
    .row{display:flex;gap:8px;align-items:center;margin-bottom:10px}
    label{font-size:13px;color:var(--muted)}
    input[type="number"], select, input[type="text"], input[type="color"]{width:100%;padding:8px;border-radius:8px;border:1px solid #e4e4e7;background:#fff}
    button{padding:10px 12px;border-radius:10px;border:0;background:#111827;color:#fff;font-weight:600;cursor:pointer}
    .ghost{background:transparent;color:var(--accent);border:1px solid #ddd}
    footer{max-width:var(--max-width);margin:20px auto;padding:12px 20px;color:var(--muted);font-size:13px}

    /* modal */
    .modal{position:fixed;left:0;top:0;width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,0.45);}
    .modal .box{background:#fff;padding:18px;border-radius:12px;width:420px;max-width:92%}
    .small{font-size:12px;color:var(--muted)}
    .pill{font-size:12px;padding:6px 8px;border-radius:999px;background:#f1f5f9;color:#0f172a;display:inline-block}
    .export{background:#0ea5e9}
    @media (max-width:920px){main{grid-template-columns:1fr}}    
  </style>
</head>
<body>
  <header>
    <h1>Píxeis à Venda — R$ 1 / pixel (MVP)</h1>
    <nav>
      <a href="#">Home</a>
    </nav>
  </header>

  <main>
    <section class="canvas-card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
        <div>
          <strong>Quadro de pixels</strong>
          <div class="small">Clique em um pixel para selecionar. Pixels já comprados aparecem coloridos.</div>
        </div>
        <div class="small pill">MVP: salva no seu navegador (localStorage)</div>
      </div>

      <div id="board-wrap">
        <canvas id="board" width="1200" height="1200"></canvas>
      </div>
    </section>

    <aside class="controls">
      <h2>Controles & Compra</h2>
      <div class="row">
        <div style="flex:1">
          <label>Preço por pixel</label>
          <input id="price" type="number" value="1" min="0" />
        </div>
      </div>

      <div class="row">
        <div style="flex:1">
          <label>Tamanho do grid (colunas)</label>
          <input id="gridW" type="number" value="200" min="10" />
        </div>
        <div style="width:100px">
          <label>linhas</label>
          <input id="gridH" type="number" value="200" min="10" />
        </div>
      </div>

      <div class="row">
        <div style="flex:1">
          <label>Tamanho visual do pixel (px)</label>
          <input id="tileSize" type="number" value="4" min="1" />
        </div>
      </div>

      <div style="height:12px"></div>
      <div class="row">
        <div style="flex:1">
          <label>Cor selecionada</label>
          <input id="color" type="color" value="#ff0000" />
        </div>
      </div>

      <div class="row">
        <div style="flex:1">
          <label>Pixel selecionado</label>
          <input id="selInfo" type="text" readonly placeholder="Nenhum" />
        </div>
      </div>

      <div class="row">
        <button id="buyBtn">Comprar este pixel</button>
        <button id="clearLocal" class="ghost">Limpar vendas (local)</button>
      </div>

      <div style="height:10px"></div>
      <div style="display:flex;gap:8px">
        <button id="exportBtn" class="export">Exportar pedidos (JSON)</button>
        <button id="adminBtn" class="ghost">Abrir painel admin</button>
      </div>

      <hr style="margin:12px 0" />
      <div class="small">Dicas:
        <ul style="margin:8px 0;padding-left:18px">
          <li>Aqui o estado é salvo apenas no seu navegador (localStorage) — para venda real, você precisa de um servidor / DB + integração de pagamentos (Stripe, MercadoPago, Pix).</li>
          <li>Use o botão Exportar para baixar os pedidos e processar pagamentos manualmente enquanto integra um gateway.</li>
        </ul>
      </div>
    </aside>
  </main>

  <footer>
    Este é um MVP: personalize o código para ajustar tamanho do grid, preço e integração com pagamento. Posso te ajudar a colocar Stripe + Firebase se quiser.
  </footer>

  <!-- modal de compra -->
  <div id="modal" style="display:none" class="modal" aria-hidden="true">
    <div class="box">
      <h3>Comprar pixel</h3>
      <div class="small" id="modalPixel"></div>
      <div style="margin-top:10px">
        <label>Nome (ex: marca)</label>
        <input id="buyerName" type="text" placeholder="Seu nome ou empresa" />
      </div>
      <div style="margin-top:8px">
        <label>URL (link que será associado ao pixel)</label>
        <input id="buyerUrl" type="text" placeholder="https://seusite.com" />
      </div>
      <div style="margin-top:12px;display:flex;gap:8px;justify-content:flex-end">
        <button id="cancelBuy" class="ghost">Cancelar</button>
        <button id="confirmBuy">Simular pagamento e confirmar</button>
      </div>
      <p class="small" style="margin-top:8px">Observação: este botão apenas simula o pagamento (marca o pixel como vendido no seu navegador). Para pagamentos reais, você deve integrar um gateway e validar via servidor/webhook.</p>
    </div>
  </div>

  <!-- painel admin (simples) -->
  <div id="adminPanel" style="display:none" class="modal" aria-hidden="true">
    <div class="box">
      <h3>Painel Admin</h3>
      <div class="small" id="ordersList" style="max-height:340px;overflow:auto;margin-top:8px"></div>
      <div style="margin-top:8px;display:flex;gap:8px;justify-content:flex-end">
        <button id="closeAdmin" class="ghost">Fechar</button>
      </div>
    </div>
  </div>

  <script>
    // =====================
    // Config (edite antes de usar)
    // =====================
    const STORAGE_KEY = 'pixel_sales_v1';

    // Carregamento inicial e controle da UI
    const canvas = document.getElementById('board');
    const ctx = canvas.getContext('2d');

    const gridWInput = document.getElementById('gridW');
    const gridHInput = document.getElementById('gridH');
    const tileSizeInput = document.getElementById('tileSize');
    const priceInput = document.getElementById('price');
    const colorInput = document.getElementById('color');
    const selInfo = document.getElementById('selInfo');

    const buyBtn = document.getElementById('buyBtn');
    const modal = document.getElementById('modal');
    const modalPixel = document.getElementById('modalPixel');
    const confirmBuy = document.getElementById('confirmBuy');
    const cancelBuy = document.getElementById('cancelBuy');
    const buyerName = document.getElementById('buyerName');
    const buyerUrl = document.getElementById('buyerUrl');

    const exportBtn = document.getElementById('exportBtn');
    const clearLocal = document.getElementById('clearLocal');
    const adminBtn = document.getElementById('adminBtn');
    const adminPanel = document.getElementById('adminPanel');
    const ordersList = document.getElementById('ordersList');
    const closeAdmin = document.getElementById('closeAdmin');

    let GRID_W = parseInt(gridWInput.value,10);
    let GRID_H = parseInt(gridHInput.value,10);
    let TILE = parseInt(tileSizeInput.value,10);
    let PRICE = parseFloat(priceInput.value);

    let pixels = {}; // mapa "x_y" => {color,name,url,paid,ts}
    let selected = null;

    function resizeCanvas(){
      canvas.width = GRID_W * TILE;
      canvas.height = GRID_H * TILE;
      canvas.style.width = Math.min(canvas.width, 960) + 'px';
      canvas.style.height = (canvas.height * (parseInt(canvas.style.width) / canvas.width)) + 'px';
    }

    function loadState(){
      try{
        const raw = localStorage.getItem(STORAGE_KEY);
        pixels = raw ? JSON.parse(raw) : {};
      }catch(e){pixels={}};
    }

    function saveState(){
      localStorage.setItem(STORAGE_KEY, JSON.stringify(pixels));
    }

    function draw(){
      // clear
      ctx.clearRect(0,0,canvas.width,canvas.height);
      // white background
      ctx.fillStyle = '#ffffff';
      ctx.fillRect(0,0,canvas.width,canvas.height);

      // draw sold pixels
      for(const key in pixels){
        const [x,y] = key.split('_').map(Number);
        const p = pixels[key];
        ctx.fillStyle = p.color || '#000';
        ctx.fillRect(x*TILE, y*TILE, TILE, TILE);
      }

      // selection highlight
      if(selected){
        ctx.strokeStyle = '#000';
        ctx.lineWidth = 1;
        ctx.strokeRect(selected.x*TILE+0.5, selected.y*TILE+0.5, TILE-1, TILE-1);
      }

      // optional faint grid when tile big enough
      if(TILE >= 6){
        ctx.strokeStyle = 'rgba(0,0,0,0.06)';
        ctx.lineWidth = 0.5;
        for(let x=0;x<=GRID_W;x++) ctx.strokeRect(x*TILE,0,0,canvas.height);
        for(let y=0;y<=GRID_H;y++) ctx.strokeRect(0,y*TILE,canvas.width,0);
      }
    }

    // map mouse event to grid coord
    function clientToGrid(evt){
      const rect = canvas.getBoundingClientRect();
      const scaleX = canvas.width / rect.width;
      const scaleY = canvas.height / rect.height;
      const cx = (evt.clientX - rect.left) * scaleX;
      const cy = (evt.clientY - rect.top) * scaleY;
      const gx = Math.floor(cx / TILE);
      const gy = Math.floor(cy / TILE);
      return {x: Math.max(0, Math.min(GRID_W-1,gx)), y: Math.max(0, Math.min(GRID_H-1,gy))};
    }

    canvas.addEventListener('click', (e)=>{
      const g = clientToGrid(e);
      selected = g;
      selInfo.value = g.x + ' , ' + g.y;
      draw();
    });

    buyBtn.addEventListener('click', ()=>{
      if(!selected){ alert('Selecione um pixel antes.'); return; }
      modalPixel.textContent = `Pixel: ${selected.x}, ${selected.y} — Preço: R$ ${PRICE.toFixed(2)}`;
      buyerName.value = '';
      buyerUrl.value = '';
      modal.style.display = 'flex';
    });

    cancelBuy.addEventListener('click', ()=>{ modal.style.display='none'; });

    confirmBuy.addEventListener('click', ()=>{
      const key = selected.x + '_' + selected.y;
      if(pixels[key] && pixels[key].paid){ alert('Pixel já comprado.'); modal.style.display='none'; return; }
      // simulação de pagamento: marcar como vendido
      pixels[key] = {
        color: colorInput.value,
        name: buyerName.value || 'Comprador anônimo',
        url: buyerUrl.value || '',
        paid: true,
        ts: Date.now()
      };
      saveState();
      modal.style.display='none';
      draw();
      alert('Pagamento simulado: pixel marcado como vendido (salvo localmente). Para vendas reais, integre um gateway e um DB.');
    });

    exportBtn.addEventListener('click', ()=>{
      const data = {meta:{gridW:GRID_W,gridH:GRID_H,price:PRICE}, orders: pixels};
      const blob = new Blob([JSON.stringify(data, null, 2)], {type:'application/json'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url; a.download = 'pixel-orders.json';
      a.click();
      URL.revokeObjectURL(url);
    });

    clearLocal.addEventListener('click', ()=>{
      if(confirm('Tem certeza? Isso limpará todas as vendas salvas no seu navegador.')){
        pixels = {};
        saveState();
        draw();
      }
    });

    // admin panel (local)
    adminBtn.addEventListener('click', ()=>{
      // pedir senha simples (MVP)
      const p = prompt('Senha admin (MVP):');
      if(p !== 'admin123') { alert('Senha incorreta.'); return; }
      ordersList.innerHTML = '';
      const keys = Object.keys(pixels).sort((a,b)=>pixels[a].ts - pixels[b].ts);
      if(keys.length===0) ordersList.innerHTML = '<div class="small">Nenhum pedido</div>';
      for(const k of keys){
        const it = pixels[k];
        const el = document.createElement('div');
        el.style.padding='8px'; el.style.borderBottom='1px solid #f2f2f4';
        el.innerHTML = `<strong>${k}</strong> — ${it.name} — ${it.url || '-'} <div class='small'>${new Date(it.ts).toLocaleString()}</div>`;
        ordersList.appendChild(el);
      }
      adminPanel.style.display='flex';
    });
    closeAdmin.addEventListener('click', ()=>{ adminPanel.style.display='none'; });

    // atualizar configuração (recria canvas size)
    function applyConfig(){
      GRID_W = parseInt(gridWInput.value,10);
      GRID_H = parseInt(gridHInput.value,10);
      TILE = parseInt(tileSizeInput.value,10);
      PRICE = parseFloat(priceInput.value);
      resizeCanvas();
      draw();
    }

    gridWInput.addEventListener('change', applyConfig);
    gridHInput.addEventListener('change', applyConfig);
    tileSizeInput.addEventListener('change', applyConfig);
    priceInput.addEventListener('change', ()=>{PRICE=parseFloat(priceInput.value)});

    colorInput.addEventListener('change', ()=>{ if(selected){ draw(); }});

    // inicialização
    loadState();
    applyConfig();

    // instruções no console para desenvolvedor
    console.log('MVP pronto — personalize GRID_W, GRID_H, TILE e integre um gateway de pagamento (Stripe, MercadoPago) e um DB (Firebase, Supabase) para produção.');

  </script>
</body>
</html>
