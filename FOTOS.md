# Guía de Imágenes — APAI Web

Todas las imágenes están en la carpeta `images/`.
Este archivo explica qué foto corresponde a cada sección y cómo agregar o quitar imágenes.

---

## Estructura de secciones

### 1. LOGOS (aparecen fijos en la página)

| Archivo | Sección | Descripción |
|---------|---------|-------------|
| `favicon.png` | Pestaña del navegador | Icono pequeño que aparece en la pestaña |
| `logo-nav.png` | Barra de navegación | Logo APAI en la barra superior |
| `logo-hero.png` | Portada (hero) | Logo grande redondo en la sección principal |
| `logo-footer.png` | Pie de página | Logo APAI en el footer |

> **Para cambiar un logo:** reemplazá el archivo manteniendo el mismo nombre y formato (PNG).

---

### 2. FONDOS — Tarjetas de categorías

Estas fotos son las miniaturas que aparecen en cada tarjeta de la sección "Fondos de la APAI".
Al hacer clic en una tarjeta se abre un lightbox con más fotos de esa categoría.

| Archivo | Categoría | Descripción |
|---------|-----------|-------------|
| `fondos-limpieza.jpg` | Limpieza e higiene | Foto de portada de la tarjeta |
| `fondos-fumigacion.jpg` | Fumigación y sanidad | Foto de portada de la tarjeta |
| `fondos-luminarias.jpg` | Iluminación y seguridad | Foto de portada de la tarjeta |
| `fondos-herramientas.jpg` | Herramientas e insumos | Foto de portada de la tarjeta |
| `fondos-informatica.jpg` | Equipamiento informático | Foto de portada de la tarjeta |
| `fondos-impresion3d.jpg` | Impresión 3D | Foto de portada de la tarjeta |
| `fondos-pintura.jpg` | Pintura de aeronaves | Foto de portada de la tarjeta |

> **Para cambiar la foto de una tarjeta:** reemplazá el archivo JPG manteniendo el mismo nombre.
> Tamaño recomendado: 400×300px mínimo, formato JPG.

---

### 3. LIGHTBOX — Fotos detalladas por categoría

Estas fotos se muestran al hacer clic en una tarjeta de fondos. Se configuran en el JavaScript del `index.html` dentro del objeto `catPhotos`.

#### 🧹 Limpieza e higiene
| Archivo | Descripción |
|---------|-------------|
| `cat-limpieza-insumos.jpg` | Insumos de limpieza adquiridos por la APAI |

#### 💡 Iluminación y seguridad
| Archivo | Descripción |
|---------|-------------|
| `cat-luminarias-acceso.jpg` | Iluminación nocturna del acceso al INAC |
| `cat-luminarias-led-corredor.jpg` | Luminarias LED instaladas en el corredor de tránsito |

#### 🔧 Herramientas e insumos
| Archivo | Descripción |
|---------|-------------|
| `cat-herramientas-ferreteria.jpg` | Insumos de ferretería y taller: discos, lubricantes, bulones, LEDs |

#### ✈️ Pintura de aeronaves
| Archivo | Descripción |
|---------|-------------|
| `cat-pintura-alumno-carlinga.jpg` | Alumno pintando la carlinga de una aeronave |
| `cat-pintura-ala-preparacion.jpg` | Ala de aeronave enmascarada y lista para pintura |
| `cat-pintura-fuselaje.jpg` | Fuselaje enmascarado y pintado frente al hangar |

#### 💻 Equipamiento informático
| Archivo | Descripción |
|---------|-------------|
| `cat-informatica-ssd.jpg` | Discos SSD Kingston para el laboratorio |
| `cat-informatica-laboratorio.jpg` | Laboratorio de computación con equipos actualizados |

#### 🖨️ Impresión 3D
| Archivo | Descripción |
|---------|-------------|
| `cat-impresion3d-filamentos.jpg` | Filamentos PLA Grilon3 para impresoras 3D |
| `cat-impresion3d-elegoo.jpg` | Impresora 3D Elegoo instalada en el aula taller |

#### 🏫 Fumigación y sanidad
| Archivo | Descripción |
|---------|-------------|
| `cat-fumigacion-interior.jpg` | Fumigación interior del hall principal del INAC |
| `cat-fumigacion-exterior.jpg` | Fumigación exterior de jardines y espacios verdes |

---

### 4. GALERÍA INAC — Fotos propias locales

Estas dos fotos son locales (el resto de la galería INAC viene de `inac.edu.ar`).

| Archivo | Descripción |
|---------|-------------|
| `galeria-lab-electronica.jpg` | Alumnos con osciloscopio en el laboratorio de electrónica |
| `galeria-lab-electronica-2.jpg` | Edificio principal del CIATA con planeador |

---

## Cómo agregar una foto nueva

### A una tarjeta de fondos (miniatura)
1. Guardá tu imagen JPG en la carpeta `images/` con nombre `fondos-CATEGORIA.jpg`
2. En `index.html`, buscá la tarjeta correspondiente y cambiá el `src` de la `<img>`

### Al lightbox de una categoría (foto detallada)
1. Guardá tu imagen JPG en `images/` con nombre tipo `cat-CATEGORIA-descripcion.jpg`
2. En `index.html`, buscá el bloque `const catPhotos = {` en el JavaScript
3. Dentro de la categoría correspondiente, agregá una línea:
```javascript
{src:"images/cat-CATEGORIA-nuevo-nombre.jpg", desc:"Descripción de la foto", title:"Título corto"},
```

**Ejemplo:** para agregar una foto de limpieza:
```javascript
// Buscá esta sección en el JS:
limpieza:[
  {src:"images/cat-limpieza-insumos.jpg", desc:"Insumos de limpieza adquiridos", title:"🧹 Insumos"},
  // AGREGÁ ACÁ la nueva línea:
  {src:"images/cat-limpieza-nueva-foto.jpg", desc:"Descripción de la nueva foto", title:"🧹 Título"},
],
```

### A la galería INAC (foto local)
1. Guardá tu imagen JPG en `images/` con nombre tipo `galeria-descripcion.jpg`
2. En `index.html`, buscá `<div class="ig-grid reveal">` y agregá:
```html
<div class="ig-cell" onclick="openInacLightbox(NUMERO)" title="Título de la foto">
  <img src="images/galeria-descripcion.jpg" alt="Descripción" loading="lazy">
  <div class="ig-cap">Texto que aparece debajo</div>
</div>
```
3. También agregá la foto al array `inacPhotos` en el JavaScript:
```javascript
{src:"images/galeria-descripcion.jpg", desc:"Descripción"},
```

---

## Cómo quitar una foto

1. Borrá el archivo de la carpeta `images/`
2. En `index.html`, borrá la línea que referencia esa imagen:
   - Si es del lightbox: borrá la línea `{src:"images/...", desc:"...", title:"..."},`
   - Si es de la galería: borrá el bloque `<div class="ig-cell">...</div>` correspondiente
3. Hacé commit y push

---

## Tamaños recomendados

| Tipo | Tamaño mínimo | Formato | Peso máximo |
|------|--------------|---------|-------------|
| Logo | 100×100px | PNG (fondo transparente) | 50 KB |
| Tarjeta fondos | 400×300px | JPG | 100 KB |
| Lightbox categoría | 800×600px | JPG | 200 KB |
| Galería INAC | 800×600px | JPG | 150 KB |
| Favicon | 32×32px | PNG | 15 KB |

> **Tip:** Para comprimir imágenes antes de subir, usá [tinypng.com](https://tinypng.com/) o [squoosh.app](https://squoosh.app/).
