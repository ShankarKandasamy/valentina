# Valentina — Website

Single-page static site for the Tech & Conversation Hour program.

The public site uses Valentina's name (matching the valentinapupic.com domain) but
intentionally omits phone and home address, routing all contact through the form so
replies come from a dedicated email rather than personal contact details.

## Run locally
Double-click `index.html`, or serve the folder:
`python -m http.server` then open http://localhost:8000

## Deploy
Push this folder to a GitHub repo and enable GitHub Pages (Settings -> Pages -> deploy from branch, root),
or drag the folder onto https://app.netlify.com/drop.

## Contact form
Submissions are forwarded to Valentina's Gmail via [Formspree](https://formspree.io)
(free tier: 50 submissions/month, no backend). The form endpoint lives in the
`action` of the `<form>` in `index.html`. Messages are delivered to the email on
the Formspree account that owns the form.

To change the destination: log in at https://formspree.io and update the form's
recipient, or create a new form and replace the `action` URL in `index.html`.

## Before going live
1. Add Valentina's photo as `assets/valentina.jpg` (see Task 3 placeholder).
2. Confirm the first submission has been verified in Formspree (Formspree emails a
   one-time confirmation link the first time the form is used).
