# Cal.com Setup Guide - Complete Instructions

## Why Cal.com?

✅ **FREE redirect after booking** (Calendly charges $12/month for this!)
✅ **FREE webhooks**
✅ **Unlimited bookings**
✅ **Better event handling**
✅ **Open source**
✅ **All features you need**

---

## Step 1: Create Cal.com Account (5 minutes)

1. Go to **https://cal.com**
2. Click **"Get Started Free"**
3. Sign up with:
   - **Gmail** (recommended - easier integration)
   - Or email + password
4. Verify your email
5. Complete your profile:
   - Name: Isabella Prieto
   - Username: Choose a username (e.g., `isabellaprieto` or `isabellaprietopsic`)
   - Time zone: (GMT-5:00) Bogotá, Lima, Quito

---

## Step 2: Connect Your Calendar (Optional but Recommended)

1. In Cal.com dashboard, go to **"Apps"** or **"Integrations"**
2. Find **"Google Calendar"**
3. Click **"Install"** or **"Connect"**
4. Authorize Cal.com to access your Google Calendar

**Why connect?**
- Prevents double-booking
- Auto-adds bookings to your calendar
- Checks your availability in real-time

---

## Step 3: Create Your Event Type

### 3.1 Basic Settings

1. Click **"Event Types"** → **"+ New Event Type"**
2. Select **"One-on-One"**
3. Fill in the details:

   **Event Name:**
   ```
   Consulta Psicológica
   ```

   **URL Slug:** (will be auto-generated from name)
   ```
   consulta-psicologica
   ```
   Your booking link will be: `cal.com/YOUR_USERNAME/consulta-psicologica`

   **Duration:**
   ```
   60 minutes
   ```

   **Description:**
   ```
   Sesión de terapia psicológica individual con Isabella Prieto.

   📋 Antes de la sesión:
   - Encuentra un lugar tranquilo y privado
   - Verifica tu conexión a internet
   - Ten papel y lápiz si lo deseas

   💳 Después de agendar:
   Serás redirigida automáticamente al pago.

   📧 Recibirás:
   - Confirmación por email
   - Enlace de videollamada
   - Recordatorios antes de la sesión

   ¿Preguntas? WhatsApp: +57 310 544 1488
   ```

### 3.2 Location Settings

1. In your event type, go to **"Where"** or **"Location"**
2. Choose one:

   **Option A: Google Meet** (Recommended - Free)
   - Select **"Google Meet"**
   - Cal.com creates unique link for each booking

   **Option B: Zoom**
   - Select **"Zoom"**
   - Connect your Zoom account

   **Option C: Custom Link**
   - Select **"Link"** or **"Custom"**
   - Add your permanent video call link

---

## Step 4: Configure Availability

1. In your event type, go to **"Availability"** or **"When"**
2. Set your working hours:

   **Example Schedule:**
   ```
   Monday:    9:00 AM - 6:00 PM
   Tuesday:   9:00 AM - 6:00 PM
   Wednesday: 9:00 AM - 6:00 PM
   Thursday:  9:00 AM - 6:00 PM
   Friday:    9:00 AM - 6:00 PM
   Saturday:  Unavailable
   Sunday:    Unavailable
   ```

3. **Additional Settings:**

   **Minimum Notice:**
   ```
   24 hours
   ```
   (Prevents last-minute bookings)

   **Buffer Time:**
   ```
   Before event: 15 minutes
   After event: 15 minutes
   ```
   (Gives you breathing room between sessions)

   **Future Booking:**
   ```
   60 days
   ```
   (How far ahead people can book)

---

## Step 5: Set Up AUTO-REDIRECT (Most Important!) 🎯

This is the **KEY FEATURE** that's FREE on Cal.com but costs $12/month on Calendly!

1. In your event type settings, go to **"Advanced"** tab
2. Find **"Success Redirect URL"** or **"Redirect on Booking"**
3. Enter your payment page URL:

   **For local testing:**
   ```
   file:///Users/mariodiaz/Development/psicologa-isa/pago.html
   ```

   **For production (when published online):**
   ```
   https://yourwebsite.com/pago.html
   ```

4. **Save** the event type

**Result:** When someone books, they'll be **automatically redirected** to your payment page! ✅

---

## Step 6: Configure Email Notifications

1. In event type settings, go to **"Notifications"** or **"Workflows"**
2. Enable:

   ✅ **Email Confirmation to Attendee**
   - Sends confirmation with booking details
   - Includes video call link

   ✅ **Email Confirmation to You**
   - Notifies you when someone books

   ✅ **Reminder Emails:**
   - 24 hours before appointment
   - 1 hour before appointment (optional)

---

## Step 7: Customize Questions (Optional)

Add custom questions to collect more info:

1. Go to event type → **"Questions"** or **"Booking Questions"**
2. Default questions (already included):
   - ✅ Name
   - ✅ Email

3. **Add additional questions:**

   **Phone Number:**
   - Type: Phone
   - Label: "Número de teléfono/WhatsApp"
   - Required: Yes

   **Reason for Consultation:**
   - Type: Long text
   - Label: "¿Cuál es el motivo de tu consulta?"
   - Required: No (keep it optional to avoid overwhelming)

   **First Time in Therapy:**
   - Type: Yes/No
   - Label: "¿Es tu primera vez en terapia psicológica?"
   - Required: No

