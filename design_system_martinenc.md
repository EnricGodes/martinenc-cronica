# Mini design system — FC Martinenc / crònica de partit

Documento breve para usar como referencia de maquetación y diseño en Claude Code.

## Objetivo

Crear una página web en catalán para una **crónica de partido** inspirada en la página de noticias del FC Martinenc.

El tono debe ser:

- Deportivo
- Institucional
- Claro
- De club histórico
- Editorial, no excesivamente moderno
- Con mucha importancia visual para el marcador y la ficha técnica

---

## Paleta de color

Colores aproximados a partir de la identidad visual del club.

```css
:root {
  --color-blue: #062e6f;
  --color-red: #e3062c;
  --color-yellow: #ffd400;

  --color-black: #1a1a1a;
  --color-grey: #666666;
  --color-light-grey: #f6f6f6;
  --color-border: #e5e5e5;
  --color-white: #ffffff;
}
```

### Uso recomendado

- `--color-blue`: color principal institucional. Titulares, fondos destacados, elementos de navegación.
- `--color-red`: acento deportivo. Categorías, líneas laterales, momentos clave, llamadas de atención.
- `--color-yellow`: acento puntual. Marcador, detalles gráficos, highlights.
- `--color-light-grey`: módulos secundarios, ficha técnica, bloques informativos.
- `--color-black`: texto principal.
- `--color-grey`: metadatos, fecha, autor, texto secundario.

---

## Tipografía

Usar una sans-serif limpia y editorial.

```css
:root {
  --font-main: "Inter", "Helvetica Neue", Arial, sans-serif;
}
```

Jerarquía sugerida:

```css
.article-title {
  font-size: clamp(38px, 6vw, 68px);
  line-height: 0.95;
  font-weight: 800;
}

.kicker {
  font-size: 13px;
  font-weight: 800;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.article-meta {
  font-size: 14px;
  color: var(--color-grey);
}

.article-body {
  font-size: 18px;
  line-height: 1.7;
}

.score {
  font-size: clamp(36px, 7vw, 64px);
  font-weight: 800;
}
```

---

## Layout general

Estructura recomendada de página:

```text
HEADER
HERO / TITULAR
MARCADOR DESTACADO
IMAGEN PRINCIPAL
CRÓNICA
MOMENTS CLAU
FITXA TÈCNICA
CIERRE IDENTITARIO
FOOTER
```

Contenedores:

```css
:root {
  --container-wide: 1180px;
  --container-text: 760px;

  --space-xs: 8px;
  --space-sm: 16px;
  --space-md: 24px;
  --space-lg: 40px;
  --space-xl: 72px;
}
```

---

## Header

El header debe ser blanco, institucional y con navegación clara.

Secciones de navegación sugeridas:

```text
Club · Futbol · Bàsquet · Hoquei · Futbol Sala · Altres Capacitats · Contacte
```

CSS orientativo:

```css
.header {
  background: var(--color-white);
  border-bottom: 1px solid var(--color-border);
  height: 88px;
}

.nav {
  text-transform: uppercase;
  font-size: 13px;
  letter-spacing: 0.04em;
  font-weight: 700;
}
```

---

## Hero de crónica

Debe contener categoría, título, marcador resumido y metadatos.

Ejemplo de contenido:

```text
FUTBOL SALA · CRÒNICA

El Martinenc signa una victòria de caràcter al Guinardó

FC MARTINENC 3 - 1 RIVAL

Diumenge, 10 de maig de 2026 · CEM Guinardó
```

CSS orientativo:

```css
.article-hero {
  max-width: var(--container-wide);
  margin: 0 auto;
  padding: var(--space-xl) var(--space-md) var(--space-lg);
}

.kicker {
  color: var(--color-red);
}

.article-title {
  color: var(--color-blue);
}
```

---

## Marcador destacado

El marcador debe tener protagonismo visual.

```css
.scoreboard {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  gap: 24px;
  background: var(--color-blue);
  color: var(--color-white);
  padding: 28px;
}

.score {
  color: var(--color-yellow);
}

.team {
  font-weight: 800;
  text-transform: uppercase;
}
```

