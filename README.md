# Charting the World: your guide to global data
#### Lucas Bryan Treuke, Gustavo Sanches Costa, Rodrigo Gomes Hutz Pintucci
## Descrição

Esse projeto é fruto de uma atividade da disciplina de Visualização de Dados do curso de Ciência de Dados da *FGV*. O objetivo é implementar uma visualização interativa e animada, buscando utilizar ferramentas e técnicas aprendidas durante o curso de acordo com sua efetividade.
Decidimos, portanto, trazer uma visão de indicadores de desenvolvimento humano ao redor do mundo, utilizando de dados da [World Bank Data Indicators](https://github.com/light-and-salt/World-Bank-Data-by-Indicators).
Para isto, utilizamos do *d3.js* para a construção da visualização, sendo importado para um arquivo *HTML* que pode ser acessado através do nosso [site github-pages](https://fgv-vis-2023.github.io/assignment-3-chartingtheworld/).

## Desenvolvimento

#### Decisões de projeto

Uma vez definido o tema e a fonte dos dados, a decisão mais direta foi ter um mapa como elemento central da visualização. A partir disso, decidimos que o mapa seria interativo, com a possibilidade de filtrarmos qual índice seria exibido, além da escolha de ano. 
Para representar os dados, optamos por um mapa coroplético, sendo a luminosidade da cor proporcional ao valor do índice. Além disso, tinhamos em mente como gráfico principal um globo, acompanhado de um mapa-mundi em menor escala.
Contudo, os dados retirados da fonte eram divididos entre vários datasets, de acordo com categorias gerais, como educação, saúde, economia, etc. Dessa forma, nossa ideia inicial consistia de um menu de seleção de categoria e, a partir disso, um menu de seleção de índice.
Um primeiro protótipo foi desenvolvido, com o objetivo de visualizar a ideia inicial e, a partir disso, decidir se a ideia era viável e se seria necessário fazer alguma alteração. O protótipo pode ser visto abaixo:

![Primeiro protótipo](\images\prototype1.jpeg)

Depois de uma melhor análise, observamos que poderíamos filtrar uma boa quantidade de índices. Dessa forma, decidimos tratar e filtrar os dados para a criação de um único dataset, contendo todos os índices que julgamos relevantes. Com isso, o menu de seleção de categoria foi removido, permanecendo apenas a seleção de índice. 
Além disso, aproveitamos a ideia da seleção de ano para adicionar uma animação, que mostra a evolução do índice ao longo dos anos. 
Com um número consideravelmente menor de índices, decidimos que seria viável adicionar um gráfico que indicasse a relação entre eles. Optamos por um gráfico de coordenadas paralelas, pois apresenta uma visualização agradável e apropriada para o número de dimensões que queríamos representar. 
Com essas decisões, criamos um segundo protótipo, que pode ser visto abaixo:

![Segundo protótipo](\images\prototype2.jpeg)

Com essa base formada, partimos para a implementação inicial da visualização em *d3.js*. A partir disso, começamos a perceber que algumas decisões não eram tão efetivas quanto imaginávamos, tal como a utilização do mapa-mundi em menor escala, que atrapalhava a visualização geral dos países. Portanto, decidimos utilizar um botão para ser capaz de alternar entre projeções.
Ademais, adicionamos a possibilidade de selecionar quais índices seriam exibidos no gráfico de coordenadas paralelas. Para interatividade, adicionamos um *tooltip* que exibe o valor do índice e o nome do país ao realizar *hover* sobre ele.
O resultado foi um *MVP*, que pode ser visto abaixo:

![MVP](\images\mvp.jpeg)

Ao apresentar o *MVP* em sala e levar em consideração o *feedback* dos colegas, percebemos que muitas coisas ainda poderiam ser melhoradas. A estética dos gráficos não estava agradável, as cores não eram padronizadas durante a animação, a escolha dos limites de ano fazia com que muitos anos com nenhum dado fossem exibidos, não havia padronização de língua, algum tipo de interação entre os gráficos ou maior interatividade do usuário com os dados, etc.
Assim, para a versão final consertamos os problemas mencionados acima. Além disso, decidimos que as projeções finais seriam a *Equal Earth*, apresentando uma visão geral dos países, e a *Orthographic*, que permite uma visão mais detalhada de regiões e amplifica a interatividade e do usuário com o mapa, com o objetivo de reter o interesse do usuário.
Em relação à interatividade, adicionamos a possibilidade de destacar um país nas coordenadas paralelas ao realizar *hover* sobre ele. Também podemos utilizar do *brush* para selecionar um intervalo nas coordenadas paralelas que limitará os países exibidos no mapa.
O resultado final pode ser visto abaixo:
[inserir imagem do final]


#### Equipe e divisão de tarefas

Nossa equipe é composta por três integrantes, responsáveis por todo o processo de desenvolvimento da visualização, desde a escolha do tema até a implementação final. Todos participaram de todas as etapas do projeto, sendo que toda decisão recebeu *input* de todos os membros. 
Contudo, para que várias tarefas pudessem ser realizadas simultaneamente, cada membro teve maior foco em certas etapas do projeto. Dessa forma, abaixo segue os integrantes e algumas áreas de maior foco:

- **Lucas Bryan Treuke**: Filtragem e tratamento dos dados, construção, estética e layout do site;
- **Gustavo Sanches Costa**: Ferramentas de interatividade, relação entre gráficos, estética dos gráficos;
- **Rodrigo Gomes Hutz Pintucci**: Ferramentas de animação, estética e padronização de escalas e legendas, relatório.

Vale ressaltar que a participação dos membros não se limitou às áreas de maior foco mencionadas.

#### Overview

A implementação do projeto foi feita em *d3.js*, como mencionado anteriormente. Inicialmente, trabalhamos com um dataset filtrado a um ano específico, para que pudéssemos testar a visualização.
Dessa forma, inspirado pelo [tutorial de mapas coropléticos](https://d3-graph-gallery.com/choropleth.html), começamos a implementar o mapa, com a escala de cores sendo definida de acordo com a seleção de um índice por meio de um menu de seleção.
Uma vez que o mapa estava funcionando, começamos a trabalhar na animação, que foi inspirada pelo [tutorial de interatividade](https://observablehq.com/@visualdslab/making-d3-charts-interactive) visto em sala. Assim, ao invés de trabalhar com um dataset menor, decidimos trabalhar com o dataset completo, sendo possível realizar uma filtragem por ano através de um *slider*.
Para as coordenadas paralelas, utilizamos como base o [tutorial de coordenadas paralelas](https://d3-graph-gallery.com/parallel.html), adaptando-o para o nosso dataset.
Por fim, adaptamos o código para que os gráficos funcionassem em conjunto, com a possibilidade de interação entre eles.
Dessa forma, como um passo é construído por cima do anterior, observamos um aumento gradual na complexidade do código e na probabilidade de gerar *bugs*, sendo necessária uma maior atenção à detalhes. Portanto, os aspectos mais recentes da implementação foram mais trabalhosos e demorados, em especial a interação entre os gráficos.
Uma estimativa de tempo para o projeto ao todo seja de 65 a 70 horas, com 20 horas até o *MVP* e 45 a 50 horas para a versão final. (não considerando o tempo gasto com busca do tema e idealização da visualização)