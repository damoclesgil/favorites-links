# Dicas de Perfomance

- [x] Minificar
- [x] Gzip
- [x] Otimizar Imagens
- [x] Concatenar CSS/JS
- [x] Sprites
- [x] Cache
- [x] Inline de recursos
- [x] Paralelização de requests;
- [x] Diminuir o número de requisições
- [x] Diminuir o volume de dados nas requisições
- [x] Otimizar a renderização no navegador

## Otimizações WEB

- Diminuir requests > Junstar css e JS/Sprites, Inline de Recursos
- Diminuir tráfego > Gzip, minificação e domínios sem cookies
- Paralelizar requests > Múltiplos Hostnames, CDNs

### Novo HTTP/2

- gzip
- tls = binario e seguro.
- obrigatorio certificado, mas ainda pode usar sem certificado.
- hpack
- header binário

## Setar um time para rodar depois de um tempo

```js
setTimeout(function(){
    console.log('script-carregado.js')
    // ... miolo da funcao...
}, 2000);
```

## Adiar Video para carregar depois de um time

```js
setTimeout(function(){
 var iframe = '<iframe class="video-resposivo" src="https://..."></iframe>';
    document.querySelector('.video-responsivo').innerHTML = iframe;
}, 1500);
```

### Adiar Imagem de acordo com o scrool com o Trottle

```html
<img data-src="" class="image">
```

```js
 var jarodei = false;

    window.onscroll = function () {

        // throttle
        if (jarodei) return;
        jarodei = true;
        setTimeout(function () {
            jarodei = false;
        }, 200);

        console.log('scroll');

        // código em si
        var imgs = document.querySelectorAll('img[data-src]:not([src])');
        for (var i = 0; i < imgs.length; i++) {
            if (imgs[i].getBoundingClientRect().top < window.innerHeight + 200) {
                imgs[i].src = imgs[i].getAttribute('data-src');
            }
        }

    };
```

```js
(function(){

    // controle do throttle
    var jarodei = false;

    // pega todas as imagens num array e pre-calcula seu topo
    var imgs = document.querySelectorAll('img[data-src]:not([src])');
    var cache = [];
    for (var i = 0; i < imgs.length; i++) {
        cache.push({
            topo: imgs[i].getBoundingClientRect().top + pageYOffset,
            elemento: imgs[i]
        });
    }

    // cache da altura da janela
    var alturaJanela = window.innerHeight;

    window.addEventListener('scroll', function scrollListener() {

        // throttle
        if (jarodei) return;
        jarodei = true;
        setTimeout(function () { 
            jarodei = false; 
        }, 100);

        // meu while não toca no DOM, observa apenas variáveis cacheadas e o pageYOffset.
        // só manipulo o DOM quando preciso realmente mexer na imagem.
        while (cache.length && cache[0].topo < pageYOffset + alturaJanela + 200) {
            var img = cache.shift().elemento;
            img.src = img.getAttribute('data-src');
        }

        // removo o onscroll se não precisar mais dele
        if (cache.length == 0) {
            window.removeEventListener('scroll', scrollListener);
        }

    });

})();
```

### Nginx Confs

```json
server {
  listen 3030;
  root /Users/alura/performance-web/dist;

  gzip on;
  gzip_types text/css application/javascript image/svg+xml;

  location /assets {
    expires 1y;
    add_header Cache-Control public;
  }
}
```
