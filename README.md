<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Armadillo Outdoor - Rutas y Sitios</title>
    <style>
        :root {
            --body-bg: #808e9b; /* COLOR PLOMO */
            --black-header: #0a0a0a; /* NEGRO HEADER */
            --black-card: #141414; /* NEGRO TARJETAS Y PANELES */
            --black-input: #000000; /* NEGRO CAMPOS */
            --black-border: #2a2a2a;
            --accent-cyan: #00d2ff; /* CIAN ACCESO Y DETALLES */
            --text-light: #f4f4f5;
            --text-muted: #a1a1aa;
            --star-color: #ffc107;
            --danger-color: #ff4d4d;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--body-bg);
            color: var(--text-light);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* HEADER PRINCIPAL */
        header {
            background-color: var(--black-header);
            padding: 14px 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            position: sticky;
            top: 0;
            z-index: 90;
        }

        header img {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            border: 2px solid var(--accent-cyan);
            object-fit: cover;
        }

        .header-title h1 {
            font-size: 1.15rem;
            color: var(--accent-cyan);
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .header-title p {
            font-size: 0.75rem;
            color: var(--text-muted);
        }

        /* ESTRUCTURA PRINCIPAL EN 2 COLUMNAS */
        .app-layout {
            display: flex;
            flex: 1;
            max-width: 1300px;
            width: 100%;
            margin: 0 auto;
            padding: 20px 15px;
            gap: 20px;
        }

        /* BARRA LATERAL IZQUIERDA (LUGARES Y BÚSQUEDA) */
        .sidebar {
            width: 360px;
            flex-shrink: 0;
            background-color: var(--black-card);
            border-radius: 12px;
            padding: 18px;
            display: flex;
            flex-direction: column;
            gap: 15px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
            height: fit-content;
            max-height: calc(100vh - 110px);
            position: sticky;
            top: 85px;
        }

        .search-add-bar {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .search-box {
            position: relative;
            flex: 1;
        }

        .search-box input {
            width: 100%;
            padding: 10px 12px;
            background-color: var(--black-input);
            border: 1px solid var(--black-border);
            border-radius: 8px;
            color: var(--text-light);
            font-size: 0.9rem;
            outline: none;
        }

        .search-box input:focus {
            border-color: var(--accent-cyan);
        }

        .btn-add-main {
            width: 42px;
            height: 42px;
            background: linear-gradient(135deg, #00d2ff, #0072ff);
            color: #ffffff;
            border: none;
            border-radius: 8px;
            font-size: 1.5rem;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(0, 210, 255, 0.3);
            flex-shrink: 0;
            transition: transform 0.1s;
        }

        .btn-add-main:active {
            transform: scale(0.95);
        }

        .sidebar-header-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--black-border);
            padding-bottom: 8px;
        }

        .sidebar-title {
            font-size: 0.95rem;
            color: var(--accent-cyan);
            font-weight: 700;
        }

        .btn-show-all {
            background: transparent;
            border: 1px solid var(--accent-cyan);
            color: var(--accent-cyan);
            font-size: 0.72rem;
            padding: 3px 8px;
            border-radius: 4px;
            cursor: pointer;
        }

        .btn-show-all:hover {
            background-color: rgba(0, 210, 255, 0.1);
        }

        /* LISTA DE LUGARES EN LA IZQUIERDA */
        .places-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
            overflow-y: auto;
            padding-right: 4px;
        }

        .place-card-item {
            background-color: var(--black-input);
            border: 1px solid var(--black-border);
            border-left: 4px solid var(--accent-cyan);
            border-radius: 8px;
            padding: 10px 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 10px;
            transition: background 0.2s;
        }

        .place-card-item:hover {
            background-color: #1a1a1a;
        }

        .place-info {
            flex: 1;
            cursor: pointer;
        }

        .place-info h4 {
            font-size: 0.9rem;
            color: var(--text-light);
            margin-bottom: 4px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .place-badge-count {
            background-color: rgba(0, 210, 255, 0.2);
            color: var(--accent-cyan);
            font-size: 0.7rem;
            padding: 1px 6px;
            border-radius: 10px;
            font-weight: bold;
        }

        .place-info p {
            font-size: 0.78rem;
            color: var(--text-muted);
        }

        .btn-add-review-site {
            background-color: transparent;
            color: var(--accent-cyan);
            border: 1px solid var(--accent-cyan);
            border-radius: 6px;
            padding: 6px 10px;
            font-size: 0.75rem;
            font-weight: 700;
            cursor: pointer;
            white-space: nowrap;
            transition: all 0.2s;
        }

        .btn-add-review-site:hover {
            background-color: var(--accent-cyan);
            color: var(--black-input);
        }

        /* ÁREA PRINCIPAL (DERECHA) */
        .main-content {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .card {
            background-color: var(--black-card);
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
        }

        .card h2 {
            font-size: 1.15rem;
            color: var(--accent-cyan);
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 700;
        }

        .filter-status-banner {
            background-color: var(--black-input);
            border: 1px dashed var(--accent-cyan);
            border-radius: 8px;
            padding: 10px 14px;
            margin-bottom: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
            color: var(--text-light);
        }

        /* MODAL / INTERFAZ REGISTRO FLOTANTE */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: rgba(0, 0, 0, 0.75);
            backdrop-filter: blur(4px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.25s ease;
            padding: 15px;
        }

        .modal-overlay.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal-container {
            background-color: var(--black-card);
            border: 1px solid var(--black-border);
            border-radius: 12px;
            max-width: 550px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            padding: 22px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.8);
            position: relative;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 18px;
            border-bottom: 1px solid var(--black-border);
            padding-bottom: 10px;
        }

        .modal-header h2 {
            font-size: 1.15rem;
            color: var(--accent-cyan);
            margin-bottom: 0;
        }

        .btn-close-modal {
            background: transparent;
            border: none;
            color: var(--text-muted);
            font-size: 1.5rem;
            cursor: pointer;
            line-height: 1;
        }

        .btn-close-modal:hover {
            color: var(--text-light);
        }

        /* FORMULARIO */
        .upload-top-box {
            background-color: var(--black-input);
            border: 2px dashed var(--accent-cyan);
            border-radius: 10px;
            padding: 18px;
            text-align: center;
            margin-bottom: 16px;
        }

        .upload-top-box label {
            cursor: pointer;
            color: var(--accent-cyan);
            font-weight: 700;
            font-size: 0.95rem;
            display: inline-block;
        }

        .upload-top-box p {
            font-size: 0.75rem;
            color: var(--text-muted);
            margin-top: 4px;
        }

        input[type="file"] {
            display: none;
        }

        /* GRID PREVISUALIZACIÓN MULTIMEDIA EN EL FORMULARIO */
        .preview-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(90px, 1fr));
            gap: 10px;
            margin-top: 12px;
        }

        .preview-item {
            position: relative;
            width: 100%;
            height: 90px;
        }

        .preview-item img, .preview-item video {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid var(--accent-cyan);
        }

        .btn-remove-preview {
            position: absolute;
            top: -6px;
            right: -6px;
            background: var(--danger-color);
            color: #ffffff;
            border: none;
            border-radius: 50%;
            width: 22px;
            height: 22px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 6px rgba(0,0,0,0.5);
            z-index: 5;
        }

        .form-group {
            margin-bottom: 14px;
        }

        label {
            display: block;
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 6px;
            font-weight: 600;
        }

        input[type="text"], textarea {
            width: 100%;
            padding: 10px 12px;
            background-color: var(--black-input);
            border: 1px solid var(--black-border);
            border-radius: 8px;
            color: var(--text-light);
            font-size: 0.9rem;
            outline: none;
        }

        input[type="text"]::placeholder, textarea::placeholder {
            color: #52525b;
        }

        input[type="text"]:focus, textarea:focus {
            border-color: var(--accent-cyan);
        }

        .existing-site-tag {
            display: inline-block;
            background-color: rgba(0, 210, 255, 0.15);
            color: var(--accent-cyan);
            font-size: 0.75rem;
            padding: 4px 8px;
            border-radius: 6px;
            margin-bottom: 8px;
        }

        /* ESTRELLAS */
        .star-rating-input {
            display: flex;
            gap: 6px;
            direction: rtl;
            justify-content: flex-start;
            width: fit-content;
        }

        .star-rating-input input {
            display: none;
        }

        .star-rating-input label {
            font-size: 1.6rem;
            color: #27272a;
            cursor: pointer;
            margin-bottom: 0;
            transition: color 0.2s;
        }

        .star-rating-input input:checked ~ label,
        .star-rating-input label:hover,
        .star-rating-input label:hover ~ label {
            color: var(--accent-cyan);
        }

        .btn-submit {
            width: 100%;
            background: linear-gradient(135deg, #00d2ff, #0072ff);
            color: #ffffff;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: 800;
            font-size: 1rem;
            cursor: pointer;
            box-shadow: 0 4px 14px rgba(0, 114, 255, 0.4);
            margin-top: 10px;
        }

        /* ESTILOS ÁLBUMES DE USUARIOS Y RESEÑAS */
        .album-card {
            background-color: var(--black-input);
            border: 1px solid var(--black-border);
            border-radius: 10px;
            padding: 16px;
            margin-bottom: 16px;
        }

        .album-header {
            display: flex;
            align-items: center;
            gap: 12px;
            border-bottom: 1px solid var(--black-border);
            padding-bottom: 10px;
            margin-bottom: 12px;
        }

        .album-user-avatar {
            width: 38px;
            height: 38px;
            border-radius: 50%;
            background-color: var(--accent-cyan);
            color: var(--black-input);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1rem;
        }

        .album-title {
            font-size: 1rem;
            font-weight: 700;
            color: var(--accent-cyan);
        }

        .route-item {
            background-color: var(--black-card);
            border-radius: 8px;
            padding: 12px;
            margin-bottom: 12px;
            border-left: 4px solid var(--accent-cyan);
        }

        .route-header-flex {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
        }

        .route-title {
            font-size: 0.95rem;
            font-weight: 700;
            color: var(--text-light);
        }

        .sport-badge {
            display: inline-block;
            background-color: rgba(0, 210, 255, 0.15);
            color: var(--accent-cyan);
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 0.75rem;
            font-weight: 700;
            margin-top: 4px;
            margin-bottom: 6px;
        }

        .stars-display {
            color: var(--star-color);
            font-size: 0.85rem;
            margin-bottom: 6px;
        }

        .route-info {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 8px;
            line-height: 1.4;
        }

        /* GRID PARA MOSTRAR MÚLTIPLES ARCHIVOS EN LA RESEÑA */
        .media-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
            gap: 8px;
            margin-top: 10px;
        }

        .media-display-item {
            width: 100%;
            height: 120px;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid var(--black-border);
        }

        .btn-delete {
            background-color: transparent;
            color: var(--danger-color);
            border: 1px solid var(--danger-color);
            padding: 4px 8px;
            border-radius: 5px;
            font-size: 0.75rem;
            cursor: pointer;
            margin-top: 8px;
        }

        /* RESPONSIVE EN MÓVILES */
        @media (max-width: 820px) {
            .app-layout {
                flex-direction: column;
            }

            .sidebar {
                width: 100%;
                max-height: none;
                position: static;
            }
        }
    </style>
