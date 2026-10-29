# Entornos

Rutas y referencias del espacio; nunca valores de secretos.

Created 2026-10-28

- Sistema observado: Windows, PowerShell.
- Raíz absoluta activa de entrega: `C:/Users/andre/OneDrive/Documentos/U/2026 Ciclo II/Paradigmas/Lab 6/337f1600-9294-4f52-827b-df9ca2f7a25f/my-team-workspace/my-team-workspace/Repos/Lab6_paradigmas`.
- Archivo para abrir en el editor: `Workspace.code-workspace`, relativo a esa raíz.
- Memoria: `brain/`, relativa a esa raíz; no se mantiene una segunda memoria en `Knowledge/`.
- Documento y archivo de instrucciones originales: `../../../../Lab8.docx` y `../../../../obsidian-brain-instructions 1.md` desde esta raíz local. Son referencias locales externas, no requisitos para abrir una copia nueva de la entrega; las instrucciones completas están integradas en `AGENTS.md`.
- Repositorio de entrega: `https://github.com/Andrey2025-lang/Lab6_paradigmas.git`, raíz actual, rama `main`, publicación inicial `36b3b6b263cff41de552bdeca5f543d7ba0565b6`, sobre base `219dea8`; notas de cierre añadidas después de verificar esa publicación.
- Repositorio del chat: `https://github.com/Andrey2025-lang/Lab5.git`; clon en `Repos/Lab5/`, rama `main`, actualizado por avance rápido al commit publicado `510ee97cb4331b297937d112c99d81ec6c68bae1`.
- URL local del chat según `server.js`: `http://localhost:3001`; variable opcional `PORT`.
- Node.js disponible: `v26.4.0`; npm: `11.17.0`. Dependencias del clon publicado instaladas con `npm ci`, sin cambios en Git.
- Copia original: `C:/Users/andre/OneDrive/Documentos/U/2026 Ciclo II/Seguridad Informática/Lab/Lab5/antes`. Mismo origen y revisión publicada `510ee97` que el clon; únicamente `package.json` y `package-lock.json` conservan sus cambios locales previos, fuera del commit de interfaz.
- Actualización autorizada de interfaz: en esa copia `antes` se mejoraron `index.html` y las pruebas E2E. Las dependencias previas se conservaron intactas y no se mezcló con `Repos/Lab5/`. Usar `npm start` desde `antes` para ver el diseño nuevo en `http://localhost:3001`.
- Comprobaciones de la mejora: `npm test -- --runInBand` (6 pruebas) y Playwright Chromium headless (12 pruebas) mediante configuración temporal en `C:/Users/andre/AppData/Local/Temp/opencode/una-chat-ui-playwright.config.cjs`; servidor de prueba en `3217`, cerrado al terminar. Capturas de revisión en esa carpeta temporal, no en la entrega.
- Revalidación del clon publicado: mismas 6 pruebas Jest y 12 E2E correctas con configuración temporal `una-chat-publicado-playwright.config.cjs`, servidor aislado en `3219`. Los servidores de prueba se detuvieron; no se cerró la instancia que usa Andrey.
- Estas rutas absolutas son referencias de esta máquina. En otra copia, calcular la raíz de trabajo actual; no escribir en las rutas de Andrey por asumir que corresponden al entorno nuevo.
- Reconstrucción independiente comprobada en `C:/Users/andre/AppData/Local/Temp/opencode/una-entrega-verificacion-20261028-1937`: Lab6 clonado desde GitHub, seguido de Lab5 en Repos, con memoria presente, frontend nuevo y Git de Lab6 limpio. Esa copia temporal es solo verificación, no la raíz activa de trabajo.
- Plantilla de origen preservada: dos niveles por encima de esta raíz. Su memoria quedó como referencia de la preparación anterior; la activa es la de esta entrega.
- Cada clon mantiene su propio Git; el repositorio del espacio excluye el código clonado.
- Zona horaria de los diarios: `America/Costa_Rica` (UTC−6).

Last reinforced 2026-10-28
