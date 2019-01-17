# SEO

````HTML
<title> Dâmocles Gil Marçal</title>
<meta name="description" content="Dâmocles Gil - Porfólio digital de um desenvolvedor web">
<meta name="author" content="damoclesgil" />
<meta name="url" content="https://damoclesgil.github.io/">
<meta name="copyright" content="company name">
<meta name="robots" content="index,follow">
````

#### ROBOTS

* nofollow: indica que o ::bot:: não deve seguir para nenhum link a partir da página em que ele estiver. Seu uso é indicado para quando uma página possui link para páginas que não têm relação com seu conteúdo principal. Veremos mais sobre isso ainda no livro, ao falarmos sobre ::Link Building::;
* noarchive: impossibilita que uma cópia cacheada desse site seja devolvida como resultado;
* nosnippet: diz que não deve ser mostrada uma descrição para o site no resultado da busca;
* noodp: desabilita o uso do ::Open Directory Project:: como alternativa para escolher o conteúdo a ser usado para exibir a descrição do site no resultado da busca;
* none: equivalente ao nodeindex mais nofollow. 

#### Utilizar Apenas um H1

````HTML
<h1 class="destaque"> Introdução...</h1>
````

#### robots.txt

````txt
# Coment
User-Agent: *
Disallow: /_
Disallow: /admin/
Sitemap: https://www.actuar.com.br/sitemap.xml

# Google adsbot ignores robots.txt unless specifically named!
User-agent: adsbot-google
Disallow: /checkout

User-agent: Nutch
Disallow: /

User-agent: MJ12bot
Crawl-Delay: 10

User-agent: Pinterest
Crawl-delay: 1
````

### sitemap xml

````xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset
      xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9">

  <url>
   <loc>https://damoclesgil.github.io/</loc>
    <lastmod>2017-10-12</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1</priority>
  </url>
</urlset>
````

#### Utilizar Alts

````HTML
<img src="imagens/decoracao-banheiro-pequeno-verde.png" alt="Decoração de banheiro pequeno com tons de verde" />
````

#### Others

````txt
Regras dos 3 Cliques 
Padrão de URL underline ou hiffen nunca os dois 
::Mobile-friendly:: 
Criar uma página 404 bonita para linkar de volta ou buscar 
Redirecionamento no servidor 
Páginas que não pode ser indexada: 404, login, cadastro 
````
