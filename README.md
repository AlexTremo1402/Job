# Job
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Informe Diario de Monitoreo Clínico - Pro</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #34495e;
            --accent-color: #2980b9;
            --bg-color: #f5f7fa;
            --card-bg: #ffffff;
            --border-color: #bdc3c7;
            --text-color: #2c3e50;
            --light-bg: #eef2f5;
            --danger-color: #c0392b;
        }

        * {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            padding: 15px;
            display: flex;
            justify-content: center;
        }

        .container {
            width: 100%;
            max-width: 950px;
            background: var(--card-bg);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        .header {
            text-align: center;
            margin-bottom: 20px;
            border-bottom: 3px solid var(--primary-color);
            padding-bottom: 12px;
        }

        .header h1 {
            color: var(--primary-color);
            font-size: 22px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 10px;
        }

        .meta-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        .meta-item {
            display: flex;
            align-items: center;
            border: 1px solid var(--border-color);
            padding: 8px 12px;
            background: var(--light-bg);
            border-radius: 4px;
        }

        .meta-item label {
            font-weight: bold;
            margin-right: 10px;
            font-size: 13px;
        }

        .meta-item input {
            border: none;
            background: transparent;
            width: 100%;
            font-size: 14px;
            color: var(--text-color);
        }

        .meta-item input:focus {
            outline: none;
        }

        .section {
            margin-bottom: 25px;
        }

        .section-title {
            background-color: #cbdbe6;
            color: var(--primary-color);
            padding: 8px 12px;
            font-size: 14px;
            font-weight: bold;
            text-transform: uppercase;
            margin-bottom: 12px;
            border-radius: 4px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 12px;
            background: #fff;
        }

        th, td {
            border: 1px solid var(--border-color);
            padding: 10px 8px;
            text-align: center;
            font-size: 13px;
        }

        th {
            background-color: var(--light-bg);
            font-weight: bold;
            color: var(--primary-color);
        }

        input[type="text"], input[type="time"], select {
            width: 100%;
            padding: 6px;
            border: 1px solid #ddd;
            border-radius: 4px;
            text-align: center;
            font-size: 13px;
        }

        .search-container {
            margin-bottom: 10px;
        }
        .search-box {
            width: 100%;
            padding: 10px;
            border: 2px solid var(--accent-color);
            border-radius: 6px;
            font-size: 14px;
            outline: none;
        }

        .workspace-zone {
            display: grid;
            grid-template-columns: 1fr 120px;
            gap: 10px;
            margin-bottom: 15px;
        }

        @media (max-width: 500px) {
            .workspace-zone {
                grid-template-columns: 1fr;
            }
            .delete-zone {
                height: 55px !important;
            }
        }

        .drag-zone {
            display: flex;
            gap: 10px;
            padding: 12px;
            background: var(--light-bg);
            border: 2px dashed var(--border-color);
            border-radius: 6px;
            overflow-x: auto;
            align-items: center;
            touch-action: pan-x; 
            -webkit-overflow-scrolling: touch;
        }

        .delete-zone {
            background: #fdf2f2;
            border: 2px dashed var(--danger-color);
            border-radius: 6px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: var(--danger-color);
            font-size: 11px;
            font-weight: bold;
            cursor: pointer;
            text-align: center;
            padding: 5px;
            transition: background 0.2s, transform 0.2s;
            user-select: none;
        }

        .delete-zone.hover-delete {
            background: #f8d7da;
            transform: scale(1.02);
        }

        .drag-item {
            background: var(--accent-color);
            color: white;
            padding: 8px 12px;
            border-radius: 4px;
            cursor: pointer;
            user-select: none;
            font-size: 12px;
            font-weight: bold;
            white-space: nowrap;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 4px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.15);
            transition: transform 0.1s, background-color 0.2s;
        }

        .drag-item.selected-active {
            background-color: #e67e22;
            transform: scale(1.05);
            box-shadow: 0 0 8px #e67e22;
        }

        .drag-item .icon-fallback, .drag-item img {
            width: 28px;
            height: 28px;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            background: rgba(255,255,255,0.2);
        }

        .patient-drop-cell {
            background: #fafbfc;
            min-height: 50px;
            padding: 6px;
            border-radius: 4px;
            border: 1px solid #ddd;
            text-align: left;
            cursor: pointer;
            transition: background 0.2s;
        }
        .patient-drop-cell.hover {
            background: #e8f4fd;
            border: 1px dashed var(--accent-color);
        }

        .med-list-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #fff;
            padding: 6px 10px;
            margin-bottom: 5px;
            border: 1px solid #e2e8f0;
            border-radius: 4px;
            font-size: 12px;
            box-shadow: 0 1px 2px rgba(0,0,0,0.05);
        }

        .med-list-right {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .med-list-item span.med-count {
            background: #e2e8f0;
            padding: 2px 6px;
            border-radius: 10px;
            font-weight: bold;
            color: #4a5568;
        }

        .btn-remove-med {
            background: #f8d7da;
            color: var(--danger-color);
            border: none;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 10px;
            font-weight: bold;
            cursor: pointer;
            padding: 0;
        }
        .btn-remove-med:hover {
            background: var(--danger-color);
            color: white;
        }

        .empty-list-msg {
            color: #a0aec0;
            font-style: italic;
            font-size: 12px;
            text-align: center;
            padding-top: 6px;
        }

        .creator-panel {
            background: #fcfcfc;
            border: 1px solid #dcdcdc;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 15px;
        }

        .creator-grid {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr;
            gap: 10px;
            margin-bottom: 10px;
        }

        @media (max-width: 600px) {
            .creator-grid { grid-template-columns: 1fr; }
            .meta-grid { grid-template-columns: 1fr; }
        }

        .creator-field {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .creator-field label {
            font-size: 11px;
            font-weight: bold;
            color: var(--secondary-color);
        }

        .btn-row {
            margin-top: 8px;
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        button {
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 10px 16px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            font-size: 13px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        button.btn-success { background-color: #27ae60; }
        button.btn-pdf { 
            background-color: #e74c3c; 
            width: 100%;
            font-size: 15px;
            padding: 14px;
            margin-top: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .select-box {
            width: 100%;
            padding: 8px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            background-color: white;
            font-size: 13px;
            margin-bottom: 15px;
        }

        .notes-area {
            border: 1px solid var(--border-color);
            padding: 12px;
            background: var(--light-bg);
            border-radius: 4px;
        }

        .notes-area textarea {
            width: 100%;
            height: 70px;
            padding: 8px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            resize: none;
            font-size: 13px;
        }

        @media print {
            @page {
                size: A4 portrait;
                margin: 8mm;
            }
            body { background: #fff; padding: 0; margin: 0; }
            .container { box-shadow: none; padding: 0; max-width: 100%; width: 100%; }
            .creator-panel, .btn-row, button, .search-container, .workspace-zone, p, label[for="totals-alphabetical-select"], #totals-alphabetical-select, .btn-remove-med {
                display: none !important;
            }
            input[type="text"], input[type="time"], textarea {
                border: none !important;
                background: transparent !important;
                padding: 0 !important;
                text-align: center !important;
            }
            th, td { padding: 6px 5px !important; font-size: 11px !important; }
            .section { margin-bottom: 12px !important; }
            .section-title { padding: 4px 8px !important; font-size: 12px !important; margin-bottom: 6px !important; }
            .patient-drop-cell { min-height: auto !important; border: none !important; padding: 0 !important; }
            .med-list-item { border: none !important; padding: 2px 0 !important; margin: 0 !important; box-shadow: none; }
            .notes-area { padding: 8px !important; }
            .notes-area textarea { height: 50px !important; }
        }
    </style>
</head>
<body>

<div class="container">

    <div class="header">
        <h1>Informe de Insumos Aplicados</h1>
        <div class="meta-grid">
            <div class="meta-item">
                <label>Fecha:</label>
                <input type="text" id="current-date" value="">
            </div>
            <div class="meta-item">
                <label>Enfermero:</label>
                <input type="text" id="nurse-name" placeholder="Escriba su nombre">
            </div>
        </div>
    </div>

    <div class="section">
        <div class="section-title">Pacientes Registrados</div>
        <table id="patients-table">
            <thead>
                <tr>
                    <th style="width: 15%;">Paciente</th>
                    <th style="width: 35%;">Apellidos e Historial</th>
                    <th style="width: 30%;">Número de Cédula</th>
                    <th style="width: 20%;">Hora Llegada</th>
                </tr>
            </thead>
            <tbody id="patients-tbody">
                <tr id="reg-row-1" data-id="1">
                    <td><b class="paciente-lbl-master">Paciente 1</b></td>
                    <td><input type="text" id="input-pname-1" placeholder="Ej. García Mendoza" oninput="syncPatientName(1)"></td>
                    <td><input type="text" placeholder="Cédula"></td>
                    <td><input type="time" id="time-pname-1" onchange="sortPatientsByTime()"></td>
                </tr>
            </tbody>
        </table>
        <div class="btn-row">
            <button type="button" onclick="addPatientMaster()">+ Agregar Paciente</button>
        </div>
    </div>

    <div class="section">
        <div class="section-title">Aplicación de Insumos Activos</div>
        
        <div class="creator-panel">
            <h4 style="font-size: 12px; margin-bottom: 8px; color: var(--primary-color);">⚙️ Registrar Nuevo Insumo Personalizado</h4>
            <div class="creator-grid">
                <div class="creator-field">
                    <label>Nombre del Insumo:</label>
                    <input type="text" id="new-insumo-name" placeholder="Ej. Dipirona">
                </div>
                <div class="creator-field">
                    <label>Tipo:</label>
                    <select id="new-insumo-type" onchange="toggleInputType()">
                        <option value="icon">Emoji / Ícono</option>
                        <option value="image">Subir Imagen</option>
                    </select>
                </div>
                <div class="creator-field">
                    <label>Contenido:</label>
                    <input type="text" id="new-insumo-icon" placeholder="Ej. 💊" value="💊">
                    <input type="file" id="new-insumo-file" accept="image/*" style="display: none;">
                </div>
            </div>
            <button type="button" class="btn-success" onclick="createNewInsumoElement()">Guardar en Barra</button>
        </div>

        <div class="search-container">
            <input type="text" id="search-input" class="search-box" placeholder="🔍 Buscar insumos (Ej: Jeringa, Cloruro, d)..." oninput="filterInsumos()">
        </div>

        <p style="font-size: 11px; margin-bottom: 6px; color: #555; font-weight: bold;">
            💡 Deslice con el dedo de lado a lado para buscar. Presione un insumo y toque la celda del paciente. Mantenga pulsado 1s para borrar el insumo del sistema o arrástrelo a la papelera.
        </p>
        
        <div class="workspace-zone">
            <div class="drag-zone" id="main-drag-zone">
                <div class="drag-item" draggable="true" id="ins-cloruro" data-name="Cloruro de Sodio 500ml">
                    <div class="icon-fallback">💧</div>
                    <span>Cloruro 500ml</span>
                </div>
                <div class="drag-item" draggable="true" id="ins-paracetamol" data-name="Paracetamol IV 1g">
                    <div class="icon-fallback">💊</div>
                    <span>Paracetamol 1g</span>
                </div>
                <div class="drag-item" draggable="true" id="ins-jeringa" data-name="Jeringa 5cc">
                    <div class="icon-fallback">💉</div>
                    <span>Jeringa 5cc</span>
                </div>
                <div class="drag-item" draggable="true" id="ins-cateter" data-name="Catetér IV Nro 20">
                    <div class="icon-fallback">📌</div>
                    <span>Catetér Nro 20</span>
                </div>
                <div class="drag-item" draggable="true" id="ins-gasa" data-name="Gasa Estéril">
                    <div class="icon-fallback">⬜</div>
                    <span>Gasa Estéril</span>
                </div>
            </div>

            <div class="delete-zone" id="main-delete-zone" ondragover="allowDeleteOver(event)" ondragleave="dragDeleteLeave(event)" ondrop="dropDeleteInsumo(event)">
                <span>🗑️ Papelera</span>
                <span style="font-size:9px; font-weight:normal;">Soltar aquí</span>
            </div>
        </div>

        <table id="active-monitoring-table">
            <thead>
                <tr>
                    <th style="width: 30%;">Paciente Activo</th>
                    <th style="width: 70%;">Medicamentos e Insumos Entregados (Toque 'X' para quitar)</th>
                </tr>
            </thead>
            <tbody id="monitoring-tbody">
                <tr id="mon-row-1" data-id="1">
                    <td id="lbl-pname-1" style="font-weight: bold; color: var(--accent-color); cursor:pointer;">Paciente 1</td>
                    <td>
                        <div class="patient-drop-cell" id="drop-cell-1" data-patient-id="1"
                             ondragover="allowDrop(event)" ondragleave="dragLeave(event)" ondrop="dropInsumo(event)"
                             onclick="cellClicked(1)">
                            <div class="empty-list-msg" id="empty-msg-1">Sin insumos asignados</div>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>

    <div class="section">
        <div class="section-title">Consolidado Total del Turno (Orden Alfabético)</div>
        <select class="select-box" id="totals-alphabetical-select"></select>

        <table id="totals-table">
            <thead>
                <tr>
                    <th style="text-align: left; padding-left: 15px;">Descripción General del Insumo</th>
                    <th style="width: 25%;">Cantidad Utilizada</th>
                </tr>
            </thead>
            <tbody id="totals-table-body">
                <tr>
                    <td colspan="2" style="color: #777; font-style: italic;">Asigne insumos arriba para calcular los totales automáticamente.</td>
                </tr>
            </tbody>
        </table>
    </div>

    <div class="notes-area">
        <label style="font-weight: bold; font-size: 13px; color: var(--primary-color);">Notas de Incidencias o Novedades:</label>
        <textarea id="txt-notes" placeholder="Escriba aquí los eventos críticos presentados durante el turno..."></textarea>
    </div>

    <button type="button" class="btn-pdf" onclick="exportToPDF()">📄 EXPORTAR INFORME A PDF / WHATSAPP</button>

</div>

<script>
    let insumosRegistroGlobal = {
        "Cloruro de Sodio 500ml": 0,
        "Paracetamol IV 1g": 0,
        "Jeringa 5cc": 0,
        "Catetér IV Nro 20": 0,
        "Gasa Estéril": 0
    };

    let datosInsumosPacientes = { 1: {} };
    let totalPatientsCount = 1;
    let selectedInsumoId = null; 
    let draggedElementId = null;
    let uniqueIdCounter = 0;
    let touchTimer = null; 

    document.addEventListener("DOMContentLoaded", function() {
        const dateInput = document.getElementById('current-date');
        const opciones = { day: 'numeric', month: 'long' };
        dateInput.value = new Date().toLocaleDateString('es-ES', opciones);
        
        const now = new Date();
        document.getElementById('time-pname-1').value = `${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;
        
        setupInsumoSelectionEvents();
        updateTotalsDisplay();
    });

    function toggleInputType() {
        const type = document.getElementById('new-insumo-type').value;
        document.getElementById('new-insumo-icon').style.display = (type === 'icon') ? 'block' : 'none';
        document.getElementById('new-insumo-file').style.display = (type === 'image') ? 'block' : 'none';
    }

    function syncPatientName(id) {
        const val = document.getElementById(`input-pname-${id}`).value.trim();
        const displayLabel = document.getElementById(`lbl-pname-${id}`);
        if (displayLabel) {
            displayLabel.innerText = val ? `Paciente ${id} (${val})` : `Paciente ${id}`;
        }
    }

    function addPatientMaster() {
        totalPatientsCount++;
        const currentId = totalPatientsCount;
        const now = new Date();
        const currentHour = `${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;
        
        const rowMaster = document.createElement('tr');
        rowMaster.id = `reg-row-${currentId}`;
        rowMaster.setAttribute('data-id', currentId);
        rowMaster.innerHTML = `
            <td><b class="paciente-lbl-master">Paciente ${currentId}</b></td>
            <td><input type="text" id="input-pname-${currentId}" placeholder="Ej. Apellidos" oninput="syncPatientName(${currentId})"></td>
            <td><input type="text" placeholder="Cédula"></td>
            <td><input type="time" id="time-pname-${currentId}" value="${currentHour}" onchange="sortPatientsByTime()"></td>
        `;
        document.getElementById('patients-tbody').appendChild(rowMaster);

        datosInsumosPacientes[currentId] = {};

        const rowMonitoring = document.createElement('tr');
        rowMonitoring.id = `mon-row-${currentId}`;
        rowMonitoring.setAttribute('data-id', currentId);
        rowMonitoring.innerHTML = `
            <td id="lbl-pname-${currentId}" style="font-weight: bold; color: var(--accent-color); cursor:pointer;">Paciente ${currentId}</td>
            <td>
                <div class="patient-drop-cell" id="drop-cell-${currentId}" data-patient-id="${currentId}"
                     ondragover="allowDrop(event)" ondragleave="dragLeave(event)" ondrop="dropInsumo(event)"
                     onclick="cellClicked(${currentId})">
                    <div class="empty-list-msg" id="empty-msg-${currentId}">Sin insumos asignados</div>
                </div>
            </td>
        `;
        document.getElementById('monitoring-tbody').appendChild(rowMonitoring);
        
        sortPatientsByTime();
    }

    function sortPatientsByTime() {
        const tbodyMaster = document.getElementById('patients-tbody');
        const rowsMaster = Array.from(tbodyMaster.querySelectorAll('tr'));

        rowsMaster.sort((a, b) => {
            const idA = a.getAttribute('data-id');
            const idB = b.getAttribute('data-id');
            const timeA = document.getElementById(`time-pname-${idA}`).value || "00:00";
            const timeB = document.getElementById(`time-pname-${idB}`).value || "00:00";
            return timeB.localeCompare(timeA); 
        });

        rowsMaster.forEach(row => tbodyMaster.appendChild(row));

        const tbodyMon = document.getElementById('monitoring-tbody');
        const rowsMon = Array.from(tbodyMon.querySelectorAll('tr'));

        rowsMon.sort((a, b) => {
            const idA = a.getAttribute('data-id');
            const idB = b.getAttribute('data-id');
            const timeA = document.getElementById(`time-pname-${idA}`).value || "00:00";
            const timeB = document.getElementById(`time-pname-${idB}`).value || "00:00";
            return timeB.localeCompare(timeA);
        });

        rowsMon.forEach(row => tbodyMon.appendChild(row));
    }

    function createNewInsumoElement() {
        const nameInput = document.getElementById('new-insumo-name');
        const insumoName = nameInput.value.trim();
        
        if (!insumoName) return;
        if (insumosRegistroGlobal.hasOwnProperty(insumoName)) {
            alert("Este insumo ya existe.");
            return;
        }

        const type = document.getElementById('new-insumo-type').value;
        uniqueIdCounter++;
        const newId = `ins-custom-${uniqueIdCounter}`;

        const dragItem = document.createElement('div');
        dragItem.className = 'drag-item';
        dragItem.draggable = true;
        dragItem.id = newId;
        dragItem.setAttribute('data-name', insumoName);

        insumosRegistroGlobal[insumoName] = 0;

        if (type === 'icon') {
            const iconVal = document.getElementById('new-insumo-icon').value || "📦";
            dragItem.innerHTML = `<div class="icon-fallback">${iconVal}</div><span>${insumoName}</span>`;
            finalizeInsumoCreation(dragItem);
        } else {
            const fileInput = document.getElementById('new-insumo-file');
            if (fileInput.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    dragItem.innerHTML = `<img src="${e.target.result}" alt="img"><span>${insumoName}</span>`;
                    finalizeInsumoCreation(dragItem);
                };
                reader.readAsDataURL(fileInput.files[0]);
            } else {
                dragItem.innerHTML = `<div class="icon-fallback">📦</div><span>${insumoName}</span>`;
                finalizeInsumoCreation(dragItem);
            }
        }
        nameInput.value = "";
    }

    function finalizeInsumoCreation(element) {
        document.getElementById('main-drag-zone').appendChild(element);
        setupInsumoSelectionEvents();
        updateTotalsDisplay();
        filterInsumos();
    }

    function filterInsumos() {
        const filterText = document.getElementById('search-input').value.toLowerCase().trim();
        const items = document.querySelectorAll('#main-drag-zone .drag-item');
        
        items.forEach(item => {
            const name = item.getAttribute('data-name').toLowerCase();
            if (name.includes(filterText)) {
                item.style.display = 'flex';
            } else {
                item.style.display = 'none';
            }
        });
    }

    function setupInsumoSelectionEvents() {
        const items = document.querySelectorAll('.drag-item');
        items.forEach(item => {
            item.addEventListener('dragstart', function(e) {
                e.dataTransfer.setData('text/plain', this.id);
                draggedElementId = this.id; // Respaldo global para navegadores móviles/híbridos
            });

            item.onclick = function(e) {
                e.stopPropagation();
                if (selectedInsumoId === this.id) {
                    this.classList.remove('selected-active');
                    selectedInsumoId = null;
                } else {
                    document.querySelectorAll('.drag-item').forEach(el => el.classList.remove('selected-active'));
                    this.classList.add('selected-active');
                    selectedInsumoId = this.id;
                }
            };

            item.addEventListener('touchstart', function(e) {
                draggedElementId = this.id;
                touchTimer = setTimeout(() => {
                    if (window.navigator && window.navigator.vibrate) {
                        window.navigator.vibrate(50);
                    }
                    triggerInsumoDeletion(this.id);
                }, 1000);
            }, { passive: true });

            item.addEventListener('touchend', function(e) {
                if (touchTimer) clearTimeout(touchTimer);
            }, { passive: true });

            item.addEventListener('touchmove', function(e) {
                if (touchTimer) clearTimeout(touchTimer);
            }, { passive: true });
        });
    }

    function triggerInsumoDeletion(elementId) {
        if (!elementId) return; // Validación anti-errores catastróficos
        const item = document.getElementById(elementId);
        if (!item) return;
        
        const insumoName = item.getAttribute('data-name');
        const confirmDelete = confirm(`¿Deseas eliminar el insumo "${insumoName}" de la barra disponible?`);
        
        if (confirmDelete) {
            if (insumosRegistroGlobal.hasOwnProperty(insumoName)) {
                delete insumosRegistroGlobal[insumoName];
            }
            if (selectedInsumoId === elementId) selectedInsumoId = null;
            item.remove();
            
            updateTotalsDisplay();
        }
    }

    function allowDeleteOver(e) { 
        e.preventDefault(); 
        document.getElementById('main-delete-zone').classList.add('hover-delete'); 
    }
    
    function dragDeleteLeave(e) { 
        document.getElementById('main-delete-zone').classList.remove('hover-delete'); 
    }
    
    function dropDeleteInsumo(e) {
        e.preventDefault();
        document.getElementById('main-delete-zone').classList.remove('hover-delete');
        
        // CORRECCIÓN CRÍTICA: Intenta leer el id desde la transferencia nativa de datos o recupera el respaldo global.
        let id = e.dataTransfer.getData('text/plain') || draggedElementId;
        
        if (id) {
            triggerInsumoDeletion(id);
        } else {
            alert("No se pudo detectar el insumo seleccionado. Por favor, vuelve a arrastrarlo o usa presión larga.");
        }
        draggedElementId = null; // Reiniciar referencias seguras
    }

    function cellClicked(pId) {
        if (selectedInsumoId) {
            executeMedicationDelivery(selectedInsumoId, pId);
            document.querySelectorAll('.drag-item').forEach(el => el.classList.remove('selected-active'));
            selectedInsumoId = null;
        }
    }

    function allowDrop(e) { e.preventDefault(); e.currentTarget.classList.add('hover'); }
    function dragLeave(e) { e.currentTarget.classList.remove('hover'); }
    function dropInsumo(e) {
        e.preventDefault();
        e.currentTarget.classList.remove('hover');
        let id = e.dataTransfer.getData('text/plain') || draggedElementId;
        if (id) {
            const pId = e.currentTarget.getAttribute('data-patient-id');
            executeMedicationDelivery(id, pId);
        }
        draggedElementId = null;
    }

    function executeMedicationDelivery(elementId, patientId) {
        const item = document.getElementById(elementId);
        if (!item) return;

        const insumoName = item.getAttribute('data-name');

        if (!datosInsumosPacientes[patientId][insumoName]) {
            datosInsumosPacientes[patientId][insumoName] = 0;
        }
        datosInsumosPacientes[patientId][insumoName]++;
        
        if (insumosRegistroGlobal.hasOwnProperty(insumoName)) {
            insumosRegistroGlobal[insumoName]++;
        }

        renderPatientCellList(patientId);
        updateTotalsDisplay();
    }

    function removeSingleInsumoFromPatient(pId, insumoName, event) {
        if(event) event.stopPropagation(); 

        if (datosInsumosPacientes[pId] && datosInsumosPacientes[pId][insumoName] > 0) {
            datosInsumosPacientes[pId][insumoName]--;
            
            if (insumosRegistroGlobal[insumoName] > 0) {
                insumosRegistroGlobal[insumoName]--;
            }

            if (datosInsumosPacientes[pId][insumoName] === 0) {
                delete datosInsumosPacientes[pId][insumoName];
            }

            renderPatientCellList(pId);
            updateTotalsDisplay();
        }
    }

    function renderPatientCellList(pId) {
        const cell = document.getElementById(`drop-cell-${pId}`);
        if (!cell) return;

        cell.querySelectorAll('.med-list-item').forEach(el => el.remove());

        const medData = datosInsumosPacientes[pId] || {};
        const activeKeys = Object.keys(medData).filter(k => medData[k] > 0);

        if (activeKeys.length === 0) {
            if (!document.getElementById(`empty-msg-${pId}`)) {
                cell.innerHTML = `<div class="empty-list-msg" id="empty-msg-${pId}">Sin insumos asignados</div>`;
            }
            return;
        }

        const msg = document.getElementById(`empty-msg-${pId}`);
        if (msg) msg.remove();

        activeKeys.sort().forEach(medName => {
            const qty = medData[medName];
            const listItem = document.createElement('div');
            listItem.className = 'med-list-item';
            listItem.innerHTML = `
                <span class="med-name">▪️ ${medName}</span>
                <div class="med-list-right">
                    <span class="med-count">x${qty}</span>
                    <button class="btn-remove-med" onclick="removeSingleInsumoFromPatient(${pId}, '${medName}', event)">✕</button>
                </div>
            `;
            cell.appendChild(listItem);
        });
    }

    function updateTotalsDisplay() {
        const selectBox = document.getElementById('totals-alphabetical-select');
        const tableBody = document.getElementById('totals-table-body');
        
        selectBox.innerHTML = "";
        tableBody.innerHTML = "";

        const sortedKeys = Object.keys(insumosRegistroGlobal).sort((a, b) => a.localeCompare(b));
        let totalAcumuladoTurno = 0;

        sortedKeys.forEach(insumo => {
            const cantidadTotal = insumosRegistroGlobal[insumo];
            totalAcumuladoTurno += cantidadTotal;

            const opt = document.createElement('option');
            opt.text = `${insumo} (Total: ${cantidadTotal})`;
            selectBox.add(opt);

            if (cantidadTotal > 0) {
                const row = tableBody.insertRow();
                row.innerHTML = `
                    <td style="text-align: left; padding-left: 15px; font-weight: 500;">${insumo}</td>
                    <td><span style="background: #2c3e50; color: white; padding: 2px 8px; border-radius: 4px; font-weight: bold;">${cantidadTotal}</span></td>
                `;
            }
        });

        if (totalAcumuladoTurno === 0) {
            selectBox.innerHTML = "<option>No hay insumos registrados...</option>";
            tableBody.innerHTML = `
                <tr>
                    <td colspan="2" style="color: #a0aec0; font-style: italic;">Asigne insumos arriba para calcular los totales automáticamente.</td>
                </tr>
            `;
        }
    }

    function exportToPDF() {
        window.print();
    }
</script>

</body>
</html>
