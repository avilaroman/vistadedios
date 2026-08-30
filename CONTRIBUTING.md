# 👁️ Contribuyendo a Vista de Dios

Gracias por estar aquí. God's Eye View es una plataforma abierta para inteligencia espacial en tiempo real en el navegador, y mejora con cada nueva persona que la usa, la pone a prueba y la amplía.

## 🚀 Configuración

Usa Node.js 24.14.x o 26.x (esto también se aplica mediante `package.json`).

```bash
git clone https://github.com/bilawalsidhu/gods-eye-view.git
cd gods-eye-view
nvm install 24.14.0
nvm use 24.14.0
npm install
./scripts/dev-fresh.sh # o: GOOGLE_MAPS_API_KEY="…" npm run dev
```

Necesitas una **clave API de Google Maps** con la API de mosaicos de mapas habilitada (consulta el [README](README.md#-api-keys)). La mayoría de las capas de datos funcionan sin otras cuentas. En macOS, el lanzador obtiene las claves del llavero; en cualquier plataforma, puedes pasarlas como variables de entorno o usar un archivo `.env` (copia `.env.example`).

Abre `http://localhost:4173`. Antes de enviar una solicitud de extracción, ejecuta `npm run build`, `npm test` y `npm run test:track` (el servidor de desarrollo debe estar activo). **Los tres comandos deben permanecer en verde.** ✅

## 🎯 Buenas primeras contribuciones

Los puntos de mayor impacto para empezar:

- **🌆 Añadir un paquete de fuentes de CCTV.** Austin es la fuente de referencia de cámaras. Añadir otra ciudad implica un catálogo público de cámaras limpio con coordenadas, atribución y URL de fotogramas registradas en el servidor (el proxy solo obtiene las URL registradas, nunca las proporcionadas por el cliente; consulta [SECURITY.md](SECURITY.md)). Los paquetes de ciudades son la mejor opción para empezar.

- **🛰️ Añadir o mejorar una capa de datos.** Cada capa es un módulo independiente en `src/data/<layer>.js` que implementa la interfaz de capa (`init/enable/disable/update/destroy/getStats`, opcionalmente `getDetectableObjects`/`getStats`). Utilice una capa existente como plantilla.

- **🎙️ Ampliar el control por voz.** Las herramientas de voz se declaran en el servidor (`GEV_REALTIME_TOOLS` en `vite.config.js`) y se ejecutan en el cliente (`src/voice/gevActions.js`). Mantenga la interfaz de la herramienta sencilla y las respuestas honestas (confirme solo lo que realmente sucedió).

- **🎨 Añadir un estilo visual.** Los estilos son sombreadores de posprocesamiento GLSL en `src/styles/`.

- **🐛 Corrección de errores / mejora de la experiencia inicial.** Consulta [docs/KNOWN-ISSUES.md](docs/KNOWN-ISSUES.md).

## 🏗️ Arquitectura en un minuto

- **🔧 Sin framework.** JavaScript puro + [CesiumJS](https://cesium.com/platform/cesiumjs/) + [Vite](https://vitejs.dev/).

- **📱 La interfaz de usuario se encuentra en `src/ui.js`** (paneles, HUD, estilos, la fachada de control). **La lógica de las capas se encuentra en `src/data/<layer>.js`.** Manténgalas separadas.

- **🔐 Los secretos se almacenan en el servidor.** Todo lo que requiere una clave privada pasa por un proxy Vite en `vite.config.js`. El navegador solo ve la clave de Google Maps (que usted restringe) y los tokens efímeros.

- **📖 `docs/CURRENT-STATE.md` es la referencia principal en tiempo de ejecución; léala primero.**

## 💻 Estilo de codificación

- 📝 Módulos ES, **sangría de 2 espacios, comillas simples, punto y coma.**
- 📚 JSDoc para funciones exportadas/públicas.

- 🎯 Mantenga la misma densidad de comentarios, nomenclatura y estilo que el código circundante.

- ✨ Prefiera commits pequeños y revisables. Se agradecen los prefijos de estilo convencional (`feat:`, `fix:`, `perf:`, `docs:`), pero no son obligatorios.

## 🔄 Solicitudes de extracción

1. 🌿 Cree una rama a partir de `main`.

2. ✅ Mantenga `npm run build`, `npm test` y `npm run test:track` en verde y evite nuevos errores en la consola.

3. 📝 Si modifica el comportamiento en tiempo de ejecución, actualice `docs/CURRENT-STATE.md` y `CHANGELOG.md` en la misma solicitud de extracción.

4. 📊 Si añades o modificas una fuente de datos, actualiza [DATA_SOURCES.md](DATA_SOURCES.md) con su licencia y atribución. **No añadas datos que no tengas derecho a redistribuir**; obténlos en tiempo de ejecución.

5. 📸 Describe los cambios realizados y cómo los verificaste (se agradecen las capturas de pantalla para cualquier elemento visual).

## 📋 Reglas básicas

- 🌍 Esta es una herramienta para datos **públicos**. No añadas extracción de datos de fuentes cuyos términos lo prohíban, conjuntos de datos privados o de pago, ni nada que presente la inferencia de datos públicos como información fidedigna.

- 🤝 Sean respetuosos entre ustedes. Partan de la base de que actúan de buena fe y mantengan una actitud constructiva.

Al contribuir, aceptas que tus contribuciones se rigen por la [Licencia MIT](LICENSE) del proyecto. ⚖️
