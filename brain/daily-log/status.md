# Estado actual

Resumen vigente para retomar el trabajo; no es un historial.

Created 2026-10-28

## Foco

Finalizar publicación autorizada de Lab6 y verificación de clonación. Lab5 ya publicado con el frontend mejorado; sin harness, Auth0 ni despliegue.

## Completado — 2026-10-28

- `Repos/AGENTS.md` y excepciones de `.gitignore` preparados.
- Andrey eligió Lab6 como repositorio de entrega; se preparó a partir del espacio existente sin copiar su `.git` ni borrar la plantilla original.
- Lab5 publicado y clonado en `Repos/Lab5/`, rama `main`, commit `510ee97`, con Git independiente y excluido del Git de Lab6.
- Chat localizado: Node.js, Express y Socket.IO, puerto predeterminado `3001`. Contexto, estructura y comandos revisados en [[Working/UNA Chat|UNA Chat]].
- Conservados los cambios previos de la copia original `antes`; no se mezclaron con el clon. La mejora posterior autorizada se describe a continuación.
- Andrey autorizó mejorar el frontend en `antes`: implementado diseño claro con rojo UNA, burbujas, estado real de conexión y formulario adaptable. Conservados backend y cambios previos de dependencias; no se creó `chat/`. El clon recibió después la revisión publicada desde GitHub.
- Memoria activa en esta raíz, `brain/`; instrucciones originales completas y licencia conservadas en `AGENTS.md`. README explica organización, reconstrucción y uso de la memoria.
- En la revisión inicial se comprobó sintaxis con `node --check`; las suites se ejecutaron primero en `antes` y luego también sobre el clon limpio de la revisión publicada.
- Interfaz/pruebas publicadas en Lab5 como `510ee97`, con autorización posterior de Andrey. Se dejaron fuera `package.json` y `package-lock.json` de `antes`; sus cambios siguen locales.
- Clon de referencia actualizado por avance rápido desde GitHub e instalado con `npm ci`; limpio y revalidado con 6 pruebas Jest y 12 E2E Chromium correctas, usando puerto aislado `3219`.
- Validación de la mejora: 6 pruebas Jest y 12 pruebas Playwright Chromium correctas; capturas de escritorio/celular revisadas. Se usaron dependencias ya instaladas, sin modificar `package.json` ni `package-lock.json`.
- Validación final superada: 18 archivos candidatos previstos, instrucciones originales y licencia íntegras, ocho casos de exclusión Git, enlaces Markdown y wikilinks, rutas del índice, clon Lab5 limpio y `git diff --check`. Sin coincidencias de los patrones de claves/tokens revisados; no sustituye revisión manual.
- El espacio de origen conserva sus archivos y apunta a esta entrega; no mantener ambas memorias activas.
- Recuperación de memoria desde la nueva raíz comprobada: Andrey compartió la respuesta de una sesión nueva que identificó correctamente identidad, alcance, ubicaciones y pendientes. Se registra ahora, pues esa sesión no modificó archivos.

## Pendientes

- Publicar Lab6 y verificar que una clonación nueva, siguiendo el README, contenga la documentación/memoria y descargue el nuevo frontend desde Lab5.
- Confirmar el formato de entrega de las dos primeras partes con el profesor.

## Esperando

- Andrey/profesor: confirmar formato de entrega para las dos primeras partes, no definido por separado en el documento.
- No hay bloqueo de autorización: Andrey pidió completar la publicación. No realizar nuevas funcionalidades ni publicaciones ajenas al alcance.
