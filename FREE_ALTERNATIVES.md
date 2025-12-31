# Free Alternatives to Calendly Pro

Since Calendly's redirect feature requires a paid plan, here are your **free options**:

---

## Option 1: Cal.com (Best Free Alternative) ⭐⭐⭐⭐⭐

**Best for:** Getting all of Calendly's features for free

### Why Cal.com?
- ✅ **100% Free** with all essential features
- ✅ **Webhooks included** (free plan)
- ✅ **Better event handling** for redirects
- ✅ **Open source** - can self-host
- ✅ **Redirect on booking** (free feature!)
- ✅ **Very similar to Calendly**

### Setup Cal.com:

#### Step 1: Create Account
1. Go to [cal.com](https://cal.com)
2. Sign up for free (use Gmail)
3. Complete your profile

#### Step 2: Create Event Type
1. Click "Event Types" → "New Event Type"
2. Name: "Consulta Psicológica"
3. Duration: 60 minutes
4. Add your availability

#### Step 3: Configure Redirect (FREE!)
1. Go to your event type settings
2. **"Advanced" → "Success Redirect URL"**
3. Enter: Your payment page URL
4. Save

This is **FREE on Cal.com** (whereas Calendly charges for it!)

#### Step 4: Get Embed Code
1. Click "Embed" on your event type
2. Choose "Inline Embed"
3. Copy the code

#### Step 5: Replace in Your Site
In `index.html`:

```html
<!-- Replace Calendly div with Cal.com -->
<div
    data-cal-link="YOUR_USERNAME/consulta-psicologica"
    data-cal-config='{"theme":"light"}'
    style="width:100%;height:630px;overflow:scroll">
</div>
```

**Advantage:** Redirect is built-in and FREE!

---

## Option 2: Keep Manual Button (Simplest) ⭐⭐⭐⭐

**Best for:** Simplicity and avoiding dependencies

### What You Already Have:
- ✅ Working Calendly booking
- ✅ Manual "Continue to Payment" button
- ✅ 100% reliable
- ✅ No code needed

### User Flow:
1. User clicks "Agenda tu Consulta"
2. Books appointment in Calendly
3. Sees confirmation
4. Clicks green "Continuar al Pago" button
5. Goes to payment page

### Pros:
- Works now
- Zero dependencies
- Clear user experience
- Professional (many sites use this)

### Cons:
- Requires user to click button (not automatic)
- One extra step

**Reality:** This is how many professional booking sites work!

---

## Option 3: Build Custom Booking Form ⭐⭐⭐

**Best for:** Maximum control and no external dependencies

### How It Works:
Build a simple booking form that:
1. Collects: Name, email, date, time
2. Saves to your own system or Google Calendar
3. **Immediately redirects** to payment
4. Sends confirmation email

### Implementation:

Create a simple form:
```html
<form id="booking-form">
    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <input type="date" name="date" required>
    <input type="time" name="time" required>
    <button type="submit">Reservar</button>
</form>

<script>
document.getElementById('booking-form').addEventListener('submit', function(e) {
    e.preventDefault();

    // Save booking (to Google Calendar API, Firebase, or email)
    const formData = new FormData(this);

    // Redirect to payment immediately
    window.location.href = 'pago.html?name=' + formData.get('name');
});
</script>
```

### To Save to Google Calendar:
Use Google Calendar API:
1. Create Google Cloud project
2. Enable Calendar API
3. Get API credentials
4. Use JavaScript to create events

**Code example:**
```javascript
// After user submits form
gapi.client.calendar.events.insert({
    calendarId: 'primary',
    resource: {
        summary: 'Consulta Psicológica',
        start: { dateTime: selectedDate },
        end: { dateTime: endDate },
        attendees: [{ email: userEmail }]
    }
}).then(() => {
    // Redirect to payment
    window.location.href = 'pago.html';
});
```

### Pros:
- Full control
- Instant redirect
- No external dependencies
- Free forever

### Cons:
- More code to write
- Need to handle email notifications yourself
- Need to manage calendar conflicts

---

## Option 4: TidyCal (One-time Payment) ⭐⭐⭐

**Best for:** If you're willing to pay once (not subscription)

- **Price:** $29 one-time (lifetime access)
- All Calendly features
- Unlimited bookings
- Redirect feature included
- No monthly fees

Website: [tidycal.com](https://tidycal.com)

---

## Option 5: Koalendar (Free Tier) ⭐⭐⭐

**Best for:** Another free Calendly alternative

- Free plan available
- Redirect after booking
- Unlimited bookings
- Email notifications

Website: [koalendar.com](https://koalendar.com)

---

## Option 6: zcal (Free) ⭐⭐⭐

**Best for:** Minimalist free scheduling

- Completely free
- Open source
- Simple and fast
- Good for basic needs

Website: [zcal.co](https://zcal.co)

---

## Comparison Table:

| Feature | Cal.com | Manual Button | Custom Form | Calendly Free |
|---------|---------|---------------|-------------|---------------|
| **Cost** | Free | Free | Free | Free |
| **Auto Redirect** | ✅ Yes | ❌ Manual | ✅ Yes | ❌ No |
| **Setup Time** | 30 min | 0 min | 2-4 hours | Done |
| **Control** | Medium | Full | Full | Low |
| **Maintenance** | None | None | Medium | None |
| **Reliability** | High | 100% | High | Medium |

---

## My Recommendation:

### For You Right Now:

**Option A: Keep Manual Button + Calendly** (Best for now)
- Works perfectly
- Zero cost
- Zero setup
- Professional enough

**Option B: Switch to Cal.com** (Best long-term)
- Free redirect feature
- Better than Calendly free tier
- 30 minutes to set up
- More features

### Implementation Priority:

1. **Keep current setup** (manual button) - it works!
2. **Try Cal.com** when you have time
3. **Only build custom** if you need very specific features

---

## Step-by-Step: Switching to Cal.com

If you want to try Cal.com:

### 1. Create Account
```
1. Go to cal.com
2. Sign up with Gmail
3. Verify email
```

### 2. Create Event
```
1. Event Types → New
2. Name: Consulta Psicológica
3. Duration: 60 min
4. Set availability
5. Connect Google Calendar (optional)
```

### 3. Configure Redirect (FREE!)
```
1. Event Settings → Advanced
2. "Success Redirect URL": pago.html
3. Save
```

### 4. Update Your Site
```html
<!-- In index.html, replace Calendly with: -->

<!-- 1. Add Cal.com script to head -->
<script type="text/javascript" src="https://app.cal.com/embed/embed.js"></script>

<!-- 2. Replace inline widget -->
<div
    data-cal-link="YOUR_USERNAME/consulta"
    data-cal-config='{"theme":"light"}'
    style="width:100%;height:630px;">
</div>
```

### 5. Test
```
1. Open your site
2. Click "Agenda tu Consulta"
3. Book a test appointment
4. Should auto-redirect to pago.html ✅
```

---

## Why NOT Google Calendar?

**Google Calendar Appointment Scheduling:**
- ❌ No JavaScript events
- ❌ No redirect feature
- ❌ Same problem as Calendly inline widget
- ❌ Limited customization

It won't solve your problem.

---

## Final Verdict:

### Best Free Solution: **Cal.com**
- Has everything Calendly Pro has
- Free redirect feature
- Better than current setup
- 30 minutes to switch

### Simplest Solution: **Keep Manual Button**
- Already works
- Professional enough
- Zero risk
- Zero cost

**My advice:** Start with what you have (manual button), try Cal.com when you have 30 minutes free. It's a direct upgrade with no downsides.

---

## Need Help Switching?

If you want to try Cal.com, let me know and I'll:
1. Help you set it up
2. Update your site code
3. Test the auto-redirect

Just say the word!
