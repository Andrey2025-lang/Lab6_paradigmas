# UNA Chat

Contexto confirmado del chat original y límites de la revisión.

Created 2026-10-28

## Current status — 2026-10-28

- Interfaz y pruebas publicadas en Lab5, commit `510ee97cb4331b297937d112c99d81ec6c68bae1`. Solo se incluyeron `index.html`, `test/e2e/chat.spec.js` y `test/e2e/interface.spec.js`; los cambios previos de dependencias de `antes` siguen locales.
- Clon `Repos/Lab5/` actualizado limpiamente por avance rápido a esa revisión, con `npm ci` y Git sin cambios. También sobre la versión publicada pasaron 6 pruebas Jest y 12 E2E Chromium; la mejora ya llega a nuevas clonaciones desde el README.
- npm avisó sobre `glob` antiguo y scripts de instalación pendientes de aprobación; no se aprobaron scripts adicionales ni se actualizaron dependencias. Las suites de prueba ejecutadas pasaron de todos modos.
- Pendiente cerrar la publicación/verificación de Lab6 y confirmar evidencias con el profesor. Auth0 y Vercel siguen para después.

## Previous status — 2026-10-28, mejora local antes de publicar

- Por solicitud expresa de Andrey se mejoró `antes/index.html`: diseño claro con acentos rojos, burbujas, avatares y hora, bienvenida, formulario etiquetado, adaptación móvil y estado real de conexión. Se conservaron el protocolo Socket.IO y el contenido multimedia.
- El cliente Socket.IO se sirve desde `/socket.io/socket.io.js`; el frontend mejorado usa JavaScript nativo, sin jQuery ni CDN para sus bibliotecas. No se añadieron dependencias.
- Actualizadas las tres referencias del botón en `test/e2e/chat.spec.js` de Send a Enviar y añadido `test/e2e/interface.spec.js` con nueve casos de interfaz. El backend no se modificó.
- Verificaciones en `antes`: Jest, 2 suites y 6 pruebas correctas; Playwright en Chromium sin interfaz, 12 pruebas correctas (3 existentes y 9 nuevas). Se comprobaron Enter, dos clientes, desconexión/reconexión, nombre como texto, anchos de 320/390/768/1440 px y multimedia sin desbordamiento.
- Se corrigió durante las pruebas el desbordamiento de imágenes con estilos inline del servidor. Se revisaron capturas de escritorio y celular; los archivos de prueba y capturas temporales están fuera de la entrega.
- `package.json` y `package-lock.json` conservan exactamente los hashes anteriores a esta mejora; sus modificaciones previas pertenecen a Andrey. No se deben incluir automáticamente en un futuro commit de la interfaz.
- El clon `Repos/Lab5/` sigue limpio en `40c0608`, con el frontend anterior. La mejora todavía no está en GitHub: no hubo commit, push, pull ni sincronización entre copias.
- Para que el comando del README descargue el diseño nuevo, revisar y autorizar posteriormente el commit y push al repositorio Lab5. No crear una copia adicional del chat en Lab6.

## Previous status — 2026-10-28, revisión inicial del clon

- Código localizado y clonado desde https://github.com/Andrey2025-lang/Lab5.git en `Repos/Lab5/`, relativo a la raíz de Lab6.
- Rama observada: `main`. Commit base: `40c0608`, `Lab 5 Seguridad Informatica - Completado`.
- El chat conserva su propio Git y queda excluido del Git del repositorio de entrega `Lab6_paradigmas`.
- La copia local original `antes` apunta al mismo origen y commit base, pero tiene cambios sin commit en `index.html`, `package.json` y `package-lock.json`. Se dejó intacta; no se mezcló con el clon. Ubicaciones en [[Working/Environments|Entornos]].

## Estructura confirmada del clon de referencia

- `server.js`: Express sobre servidor HTTP y Socket.IO. Ruta `/` entrega `index.html`; evento `Evento-Mensaje-Server` valida y retransmite mensajes a todos los clientes.
- `index.html` actual: interfaz con nombre y mensaje, JavaScript nativo y Socket.IO servido localmente. La versión inicial usaba jQuery y CDN; no se auditó completamente el HTML de mensajes generado por el backend.
- `libs/unalib.js`: validaciones de teléfono/URL, detección de imágenes y YouTube, generación de HTML y saneamiento parcial de mensajes. No asumir protección completa contra XSS por existir estas funciones.
- `test/una-lib.test.js` y `test/integration/chat.test.js`: seleccionados por Jest en `package.json`.
- `test/e2e/chat.spec.js` y `playwright.config.js`: pruebas de extremo a extremo para imágenes, video y caso de script; requieren servidor en `3001` y navegadores de Playwright.
- `README.md` del chat contiene únicamente `# Lab5`; la guía de ejecución revisada se documentó en el README de Lab6.

## Ejecución y pruebas

- Desde `Repos/Lab5/`: `npm ci`, luego `npm start`; URL predeterminada `http://localhost:3001`.
- `PORT` permite cambiar el puerto. Con `NODE_ENV=test`, `server.js` no inicia la escucha por sí mismo.
- `npm test` ejecuta Jest; la integración inicia un servidor en `3002`.
- Playwright: iniciar el chat por separado en `3001`, instalar navegadores con `npx playwright install` y ejecutar `npx playwright test`. `webServer` está comentado y `headless` es `false`.
- Entorno observado: Node.js `v26.4.0`, npm `11.17.0`. Son versiones disponibles, no una versión mínima confirmada del proyecto.
- En el diseño publicado las bibliotecas se sirven localmente; el contenido externo de imágenes y videos necesita Internet.

## Validación inicial del clon (antes de la mejora local)

- Revisados archivos, estado Git, origen, commit y diferencias de la copia local.
- `node --check server.js` y `node --check libs/unalib.js`: correctos.
- No se instalaron dependencias, arrancó el chat ni ejecutaron suites Jest/Playwright. No afirmar que las pruebas funcionales pasaron.
- No se modificó el código de Lab5 ni la copia original `antes`.

## Alcance

El laboratorio sigue limitado a organización y memoria. La mejora de interfaz en `antes` es un trabajo adicional autorizado por Andrey. No implementar harness, Auth0 ni despliegue. No descartar cambios previos, copiar automáticamente versiones entre repositorios ni publicar sin autorización. Los casos XSS que pasan no equivalen a una auditoría completa del saneamiento del backend.

Last reinforced 2026-10-28
