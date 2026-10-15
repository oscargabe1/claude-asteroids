# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Demo:

[Asteroids demo](https://klerith.github.io/claude-asteroids/)

## Descripción del juego

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales y tipos de asteroides únicos como la estrella fugaz...

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
| `↓`       | Reversa    |
| `Espacio` | Disparar   |
| `B`       | Bomba nova |

## Power-ups

Se sueltan al destruir asteroides (10% de probabilidad). Tócalos con la nave para recogerlos.

| Ítem | Efecto | Duración |
| ---- | ------ | -------- |
| `3` Disparo triple | 3 balas en abanico | 10 s |
| `S` Escudo | Absorbe un impacto de asteroide | 5 s o 1 golpe |
| `~` Slow motion | Asteroides a la mitad de velocidad | 6 s |
| `N` Bomba nova | Destruye todos los asteroides en pantalla (se guarda, máx. 3, se usa con `B`) | 1 uso |

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
