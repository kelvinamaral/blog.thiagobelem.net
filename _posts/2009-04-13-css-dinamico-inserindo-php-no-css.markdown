---
layout: post
title: 'CSS dinâmico: Inserindo PHP no CSS'
excerpt: Aprenda a misturar PHP e CSS e criar arquivos CSS dinâmicos que podem trazer
  informações de cores, fontes e caminhos de imagens direto do banco de dados ou de
  outra "fonte" de informações. ;)

date: '2009-04-13 19:42:10 -0300'
categories:
- PHP
- CSS
- Tutoriais
tags: []
---
Com esse recurso você vai poder transformar códigos de cores, caminho de imagens e qualquer parte de um arquivo CSS em variáveis e scripts PHP tornando o trabalho bem mais fácil.

Há duas formas de se alcançar esse objetivo:

A primeira, um pouco mais complicada, é fazendo o <em>parser</em> (interpretador) do PHP ler os arquivos .css antes de enviá-los para o visitante. Você pode fazê-lo da seguinte forma: crie/edite um arquivo chamado .htaccess dentro do root (raiz) do seu servidor e insira essa linha nele:


{% highlight text linenos %}
AddType application/x-httpd-php.css
{% endhighlight %}

Depois é só editar o seu arquivo .css e inserir códigos PHP da forma que bem entender... Lembrando apenas de que o retorno (via echo) deve ser a mesma formatação de um CSS... Exemplo:


{% highlight php linenos %}
<?php
$cor_fundo = '#CCCCFF';
$cor_texto = '#003333';
$imagem_link = '../img/link.jpg'
?>

body {
background: <?php echo $cor_fundo; ?>;
}

p.texto {
font-family: Verdana, Arial, serif;
color: <?php echo $cor_texto; ?>;
font-size: 12px;
}

a.especial {
text-decoration: none;
background: white url('<?php echo $imagem_link; ?>') 0px 0px no-repeat;
}
{% endhighlight %}

--

A outra forma eu considero um pouco mais simples: Você renomeará o seu arquivo <strong>.css</strong> trocando a extensão para <strong>.php</strong> e adicionará apenas uma linha logo no começo:


{% highlight php linenos %}
<?php
// Define que o arquivo terá a codificação de saída no formato CSS
header("Content-type: text/css");

$cor_fundo = '#CCCCFF';
$cor_texto = '#003333';
$imagem_link = '../img/link.jpg'
?>

body {
background: <?php echo $cor_fundo; ?>;
}

p.texto {
font-family: Verdana, Arial, serif;
color: <?php echo $cor_texto; ?>;
font-size: 12px;
}

a.especial {
text-decoration: none;
background: white url('<?php echo $imagem_link; ?>') 0px 0px no-repeat;
}
{% endhighlight %}

Não esqueça também de mudar o HTML que inclui a folha de estilos:


{% highlight text linenos %}
<link rel="stylesheet" href="estilo.php" type="text/css" />
{% endhighlight %}

--

Viram como é fácil? Com isso você vai poder usar sessões, fazer conexões a banco de dados, interpretar arquivos XML com informações e etc na hora de montar o CSS do seu site! Os exemplos de uso são inifinitos. E o melhor: não vai precisar ficar entupindo o HTML seu site de <strong>style=""</strong> pra todo lado.

Vale lembrar que esse recurso vai valer se você quiser inserir PHP dentro de qualquer tipo de arquivo que normalmente não seja interpretado pelo PHP (e por nenhum outro interpretador), como por exemplo: XML, JS, HTML ou uma extensão que você mesmo inventar.

Abraços e até a próxima! ;)

