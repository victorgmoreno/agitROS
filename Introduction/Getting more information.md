# Obtendo mais informações

Como aludido acima, este livro não faz nenhuma tentativa de ser uma referência abrangente para ROS. É quase certo que você precisará de detalhes adicionais para fazer algo interessante. Felizmente, as informações online sobre ROS são abundantes.

- Mais importante ainda, os desenvolvedores de ROS mantêm uma [documentação](http://wiki.ros.org/) extensa, including a set of tutorials. incluindo um conjunto de tutoriais. Este livro inclui links para muitas das páginas correspondentes nesta documentação. Se você estiver lendo uma versão eletrônica do livro em um visualizador de PDF razoavelmente moderno, poderá clicar nesses links diretamente para abri-los em seu navegador.
- Quando coisas inesperadas acontecem - e é muito provável que isso aconteça - há um site de perguntas e respostas (no estilo do Stack Exchange) dedicado ao [ROS](http://answers.ros.org/).
- Também pode ser valioso se inscrever na [lista de discussão dos usuários de ROS](http://lists.ros.org/mailman/listinfo/ros-users), na qual as novidades geralmente aparecem.

Aqui estão dois detalhes importantes que o ajudarão a entender parte da documentação, mas nem sempre são totalmente explicados no contexto.

## Distribuições

As versões principais de ROS são chamadas de [**distributions**](http://wiki.ros.org/Distributions) e são nomeadas usando adjetivos que começam com letras sucessivas do alfabeto. (Isso é, para comparação, muito semelhante aos esquemas de nomenclatura usados ​​para outros grandes projetos de software, incluindo Ubuntu e Android.) No momento em que este livro foi escrito, a distribuição atual era índigo. A próxima distribuição, chamada de [`jade`](http://wiki.ros.org/jade), será lançada em maio de 2015. Distribuições mais antigas incluem `hydro`, `groovy`, `fuerte`, `electric`, `diamondback`, `C Turtle`, e `box turtle`. Esses nomes de distribuição aparecem em muitos lugares ao longo da documentação.

> :warning: Para manter as coisas o mais simples e atualizadas possível, este livro pressupõe que você esteja usando `indigo`.

> :fast_forward:  Se, por algum motivo, você precisar usar `hydro` em vez de `indigo`, uase todo o conteúdo do livro ainda se aplica sem modificação. O mesmo é verdadeiro para `groovy` também, com uma exceção importante: em distribuições mais recentes que `groovy` (e, portanto, neste livro), os comandos de velocidade para o simulador `turtlesim` oram alterados para usar um tipo de mensagem padrão e nome de tópico que é compartilhado entre muitos robôs móveis
>
> | Distribuição  | Nome do tópico    | tipo de mensagem  |
> | ------------- | ----------------- | ----------------- |
> | `groovy` | `/turtle1/command_velocity`  | `turtlesim/Velocity` |
> | `indigo`/`hydro`  | `/turtle1/cmd_vel` | `geometry_msgs/Twist`  |
>
> Essa mudança tem algumas implicações práticas:
> - Ao adicionar dependências ao seu pacote, você precisará de uma dependência de `turtlesim`, em vez de `geometry_msgs`.
> - O arquivo de cabeçalho relevante (consulte a página 49) é `turtlesim/Velocity.h`  em vez de `geometry_msgs/Twist.h`.
> - O tipo de mensagem `turtlesim/Velocity` tem apenas dois campos, chamados linear e angular. Esses campos desempenham as mesmas funções que os campos `linear.x` e `angular.z` de `geometry_msgs/Twist`. Essa alteração se aplica à linha de comando e ao código C++.

## Sistemas de construção 

Começando com a distribuição `groovy` distribution, ROS teve algumas mudanças importantes na forma como o _software_ é compilado. Distribuições mais antigas e pré `groovy`  usavam um sistema de construção chamado `rosbuild`,  mas versões mais recentes começaram a substituir o `rosbuild` por um novo sistema de construção chamado `catkin`. É importante saber sobre essa mudança porque alguns dos tutoriais têm versões separadas, dependendo se você está usando `rosbuild` ou `catkin`. Essas versões separadas são selecionadas usando um par de botões próximo ao topo do tutorial. Este livro descreve `catkin`, mas pode haver alguns casos em que `rosbuild` é a escolha melhor.

