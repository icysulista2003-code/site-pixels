🌟 Compre um Pixel, Marque sua História 🌟
Cada pixel aqui é muito mais que um ponto colorido na tela. Ele é um espaço único, eterno, que carrega a sua marca, a sua mensagem ou a sua lembrança.

Ao comprar um pixel, você está:
Deixando um pedaço seu no mundo – sua marca, seu nome ou até uma memória especial ficará visível para todos que visitarem.
Participando de algo maior – este mural é coletivo, feito por centenas de pessoas diferentes, cada uma contando sua própria história.
Apoiando um projeto criativo – sua compra ajuda a manter vivo este espaço, e você se torna parte de uma comunidade única.
Seja um anúncio, uma homenagem, uma arte ou apenas um recado engraçado… seu pixel é seu espaço no mural digital que nunca será apagado.
Não é só um pixel. É a sua presença. É o seu legado.
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>PixelMarket — Compre um pedacinho da tela</title>
  <style>
    :root{
      --bg:#0f1115;--panel:#151923;--muted:#8188a1;--text:#e6e9f2;--brand:#6ee7ff;--accent:#7c3aed;--ok:#10b981;--warn:#f59e0b;--err:#ef4444;
      --grid-cols:100; /* 100 x 100 blocos => 10.000 blocos; cada bloco representa 10x10 pixels => 1.000.000 px */
      --cell-gap:2px; --cell-size: min(10vw, 16px);
    }
    *{box-sizing:border-box}
    body{margin:0;background:linear-gradient(180deg,#0b0d12,#0f1115 30%);color:var(--text);font-family:Inter,system-ui,Segoe UI,Roboto,Helvetica,Arial,sans-serif;}
    header{position:sticky;top:0;z-index:30;backdrop-filter:saturate(1.1) blur(6px);background:rgba(15,17,21,.7);border-bottom:1px solid #23283a}
    .wrap{max-width:1200px;margin:0 auto;padding:16px}
    .row{display:flex;gap:16px;align-items:center;flex-wrap:wrap}
    .brand{font-weight:800;letter-spacing:.3px}
    .chip{display:inline-flex;gap:8px;align-items:center;padding:8px 12px;border:1px solid #2a3146;border-radius:999px;background:#121521}
    .chip input{width:90px;background:transparent;color:var(--text);border:none;outline:none;text-align:right}
    .btn{padding:10px 14px;border-radius:14px;border:1px solid #2a3146;background:#141826;color:var(--text);cursor:pointer}
    .btn:hover{border-color:#3a4261}
    .btn.primary{background:linear-gradient(135deg,#1f2937,#1b2234);border-color:#3b82f6}
    .btn.ghost{background:transparent}
    .btn.warn{border-color:var(--warn)}
    .btn.ok{border-color:var(--ok)}
    .btn.err{border-color:var(--err)}

    main{display:grid;grid-template-columns:1fr 330px;gap:18px;margin-top:16px}
    @media (max-width: 980px){main{grid-template-columns:1fr}}

    .board{background:var(--panel);border:1px solid #23283a;border-radius:18px;padding:14px}
    .grid{display:grid;grid-template-columns:repeat(var(--grid-cols), minmax(0,1fr));gap:var(--cell-gap);user-select:none}
    .cell{width:100%;aspect-ratio:1;border-radius:4px;background:#0e1320;border:1px solid #1f2436;position:relative;overflow:hidden;cursor:pointer}
    .cell:hover{outline:2px solid #44538055}
    .cell.sold{background:#0b1020;border-color:#343b55;cursor:not-allowed}
    .cell .thumb{position:absolute;inset:0;background-size:cover;background-position:center;filter:saturate(1.05)}
    .cell .overlay{position:absolute;inset:0;background:linear-gradient(0deg, #0008, #0000);opacity:0;transition:opacity .15s}
    .cell:hover .overlay{opacity:1}
    .cell .meta{position:absolute;bottom:2px;left:2px;right:2px;font-size:10px;color:#d1d7ffb0;text-shadow:0 1px 2px #000}

    .side{background:var(--panel);border:1px solid #23283a;border-radius:18px;padding:14px;position:sticky;top:72px;align-self:start}
    .side h3{margin:0 0 12px 0}
    .muted{color:var(--muted)}
    .list{display:grid;gap:8px;max-height:50vh;overflow:auto;padding-right:4px}
    .item{display:flex;gap:8px;align-items:center;justify-content:space-between;padding:8px;border:1px solid #2a3146;border-radius:12px;background:#0f1320}
    .item strong{font-size:13px}

    .legend{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:10px}
    .pill{padding:6px 10px;border-radius:999px;border:1px solid #2a3146;background:#0f1320;font-size:12px}
    .pill.sold{border-color:#3b4260;color:#96a0cc}

    .modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(5,7,10,.65);z-index:50}
    .modal.open{display:flex}
    .card{width:min(520px,94vw);background:#0f1320;border:1px solid #2a3146;border-radius:18px;padding:16px}
    .card h3{margin:0 0 8px}
    .field{display:grid;gap:6px;margin:10px 0}
    .field input,.field textarea{padding:10px;border-radius:12px;border:1px solid #2a3146;background:#0c101a;color:var(--text)}
    .grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
    .hint{font-size:12px;color:#a6acc8}
    .preview{height:120px;border-radius:12px;border:1px dashed #2a3146;background:#0c101a;display:grid;place-items:center;overflow:hidden}
    .preview img{max-width:100%;max-height:100%;display:block}

    .adm{margin-top:10px;padding-top:10px;border-top:1px dashed #2a3146}
    .footer{margin-top:10px;color:#8a90a8;font-size:12px}
  </style>
</head>
<body>
  <header>
    <div class="wrap row">
      <div class="row" style="gap:10px;align-items:center">
        <span class="brand">🧊 PixelMarket</span>
        <span class="pill">1.000.000 px (10.000 blocos)</span>
        <span class="pill sold" id="sold-pill">Disponíveis: —</span>
      </div>
      <div class="row" style="margin-left:auto">
        <span class="chip">R$ por pixel
          <input type="number" min="0" step="0.01" id="pricePerPixel" />
        </span>
        <button class="btn" id="exportBtn">Exportar</button>
        <button class="btn" id="importBtn">Importar</button>
        <button class="btn" id="adminBtn">Modo Admin</button>
        <button class="btn primary" id="checkoutBtn">Finalizar compra</button>
      </div>
    </div>
  </header>

  <div class="wrap">
    <main>
      <section class="board">
        <div class="legend">
          <span class="pill">Clique para selecionar blocos (cada bloco = 10x10 px)</span>
          <span class="pill">Ctrl/Cmd + clique para múltiplos</span>
          <span class="pill">Dê duplo clique num bloco comprado para abrir o link</span>
        </div>
        <div class="grid" id="grid"></div>
      </section>

      <aside class="side">
        <h3>Seu carrinho</h3>
        <div class="muted" id="cartInfo">Nenhum bloco selecionado.</div>
        <div class="list" id="cartList"></div>
        <hr style="border-color:#23283a;border-width:1px;margin:12px 0" />
        <div class="row" style="justify-content:space-between">
          <strong>Total</strong>
          <strong id="totalLabel">R$ 0,00</strong>
        </div>
        <button class="btn ok" style="width:100%;margin-top:10px" id="openDesignBtn">Definir arte/infos</button>
        <div class="footer">
          Pagamentos podem ser feitos por PIX/Stripe manualmente. Após confirmar, o admin aprova e bloqueia os blocos.
        </div>
        <div class="adm" id="adminPanel" style="display:none">
          <h3>Admin</h3>
          <div class="field">
            <label>Senha do admin</label>
            <input type="password" id="adminPass" placeholder="digite a senha" />
          </div>
          <div class="row" style="gap:8px">
            <button class="btn ok" id="authBtn">Entrar</button>
            <button class="btn warn" id="lockBtn" disabled>Marcar como pago (bloquear)</button>
            <button class="btn err" id="unlockBtn" disabled>Desbloquear</button>
          </div>
          <div class="hint">Padrão: <code>admin123</code>. Altere no código antes de publicar.</div>
        </div>
      </aside>
    </main>
  </div>

  <!-- Modal de design/compra -->
  <div class="modal" id="designModal">
    <div class="card">
      <h3>Configurar arte do(s) bloco(s)</h3>
      <div class="grid2">
        <div>
          <div class="field">
            <label>Título (tooltip)</label>
            <input type="text" id="titleInput" placeholder="Ex: Minha marca" />
          </div>
          <div class="field">
            <label>Link (abre ao clicar)</label>
            <input type="url" id="urlInput" placeholder="https://..." />
          </div>
          <div class="field">
            <label>Cor de fundo</label>
            <input type="color" id="colorInput" value="#2dd4bf" />
          </div>
          <div class="field">
            <label>Imagem (opcional)</label>
            <input type="file" id="imgInput" accept="image/*" />
            <div class="hint">Imagens são redimensionadas para caber no bloco.</div>
          </div>
        </div>
        <div>
          <div class="preview" id="imgPreview">Pré-visualização</div>
          <div class="field">
            <label>Aplicar aos blocos selecionados</label>
            <button class="btn ok" id="applyDesignBtn">Aplicar</button>
          </div>
        </div>
      </div>
      <div class="row" style="justify-content:flex-end;gap:8px">
        <button class="btn ghost" id="closeDesign">Fechar</button>
      </div>
    </div>
  </div>

  <script>
    /****************************
     * Configurações básicas
     ****************************/
    const GRID_COLS = 100; // 100 x 100 blocos
    const GRID_ROWS = 100;
    const ADMIN_PASSWORD = 'admin555@r!'; // ALTERE isto antes de publicar
    const DEFAULT_PRICE_PER_PIXEL = 1.0; // R$ por pixel. Cada bloco tem 100 px.

    /****************************
     * Estado
     ****************************/
    const state = {
      pricePerPixel: parseFloat(localStorage.getItem('pricePerPixel')) || DEFAULT_PRICE_PER_PIXEL,
      blocks: {}, // key "r,c" => { sold, title, url, color, imgData }
      cart: new Set(),
      adminAuthed: false
    };

    // Carregar estado salvo
    try{
      const saved = JSON.parse(localStorage.getItem('pixelMarketBlocks')||'{}');
      if(saved && typeof saved === 'object') state.blocks = saved;
    }catch(e){ console.warn('Sem estado salvo'); }

    /****************************
     * Helpers
     ****************************/
    const fmtBRL = (n)=> n.toLocaleString('pt-BR',{style:'currency',currency:'BRL'});
    const blockKey = (r,c)=> `${r},${c}`;
    const pricePerBlock = ()=> state.pricePerPixel * 100; // 10x10 px por bloco

    function updateAvailableCount(){
      const total = GRID_COLS * GRID_ROWS;
      const sold = Object.values(state.blocks).filter(b=>b.sold).length;
      const available = total - sold;
      document.getElementById('sold-pill').textContent = `Disponíveis: ${available} / ${total}`;
    }

    function save(){
      localStorage.setItem('pixelRealBlocks', JSON.stringify(state.blocks));
      localStorage.setItem('pricePerPixel', String(state.pricePerPixel));
    }

    /****************************
     * Montar grade
     ****************************/
    const gridEl = document.getElementById('grid');
    gridEl.style.setProperty('--grid-cols', GRID_COLS);

    for(let r=0;r<GRID_ROWS;r++){
      for(let c=0;c<GRID_COLS;c++){
        const k = blockKey(r,c);
        const cell = document.createElement('div');
        cell.className = 'cell';
        cell.dataset.key = k;

        const thumb = document.createElement('div');
        thumb.className = 'thumb';
        cell.appendChild(thumb);

        const overlay = document.createElement('div');
        overlay.className = 'overlay';
        cell.appendChild(overlay);

        const meta = document.createElement('div');
        meta.className = 'meta';
        cell.appendChild(meta);

        // Restaurar arte se existir
        const b = state.blocks[k];
        if(b){
          if(b.color) cell.style.background = b.color;
          if(b.imgData){ thumb.style.backgroundImage = `url(${b.imgData})`; }
          if(b.title) meta.textContent = b.title;
          if(b.sold) cell.classList.add('sold');
        }

        // Clique para selecionar / abrir link
        cell.addEventListener('click', (ev)=>{
          const k = cell.dataset.key;
          if(cell.classList.contains('sold')) return; // bloqueado

          if(ev.ctrlKey || ev.metaKey){
            if(state.cart.has(k)) state.cart.delete(k); else state.cart.add(k);
          }else{
            state.cart.clear(); state.cart.add(k);
          }
          renderCart();
        });

        cell.addEventListener('dblclick', ()=>{
          const b = state.blocks[k];
          if(b && b.url){ window.open(b.url, '_blank'); }
        })

        gridEl.appendChild(cell);
      }
    }

    /****************************
     * Carrinho
     ****************************/
    const cartInfo = document.getElementById('cartInfo');
    const cartList = document.getElementById('cartList');
    const totalLabel = document.getElementById('totalLabel');

    function renderCart(){
      cartList.innerHTML = '';
      if(state.cart.size === 0){
        cartInfo.textContent = 'Nenhum bloco selecionado.';
        totalLabel.textContent = fmtBRL(0);
        // deselecionar visualmente
        document.querySelectorAll('.cell').forEach(el=> el.style.outline='');
        return;
      }
      cartInfo.textContent = `${state.cart.size} bloco(s) selecionado(s).`;
      const total = state.cart.size * pricePerBlock();
      totalLabel.textContent = fmtBRL(total);

      // destacar
      document.querySelectorAll('.cell').forEach(el=> el.style.outline='');
      state.cart.forEach(k=>{
        const el = document.querySelector(`.cell[data-key="${k}"]`);
        if(el) el.style.outline = '2px solid #7c3aed88';
      });

      // listar
      const arr = Array.from(state.cart).slice(0,100); // limitar exibição
      arr.forEach(k=>{
        const div = document.createElement('div');
        div.className = 'item';
        div.innerHTML = `<strong>Bloco ${k}</strong><span>${fmtBRL(pricePerBlock())}</span>`;
        cartList.appendChild(div);
      });
    }

    /****************************
     * Modal de design
     ****************************/
    const designModal = document.getElementById('designModal');
    const openDesignBtn = document.getElementById('openDesignBtn');
    const closeDesign = document.getElementById('closeDesign');
    const applyDesignBtn = document.getElementById('applyDesignBtn');
    const titleInput = document.getElementById('titleInput');
    const urlInput = document.getElementById('urlInput');
    const colorInput = document.getElementById('colorInput');
    const imgInput = document.getElementById('imgInput');
    const imgPreview = document.getElementById('imgPreview');

    openDesignBtn.addEventListener('click', ()=>{
      if(state.cart.size===0){ alert('Selecione pelo menos 1 bloco.'); return; }
      designModal.classList.add('open');
    });
    closeDesign.addEventListener('click', ()=> designModal.classList.remove('open'));

    imgInput.addEventListener('change', ()=>{
      const file = imgInput.files?.[0];
      if(!file){ imgPreview.textContent = 'Pré-visualização'; imgPreview.innerHTML='Pré-visualização'; return; }
      const reader = new FileReader();
      reader.onload = ()=>{
        const data = reader.result;
        imgPreview.innerHTML = `<img src="${data}" alt="preview"/>`;
      };
      reader.readAsDataURL(file);
    });

    applyDesignBtn.addEventListener('click', ()=>{
      const file = imgInput.files?.[0];
      if(file){
        const reader = new FileReader();
        reader.onload = ()=>{
          applyDesign(reader.result);
        };
        reader.readAsDataURL(file);
      }else{
        applyDesign(null);
      }
    });

    function applyDesign(imgData){
      const title = titleInput.value.trim();
      const url = urlInput.value.trim();
      const color = colorInput.value;

      state.cart.forEach(k=>{
        const cell = document.querySelector(`.cell[data-key="${k}"]`);
        if(!state.blocks[k]) state.blocks[k] = {};
        const b = state.blocks[k];
        b.title = title || b.title || '';
        b.url = url || b.url || '';
        b.color = color || b.color || '#0e1320';
        if(imgData !== null){ b.imgData = imgData; }

        // aplicar visualmente
        if(cell){
          cell.style.background = b.color || '#0e1320';
          const thumb = cell.querySelector('.thumb');
          thumb.style.backgroundImage = b.imgData ? `url(${b.imgData})` : '';
          const meta = cell.querySelector('.meta');
          meta.textContent = b.title || '';
        }
      });
      save();
      designModal.classList.remove('open');
    }

    /****************************
     * Admin
     ****************************/
    const adminBtn = document.getElementById('adminBtn');
    const adminPanel = document.getElementById('adminPanel');
    const adminPass = document.getElementById('adminPass');
    const authBtn = document.getElementById('authBtn');
    const lockBtn = document.getElementById('lockBtn');
    const unlockBtn = document.getElementById('unlockBtn');

    adminBtn.addEventListener('click', ()=>{
      adminPanel.style.display = adminPanel.style.display==='none' ? 'block' : 'none';
    });
    authBtn.addEventListener('click', ()=>{
      if(adminPass.value === ADMIN_PASSWORD){
        state.adminAuthed = true; lockBtn.disabled=false; unlockBtn.disabled=false; alert('Admin autenticado.');
      }else{ alert('Senha incorreta'); }
    });

    lockBtn.addEventListener('click', ()=>{
      if(!state.adminAuthed) return;
      if(state.cart.size===0){ alert('Selecione blocos a bloquear.'); return; }
      state.cart.forEach(k=>{
        if(!state.blocks[k]) state.blocks[k] = {};
        state.blocks[k].sold = true;
        const cell = document.querySelector(`.cell[data-key="${k}"]`);
        cell?.classList.add('sold');
        cell && (cell.style.outline='');
      });
      state.cart.clear(); renderCart(); save(); updateAvailableCount();
    });

    unlockBtn.addEventListener('click', ()=>{
      if(!state.adminAuthed) return;
      if(state.cart.size===0){ alert('Selecione blocos a desbloquear.'); return; }
      state.cart.forEach(k=>{
        if(!state.blocks[k]) state.blocks[k] = {};
        state.blocks[k].sold = false;
        const cell = document.querySelector(`.cell[data-key="${k}"]`);
        cell?.classList.remove('sold');
      });
      save(); updateAvailableCount();
    });

    /****************************
     * Import / Export
     ****************************/
    document.getElementById('exportBtn').addEventListener('click', ()=>{
      const payload = {
        v:1,
        pricePerPixel: state.pricePerPixel,
        grid:{rows:GRID_ROWS, cols:GRID_COLS},
        blocks: state.blocks
      };
      const blob = new Blob([JSON.stringify(payload,null,2)], {type:'application/json'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url; a.download = 'pixelmarket-export.json'; a.click();
      URL.revokeObjectURL(url);
    });

    document.getElementById('importBtn').addEventListener('click', ()=>{
      const inp = document.createElement('input');
      inp.type='file'; inp.accept='application/json';
      inp.onchange = ()=>{
        const file = inp.files?.[0]; if(!file) return;
        const reader = new FileReader();
        reader.onload = ()=>{
          try{
            const data = JSON.parse(reader.result);
            if(data.blocks){ state.blocks = data.blocks; }
            if(data.pricePerPixel){ state.pricePerPixel = data.pricePerPixel; pricePerPixelInput.value = String(state.pricePerPixel); }
            // aplicar visual
            document.querySelectorAll('.cell').forEach(cell=>{
              const k = cell.dataset.key; const b = state.blocks[k];
              cell.classList.remove('sold');
              cell.style.background = '#0e1320';
              cell.querySelector('.thumb').style.backgroundImage = '';
              cell.querySelector('.meta').textContent = '';
              if(b){
                if(b.color) cell.style.background = b.color;
                if(b.imgData) cell.querySelector('.thumb').style.backgroundImage = `url(${b.imgData})`;
                if(b.title) cell.querySelector('.meta').textContent = b.title;
                if(b.sold) cell.classList.add('sold');
              }
            });
            save(); updateAvailableCount(); alert('Importado com sucesso');
          }catch(e){ alert('Arquivo inválido'); }
        };
        reader.readAsText(file);
      };
      document.body.appendChild(inp); inp.click(); inp.remove();
    });

    /****************************
     * Checkout simples (manual)
     ****************************/
    const checkoutBtn = document.getElementById('checkoutBtn');
    checkoutBtn.addEventListener('click', ()=>{
      if(state.cart.size===0){ alert('Selecione blocos para comprar.'); return; }
      const total = state.cart.size * pricePerBlock();
      const list = Array.from(state.cart).join(', ');
      const msg = `Olá! Quero comprar ${state.cart.size} bloco(s): ${list}. Total: ${fmtBRL(total)}.`;
      const wpp = `https://wa.me/?text=${encodeURIComponent(msg)}`;
      window.open(wpp,'_blank');
    });

    /****************************
     * Preço por pixel
     ****************************/
    const pricePerPixelInput = document.getElementById('pricePerPixel');
    pricePerPixelInput.value = String(state.pricePerPixel);
    pricePerPixelInput.addEventListener('input', ()=>{
      const v = parseFloat(pricePerPixelInput.value||'0');
      state.pricePerPixel = isNaN(v)?0:v; save(); renderCart();
    });

    // Inicializar
    updateAvailableCount();
  </script>
</body>
</html>
