# CampusShop - Explicación del Código

Este proyecto es una tienda web de ropa maquetada únicamente con **HTML5 y CSS3 puro** (sin JavaScript ni frameworks externos). Toda la interactividad visual funciona mediante selectores y estados de CSS.

---

## 1. Estructura de Archivos

```text
Campus-shop/
├── index.html         # Página de inicio con buscador, categorías y novedades
├── catalogo.html      # Catálogo con filtros de categorías funcionales por CSS
├── producto.html      # Detalle de una prenda con selección de talla y cantidad
├── carrito.html       # Carrito de compras con opción de eliminar prendas
├── vacio.html         # Vista cuando no hay productos en el carrito
├── checkout.html      # Formulario de datos de envío y métodos de pago
├── historial.html     # Tarjetas con el historial de pedidos realizados
├── perfil.html        # Datos del usuario y accesos rápidos
├── css/
│   ├── base.css       # Variables globales (:root) y reseteo básico
│   ├── layout.css     # Estructura del cascarón (header, main, footer nav)
│   ├── components.css # Estilos de tarjetas, botones, inputs, menú lateral
│   └── responsive.css # Media queries para adaptar la web a tablet y PC
└── img/               # Imágenes de las prendas en formato .webp
```

---

## 2. Cómo están organizados los estilos CSS

El CSS está dividido en 4 archivos para que sea modular y fácil de mantener:

### `css/base.css` (Variables y Reset)

- Define las variables de color en `:root`:
  - `--color-primario: #4f46e5` (violeta/azul principal).
  - `--color-acento: #ede9fe` (violeta claro para badges y fondos suaves).
  - `--color-fondo: #f8fafc` (color de fondo de la web).
  - `--color-tarjeta: #ffffff` (blanco para las cards).
  - `--sombra-suave` y `--sombra-elevada` (sombras tenues para dar profundidad).
- Aplica el reseteo estándar (`box-sizing: border-box`, márgenes en 0 y tipografía del sistema).

### `css/layout.css` (Estructura general)

- `.contenedor-app`: Contenedor principal de la aplicación.
- `.encabezado-superior`: Barra superior fija (`position: sticky`) con el logo y el botón del menú.
- `main`: Área de contenido central (`flex: 1; align-content: start;`).
- `.navegacion-inferior`: Menú de navegación fijo en la parte inferior (`position: fixed`).

### `css/components.css` (Componentes visuales)

- **Tarjetas de producto (`.tarjeta-producto`)**:
  - Usan `display: flex; flex-direction: column; height: 100%;`.
  - El título tiene `min-height: 2.7em` y `line-clamp: 2` para que todos los títulos ocupen el mismo espacio.
  - El precio tiene `margin-top: auto`, lo que empuja el precio y el botón "Ver detalle" al fondo, manteniéndolos siempre alineados horizontalmente sin importar el largo del texto.
- **Botones**: `.boton-primario` (fondo sólido con hover) y `.boton-lineas` (borde con fondo transparente).
- **Formularios**: `.campo-formulario` con bordes redondeados y sombra violeta al hacer foco (`:focus`).
- **Historial (`.tarjeta-pedido`)**: Tarjetas de pedidos con líneas divisorias para cabecera, prendas y total.

### `css/responsive.css` (Media Queries)

Detecta el tamaño de la pantalla mediante `@media`:

1. **Móvil (< 640px)**: 2 columnas en productos, elementos apilados y dock inferior móvil.
2. **Tablet (640px a 1023px)**:
   - Catálogo pasa a 3 columnas.
   - Categorías en fila de 4 columnas.
   - Detalle de prenda, carrito, checkout y pedidos se dividen en 2 columnas equilibradas.
3. **Computador Completo (>= 1024px)**:
   - La pantalla se abre al 100% de ancho sin marcos de celular.
   - El contenido se centra con un ancho máximo de `1280px`.
   - Catálogo a 4 columnas y pedidos en 3 columnas simétricas.

---

## 3. Trucos interactivos con Puro CSS (Sin JavaScript)

El proyecto simula interactividad utilizando pseudo-clases y selectores avanzados de CSS:

1. **Abrir y cerrar el Menú Lateral:**

   - Hay un checkbox oculto (`#interruptor-menu`).
   - Al hacer clic en el icono `☰`, el checkbox cambia a `:checked`.
   - Con `#interruptor-menu:checked ~ .menu-lateral`, el menú cambia su posición de `left: -100%` a `left: 0`.
2. **Filtros por categoría en `catalogo.html`:**

   - Se usan radio buttons ocultos (`#filtro-sudaderas`, `#filtro-camisetas`, etc.).
   - Cuando uno está `:checked`, oculta las tarjetas que no corresponden mediante `:not()`:
     ```css
     #filtro-sudaderas:checked ~ main .cuadricula-productos .tarjeta-producto:not(.prenda-sudadera) {
         display: none;
     }
     ```
   - Además, la etiqueta activa cambia su color a violeta primario.
