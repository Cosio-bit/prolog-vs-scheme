# Prolog vs Scheme: marcador de alianzas

Página del marcador de alianzas de la Semana Informática (DIINF USACH, 2026).
Dueña: Andrea (Cosio-bit). Habla con ella en español, simple y paso a paso.

## Cómo funciona
- `index.html` es toda la página (HTML + JS, sin build). Vercel la publica en
  https://prolog-vs-scheme.vercel.app cada vez que se hace push a `main`.
- Los puntajes NO están en el código: la página lee cada 30 s la hoja
  "Puntajes – Prolog vs Scheme" (en el Drive de Andrea; buscarla por nombre) a través del
  link CSV de "Publicar en la web" (`URL_CSV` en index.html). La hoja en sí es PRIVADA.
- NUNCA escribir en el repo ni en la página el link/ID de edición de las hojas:
  el repo es público y Vercel sirve los archivos.
- Columnas de esa hoja (se ubican por el texto del encabezado):
  Actividad | Fecha | Puntos Prolog | Puntos Scheme | Detalle | Categoría
- Cambiar puntajes = editar filas en esa hoja. No hace falta redesplegar.

## Reglas de puntaje
Fuente: "PUNTAJES SEMANA INFORMÁTICA 2026" (en el Drive de Andrea; buscarla por nombre).
- DEPORTES: 1er y 2do lugar según la pestaña DEPORTES.
- VIDEOJUEGOS: 90 / 45 / 15 por 1°, 2° y 3° lugar. Cada lugar suma para la alianza
  del jugador que lo obtuvo (si Prolog saca 1°, 2° y 3°, Prolog recibe 150 y Scheme 0).
- ACTIVIDADES: 1er/2do lugar según la pestaña. Las actividades "por unidad" se mantienen:
  El que se la sabe (5 pts por canción), Quiz (5 pts por pregunta),
  Concurso de talentos (30 por participante), Cuecatón (30 por pareja).
- RETOS IMPOSIBLES: usar la tabla PONDERADA (columnas B/C de arriba, ej. STRAVA 61 / 48),
  NO la tabla original de más abajo.
- Categorías a usar: Deportes, Videojuegos, Actividades, Retos.

## Flujo de trabajo
Andrea manda los resultados (a veces fotos u hojas desordenadas desde el celular).
1. Leer/parsear los resultados y calcular los puntos con las reglas de arriba.
2. Mostrarle una tabla con lo calculado y pedir confirmación antes de escribir.
3. Escribir las filas en la hoja de puntajes (requiere el conector de Google Sheets;
   si no está, entregarle las filas listas para copiar y pegar).
