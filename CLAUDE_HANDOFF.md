# Traspaso del proyecto a Claude

## Qué es este proyecto

Portfolio web de Gala Devincenti, estudiante de tercer año de Diseño Industrial en la Universidad Nacional de La Plata (UNLP). Es una landing estática, hecha en HTML, CSS y JavaScript, con estética moderna, tonos claros y acentos naranjas. El objetivo es mostrar su perfil y proyectos académicos y poder sumar trabajos con facilidad.

Sitio publicado: https://proyectos-de-gala.vercel.app/

## Cómo está organizado

- `index.html`: portada del portfolio, perfil, formación, contacto y tarjetas de proyectos.
- `styles.css`: estilos y adaptación responsive de la portada.
- `proyecto-grupo-12.html`: página de detalle del proyecto del asiento. El nombre del archivo quedó así por el origen del trabajo; en pantalla el proyecto se presenta como **C-seat**.
- `proyecto.css`: estilos de esa página de detalle.
- `models/`: archivos GLB que carga el visor 3D, imágenes de vista previa y recorte transparente usado en la tarjeta del portfolio.
- `C-Seat.fbx` y `C-Seat_plegado_final.fbx`: archivos FBX fuente actuales del modelo desplegado y plegado (exportados de Fusion). Se convierten a `models/c-seat-abierto.glb` y `models/c-seat-plegado.glb`, con vistas previas `c-seat-abierto-preview.png` y `c-seat-plegado-preview.png`.
- `asiento abierto ga.fbx` y `Configuración 1.fbx`: FBX de la versión anterior del asiento (ya no se usan en la página).
- `README.md`: instrucciones breves para editar y publicar la landing.

El sitio no usa framework, dependencias npm ni proceso de build. En Vercel el preset es **Other** y el directorio raíz es `./`.

## Contenido y decisiones de diseño

- El portfolio es para Gala, no para una empresa. Mantener una voz cercana y profesional, en español rioplatense.
- La identidad visual usa fondos claros, tipografía oscura y naranja como acento. La portada tiene un estilo editorial, con animaciones discretas y sin emojis.
- El nombre de Gala debe destacarse apenas se abre la página.
- Hacer que perfil, recorrido, formación y correo sean fáciles de leer, con tamaños notorios.
- Correo de contacto: `galadevincenti123@gmail.com`.
- El botón del CV debe permanecer visible pero desactivado hasta que se agregue el PDF. Cuando se entregue el CV, enlazarlo al archivo local.
- La tarjeta principal de C-seat en `index.html` usa `models/asiento-preview-cutout.png`, una imagen recortada para que el asiento conserve sus colores sobre el panel naranja.
- La página de C-seat muestra los modelos **01 Desplegado** y **02 Plegado**, uno debajo del otro en desktop, tablet y mobile. Mantener los modelos grandes y la página cómoda para pantallas táctiles.
- Los modelos interactivos usan `<model-viewer>` con controles para girar e inclinar. La biblioteca se carga desde Google CDN.
- Los colores y acabados están guardados dentro de los GLB, tomados del FBX de Fusion: metal cromado pulido (`Steel - Satin`), negro brillante (`ABS (White)`, que en Fusion está en negro) y puntas naranja vivo (`EPX 150`), igual que los renders de Fusion que mostró Gala. Se ajustó metalizado/rugosidad para el entorno `neutral` de model-viewer. El JavaScript de la página ya no modifica materiales. No se añadió geometría nueva; para cambiar la forma hay que editar en Fusion y volver a exportar.
- Hubo ocasiones en que el visor mostró un error de carga aunque existía una vista previa estática. Si vuelve a pasar, comprobar que los archivos GLB están en `models/`, que se publicaron los cambios y que el CDN y el visor cargan en el navegador. La interacción 3D debe revisarse desde el sitio HTTPS publicado, no abriendo el HTML con `file://`.
- No inventar textos, materiales, procesos ni datos biográficos. Dejar marcadores claros o pedirle a Gala la información y las imágenes reales.

## Cómo editar

1. Cambiar textos, enlaces y tarjetas en `index.html` o `proyecto-grupo-12.html`.
2. Cambiar el diseño en `styles.css` y `proyecto.css`.
3. Para sumar proyectos, agregar sus imágenes a una carpeta apropiada, crear una tarjeta en `index.html` y una página de detalle si corresponde.
4. Para actualizar el asiento, editar el original en Fusion, exportar FBX y convertirlo a GLB para la web; conservar las vistas previas estáticas como respaldo.
5. Mantener nombres de archivos sencillos y actualizar las rutas en el HTML al cambiar un archivo.

## Publicación

El proyecto está pensado para desplegarse en Vercel desde el repositorio de GitHub `Laradev88/Landing_Industrial_Design`. Al subir cambios a la rama `main`, Vercel inicia un nuevo deploy automáticamente. No hace falta correr un build. Confirmar que el deploy quede **Ready** antes de revisar la URL pública.

## Instrucciones sugeridas para el proyecto de Claude

> Trabajá sobre este portfolio estático de Gala. Antes de cambiar algo, revisá los archivos y conservá las decisiones de diseño y el contenido existentes. Usá HTML, CSS y JavaScript simples; no agregues frameworks ni dependencias si no hacen falta. Mantené una estética editorial clara con acentos naranjas, buen contraste, tipografía legible y adaptación a mobile y tablet. No inventes datos ni contenido de proyectos. No publiques ni hagas cambios externos sin que Gala lo pida. Al terminar, explicá qué archivos cambiaste y si hay que subir los cambios a GitHub para que Vercel los publique.

## Qué cargar en Claude

Conectá el repositorio de GitHub al proyecto de Claude para que pueda consultar el código. Añadí también este documento a la base de conocimiento del proyecto. Si no conectás el repositorio, subí como mínimo los HTML, CSS, `README.md` y la carpeta `models/`; los modelos FBX originales sirven como fuente para futuras modificaciones 3D.
