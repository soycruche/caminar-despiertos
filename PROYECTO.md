# Caminar Despiertos — Contexto del Proyecto

> Este archivo es el punto de entrada para cualquier sesión de desarrollo.
> Leerlo completo antes de tocar cualquier archivo.

---

## Qué es esto

**Caminar Despiertos** es una experiencia de turismo receptivo premium en Buenos Aires.
Es una caminata fotográfica de 2 horas por los barrios reales de la ciudad, creada y guiada por **Barbara Prajs** (fotógrafa, diseñadora gráfica, artista).

No es un tour fotográfico genérico. El diferencial es que usa la fotografía como herramienta de percepción — la cámara es el pretexto, la mirada es el destino. Sin experiencia fotográfica previa necesaria.

**Mercados objetivo:** México, Colombia, España, Chile, Uruguay  
**Idioma de la experiencia:** Español  
**Formato:** Individual (USD 75) o pareja (USD 130)

---

## Personas clave

### Barbara Prajs
- Fotógrafa y diseñadora gráfica, Buenos Aires, nacida en 1976
- Instagram: [@_pasares](https://www.instagram.com/_pasares/)
- Sitio de su obra: [pasares.com.ar](https://www.pasares.com.ar)
- Historia de origen: en octubre 2020 le diagnosticaron cáncer de mama. Durante 585 días de tratamiento caminó Chacarita fotografiando diariamente — más de 10.000 fotos. De esa experiencia nació su instalación fotográfica `_pasares`, exhibida en museos de Argentina e India. Caminar Despiertos es la evolución natural: enseñarle a otros a ver como ella aprendió a ver.
- Habla español. Inglés limitado (relevante para escalar a mercado angloparlante en el futuro).

### Cruche
- Gestiona el lado comercial y digital del proyecto
- No es Barbara — son dos personas distintas

---

## Decisiones de marca tomadas (no reabrir)

| Decisión | Resultado |
|---|---|
| Nombre comercial | **Caminar Despiertos** (no "Despiertxs") |
| Dominio | **caminardespiertos.com** |
| La "x" inclusiva | Puede usarse en redes de Barbara (@_pasares) pero no en la marca comercial |
| Idioma del sitio | Español |
| Plataformas de reserva | WhatsApp Business + Airbnb Experiences |

---

## Identidad visual

### Paleta
```css
--ink:      #1a1612;   /* fondo principal */
--cream:    #f7f2ea;   /* texto principal */
--warm:     #ede5d4;   /* fondos secundarios */
--terra:    #b8601e;   /* acento principal */
--terra-l:  #d4845a;   /* acento claro */
--stone:    #7a6f62;   /* texto secundario */
--stone-l:  #a89f94;   /* texto terciario */
--dark:     #0f0d0a;   /* negro profundo */
```

### Tipografía
- **Display / títulos:** Cormorant Garamond (Google Fonts) — serif, itálica para énfasis
- **Body / UI:** DM Sans (Google Fonts) — sans-serif, weight 300/400/500
- **Tono visual:** editorial oscuro, estética de fotografía análoga, grano de película, tonos tierra

### Grain overlay
El sitio usa un SVG noise como `body::before` para simular grano fotográfico analógico. Mantenerlo en cualquier nuevo componente.

---

## Archivos existentes

| Archivo | Descripción | Estado |
|---|---|---|
| `caminardespiertos.html` | Landing page completa (una sola página) | ✅ Listo — faltan fotos reales |
| `CaminarDespiertos_MetaAds.pdf` | Kit de campaña Meta Ads completo | ✅ Listo |
| `CaminarDespiertos_Ebook.pdf` | Ebook de marca — historia de Barbara | ✅ Listo |

---

## Estructura del sitio (`caminardespiertos.html`)

El sitio es una **single page** con estas secciones en orden:

1. **Nav** — fija, con scroll effect. Logo + links + CTA "Reservar"
2. **Hero** — grid 2 columnas. Izquierda: copy + meta + CTAs. Derecha: foto principal (placeholder)
3. **Quote** — manifiesto de una línea: *"Hay gente que llega a una ciudad y la ve. Y hay gente que llega y la siente."*
4. **Qué es** (`#que-es`) — sticky left con título + body. Right con 4 pillares animados
5. **Photo grid** — 5 fotos: 1 vertical grande (2 rows) + 4 pequeñas
6. **Barbara** (`#barbara`) — foto de Barbara + bio en primera persona + link a @_pasares
7. **Precios** (`#precios`) — 2 cards: Solo (USD 75) y Para dos (USD 130 / pareja)
8. **Reservar** (`#reservar`) — izquierda: WhatsApp + Airbnb. Derecha: formulario de email (captura de leads)
9. **Testimonios** — 3 cards (Valeria G. / México, Rodrigo M. / Bogotá, Ana y Carlos / Madrid)
10. **FAQ** — accordion con 5 preguntas
11. **Footer** — logo + links + "Buenos Aires, Argentina"

### Pendiente crítico — reemplazar placeholders de fotos
Hay 6 bloques de color oscuro donde van fotos reales. Cada uno tiene un comentario HTML marcado:
```html
<!-- <img src="foto.jpg" alt="" style="width:100%;height:100%;object-fit:cover;"> -->
```

| Placeholder | Ubicación | Proporción sugerida |
|---|---|---|
| `photo-hero` | Hero derecha | vertical, 16:9 o taller |
| `photo-cell:first-child` | Grid, columna grande | vertical, ocupa 2 rows |
| `photo-cell:nth-child(2)` | Grid pequeña | horizontal |
| `photo-cell:nth-child(3)` | Grid pequeña | horizontal |
| `photo-cell:nth-child(4)` | Grid pequeña | horizontal |
| `photo-cell:nth-child(5)` | Grid pequeña | horizontal |
| `barbara-photo` | Sección Barbara | 3:4 vertical (retrato) |

---

## Funcionalidades JS implementadas

- **Nav scroll effect:** clase `.scrolled` al pasar 60px
- **Fade-up animations:** IntersectionObserver con threshold 0.12 y stagger delay
- **FAQ accordion:** un ítem abierto a la vez
- **Email form:** submit previene default, muestra mensaje de éxito (sin backend todavía)

---

## Lo que falta implementar

### Prioridad alta
- [ ] Reemplazar todos los placeholders de fotos con imágenes reales de Barbara
- [ ] Actualizar número de WhatsApp real en el link `wa.me/5491100000000`
- [ ] Actualizar URL de Airbnb Experiences cuando esté publicado el listing
- [ ] Conectar formulario de email a un backend real (opciones: Netlify Forms, Formspree, o endpoint propio)

### Prioridad media
- [ ] Meta Pixel — agregar snippet cuando se active la campaña de Meta Ads
- [ ] Open Graph tags para compartir en redes (og:title, og:image, og:description)
- [ ] Google Analytics o Plausible para tracking
- [ ] Optimización de imágenes (WebP, lazy loading)

### Prioridad baja / Fase 2
- [ ] Versión en inglés del sitio (cuando se sume co-anfitrión bilingüe)
- [ ] Landing page de conversión para Meta Ads (con pixel y thank-you page)
- [ ] Sistema de reservas propio (por ahora WhatsApp es suficiente)

---

## Contexto de negocio relevante para el desarrollo

### Canales de reserva (Fase 1)
1. **WhatsApp Business** — canal principal para LatAm. Respuesta < 3 horas.
2. **Airbnb Experiences** — da confianza y visibilidad orgánica. Comisión ~20%.
3. **Email** — captura de leads de personas que todavía están planificando el viaje.

### Campaña Meta Ads
- Mercados: México, Colombia, España, Chile/Uruguay
- Presupuesto: USD 200–500/mes
- Fase 1 objetivo: Mensajes (WhatsApp) o Tráfico — NO Conversiones todavía
- El kit completo está en `CaminarDespiertos_MetaAds.pdf`
- **Bloqueador actual:** necesita fotos reales del recorrido antes de activar

### Precios
- Individual: USD 75/persona
- Pareja: USD 130/pareja (no por persona)

---

## Tono de comunicación

La voz del sitio es de Barbara en primera persona — introspectiva, honesta, con profundidad emocional pero sin grandilocuencia. Evitar:
- Lenguaje de turismo genérico ("experiencia única e irrepetible")
- Superlativas vacíos
- Anglicismos innecesarios
- Emojis en el sitio (sí en WhatsApp)

El copy del sitio se construyó tomando como base la voz real de Barbara en pasares.com.ar y sus entrevistas en medios (Página 12, Revista Ohlalá, Infobae).

---

## Links útiles

- Sitio de la obra de Barbara: https://www.pasares.com.ar
- Instagram: https://www.instagram.com/_pasares/
- Nota Página 12: https://www.pagina12.com.ar/598098-pasares-la-nueva-muestra-fotografica-de-barbara-prajs

---

*Última actualización: marzo 2026*