</head>
<body>

    <header>
        <img src="watermarked_img_12913599742035088314.jpg" alt="Logo Armadillo">
        <div class="header-title">
            <h1>ARMADILLO OUTDOOR</h1>
            <p>Álbumes, Sitios y Reseñas Deportivo-Outdoor</p>
        </div>
    </header>

    <div class="app-layout">
        <!-- BARRA LATERAL IZQUIERDA: BÚSQUEDA + BOTÓN Y LISTA DE LUGARES -->
        <aside class="sidebar">
            <div class="search-add-bar">
                <div class="search-box">
                    <input type="text" id="searchInput" placeholder="Buscar sitio o reseña...">
                </div>
                <button id="btnOpenModal" class="btn-add-main" title="Registrar nueva reseña o sitio">+</button>
            </div>

            <div class="sidebar-header-row">
                <div class="sidebar-title">📍 Sitios Registrados</div>
                <button id="btnShowAll" class="btn-show-all" style="display:none;" onclick="clearFilter()">Ver Todos</button>
            </div>
            
            <div id="placesList" class="places-list">
                <!-- Se llena dinámicamente con los lugares guardados -->
            </div>
        </aside>

        <!-- ÁREA PRINCIPAL DERECHA: VER ÁLBUMES / RESEÑAS -->
        <main class="main-content">
            <div class="card">
                <div id="filterBanner" class="filter-status-banner" style="display: none;">
                    <span id="filterText">Filtrando por sitio...</span>
                    <button class="btn-show-all" onclick="clearFilter()">Mostrar todos</button>
                </div>

                <h2>📁 Reseñas y Álbumes por Usuario</h2>
                <div id="albumsList">
                    <!-- Se puebla dinámicamente -->
                </div>
            </div>
        </main>
    </div>

    <!-- INTERFAZ MODAL PARA REGISTRAR NUEVA RESEÑA O SITIO -->
    <div id="modalFormOverlay" class="modal-overlay">
        <div class="modal-container">
            <div class="modal-header">
                <h2 id="modalTitle">➕ Registrar Nueva Reseña</h2>
                <button id="btnCloseModal" class="btn-close-modal">&times;</button>
            </div>

            <div id="existingSiteBadge" class="existing-site-tag" style="display:none;"></div>

            <form id="routeForm">
                <div class="upload-top-box">
                    <label for="mediaInput">📸 / 🎥 Subir Fotos y/o Videos (Múltiples)</label>
                    <p>Haz clic para seleccionar uno o varios archivos a la vez</p>
                    <!-- SE AÑADE EL ATRIBUTO multiple PARA PERMITIR SELECCIÓN MÚLTIPLE -->
                    <input type="file" id="mediaInput" accept="image/*,video/*" multiple>
                    <div id="mediaPreview" class="preview-container"></div>
                </div>

                <div class="form-group">
                    <label for="userName">Nombre del Deportista / Usuario:</label>
                    <input type="text" id="userName" required placeholder="Ej: Juan Pérez">
                </div>

                <div class="form-group">
                    <label for="routeName">Nombre del Sitio o Ruta:</label>
                    <input type="text" id="routeName" list="existingPlacesList" required placeholder="Selecciona o escribe el nombre del sitio">
                    <datalist id="existingPlacesList"></datalist>
                </div>

                <div class="form-group">
                    <label for="sportType">Deporte / Actividad:</label>
                    <input type="text" id="sportType" required placeholder="Escribe la actividad (Ej: Ciclismo, Trail Running...)">
                </div>

                <div class="form-group">
                    <label for="location">Ubicación / Punto de Partida:</label>
                    <input type="text" id="location" required placeholder="Ej: Entrada Principal / Av. Las Monjas">
                </div>

                <div class="form-group">
                    <label>Calificación del Lugar (Máx 5 Estrellas):</label>
                    <div class="star-rating-input">
                        <input type="radio" id="star5" name="rating" value="5" required><label for="star5">★</label>
                        <input type="radio" id="star4" name="rating" value="4"><label for="star4">★</label>
                        <input type="radio" id="star3" name="rating" value="3"><label for="star3">★</label>
                        <input type="radio" id="star2" name="rating" value="2"><label for="star2">★</label>
                        <input type="radio" id="star1" name="rating" value="1"><label for="star1">★</label>
                    </div>
                </div>

                <div class="form-group">
                    <label for="comments">Reseña o Comentarios:</label>
                    <textarea id="comments" rows="3" placeholder="¿Qué tal el terreno, seguridad e iluminación?" required></textarea>
                </div>

                <button type="submit" class="btn-submit">Publicar Reseña</button>
            </form>
        </div>
    </div>

    <script>
        // Array para almacenar múltiples fotos/videos cargados
        let currentMediaList = [];
        let activeSiteFilter = '';

        // Controles de Modal
        const modal = document.getElementById('modalFormOverlay');
        const btnOpenModal = document.getElementById('btnOpenModal');
        const btnCloseModal = document.getElementById('btnCloseModal');
        const routeNameInput = document.getElementById('routeName');
        const locationInput = document.getElementById('location');
        const sportTypeInput = document.getElementById('sportType');
        const existingSiteBadge = document.getElementById('existingSiteBadge');

        btnOpenModal.addEventListener('click', () => {
            resetModalForm();
            modal.classList.add('active');
        });

        btnCloseModal.addEventListener('click', () => modal.classList.remove('active'));

        modal.addEventListener('click', (e) => {
            if (e.target === modal) modal.classList.remove('active');
        });

        function addReviewToSite(siteName, siteLocation, siteSport) {
            resetModalForm();
            routeNameInput.value = siteName;
            if (siteLocation) locationInput.value = siteLocation;
            if (siteSport) sportTypeInput.value = siteSport;

            existingSiteBadge.style.display = 'inline-block';
            existingSiteBadge.textContent = `📍 Añadiendo reseña para: ${siteName}`;

            modal.classList.add('active');
            document.getElementById('userName').focus();
        }

        routeNameInput.addEventListener('input', function(e) {
            const val = e.target.value.trim().toLowerCase();
            let entries = JSON.parse(localStorage.getItem('armadillo_user_albums')) || [];
            const match = entries.find(item => item.name.toLowerCase() === val);
            
            if (match) {
                if (!locationInput.value) locationInput.value = match.location;
                if (!sportTypeInput.value) sportTypeInput.value = match.sport;
                existingSiteBadge.style.display = 'inline-block';
                existingSiteBadge.textContent = `📍 Sitio existente detectado (${match.name})`;
            } else {
                existingSiteBadge.style.display = 'none';
            }
        });

        function resetModalForm() {
            document.getElementById('routeForm').reset();
            document.getElementById('mediaPreview').innerHTML = '';
            existingSiteBadge.style.display = 'none';
            currentMediaList = [];
        }

        // PROCESAR SUBIDA DE MÚLTIPLES ARCHIVOS (IMÁGENES Y VIDEOS)
        document.getElementById('mediaInput').addEventListener('change', async function(e) {
            const files = Array.from(e.target.files);
            if (files.length === 0) return;

            const readPromises = files.map(file => {
                return new Promise((resolve) => {
                    const reader = new FileReader();
                    reader.onload = (evt) => {
                        resolve({
                            type: file.type.startsWith('video') ? 'video' : 'image',
                            src: evt.target.result
                        });
                    };
                    reader.readAsDataURL(file);
                });
            });

            const newFiles = await Promise.all(readPromises);
            currentMediaList = currentMediaList.concat(newFiles);
            renderPreviews();
            this.value = ''; // Reset input para permitir volver a elegir más archivos
        });

        function renderPreviews() {
            const previewContainer = document.getElementById('mediaPreview');
            previewContainer.innerHTML = '';

            currentMediaList.forEach((media, index) => {
                const wrapper = document.createElement('div');
                wrapper.className = 'preview-item';

                const mediaElem = media.type === 'image'
                    ? `<img src="${media.src}">`
                    : `<video src="${media.src}" controls></video>`;

                wrapper.innerHTML = `
                    ${mediaElem}
                    <button type="button" class="btn-remove-preview" onclick="removeMediaFromPreview(${index})" title="Eliminar este archivo">&times;</button>
                `;
                previewContainer.appendChild(wrapper);
            });
        }

        function removeMediaFromPreview(index) {
            currentMediaList.splice(index, 1);
            renderPreviews();
        }

        // Guardar la reseña con la lista de fotos/videos
        document.getElementById('routeForm').addEventListener('submit', function(e) {
            e.preventDefault();

            const userName = document.getElementById('userName').value.trim();
            const name = routeNameInput.value.trim();
            const sport = sportTypeInput.value.trim();
            const location = locationInput.value.trim();
            const rating = document.querySelector('input[name="rating"]:checked').value;
            const comments = document.getElementById('comments').value.trim();

            const newEntry = {
                id: Date.now(),
                userName,
                name,
                sport,
                location,
                rating: parseInt(rating),
                comments,
                media: [...currentMediaList] // Guarda el array de elementos multimedia
            };

            saveEntry(newEntry);
            resetModalForm();
            modal.classList.remove('active');
            loadAll();
        });

        function saveEntry(entry) {
            let entries = JSON.parse(localStorage.getItem('armadillo_user_albums')) || [];
            entries.unshift(entry);
            localStorage.setItem('armadillo_user_albums', JSON.stringify(entries));
        }

        document.getElementById('searchInput').addEventListener('input', function(e) {
            const query = e.target.value.toLowerCase().trim();
            activeSiteFilter = query;
            loadAll();
        });

        function clearFilter() {
            activeSiteFilter = '';
            document.getElementById('searchInput').value = '';
            loadAll();
        }

        function filterBySite(siteName) {
            activeSiteFilter = siteName.toLowerCase();
            document.getElementById('searchInput').value = siteName;
            loadAll();
        }

        function loadAll() {
            let entries = JSON.parse(localStorage.getItem('armadillo_user_albums')) || [];

            updateDataList(entries);
            renderPlacesSidebar(entries);

            let filteredEntries = entries;
            if (activeSiteFilter) {
                filteredEntries = entries.filter(e => 
                    e.name.toLowerCase().includes(activeSiteFilter) || 
                    e.location.toLowerCase().includes(activeSiteFilter) ||
                    e.sport.toLowerCase().includes(activeSiteFilter) ||
                    e.userName.toLowerCase().includes(activeSiteFilter)
                );

                document.getElementById('filterBanner').style.display = 'flex';
                document.getElementById('filterText').textContent = `Mostrando reseñas relacionadas con: "${activeSiteFilter}"`;
                document.getElementById('btnShowAll').style.display = 'inline-block';
            } else {
                document.getElementById('filterBanner').style.display = 'none';
                document.getElementById('btnShowAll').style.display = 'none';
            }

            renderAlbumsMain(filteredEntries);
        }

        function updateDataList(entries) {
            const datalist = document.getElementById('existingPlacesList');
            datalist.innerHTML = '';
            
            const placesMap = new Set();
            entries.forEach(e => placesMap.add(e.name));

            placesMap.forEach(placeName => {
                const option = document.createElement('option');
                option.value = placeName;
                datalist.appendChild(option);
            });
        }

        function renderPlacesSidebar(entries) {
            const container = document.getElementById('placesList');
            container.innerHTML = '';

            if (entries.length === 0) {
                container.innerHTML = '<p style="font-size: 0.8rem; color: var(--text-muted); text-align: center;">No hay sitios registrados.</p>';
                return;
            }

            const placesMap = {};
            entries.forEach(item => {
                const key = item.name.toLowerCase();
                if (!placesMap[key]) {
                    placesMap[key] = {
                        name: item.name,
                        location: item.location,
                        sport: item.sport,
                        count: 0
                    };
                }
                placesMap[key].count += 1;
            });

            Object.values(placesMap).forEach(place => {
                const div = document.createElement('div');
                div.className = 'place-card-item';

                div.innerHTML = `
                    <div class="place-info" onclick="filterBySite('${place.name.replace(/'/g, "\\'")}')">
                        <h4>
                            📍 ${place.name}
                            <span class="place-badge-count" title="Número de reseñas">${place.count} ${place.count === 1 ? 'reseña' : 'reseñas'}</span>
                        </h4>
                        <p>${place.sport} • ${place.location}</p>
                    </div>
                    <button class="btn-add-review-site" onclick="addReviewToSite('${place.name.replace(/'/g, "\\'")}', '${place.location.replace(/'/g, "\\'")}', '${place.sport.replace(/'/g, "\\'")}')">
                        + Reseña
                    </button>
                `;

                container.appendChild(div);
            });
        }

        function renderAlbumsMain(entries) {
            const container = document.getElementById('albumsList');
            container.innerHTML = '';

            if (entries.length === 0) {
                container.innerHTML = '<p style="text-align:center; color: var(--text-muted); padding:10px;">No se encontraron reseñas para esta búsqueda.</p>';
                return;
            }

            const albumsByUser = entries.reduce((acc, item) => {
                const userKey = item.userName.toLowerCase();
                if (!acc[userKey]) {
                    acc[userKey] = {
                        displayName: item.userName,
                        items: []
                    };
                }
                acc[userKey].items.push(item);
                return acc;
            }, {});

            Object.values(albumsByUser).forEach(album => {
                const albumCard = document.createElement('div');
                albumCard.className = 'album-card';

                const initial = album.displayName.charAt(0).toUpperCase();

                let itemsHTML = album.items.map(r => {
                    const stars = '★'.repeat(r.rating) + '☆'.repeat(5 - r.rating);
                    
                    // COMPATIBILIDAD CON REGISTROS ANTIGUOS (SI ERA OBJETO ÚNICO O ARRAY)
                    let mediaHTML = '';
                    if (r.media) {
                        const mediaArray = Array.isArray(r.media) ? r.media : [r.media];
                        if (mediaArray.length > 0) {
                            const mediaItemsHTML = mediaArray.map(m => {
                                return m.type === 'image'
                                    ? `<img src="${m.src}" class="media-display-item">`
                                    : `<video src="${m.src}" controls class="media-display-item"></video>`;
                            }).join('');
                            
                            mediaHTML = `<div class="media-grid">${mediaItemsHTML}</div>`;
                        }
                    }

                    return `
                        <div class="route-item">
                            <div class="route-header-flex">
                                <div>
                                    <div class="route-title">📍 ${r.name}</div>
                                    <span class="sport-badge">${r.sport}</span>
                                </div>
                                <button class="btn-add-review-site" onclick="addReviewToSite('${r.name.replace(/'/g, "\\'")}', '${r.location.replace(/'/g, "\\'")}', '${r.sport.replace(/'/g, "\\'")}')">
                                    + Reseñar sitio
                                </button>
                            </div>
                            <div class="stars-display">${stars} (${r.rating}/5)</div>
                            <div class="route-info">
                                <strong>📍 Ubicación:</strong> ${r.location}<br>
                                <strong>💬 Reseña:</strong> ${r.comments}
                            </div>
                            ${mediaHTML}
                            <button class="btn-delete" onclick="deleteEntry(${r.id})">Eliminar</button>
                        </div>
                    `;
                }).join('');

                albumCard.innerHTML = `
                    <div class="album-header">
                        <div class="album-user-avatar">${initial}</div>
                        <div class="album-title">Álbum de ${album.displayName} (${album.items.length})</div>
                    </div>
                    ${itemsHTML}
                `;

                container.appendChild(albumCard);
            });
        }

        function deleteEntry(id) {
            let entries = JSON.parse(localStorage.getItem('armadillo_user_albums')) || [];
            entries = entries.filter(r => r.id !== id);
            localStorage.setItem('armadillo_user_albums', JSON.stringify(entries));
            loadAll();
        }

        document.addEventListener('DOMContentLoaded', () => loadAll());
    </script>
</body>
</html>