3. **Simular eliminación de prendas en `carrito.html`:**

   - Cada producto tiene un checkbox oculto (`#eliminar-item-1`, etc.).
   - Al hacer clic en la papelera `🗑️`, se desmarca el checkbox.
   - Con `:not(:checked)`, el item se oculta con `display: none;`.
   - Si ambos se desmarcan, se oculta la lista y aparece la sección `#seccion-carrito-vacio`.
4. **Selección de talla en `producto.html`:**

   - Radio buttons ocultos (`name="talla"`) asociados a `<label class="opcion-talla">`.
   - Con `.input-talla:checked + .opcion-talla`, la talla seleccionada se pinta de color violeta con texto blanco.

---

## 4. Cómo probar el código

Solo abre cualquiera de los archivos `.html` en tu navegador:

- En VS Code, haz clic derecho en `index.html` y selecciona **Open with Live Server**.
- O haz doble clic directo sobre `index.html` para abrirlo en el navegador.




# Numero
Maqueta
Resultado
Observaciones del Resultado Real (Diseño e Interfaz)
1![1789685744675](image/README/1789685744675.png)![1789692332554](image/README/1789692332554.png)Presenta un panel modal deslizable sobre fondo blanco con botón de cierre (`x`) en la esquina superior. Utiliza una lista vertical con íconos ilustrados a color y texto en tono oscuro para los enlaces ( *Inicio* ,  *Catálogo de Ropa* ,  *Mi Carrito* ,  *Mis Pedidos* ,  *Mi Perfil* ).
2![1789685775857](image/README/1789685775857.png)![1789685562331](image/README/1789685562331.png)Encabezado blanco con título "CampusShop" e íconos de acción en color azul rey (`#4C43EC`). Incorpora una barra de búsqueda gris clara, botones tipo *pills* para categorías con íconos, tarjetas de productos en 2 columnas con precios en COP, botones azules "Ver detalle" y barra de navegación inferior ( *Bottom Nav* ) fija.
3![1789685800113](image/README/1789685800113.png)![1789685586943](image/README/1789685586943.png)Barra superior con botón de retorno y título "Catálogo de Ropa". Incluye campo de búsqueda e historial de filtros horizontales con el estado activo "Todos" en azul. Tarjetas de producto con botón de corazón flotante, etiqueta de categoría superior en mayúsculas, precio destacado y botón "Ver prenda".
4![1789685855458](image/README/1789685855458.png)![1789685617055](image/README/1789685617055.png)Diseño centrado que utiliza una ilustración 3D de bolsas de compras en tonos azul y naranja. Muestra un título en negrita "Tu carrito está vacío", texto descriptivo en gris y un botón de ancho completo ( *CTA* ) "Explorar Catálogo de Ropa" estilizado en azul rey.
5 ![1789693623792](image/README/1789693623792.png) ![1789693743052](image/README/1789693743052.png) Marco de imagen con esquinas redondeadas sobre fondo gris tenue. Título principal en negrita, código de referencia (`#ROPA-67890`), precio en color azul rey (`$45.000 COP`), bloque descriptivo, botones cuadrados para selección de talla (resaltando la talla activa en azul), control numérico de cantidad y botón "Añadir al Carrito".
6 ![1789696415004](image/README/1789696415004.png) ![1789694201022](image/README/1789694201022.png) Vista con enlace superior "Vaciar carrito" en texto rojo. Las tarjetas de producto incluyen selectores desplegables ( *dropdowns* ) para `Talla` y `Cant`, ícono de papelera gris y precio en azul. Cuenta con un botón de borde azul `+ Agregar más prendas`, tarjeta de desglose (Subtotal, Impuestos 19%, Total) y botón "Proceder al Pago".
7![1789685919355](image/README/1789685919355.png)![1789685639469](image/README/1789685639469.png)Tarjetas de órdenes numeradas (`#ORD-XXXX`) con indicación de estado a la derecha ("En Preparación", "Entregado"). Detalla fecha de compra, resumen de prendas en texto secundario, monto total en azul y etiquetas de confirmación como "Pagado" o "✓ Recibido" en verde.
8![1789685942691](image/README/1789685942691.png)![1789685669027](image/README/1789685669027.png)Tarjeta de usuario destacada con ícono de avatar, datos personales y la etiqueta flotante "Estudiante Activo". Lista de menú vertical encerrada en contenedores con bordes redondeados y flechas indicadoras (`>`), terminando con un botón de contorno azul para "Cerrar Sesión".
9![1789693802643](image/README/1789693802643.png) ![1789693398554](image/README/1789693398554.png) Formulario organizado en 3 bloques independientes con íconos identificadores:
**Datos de Entrega:** Campos para  *Nombre* ,  *Dirección/Salón* , *Ciudad* y *Teléfono* con textos de ejemplo.
**Método de Pago:** Lista vertical con opciones ( *Tarjeta* ,  *Nequi/Daviplata* ,  *Efectivo* ) seleccionables mediante  *radio buttons
**Resumen del Pedido:** Desglose financiero resaltando "Envío campus: Gratis" y botón azul "Confirmar Pedido".*
