# Magento 1 Simple lazy loading
Questo simple Lazy Loading per Magento 1 permette di vedere

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
