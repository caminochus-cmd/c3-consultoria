# 🎯 Guía de Configuración Web3Forms - C³ Consultoría

## ✅ SOLUCIÓN IMPLEMENTADA: Web3Forms

Todos tus formularios ahora usan **Web3Forms**, que:
- ✅ Funciona desde archivos locales (`file://`)
- ✅ No requiere servidor web
- ✅ Sin confirmación de email previa
- ✅ 250 envíos/mes gratis
- ✅ Dashboard para ver todos los envíos

---

## 📋 CONFIGURACIÓN EN 3 PASOS (5 minutos)

### PASO 1: Obtener tu Access Key de Web3Forms

1. **Ir a:** https://web3forms.com
2. **Hacer scroll** hasta el formulario "Get Your Access Key"
3. **Ingresar tu email:** `camino.chus@gmail.com`
4. **Hacer clic en:** "Get Access Key"
5. **Copiar** el Access Key que aparece (algo como: `a1b2c3d4-e5f6-7890-abcd-ef1234567890`)

### PASO 2: Aplicar el Access Key en los Cuestionarios

Abrir cada uno de estos 3 archivos HTML con un editor de texto (Notepad++, VSCode, o el Bloc de notas):

#### Archivos a editar:
- `Cuestionario_Autonomos_sin_trabajadores.html`
- `Cuestionario_Autonomos_con_trabajadores.html`
- `Cuestionario_basic_PYME.html`

#### Buscar esta línea (Ctrl+F):
```javascript
access_key: "TU_WEB3FORMS_ACCESS_KEY_AQUI",
```

#### Reemplazar por:
```javascript
access_key: "a1b2c3d4-e5f6-7890-abcd-ef1234567890", // TU ACCESS KEY REAL
```

### PASO 3: Aplicar el Access Key en el Formulario de Contacto

Abrir el archivo:
- `c3_landing_page_FINAL.html`

#### Buscar esta línea (Ctrl+F):
```html
<input type="hidden" name="access_key" value="TU_WEB3FORMS_ACCESS_KEY_AQUI">
```

#### Reemplazar por:
```html
<input type="hidden" name="access_key" value="a1b2c3d4-e5f6-7890-abcd-ef1234567890">
```

---

## 🧪 PASO 4: Probar el Envío

### Prueba 1: Cuestionario

1. Abrir `Cuestionario_Autonomos_sin_trabajadores.html` en tu navegador
2. Responder al menos 1 pregunta
3. Hacer clic en **"ENVIAR A C³"**
4. Deberías ver: ✅ "¡Cuestionario enviado correctamente!"
5. Revisar tu email `camino.chus@gmail.com`

### Prueba 2: Formulario de Contacto

1. Abrir `c3_landing_page_FINAL.html` en tu navegador
2. Hacer scroll hasta la sección de contacto
3. Llenar el formulario (Nombre, Email, Teléfono, Consulta)
4. Hacer clic en **"Enviar Consulta"**
5. Deberías ver: ✅ "¡Consulta enviada correctamente!"
6. Revisar tu email

---

## 📬 Formato de los Emails que Recibirás

### **Cuestionarios:**

**Asunto:** `C³ Cuestionario: Cuestionario Autónomos Sin Trabajadores`

**Contenido:**
```
From: Sistema C³ Consultoría
To: camino.chus@gmail.com

tipo_cuestionario: Cuestionario Autónomos Sin Trabajadores
fecha_envio: 18/2/2025, 15:30:45
preguntas_respondidas: 85
total_preguntas: 106
porcentaje_completado: 80%
promedio_general: 3.45

datos_json: {
  "metadata": {...},
  "estadisticas": {...},
  "respuestas": [...]
}
```

### **Formulario de Contacto:**

**Asunto:** `Nueva Consulta desde Landing C³`

**Contenido:**
```
From: Landing C³ Consultoría
To: camino.chus@gmail.com

nombre: Juan
apellidos: García López
email: juan.garcia@empresa.com
telefono: +34 600 123 456
consulta: Necesitamos ayuda con...
```