Ejemplo:

```text
FC Martinenc     3 - 1     Rival
```

---

## Imagen principal

Usar una imagen horizontal grande después del marcador o después de la entradilla.

```css
.main-image {
  width: 100%;
  margin: 40px 0;
}

.main-image img {
  width: 100%;
  display: block;
  object-fit: cover;
}
```

---

## Cuerpo de crónica

El texto debe ser cómodo de leer y no demasiado ancho.

```css
.article-body {
  max-width: var(--container-text);
  margin: 0 auto;
  color: var(--color-black);
}

.article-body p {
  margin-bottom: 24px;
}

.article-body strong {
  color: var(--color-blue);
}
```

Estructura narrativa sugerida:

```text
Entradilla
Primer temps
Segon temps
Moment clau
Conclusió
```

---

## Moments clau

Bloque opcional para resumir el partido de forma visual.

Ejemplo:

```text
12’  1-0  Gol del Martinenc
34’  2-0  El Martinenc amplia l’avantatge
58’  2-1  Reacció visitant
78’  3-1  Sentència final
```

CSS sugerido:

```css
.key-moments {
  max-width: var(--container-text);
  margin: 56px auto;
  border-top: 4px solid var(--color-red);
}

.key-moment {
  display: grid;
  grid-template-columns: 72px 72px 1fr;
  gap: 16px;
  padding: 16px 0;
  border-bottom: 1px solid var(--color-border);
}

.minute,
.result {
  font-weight: 800;
  color: var(--color-blue);
}
```

---

## Fitxa tècnica

La ficha técnica debe cerrar la crónica con información compacta.

```css
.match-sheet {
  max-width: var(--container-text);
  margin: 56px auto;
  padding: 32px;
  background: var(--color-light-grey);
  border-left: 6px solid var(--color-red);
}

.match-sheet h2 {
  margin-top: 0;
  color: var(--color-blue);
  font-size: 22px;
  text-transform: uppercase;
}
```

Contenido de ejemplo:

```text
FITXA TÈCNICA

FC MARTINENC:
Jugador 1, Jugador 2, Jugador 3, Jugador 4...

RIVAL:
Jugador 1, Jugador 2, Jugador 3, Jugador 4...

GOLS:
1-0, Jugador (12’); 2-0, Jugador (34’); 2-1, Rival (58’); 3-1, Jugador (78’).

ÀRBITRE:
Nom de l’àrbitre.

PAVELLÓ:
CEM Guinardó.
```

---

## Cierre identitario

Usar una frase corta de club al final.

```text
#SomMartinenc
```

CSS sugerido:

```css
.club-closing {
  max-width: var(--container-wide);
  margin: 72px auto;
  padding: 48px 24px;
  background: var(--color-blue);
  color: var(--color-white);
  text-align: center;
  font-size: clamp(36px, 8vw, 80px);
  font-weight: 800;
}

.club-closing span {
  color: var(--color-yellow);
}
```

---

## Reglas de diseño

- Priorizar claridad y lectura.
- No usar demasiados efectos.
- Usar azul como color base y rojo como acento.
- Reservar el amarillo para detalles de alta visibilidad.
- Hacer el marcador muy visible.
- Mantener el cuerpo de texto estrecho.
- Usar módulos simples, sin sombras excesivas.
- Evitar estética demasiado corporativa o tecnológica.
- La página debe parecer de club deportivo, no de startup.

---

## Componentes mínimos que debe implementar Claude Code

1. Header responsive.
2. Hero de crónica.
3. Marcador destacado.
4. Imagen principal.
5. Cuerpo de crónica.
6. Bloque de momentos clave.
7. Fitxa tècnica.
8. Cierre `#SomMartinenc`.
9. Footer simple.

---

## Idioma

Toda la interfaz y el contenido visible de la página debe estar en catalán.

Etiquetas recomendadas:

```text
Crònica
Futbol Sala
Primer equip
Fitxa tècnica
Gols
Pavelló
Àrbitre
Moments clau
Últimes notícies
```
