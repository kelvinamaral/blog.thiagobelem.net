---
layout: post
title: PHP e MySQL para iniciantes – Consulta Avançada
excerpt: Continuação do tutorial que ensina iniciantes a trabalharem com PHP e MySQL.
  Nessa parte você aprenderá a fazer consultas avançadas utilizando PHP para acessar
  dados salvos no MySQL, unindo resultados de duas tabelas

date: '2010-07-25 17:48:35 -0300'
categories:
- PHP
- MySQL
- Tutoriais
tags:
- PHP
- MySQL
- Query
---
Hoje vamos continuar a nossa pequena seqüencia de tutoriais ensinando o básico do trabalho com PHP e MySQL.

Na parte anterior, ensinei a fazer uma consulta simples no MySQL, a consulta utilizada buscava as últimas 10 notícias da tabela de notícias e exibia-as seqüencialmente, da mais recente para a mais antiga.

Hoje vamos fazer uma consulta semelhante, mas iremos fazer o relacionamento entre as duas tabelas (<code>noticias</code> e <code>categorias</code>) para buscar apenas as notícias de uma categoria.

Começaremos o arquivo <code>consulta-avancada.php</code> da mesma forma que iniciamos o anterior, com um bloco de comentários que explica o arquivo e inclui o arquivo que cria a instância do MySQLi que será usada nesse novo arquivo.


{% highlight php linenos %}
<?php
/**
 * PHP e MySQL para iniciantes
 *
 * Arquivo com um exemplo de consulta avançada ao banco de dados MySQL
 *
 * PHP 5+, MySQL 4.1+
 *
 * @author Thiago Belem <contato@thiagobelem.net>
 * @link /mysql/php-e-mysql-para-iniciantes-consulta-simples/
 */

// Inclui o arquivo que faz a conexão ao banco de dados
require_once('includes/mysqli.php');

?>
{% endhighlight %}

Agora iremos definir uma variável contendo o nome da categoria que iremos usar para filtrar as notícias... O conteúdo dessa variável está "<em>hard coded</em>" no arquivo, mas poderia ser dinâmico e vir da uma variável <code>$_GET</code>, por exemplo.


{% highlight php linenos %}
// Iremos buscar apenas as notícias da categoria "Esportes"
$categoria = "Esportes"; // Essa variável poderia ter vindo, por exemplo, do $_GET
{% endhighlight %}

Feito isso, montaremos a consulta que será executada no banco de dados:


{% highlight php linenos %}
// Monta a consulta SQL para trazer as últimas 10 notícias ativas e que pertençam à categoria específica
$sql = "SELECT
      Noticia.id, Noticia.titulo, Noticia.descricao,
      Categoria.nome AS categoria
    FROM `noticias` AS Noticia
      INNER JOIN `categorias` AS Categoria
        ON Categoria.`id` = Noticia.`categoria_id`
    WHERE
      Noticia.`ativa` = 1
      AND
      Categoria.`nome` = '{$categoria}'
    ORDER BY Noticia.`cadastro` DESC
    LIMIT 10";
{% endhighlight %}

O interessante dessa consulta é que ela busca os registros da tabela <code>noticia</code> que possuam um relacionamento com os registros da tabela <code>categorias</code> e, o registro correspondente na tabela <code>categorias</code> deve possuir o valor da variável <code>$categoria</code> no campo <code>nome</code>.

Para quem não entendeu a explicação acima, vale a pena a leitura do meu artigo [Relacionamento de Tabelas no MySQL](/relacionamento-de-tabelas-no-mysql).

Continuando o script, rodamos a consulta e exibimos o resultado:


{% highlight php linenos %}
// Prepara a consulta OU mostra uma mensagem de erro
$resultado = $MySQLi->query($sql) OR trigger_error($MySQLi->error, E_USER_ERROR);

// Faz um loop, passando por todos os resultados encontrados
while ($noticia = $resultado->fetch_object()) {
  // Exibe a notícia dentro de um bloco HTML
  ?>

  <h2><?php echo $noticia->categoria; ?> - <?php echo $noticia->titulo; ?></h2>
  <?php echo $noticia->descricao; ?>

  [Leia mais &raquo;](noticia.php?id=<?php echo $noticia->id; ?>)


  <?php
} // while ($noticia = $resultado->fetch_object())
{% endhighlight %}

E, para finalizar, exibimos o total de resultados encontrados e limpamos a consulta da memória do PHP:


{% highlight php linenos %}
// Exibe o total de registros encontrados
echo "Registros encontrados: {$resultado->num_rows}
";

// Libera o resultado para liberar memória
$resultado->free();
{% endhighlight %}

E vocês acabaram de ver um exemplo de consulta complexa usando MySQLi! :)

Faça o download dos arquivos desse tutorial aqui: [PHP-e-MySQL-Consulta-Avançada.zip](/arquivos/2010/07/PHP-e-MySQL-Consulta-Avançada.zip)

Abraços e até a próxima!

