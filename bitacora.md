
# BITACORA - RUEDA LIBRE

# 1. BITACORA DE URL Y RUTAS

## 1.1. Bitacora de la URL

- **URL completa:** http://127.0.0.1:5500/index.html
- **Host:** 127.0.0.1:5500
- **Puerto:** 5500
- **Ruta:** /index.html
- **Metodo de la peticion:** GET
- **Estado de codigo:** 200

## 1.2. Bitacora de la ruta que no existe

- **Ruta utilizada:** ejemplo.html
- **Error:** 404 Not Found
- **Significado:** La ruta del servidor si se establecio, pero el archivo solicitado no se encontro.

## 1.3. Bitacora de los archivos HTML, CSS y JavaScript

- **HTML:** Se va a utilizar para definir que hay en la pagina.
  ```html
  <h1>Rueda libre</h1>
  ```

- **CSS:** Se va a utilizar para darle presentacion a la pagina.
  ```css
  h1 { color: verde; }
  ```

- **JavaScript:** Se va a utilizar para definir como interactua el usuario con la pagina.
  ```javascript
  boton.addEventListener(...)
  ```

## 1.4. Bitacora de las rutas utilizadas

### index.html

| Origen | Destino | Ruta |
|---|---|---|
| index.html | Inicio | href="index.html" |
| index.html | Tarifas y Rutas | href="tarifas.html" |
| index.html | Reservas | href="reservas.html" |

### tarifas.html

| Origen | Destino | Ruta |
|---|---|---|
| tarifas.html | Inicio | href="../index.html" |
| tarifas.html | Tarifas y Rutas | href="tarifas.html" |
| tarifas.html | Reservas | href="reservas.html" |

### reservas.html

| Origen | Destino | Ruta |
|---|---|---|
| reservas.html | Inicio | href="../index.html" |
| reservas.html | Tarifas y Rutas | href="tarifas.html" |
| reservas.html | Reservas | href="reservas.html" |

# 2. ESQUEMA DE PAGINAS

## 2.1. index.html

```text
body
├── header
├── main
│   ├── section: Quienes somos
│   ├── section: Servicios (5 articulos)
│   ├── section: Pasos para alquilar
│   ├── section: Beneficios
│   ├── section: Encuentranos
│   └── section: Contacto
└── footer
```

## 2.2. tarifas.html

```text
body
├── header
├── main
│   ├── section: Tarifas
│   │   ├── section: Alquiler (tabla)
│   │   └── section: Recorridos (tabla)
│   └── aside: Que llevar
└── footer
```

## 2.3. reservas.html

```text
body
├── header
├── main
│   ├── section: Contacto (correo)
│   └── aside: Horarios de atencion
└── footer
```

# 3. CONTROLES Y VALIDACION DEL FORMULARIO

## 3.1. Justificacion de tres controles

- **Radio para el tipo de bicicleta:** Son solo tres opciones y el cliente debe elegir exactamente una.
- **Textarea para comentarios:** El texto libre puede ser largo y de varias lineas.
- **Select para la duracion:** Es una lista corta de valores fijos.

## 3.2. Pruebas de campos de la tabla de reservas

| Campo | Valor ingresado | Resultado |
|---|---|---|
| Celular | 3001234567 | Aceptado |
| Celular | 1234567890 | Rechazado (no empieza por 3) |
| Celular | 300123 | Rechazado (menos de 10 digitos) |
| Documento | 1020304050 | Aceptado |
| Documento | abc12345 | Rechazado (letras) |
| Documento | 12345 | Rechazado (menos de 6 digitos) |
| Nombre | Al | Rechazado (menos de 3 caracteres) |
| Correo | usuario@ | Rechazado (formato invalido) |
| Fecha | 2026-10-31 | Rechazada (antes del rango) |

# 4. AUDITORIA DE ACCESIBILIDAD

