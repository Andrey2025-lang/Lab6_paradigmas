# Laboratorio: espacio de trabajo y memoria persistente

**Estudiante:** Andrey Gonzalez Villegas. **Modalidad:** individual.

Este repositorio (`Lab6_paradigmas`) reúne la entrega de las **dos primeras partes** de la guía `Lab8.docx`: preparar el espacio de trabajo y configurar memoria persistente para continuar UNA Chat. El nombre del repositorio se conserva por decisión del estudiante.

**Fuera del alcance:** instalar `rsc-harness`, implementar Auth0 y desplegar en Vercel. Como trabajo adicional solicitado por Andrey, se mejoró el frontend de su copia local de Lab5; no se duplica el código del chat en esta entrega.

## 1. Organización

```text
Lab6_paradigmas/
├── AGENTS.md                    # Instrucciones del asistente y de memoria
├── README.md                    # Esta guía
├── LICENSE                      # Licencia de la plantilla
├── .gitignore
├── Workspace.code-workspace     # Abre esta raíz en el editor
├── Knowledge/
│   └── AGENTS.md                 # Referencias compartidas
├── Skills/
│   └── AGENTS.md                 # Guía de procedimientos; no es un harness
├── brain/
│   ├── INDEX.md                  # Índice: nota, cuándo usarla y ruta
│   ├── Home.md                   # Mapa de enlaces
│   ├── Owner.md                  # Propietario y zona horaria
│   ├── daily-log/
│   │   ├── status.md             # Estado vigente y pendientes
│   │   └── YYYY-MM-DD.md         # Registro diario de avances
│   └── Working/
│       ├── UNA Chat.md           # Contexto confirmado del proyecto
│       ├── Tickets and recent work.md
│       ├── How I work.md
│       ├── Environments.md
│       └── Gaps.md
└── Repos/
    ├── AGENTS.md                 # Índice de repositorios, incluido en la entrega
    └── Lab5/                     # Clon local del chat; NO se incluye en Git de Lab6
```