---

## 🎨 Personalización Avanzada (Opcional)

### Cambiar el Email Destino

Si en el futuro quieres enviar a otro email:

**En los Cuestionarios**, buscar:
```javascript
to_email: "camino.chus@gmail.com",
```
Cambiar por:
```javascript
to_email: "nuevo@email.com",
```

**En el Formulario de Contacto:**
Web3Forms usa el email con el que registraste el Access Key, 
pero puedes crear un nuevo Access Key con otro email.

### Personalizar el Asunto del Email

**En los Cuestionarios**, buscar:
```javascript
subject: `C³ Cuestionario: ${datosFormulario.metadata.formulario}`,
```
Cambiar por:
```javascript
subject: `Tu asunto personalizado`,
```

### Añadir Campos Personalizados

En el payload del cuestionario, puedes añadir cualquier campo:
```javascript
nombre_cliente: "Juan García",
empresa: "Mi Empresa SL",
telefono: "+34 600 123 456",
```

---

## 📊 Dashboard de Web3Forms

### Ver todos los envíos:

1. Ir a: https://web3forms.com/platforms
2. Ingresar tu email: `camino.chus@gmail.com`
3. Recibirás un link de acceso por email
4. **Verás:**
   - Todos los formularios enviados
   - Fecha y hora de cada envío
   - Todos los datos de cada envío
   - Estadísticas de uso

---

## ❓ Solución de Problemas

### Error: "Invalid access key"
**Solución:** Verificar que copiaste bien el Access Key (sin espacios ni comillas extra)

### Error: "CORS error"
**Solución:** Web3Forms debería funcionar desde `file://`, pero si tienes problemas:
1. Abrir los HTML desde un servidor local:
   ```bash
   python3 -m http.server 8000
   ```
2. Abrir: `http://localhost:8000/c3_landing_page_FINAL.html`

### No llega el email
**Revisar:**
- [ ] Carpeta de SPAM/Correo no deseado
- [ ] Esperar 1-2 minutos (a veces hay retraso)
- [ ] Verificar el Access Key en el código
- [ ] Ver el Dashboard de Web3Forms para confirmar que se recibió

### Error: "TU_WEB3FORMS_ACCESS_KEY_AQUI"
**Solución:** Todavía no has reemplazado el Access Key en el código. 
Ver PASO 2 y PASO 3 arriba.

---

## 🚀 Alternativa: Subir a Hosting (Sin configuración necesaria)

Si subes los HTML a un hosting gratuito, **FormSubmit volverá a funcionar** 
sin necesidad de Web3Forms ni configuración adicional:

### Opciones más simples:

#### **Netlify Drop** (30 segundos):
1. Ir a: https://app.netlify.com/drop
2. Arrastrar la carpeta con todos los HTML
3. Listo, FormSubmit funcionará automáticamente

#### **GitHub Pages** (5 minutos):
1. Crear cuenta en GitHub
2. Crear repositorio `c3-consultoria`
3. Subir archivos
4. Activar GitHub Pages en Settings
5. Listo, FormSubmit funcionará automáticamente

---

## ✅ Resumen Final

**Archivos modificados:**
- ✅ 3 Cuestionarios (usan Web3Forms)
- ✅ 1 Formulario de Contacto (usa Web3Forms)

**Configuración necesaria:**
- ⚠️ Obtener Access Key de Web3Forms (5 min)
- ⚠️ Reemplazar en 4 archivos HTML (2 min)

**Beneficios:**
- ✅ Funciona desde archivos locales
- ✅ Sin servidor web necesario
- ✅ 250 envíos/mes gratis
- ✅ Dashboard para ver envíos
- ✅ Notificaciones instantáneas

---

## 📞 Soporte

**Web3Forms:**
- Documentación: https://docs.web3forms.com
- Soporte: https://web3forms.com/support

**C³ Consultoría:**
- Email: camino.chus@gmail.com

---

🎉 **¡Listo para recibir cuestionarios y consultas!**