| Pagina | Problema encontrado | Solucion |
|---|---|---|
| index | img/bicicleta.png con alt="Bicicleta" es decorativa: aparece junto a los pasos y no aporta informacion. | Cambiar a alt="" |
| index | img/ruta.png es un mapa, y alt="Mapa de ubicacion de Rueda libre" es poco descriptivo. | alt="Mapa con la ubicacion de Rueda libre en el centro de Medellin, cerca de ciclovias" |
| index | El enlace "Ver en Google Maps" no dice a donde lleva. | Ver ubicacion de Rueda libre en Google Maps |
| tarifas | Tres enlaces identicos "Reserva ahora" en dos secciones. | Reserva ahora una bicicleta y Reserva ahora un recorrido. |
| reservas | Los radios estan sin un grupo con nombre. | Envolver los tres radios en un `<fieldset>` con `<legend>Tipo de bicicleta</legend>` en lugar del `<p>` suelto. |

# 5. MAPA DE USO DE COLOR

| Elemento | Color del texto | Fondo |
|---|---|---|
| Texto general | Azul Noche | Crema |
| Texto secundario | Gris Asfalto | Crema |
| Titulos y encabezado | Blanco (sobre Azul Noche) o Azul Noche (sobre Crema) | Azul Noche / Crema |
| Botones principales y enlaces | Blanco | Verde Ruta |
| Enlaces dentro de texto sobre Crema | Verde Ruta (con subrayado) | Crema |
| Destacados y botones secundarios | Azul Noche (nunca blanco) | Naranja Pedal |

# 6. URL DEL SITIO Y BITACORA DE ERROR

## 6.1. URL del sitio

https://mrgarcia3108.github.io/rueda-libre/

## 6.2. Bitacora del error de especificidad

### Codigo utilizado

```css
#menu a {
    color: var(--color-gris-asfalto);
}

.activo {
    color: var(--color-verde-ruta);
    font-weight: 600;
}
```

### Comparacion de especificidad

| Selector | ID | Clase | Etiqueta | Especificidad | Resultado |
|---|---:|---:|---:|---|---|
| #menu a | 1 | 0 | 1 | (1, 0, 1) | Gana en color |
| .activo | 0 | 1 | 0 | (0, 1, 0) | Pierde en color, aparece tachada |


# 7. CIERRE DE LA SEMANA 1 - V1.0

## 7.1. Que construi

- **Estructura:** Se hizo una estructura ordenada con HTML semantico.
- **Formulario:** Grupos con creacion de formulario con fieldset para un mejor orden.
- **Validacion:** Las reglas del cliente se cumplieron con sus correcciones.
- **Accesibilidad y publicacion:** Creacion de la URL en la herramienta de GitHub en GitHub Pages.
- **CSS con variables:** Paleta, tipografias y espaciado, con herencia desde `body`.
- **Selectores y cascada:** Conflicto ID contra clase resuelto por especificidad, y estados `:hover` y `:focus`.
- **Modelo de caja:** Ancho maximo, tarjetas, tablas y formulario.
- **Posicionamiento y cierre:** WhatsApp fijo y hoja de estilos organizada.

## 7.2. Flexbox: encabezado y pie

| Ancho aproximado | Encabezado | Pie |
|---|---|---|
| 576 PX | Se desplaza para la izquierda | Se desplaza para la izquierda |
| 768 PX | Se desplaza para la izquierda | Se desplaza para la izquierda |
| 1200 PX | Tiene su diseño original | Tiene su diseño original |

## 7.3. Cuadricula de la flota

| Ancho | Columnas |
|---|---|
| 1280 px | Se muestran 4 columnas |
| 900 px | Se muestran 3 columnas |
| 500 px | Se muestran 2 columnas |

## 7.4. Layout con Grid y Flexbox

