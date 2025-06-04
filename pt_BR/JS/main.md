# 🇧🇷 JAVASCRIPT

Aqui abordaremos boas práticas, como exemplos colocarei REACT, mas vai valer para qualquer framework ou até a forma pura de JS. Abordarei uma mistura de conceitos encontrados no [CleanCode](https://www.amazon.com.br/C%C3%B3digo-limpo-Robert-C-Martin/dp/8576082675/ref=asc_df_8576082675?mcid=2b0fb83a4146383497d27512de9c9086&tag=googleshopp00-20&linkCode=df0&hvadid=709884550309&hvpos=&hvnetw=g&hvrand=8913489556377063343&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9047750&hvtargid=pla-398225630878&psc=1&language=pt_BR&gad_source=1), até conceitos mais práticos de organização do arquivo JS.

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

Utilizando os tópicos já abordados até aqui
✅