# Sitio de Isabella Prieto – Psicóloga Online

Sitio estático (HTML), sin servidor ni variables de entorno.

```
index.html     página principal (diseño nuevo + ventana modal de Cal.com)
pago.html      página de pago a la que pasa la paciente después de agendar
assets/        logo (horizontal y símbolo) y foto
robots.txt, sitemap.xml, vercel.json
```

## Cómo funciona
1. Todos los botones "Agenda tu consulta" abren una ventana modal con tu calendario de Cal.com
   (`isabella-prieto-1rte61/consulta-psicologica`, definido en `CAL_LINK` dentro de `index.html`).
2. Al confirmar la reserva, el sitio detecta el evento de Cal.com y lleva a la paciente a `pago.html?booking=...`.
3. En `pago.html` paga con tu enlace de Wompi (`https://checkout.wompi.co/l/mAYVc3`), por transferencia Bancolombia o por Nequi/Daviplata.

En Cal.com deja **vacío** "Redirect on booking" en el evento: la redirección la hace el sitio.

## Subir a GitHub
1. En tu repositorio crea una rama: `git checkout -b nuevo-diseno`.
2. Copia el contenido de esta carpeta en la raíz (reemplaza `index.html` y `pago.html`; conserva tus páginas `anorexia-nerviosa.html`, `bulimia-nerviosa.html` y `trastorno-por-atracon.html`).
3. `git add . && git commit -m "Nuevo diseño con modal de Cal.com y pago" && git push -u origin nuevo-diseno`

## Desplegar en Vercel
1. vercel.com > Add New > Project > importa el repositorio. Framework: **Other**; sin build command.
2. Vercel genera una URL de vista previa para la rama: pruébala (agenda, pago).
3. Si todo funciona, haz merge a `main` y se publica. Dominio: Settings > Domains.

## Después de publicar
- Verifica el sitio en Google Search Console y envía `https://www.psicologaisabellaprieto.com/sitemap.xml`.
