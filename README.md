# Charting the World: your guide to global data
#### Lucas Bryan Treuke, Gustavo Sanches Costa, Rodrigo Gomes Hutz Pintucci
## Descrição

Esse projeto é fruto de uma atividade da disciplina de Visualização de Dados do curso de Ciência de Dados da *FGV*. O objetivo é implementar uma visualização interativa e animada, buscando utilizar ferramentas e técnicas aprendidas durante o curso de acordo com sua efetividade.
Decidimos, portanto, trazer uma visão de indicadores de desenvolvimento humano ao redor do mundo, utilizando de dados da [World Bank Data Indicators](https://github.com/light-and-salt/World-Bank-Data-by-Indicators).
Para isto, utilizamos do *d3.js* para a construção da visualização, sendo importado para um arquivo *HTML* que pode ser acessado através do nosso [site github-pages](https://fgv-vis-2023.github.io/assignment-3-chartingtheworld/). O source code pode ser encontrado neste [notebook](https://observablehq.com/d/73cb3dcdc6d879de)

## Desenvolvimento

#### Decisões de projeto

Uma vez definido o tema e a fonte dos dados, a decisão mais direta foi ter um mapa como elemento central da visualização. A partir disso, decidimos que o mapa seria interativo, com a possibilidade de filtrarmos qual indicador seria exibido, além da escolha de ano. 
Para representar os dados, optamos por um mapa coroplético, sendo a luminosidade da cor proporcional ao valor do indicador. Além disso, tinhamos em mente como gráfico principal um globo, acompanhado de um mapa-mundi em menor escala.
Os dados retirados da fonte eram divididos entre vários datasets, de acordo com categorias gerais, como educação, saúde, economia, etc. Dessa forma, nossa ideia inicial consistia de um menu de seleção de categoria e, a partir disso, um menu de seleção de indicador.
Um primeiro protótipo foi desenvolvido, com o objetivo de visualizar a ideia inicial e, a partir disso, decidir se a ideia era viável e se seria necessário fazer alguma alteração. O protótipo pode ser visto abaixo:

![Primeiro protótipo](.\images\prototype1.jpeg)

Depois de uma melhor análise, observamos que poderíamos filtrar uma boa quantidade de indicadores. Dessa forma, decidimos tratar e filtrar os dados para a criação de um único dataset, contendo todos os indicadores que julgamos relevantes. Com isso, o menu de seleção de categoria foi removido, permanecendo apenas a seleção de indicador. 
Além disso, aproveitamos a ideia da seleção de ano para adicionar uma animação, que mostra a evolução do indicador ao longo dos anos. 
Com um número consideravelmente menor de indicadores, decidimos que seria viável adicionar um gráfico que indicasse a relação entre eles. Optamos por um gráfico de coordenadas paralelas, pois apresenta uma visualização agradável e apropriada para o número de dimensões que queríamos representar. 
Com essas decisões, criamos um segundo protótipo, que pode ser visto abaixo:

![Segundo protótipo](.\images\prototype2.jpeg)

Com essa base formada, partimos para a implementação inicial da visualização em *d3.js*. A partir disso, começamos a perceber que algumas decisões não eram tão efetivas quanto imaginávamos, tal como a utilização do mapa-mundi em menor escala, que atrapalhava a visualização geral dos países. Portanto, decidimos utilizar um botão para ser capaz de alternar entre projeções.
Ademais, adicionamos a possibilidade de selecionar quais indicadores seriam exibidos no gráfico de coordenadas paralelas. Para interatividade, adicionamos um *tooltip* que exibe o valor do indicador e o nome do país ao realizar *hover* sobre ele.
O resultado foi um *MVP*, que pode ser visto abaixo:

![MVP](.\images\mvp.jpeg)

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
Dessa forma, inspirado pelo [tutorial de mapas coropléticos](https://d3-graph-gallery.com/choropleth.html), começamos a implementar o mapa, com a escala de cores sendo definida de acordo com a seleção de um indicador por meio de um menu de seleção.
Uma vez que o mapa estava funcionando, começamos a trabalhar na animação, que foi inspirada pelo [tutorial de interatividade](https://observablehq.com/@visualdslab/making-d3-charts-interactive) visto em sala. Assim, ao invés de trabalhar com um dataset menor, decidimos trabalhar com o dataset completo, sendo possível realizar uma filtragem por ano através de um *slider*.
Para as coordenadas paralelas, utilizamos como base o [tutorial de coordenadas paralelas](https://d3-graph-gallery.com/parallel.html), adaptando-o para o nosso dataset.
Por fim, adaptamos o código para que os gráficos funcionassem em conjunto, com a possibilidade de interação entre eles.
Dessa forma, como um passo é construído por cima do anterior, observamos um aumento gradual na complexidade do código e na probabilidade de gerar *bugs*, sendo necessária uma maior atenção à detalhes. Portanto, os aspectos mais recentes da implementação foram mais trabalhosos e demorados, em especial a interação entre os gráficos.
Uma estimativa de tempo para o projeto ao todo seja de 65 a 70 horas, com 20 horas até o *MVP* e 45 a 50 horas para a versão final. (não considerando o tempo gasto com busca do tema e idealização da visualização)

#### Interatividade

Utilizamos várias ferramentas para que o usuário pudesse interagir com os dados. Abaixo, segue uma lista das possibilidades de interação:

- **Seleção de indicador**: O usuário pode selecionar um indicador através de um menu de seleção. Os gráficos serão atualizado de acordo com a seleção, modificando a escala de cores e suas atribuições.

- **Seleção de ano**: O usuário pode selecionar um ano através de um *slider*. Os gráficos serão atualizado de acordo com a seleção, filtrando quais dados serão exibidos. Os valores mínimos e máximos do *slider* são definidos de acordo com os dados disponíveis para o indicador selecionado.
    - **Animação**: O usuário pode selecionar a opção de animação, através de um botão de play, que fará com que o ano seja atualizado automaticamente. 

- **Seleção de coordenadas paralelas**: Ao lado de cada reta que indica um indicador, há um *checkbox* que desativa ou ativa a exibição da reta. Dessa forma, o usuário pode selecionar quais indicadores serão exibidos no gráfico de coordenadas paralelas.
    - Caso um *checkbox* esteja desativado, o nome do indicador não será exibido no gráfico de coordenadas paralelas. Contudo, ao realizar *hover* sobre o *checkbox*, o nome será exibido.
    - É possível que um indicador não tenha dados para o ano selecionado, fazendo com que as linhas correspondentes ao indicador não sejam exibidas no gráfico de coordenadas paralelas.
        - Isso faz com que todas as retas subsequentes também não sejam exibidas. Desativar o *checkbox* desse indicador faz com que as retas subsequentes sejam exibidas, desde que possuam dados para o ano selecionado.

- **Hover**: Ao realizar *hover* sobre um país no mapa, o mesmo será destacado no mapa e nas coordenadas paralelas. Além disso, um *tooltip* será exibido, contendo o nome do país e o valor do indicador selecionado.
    - Para o mapa, o país selecionado irá ter um leve aumento de tamanho, enquanto os demais países terão sua opacidade reduzida.
    - Ao selecionar um país no mapa, as linhas correspondentes ao país terão um destaque quanto à sua grossura, enquanto as demais linhas terão sua opacidade reduzida.

- **Brush**: O usuário pode selecionar um intervalo nas coordenadas paralelas através do *brush*. O mapa será atualizado de acordo com a seleção, filtrando quais dados serão exibidos. Os valores mínimos e máximos do *brush* são definidos de acordo com os dados disponíveis para o indicador selecionado.
    - Os países que não estão dentro do intervalo selecionado serão atribuídos à cor cinza, tal como os países que não possuem dados para o ano selecionado.
    - Um texto será exibido embaixo do grsáfico, indicando o número de países que estão dentro do intervalo selecionado. Caso não haja nenhum país dentro do intervalo, o texto será colorido de vermelho.

- **Alteração de projeção**: O usuário pode alternar entre as projeções *Equal Earth* e *Orthographic* através de um botão. 

- **Drag**: Caso o usuário esteja utilizando a projeção *Orthographic*, ele pode arrastar o mapa para alterar o ângulo de visualização, sendo possível focar em qualquer região do globo.