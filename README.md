# Cronograma de eventos Bukz 2026

Página pública con el calendario de eventos de todas las sedes Bukz. Cualquiera con el link puede verla; para crear, editar o eliminar eventos se pide la clave del equipo. Los datos se guardan en Google Sheets, así que lo que cambie una persona lo ve todo el equipo.

## Archivos

- `index.html` — la página (calendario, agenda y editor).
- `Code.gs` — el código que conecta la página con Google Sheets.
- `eventos.csv` — los 152 eventos actuales, listos para importar.

## Puesta en marcha (una sola vez, ~10 minutos)

### 1. Cargar los datos en Google Sheets
1. Abre la hoja **CRONOGRAMA DE EVENTOS BUKZ 2026** (o crea una nueva).
2. **Archivo → Importar → Subir** y elige `eventos.csv`.
3. En "Ubicación de importación" elige **Insertar hojas nuevas** y desmarca **Convertir texto en números, fechas y fórmulas**.
4. Revisa que la pestaña nueva se llame exactamente `eventos`.

### 2. Publicar la conexión (Apps Script)
1. En la misma hoja: **Extensiones → Apps Script**.
2. Borra lo que haya y pega el contenido de `Code.gs`.
3. Cambia `CLAVE` por la clave que usará el equipo para editar.
4. **Implementar → Nueva implementación → tipo: Aplicación web**.
   - Ejecutar como: **Yo**
   - Quién tiene acceso: **Cualquier usuario**
5. Autoriza los permisos y copia la **URL de la aplicación web** (termina en `/exec`).

### 3. Conectar la página
Abre `index.html`, busca `PEGA_AQUI_LA_URL_DE_APPS_SCRIPT` y reemplázalo por la URL del paso anterior.

### 4. Subir a GitHub y publicar
1. Crea un repositorio nuevo (por ejemplo `cronograma-bukz`).
2. **Add file → Upload files** y sube `index.html` (y si quieres `README.md`).
3. **Settings → Pages → Branch: main / root → Save**.
4. En uno o dos minutos la página queda en `https://TU-USUARIO.github.io/cronograma-bukz/`.

## Uso diario
- Ver: abrir el link. La página se actualiza sola cada minuto.
- Editar: tocar un evento, o el **+** de un día vacío, o **Nuevo evento**. La primera vez pide la clave y la recuerda en ese navegador.
- También se puede editar directamente en la pestaña `eventos` de la hoja; la página toma los cambios al recargar.

## Si cambias el código de Apps Script
Usa **Implementar → Administrar implementaciones → Editar → Versión nueva**. Así la URL se mantiene y no hay que tocar `index.html`.

## Seguridad
- Cualquiera con el link de GitHub ve los eventos (nombres, encargados, organizadores). No pongas datos privados de clientes en las notas.
- La clave protege la edición, pero no es una contraseña fuerte: compártela solo con el equipo y cámbiala en `Code.gs` si se filtra.
