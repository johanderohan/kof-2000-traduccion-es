# The King of Fighters 2000 — Traducción al español

[![Invítame a un café en Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/johanderohan)

Ficha del proyecto, capturas y más traducciones al castellano en **[Parches en Castellano](https://parchesencastellano.com/traducciones/dreamcast/the-king-of-fighters-2000)**.

Traducción al **español de España** de *The King of Fighters 2000* para Dreamcast (versión
japonesa de Playmore, 2002), traducida directamente del japonés.

Los menús del juego ya venían en inglés, pero todo lo que cuenta la historia estaba en japonés:
las frases de victoria de cada luchador, las escenas con el jefe, los finales de cada equipo y los
mensajes de la tarjeta de memoria. Este parche lo traduce todo.

La traducción se reparte como **parche**: no incluye el juego. Necesitas tu propia copia para
aplicarlo.

## Estado

Última versión: **[v1.0 — Primera versión](../../releases/tag/v1.0)**. Estado: **en revisión**.

| Parte | Estado |
|---|---|
| Frases de victoria (198), frases tras perder (35) y del jefe (32) | Traducidas |
| Escenas de historia con el jefe final (128 mensajes) y con la semijefa | Traducidas |
| Finales de los 11 equipos (161 mensajes) | Traducidos |
| Pantallas de la tarjeta de memoria (30), aviso de mando desconectado, ayuda y explicación del puzle | Traducidas (son imágenes; redibujadas) |
| Menús, rótulos de combate y créditos | Ya estaban en inglés en el original; se dejan |
| Caracteres españoles | **á é í ó ú ü ñ Á É Í Ó Ú Ü Ñ ¡ ¿ « »** |
| Partida completa de principio a fin | Hecha en emulador con un equipo (y otra hasta el final con un segundo equipo) |

La fuente japonesa del juego es de 16×16 píxeles por carácter. Para que quepa el castellano, cada
casilla lleva **dos letras** de una fuente de 8×16 con el mismo trazo fino y el mismo color que la
original. Traducción y revisión asistidas por IA, sin revisión humana independiente.

### Cómo se ha comprobado

Todo en emulador (Flycast), no en una Dreamcast real:

- **Modo TEAM PLAY completo desde partida nueva** con el equipo de K': todos los combates, frases de
  victoria, escenas con la semijefa y con el jefe, final y créditos.
- **Otra partida hasta el final** con un segundo equipo (Benimaru, Shingo, Lin y Seth).
- **Derrota y pantalla CONTINUE**, cuenta atrás y GAME OVER.
- **Tarjeta de memoria**: guardado y carga reales en la VMU emulada, guardado automático y sus
  pantallas de mensajes; aviso de mando desconectado en pleno combate.
- La explicación del puzle de la galería.
- Una auditoría automática comprueba en cada imagen los límites de memoria conocidos (el archivo de
  frases de victoria tiene un búfer fijo), el número de caracteres por línea y la integridad de los
  gráficos. El parche se ha aplicado sobre el original y el resultado se ha comparado byte a byte.

### Limitaciones conocidas

- Solo se han visto en el juego dos de los once finales; los demás se han revisado como texto.
- No todas las frases de victoria ni de derrota se han visto en pantalla (dependen de quién gane a
  quién); todas pasan los límites de anchura medidos.
- No se ha probado en hardware real.
- Las frases de victoria se han escrito concisas: todas tienen que caber en un búfer de memoria fijo
  del juego.
- Se mantienen en inglés los menús, rótulos y créditos que ya lo estaban, y los logotipos.
- En el original, una docena de frases de victoria mostraban recuadros en lugar de algunos kanji;
  en castellano se leen completas.

## Cómo aplicar el parche

El parche modifica **las pistas 3 y 5** de la imagen Redump del juego.

1. Descarga los dos parches `.xdelta` de la sección **[Releases](../../releases)**.
2. Consigue tu copia del juego en formato **Redump BIN/CUE** de la versión **japonesa**
   (`King of Fighters 2000, The (Japan).cue` con cinco pistas).
3. **Comprueba que tus pistas 3 y 5 son las correctas**:

   | Archivo | Tamaño | MD5 |
   |---|---|---|
   | `King of Fighters 2000, The (Japan) (Track 3).bin` | 420.492.912 bytes | `f971082185854ce7b010681325ee8588` |
   | `King of Fighters 2000, The (Japan) (Track 5).bin` | 763.532.112 bytes | `efc6a06a170f3ba6a0623a7c5e48b98c` |

   ```bash
   md5sum "King of Fighters 2000, The (Japan) (Track 3).bin"                    # Linux
   md5 "King of Fighters 2000, The (Japan) (Track 3).bin"                       # macOS
   CertUtil -hashfile "King of Fighters 2000, The (Japan) (Track 3).bin" MD5    # Windows
   ```

   Si no coinciden, el parche fallará o dará un resultado corrupto.
4. Aplica cada parche a su pista:
   - **Windows**: [Delta Patcher](https://github.com/marco-calautti/DeltaPatcher/releases)
   - **Linux / macOS**:
     ```bash
     xdelta3 -d -s "King of Fighters 2000, The (Japan) (Track 3).bin" KOF2000.ES.v1.0.pista3.xdelta "pista3.bin"
     xdelta3 -d -s "King of Fighters 2000, The (Japan) (Track 5).bin" KOF2000.ES.v1.0.pista5.xdelta "pista5.bin"
     ```
5. Sustituye cada pista por la traducida **con el mismo nombre de archivo**. Las pistas 1, 2 y 4 y el
   `.cue` no cambian.
6. Para **v1.0**, las pistas resultantes tienen el mismo tamaño que las originales y estos MD5:
   pista 3 **`bb43fbf84b83e6f485b772eed4bd89d8`**, pista 5 **`0af0bb336a64bb08c69ceb8e3eafbe0b`**.
7. Carga el `.cue` en tu emulador (probado en Flycast).

Aplica cada versión sobre las **pistas originales**, no sobre unas ya traducidas.

## Cambios

### v1.0 — 16 de octubre de 2026
- Primera versión: The King of Fighters 2000 en castellano, con su historia completa traducida del japonés.
- Traducidas frases de victoria y de derrota, escenas con el jefe y los finales de los once equipos.
- Redibujadas en castellano las pantallas de la tarjeta de memoria, avisos y la explicación del puzle.

## Créditos

- Fuente de los textos: [Terminus Font](https://terminus-font.sourceforge.net/) (SIL Open Font
  License 1.1), adaptada a casillas de dos letras. Textos en imagen con Noto Sans (SIL OFL 1.1).

## Aviso

Este proyecto es una traducción hecha por afición, sin ánimo de lucro y sin relación alguna con
SNK, Playmore ni SEGA. Aquí no se distribuye el juego ni ninguna parte de él: solo un parche que
modifica una copia que ya tengas.

Si eres el titular de los derechos y quieres que retire esto, abre una incidencia y lo hago.
