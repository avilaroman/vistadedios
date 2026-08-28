🤝 Contribuyendo a God's Eye View

Gracias por estar aquí. God's Eye View es una fundación abierta para inteligencia espacial en vivo en el navegador, ¡y mejora cuando más personas lo ejecutan, lo rompen y lo extienden!

🚀 Configuración inicial

Usa Node.js 24.14.x o 26.x (también requerido por package.json).

bash
git clone https://github.com/bilawalsidhu/gods-eye-view.git
cd gods-eye-view
nvm install 24.14.0
nvm use 24.14.0
npm install
./scripts/dev-fresh.sh        # o: GOOGLE_MAPS_API_KEY="…" npm run dev

Necesitas una clave de API de Google Maps con la API Map Tiles habilitada (consulta el README). La mayoría de capas de datos funcionan sin otras cuentas. En macOS, el lanzador extrae claves del Keychain; en cualquier plataforma puedes pasarlas como variables de entorno o usar un .env (copia .env.example).

Abre http://localhost:4173. Antes de enviar un PR ejecuta npm run build, npm test, y npm run test:track (el servidor dev debe estar activo) — los tres deben estar en verde. ✅

🎯 Buenas primeras contribuciones

Los lugares de mayor impacto para comenzar:

🌆 Agrega un paquete de fuente CCTV. Austin es la fuente de cámara de referencia. Agregar otra ciudad significa un catálogo de cámaras públicas limpio con coordenadas, atribución y URLs de fotogramas registrados en el servidor (el proxy solo obtiene URLs registradas — nunca proporcionadas por el cliente, ver SECURITY.md). Los paquetes de ciudades son el mejor primer paso.
🛰️ Agrega o mejora una capa de datos. Cada capa es un módulo independiente en src/data/<layer>.js que implementa la interfaz de capa (init/enable/disable/update/destroy/getStats, opcional getDetectableObjects/getStats). Usa una capa existente como plantilla.
🎙️ Extiende el control de voz. Las herramientas de voz se declaran del lado del servidor (GEV_REALTIME_TOOLS en vite.config.js) y se ejecutan del lado del cliente (src/voice/gevActions.js). Mantén la superficie de herramientas ajustada y las respuestas honestas (confirma solo lo que realmente pasó).
🎨 Agrega un estilo visual. Los estilos son shaders de post-procesamiento GLSL en src/styles/.
🐛 Corrige bugs / mejora la experiencia de primera ejecución. Ver docs/KNOWN-ISSUES.md.
⚡ Arquitectura en un minuto
Sin framework. Vanilla JS + CesiumJS + Vite.
La UI vive en src/ui.js (paneles, HUD, estilos, la fachada de control). La lógica de capas vive en src/data/<layer>.js. Mantenlos separados.
Los secretos se quedan del lado del servidor. Cualquier cosa que necesite una clave privada pasa por un proxy de Vite en vite.config.js. El navegador solo ve la clave de Google Maps (que restrictas) y tokens efímeros.
docs/CURRENT-STATE.md es la referencia autorizada en tiempo de ejecución — léela primero.
📝 Estilo de código
Módulos ES, indentación de 2 espacios, comillas simples, punto y coma.
JSDoc en funciones exportadas/públicas.
Coincide con el código circundante — densidad de comentarios, nombres e idioma.
Prefiere commits pequeños y revisables. Los prefijos de estilo de commit convencional (feat:, fix:, perf:, docs:) se aprecian pero no son obligatorios.
📤 Solicitudes de cambios (Pull Requests)
Crea una rama a partir de main.
Mantén npm run build, npm test, y npm run test:track en verde y evita nuevos errores en la consola.
Si cambias el comportamiento en tiempo de ejecución, actualiza docs/CURRENT-STATE.md y CHANGELOG.md en el mismo PR.
Si agregas o cambias una fuente de datos, actualiza DATA_SOURCES.md con su licencia y atribución. No agregues datos que no tengas derecho a redistribuir — obtén el acceso en tiempo de ejecución en su lugar.
Describe qué cambiaste y cómo lo verificaste (capturas de pantalla bienvenidas para cualquier cosa visual). 📸
🏛️ Reglas básicas
Esta es una herramienta para datos públicos. No agregues scraping de fuentes cuyos términos lo prohíben, conjuntos de datos privados/pagos, o cualquier cosa que represente falsamente la inferencia de datos públicos como inteligencia autorizada.
Sé decente con los demás. Asume buena fe, mantén las cosas constructivas. 🤗

Al contribuir, aceptas que tus contribuciones están licenciadas bajo la Licencia MIT del proyecto.
