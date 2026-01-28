# Interfaces - Resumen del Curso

Este repositorio contiene todos los materiales, ejemplos y ejercicios del curso de Interfaces Web, enfocado en diseño responsivo y frameworks CSS modernos.

---

## 📑 Índice

1. [Diseño Web Responsivo (RWD)](#diseño-web-responsivo-rwd)
2. [CSS Flexbox](#css-flexbox)
3. [CSS Grid](#css-grid)
4. [Patrones de Diseño Responsivo](#patrones-de-diseño-responsivo)
5. [Tailwind CSS](#tailwind-css)
6. [Estructura del Proyecto](#estructura-del-proyecto)

---

## 🌐 Diseño Web Responsivo (RWD)

### Conceptos Fundamentales

El **Responsive Web Design** es una técnica de diseño web que permite que las páginas se adapten a diferentes tamaños de pantalla y dispositivos.

### Elementos Clave

#### 1. Meta Viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```
Esta etiqueta es **esencial** para que el diseño responsivo funcione correctamente en dispositivos móviles.

#### 2. Media Queries
Las media queries permiten aplicar estilos CSS específicos según las características del dispositivo:

```css
/* Estilos para pantallas menores a 768px */
@media screen and (max-width: 768px) {
  body {
    background-color: #fff;
  }
  div#contenedor {
    width: 100%;
    margin: 0;
  }
  section#contenido {
    float: none;
    width: auto;
  }
}
```

#### 3. Técnicas Responsivas
- **Unidades relativas**: Usar `%`, `em`, `rem`, `vw`, `vh` en lugar de píxeles fijos
- **Imágenes fluidas**: `max-width: 100%` para que las imágenes se adapten
- **Layouts flexibles**: Evitar anchos fijos, usar `float`, `flexbox` o `grid`

### Ejemplo Práctico
El archivo `Ejemplos/Cap 09/09_01.html` muestra una página completa con:
- Header con título y eslogan
- Barra de navegación
- Contenido principal con artículos
- Sidebar lateral
- Footer

Que se adapta a móviles mediante media queries en `rwd.css`.

---

## 🔲 CSS Flexbox

### ¿Qué es Flexbox?

Flexbox es un modelo de layout unidimensional que permite distribuir elementos en una fila o columna de manera eficiente.

### Propiedades del Contenedor (Flex Container)

```css
.container {
  display: flex;
  flex-direction: row | column;
  justify-content: flex-start | center | space-between | space-around;
  align-items: stretch | center | flex-start | flex-end;
  flex-wrap: nowrap | wrap;
  gap: 20px;
}
```

### Propiedades de los Items (Flex Items)

```css
.item {
  flex-grow: 1;    /* Capacidad de crecer */
  flex-shrink: 1;  /* Capacidad de encogerse */
  flex-basis: auto; /* Tamaño base */
  flex: 1;         /* Shorthand para grow, shrink, basis */
  align-self: auto | center | flex-start | flex-end;
}
```

### Casos de Uso Comunes

1. **Centrado perfecto**:
```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

2. **Navegación horizontal**:
```css
nav ul {
  display: flex;
  gap: 20px;
  list-style: none;
}
```

3. **Layout de página completa**:
```css
.wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.page-main {
  flex: 1; /* Ocupa todo el espacio disponible */
}
```

### Ejemplo del Curso
El archivo `Ejercicios/Tutorial Flex/html1.html` implementa una página completa usando Flexbox con:
- Header con navegación
- Main content que ocupa el espacio disponible
- Footer fijo en la parte inferior

---

## 📊 CSS Grid

### ¿Qué es CSS Grid?

CSS Grid es un sistema de layout bidimensional que permite crear diseños complejos con filas y columnas.

### Propiedades Básicas del Grid

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 columnas iguales */
  grid-template-rows: auto;
  gap: 20px;
  grid-template-areas:
    "header header header"
    "sidebar content content"
    "footer footer footer";
}
```

### Propiedades de Grid Items

```css
.grid-item {
  grid-column: 1 / 3;  /* Ocupa de la columna 1 a la 3 */
  grid-row: 1 / 2;
  grid-area: header;   /* Usa un área nombrada */
}
```

### Funciones Útiles

- `repeat(3, 1fr)`: Repite 3 columnas de 1 fracción
- `minmax(200px, 1fr)`: Mínimo 200px, máximo 1 fracción
- `auto-fit` / `auto-fill`: Grid responsivo automático

```css
.responsive-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

### Ejemplo del Curso
El archivo `Ejercicios/Flex-Grid/index.html` implementa la landing page "Skilllz" combinando Flexbox y Grid:
- Grid para el layout general
- Flexbox para componentes específicos (navbar, stats)
- Grid de 3 columnas para testimonios

---

## 🎨 Patrones de Diseño Responsivo

El curso cubre **5 patrones principales** de diseño responsivo:

### 1. **Mostly Fluid** 📱➡️💻
El patrón más común. El contenido se organiza en columnas en pantallas grandes y se apila verticalmente en móviles.

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}
```

**Características**:
- Columnas fluidas que se reorganizan
- Márgenes laterales en pantallas muy grandes
- Apilamiento vertical en móviles

### 2. **Column Drop** 📉
Las columnas se van "cayendo" debajo una de otra a medida que el viewport se reduce.

**Características**:
- Orden específico de caída de columnas
- Puntos de ruptura definidos
- Ideal para contenido de prioridad variable

### 3. **Layout Shifter** 🔄
El layout cambia drásticamente entre diferentes tamaños de pantalla.

**Características**:
- Cambios significativos en la estructura
- Reordenamiento de elementos
- Mayor control sobre el diseño en cada breakpoint

### 4. **Tiny Tweaks** 🔧
Pequeños ajustes en lugar de cambios drásticos.

**Características**:
- Cambios mínimos (tamaño de fuente, padding)
- Ideal para contenido simple
- Una sola columna en todos los tamaños

### 5. **Off Canvas** 🎭
El contenido secundario (menú, sidebar) se oculta fuera de la pantalla y aparece con interacción.

**Características**:
- Menú hamburguesa típico
- Sidebar deslizable
- Maximiza espacio en móviles

### Ubicación en el Proyecto
Todos los patrones están implementados en `Ejercicios/Patrones/`:
- `MostlyFluid/`
- `ColumnDrop/`
- `LayoutShifter/`
- `TinyTweaks/`
- `OffCanvas/`

Cada carpeta contiene `html.html` y `css.css` con la implementación completa.

---

## ⚡ Tailwind CSS

### ¿Qué es Tailwind CSS?

Tailwind es un **framework CSS utility-first** que permite construir interfaces rápidamente usando clases predefinidas.

### Filosofía Utility-First

En lugar de escribir CSS personalizado:
```css
.btn-primary {
  background-color: blue;
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
}
```

Usas clases de utilidad directamente en el HTML:
```html
<button class="bg-blue-500 text-white px-6 py-3 rounded-lg">
  Click me
</button>
```

### Métodos de Instalación

#### 1️⃣ Instalación mediante CDN (Desarrollo/Pruebas)

**Ventajas**: Rápido, sin configuración
**Desventajas**: Archivo muy pesado, no optimizado

```html
<head>
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
</head>
```

#### 2️⃣ Instalación mediante CLI (Producción) ⭐ RECOMENDADO

**Paso 1**: Inicializar proyecto
```bash
npm init -y
```

**Paso 2**: Instalar Tailwind
```bash
npm install tailwindcss @tailwindcss/cli
```

**Paso 3**: Estructura de archivos
```
proyecto/
├── src/
│   ├── css/
│   │   ├── tailwind.css    (configuración)
│   │   └── estilos.css     (generado)
│   └── index.html
├── package.json
└── node_modules/
```

**Paso 4**: Configurar `src/css/tailwind.css`
```css
@import "tailwindcss";
```

**Paso 5**: Compilar CSS
```bash
npx @tailwindcss/cli -i ./src/css/tailwind.css -o ./src/css/estilos.css --watch
```

**Paso 6**: Vincular en HTML
```html
<link rel="stylesheet" href="css/estilos.css">
```

### Automatización con Scripts

Añadir en `package.json`:
```json
{
  "scripts": {
    "tailwind": "npx tailwindcss -i ./src/css/tailwind.css -o ./src/css/estilos.css --watch"
  }
}
```

Ejecutar:
```bash
npm run tailwind
```

### Clases de Utilidad Comunes

#### Espaciado
```html
<div class="p-4">Padding 1rem</div>
<div class="m-8">Margin 2rem</div>
<div class="px-6 py-3">Padding horizontal y vertical</div>
```

#### Colores
```html
<div class="bg-red-500 text-white">Fondo rojo, texto blanco</div>
<div class="bg-blue-900 text-gray-100">Fondo azul oscuro</div>
```

#### Tipografía
```html
<h1 class="text-3xl font-bold">Título grande</h1>
<p class="text-center text-sm">Texto pequeño centrado</p>
```

#### Layout
```html
<div class="flex justify-center items-center">Flexbox centrado</div>
<div class="grid grid-cols-3 gap-4">Grid de 3 columnas</div>
```

### Preflight

Tailwind incluye **Preflight**, un conjunto de estilos base que normaliza el CSS entre navegadores. Por eso los elementos HTML se ven "sin estilo" antes de añadir clases.

### Recursos

📖 **Documentación oficial**: [https://tailwindcss.com/docs](https://tailwindcss.com/docs)

> [!IMPORTANT]
> La documentación de Tailwind es tu mejor amiga. Está constantemente actualizada y contiene todos los detalles.

---

## 📁 Estructura del Proyecto

```
Interfaces/
├── Ejemplos/
│   └── Cap 09/                    # Ejemplos de RWD con media queries
│       ├── 09_01.html
│       ├── 09_02.html
│       ├── rwd.css
│       ├── tigre.jpg
│       └── cebra.jpg
│
├── Ejercicios/
│   ├── Flex-Grid/                 # Landing page "Skilllz" con Flex + Grid
│   │   ├── index.html
│   │   └── styles.css
│   │
│   ├── Tutorial Flex/             # Página completa con Flexbox
│   │   ├── html1.html
│   │   └── css1.css
│   │
│   └── Patrones/                  # 5 patrones de diseño responsivo
│       ├── MostlyFluid/
│       ├── ColumnDrop/
│       ├── LayoutShifter/
│       ├── TinyTweaks/
│       └── OffCanvas/
│
├── TailwindCSS/
│   ├── 01-Instalacion-y-Configuracion.md  # Guía completa de Tailwind
│   └── Ejemplos/
│       ├── package.json
│       └── package-lock.json
│
└── README.md                      # Este archivo
```

---

## 🎯 Conceptos Clave del Curso

### 1. Mobile First
Diseñar primero para móviles y luego escalar a pantallas más grandes:

```css
/* Estilos base para móvil */
.container {
  width: 100%;
}

/* Estilos para tablet y desktop */
@media (min-width: 768px) {
  .container {
    width: 750px;
  }
}
```

### 2. Breakpoints Comunes

```css
/* Móvil: < 768px */
@media (max-width: 767px) { }

/* Tablet: 768px - 1024px */
@media (min-width: 768px) and (max-width: 1024px) { }

/* Desktop: > 1024px */
@media (min-width: 1025px) { }
```

### 3. Flexbox vs Grid

**Usa Flexbox cuando**:
- Necesitas alinear elementos en una dirección (fila o columna)
- Componentes pequeños (navbar, cards)
- Distribución de espacio flexible

**Usa Grid cuando**:
- Necesitas control bidimensional (filas Y columnas)
- Layouts de página completa
- Diseños complejos con áreas nombradas

### 4. Utility-First vs Component-First

**Component-First (CSS tradicional)**:
```css
.card {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

**Utility-First (Tailwind)**:
```html
<div class="bg-white p-5 rounded-lg shadow-md">
  <!-- contenido -->
</div>
```

---

## 🚀 Mejores Prácticas

### HTML Semántico
```html
<header>   <!-- Cabecera -->
<nav>      <!-- Navegación -->
<main>     <!-- Contenido principal -->
<section>  <!-- Secciones -->
<article>  <!-- Artículos independientes -->
<aside>    <!-- Contenido relacionado -->
<footer>   <!-- Pie de página -->
```

### CSS Organizado
```css
/* 1. Reset/Base */
* { margin: 0; padding: 0; }

/* 2. Variables */
:root {
  --primary-color: #3490dc;
}

/* 3. Layout */
.container { max-width: 1200px; }

/* 4. Componentes */
.card { ... }

/* 5. Media Queries */
@media (max-width: 768px) { ... }
```

### Rendimiento
- ✅ Minimizar CSS en producción
- ✅ Usar Tailwind CLI para purgar clases no usadas
- ✅ Optimizar imágenes (WebP, lazy loading)
- ✅ Evitar CDN de Tailwind en producción

---

## 📚 Recursos Adicionales

### Documentación Oficial
- [MDN Web Docs - CSS](https://developer.mozilla.org/es/docs/Web/CSS)
- [CSS-Tricks - Flexbox Guide](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS-Tricks - Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)

### Herramientas Útiles
- [Flexbox Froggy](https://flexboxfroggy.com/) - Juego para aprender Flexbox
- [Grid Garden](https://cssgridgarden.com/) - Juego para aprender Grid
- [Can I Use](https://caniuse.com/) - Compatibilidad de navegadores
- [Tailwind Play](https://play.tailwindcss.com/) - Playground online

### Extensiones VS Code Recomendadas
- **Tailwind CSS IntelliSense**: Autocompletado para Tailwind
- **Live Server**: Servidor local con recarga automática
- **Prettier**: Formateo de código

---

## ✅ Checklist de Aprendizaje

### Diseño Responsivo
- [ ] Entiendo qué es el viewport y cómo configurarlo
- [ ] Puedo escribir media queries efectivas
- [ ] Sé usar unidades relativas (%, rem, em)
- [ ] Conozco los 5 patrones de diseño responsivo

### Flexbox
- [ ] Entiendo la diferencia entre flex container e items
- [ ] Puedo centrar elementos vertical y horizontalmente
- [ ] Sé usar justify-content y align-items
- [ ] Puedo crear layouts de página completa con flex

### Grid
- [ ] Entiendo el sistema de filas y columnas
- [ ] Puedo usar grid-template-columns y rows
- [ ] Sé crear grids responsivos con auto-fit/auto-fill
- [ ] Puedo combinar Grid y Flexbox efectivamente

### Tailwind CSS
- [ ] Sé instalar Tailwind con CLI
- [ ] Entiendo la filosofía utility-first
- [ ] Puedo construir componentes con clases de utilidad
- [ ] Sé configurar el proceso de compilación

---

## 🎓 Proyectos Realizados

1. **Página Responsiva Básica** (`Ejemplos/Cap 09`)
   - Layout tradicional con float
   - Media queries para móvil
   - Imágenes responsivas

2. **Landing Page Skilllz** (`Ejercicios/Flex-Grid`)
   - Navbar con Flexbox
   - Grid para testimonios
   - Diseño completamente responsivo
   - Uso de Font Awesome

3. **Página Flexbox Full-Screen** (`Ejercicios/Tutorial Flex`)
   - Layout de altura completa (100vh)
   - Header, main y footer con Flexbox
   - Footer siempre en la parte inferior

4. **Patrones Responsivos** (`Ejercicios/Patrones`)
   - Implementación de los 5 patrones principales
   - Ejemplos prácticos de cada uno

5. **Proyecto Tailwind** (`TailwindCSS/Ejemplos`)
   - Configuración completa de Tailwind
   - Compilación con CLI
   - Scripts automatizados

---

## 💡 Consejos Finales

> [!TIP]
> **Practica constantemente**: El diseño responsivo se aprende haciendo. Intenta recrear sitios web que te gusten.

> [!NOTE]
> **Inspecciona sitios web**: Usa las DevTools del navegador (F12) para ver cómo están construidos los sitios profesionales.

> [!IMPORTANT]
> **Mobile First siempre**: Empieza diseñando para móvil y luego escala. Es más fácil que hacerlo al revés.

> [!WARNING]
> **No abuses de Tailwind**: Aunque es poderoso, aprende CSS vanilla primero para entender los fundamentos.

---

## 📞 Contacto y Contribuciones

Este README resume todo el contenido visto en clase. Si encuentras algún error o quieres añadir más información, no dudes en actualizar este documento.

**Última actualización**: Enero 2026

---

## 🏆 Objetivos de Aprendizaje Alcanzados

Al completar este curso, deberías ser capaz de:

✅ Crear sitios web completamente responsivos  
✅ Usar Flexbox y Grid con confianza  
✅ Implementar patrones de diseño responsivo profesionales  
✅ Trabajar con Tailwind CSS en proyectos reales  
✅ Optimizar el rendimiento de tus estilos CSS  
✅ Entender y aplicar las mejores prácticas de desarrollo web moderno  

---

**¡Feliz codificación! 🚀**
