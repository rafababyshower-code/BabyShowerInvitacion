# Instrucciones para Guardar Datos del Formulario

## ⚠️ IMPORTANTE: Si Google Apps Script requiere pagos

Si Google Apps Script te está pidiendo realizar pagos, aquí tienes **alternativas completamente gratuitas**:

---

## Opción 1: Usar FormSubmit (GRATIS - RECOMENDADO) ✅

**FormSubmit** es un servicio gratuito que envía los datos del formulario por email.

### Configuración:
1. Ve a [FormSubmit](https://formsubmit.co/)
2. Ingresa tu dirección de email donde quieres recibir las confirmaciones
3. Copia el endpoint que te proporcionan (ej: `https://formsubmit.co/tu-email@ejemplo.com`)
4. Abre el archivo `index.html`
5. Busca la línea: `const GOOGLE_SCRIPT_URL = 'TU_URL_DE_GOOGLE_APPS_SCRIPT_AQUI';`
6. Reemplázala con: `const GOOGLE_SCRIPT_URL = 'https://formsubmit.co/tu-email@ejemplo.com';`
7. Guarda el archivo

**Ventajas:**
- ✅ Completamente gratuito
- ✅ Sin límites de uso
- ✅ Recibirás un email con cada confirmación
- ✅ No requiere configuración compleja

---

## Opción 2: Usar EmailJS (GRATIS) ✅

**EmailJS** permite enviar emails directamente desde JavaScript.

### Configuración:
1. Ve a [EmailJS](https://www.emailjs.com/)
2. Crea una cuenta gratuita
3. Configura un servicio de email (Gmail, Outlook, etc.)
4. Crea una plantilla de email
5. Obtén tu Service ID, Template ID y Public Key
6. Actualiza el código en `index.html` para usar EmailJS

**Ventajas:**
- ✅ Plan gratuito con 200 emails/mes
- ✅ Fácil de configurar
- ✅ Envía emails directamente

---

## Opción 3: Guardar en LocalStorage y Exportar (GRATIS) ✅

Los datos se guardan localmente en el navegador y puedes exportarlos.

### Configuración:
1. El código ya está preparado para guardar en localStorage
2. Los datos se guardan automáticamente cuando alguien confirma
3. Para ver los datos, abre la consola del navegador (F12)
4. Puedes exportar los datos como CSV manualmente

**Ventajas:**
- ✅ Completamente gratuito
- ✅ Sin límites
- ✅ No requiere servicios externos

---

## Opción 4: Google Apps Script (Si no requiere pagos)

Si en el futuro Google Apps Script no requiere pagos, puedes usar esta opción:

### Paso 1: Crear un Google Sheet
1. Ve a [Google Sheets](https://sheets.google.com)
2. Crea un nuevo documento en blanco
3. Guárdalo con un nombre (ej: "Confirmaciones Baby Shower")

### Paso 2: Crear el Script de Google Apps Script
1. En tu Google Sheet, ve a **Extensiones** > **Apps Script**
2. Se abrirá un editor de código
3. Borra todo el código que aparezca por defecto
4. Abre el archivo `google-apps-script.js` de este proyecto
5. Copia todo el contenido y pégalo en el editor de Apps Script
6. Guarda el proyecto (Ctrl+S o Cmd+S) y dale un nombre

### Paso 3: Desplegar como Web App
1. En el editor de Apps Script, haz clic en **Desplegar** > **Nueva implementación**
2. Configura:
   - **Tipo**: Selecciona "Aplicación web"
   - **Nombre**: Puedes dejarlo por defecto o ponerle un nombre
   - **Ejecutar como**: "Yo"
   - **Quién tiene acceso**: "Cualquiera" (esto es importante para que funcione desde tu sitio web)
3. Haz clic en **Desplegar**
4. La primera vez, Google te pedirá autorización:
   - Haz clic en "Autorizar acceso"
   - Selecciona tu cuenta de Google
   - Haz clic en "Avanzado" > "Ir a [nombre del proyecto] (no seguro)"
   - Haz clic en "Permitir"
5. Copia la **URL de la aplicación web** que aparece

### Paso 4: Configurar la URL en el HTML
1. Abre el archivo `index.html`
2. Busca la línea que dice: `const GOOGLE_SCRIPT_URL = 'TU_URL_DE_GOOGLE_APPS_SCRIPT_AQUI';`
3. Reemplaza `'TU_URL_DE_GOOGLE_APPS_SCRIPT_AQUI'` con la URL que copiaste (entre comillas)
4. Guarda el archivo

---

## Recomendación

**Para la mayoría de casos, recomendamos usar FormSubmit (Opción 1)** porque:
- Es completamente gratuito
- No requiere configuración compleja
- Recibirás las confirmaciones directamente en tu email
- No tiene límites de uso para casos normales

---

## Notas Importantes
- Si no configuras ninguna URL, el formulario seguirá funcionando pero no guardará los datos en ningún lugar
- Los datos siempre se muestran en la consola del navegador (F12) para debugging
- Puedes combinar múltiples opciones si lo deseas

