# Instrucciones para Configurar Firebase

Firebase permite que los datos se sincronicen entre todos los usuarios, sin importar desde qué dispositivo accedan.

## Paso 1: Crear un Proyecto en Firebase

1. Ve a [Firebase Console](https://console.firebase.google.com/)
2. Haz clic en **"Agregar proyecto"** o **"Crear un proyecto"**
3. Ingresa un nombre para tu proyecto (ej: "baby-shower-regalos")
4. Sigue los pasos del asistente (puedes desactivar Google Analytics si no lo necesitas)
5. Haz clic en **"Crear proyecto"**

## Paso 2: Crear Realtime Database

1. En el menú lateral, haz clic en **"Realtime Database"**
2. Haz clic en **"Crear base de datos"**
3. Selecciona una ubicación (elige la más cercana a tus usuarios)
4. Haz clic en **"Siguiente"**
5. En **"Reglas de seguridad"**, selecciona **"Modo de prueba"** (para desarrollo)
6. Haz clic en **"Habilitar"**

## Paso 3: Configurar Reglas de Seguridad

1. En Realtime Database, ve a la pestaña **"Reglas"**
2. Reemplaza las reglas con:
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```
3. Haz clic en **"Publicar"**

⚠️ **NOTA**: Estas reglas permiten lectura y escritura a todos. Para producción, deberías restringir el acceso.

## Paso 4: Obtener la Configuración

1. En Firebase Console, haz clic en el ícono de **configuración (⚙️)** > **"Configuración del proyecto"**
2. Desplázate hacia abajo hasta **"Tus aplicaciones"**
3. Haz clic en el ícono de **Web (</>)** para agregar una app web
4. Ingresa un nombre para la app (ej: "Baby Shower")
5. **NO marques** "También configurar Firebase Hosting" (a menos que lo necesites)
6. Haz clic en **"Registrar app"**
7. Copia la configuración que aparece (firebaseConfig)

## Paso 5: Configurar en el HTML

1. Abre el archivo `index.html`
2. Busca la sección que dice:
```javascript
const firebaseConfig = {
    apiKey: "TU_API_KEY_AQUI",
    ...
};
```
3. Reemplaza todos los valores con los que copiaste de Firebase
4. Guarda el archivo

## Paso 6: Probar

1. Sube el archivo a GitHub Pages
2. Abre la página desde dos dispositivos diferentes
3. Confirma un regalo desde un dispositivo
4. En el otro dispositivo, recarga la página
5. El regalo confirmado debería desaparecer de las opciones

## Estructura de Datos en Firebase

Firebase guardará dos nodos:
- `regalos_confirmados`: Array de IDs [1, 5, 12, ...]
- `confirmaciones`: Array de objetos [{nombreRegalo: "...", nombrePersona: "..."}, ...]

## Ventajas de Firebase

✅ **Sincronización en tiempo real**: Los cambios se reflejan automáticamente
✅ **Acceso desde cualquier dispositivo**: Los datos están en la nube
✅ **Gratis para uso básico**: El plan gratuito es suficiente para la mayoría de casos
✅ **Sin servidor propio**: No necesitas configurar un backend

## Fallback a localStorage

Si Firebase no está configurado, el sistema usará localStorage automáticamente. Esto significa que:
- Funcionará localmente sin configuración
- Pero NO se sincronizará entre dispositivos
- Para sincronización, es necesario configurar Firebase

## Funciones de Administración

Si alguien seleccionó mal un regalo o quieres hacer pruebas, puedes usar estas funciones desde la **consola del navegador** (presiona F12):

### Ver confirmaciones
```javascript
verConfirmaciones()
```
Muestra todas las confirmaciones con el nombre del regalo y la persona.

### Ver regalos confirmados
```javascript
verRegalosConfirmados()
```
Muestra los IDs de los regalos confirmados y sus nombres.

### Eliminar un regalo específico
```javascript
eliminarRegaloConfirmado(5)
```
Elimina el regalo con ID 5, haciéndolo disponible nuevamente. Reemplaza `5` con el ID que quieras eliminar.

### Eliminar confirmaciones de una persona
```javascript
eliminarConfirmacionesPorPersona("Juan Pérez")
```
Elimina todas las confirmaciones de una persona específica.

### Resetear todo
```javascript
resetearTodo()
```
⚠️ **CUIDADO**: Elimina TODAS las confirmaciones. Aparecerá un mensaje de confirmación.

### Ejemplo de uso

1. Abre la página en el navegador
2. Presiona **F12** (o clic derecho > "Inspeccionar")
3. Ve a la pestaña **"Console"**
4. Escribe una de las funciones y presiona Enter:
   ```javascript
   verConfirmaciones()
   ```
5. Para eliminar un regalo, primero ve cuál es su ID:
   ```javascript
   verRegalosConfirmados()
   ```
   Luego elimínalo:
   ```javascript
   eliminarRegaloConfirmado(12)
   ```

## Solución de Problemas

- **"Firebase no configurado"**: Verifica que hayas copiado correctamente la configuración
- **"Error al inicializar Firebase"**: Verifica que las reglas de seguridad permitan lectura/escritura
- **Los datos no se sincronizan**: Asegúrate de que Firebase esté correctamente configurado y que las reglas permitan acceso
- **No puedo eliminar un regalo**: Asegúrate de usar el ID correcto. Usa `verRegalosConfirmados()` para ver los IDs disponibles

