---
layout: post
title: Trabalhando com Sessões no CakePHP
excerpt: 'Aprenda a inserir, recuperar e deletar valores da sessão usando os métodos
  do component Session do CakePHP, e o melhor: tudo orientado a objetos! :)'

date: '2009-07-31 00:33:58 -0300'
categories:
- PHP
- CakePHP
- Tutoriais
- Segurança
tags:
- PHP
- Sessions
- CakePHP
- Sessões
---
Fala pessoal,

Pretendo falar um pouquinho mais sobre o <strong>CakePHP</strong> nós próximos dias... Espero que alguém leia e goste! Não vou começar com tutoriais básicos para iniciar com o Cake mas já vou falando de algumas coisas simples que todo mundo vai ler um dia. :)

Hoje vou mostrar como é uso dos <strong>métodos</strong> do component [Session](http://book.cakephp.org/view/173/Sessions) que te ajuda a manipular os valores salvos na sessão de forma mais segura e orientada à objetos.

<h3>Pegando todos os valores da sessão</h3>
Normalmente, fora do Cake, você trabalharia com a variável global <strong style="background: gray; color: lime">$_SESSION</strong>... Agora, com o Cake, você nem precisa se lembrar do nome dela... Veja como pegamos todos os valores da sessão de dentro de um <strong>controller</strong>:


{% highlight php linenos %}
// Exibe todos os valores da sessão
print_r($this->Session->read());
{% endhighlight %}

Se você não criou nem alterou algum valor da sessão o que será exibido vais e paracer com isso:
{% highlight php linenos %}
Array ( [Config] => Array ( [rand] => 262820453 [time] => 1161876896 [userAgent] => c7f575cbe5a4b7ad0efb748d54124611 ) )
{% endhighlight %}



<h3>Escrevendo valores na sessão</h3>
Agora é hora de fazer o component Session trabalhar pra gente e escrever alguns valores na sessão... Vamos salvar dois valores:


{% highlight php linenos %}
// Salva dois valores na sessão
$this->Session->write('usuarioID', 12);
$this->Session->write('usuarioNome', 'Thiago Belem');
{% endhighlight %}
Viram que simples?



<h3>Lendo/recuperando valores da sessão</h3>
Depois de criar valores na sessão você óbviamente vai quere ler esses valores em algum lugar do controller ou da view... No controller faríamos assim:


{% highlight php linenos %}
// Recupera o valor da sessão
$usuario = $this->Session->read('usuarioID');
{% endhighlight %}
Caso você queira pegar um valor da sessão <strong>dentro da view</strong>, é mais ou menos assim:
{% highlight php linenos %}
Seja bem vindo, <?php echo $session->read('usuarioNome'); ?>!
{% endhighlight %}
Viram que simples? [2]



<h3>Destruindo a sessão</h3>
Quando o seu usuário fizer logout você provavelmente vai precisar/querer destruir a sessão dele para ele não continuar "dentro" do sistema... Então é só verificar se é uma sessão valida e o resto você manda pro espaço:


{% highlight php linenos %}
// Destruindo a sessão
if ($this->Session->valid()) {
  $this->Session->destroy(); // Destrói
  $this->redirect('/');// Redireciona o usuário
}
{% endhighlight %}
Viram que simples? [3] :D

Existem outras formas e métodos no session component mas essas que eu dei de exemplo são, sem dúvida, as mais usadas e as necessárias para você fazer um bom sistema...

Espero que tenham gostado! :)