---

## Step 8: Get Your Booking Link

After saving everything:

1. Go to your event type
2. Click **"Copy Link"** or find your booking URL
3. It will look like:
   ```
   https://cal.com/YOUR_USERNAME/consulta-psicologica
   ```

**Example:**
```
https://cal.com/isabellaprieto/consulta-psicologica
```

---

## Step 9: Update Your Website

Now integrate Cal.com into your site:

1. Open `index.html`
2. Find line **~675** that says:
   ```javascript
   calLink: "YOUR_CAL_USERNAME/consulta-psicologica",
   ```

3. **Replace** `YOUR_CAL_USERNAME` with your actual Cal.com username

   **Example:**
   ```javascript
   calLink: "isabellaprieto/consulta-psicologica",
   ```

4. **Save** the file

---

## Step 10: Test Everything!

1. Open `index.html` in your browser
2. Click **"Agenda tu Consulta"**
3. The Cal.com booking widget should appear
4. Fill out the form and book a test appointment
5. **Watch the console** (F12) for debug messages
6. You should see:
   ```
   ✅ Cal.com event detected
   🎉 BOOKING SUCCESSFUL! Redirecting to payment...
   ```
7. Should **automatically redirect** to `pago.html` ✅

---

## Troubleshooting

### Problem: Widget doesn't appear
**Solution:**
- Check that you replaced `YOUR_CAL_USERNAME` with your real username
- Open browser console (F12) and look for errors
- Make sure you're connected to the internet

### Problem: No auto-redirect after booking
**Solutions:**
1. **Check if you set up the Success Redirect URL:**
   - Cal.com → Event Type → Advanced → Success Redirect URL
   - Must be set for auto-redirect to work

2. **Check browser console:**
   - Open console (F12)
   - Look for "🎉 BOOKING SUCCESSFUL!" message
   - If you see it but no redirect, check the URL format

3. **JavaScript events as backup:**
   - The code also listens for Cal.com events
   - Should redirect even if redirect URL isn't set

### Problem: Bookings not showing in Google Calendar
**Solution:**
- Make sure you connected Google Calendar in Cal.com
- Go to Cal.com → Apps → Google Calendar → Reinstall if needed

---

## Cal.com vs Calendly Comparison

| Feature | Cal.com FREE | Calendly FREE | Calendly PRO ($12/mo) |
|---------|--------------|---------------|----------------------|
| Auto-redirect after booking | ✅ **YES** | ❌ No | ✅ Yes |
| Webhooks | ✅ **YES** | ❌ No | ✅ Yes |
| Unlimited bookings | ✅ Yes | ✅ Yes | ✅ Yes |
| Calendar integrations | ✅ Yes | ✅ Yes | ✅ Yes |
| Custom branding | ✅ Yes | ❌ No | ✅ Yes |
| Video call integration | ✅ Yes | ✅ Yes | ✅ Yes |
| Email reminders | ✅ Yes | ✅ Yes | ✅ Yes |

**Cal.com gives you everything for FREE that Calendly charges for!** 🎉

---

## Advanced: Using Webhooks (Optional)

If you want even more automation:

1. Go to Cal.com → **Settings** → **Developer** → **Webhooks**
2. Click **"New Webhook"**
3. Select trigger: **"Booking Created"**
4. Enter webhook URL (requires a backend server)
5. Cal.com will POST to your server when bookings happen

**Use cases:**
- Send custom emails
- Add to your own database
- Integrate with payment processors
- Create Slack notifications

**Requirements:**
- Backend server (Node.js, Python, PHP, etc.)
- Public URL for webhook endpoint

---

## Pro Tips

### Tip 1: Customize Confirmation Page
While the auto-redirect will take users to payment, Cal.com also shows a confirmation page. You can customize it:
- Cal.com → Event Type → Advanced → Confirmation Page Message

### Tip 2: Use Routing Forms (Advanced)
If you want to offer different consultation types:
1. Create multiple event types (30 min intro, 60 min session, etc.)
2. Use Cal.com's routing forms to help users choose
3. Different prices for different session types

### Tip 3: Block Out Personal Time
To prevent bookings during personal appointments:
- Keep your Google Calendar connected
- Mark personal events as "Busy"
- Cal.com won't allow bookings during those times

---

## Need Help?

If you run into issues:
1. Check the troubleshooting section above
2. Open browser console (F12) to see debug messages
3. Contact me: mdiaz00147@gmail.com

**Include:**
- Screenshot of console
- Your Cal.com username
- What step you're stuck on

---

## Next Steps After Setup

Once Cal.com is working:

1. ✅ **Delete old Calendly account** (if you want)
2. ✅ **Test the full booking → payment flow**
3. ✅ **Set up payment integration** (see PAYMENT_INTEGRATION.md)
4. ✅ **Go live!**

**Congratulations!** You now have a professional booking system with **free** auto-redirect to payment! 🎉
