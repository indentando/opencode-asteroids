# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales y tipos de asteroides únicos como la estrella fugaz.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción     |
| --------- | ---------- |
| `←` `→`   | Rotar nave |
| `↑`       | Propulsar  |
| `Espacio` | Disparar   |
| `C`       | Cambiar la skin de la nave |

## Puntuación

| Asteroide | Puntos |
| --------- | ------ |
| Grande    | 20     |
| Mediano   | 50     |
| Pequeño   | 100    |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Partículas de explosión al destruir asteroides
- Power-up **Velocidad**: aparece periódicamente en el campo; al recogerlo, la nave se mueve al doble de velocidad durante 5 segundos (el HUD muestra el tiempo restante)
- Power-up **Escudo**: aparece periódicamente en el campo; al recogerlo, una burbuja rodea la nave y destruye cualquier asteroide o estrella fugaz que la toque (dando puntos, como si fueran disparados) durante 8 segundos (el HUD muestra el tiempo restante)
- **Estrella fugaz**: aparece periódicamente; se mueve mucho más rápido que los asteroides normales, vale 150 puntos (no se parte) y desaparece por sí sola al cabo de unos segundos. Destruirla o esquivarla, pero cuidado: al chocar mata a la nave.
- **Skins de nave**: pulsa `C` para ciclar entre 4 apariencias distintas (forma y color, incluida la llama del propulsor). La selección se guarda en `localStorage` y los iconos de vidas reflejan la skin activa.
