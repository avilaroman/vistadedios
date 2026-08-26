<div align="center">

# 🌐 Vista desde la perspectiva de Dios

### Un simulador de satélite espía en tu navegador: descubre que las fuentes son públicas y los datos son reales.

Globo 3D fotorrealista. Aviones, barcos, satélites, terremotos, tráfico y cámaras públicas en tiempo real, con vistas modeladas claramente etiquetadas donde no hay transmisión en vivo. Control por voz manos libres con IA en tiempo real.

*Ningún lugar se queda atrás.*

![HUD orbital, globo terráqueo en tiempo real con seguimiento, terreno FLIR — luego CÓDIGO ABIERTO](docs/media/hero-open-source-reveal.gif)

<a href="https://www.youtube.com/@bilawalsidhu">

<img src="docs/media/youtube-popular-videos.png" alt="La serie de videos God's Eye View en YouTube" width="100%">
</a>

▶️ **Del proyecto detrás de la viral serie God's Eye View** *(anteriormente WorldView)* — [Más de 5 millones en YouTube](https://youtube.com/playlist?list=PL6qSg2I-7_koPbDnSMo0QeeHX_RknA2uv&si=nBGYMoHWQw41v93Q)

</div>

---

<div> align="center">

**[Inicio rápido](#-quick-start) · [Primeros cinco minutos](#-the-first-five-minutes) · [Comunícate con él](#-talk-to-it) · [Actualización en vivo](#-whats-on-the-globe) · [Funcionamiento interno](#-under-the-hood) · [Claves y costos](#-api-keys)**

</div>

---

## 🌍 ¿Por qué existe?

**Lo pediste, así que aquí está.** God's Eye View es de código abierto. Monitorea el mundo en vivo. Comunícate con él. Expándelo. Amplíalo.

La mayoría de las herramientas de inteligencia de código abierto son un montón de pestañas del navegador. Las señales son abundantes, pero la *interfaz* es el cuello de botella. God's Eye View transforma esas señales en un **lugar**: el mundo ya está transmitiendo —transpondedores de vuelo, balizas de barcos, elementos orbitales, sismógrafos, cámaras públicas— y esto lo hace visible en una Tierra 3D fotorrealista en tiempo real. No se requiere autorización de seguridad; es señal pública en todo momento, y la interfaz se ejecuta en tu navegador, bajo tu control.

> Parte de la magia reside en que parece una cabina de mando prohibida. La otra parte es que cada línea de código es inspeccionable.

Las capas en tiempo real se basan en fuentes públicas: el avión que cruza tu pantalla informa de telemetría, la cámara está instalada en una ubicación publicada y la posición de la ISS se propaga a partir de los elementos orbitales actuales. El cliente renderiza deliberadamente los vuelos con un intervalo de sondeo de retraso respecto al tiempo real para poder interpolar con fluidez. Algunas experiencias se modelan en lugar de ser en tiempo real: el tráfico sin llave se etiqueta como simulación, las posiciones de la cámara se estiman hasta su calibración y la reproducción del ascenso del lanzamiento se marca como «ESTIMACIÓN RECONSTRUIDA». Cada capa mantiene visible su origen y estado de actualización, incluyendo estados parciales, retrasados, simulados y no disponibles.

--

## 🎛️ Qué hace

- **🛩️ Vista de cabina:** Viaja dentro de un vuelo rastreado; la cámara mantiene el terreno bajo ti durante todo el descenso.

- **📡 Contactos:** Un listado de 250 km de todo lo que se encuentre cerca de tu objetivo: navega por aeronaves en tiempo real y accede a cualquier cabina.

- **🎯 Rastreo con un clic:** La cámara se fija en el objetivo, dibuja un rastro que se desvanece y muestra todos los metadatos; y un incendio o una embarcación rastreada te conecta con la cámara en vivo más cercana con un solo clic.

- **🖊️ Pizarra de voz:** Anota en el mundo mediante voz: polígonos de límites reales, marcas y rutas.
- **🛫 Hangar 3D:** Modelos reales de aeronaves de cada clase — 787, ATR-72, Citation, Bell 206, MQ-9 — y un contacto rastreado que cambia de glifo a modelo 3D al acercarse.
- **🎨 Realidad con texturas realistas:** El sensor GLSL analiza el entorno normal — CRT, NVG, FLIR/térmica, Noir, Snow.

- **🟩 Superposición de detección:** Cuadros delimitadores e identificadores en el espacio de la pantalla para todo lo que se ve.

- **🎖️ HUD militar:** Pantalla de visualización frontal táctica con telemetría de inteligencia.

- **🌐 Contexto global:** Recrea la situación completa con un solo interruptor y recupera tu vista exacta al salir.

- **🎥 Director de escena:** Captura recorridos de cámara cinematográficos para clips y demostraciones.
- **🔗 Compartir enlaces:** La cámara, el estilo, las capas e incluso un objetivo rastreado se serializan en una URL; un objetivo en tiempo real es una transferencia, no un marcador.

- **🏠 Reiniciar globo:** Un control (o una frase) para volver a la Tierra completa.

--

## ⚡ Inicio rápido

Requiere Node.js 24.14.x o 26.x (se aplica mediante `package.json`).

1. Copie `.env.example` → `.env` y configure `GOOGLE_MAPS_API_KEY`.

2. Instale y ejecute:

```bash
npm install
npm run dev -- --host localhost --port 4173
```

3. Abra **`http://localhost:4173`**. El arranque en frío se estabiliza en menos de dos segundos en un portátil reciente (media de 1,86 s en una captura puntual de M5/Chrome — [docs/PERFORMANCE.md](docs/PERFORMANCE.md); una referencia comparativa, no un requisito de hardware). Una tarjeta de primera ejecución te ofrece configurar una misión — **Contactos en vivo**, **Misiones espaciales**, **Medio ambiente** — o te permite explorar manualmente.

**Esa única clave es todo el coste de entrada.** Todo en este README está codificado por colores: 🟢 no requiere nada · 🟡 clave gratuita · 🔴 de pago — y Google Maps es la única 🔴 que necesitas: compra el planeta fotorrealista y la mayor parte del globo se ilumina 🟢 a partir de ahí. Mapa completo en [Claves y costes](#-api-keys).

El servidor de desarrollo se enlaza a **localhost**; tus claves permanecen en tu máquina. Compartir en una LAN y el costo rai
