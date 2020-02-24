# Magento 1 Simple Lazy Loading
Questo Simple Lazy Loading per Magento 1 permette di rimandare il caricamento delle immagini quando il browser 
ha già renderizzato il documento.
In questo modo il PageSpeedInsight non vede più il problema del *defer offscreen images*

## Script JS
Inserire lo script in fondo al file app/code/design/frontend/rwd/*theme_name*/template/page/html/footer.phtml
```
<script>
jQuery( document ).ready(function() {
   [].forEach.call(document.querySelectorAll('img[data-src]'), function(img) {
         img.setAttribute('src', img.getAttribute('data-src'));
         img.onload = function() {
            img.removeAttribute('data-src');
         };
   });
});
</script>
```
## Tag img
Modificare i tag img sostituendo l'attributo *src* con *data-src* e la classe *lazyload*
```
<!-- Senza lazyload --!>
<img src="path-to-img" />

<!-- Con lazyload --!>
<img data-src="path-to-img" class="lazyload" />
``` 
