# Integración de Pagos - Guía Completa

## Cómo Funciona el Flujo de Pago

1. Usuario agenda una cita en el calendario (Calendly/Google Calendar)
2. El sistema detecta que la cita fue agendada
3. **Automáticamente** redirige al usuario a `pago.html`
4. El usuario selecciona su método de pago preferido
5. Completa el pago y confirma la consulta

## Opciones de Pago para Colombia

### Opción 1: Stripe (Recomendado - Internacional)

**Ventajas:**
- Acepta tarjetas de crédito/débito internacionales
- Proceso simple y seguro
- Buena integración con websites
- Comisión: ~3.4% + $0 COP por transacción

**Cómo Integrar:**

1. Crea una cuenta en [Stripe](https://stripe.com)
2. Verifica tu cuenta con tus datos bancarios
3. Crea un "Payment Link" o "Checkout Session"
4. En `pago.html`, reemplaza el botón "Pagar con Tarjeta":

```html
<!-- Reemplaza esta línea (aproximadamente línea 86): -->
<button onclick="alert('Integra aquí tu botón de pago')"
        class="w-full bg-teal-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-teal-700 transition">
    Pagar con Tarjeta
</button>

<!-- Por esto: -->
<a href="https://buy.stripe.com/TU_LINK_AQUI"
   class="block w-full bg-teal-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-teal-700 transition text-center">
    Pagar $150.000 COP
</a>
```

5. Tutorial completo: https://stripe.com/docs/payment-links

---

### Opción 2: Mercado Pago (Mejor para Colombia/LATAM)

**Ventajas:**
- Muy popular en América Latina
- Acepta múltiples métodos de pago locales
- PSE (débito desde bancos colombianos)
- Tarjetas de crédito/débito
- Comisión: ~3.99% + IVA

**Cómo Integrar:**

1. Crea cuenta en [Mercado Pago](https://www.mercadopago.com.co)
2. Ve a "Cobrar por internet" → "Botones de pago"
3. Crea un botón de pago de $150.000 COP
4. Copia el código del botón
5. En `pago.html`, reemplaza el botón de pago:

```html
<!-- Pega aquí el código de Mercado Pago -->
```

Tutorial: https://www.mercadopago.com.co/developers/es/docs/checkout-pro/landing

---

### Opción 3: PayPal

**Ventajas:**
- Reconocido mundialmente
- Fácil de integrar
- Comisión: ~3.99% + tarifa fija

**Cómo Integrar:**

1. Crea cuenta Business en [PayPal](https://www.paypal.com/co/business)
2. Ve a "Herramientas" → "Todos los productos de PayPal" → "Botones de Pago"
3. Crea un botón para $150.000 COP (o equivalente en USD)
4. Copia el código HTML
5. Pégalo en `pago.html` donde está el botón de pago

---

### Opción 4: Wompi (Colombia)

**Ventajas:**
- Específico para Colombia
- Acepta PSE, tarjetas, Nequi, etc.
- Integración sencilla
- Comisión competitiva

**Cómo Integrar:**

1. Crea cuenta en [Wompi](https://wompi.co)
2. Genera un enlace de pago
3. Intégralo en el botón de pago

---

### Opción 5: Pago Manual (Sin procesador)

Si prefieres no usar procesadores de pago (al menos inicialmente), puedes usar:

**Métodos incluidos en `pago.html`:**
- Transferencia bancaria
- Nequi
- Daviplata

**Pasos:**
1. Abre `pago.html`
2. Actualiza los datos bancarios (líneas 103-109):
   ```html
   <strong>Banco:</strong> Bancolombia<br>
   <strong>Tipo de Cuenta:</strong> Ahorros<br>
   <strong>Número de Cuenta:</strong> 1234-5678-9012<br>
   <strong>Titular:</strong> Isabella Prieto<br>
   <strong>Cédula:</strong> 12345678
   ```

3. Los pacientes te enviarán el comprobante por WhatsApp

---

## Integración Avanzada con Webhooks

Si quieres **automatizar** la confirmación de pago:

### Con Stripe/Mercado Pago/Wompi:

1. Configura un webhook en tu cuenta
2. Cuando el pago se complete, recibirás una notificación
3. Puedes enviar automáticamente:
   - Email de confirmación
   - Enlace de videollamada
   - Recordatorios

**Nota:** Esto requiere un backend (Node.js, PHP, etc.) o servicios como Zapier/Make.

---

## Recomendación para Empezar

### Opción Más Sencilla (Sin código):
1. **Mercado Pago** - Crea un link de pago
2. Reemplaza el botón en `pago.html`
3. ¡Listo!

### Opción Más Profesional:
1. **Stripe** + **Calendly webhooks**
2. Automación completa del flujo
3. Requiere configuración técnica

---

## Configurar el Precio

Para cambiar el precio de la consulta:

1. Abre `pago.html`
2. Busca la línea 77:
   ```html
   <p class="text-white text-4xl font-bold">$150.000 COP</p>
   ```
3. Cambia el monto según tu tarifa

---

## Eventos de Calendly Disponibles

El código actual escucha el evento:
- `calendly.event_scheduled` - Cuando se agenda una cita

Otros eventos disponibles:
- `calendly.event_type_viewed` - Usuario ve el tipo de evento
- `calendly.profile_page_viewed` - Usuario ve tu perfil
- `calendly.date_and_time_selected` - Usuario selecciona fecha/hora

Puedes personalizar qué hacer en cada evento editando el código en `index.html` (líneas ~654-682).

---

## Testing

Para probar el flujo:

1. Abre `index.html` en tu navegador
2. Haz clic en "Agenda tu Consulta"
3. Completa el formulario de Calendly
4. Deberías ser redirigido automáticamente a `pago.html`

**Nota:** Asegúrate de estar usando Calendly (no Google Calendar) para que funcionen los eventos.

---

## Preguntas Frecuentes

### ¿Google Calendar también dispara eventos?
No, Google Calendar embebido no dispara eventos JavaScript. Por eso recomendamos Calendly.

### ¿Puedo cobrar después de la sesión?
Sí, simplemente no redirijas a la página de pago. Elimina o comenta las líneas 671-679 en `index.html`.

### ¿Puedo tener precios diferentes?
Sí, puedes pasar información del tipo de consulta en la URL y mostrar diferentes precios en `pago.html`.

### ¿Necesito backend/servidor?
No para la integración básica con links de pago. Sí si quieres automatización avanzada.

---

## Soporte

Si necesitas ayuda con la integración, contáctame: mdiaz00147@gmail.com
