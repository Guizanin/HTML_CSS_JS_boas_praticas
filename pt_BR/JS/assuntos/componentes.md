# Componentes
Assunto delicado, pois dependendo de como forem desenvolvidos, teremos que ficar adicionando regras dentro da parte principal, para exibir ou não determinada parte de acordo com parâmetros recebidos ou não. Ou as vezes acabamos fazendo o componente específico para uma parte do projeto e no final temos que alterar ele adicionando regras de validações. Isso tudo pode virar uma bola de neve gigantesca.

Tendo isso em vista, devemos sempre pensar em alguns pontos ao desenvolver um componente.

## Criar componenetes <i>white label</i>
Assim como nos produtos white label a ideia é a mesma. O conteúdo do componente ou os dados principais serão recebidos por parâmetro, isso torna seu componente reutilizável e mais flexível também.

## Utilizar patterns de desenvolvimento -> Composite pattern
o [Composite pattern](https://medium.com/@guilherme.pomp/creating-react-components-with-the-composition-pattern-f59c895f27bc) pode ser de grande ajuda quando desenvolvemos algum componente mais complexo, se de alguma forma teria diversos if's ou qualquer outra regra tornando-o complexo e gigantesco. Resumindo o composite pattern, segmentamos todas partes do componentes em mini componentes, o arquivo principal trata de gerenciar tudo e exportar. Quando utilizamos o componente, montados ele com as partes necessárias para nossa utilização e o que não for necessário simplismente não é utilizado. Isso remove do componente uma complexidade gigantesca que ele teria para gerenciar quais partes seriam chamadas em determinada parte e seu conteúdo.  Isso lembra um pouco aquela questão da função não ter responsabilidades de mais dentro dela e ter outras mini funções que realizem pequenas coisas para ela.