| Caso | Herramienta | Por que |
|---|---|---|
| Portada | Grid | Dos columnas iguales |
| Galeria | Grid | Tres columnas iguales |
| Reservas | Grid | Proporcion exacta 2:1 |
| Fila | Flexbox | Solo hay una dimension |
| Encabezado | Flexbox | Una fila: nombre y menu |
| Pie | Flexbox | Una fila de tres bloques repartidos |

## 7.5. Problemas y soluciones

| Problema | Causa | Solucion |
|---|---|---|
| La tabla obligaba a desplazarse | display: block con overflow-x | Tabla normal con letra y relleno pequeños |
| El menu se amontonaba | space-between en una fila estrecha | Nombre y menu centrados, cada uno en su fila |
| Una imagen pasaba del ancho | Sin ancho maximo | img { max-width: 100%; height: auto; } |
| El pie quedaba con bloques apretados | Tres bloques en fila en pantalla estrecha | Una columna en el celular y fila desde 768 px |

# 8. PRUEBA CON BOOTSTRAP

## 8.1. Comparacion

### Que me dio Bootstrap

- Cuatro breakpoints ya definidos.
- Gutters uniformes con una sola clase.
- Tarjetas, botones y tipografia con aspecto uniforme.

### Que control perdi

- Los colores y las fuentes de la marca.
- La escala de espaciado con variables.
- El auto-fit: Bootstrap solo cambia en sus cuatro breakpoints.
- La repeticion de clases en cada columna.

## 8.2. Utilidades

| Utilidad | Funcion |
|---|---|
| flex-md-row | Cambia la direccion de los elementos a fila desde 768 px |
| d-none + d-md-block | Oculta el elemento y lo muestra como bloque desde 768 px |
| gap-3 | Separacion uniforme entre elementos de un contenedor flex |
| fs-4 | Tamaño de letra mayor, sin etiquetas de titulo |
| text-bg-dark | Fondo oscuro con texto de contraste automatico |

A comparacion con un CSS propio, Bootstrap agiliza mucho el trabajo que es darle a cada caracter un estilo.

## 8.3. Integracion de Bootstrap

### Conflictos y soluciones

1. **Tamaño de titulos:** Declare font-size de h1-h3 en styles.css, que carga despues.
2. **Colores de utilidades:** Redefini --bs-*-rgb en mi :root.
3. **Reglas de cuadricula antiguas:** Elimine las reglas #rutas y .portada.

Bootstrap se carga antes que styles.css y los div.row y div.col-* son obligatorios en la grilla de Bootstrap.

## 8.4. Comparativa final: V1.5 a V2.0

| Criterio | V1.5 (CSS propio) | V2.0-beta (Bootstrap) |
|---|---|---|
| Lineas de styles.css | Aproximado de 550 lineas de codigo (sin contar los comentarios). | Aproximado de 300 lineas de codigo (sin contar los comentarios). |
| Reduccion | Obtuve una reduccion estimada de entre 300 y 200 lineas de codigo en los estilos, con la eliminacion y modificacion de codigo. | |
| Tiempo invertido (Propio) | No tengo el tiempo exacto trabajado, pero la mitad de la primera semana, hasta el dia 2 de la semana 2 de HTML y CSS se trabaja en su mayoria con CSS y mas lo que adelante desde casa. | |
| Tiempo invertido (Bootstrap) | | De momento llevo todo un dia modificando la pagina a Bootstrap y estoy intentando que se vea casi igual a lo que llevaba en CSS propio. |

### Ventajas

- Me permitio organizar mejor la pagina sin tener que escribir tantas reglas de CSS.
- Clases como row, col-md-6 y col-lg-4 facilitan la distribucion y ahorraron tiempo al adaptar el diseño a celulares y computadores.
- Los botones y formularios ya tenian estilos definidos, lo que ayudo a mantener una apariencia mas ordenada.

### Desventajas

- Algunos elementos, como los titulos y formularios, tomaron estilos predeterminados que tuve que modificar para adaptarlo a mis estilos.
- El HTML quedo con mas clases y contenedores, por lo que en el codigo se veia mas largo.

