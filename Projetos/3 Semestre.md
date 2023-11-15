# Projeto 3: 2º Semestre de 2022 

<img src="https://github.com/fluffyfatec/Iacit/blob/Sprint-2/GIT/cabecario (3).jpg" width="60%" height="55%">

### Reposiório do Projeto

[IACIT - Fluffy Fatec](https://github.com/fluffyfatec/Iacit)

### Parceiro Acadêmico

IACIT Soluções Tecnológicas

### Visão do Projeto

O desafio foi estipulado como desenvolver um sistema que permita realizar a importação dos dados meteorológicos, bem como armazená-los em uma base de dados, para posteriormente gerar os relatórios desejados por nossos clientes.

Como solução, a equipe desenvolveu um software web para a empresa, que possibilita a automatização desde o download, o processamento dos dados e a persistência dos dados no banco de dados de forma simplificada. Também é possível realizar a filtragem desses dados por temperatura, umidade, estações, vento, pressão atmosférica, radiação global e precipitação, além da diversa visualizações desses dados. E por último, foram desenvolvidos diferentes níveis de usuários juntamente com o painel administrativo possibilitando a exportação dos relatórios a partir dos dados.

Representação da solução do projeto:

<img src="https://github.com/fluffyfatec/Iacit/blob/Sprint-2/GIT/VID-20221009-WA0013%20(2).gif" width="60%" height="55%">


### Tecnologias Adotadas na Solução

#### Java - Spring Boot

A linguagem Java foi utilizada em praticamente todo o back-end da aplicação. Junto com o framework Spring Boot, foram desenvolvidas, com a linguagem, diversas funcionalidades da aplicação, como a configuração da lógica para a utilização dos dados armazenados no banco de dados, o desenvolvimento de toda a API do sistema para que os dados possam ser consumidos pelo front-end, as funções de CRUD (Create, Read, Update, Delete) do usúario, e a segurança da aplicação via token.  

Para saber mais, acesse: [Java](https://www.java.com)

#### Python

A linguagem Python foi utilizada para a automatização do tratamento de dados da aplicação. Com ela, foi feito desde o download dos arquivos CSVs, originados do [Portal INMET](https://portal.inmet.gov.br), efetuando a descompactação dos arquivos, tratamento de todos os dados meteorológicos, e a inserção desses dados no banco de dados. Tudo de forma automatizada pela rotina de tarefas desenvolvidas na linguagem.

Para saber mais, acesse: [Python](https://www.python.org)

#### JavaScript

A linguagem JavaScript foi utilizada em grande parte do front-end da aplicação. Com ela foi efetuada a utilização dos dados enviados do back-end para o front-end, desenvolvendo gráficos, tabelas e outras formas de visualização de dados para o usuário. Além de ser utilizada para deixar as telas da aplicação de forma dinâmica, fazendo com que elas sejam responsivas com as ações tomadas pelo usuário e os dados atuais do banco de dados.

Para saber mais, acesse: [JavaScript](https://www.javascript.com)

#### PostgreSQL

O SGDB (Sistema Gerenciador de Banco de Dados) PostgreSQL foi utilizado para o armazenamento dos dados automatizados pelo Python. Com ele, foram feitas as criações de tabelas, views e triggers do banco de dados da aplicação, e era feito o gerenciamento dos dados.

Para saber mais, acesse: [PostgreSQL](https://www.postgresql.org)

### Contribuições Pessoais

Fui responsável pela programação do front-end da aplicação, que se consistia em consumir os dados gerados pelo back-end através de API e gerar uma interface para o usuário poder utilizar a aplicação.

Por estar focado nesta parte do projeto, fui encarregado, junto com a equipe de front-end, de estudar e desenvolver as telas da aplicação. Com isso, foram definidos os layouts de cada tela, desenvolvidos gráficos, tabelas e filtros dinâmicos, todos utilizando os dados consumidos do back-end.

O desenvolvimento das telas contou com a linguagem de marcação HTML, junto com a estilização em CSS. A parte lógica da aplicação contou com JavaScript, e em algumas situações, a técnica AJAX.

Exemplos de etapas do desenvolvimento do projeto:


<details open>
<summary>Geração de gráficos</summary>
<br>

```js
const ctx = document.getElementById('graficoTemperatura');
const myChart = new Chart(ctx, {
  type: 'line',
  data: {
      labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
      datasets: [{
          label: 'Temperatura',
          data: [12, 19, 3, 5, 2, 3],
          backgroundColor: [
              'rgba(255, 99, 132, 0.2)','rgba(54, 162, 235, 0.2)','rgba(255, 206, 86, 0.2)',
              'rgba(75, 192, 192, 0.2)','rgba(153, 102, 255, 0.2)','rgba(255, 159, 64, 0.2)'],
          borderColor: [
              'rgba(255, 99, 132, 1)','rgba(54, 162, 235, 1)','rgba(255, 206, 86, 1)',
              'rgba(75, 192, 192, 1)','rgba(153, 102, 255, 1)','rgba(255, 159, 64, 1)'],
          fill: 1
      }]
  },
  options: {
    responsive: true,
    scales: {
      y: { beginAtZero: false }
    }}
});
```

</details>

<details>
<summary>Exibição de gráficos</summary>
<br>

``` html
<div th:replace="~{fragmentCards :: Cards}"></div>
    <div class="row">
        <section class="col-lg-12 connectedSortable">
            <div th:replace="~{fragmentGraficos :: graficoTemperaturaBar}"></div>
            <div th:replace="~{fragmentGraficos :: graficoTemperaturaLinha}"></div>
            <div th:replace="~{fragmentGraficos :: graficoUmidadeLinha}"></div>
            <div th:replace="~{fragmentGraficos :: graficoUmidadeBar}"></div>
            <div th:replace="~{fragmentGraficos :: graficoVentoLinha}"></div>
            <div th:replace="~{fragmentGraficos :: graficoVentoBar}"></div>             
        </section>
    </div>
</div>
```

</details>

<details>
<summary>Geração de Tabelas</summary>
<br>

``` js
var $table = document.getElementById("tabelaPressao"),
$n = 16,
$rowCount = $table.rows.length,
$firstRow = $table.rows[0].firstElementChild.tagName,
$hasHead = ($firstRow === "TH"),
$tr = [],
$i,$ii,$j = ($hasHead)?1:0,
$th = ($hasHead?$table.rows[(0)].outerHTML:"");
var $pageCount = Math.ceil($rowCount / $n);

if ($pageCount > 1) {
  for ($i = $j,$ii = 0; $i < $rowCount; $i++, $ii++)
    $tr[$ii] = $table.rows[$i].outerHTML;
  $table.insertAdjacentHTML("afterend","<div id='buttons'></div");
  sort(1);
}

function sort($p) {
  var $rows = $th,$s = (($n * $p)-$n);
  for ($i = $s; $i < ($s+$n) && $i < $tr.length; $i++)
    $rows += $tr[$i];
  
  $table.innerHTML = $rows;
  document.getElementById("buttons").innerHTML = pageButtons($pageCount,$p);
  document.getElementById("id"+$p).setAttribute("class","chart");
}

function pageButtons($pCount,$cur) {
  var $prevDis = ($cur == 1)?"disabled":"",
    $nextDis = ($cur == $pCount)?"disabled":"",
    $buttons = "<input class='chart' type='button' value='&lt;&lt; Anterior' onclick='sort("+($cur - 1)+")' "+$prevDis+">";
  for ($i=1; $i<=$pCount;$i++)
    $buttons += "<input  class='chart' type='button' id='id"+$i+"'value='"+$i+"' onclick='sort("+$i+")'>";
  $buttons += "<input class='chart' type='button' value='Próximo &gt;&gt;' onclick='sort("+($cur + 1)+")' "+$nextDis+">";
  return $buttons;
}
```

</details>

<details>
<summary>Filtros dinâmicos</summary>

``` html
<select class="form-control" id="jsAjaxFiltro" onchange="filtroEstacao()" required>
    <option value="" selected>Escolha a Estação...</option>
    <option value="estacao" th:each="zz : ${filtroEstacao}">[[${zz.estacaoNome}]]</option>
</select>
```


</details>

### Aprendizados Efetivos (Soft e Hard Skills)

Com o desenvolvimento desse projeto, pude ter a oportunidade de me desenvolver de várias formas, tanto no âmbito acadêmico, como também no profissional e pessoal. Dentre estas oportunidades, destacam-se:
- Aprendizado e o aperfeiçoamento em áreas como a colaboração/trabalho em equipe;
- Comunicação entre os membros do grupo;
- Utilização do pensamento crítico; 
- Capacidade de resolução de problemas; 
- Gestão do tempo. 

Todas essas habilidades foram necessárias para que o grupo pudesse concluir o projeto de forma positiva e eficaz, entregando a solução do projeto. Essas "soft skills" são responsáveis por manter o grupo alinhado e trabalhando junto, cada um com a sua função específica, para que podessemos avançar nas etapas e nos desafios do projeto.

Juntos com elas, também se pode ressaltar algumas "hard skills" exigidas para esse projeto, como por exemplo:
- Conhecimento ligado ao desenvolvimento web;
- Gestão do banco de dados;
- Configuração de segurança da aplicação;
- Desenvolvimento de usuário e interface do usuário;
- Administração do sistema desenvolvido. 

Essas habilidades foram relevantes para a parte prática do projeto em si e, com a busca de materiais e trabalho em equipe, cada uma foi aperfeiçoada nesse tempo de desenvolvimento, resultando numa conclusão correta do sistema.