BULSHO-KAAB PHARMACY PWA starter assets

1. Put manifest.json, service-worker.js, icon-192.png and icon-512.png in the SAME folder as index.html.
2. In the <head> of index.html, add:
   <link rel="manifest" href="./manifest.json">
   <meta name="apple-mobile-web-app-capable" content="yes">
   <meta name="apple-mobile-web-app-status-bar-style" content="default">
3. Just before </body> in index.html, add:
   <script>
   if ("serviceWorker" in navigator) {
     window.addEventListener("load", () => {
       navigator.serviceWorker.register("./service-worker.js")
         .catch(error => console.error("Service worker registration failed:", error));
     });
   }
   </script>
4. Upload the whole folder to an HTTPS host (for example, Netlify). Service workers do not work reliably by opening index.html directly from phone storage.
5. Open the published HTTPS website in Chrome on Android, open the browser menu, and choose "Install app" or "Add to Home screen".

Keep your existing pic1.jpg ... pic8.jpg files in the same folder as index.html (unless your HTML uses another path).
