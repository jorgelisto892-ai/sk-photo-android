# SK Photo para Android

Editor de fotos y collage. Este proyecto convierte la app web (carpeta `www`) en una app Android con Capacitor.

Hay dos formas de sacar el APK. La **A** no necesita instalar nada en tu computadora.

---

## A0. Subir el proyecto con VS Code (lo más fácil)

1. Instala **Git** desde https://git-scm.com (en Windows deja todas las opciones como vienen).
2. En VS Code: **Archivo → Abrir carpeta** y elige la carpeta `sk-photo-android` (la que tiene `package.json`).
3. Primera vez solamente: abre **Terminal → Nueva terminal** y escribe, con tus datos:
   ```
   git config --global user.name "Tu Nombre"
   git config --global user.email "tucorreo@ejemplo.com"
   ```
4. Toca el ícono de **Control de código fuente** en la barra izquierda (tres circulitos unidos por líneas) → **Publicar en GitHub**.
5. Inicia sesión en GitHub cuando te lo pida el navegador, elige **privado** y deja todos los archivos marcados.
6. Sigue desde el paso 6 de la opción A (pestaña Actions).

Para subir cambios después: en Control de código fuente escribe un mensaje corto, toca **Confirmar** y luego **Sincronizar cambios**.

## A. Compilar en GitHub (recomendado)

GitHub tiene computadoras que compilan el APK por ti, gratis.

1. Crea una cuenta en https://github.com si no tienes.
2. Arriba a la derecha: **+ → New repository**. Nombre: `sk-photo`. Déjalo **Private** si quieres. Pulsa **Create repository**.
3. En la página del repositorio vacío, pulsa el enlace **uploading an existing file**.
4. Descomprime el ZIP en tu computadora y **arrastra todo el contenido** de la carpeta `sk-photo-android` (no la carpeta en sí, lo que hay adentro) a la ventana de GitHub. Pulsa **Commit changes**.
5. Revisa que se haya subido la carpeta `.github`. Algunas computadoras ocultan las carpetas que empiezan con punto y no la suben. Si no aparece, ve a la sección **"Si no se subió .github"** abajo.
6. Ve a la pestaña **Actions**. Verás "Construir APK" corriendo (círculo amarillo). Tarda de 5 a 10 minutos. Cuando termine tendrá una palomita verde.
7. Ve a la página principal del repositorio y, a la derecha, entra a **Releases**. Ahí está `SK-Photo.apk`.

### Si no se subió .github

En el repositorio: **Add file → Create new file**. En el nombre escribe exactamente
`.github/workflows/build-apk.yml`
Abre ese mismo archivo del ZIP con el Bloc de notas, copia todo y pégalo. Pulsa **Commit changes**. La compilación arranca sola.

### Para hacer una versión nueva

Sube el archivo cambiado (por ejemplo `www/index.html`) con **Add file → Upload files**, con el mismo nombre y en la misma carpeta. GitHub compila otra vez y aparece una nueva entrada en Releases. Como siempre se firma con la misma llave de prueba, la nueva versión se instala encima de la anterior sin borrarla.

---

## Instalar el APK en tu teléfono

1. En el teléfono, abre Chrome, entra a tu repositorio en github.com (inicia sesión si es privado) → **Releases** → toca `SK-Photo.apk`.
2. Cuando termine de bajar, toca el archivo.
3. Android pedirá permiso para **instalar apps de fuentes desconocidas** desde Chrome. Actívalo y regresa.
4. Si Play Protect avisa que la app no es conocida, elige **Instalar de todos modos**. Es normal: la app no viene de Play Store.
5. Busca **SK Photo** en tus apps.

---

## B. Compilar en tu computadora con Android Studio

Necesitas una computadora con Windows, Mac o Linux y unos 10 GB libres.

1. Instala **Node.js** versión 22 o más nueva desde https://nodejs.org (la opción LTS).
2. Instala **Android Studio** desde https://developer.android.com/studio. La primera vez que lo abras, deja que descargue el SDK de Android.
3. Abre una terminal dentro de la carpeta `sk-photo-android` y ejecuta:

   ```
   npm install
   npm run android
   npm run open
   ```

4. Se abre Android Studio. Espera a que termine "Gradle sync" (barra de abajo).
5. Para tener el APK: menú **Build → Build App Bundle(s) / APK(s) → Build APK(s)**. Al terminar, el aviso trae un enlace **locate** que abre la carpeta del APK.
6. O conecta tu teléfono por USB con la **depuración USB** activada (Ajustes → Acerca del teléfono → toca 7 veces "Número de compilación" → Opciones de desarrollador → Depuración USB) y pulsa el botón verde ▶ de Android Studio.

Cada vez que cambies `www/index.html`, ejecuta `npm run sync` y vuelve a compilar.

---

## Qué hay en esta carpeta

| Archivo | Para qué sirve |
|---|---|
| `www/index.html` | La app completa |
| `capacitor.config.json` | Nombre de la app (SK Photo) y su identificador (`com.skphoto.editor`) |
| `package.json` | Las piezas de Capacitor que se instalan |
| `assets/` | Ícono y pantalla de inicio |
| `.github/workflows/build-apk.yml` | Las instrucciones que GitHub sigue para compilar |
| `keystore/debug.keystore` | Llave de firma **solo para pruebas** |

## Importante

- Este APK es de **prueba**. Para publicar en Google Play se necesita otra llave de firma, privada, que no se sube a ningún lado.
- Al guardar una imagen, la app abre el menú de compartir de Android. Elige **Archivos** (o "Guardar en el dispositivo") para dejarla en el teléfono, o cualquier app para mandarla.
- Las tipografías vienen de internet. Sin conexión, la app usa las letras del sistema y funciona igual.
