# Sitio Web - Isabella Prieto - Psicóloga Especialista en Trastornos Alimentarios

Website profesional y responsive para Isabella Prieto, psicóloga especializada en trastornos alimentarios.

## Características

- 5 secciones informativas sobre la psicóloga y trastornos alimentarios
- Diseño completamente responsive usando Tailwind CSS
- **Sistema de agendamiento de citas con Google Calendar**
- Modales informativos para cada trastorno alimentario
- Formulario de contacto funcional
- Integración con WhatsApp
- Navegación smooth scroll
- Menú móvil responsivo
- Enlaces a redes sociales (Facebook, Instagram)

## Configuración Importante

### 1. Sistema de Agendamiento de Citas (Cal.com)

El sitio incluye un sistema de agendamiento integrado con **Cal.com** que automáticamente redirige a los pacientes al pago después de agendar.

**¿Por qué Cal.com?**
- ✅ **Redirect gratuito** (Calendly cobra $12/mes por esto)
- ✅ **Webhooks gratuitos**
- ✅ **Todas las funciones que necesitas - GRATIS**

**Para activarlo:**

1. Lee el archivo **`CALCOM_SETUP.md`** que contiene instrucciones detalladas paso a paso
2. Crea tu cuenta gratuita en [Cal.com](https://cal.com)
3. Configura tu tipo de evento (Consulta Psicológica - 60 minutos)
4. **Configura el redirect URL** en Cal.com (Advanced → Success Redirect URL → pago.html)
5. Obtén tu enlace de Cal.com (ej: `cal.com/tu-usuario/consulta-psicologica`)
6. Reemplaza el enlace en el archivo `index.html` (línea ~675):
   ```javascript
   calLink: "YOUR_CAL_USERNAME/consulta-psicologica",
   ```
   Por tu enlace real:
   ```javascript
   calLink: "isabellaprieto/consulta-psicologica",
   ```

**IMPORTANTE:** El enlace actual es un placeholder. Debes configurar tu propio Cal.com para que funcione.

### 2. Configuración del Formulario de Contacto

Para que el formulario de contacto funcione y envíe los mensajes a tu email `mdiaz00147@gmail.com`, sigue estos pasos:

### Opción 1: Web3Forms (Recomendado - Gratis)

1. Ve a [https://web3forms.com](https://web3forms.com)
2. Ingresa tu email: `mdiaz00147@gmail.com`
3. Haz clic en "Create Access Key"
4. Copia el Access Key que te proporcionen
5. Abre el archivo `index.html`
6. Busca la línea que dice: `access_key: 'YOUR_WEB3FORMS_ACCESS_KEY'` (aproximadamente línea 510)
7. Reemplaza `YOUR_WEB3FORMS_ACCESS_KEY` con tu Access Key
8. Guarda el archivo

### Opción 2: Formspree (Alternativa - Gratis)

Si prefieres usar Formspree:

1. Ve a [https://formspree.io](https://formspree.io)
2. Crea una cuenta gratuita
3. Crea un nuevo formulario
4. Reemplaza el código del formulario en `index.html` con el endpoint de Formspree

## Cómo Usar

1. Abre el archivo `index.html` en tu navegador web
2. Para producción, sube el archivo a tu servidor web o servicio de hosting (Netlify, Vercel, GitHub Pages, etc.)

## Estructura del Sitio

1. **Inicio** - Hero section con llamado a la acción
2. **Sobre Mí** - Información sobre la psicóloga y su experiencia
3. **Trastornos Alimentarios** - Información sobre los diferentes tipos de trastornos
4. **Tratamiento** - Enfoques terapéuticos utilizados
5. **¿Por Qué Elegirme?** - Ventajas y testimonios
6. **Contacto** - Formulario de contacto funcional

## Tecnologías Utilizadas

- HTML5
- Tailwind CSS (vía CDN)
- JavaScript vanilla
- Font Awesome para iconos
- Web3Forms API para envío de emails

## Personalización

Puedes personalizar fácilmente:
- Colores: Busca `teal-600` y reemplaza con tu color preferido de Tailwind
- Textos: Todos los textos están en español y pueden modificarse directamente en el HTML
- Imágenes: Actualmente usa iconos de Font Awesome, puedes reemplazarlos con fotos reales

## Contacto

Para cualquier duda sobre el sitio web, contacta a: mdiaz00147@gmail.com