### Conclusion

Bootstrap si me ayudo a trabajar mas rapido, al organizar las columnas y adaptar la pagina a diferentes pantallas. Aunque tuve que corregir estilos y agregar varias clases, me ahorro tiempo al no tener que escribir todo el CSS.

# 9. CIERRE DE LA SEMANA 2 - V2.0

## 9.1. Que construi

- Pagina aparte con la flota en la grilla y una seccion armada solo con utilidades.
- **Migracion:** Inicio, tarifas y reservas con grilla.
- **Navbar y botones:** Menu colapsable con pagina actual.
- **Cards y carrusel:** Tres promociones que rotan.
- **Formulario:** Validacion visual, mensajes por campo, alerta.
- **Personalizacion:** --bs-*, boton principal y variante naranja.

## 9.2. Que mejoraria

- Mover el foco al primer campo con error al enviar el formulario.
- Mejorar la seccion de promociones.

# 10. PROTOTIPO CON TAILWIND

## 10.1. Bootstrap

### HTML

```html
<a href="paginas/reservas.html" class="btn btn-primary btn-lg">
    Reserva ahora
</a>
```

### CSS

```css
.btn-primary {
    --bs-btn-bg: var(--color-verde-ruta);
    --bs-btn-hover-bg: var(--color-azul-noche);
}
```

Elegi un componente que ya existe, una variante. El aspecto ya venia hecho. Para que usara los colores de la pagina tuve que escribir CSS, sobrescribiendo Bootstrap.

## 10.2. Utilidades

Cada clase hace una sola cosa (color de fondo, relleno, bordes redondeados, grosor de letra), sin CSS.

## 10.3. Diferencias

| Bootstrap | Tailwind |
|---|---|
| Piezas ya diseñadas | Clases pequeñas de una sola propiedad |
| Las clases de Bootstrap y en mi CSS | En el HTML, en cada elemento |
| Sobrescribir variables | Cambiar las clases del elemento |
| Pocas | Muchas |
| Estilo Bootstrap | Parte de cero |

### Diferencia

Un framework de componentes me entrega elementos ya diseñados y yo los personalizo, uno utility-first me entrega las piezas y yo diseño cada elemento.

# 11. TAILWIND CLI

## 11.1. Configuracion

- Instale tailwindcss y @tailwindcss/cli con npm dentro de la carpeta nocturna.
- src/input.css contiene @import "tailwindcss";.
- .gitignore excluye node_modules/.
- Comando:

```bash
npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch
```

## 11.2. Que encontre en output.css

| Clase | Resultado | Explicacion |
|---|---|---|
| rounded-lg | Si | La CLI la detecto en index.html y genero su CSS |
| bg-pink-500 | No | Ningun archivo la menciona, asi que no se genera |
| bg-pink-500 escrita en index.html | Si, aparece al guardar | --watch la CLI regenera el archivo |

### Por que una clase que no uso no aparece

Tailwind lee los archivos del proyecto, detecta los nombres y genera CSS solo para esos.

## 11.3. Botones

| Tipo | Apariencia | Hover | Focus |
|---|---|---|---|
| Principal | Fondo y texto: Naranja Pedal con texto Azul Noche | Fondo blanco y sombra mayor | Anillo blanco de 4 px |
| Secundario | Fondo y texto: Crema con texto Azul Noche | Fondo Naranja Pedal y sombra mayor | Anillo blanco de 4 px |
| Contorno | Fondo y texto: Borde y texto Crema, sin fondo | Fondo Crema con texto Azul Noche | Anillo naranja de 4 px |

## 11.4. Por que la CLI y no Play CDN

El Play CDN compila cada vez que se abre la pagina y es para desarrollo. La CLI genera una hoja estatica que GitHub Pages puede servir.

## 11.5. Kit de componentes

