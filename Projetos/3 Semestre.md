# Projeto 3: 2º Semestre de 2023 

<html>
  <body>
     <table align ="center">
     <tr>
       <p align ="center"><img src="https://github.com/fluffyfatec/Iacit/blob/Sprint-1/GIT/cabecario%20(3).jpg" width="100%" height="100%"></img></p>
     </tr>
    </table>

## Empresa parceira

A IACIT é uma empresa brasileira, fundada em 1986, e com sede em São José dos Campos (SP), um dos principais polos tecnológicos do Brasil e do mundo.

São 36 anos de experiência que começaram com a prestação de suporte técnico à Tecnasa, fabricante de equipamentos para o segmento de navegação aérea. Desde então, a empresa é impulsionada pelos constantes esforços para ampliar suas referências e conquistar novos mercados.

<h1>Portifólio da 3°API</h1>
<p align="justify"> Portfólio das Aprendizagens a partir de Projeto Integrador (APIs),
apresentado à Faculdade de Tecnologia de São José dos Campos,
como parte dos requisitos necessários para a obtenção do título de Tecnólogo em Banco de Dados.</p>
<hr>
<h2><li><b>Descrição do Projeto</b></li></h2>
    <p align="justify">
      <a href="https://github.com/heyMichaelS/Iacit">#DASHBOARD METEOROLÓGICO</a> Foi elaborado um programa online para a empresa Iacit que permite automatizar o download, processamento e armazenamento simplificado dos dados meteorológicos no banco de dados. Além disso, será possível filtrar esses dados por temperatura, umidade, estações, vento, pressão atmosférica, radiação solar e precipitação, bem como visualizá-los de várias formas. Além disso, foram desenvolvidos diferentes níveis de usuários, juntamente com um painel administrativo, que permite exportar relatórios com base nos dados obtidos.
    </p>

<p align="center">
      <img src="https://github.com/fluffyfatec/Iacit/blob/Sprint-2/GIT/VID-20221009-WA0013%20(2).gif" width="100%" height="100%">
<p align="center">

  
Dominar a biblioteca Chart.js e a criação de gráficos foi uma experiência técnica enriquecedora. Explorei suas funcionalidades, personalizando a aparência e adicionando interatividade. Agora sou capaz de criar visualizações de dados sofisticadas e profissionais, transmitindo informações complexas de forma clara e impactante. Essa habilidade amplia minhas capacidades como desenvolvedor, oferecendo aos usuários uma experiência excepcional de análise de dados.



<h2>Tecnologias Utilizadas</h2>
    <details open>
<summary>Front-End</summary>

* JavaScript
* HTML
* CSS
* ChartJs

</details>

 <details open>
<summary>Back-End</summary>

* Java
* Python
* Spring boot

</details>

<details open>
<summary>Banco de Dados</summary>

* PostgresSQL

</details>

<details open>
<summary>Reuniões e Comunicação</summary>

* Discord
* Whatsaap
* Slack

</details>

<details open>
<summary>Outras Ferramentas</summary>

* Github
* Eclipse IDE
* Intellij IDE
* Azure DevOps
* Photoshop

</details>
    

Minha atuação como desenvolvedor do grupo Fluffy fiquei na parte do front-end onde tivemos uma missão de criar um deashbord intuitivo que fosse possivel ter a visualização de algumas formas de dados meterologicos
<br>
 
# Contribuicoes individuais

<details open>
 <summary>Plotar Graficos</summary>
  <br>
 
  Apresentamos abaixo um trecho de código responsável por recuperar informações geradas no banco de dados e exibi-las visualmente na forma de gráficos de linha. Essa funcionalidade permite que os dados sejam apresentados de maneira visual na tela, possibilitando uma análise prioritária de acordo com as necessidades do cliente. Com esse recurso, é possível oferecer uma experiência interativa e personalizada, permitindo que o cliente tome decisões com base nas informações apresentadas de forma clara e visualmente atraente.
  
  <br>
  
  ```
  let tipo = ''

function btnlinha(){
    tipo = 'line'
    gerarGrafico()
}

function btnhist(){
    tipo = 'bar'
    gerarGrafico()
}


function gerarGrafico(){

    if (tipo == 'line'){ //LINHA///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
        const ctx = document.getElementById('grafico').getContext('2d');
        const myChart = new Chart(ctx, {
            type: tipo,
            data: {
                labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
                datasets: [{
                    label: '# of Votes',
                    data: [12, 19, 3, 5, 2, 3],
                    backgroundColor: [
                        'rgba(255, 99, 132, 0.2)',
                        'rgba(54, 162, 235, 0.2)',
                        'rgba(255, 206, 86, 0.2)',
                        'rgba(75, 192, 192, 0.2)',
                        'rgba(153, 102, 255, 0.2)',
                        'rgba(255, 159, 64, 0.2)'
                    ],
                    borderColor: [
                        'rgba(255, 99, 132, 1)',
                        'rgba(54, 162, 235, 1)',
                        'rgba(255, 206, 86, 1)',
                        'rgba(75, 192, 192, 1)',
                        'rgba(153, 102, 255, 1)',
                        'rgba(255, 159, 64, 1)'
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                scales: {
                    y: {
                        beginAtZero: true
                    }
                }
            }
        });

    }
  
  ```
</details>


