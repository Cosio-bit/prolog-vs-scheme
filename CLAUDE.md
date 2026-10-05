# Prolog vs Scheme: marcador de alianzas

Página del marcador de alianzas de la Semana Informática (DIINF USACH, 2026).
Dueña: Andrea (Cosio-bit). Habla con ella en español, simple y paso a paso.

## Cómo funciona
- `index.html` es toda la página (HTML + JS, sin build). Vercel la publica en
  https://prolog-vs-scheme.vercel.app cada vez que se hace push a `main`.
- Los puntajes están en `puntajes.json`. La página lo lee al abrir y cada 30 s,
  así que tras un push las pantallas abiertas se actualizan solas (~1 min).
- La hoja de Google "Puntajes – Prolog vs Scheme" (Drive de Andrea, buscarla por nombre)
  es PRIVADA y es el registro maestro. Columnas:
  Actividad | Fecha | Puntos Prolog | Puntos Scheme | Detalle | Categoría
  La página NUNCA lee la hoja: Claude la lee con el conector de Google Sheets y
  copia los datos a `puntajes.json`.
- NUNCA escribir en el repo ni en la página el link/ID de las hojas:
  el repo es público y Vercel sirve los archivos.

## Reglas de puntaje
Fuente: "PUNTAJES SEMANA INFORMÁTICA 2026" (en el Drive de Andrea; buscarla por nombre).
- DEPORTES: 1er y 2do lugar según la pestaña DEPORTES. En pruebas individuales
  (lagartijas, plancha, dominadas) gana la alianza con la SUMA más alta de sus participantes
  (Forma A, aprobada por Andrea). Los asteriscos en las hojas de registro: significado desconocido.
  Si una alianza no se presenta (gana la otra por default), la que no se presentó recibe 0.
- VIDEOJUEGOS: 90 / 45 / 15 por 1°, 2° y 3° lugar. Cada lugar suma para la alianza
  del jugador que lo obtuvo (si Prolog saca 1°, 2° y 3°, Prolog recibe 150 y Scheme 0).
- ACTIVIDADES: 1er/2do lugar según la pestaña. Las actividades "por unidad" se mantienen:
  El que se la sabe (5 pts por canción), Quiz (5 pts por pregunta),
  Concurso de talentos (30 por participante), Cuecatón (30 por pareja).
- RETOS IMPOSIBLES: la fuente final es la hoja "PUNTAJES RETOS IMPOSIBLES" (Drive de Andrea).
  Pestaña PUNTAJES = puntos 1er/2do lugar (valores originales, ej. STRAVA 100 / 50).
  Pestaña GANADOS = un "1" por alianza en cada reto que hizo.
  Cada "1" suma el puntaje de PRIMER LUGAR. Confirmado: la fila TOTALES de la pestaña GANADOS
  coincide con esta forma de contar. Para revisar retos nuevos, comparar con esa fila TOTALES.
- Categorías a usar: Deportes, Videojuegos, Actividades, Retos.

## Flujo de trabajo
Andrea manda los resultados (a veces fotos u hojas desordenadas desde el celular).
1. Leer/parsear los resultados y calcular los puntos con las reglas de arriba.
2. Mostrarle una tabla con lo calculado y pedir confirmación antes de escribir.
3. Escribir las filas en la hoja de puntajes (conector de Google Sheets).
4. Volver a leer la hoja completa y regenerar `puntajes.json` con todas las filas
   (sin filas de ejemplo), hacer commit y push a `main`. Vercel publica solo.

Formato de `puntajes.json`:
{"actividades": [{"actividad": "...", "fecha": "...", "prolog": 0, "scheme": 0,
  "detalle": "...", "categoria": "Deportes"}],
 "juegos": [{"nombre": "Valorant", "estado": "Terminado|En curso|Por jugar",
   "podio": ["Scheme", {"equipo": "Los six seven", "alianza": "Scheme"}],
   "tabla": {"columnas": ["Equipo", "G", "P", "Pts"], "filas": [{"alianza": "Scheme", "celdas": ["Los six seven", "1", "0", "1"]}]},
   "partidas": [{"a": "Schemen", "aliA": "Scheme", "b": "ART4RUSGAN", "aliB": "Prolog", "resultado": "13 – 3"}],
   "rondas": [{"titulo": "Primera ronda", "partidas": [...]}],      (rondas reemplaza a partidas si existe)
   "tablas": [{"titulo": "Pista 1", "columnas": [...], "filas": [...]}],  (tablas reemplaza a tabla si existe)
   "nota": "texto corto opcional"}]}
- Mario Kart: se muestran los PERSONAJES (Waluigi, Huesito…), nunca los nombres reales.
- Smash Bros: jugadores anonimizados como P1–P7 / S1–S7 (número = cruce de la ronda 1).
- Valorant: 1ª ronda = 3 cruces (Schemen–21068 pilotos, BETANORANT–ART4RUSGAN,
  Los six seven–Chanchitas Lindas); los ganadores juegan una tabla final todos contra todos.

## Privacidad (regla de Andrea)
- En la página NO puede aparecer ningún nombre de PERSONA. Los nombres de EQUIPOS sí van.
  En juegos individuales (ej. Just Dance) el podio muestra solo la alianza.
  Aplica a puntajes.json, al "detalle" de las actividades y a la hoja de puntajes.

## Brackets de videojuegos
- Hoja "Brackets" (Drive de Andrea, buscarla por nombre): una pestaña por juego
  (Just Dance, Valorant, FC26, LoL, Rocket League).
- La alianza de cada equipo/persona se ve por COLOR de celda: rosado = Scheme, amarillo = Prolog
  (leer con get_spreadsheet + effectiveFormat.backgroundColor). En Just Dance está en texto.
- La sección "juegos" de puntajes.json se copia desde esa hoja. Un juego solo suma puntos
  a las alianzas (fila en "actividades") cuando Andrea confirma que terminó.
