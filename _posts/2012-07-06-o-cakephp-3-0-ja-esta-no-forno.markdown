---
layout: post
title: O CakePHP 3.0 já está no forno!

date: '2012-07-06 20:14:29 -0300'
categories:
- CakePHP
- Artigos
tags:
- CakePHP
- cakephp 3.0
---
Desde sua criação, mais de <strong>7 anos atrás</strong>, o [CakePHP](http://cakephp.org) criou vida própria. Seu principal objetivo sempre foi o de capacitar os desenvolvedores com<strong> ferramentas e bibliotecas que são fáceis usar e de aprender</strong>, (...). Tivemos vários grandes lançamentos ao longo destes anos e uma comunidade cada vez maior. Sendo <strong>um dos frameworks mais populares</strong> lá fora, e provavelmente o primeiro (!), conseguido também uma série de críticas da comunidade de desenvolvedores em geral. Nós aceitamos e aprendemos com nossos erros para continuar a construir o melhor framework de PHP que existe.

CakePHP é conhecido por ter um ritmo muito lento de adoção coisas novas e isso tem servido muito bem para sua comunidade. Quando estávamos fazendo a versão 2.0, decidimos manter suporte à  versão 5.2 do PHP por vários motivos e - por causa disso - não pudemos inovar tanto quanto queríamos, mas essa foi uma excelente escolha, dado o ambiente geral sobre as soluções de hospedagem e de adoção geral do PHP 5.3.

Um olhar para o passado lembrou-nos que éramos grandes inovadores em PHP, trazendo recursos para desenvolvedores que poucos sonharam possível fazer com esta linguagem. Agora, é hora de olhar para frente, no futuro, e decidir em ficar na nossa zona de conforto ou <strong>ter de volta nossa posição de liderança como inovadores</strong>.

Por isso, é com grande entusiasmo que anunciamos que estamos colocando investindo nossos esforços em trazer-lhe a <strong>próxima versão do CakePHP</strong>. Versão 3.0 vai aproveitar os [novos recursos do PHP 5.4](/php-5-4-novas-funcionalidades) e incluirá uma mudança importante em nossos <strong>Models</strong> e sistema de banco de dados. CakePHP 3.0 <strong>não estará pronto menos de 6 ou 8 meses</strong> e nós consideramos que, dado o aumento soluções baratas de hospedagem cloud e lançamento de novas versões de sistemas operacionais, não há melhor momento para "saltar sobre" a versão mais atual estável do PHP.

Como você já deve saber, PHP 5.4 oferece características impressionantes que introduzem novos conceitos úteis e soluções interessantes para problemas antigos. <strong>Closures</strong>, [](/php-5-4-traits), <strong>suporte multibyte</strong> são de grande utilidade para <strong>implementações adequadas de funcionalidades avançadas</strong> de frameworks, que temos em mente há muito tempo. Também há a nova sintaxe, que torna o PHP mais agradável para escrever tanto para aplicações de pequenas quanto complexas, sem perder a sempre bem-vinda melhoria de performance e desempenho.

Temos um recente porém bem definido <strong>roadmap</strong> para o que queremos realizar na próxima versão e <strong>você está convidado a contribuir e sugerir</strong> o que vem a seguir:

<ul>
<li>Abandonar o suporte ao <strong>PHP 5.2.x</strong>, ficando com o [PHP 5.4](/php-5-4-novas-funcionalidades) + apenas</li>
<li>Adicionar <strong>namespaces</strong> apropriados para todas as classes. Isto tornará mais fácil a reutilização de classes fora do CakePHP, usar bibliotecas externas e, finalmente, sem chances de colisões entre as classes da aplicação e do core</li>
<li>Uso de [traits](/php-5-4-traits) onde for possível</li>
<li>Melhorar o processo de inicialização para permitir um maior controle do desenvolvedor e melhor desempenho</li>
<li>Mudanças na camada <strong>Model</strong>:
<ul>
<li>Models retornando objetos a partir das consultas</li>
<li>Paradiga de Datamapper</li>
<li>API Rica de consulta (query)</li>
<li>Suporte para qualquer tipo de banco de dados</li>
<li>Suporte a drivers de banco de dados, tanto os nativos quanto via PDO</li>
</ul>
</li>
<li>Melhoras no mecanismo de rotas (Router):
<ul>
<li>Torná-lo mais rápido</li>
<li>Remover parâmetros nomeados</li>
<li>Adicionar suporte para rotas nomeadas</li>
<li>Rotas com prefixos inteligentes</li>
<li>Sintaxe encurtada de URLs</li>
</ul>
</li>
</ul>
Como você pode imaginar a maior parte do tempo será gasta em reescrever a camada de modelo, mas também será um dos mais poderosos recursos que o <strong>CakePHP 3.0</strong> irá ter. Sua nova arquitetura baseada nas funcionalidades do <strong>PHP 5.4</strong> irá oferecer um conjunto mais fácil e mais poderoso de ferramentas para construir aplicações web rapidamente.

(...)

<strong></strong>Estamos sempre à procura de pessoas diferentes que têm uma visão sobre o desenvolvimento de software, você está interessado em ajudar? Não há melhor momento para iniciar o envio de correções e se tornar um membro da equipe principal!

Tradução livre do [artigo original](http://bakery.cakephp.org/articles/lorenzo/2012/07/06/3_0_a_peek_into_cakephps_future).

