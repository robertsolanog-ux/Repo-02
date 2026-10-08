# Mi Finanzas · App Android

App nativa con **widget** (Ingreso / Gasto) y **botón en ajustes rápidos** para registrar en segundos.
Usa tu misma hoja de Google Sheets: lo que registres aquí aparece en la app web.

## 1. Preparar Apps Script (una sola vez)
1. Reemplaza `Code.gs` e `Index` con los archivos nuevos y guarda.
2. En el editor, elige la función **crearToken** y pulsa **Ejecutar**. Abre **Registro de ejecución** y copia tu clave.
3. **Implementar → Nueva implementación → Aplicación web**
   - Ejecutar como: **Yo**
   - Quién tiene acceso: **Cualquier persona** (la clave personal es la que protege tus datos)
4. Copia la URL que termina en `/exec`.
   Desde ahora la web también se abre con `…/exec?t=TU_CLAVE`.

## 2. Compilar el APK
Necesitas **Android Studio** (Hedgehog o más nuevo, trae el JDK 17).
1. **File → Open** y elige la carpeta `MiFinanzasAndroid`. Espera a que termine "Gradle sync".
2. **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
3. Cuando termine, pulsa **locate**. El archivo es `app/build/outputs/apk/debug/app-debug.apk`.
4. Pásalo al teléfono e instálalo (permite "instalar apps desconocidas" para el explorador de archivos).

Por consola (con Gradle 8.5 instalado): `gradle assembleDebug`.
Para un APK firmado de distribución: **Build → Generate Signed Bundle / APK**.

## 3. Primer uso
1. Abre la app, pega la URL `/exec` y tu clave, y toca **Guardar y abrir**.
2. **Widget:** mantén pulsada la pantalla de inicio → Widgets → *Mi Finanzas*.
3. **Botón de ajustes rápidos:** desliza dos veces desde arriba → lápiz (editar) → arrastra **Registrar** al panel.
4. También hay atajos al mantener pulsado el ícono de la app: *Gasto* e *Ingreso*.

Si no hay internet, el registro queda en cola y se envía en cuanto abras la app o registres otro movimiento.
Para cambiar la conexión: Más → Configuración → *Conexión de la app Android*.

## Compilar con GitHub (sin Android Studio)
1. Crea un repositorio **privado** en github.com y sube todo el contenido de esta carpeta
   (incluida `.github/workflows/build-apk.yml`).
2. Entra a la pestaña **Actions**. La compilación corre sola al subir los archivos
   (o pulsa **Compilar APK → Run workflow**).
3. Cuando salga el check verde (3 a 6 minutos), abre la ejecución y descarga **MiFinanzas-APK** en la sección *Artifacts*.
   Es un .zip: al descomprimirlo está `app-debug.apk`.