| Elemento | Clases | Uso |
|---|---|---|
| Radios de borde | rounded-lg | Botones, campos, alertas |
| Grande para contenedores | rounded-xl | Card |
| Total para etiquetas | rounded-full | Etiqueta de nivel |
| Grosor de borde | border-2, border-l-4 | Campos, boton de contorno, card, alertas |
| Colores | bg-[#14213D], bg-[#FAF6EF], bg-[#F39A2B], bg-[#1E7A4F], text-[#5B6470], text-white | Todos los componentes |
| Sombras | shadow-md hover:shadow-lg, shadow-lg hover:shadow-2xl | Botones, card |
| Foco | focus:outline-hidden focus:ring-4 | Botones y campos |
| Tipografia | font-bold, font-extrabold, uppercase, tracking-widest | Todos |

## 11.6. Como comparar

- Los cuatro usan rounded-lg o rounded-xl.
- Ningun componente usa un espaciado fuera de la escala.

## 11.7. Por que utilice Grid

Con Flexbox, el ancho de cada paso dependeria de la longitud de texto, y las columnas no quedarian alineadas. Con Grid, el contenedor define las columnas y cada paso ocupa una de ellas.

## 11.8. Contenedor comun

- `mx-auto max-w-6xl px-6`: centrado, ancho maximo y relleno lateral.

## 11.9. Comportamiento

| Ancho | Encabezado | Rutas | Pasos | Pie |
|---|---|---|---|---|
| 360 px | Apilado: logo y boton | 1 columna | 1 columna | Apilado |
| 768 px | En fila, con enlaces | 2 columnas | 2 columnas | En fila |
| 1024 px | En fila | 3 columnas | 4 columnas | En fila |
| 1280 px | En fila | 3 columnas | 4 columnas | En fila |

# 12. BOOTSTRAP FRENTE A TAILWIND

## 12.1. Clases repetidas y @apply

- Elegi los botones para `@apply` porque su lista de clases es la mas larga: 6 veces en la landing.
- Cree tres clases en `@layer components`: `btn-principal`, `btn-secundario` y `btn-contorno`.
- `index.html` paso de 33476 (sin --watch) a 26271 (con --minify) bytes.
- Las cards se quedaron con el marcado del kit, repetido tal cual.

## 12.2. Orden de clases

Layout, espaciado, tipografia, color y acabado, y estados (con `dark:` al final).

## 12.3. Comparativa

| Criterio | Bootstrap | Tailwind |
|---|---|---|
| **Curva de aprendizaje** | Fue facil: CDN, `container`, `row`, `col-*`, `btn btn-primary` y con ejemplos para copiar. Lo dificil al personalizar. | Mas lento: instalar Node, CLI, `.gitignore`, `--watch`, y aprender utilidades y prefijos (`md:`, `hover:`, `dark:`). |
| **Personalizacion** | Sobrescribi `--bs-*`, `--bs-btn-*`. Conflictos: titulos, colores, `legend` formulario y contraste de la validacion. | `@theme` definio colores y fuentes, y genero utilidades con nombres. `dark:` modo oscuro. `--color-*: initial` solo colores marca. |
| **Tamaño final** | CSS: [33476]. | CSS minificado: [26271]. |
| **Casos de uso** | Sitios con muchos componentes: navbar colapsable, carrusel, modal, alertas y formularios. Los use en Rueda Libre v2.0. | Landings y paginas, sin JavaScript, con modo oscuro y tamaño. |

## 12.4. Recomendacion para Rueda Libre

Tailwind para las paginas nuevas de Rueda Libre, empezando por la campaña Rueda Nocturna. El criterio que mas peso fue. Bootstrap daba hechos el menu colapsable, el carrusel y el modal, con Tailwind construirlos o añadir JavaScript propio. Por eso, si el sitio necesita muchos componentes interactivos, Bootstrap sigue siendo mejor.