Lab6 guarda organización, documentación y memoria. [Lab5](https://github.com/Andrey2025-lang/Lab5) guarda el código del chat. Cada uno conserva su propio control de versiones; **Lab5 no es un submódulo ni se duplica en esta entrega**.

## 2. Abrir el espacio y obtener el chat

Requisitos: Git y un editor. Para ejecutar el chat, también Node.js y npm; Obsidian es opcional.

```powershell
git clone https://github.com/Andrey2025-lang/Lab6_paradigmas.git
cd Lab6_paradigmas
git clone https://github.com/Andrey2025-lang/Lab5.git Repos/Lab5
```

Abrir `Workspace.code-workspace` en el editor e iniciar el asistente desde esa raíz. Si una carpeta ya existe, no repetir el clon encima: revisar primero su contenido.

El frontend mejorado ya está publicado en **Lab5**, commit [`510ee97`](https://github.com/Andrey2025-lang/Lab5/commit/510ee97cb4331b297937d112c99d81ec6c68bae1). Los comandos anteriores obtienen ese diseño desde su rama `main`. Andrey autorizó también publicar esta entrega de Lab6; su comprobación final se registra en la memoria.

### Exclusión de repositorios

Las reglas principales son:

```gitignore
/Repos/*
!/Repos/AGENTS.md
/brain/.obsidian/workspace.json
```

Permiten entregar el índice sin incorporar el clon ni su historial. También se excluyen dependencias, variables de entorno reales e informes generados.

## 3. Qué se revisó del chat

Revisión actual: `Lab5`, rama `main`, commit `510ee97` (`Mejora interfaz de UNA Chat y agrega pruebas responsivas`), sobre la base inicial `40c0608`.

- `server.js`: servidor Express, entrega el HTML y retransmite mensajes mediante Socket.IO.
- `index.html`: interfaz adaptable con tema claro y rojo UNA, burbujas, nombre, hora y estado de conexión; JavaScript nativo y cliente Socket.IO servido desde la propia aplicación.
- `libs/unalib.js`: validaciones y transformación de mensajes, enlaces de imagen y YouTube.
- `package.json`: comandos `start` y `test`, dependencias de la aplicación y herramientas de pruebas.
- `test/`: pruebas unitarias, de integración y de extremo a extremo con Playwright.
- Puerto predeterminado: `3001`; configurable con la variable `PORT`.

### Ejecución local del chat

Desde la raíz de Lab6:

```powershell
cd Repos/Lab5
npm ci
npm start
```

Abrir `http://localhost:3001`. Las bibliotecas de la interfaz se sirven localmente; las imágenes y videos externos dependen de Internet y de sus servicios.

Si aparece `EADDRINUSE`, el puerto ya está ocupado. Revisar primero si el chat está abierto en ese puerto, o iniciar otra instancia en un puerto libre:

```powershell
$env:PORT = "3003"
npm start
```

En ese caso abrir `http://localhost:3003`. Para las pruebas E2E con la configuración original debe haber un servidor en `3001`.

Comandos de pruebas existentes, desde `Repos/Lab5`:

```powershell
npm test
```

Ejecuta Jest sobre las pruebas unitarias y de integración; estas últimas usan el puerto `3002`. Para Playwright, la configuración actual requiere iniciar el servidor por separado en `3001`, instalar sus navegadores (`npx playwright install`) y ejecutar `npx playwright test`. No iniciar otro servidor en el mismo puerto.

El clon de referencia se actualizó mediante avance rápido a `510ee97`, se instalaron sus dependencias con `npm ci` y pasaron **6 pruebas Jest y 12 pruebas E2E en Chromium** usando un servidor aislado. Las pruebas realizadas no equivalen a una auditoría completa de seguridad. npm mostró una advertencia sobre la dependencia transitiva antigua `glob`; no se actualizaron dependencias como parte de esta entrega.

### Copia local distinta

La carpeta original de Andrey, llamada `antes`, ya tenía cambios locales de interfaz y dependencias. Se mejoró su interfaz y se publicaron **solo `index.html`, `test/e2e/chat.spec.js` y `test/e2e/interface.spec.js`**. Sus cambios previos de `package.json` y `package-lock.json` siguen locales y no se incluyeron. El clon de esta entrega se actualizó desde GitHub sin mezclar esas dependencias. El detalle de la ubicación local está en `brain/Working/Environments.md`.

### Nuevo frontend publicado y cómo obtenerlo al clonar

El diseño mejorado está en **Lab5, commit `510ee97`**, además de las copias locales: tema claro con acentos rojos, burbujas con autor y hora, formulario adaptable a celular y estado real de conexión. Usa el cliente Socket.IO servido por el propio servidor y JavaScript nativo, sin CDN para sus bibliotecas ni dependencias nuevas. Imágenes y videos externos siguen necesitando Internet.

Para verlo, seguir la clonación e instalación de la sección 2 y ejecutar `npm start` desde `Repos/Lab5`.

**El comando `git clone` de este README ya descarga el frontend nuevo.** No es necesario copiar el chat dentro del Git de Lab6 ni crear `chat/`.

Verificaciones realizadas sobre `antes`, con sus dependencias ya instaladas:

- `npm test -- --runInBand`: **6 pruebas correctas** en 2 suites.
- Playwright en Chromium headless: **12 pruebas correctas**, incluidas 3 existentes y 9 nuevas para la interfaz. Se usó una configuración temporal fuera del repositorio y un servidor de prueba aislado.
- Comprobados mensajes entre dos clientes, Enter, desconexión/reconexión, nombres como texto, anchos de 320/390/768/1440 px e imágenes/videos sin desbordamiento.
- Revisadas capturas de escritorio y celular. `package.json` y `package-lock.json` no fueron modificados durante la mejora.

No se ejecutaron Firefox/WebKit. Los casos de seguridad existentes que pasaron no garantizan saneamiento completo de todo HTML recibido.

## 4. Memoria persistente: qué se creó y para qué sirve

Las instrucciones de `obsidian-brain-instructions 1.md` se integraron completas en `AGENTS.md`, conservando su licencia. La memoria activa está en **`brain/`**, no en una segunda carpeta dentro de `Knowledge/`.

- **`INDEX.md` y `Home.md`:** encontrar notas y navegar mediante enlaces `[[wikilinks]]`.
- **`Owner.md`:** identificar al propietario y su zona horaria: Costa Rica, `America/Costa_Rica` (UTC−6).
- **`daily-log/status.md`:** saber qué está listo, qué falta y qué bloquea el trabajo.
- **Diario por fecha:** conservar avances y decisiones, agregando entradas sin borrar registros anteriores.
- **`Working/`:** conservar contexto de UNA Chat, preferencias, rutas, tareas y dudas pendientes.

### Uso en próximas sesiones

1. Al iniciar: leer `AGENTS.md`, el estado actual, el diario del día si existe y `INDEX.md`; consultar solo las notas relevantes.
2. Durante el trabajo: registrar avances, decisiones y bloqueos en el diario; guardar preferencias y hallazgos en su nota correspondiente.
3. Al terminar: actualizar el estado vigente y las notas duraderas; enlazar las nuevas notas desde índice e inicio.

Para comprobarlo en una conversación nueva, abierta **en la raíz de Lab6**, pedir:

> Lee las instrucciones y la memoria. Dime el alcance del laboratorio, qué está listo, dónde está el chat y qué queda pendiente.

Andrey realizó la prueba desde la nueva raíz de Lab6 y compartió una respuesta que recuperó correctamente identidad, alcance, ubicaciones y pendientes. La sesión de comprobación no modificó archivos; el resultado se registró posteriormente en el diario.

Opcional: abrir `brain/` como bóveda en Obsidian para explorar notas y su grafo. No es necesario instalarlo para usar los Markdown.

## 5. Comprobación y pendientes de entrega

- Espacio organizado y clon independiente del Laboratorio 5.
- Memoria con propietario, contexto confirmado, preferencias, estado y diario.
- Reglas Git para conservar `Repos/AGENTS.md` y excluir los clones.
- Comprobados los 18 archivos candidatos de entrega, ocho casos de exclusión Git, enlaces Markdown y wikilinks, rutas del índice e integración íntegra de instrucciones y licencia. Clon Lab5 limpio en la revisión publicada, con instalación reproducible y pruebas correctas.
- No se añadieron Auth0, harness, secretos ni despliegue.
- Pendiente del estudiante: confirmar con el profesor el formato de evidencias para las dos primeras partes.
- Publicación autorizada por Andrey: interfaz/pruebas en Lab5 y documentación/memoria en Lab6. No guardar contraseñas, tokens ni claves; no incorporar clones, dependencias instaladas ni secretos al Git de Lab6.