<details open>
 <summary> Desenvolvi a tabela juntamente com a paginação</summary>
  <br>
 
  Abaixo com esse trecho de codigo onde no front foi gerada a paginação das tabelas nesse em questão foi da tabela de precipitação onde também é decidido a quantidade de paginas que vai ter de acordo com dados que são poulados na tabela em questão.

  <br> 
  
  ```
  // get the table element
var $table = document.getElementById("tabelaPrecipitacao"),
// number of rows per page
$n = 16,
// number of rows of the table
$rowCount = $table.rows.length,
// get the first cell's tag name (in the first row)
$firstRow = $table.rows[0].firstElementChild.tagName,
// boolean var to check if table has a head row
$hasHead = ($firstRow === "TH"),
// an array to hold each row
$tr = [],
// loop counters, to start count from rows[1] (2nd row) if the first row has a head tag
$i,$ii,$j = ($hasHead)?1:0,
// holds the first row if it has a (<TH>) & nothing if (<TD>)
$th = ($hasHead?$table.rows[(0)].outerHTML:"");
// count the number of pages
var $pageCount = Math.ceil($rowCount / $n);
// if we had one page only, then we have nothing to do ..
if ($pageCount > 1) {
  // assign each row outHTML (tag name & innerHTML) to the array
  for ($i = $j,$ii = 0; $i < $rowCount; $i++, $ii++)
    $tr[$ii] = $table.rows[$i].outerHTML;
  // create a div block to hold the buttons
  $table.insertAdjacentHTML("afterend","<div id='buttons'></div");
  // the first sort, default page is the first one
  sort(1);
}

  ```
</details>




<details open>
 <summary>Auxilei também na exportação tanto das tabelas quanto dos graficos em pdf</summary>
    <br>
  
Com base no código abaixo, apresentamos um exemplo do processo de geração de gráficos em PDF. Os parâmetros necessários para a criação de cada imagem são passados, permitindo ao cliente baixar qualquer gráfico de qualquer tela que ofereça essa funcionalidade. Isso oferece flexibilidade ao usuário, que pode escolher livremente quais gráficos deseja incluir em seu PDF.
 
  <br> 
  
  
  ```
  function jsGraficosPDF(chart1, chart2, tela) {

    const canvas = document.getElementById(chart1);
    const canvas2 = document.getElementById(chart2);

    //criando a imagem a partir do gráfico
    const canvasImage = canvas.toDataURL('image/png', 1);
    const canvasImage2 = canvas2.toDataURL('image/png', 1);

    //variáveis para o texto do PDF
    var estado = document.getElementById('estado');
    var estacao = document.getElementById('estacao');
    var dataMin = document.getElementById('dtMin');
    var dataMax = document.getElementById('dtMax');

    //passando a imagem para o pdf
    let pdf = new jsPDF('landscape');
    pdf.setFontSize(24);
    pdf.setFont('helvetica', 'bold');
    pdf.text(15, 15, ["Estação " + estacao.innerText + ", Estado de " + estado.innerText, " "]);
    pdf.setFont('helvetica', '');
    pdf.text(15, 15, [" ", "Dados de " + dataMin.innerText + " até " + dataMax.innerText]);
    pdf.addImage(canvasImage, 'PNG', 10, 35, 275, 150);
    pdf.addPage();
    pdf.addImage(canvasImage2, 'PNG', 10, 30, 275, 150);
    pdf.save('Gráficos ' + tela + ' (' + estacao.innerText + ').pdf');

}

  
  ```
</details>



<br>

 <details open>

   <summary>Soft skills:</summary>
     
   <br>
 
`Trabalho em equipe:` Colaborei de forma eficaz em um projeto, contribuindo para o desenvolvimento de um dashboard eficiente e intuitivo.
  
   <br>
   
`Comunicação:` Mantive uma comunicação clara e efetiva com a equipe, garantindo que as tarefas fossem executadas de maneira adequada.
   
   <br>
   
`Adaptabilidade:` Fui capaz de me adaptar a diferentes desafios e requisitos do projeto, buscando soluções criativas para atender às necessidades dos usuários.
     
   <br>
   
`Organização:` Gerenciei meu tempo e tarefas de forma eficiente, garantindo que os prazos fossem cumpridos e o trabalho fosse entregue com qualidade.
    
   <br>
   
`Aprendizado rápido:` Assimilei novas tecnologias e conceitos, como bibliotecas de visualização de dados e frameworks de desenvolvimento web, de forma rápida e eficiente.
  <br> 
 </details>
  
  
   <details open>

   <summary>Hard skills:</summary>
     
   <br>
  
  

`Desenvolvimento Front-end:` Possuo habilidades sólidas em HTML, CSS e JavaScript, aplicando essas tecnologias para criar interfaces amigáveis e responsivas.

   <br>
     
`Chart.js:` Dominei a biblioteca Chart.js para criar gráficos interativos e atrativos, exibindo informações de maneira clara.

   <br>
     
`Bootstrap Table:` Utilizei o framework Bootstrap Table para desenvolver tabelas dinâmicas e implementar a funcionalidade de paginação.

   <br>
     
`Figma:`  Adquiri conhecimentos básicos em Figma, utilizando-o para criar esboços de layout e fluxos de interação, contribuindo para a concepção de uma interface de usuário intuitiva.

   <br>
     
`UX/UI Design:` Aprendi sobre os princípios de design de experiência do usuário (UX) e design de interface do usuário (UI), aplicando elementos visuais e interativos para facilitar a navegação e criar uma experiência agradável para o usuário.
   
   <br>
     
</details>

### Aprendizados Efetivos Hard Skills
<table>
  <tr>
    <th width="300px">Tecnologia/Metodologia</th>
    <th width="300px">Classificação</th>
  </tr>
  <tr>
    <td>Java</td>
    <td>★★★★★☆☆☆☆☆</td>
  </tr>
  <tr>
    <td>Chart.js</td>
    <td>★★★★★★★☆☆☆</td>
  </tr>
  <tr>
    <td>Vue</td>
    <td>★★★★★☆☆☆☆☆</td>
  </tr>
  <tr>
    <td>Figma</td>
    <td>★★★☆☆☆☆☆☆☆</td>
  </tr>
</table>
  
