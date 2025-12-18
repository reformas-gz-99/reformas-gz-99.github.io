<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Facturador</title>
    
    <!-- ICONO -->
    <link rel="icon" type="image/svg+xml" href="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA2NCA2NCI+PHY+PGNpcmNsZSBjeD0iMzIiIGN5PSIzMiIgcj0iMzIiIGZpbGw9IiNGRkM0MDAiLz48cGF0aCBkPSJNNDQgMThIMjB2MTJoNnYyMmgyVjMwaDZ6IiBmaWxsPSIjMEIyQjQ1IiB0cmFuc2Zvcm09InJvdGF0ZSgtNDUgMzIgMzIpIi8+PC9zdmc+">

    <!-- Fuente Moderna -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">

    <style>
        /* --- VARIABLES DE DISEÑO --- */
        :root {
            --primary: #FFC400;       
            --primary-hover: #e6b200;
            --dark: #0B2B45;          
            --text-main: #334155;     
            --text-light: #64748b;    
            --bg-body: #f1f5f9;       
            --bg-card: #ffffff;       
            --border-color: #e2e8f0;  
            --danger: #ef4444;        
            --gmail: #ea4335;         
            --pdf: #dc2626;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }

        /* --- BASE --- */
        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-body);
            color: var(--text-main);
            margin: 0;
            padding: 20px; 
            line-height: 1.5;
        }

        .container {
            background-color: var(--bg-card);
            max-width: 850px;
            margin: 0 auto;
            padding: 50px;
            border-radius: 12px;
            box-shadow: var(--shadow);
            position: relative;
        }

        /* --- HEADER Y LOGO --- */
        .header-section {
            display: flex;
            justify-content: space-between;
            align-items: center; 
            margin-bottom: 40px;
            border-bottom: 3px solid var(--primary);
            padding-bottom: 20px;
        }

        .logo { flex-shrink: 0; }

        .logo img {
            width: 260px; 
            height: auto;
            display: block;
        }

        .company-info {
            text-align: right;
            font-size: 0.9rem;
            color: var(--text-light);
            margin-left: 20px;
        }

        .company-info h2 {
            margin: 0 0 5px 0;
            color: var(--dark);
            font-weight: 700;
            letter-spacing: -0.5px;
            font-size: 1rem; 
            text-transform: uppercase;
        }

        .company-info p { margin: 2px 0; }

        /* --- DATOS DEL DOCUMENTO (META) --- */
        .doc-meta-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #f8fafc;
            padding: 15px 20px;
            border-radius: 8px;
            margin-bottom: 30px;
            border: 1px solid var(--border-color);
        }

        #doc-type {
            font-size: 1.4rem;
            font-weight: 900;
            color: var(--dark); 
            letter-spacing: 0.5px;
            text-transform: uppercase;
            margin-bottom: 0; 
            line-height: 1;
        }

        .meta-group {
            display: flex;
            gap: 20px;
            align-items: center;
        }

        .meta-item {
            display: flex;
            flex-direction: column;
            font-size: 0.85rem;
        }

        .meta-item label {
            font-weight: 600;
            color: var(--text-light);
            margin-bottom: 2px;
            font-size: 0.75rem;
            text-transform: uppercase;
        }

        .clean-input {
            border: 1px solid var(--border-color);
            border-radius: 4px;
            padding: 5px 8px;
            font-family: inherit;
            background: white;
            color: var(--dark);
            font-weight: 500;
            transition: border-color 0.2s;
            width: 140px; 
            box-sizing: border-box; 
        }
        
        .clean-input:disabled {
            background-color: #e2e8f0;
            color: #94a3b8;
            cursor: not-allowed;
            border-color: #cbd5e1;
        }
        
        .input-error {
            border: 2px solid var(--danger) !important;
            background-color: #fef2f2 !important;
        }

        /* --- GRID CLIENTE --- */
        .client-grid {
            display: grid;
            grid-template-columns: 1.2fr 1fr;
            gap: 30px;
            margin-bottom: 40px;
        }

        .client-box, .comments-box {
            display: flex;
            flex-direction: column;
            gap: 5px; 
        }

        .section-title {
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 700;
            color: var(--dark);
            border-bottom: 2px solid var(--primary);
            padding-bottom: 5px;
            margin-bottom: 5px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 80px 1fr;
            align-items: center;
            font-size: 0.9rem;
        }

        .form-row label {
            font-weight: 600;
            color: var(--text-light);
        }

        .form-row input {
            width: 100%;
            border: none;
            border-bottom: 1px dashed var(--border-color);
            padding: 1px 0; 
            font-family: inherit;
            color: var(--dark);
            background: transparent;
            transition: border 0.3s;
            height: 24px;
        }
        
        /* FUERZA MAYÚSCULAS EN DATOS DEL CLIENTE */
        .client-box input {
            text-transform: uppercase;
        }

        .form-row input::placeholder { color: #cbd5e1; text-transform: none; }

        .comments-box textarea, 
        .payment-info textarea {
            width: 100%;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            padding: 10px;
            resize: none;
            font-family: inherit;
            background-color: #fcfcfc;
            box-sizing: border-box;
            color: var(--text-main);
            line-height: 1.5;
            transition: border 0.3s;
        }
        
        /* FUERZA MAYÚSCULAS EN COMENTARIOS/OBRA */
        .comments-box textarea {
            text-transform: uppercase;
        }

        .comments-box textarea:focus, 
        .payment-info textarea:focus {
            outline: none;
            border-color: var(--primary);
            background-color: #fff;
        }

        /* --- TABLA --- */
        .table-container { margin-bottom: 30px; }

        .invoice-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.8rem; 
        }

        .invoice-table th {
            text-align: left;
            padding: 10px;
            background-color: var(--dark);
            color: white;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            border-right: 1px solid rgba(255,255,255,0.2); 
        }
        
        .invoice-table th:first-child { border-top-left-radius: 6px; }
        .invoice-table th:last-child { border-top-right-radius: 6px; border-right: none; }

        .invoice-table th:nth-child(3) { border-right: none; }

        .invoice-table td {
            padding: 8px 10px;
            border-bottom: 1px solid var(--border-color); 
            vertical-align: middle;
        }

        .invoice-table td:nth-child(1), 
        .invoice-table td:nth-child(2) {
            border-right: 1px solid var(--border-color);
        }

        /* FUERZA MAYÚSCULAS EN LAS LÍNEAS DE FACTURA */
        .invoice-table input[type="text"] {
            width: 100%;
            border: none;
            background: transparent;
            padding: 4px;
            font-family: inherit;
            font-size: 0.8rem; 
            text-transform: uppercase;
        }

        .invoice-table input[type="number"] {
            width: 100%;
            border: 1px solid transparent;
            background: #f8fafc;
            padding: 4px 8px;
            border-radius: 4px;
            text-align: right;
            font-family: 'Inter', sans-serif;
            font-weight: 500;
            box-sizing: border-box;
            font-size: 0.8rem;
        }

        .delete-btn {
            background: none;
            border: none;
            cursor: pointer;
            color: #cbd5e1;
            font-size: 1.1rem;
            padding: 5px; 
        }
        .delete-btn:hover { color: var(--danger); }

        /* --- FOOTER Y TOTALES --- */
        .footer-section {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            border-top: 2px solid var(--dark);
            padding-top: 20px;
            gap: 30px;
        }

        .payment-info {
            width: 55%;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .totals-box {
            width: 40%;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .total-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.95rem;
            color: var(--text-main);
        }

        .iva-control {
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .iva-input {
            width: 40px;
            text-align: center;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            padding: 2px;
            font-size: 0.9rem;
        }

        .grand-total {
            margin-top: 15px;
            padding: 15px;
            background-color: var(--dark);
            color: white;
            border-radius: 8px;
            font-weight: 700;
            font-size: 1.2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.2);
        }

        .grand-total span:first-child {
            font-size: 0.9rem;
            text-transform: uppercase;
            opacity: 0.9;
        }

        /* --- BOTONES DE CONTROL --- */
        .controls-area {
            margin-top: 50px;
            padding-top: 20px;
            border-top: 2px dashed var(--border-color);
            display: flex;
            justify-content: flex-end; 
            align-items: center;
            gap: 10px;
            flex-wrap: wrap; 
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 12px 24px; 
            border-radius: 8px;
            border: none;
            font-weight: 600;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.2s;
            font-family: inherit;
            color: white;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .btn:active { transform: translateY(1px); }
        .btn-dark { background-color: var(--dark); }
        .btn-dark:hover { background-color: #1e3a8a; }
        
        .btn-gmail { background-color: var(--gmail); }
        .btn-gmail:hover { background-color: #c5221f; }

        .btn-pdf { background-color: var(--pdf); }
        .btn-pdf:hover { background-color: #b91c1c; }

        .btn-add { 
            width: 100%; 
            justify-content: center; 
            margin-top: 15px; 
            background-color: #f1f5f9; 
            color: var(--text-light);
            border: 1px dashed var(--border-color);
            box-shadow: none;
            color: var(--dark);
        }
        .btn-add:hover {
            background-color: #e2e8f0;
            border-color: #cbd5e1;
        }

        .doc-select {
            padding: 12px;
            border-radius: 6px;
            border: 1px solid var(--border-color);
            font-family: inherit;
            background: white;
            font-weight: 600;
            color: var(--dark);
            cursor: pointer;
        }

        /* --- ADAPTACIÓN MÓVIL --- */
        @media screen and (max-width: 768px) {
            body { padding: 10px; }
            .container { padding: 20px; }
            .header-section { flex-direction: column; text-align: center; gap: 15px; }
            .company-info { margin-left: 0; text-align: center; }
            .logo img { width: 220px; margin: 0 auto; }
            .doc-meta-bar { flex-direction: column; gap: 15px; align-items: stretch; height: auto; }
            .meta-group { flex-wrap: wrap; justify-content: space-between; }
            .meta-item { flex: 1 1 45%; min-width: 130px; }
            .clean-input { width: 100%; text-align: center; }
            #doc-type { text-align: center; margin-bottom: 5px; }
            .client-grid { grid-template-columns: 1fr; gap: 20px; margin-bottom: 20px; }
            .footer-section { flex-direction: column; gap: 20px; }
            .payment-info, .totals-box { width: 100%; }
            .table-container { overflow-x: auto; }
            .invoice-table { min-width: 100%; }
            .invoice-table th:nth-child(1) { width: 50%; } 
            input, select, textarea { font-size: 16px !important; } 
            .controls-area { flex-direction: column; gap: 15px; align-items: stretch; }
            .btn, .doc-select { width: 100%; text-align: center; justify-content: center; }
        }

        /* --- OPTIMIZACIÓN IMPRESIÓN --- */
        @media print {
            @page { margin: 1cm; } 
            body { background: white; padding: 0; color: black; font-size: 11px; }
            .container { box-shadow: none; padding: 0; margin: 0; width: 100%; max-width: 100%; }
            .controls-area, .btn-add, .delete-btn { display: none !important; }
            .header-section { margin-bottom: 10px; padding-bottom: 10px; flex-direction: row; text-align: left; }
            .logo img { max-width: 250px; margin: 0; } 
            .company-info { text-align: right; margin-left: 20px; }
            .doc-meta-bar { margin-bottom: 10px; padding: 5px 0; background: none; border: none; border-bottom: 1px solid #000 !important; border-radius: 0 !important; flex-direction: row; align-items: flex-end !important; }
            .clean-input { border: none !important; padding: 0; text-align: left; width: auto; }
            .client-grid { gap: 20px; margin-bottom: 15px; grid-template-columns: 1.2fr 1fr; } 
            .footer-section { flex-direction: row; }
            .payment-info { width: 55%; }
            .totals-box { width: 40%; }
            .section-title { font-size: 0.8rem; color: #000; border-bottom: 1px solid #000; }
            .comments-box textarea, .payment-info textarea { height: auto; border: 1px solid #ccc !important; color: black !important; font-size: 0.85rem; }
            .form-row input { border: none; padding: 0; }
            .invoice-table th { background-color: #f0f0f0 !important; color: black !important; border-bottom: 1px solid black; padding: 5px; border-right: 1px solid #000 !important; }
            .invoice-table th:nth-child(4), .invoice-table td:nth-child(4) { display: none; }
            .invoice-table th:nth-child(3), .invoice-table td:nth-child(3) { border-right: none !important; }
            .invoice-table td { padding: 3px; border-bottom: 1px solid #ccc !important; font-size: 0.8rem; }
            .invoice-table td:nth-child(1), .invoice-table td:nth-child(2) { border-right: 1px solid #000 !important; }
            .grand-total { background: none !important; color: black !important; border: 2px solid black; box-shadow: none !important; }
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- HEADER -->
        <div class="header-section">
            <div class="logo">
                <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA1MDAgMTIwIj48Y2lyY2xlIGN4PSI2MCIgY3k9IjYwIiByPSI1MCIgZmlsbD0iI0ZGQzQwMCIgc3Ryb2tlPSIjODg4IiBzdHJva2Utd2lkdGg9IjIiLz48cGF0aCBzdHJva2U9IiNGRkYiIHN0cm9rZS13aWR0aD0iMiIgZD0iTTIwIDQwaDgwTTEwIDYwaDEwME0yMCA4MGg4ME00MCA0MHYyME04MCA0MHYyME02MCA2MHYyME00MCA4MHYyME04MCA4MHYyMCIgb3BhY2l0eT0iLjUiLz48cGF0aCBmaWxsPSIjRkZGIiBkPSJNNTUgMzVsMTAtNSA1IDEwIDEwLTUtNS0xMC0yMCA1ek02NSAzOEw0NSA5MGw3IDIgMTgtNTJ6Ii8+PHBhdGggZmlsbD0iI0ZGRiIgZD0iTTUwIDcwbDMwIDIwLTIwLTMwLTEweiIvPjxwYXRoIGZpbGw9IiNGRkYiIHN0cm9rZT0iI0ZGRiIgc3Ryb2tlLXdpZHRoPSIyIiBkPSJNNzAgNjVsNS0xNWg1bC01IDE1Ii8+PHRleHQgeD0iMTMwIiB5PSI0MCIgZm9udC1mYW1pbHk9InNhbnMtc2VyaWYiIGZvbnQtc2l6ZT0iMTYiIGZvbnQtd2VpZ2h0PSI2MDAiIGxldHRlci1zcGFjaW5nPSIyIiBmaWxsPSIjMEIyQjQ1Ij5DT05TVFJVQ0NJT05FUyBZIFJFRk9STUFTPC90ZXh0PjxwYXRoIHN0cm9rZT0iI0ZGQzQwMCIgc3Ryb2tlLXdpZHRoPSIzIiBkPSJNMTMwIDU1aDI4MCIvPjx0ZXh0IHg9IjEzMCIgeT0iMTAwIiBmb250LWZhbWlseT0ic2Fucy1zZXJpZiIgZm9udC1zaXplPSI2MCIgZm9udC13ZWlnaHQ9IjkwMCIgZmlsbD0iIzBCMkI0NSI+R09OWkFMRVo8L3RleHQ+PC9zdmc+" alt="Logo González Reformas">
            </div>
            <div class="company-info">
                <h2>EUSTAQUIO GONZÁLEZ MANGA</h2>
                <p>Carrer d'Aragó, 5</p>
                <p>08440 CARDEDEU</p>
                <p>NIF: 52144356K</p>
                <p>TEL: 615 080 924</p>
            </div>
        </div>
        
        <!-- DATOS DEL DOCUMENTO -->
        <div class="doc-meta-bar">
            <div id="doc-type">PRESUPUESTO</div>
            <div class="meta-group">
                <div class="meta-item" id="number-group">
                    <label>Número</label>
                    <input type="text" id="doc-number" class="clean-input" placeholder="2025/001" style="text-align: center;">
                </div>
                <div class="meta-item">
                    <label>Fecha</label>
                    <input type="date" id="doc-date" class="clean-input">
                </div>
            </div>
        </div>

        <!-- INFORMACIÓN CLIENTE -->
        <div class="client-grid">
            <div class="client-box">
                <div class="section-title">Datos del Cliente</div>
                
                <div class="form-row">
                    <label>Nombre:</label> 
                    <input type="text" id="client-name" placeholder="Ej: SR. JUAN PÉREZ">
                </div>
                <div class="form-row">
                    <label>Dirección:</label> 
                    <input type="text" id="client-address" placeholder="Ej: C/ MAYOR, 10, 2ºA">
                </div>
                <div class="form-row">
                    <label>Ciudad:</label> 
                    <input type="text" id="client-city" placeholder="Ej: CARDEDEU">
                </div>
                <div class="form-row">
                    <label>C.I.F.:</label> 
                    <input type="text" id="client-cif" placeholder="Ej: 12345678Z">
                </div>
            </div>
            
            <div class="comments-box">
                <div class="section-title">Descripción / Obra</div>
                <textarea id="comments" rows="5" placeholder="DESCRIBE BREVEMENTE LA OBRA O REFORMA..."></textarea>
            </div>
        </div>

        <!-- TABLA DE ARTÍCULOS -->
        <div class="table-container">
            <table class="invoice-table">
                <thead>
                    <tr>
                        <th style="width: 55%;">Concepto / Descripción</th>
                        <th style="width: 10%; text-align: center;">Horas</th>
                        <th style="width: 20%; text-align: right;">Importe</th>
                        <th style="width: 5%;"></th>
                    </tr>
                </thead>
                <tbody id="invoice-items">
                    <!-- Las filas se generan con JS -->
                </tbody>
            </table>
            
            <button id="btn-add-item" class="btn btn-add">
                <span style="font-size: 1.2em; margin-right: 5px;">+</span> Añadir Línea
            </button>
        </div>
        
        <!-- PIE DE PÁGINA Y TOTALES -->
        <div class="footer-section">
            <div class="payment-info">
                <div class="section-title">Forma de Pago</div>
                <textarea id="payment-terms" rows="3">50% al aceptar el presupuesto y el resto al finalizar la obra.</textarea>
            </div>
            
            <div class="totals-box">
                <div class="total-row">
                    <span>Base Imponible</span>
                    <span id="subtotal" style="font-weight: 600;">0,00 €</span>
                </div>
                
                <div class="total-row">
                    <div class="iva-control">
                        <input type="checkbox" id="iva-toggle" style="cursor: pointer;">
                        <label for="iva-toggle" style="cursor: pointer; font-size: 0.9em;">I.V.A.</label>
                        <input type="number" id="iva-rate" class="iva-input" data-rate-storage="21" value="0" min="0" step="0.1">
                        <span id="iva-symbol" style="display:none; font-size: 0.9em;">%</span>
                    </div>
                    <span id="tax-amount">0,00 €</span>
                </div>

                <div class="grand-total">
                    <span>Total <span id="doc-type-total">PRESUPUESTO</span></span>
                    <span id="grand-total">0,00 €</span>
                </div>
            </div>
        </div>

        <!-- CONTROLES -->
        <div class="controls-area">
            <select id="doc-selector" class="doc-select">
                <option value="PRESUPUESTO">Tipo: PRESUPUESTO</option>
                <option value="FACTURA PROFORMA">Tipo: FACTURA PROFORMA</option>
                <option value="FACTURA">Tipo: FACTURA</option>
            </select>
            
            <button id="btn-mail" class="btn btn-gmail">
                📨 Enviar
            </button>
            
            <button id="btn-print" class="btn btn-dark">
                🖨️ Imprimir
            </button>

            <button id="btn-pdf" class="btn btn-pdf">
                📄 Guardar PDF
            </button>
        </div>
    </div>

    <!-- JAVASCRIPT -->
    <script>
        document.addEventListener('DOMContentLoaded', (event) => {
            
            let hasUnsavedChanges = false;

            const itemsTable = document.getElementById('invoice-items');
            const docSelector = document.getElementById('doc-selector');
            const docTypeDisplay = document.getElementById('doc-type');
            const docTypeTotal = document.getElementById('doc-type-total');
            const ivaRateInput = document.getElementById('iva-rate');
            const ivaToggle = document.getElementById('iva-toggle'); 
            const ivaSymbol = document.getElementById('iva-symbol');
            const docNumInput = document.getElementById('doc-number'); 
            const numGroup = document.getElementById('number-group'); 

            const formatCurrency = (amount) => parseFloat(amount).toFixed(2).replace('.', ',') + ' €';

            const markAsDirty = () => { hasUnsavedChanges = true; };

            document.querySelector('.container').addEventListener('input', markAsDirty);
            document.querySelector('.container').addEventListener('change', markAsDirty);

            window.addEventListener('beforeunload', (e) => {
                if (hasUnsavedChanges) {
                    e.preventDefault();
                    e.returnValue = ''; 
                }
            });

            const handleDocTypeChange = () => {
                const rawVal = docSelector.value.replace('Tipo: ', ''); 
                docTypeDisplay.textContent = rawVal;
                docTypeTotal.textContent = rawVal;

                if (rawVal === 'PRESUPUESTO') {
                    numGroup.style.display = 'none';
                    docNumInput.disabled = true; 
                } else {
                    numGroup.style.display = 'flex'; 
                    docNumInput.disabled = false;
                }
            };

            docSelector.addEventListener('change', handleDocTypeChange);

            const addItem = () => {
                const newRow = itemsTable.insertRow();
                newRow.innerHTML = `
                    <td><input type="text" placeholder="DESCRIPCIÓN DEL TRABAJO..."></td>
                    <td><input type="number" class="hours" placeholder="0" style="text-align: center;"></td>
                    <td><input type="number" class="price" value="0.00" min="0" step="0.01"></td>
                    <td style="text-align: center;"><button class="delete-btn" onclick="removeItem(this)" title="Eliminar fila">&times;</button></td>
                `;
                newRow.querySelector('.price').addEventListener('input', calculateTotal);
                newRow.querySelector('input[type="text"]').focus();
                calculateTotal();
                markAsDirty(); 
            };

            window.removeItem = (button) => {
                const row = button.closest('tr');
                row.remove();
                calculateTotal();
                markAsDirty(); 
            };

            const calculateTotal = () => {
                let subtotalAmount = 0;
                const ivaRate = (parseFloat(ivaRateInput.value) || 0) / 100; 
                
                itemsTable.querySelectorAll('tr').forEach(row => {
                    const priceInput = row.querySelector('.price');
                    if (priceInput) {
                        subtotalAmount += parseFloat(priceInput.value) || 0;
                    }
                });

                const taxAmount = subtotalAmount * ivaRate;
                const grandTotal = subtotalAmount + taxAmount;

                document.getElementById('subtotal').textContent = formatCurrency(subtotalAmount);
                document.getElementById('tax-amount').textContent = formatCurrency(taxAmount);
                document.getElementById('grand-total').textContent = formatCurrency(grandTotal);
            };
            
            const toggleIVA = () => {
                const storedRate = ivaRateInput.getAttribute('data-rate-storage') || '21';
                const ivaContainer = document.querySelector('.iva-control');
                
                if (ivaToggle.checked) {
                    ivaRateInput.value = storedRate; 
                    ivaRateInput.disabled = false;
                    ivaContainer.style.opacity = "1";
                    ivaSymbol.style.display = "inline";
                } else {
                    if(ivaRateInput.value > 0) ivaRateInput.setAttribute('data-rate-storage', ivaRateInput.value);
                    ivaRateInput.value = 0;
                    ivaRateInput.disabled = true;
                    ivaContainer.style.opacity = "0.5";
                    ivaSymbol.style.display = "none";
                }
                calculateTotal();
            };

            const validateFields = () => {
                const fieldsToCheck = [
                    { id: 'doc-date', label: 'Fecha' },
                    { id: 'client-name', label: 'Nombre del cliente' },
                    { id: 'client-address', label: 'Dirección' },
                    { id: 'client-city', label: 'Ciudad' },
                    { id: 'client-cif', label: 'C.I.F.' },
                    { id: 'comments', label: 'Descripción / Obra' }
                ];

                if (!docNumInput.disabled) fieldsToCheck.unshift({ id: 'doc-number', label: 'Número de documento' });

                let missingFields = [];
                let isValid = true;

                document.querySelectorAll('.input-error').forEach(el => el.classList.remove('input-error'));

                fieldsToCheck.forEach(field => {
                    const el = document.getElementById(field.id);
                    if (!el || el.value.trim() === "") {
                        isValid = false;
                        missingFields.push(field.label);
                        if (el) el.classList.add('input-error'); 
                    }
                });

                if (!isValid) alert("⚠️ Faltan datos obligatorios.");
                return isValid;
            };

            const handlePrint = () => {
                if (validateFields()) {
                    const originalTitle = document.title;
                    const docType = docSelector.value.replace('Tipo: ', '');
                    const docNum = docNumInput.disabled ? 'SN' : docNumInput.value.replace(/\//g, '-'); 
                    const clientName = document.getElementById('client-name').value;
                    const docDate = document.getElementById('doc-date').value;

                    document.title = `${docType} ${docNum} - ${clientName} - ${docDate}`;
                    window.print();
                    setTimeout(() => { document.title = originalTitle; }, 1000);
                }
            };

            const handleSendMail = () => {
                if (!validateFields()) return;
                const docType = docSelector.value.replace('Tipo: ', '');
                const docNum = docNumInput.disabled ? 'S/N' : docNumInput.value;
                const clientName = document.getElementById('client-name').value;
                const subject = `${docType} ${docNum} - ${clientName}`;
                window.open(`https://mail.google.com/mail/?view=cm&fs=1&su=${encodeURIComponent(subject)}`, '_blank');
            };

            document.getElementById('btn-add-item').addEventListener('click', addItem);
            ivaRateInput.addEventListener('input', calculateTotal);
            ivaToggle.addEventListener('change', toggleIVA); 
            document.getElementById('btn-mail').addEventListener('click', handleSendMail);
            document.getElementById('btn-print').addEventListener('click', handlePrint);
            document.getElementById('btn-pdf').addEventListener('click', handlePrint); 

            document.getElementById('doc-date').valueAsDate = new Date();
            ivaToggle.checked = false;
            ivaRateInput.value = 0;
            ivaRateInput.disabled = true;
            document.querySelector('.iva-control').style.opacity = "0.5";

            handleDocTypeChange();
            addItem();
            hasUnsavedChanges = false; 
            calculateTotal();
        });
    </script>
</body>
</html>
