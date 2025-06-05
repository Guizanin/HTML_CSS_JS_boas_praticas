# Variáveis

## Use <i>const</i> ao invés de <i>let</i> ou <i>var</i>
Claro não quero obrigá-lo a usar somente <i>const</i>, mas resumindo usando <i>const</i> você estará blindando sua variável de ser modificada por algum equícovo no desenvolvimento além de ajudar na organização do seu código já que não conseguirá usá-la antes da sua declaração assim como acontece com <i>var</i>, fazendo sua aplicação quebrar ou tonrando o entendimento do código mais difícil.
Abaixo uma breve explicação e diferença entre os três tipos.

#### ```var```

Escopo: Global ou de função.

Elevação (Hoisting): Sim, as variáveis var são elevadas ao topo do seu escopo (global ou de função) durante a execução do código. A declaração da variável é içada, mas a inicialização permanece no seu lugar original. 

Reatribuição: Permite reatribuição.

---

#### ```let```

Escopo: De bloco. 

Elevação (Hoisting): Sim, mas com um período de tempo morto (Temporal Dead Zone) em que não é possível acessar a variável antes da sua declaração. Após a declaração, a variável torna-se acessível. 

Reatribuição: Permite reatribuição. 

---

### ```const```

Escopo: De bloco. 

Elevação (Hoisting): Sim, com um período de tempo morto. 

Reatribuição: Não permite reatribuição após a inicialização. 

> Observação: Se a variável const for um objeto ou array, o conteúdo do objeto/array pode ser alterado, mas não a variável em si (que aponta para o mesmo objeto/array). 

Entendento a singulariadade de cada uma conseguimos entender o que eu dizia no início deste tema, utilize com sabedoria 😉

## Variáveis, Funções, Métodos com nomes auto-explicativos
Usando a frase "Não me faça pensar" é basicamente isso que o nome da váriavel deve transmitir ao desenvolvedor, deve ser algo que reflita o seu uso, razão de sua existência, pois nem todos irão adivinhar o que significa uma variável nomeada <i>m</i> ou <i>p</i>. Aqui falei somente de variáveis, mas se tudo que for criado, você tiver o cuidado de criar um nome com o conceito abordado neste artigo, verá quão mais leve e de fácil entendimento isso trará para seu código.

```js
// nome reflete sua existência
const listUsers = ["user-1", "user-2"]
```
```js
// nome não reflete nada, somente confusão
const lU = ["user-1", "user-2"]
```

## Funções, Métodos curtos e objetivos
Você já deve ter se deparado com aquelas funções GIGANTESCAS, que fazem de tudo, até fazem café 🤣. Além de dificultarem o entendimento do que fazem, para que existem, tornam o código muito amarrado, quase uma "caixa de Pandora".
Você como desenvolvedor vai notar quando precisa retirar um trecho do seu código e criar outra função com ele.

```js
function atualizaSalvaUsuario(dadosAtualizados, dadosAntigos){
  [...métodos de validação dos dados novos...]
  [...métodos de validação dos dados antigos...]
  [...atualiza objeto com dados novos...]
  [...salva o usuário com dados atualizados...]
  [...realiza alguma função com os dados salvos...]
}
```

Aqui temos um bom exemplo de uma função com muitas responsábilidades e acoplamento. Poderiamos quebrar em diversas funções para cada tipo de ação, e dentro da função principal com o nome de <i>salvaUsuário</i> somente rodar os métodos e ao final feliz somente salvar e o retorno enviar para alguma função para tratamento. 
```js
function validaDados(dados){
  valida dados e retorna
}
function encontraUsuario(dados){
  busca usuário e realiza validações
}
function atualizaUsuario(dados){
  atualiza o objeto usuário
}
function metodosUsuarioSalvo(dados){
  realiza ações com o usuário salvo
}

function salvaUsuario(dadosAtualizados, dadosAntigos){
  1- validaDados(dados)
  2- encontraUsuario(dados)
  3- atualizaUsuario(dados)
  4- metodosUsuarioSalvo(dados)
}
```
Podemos notar agora que a função <i>salvaUsuario</i> é responsável só por orquestrar as chamadas de outras funções que realizam uma série de tarefas que a <i>salvaUsuario</i> não conhece a implementação, ela só chama os responsáveis e no final salva o usuário. 

E agora com funções realizando pequenas tarefas podemos reutilizá-las caso precisemos em outra parte do desenvolvimento 😊.

- Mas como saber quando criar uma função a parte para realizar determinada tarefa?
- Será que irei reutilizá-la algum dia?

Então, dependendo da tarefa, essa tarefa é tão específica se será utilizada somente dentro daquela função ou contexto. Mas quando se trata de algo um pouco mais genérico, muitas vezes você pode deixar esse método dentro da função que o esta utilizando, e se precisar fazer um copia/cola dele, então é a hora de criar uma função específica para ele. 

Muitas das vezes você não terá uma visão do futuro do projeto para saber se deverá criar uma função extra para ele ou não, e está tudo bem, isso faz parte da vida mesmo, até porque ficar criando função específica para tudo é cansativo, pois devem ser levados alguns fatores em questão, organização do local que conterá essa nova função, os parametros que serão recebidos e utilizados. 
O que podemos deixar combinado é, caso precise fazer um copia/cola de algum método para utilizar em outra parte do projeto, pode criar uma função para ele, pois possivelmente ele será reutilizado mais vezes, e também, pelo motivo de manutenção, imagine ter que  buscar no projeto todo os lugares ondem foi colado o método copiado para alterar uma parte dele.