Tapasya arT — Website

A single-file, production-ready website for Tapasya arT, a handcrafted art studio in Amravati, Maharashtra run by Atul Undarkar and Prashant Hirdekar. The studio creates wall murals, name plates, stone carvings, canvas paintings, decorative frames, religious murals, door murals, CNC-cut designs, and ceiling murals.

The site is built as one self-contained index.html — no build step, no server, no external dependencies at runtime. Open it in a browser and everything works, including the embedded background music and the AI sales assistant.

Live features at a glance: browsable product collections per service with an owner-only upload panel, a 360° product viewer with zoom, a shopping cart, a service-booking form, a login/register flow with Google & Apple sign-in buttons, an AI chatbot that qualifies leads and hands off to WhatsApp, a Google Maps integration, checkout with Google Pay / PayPal / WhatsApp-negotiate options, and an ambient background-music player with three original composed tracks.

✨ Features
Storefront & Content
Hero, About, Portfolio gallery (filterable), Testimonials, Contact — a full one-page marketing site with an earthy, hand-painted visual theme (custom cursor, scroll reveals, 3D-tilt cards)
Services grid ("Crafted with Devotion") — all 11 services Tapasya arT offers, each opening into its own product collection
Product collections — every service (Wall Mural, Name Plates, Stone Carving, Canvas Painting, Decorative Frames, God Mural, Door Mural, CNC Cutting, Metal Name Plate, Ceiling Mural, Acrylic Name Plate) has its own gallery of items customers can browse and buy
Product Detail view — click any item for a large view with 360° drag-to-rotate, zoom in/out, full description, specs, star ratings, and a review list
Customer photo reviews — 5-star rating picker, written review, and optional photo upload per product
Shopping cart — add to cart from any collection, running total, slide-out cart drawer
Owner Tools
Owner product upload panel — add new products (name, price, description, photo upload, badge, color theme) to any collection, right from the storefront
6-digit passcode protection (120308) — required before any product is saved, with a lockout after 5 wrong attempts, so only the owner can publish products
Sales & Booking
Service booking form — customers submit project requirements (service, city, date, message); auto-opens a pre-filled WhatsApp message to the owner
Checkout / payment options — Google Pay (UPI QR, ready to activate with a real UPI ID), PayPal (international orders, contact-based), and a "Negotiate on WhatsApp" button that sends the full cart contents
AI Customer & Sales Agent — a full rule-based chatbot (bottom-right, 🤖) that:
Greets visitors and offers to explore services, get a quote, discuss a project, or contact the team
Asks the right qualifying questions per service (location, size, indoor/outdoor, design, reference image, etc.) one at a time, not all at once
Answers FAQs (installation, materials, timelines, delivery, custom designs, etc.) from a fixed knowledge base — never invents prices
Detects Hinglish and common phrasing ("kitna", "karwana hai")
Recognizes when to hand off to a human (urgent requests, complaints, explicit ask)
Captures qualified leads and notifies the owner via WhatsApp + email, exactly like the booking form
Built with a clean provider-abstraction (CB namespace) so a real LLM API can be dropped in later without restructuring
Accounts
Login / Register modal with a manual form, plus Google Sign-In and Apple Sign-In buttons (collect the same details and notify the owner; true one-tap OAuth requires the owner's own Google Cloud / Apple Developer credentials — see Configuration)
Every registration notifies the owner via WhatsApp and (once configured) email
Location & Contact
Google Maps integration — floating map button and an embedded live map pinned to the studio's exact coordinates, plus a "Get Directions" button
Full office address, phone numbers, and business hours throughout the site
Ambience
Background music player (bottom-left, 🎵) with four modes:
🎼 Melody — a gentle looping folk tune on an earthy pentatonic scale (Sa Re Ga Pa Dha)
🎻 Instrumental — a warm, slow ambient pad/drone
🪕 Traditional — brighter sitar-style plucks with a soft rhythmic pulse
🔇 Silent (default — nothing plays until the visitor chooses)
All three tracks are original compositions, synthesized offline in Python (numpy) and embedded directly in the HTML as base64 audio — no copyrighted samples, no external files to host or license, works even if the file is opened offline
🛠️ Tech Stack
Plain HTML, CSS, and vanilla JavaScript — zero frameworks, zero build tools
Google Fonts: Cinzel Decorative, Cormorant Garamond, Noto Sans Devanagari, Caveat
Web APIs used: IntersectionObserver (scroll reveals), HTML5 <audio>, FileReader (image uploads), CSS 3D transforms (product rotation)
Audio synthesis: Python + numpy + scipy (offline, one-time — see audio/), converted to MP3 with ffmpeg
No backend, no database, no npm install — the entire storefront, cart, reviews, and chatbot state live in-memory in the browser (resets on page reload; see Limitations below)
📁 Project Structure
tapasya-art/
├── index.html          # The entire website (HTML + CSS + JS, single file)
├── audio/
│   ├── melody.mp3        # Standalone copies of the 3 composed tracks
│   ├── instrumental.mp3  # (also embedded as base64 inside index.html)
│   └── traditional.mp3
├── DEPLOY.md            # Step-by-step GitHub Pages deployment guide
└── README.md            # This file
🚀 Getting Started
Preview locally

Just open index.html in any modern browser — double-click it, or:

bash
open index.html        # macOS
start index.html        # Windows
xdg-open index.html     # Linux
Deploy it live

See DEPLOY.md for full step-by-step instructions to publish this on GitHub Pages (free), including a no-terminal drag-and-drop option.

⚙️ Configuration (before you go live)

A handful of settings are placeholders until you provide real values. Open index.html, search for these constants near the top of the <script> section, and fill them in:

Constant	Purpose	Current value
OWNER_PHONE	WhatsApp number that receives booking/registration/lead notifications	919766654460 (set)
OWNER_EMAIL	Email address that receives registration/lead notifications (via mailto:)	empty — add yours
OWNER_UPI_ID	UPI ID used to generate a live, scannable Google Pay QR code at checkout	empty — add yours
OWNER_CODE	6-digit passcode required to publish new products	120308

Google/Apple Sign-In: the buttons work today (they collect name + email and notify the owner), but true one-tap OAuth sign-in requires the site owner to register the app with Google Cloud Console (Client ID) and the Apple Developer portal (Services ID) — only an account holder can create these. Send those IDs over once you have them to upgrade to real one-tap sign-in.

⚠️ Known Limitations & What's Simulated

This is a static site with no backend, by design (fast, free to host, nothing to maintain). A few things follow from that:

Cart, reviews, and owner-added products reset on page reload — there's no database. For persistence across visits/devices, this would need a backend (e.g. Firebase, Supabase, or a custom API).
"Sending" a WhatsApp message or email requires one tap from the customer — browsers can't silently send messages on a user's behalf without a paid API (WhatsApp Business API, Twilio, EmailJS, etc.). The site opens a pre-filled message; the customer taps send.
The AI chatbot is rule-based, not an LLM — no API key is configured. It's built with a clean abstraction (see CB in index.html) specifically so a real LLM (OpenAI/Anthropic/Gemini) can be wired in later.
Google Pay QR and PayPal are payment links, not a payment gateway — there's no order processing, refunds, or transaction records. For that, integrate a real gateway (Razorpay, Stripe, etc.).

None of this blocks the site from working well today — it just means "real backend" is the natural next step if the business outgrows a static site.

🎨 Credits
Design & development: built with Claude (Anthropic)
Original ambient music: composed and synthesized specifically for this project — free to use, modify, or replace
Fonts: Google Fonts (Cinzel Decorative, Cormorant Garamond, Noto Sans Devanagari, Caveat)
📄 License

This project belongs to Tapasya arT. Use, modify, and deploy it freely for the business.
